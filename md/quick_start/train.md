# Training

## Command-Line

The following shows the command to train the model for [part-of-speech tagging](../components/pos_tagging.md), [dependency parsing](../components/dependency_parsing.md), [named entity recognition](../components/named_entity_recognition.md), or semantic role labeling: `pos`, `dep`, `ner`, `srl`.

```
java edu.emory.clir.clearnlp.bin.NLPTrain -mode <mode> -c <filename> -f <filename> -t <filepath> -d <filepath> [-m <filename> -te <string> -de <string>]

-mode <mode>  : pos|dep|ner|srl
-c <filename> : configuration file (required)
-f <filename> : feature template files (required)
-m <filename> : model filename (optional)
-t <filepath> : training path (required)
-d <filepath> : development path (required)
-te <string>  : training file extension (default: *)
-de <string>  : development file extension (default: *)
```

* Sample configuration files can be found [here](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure) (see below for more details).
* Sample feature template files can be found [here](https://github.com/clir/clearnlp/tree/master/src/main/resources/features) (see [feature template](../formats/feature_template.md)).
* If the model filename `-m` is specified, the final model is saved.
* The tarining or development path `-t|d` can point to either a file or a directory. When the path points to a file, only the specific file is processed. When the path points to a directory, all files with the file extension `-te|de` under the specific directory are processed.
* The training or development file extensions `-te|de` specifies the extensions of the training and development files. The default value `*` implies files with any extension. This option is used only when the training or development path `-t|d` points to a directory.

The following command takes the training file ([wsj_0001.parse.dep](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/wsj_0001.parse.dep)), the development file ([clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt)), and the configuration file ([config\_train_dep.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_train_dep.xml)), and generates a dependency parsing (`dep`) model `dummy-dep.xz`.

```
$ java -Xmx10g -XX:+UseConcMarkSweepGC java edu.emory.clir.clearnlp.bin.NLPTrain -mode dep -c config_train_sample.xml -f feature_en_dep.xml -t wsj_0001.parse.dep -d clearnlp.txt.cnlp -m dummy-dep.xz
```

* Make sure to use the [`-XX:+UseConcMarkSweepGC`](http://www.oracle.com/technetwork/java/tuning-139912.html) option for JVM, which reduces the memory usage into a half.
* Add the log4j configuration file ([log4j.properties](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/log4j.properties)) to your classpath.

## Configuration

The following describes the specifications of the [configuration files](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/). See more details about the individual components in their pages.

| Element | Description |
| :-----: | :---------- |
| `<language>` | Specifies the language of the models.<ul><li>See [TLanguage](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/util/lang/TLanguage.java) for all supported languages.</li></ul> |
| `<global>` | Specifies the lexicons used globally across different components.<ul><li>`distributional_semantics`: distributional semantics (e.g., brown clusters, word embeddings).</li><li>`named_entity_dictionary `: named entity dictionary.</li></ul> |
| `<reader>` | Specifies the [data format](../formats/data_format.md) of the training files. |
| `<column>` | Specifies the field information.<ul><li>`index` specifies the index of the field, starting at 1.</li><li>`field` specifies the name of the field.</li>&#9702; `id`: node ID.<br>&#9702; `form`: word form.<br>&#9702; `lemma`: lemma.<br>&#9702; `pos`: part-of-speech tag.<br>&#9702; `feats`: extra features.<br>&#9702; `headId`: head node ID.<br>&#9702; `deprel`: dependency label.<br>&#9702; `nament`: named entity tag.<br>&#9702; `sheads`: semantic heads.</ul> |
| `<trainer>` | Specifies the training algorithm and its parameters.<ul><li>`algorithm`: `adagrad` for AdaGrad, `liblinear`for Liblinear.</li><li>`type`: `svm` for hinge loss classification, `lr`for logistic regression.</li><li>`labelCutoff`: count threshold for labels appearing less than `N` times.</li><li>`featureCutoff`: count threshold for features appearing less than `N` times.</li><li>`average`: if `true`, apply averaging to online learning.</li><li>`alpha`: learning rate (AdaGrad).</li><li>`rho`: ridge to keep the inverse covariance well-conditioned (AdaGrad).</li></ul>| 
| `<bootstraps>` | If `true`, use bootstrap iterations for training sequences. | 
