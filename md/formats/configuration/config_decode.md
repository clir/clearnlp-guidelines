# Decode Configuration Format

If you wish to use the existing models in ClearNLP to decode, you will have to create a configuration xml file and pass it into ClearNLP for decode.

#### Sample decode configuration xml file
	<configuration>
	    <language>english</language>

	    <model>
	        <pos>edu/emory/clir/clearnlp/model/english/general/pos.gz</pos>
	        <dep>model/dep.0</dep>
	        <seq>model/seq.gz</seq>
	    </model>

	    <reader type="tsv">
	        <column index="1" field="id"/>
	        <column index="2" field="form"/>
	        <column index="3" field="lemma"/>
	        <column index="4" field="pos"/>
	        <column index="5" field="feats"/>
	        <column index="6" field="headId"/>
	        <column index="7" field="deprel"/>
	        <column index="8" field="sheads"/>
	    </reader>
	    
	    <dep>
	        <beam_size>16</beam_size>
	    </dep>
	</configuration>
	
#### Configuration specifications
1. `<model>`: element specifies the [kind of model](../../getting_started/add_models.md) you want to run.
2. `<language>`: element specifies the language of the models.
	- `english` - English.
3. `<reader>`: element contains information about the [data format](../data_format.md).
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

4. `<MODE>`: Decoding mode

	ClearNLP has various decoding modes already built-in: `pos|morph|dep|srl`. You will have to specify the mode that you wish to decode your document in inside the configuration file.
	
	1. Part-of-speech tagging (`pos`)
	2. Morphological analyzer (`morph`)
	3. Dependency parsing (`dep`)
	4. Semantic role labeling (`srl`)

	> You could add additional mode to ClearNLP if you wish (See [add components to ClearNLP](../../api/add_component_to_clearnlp.md))