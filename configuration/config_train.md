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
1. `<language>...</language>`: Language of the input data
2. `<reader type="...">...</reader>`: Type of reader for reading inputs

	ClearNLP supports various data format for input (see [data format](../formats/data_format.md)), you will have to sepecify reader type `type="..."` for reading inputs. You will also have to sepcify the column indices if you have data that is separated based on attributes.

	1. LineReader (`line`): For reading in document that has sentences separated in lines
	2. RawReader (`raw`): For reading in document with untokenized sentences
	3. TSVReader (`tsv`): For reading in document with attributes specified for each token

3. `<MODE>...</MODE>`: Training mode
	1. `<trainer>...</trainer>`:
	2. `<bootstraps>...</bootstraps>`:
	3. `<ATTRIBUTES>...</ATTRIBUTES>`
