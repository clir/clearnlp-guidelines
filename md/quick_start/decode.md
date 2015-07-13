# Decoding

## Command-Line

The following shows the command to run the NLP pipeline for part-of-speech tagging, morphological analysis, dependency parsing,  semantic role labeling and named entity recognition, : `pos`, `morph`, `dep`, `srl`, `ner`.

```
java edu.emory.clir.clearnlp.bin.NLPDecode -mode <mode> -c <filename> -i <filepath> [-ie <string> -oe <string>]

-mode <mode>  : pos|morph|dep|srl|ner
-c <filename> : configuration file (required)
-i <filepath> : input path (required)
-ie <string>  : input file extension (default: *)
-oe <string>  : output file extension (default: cnlp)
```

* Sample configuration files can be found [here](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure) (see below for more details).
* The input path `-i` can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension `-ie` under the specific directory are processed.
* The input file extension `-ie` specifies the extension of the input files. The default value `*` implies files with any extension. This option is used only when the input path `-i` points to a directory.
* The output file extension `-oe` is appended to each input filename, and generates the corresponding output file.

The following command takes the input file ([clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt)) and the configuration file ([config\_decode_dep.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode_dep.xml)), performs the NLP pipeline for dependency parsing (`dep`), and generates the output file ([clearnlp.txt.cnlp](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt.cnlp)).

```
$ java -Xmx5g -XX:+UseConcMarkSweepGC java edu.emory.clir.clearnlp.bin.NLPDecode -mode dep -c config_decode_dep.xml -i sample-raw.txt
Loading distributional semantics.
Loading dependency parsing models.
Loading part-of-speech tagging models.
Decoding:
sample.txt
```

* Make sure to use the [`-XX:+UseConcMarkSweepGC`](http://www.oracle.com/technetwork/java/tuning-139912.html) option for JVM, which reduces the memory usage into a half.
* If you want to run the sematic role labeling pipeline, use [config\_decode_srl.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode_srl.xml) instead.
* If you want to run the named entity recognition pipeline, use [config\_decode_ner.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode_ner.xml) instead, which takes about 9GB of RAM.
* Add the log4j configuration file ([log4j.properties](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/log4j.properties)) to your classpath.
* Use our [visualization tool](http://nlp.mathcs.emory.edu/clearnlp/demo/demo.html) to view the output.

## Configuration

The following describes the specifications of the [configuration files](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/).

| Element | Description |
| :-----: | :---------- |
| `<language>` | Specifies the language of the models.<ul><li>See [TLanguage](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/util/lang/TLanguage.java) for all supported languages.</li></ul> |
| `<global>` | Specifies the lexicons used globally across different components.<ul><li>`distributional_semantics`: distributional semantics (e.g., brown clusters, word embeddings).</li><li>`named_entity_dictionary `: named entity dictionary.</li></ul> |
| `<model>` | Specifies the model file of each component.<ul><li>See [NLPMode](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/component/utils/NLPMode.java) for all supported components.</li><li>See [How to add models](../quick_start/models.md) for more details about the model files.</li></ul> |
| `<reader>` | Specifies the data format of the input files.<ul><li>`type` specifies the type of the [data format](../formats/data_format.md):<br>&#9702; `raw`: accepts texts in any format.<br>&#9702; `line`: requires each sentence to be in one line.<br>&#9702; `tsv `: requires each field to be in one column delimited by tabs.</li><li>When `tsv ` is used, `<column>` must be specified.<br>&#9702; `index` specifies the index of the field, starting at 1.<br>&#9702; `field` specifies the name of the field.<br>&nbsp;&nbsp;&nbsp;&#8226; `form`: word form.</li></ul> |
| `<dep>` | Specifies the configuration of dependency parsing.<ul><li>`root_label`: label of the root node.</li><li>`beam_size`: beam size for selectional branching.</li></ul> |
