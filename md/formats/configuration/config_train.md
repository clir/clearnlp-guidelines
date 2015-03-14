# Train Configuration Format
If you wish to train your model in ClearNLP and/or export the model you build, you will have to create a configuration xml file and pass it into ClearNLP for train.

#### Sample train configuration xml file
	<configuration>
	    <language>english</language>
 
	    <reader type="tsv">
	        <column index="1"  field="id"/>
	        <column index="2"  field="form"/>
	        <column index="4"  field="lemma"/>
	        <column index="6"  field="pos"/>
	        <column index="8"  field="feats"/>
	        <column index="9"  field="headId"/>
	        <column index="10" field="deprel"/>
	    </reader>

	    <pos>
	        <trainer algorithm="adagrad" type="svm" labelCutoff="4" featureCutoff="3" alpha="0.02" rho="0.1" average="false"/>
	        <ambiguity_class_threshold>0.4</ambiguity_class_threshold>
	        <proper_noun_tagset>NNP,NNPS</proper_noun_tagset>
	        <bootstraps>true</bootstraps>
	    </pos>
	    
		<dep>
	        <trainer algorithm="adagrad" type="lr" labelCutoff="4" featureCutoff="3" alpha="0.02" rho="0.1" average="false"/>
	        <evaluate_punctuation>false</evaluate_punctuation>
	        <root_label>root</root_label>
	        <bootstraps>true</bootstraps>
	    </dep>
	</configuration>
	
#### Configuration specifications
1. `<language>`: element specifies the language of the models.
	- `english` - English.
2. `<reader>`: element contains information about the [data format](../data_format.md).
	- The `type` attribute specifies the type of the data format: `raw|line|tsv`.
		+ The `raw` type accepts texts in any format: `<reader type="raw">`.
		+ The `line` type requires each sentence to be in one line: `<reader type="line">`.
		+ The `tsv ` type requires each field to be in one column: `<reader type="tsv">`.
	- When the `tsv ` type is used, `<tsv>` elements need to be specified.
		+ The `index` attribute specifies the index of a field, starting at 1.
		+ The `field` attribute specifies the name of the field:
			* `id` - token ID, starting at 1
			* `form` - word form
			* `lemma` - lemma
			* `pos` - part-of-speech tag
			* `feats` - features
			* `headId` - head token ID
			* `deprel` - dependency label
			* `sheads` - semantic heads

3. `<MODE>...</MODE>`: Training mode
	1. `<trainer>...</trainer>`:
		* `algorithm=""`: `adagrad` for Adagrad algorithm, `liblinear`for liblinear algorithm
		* `type=""`: `svm` for support vector machine, `lr` for linear regression
		* `labelCutoff="N"`: Cutoff count threshold for labels appears less than N times
		* `featureCutoff="N"`: Cutoff count threshold for features appears less than N times
		* `alpha="N"`: learning rate N
		* `rho`: smoothing denominator N
		* `average ="T|F"`: boolean for averaging hyperplanes
	2. `<bootstraps>T|F</bootstraps>`: boolean for enabling bootstrap for trainer
	3. `<ATTRIBUTES>...</ATTRIBUTES>`: Additional attributes specified for associating modes