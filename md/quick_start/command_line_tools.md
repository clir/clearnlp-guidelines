# Command-Line Tools

## Contents

* [Decoding](#decoding).
* [Training](#training).

## Decoding

The following shows the command to run the NLP pipeline for part-of-speech tagging, morphological analysis, dependency parsing, or semantic role labeling: `pos`, `morph`, `dep`, `srl`.

```
java edu.emory.clir.clearnlp.bin.NLPDecode -mode <mode> -c <filename> -i <filepath> [-ie <string> -oe <string>]

-mode <mode>  : pos|morph|dep|srl
-c <filename> : configuration file (required)
-i <filepath> : input path (required)
-ie <string>  : input file extension (default: *)
-oe <string>  : output file extension (default: cnlp)
```

* A sample configuration file can be found here: [config_decode.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode.xml) (see [configuraiton format](../formats/configuration_format.md#decoding)).
* The input path `-i` can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension `-ie` under the specific directory are processed.
* The input file extension `-ie` specifies the extension of the input files. The default value `*` implies files with any extension. This option is used only when the input path `-i` points to a directory.
* The output file extension `-oe` is appended to each input filename, and generates the corresponding output file.

The following command takes the input file ([clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt)) and the configuration file ([config_decode.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode.xml)), performs the NLP pipeline for dependency parsing (`dep`), and generates the output file ([clearnlp.txt.cnlp](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt.cnlp)).

```
$ java -Xmx4g -XX:+UseConcMarkSweepGC java edu.emory.clir.clearnlp.bin.NLPDecode -mode dep -c config_decode.xml -i clearnlp.txt
Loading dependency parsing models.
Loading part-of-speech tagging models.
Decoding:
clearnlp.txt
```

* Make sure to use the [`-XX:+UseConcMarkSweepGC`](http://www.oracle.com/technetwork/java/tuning-139912.html) option for JVM, which reduces the memory usage into a half.
* Add the log4j configuration file ([log4j.properties](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/log4j.properties)) to your classpath.
* Use our [visualization tool](http://nlp.mathcs.emory.edu/clearnlp/demo/demo.html) to view the output.

## Training

The following shows the command to train the model for [part-of-speech tagging](../components/pos_tagging.md#training), dependency parsing, or semantic role labeling: `pos`, `dep`, `srl`. See more details about individual components in their pages.

```
java edu.emory.clir.clearnlp.bin.NLPTrain -mode <mode> -c <filename> -f <filename> -t <filepath> -d <filepath> [-m <filename> -te <string> -de <string>]

-mode <mode>  : pos|dep|srl
-c <filename> : configuration file (required)
-f <filename> : feature template files (required)
-m <filename> : model filename (optional)
-t <filepath> : training path (required)
-d <filepath> : development path (required)
-te <string>  : training file extension (default: *)
-de <string>  : development file extension (default: *)
```

* A sample configuration file can be found here: [config_train.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_train.xml) (see [configuraiton format](../formats/configuration_format.md#training)).
* Sample feature template files can be found [here](https://github.com/clir/clearnlp/tree/master/src/main/resources/features) (see [feature template](../formats/feature_template.md)).
* If the model filename `-m` is specified, the final model is saved.
* The tarining or development path `-t|d` can point to either a file or a directory. When the path points to a file, only the specific file is processed. When the path points to a directory, all files with the file extension `-te|de` under the specific directory are processed.
* The training or development file extensions `-te|de` specifies the extensions of the training and development files. The default value `*` implies files with any extension. This option is used only when the training or development path `-t|d` points to a directory.

The following command takes the training file ([wsj_0001.parse.dep](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/wsj_0001.parse.dep)), the development file ([clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt)), and the configuration file ([config\_train_sample.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_train_sample.xml)), and generates a dependency parsing (`dep`) model `dummy-dep.xz`.

```
$ java -Xmx10g -XX:+UseConcMarkSweepGC java edu.emory.clir.clearnlp.bin.NLPTrain -mode dep -c config_train_sample.xml -f feature_en_dep.xml -t wsj_0001.parse.dep -d clearnlp.txt.cnlp -m dummy-dep.xz
```

* Make sure to use the [`-XX:+UseConcMarkSweepGC`](http://www.oracle.com/technetwork/java/tuning-139912.html) option for JVM, which reduces the memory usage into a half.
* Add the log4j configuration file ([log4j.properties](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/log4j.properties)) to your classpath.
