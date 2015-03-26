# Part-of-Speech Tagging

Our part-of-speech tagger uses the generalized model of our previous approach, dynamic model selection, which is no longer used because the generalized model by itself performs as well as the dynamic model selection approach for most real-life applications and takes only 50% of memory and disk space. Our POS tagger processes about 80K tokens per second on an Intel Xeon 2.30GHz machine and shows state-of-the-art accuracy, especially on out-of-domain data. See [how to run command-line tools](../quick_start/command_line_tools.md) for more details about decoding and training.

* [Fast and Robust Part-of-Speech Tagging Using Dynamic Model Selection](http://aclweb.org/anthology-new/P/P12/P12-2071.pdf), Jinho D. Choi, Martha Palmer, Proceedings of the 50th Annual Meeting of the Association for Computational Linguistics (ACL'12), 363-367, Jeju, Korea, 2012.

## Training

### Configuration

The following shows a sample configuration file for training: [config\_train_pos.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_train_pos.xml).

```
<configuration>
    <language>english</language>

    <reader type="tsv">
        <column index="2" field="form"/>
        <column index="4" field="pos"/>
        <column index="5" field="feats"/>
    </reader>

    <pos>
        <trainer algorithm="adagrad" type="svm" labelCutoff="4" featureCutoff="3" alpha="0.02" rho="0.1" bias="0" average="false"/>
        <ambiguity_class_threshold>0.4</ambiguity_class_threshold>
        <document_frequency_cutoff>2</document_frequency_cutoff>
        <document_size>1500</document_size>
        <bootstraps>true</bootstraps>
    </pos>
</configuration>
```

| Element | Description |
| :-----: | :---------- |
| `<language>` | Specifies the [language](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/util/lang/TLanguage.java). |
| `<reader>` | Specifies the [data format](../formats/data_format.md) of the training files. |
| `<column>` | Specifies the field information.<ul><li>`index` specifies the index of the field, starting at 1.</li><li>`field` specifies the name of the field.</li>&#9702; `form`: word form.<br>&#9702; `pos`: part-of-speech tag.<br>&#9702; `feats`: extra features.</ul> |
| `<pos>` | Specifies the configuration for part-of-speech tagging.<ul><li>`ambiguity_class_threshold`: collect only ambiguity classes whose likelihoods are greater than this threshold (exclusive).</li><li>`document_frequency_cutoff `: use features extracted from only words whose document frequencies are greater than this cutoff (exclusive).</li><li>`document_size`: consider this many number of trees as one document.</li></ul> |
| `<trainer>` | Specifies the training algorithm  (see [configuration format](../formats/configuration_format.md#training)). |
| `<bootstraps>` | if `true`, use bootstrapping for sequence classification. | 
