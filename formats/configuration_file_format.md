# Configuration File Format

For decoding, `<model>`, `<language>`, and `<reader>` elements, must be specified in the configuration file.

	<configuration>
	    <model>general-en</model>
	    <language>en</language>
	 
	    <reader type="column">
	        <column index="1" field="id"/>
	        <column index="2" field="form"/>
	        <column index="3" field="lemma"/>
	        <column index="4" field="pos"/>
	        <column index="5" field="feats"/>
	        <column index="6" field="headId"/>
	        <column index="7" field="deprel"/>
	        <column index="8" field="sheads"/>
	    </reader>
	</configuration>
	
* The `<model>` element specifies the [kind of model](../getting_started/add_models.md) you want to run.
	- `general-en`: models trained on general domains in English.
	- `medical-en`: models trained on medical domains in English.
* The `<language>` element specifies the language of the models.
	- `en` - English.
* The `<reader>` element contains information about the [data format](data_format.md).
	- The `type` attribute specifies the type of the data format: r`aw|line|column`.
		+ The `raw` type accepts texts in any format: `<reader type="raw">`.
		+ The `line` type requires each sentence to be in one line: `<reader type="line">`.
		+ The `column` type requires each field to be in one column: `<reader type="column">`.
	- When the `column` type is used, `<column>` elements need to be specified.
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