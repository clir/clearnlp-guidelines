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
1. `<language>...</language>`: Language of the input data
2. `<model...></model>`: Import models that are needed for decode
3. `<reader type="...">...</reader>`: Type of reader for reading inputs

	ClearNLP supports various data format for input (see [data format](../formats/data_format.md)), you will have to sepecify reader type `type="..."` for reading inputs. You will also have to sepcify the column indices if you have data that is separated based on attributes.

	1. LineReader (`line`): For reading in document that has sentences separated in lines
	2. RawReader (`raw`): For reading in document with untokenized sentences
	3. TSVReader (`tsv`): For reading in document with attributes specified for each token

4. `<MODE>...</MODE>`: Decoding mode

	ClearNLP has various decoding modes already built-in: `pos|morph|dep|srl`. You will have to specify the mode that you wish to decode your document in inside the configuration file.
	
	1. Part-of-speech tagging (`pos`)
	2. Morphological analyzer (`morph`)
	3. Dependency parsing (`dep`)
	4. Semantic role labeling (`srl`)

	> You could add additional mode to ClearNLP if you wish (See [add components to ClearNLP](../api/add_component_to_clearnlp.md))