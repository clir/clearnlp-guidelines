# Named Entity Recognition

Our named entity recognizer uses gazetteers extracted from [DBPedia](http://dbpedia.org) and various distributional semantics such as brown clusters and word embeddings. It processes about 23K tokens per second on an Intel Xeon 2.30GHz machine and shows state-of-the-art accuracy on both coarse-grained and fine-grained entity types. See [how to run command-line tools](../quick_start/command_line_tools.md) for more details about decoding.

* _Paper is under submission_.

## Training

### Configuration

The following shows a sample configuration file: [config\_train_ner.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_train_ner.xml) (see [how to train](../quick_start/train.md)).

```
<configuration>
    <language>english</language>

    <reader type="tsv">
        <column field="id"     index="1"/>
        <column field="form"   index="2"/>
        <column field="lemma"  index="3"/>
        <column field="pos"    index="4"/>
        <column field="feats"  index="5"/>
        <column field="headId" index="6"/>
        <column field="deprel" index="7"/>
        <column field="nament" index="8"/>
    </reader>

    <global>
        <distributional_semantics>brown-rcv1.clean.tokenized-CoNLL03.txt-c1000-freq1.txt.xz</distributional_semantics>
        <named_entity_dictionary>general-en-ner-gazetteer.xz</named_entity_dictionary>
    </global>

	<ner>
        <trainer algorithm="adagrad" type="svm" labelCutoff="4" featureCutoff="2" alpha="0.02" rho="0.1" bias="0" average="false"/>
        <bootstraps>true</bootstraps>
    </ner>
</configuration>
```

### Feature template

The following shows a sample feature template file: [feature\_en_ner.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/features/feature_en_ner.xml) (see [feature template](../formats/feature_template.md)).

```
<!--Feature template for named entity recognition in English -->
<feature_template>
    <!-- 1-gram features -->
	<feature f0="i:f2"/>
	<feature f0="i:f3"/>
	<feature f0="i:f4"/>
	<feature f0="i:m"/>
	<feature f0="i:p"/>
	<feature f0="i:a"/>

	<feature f0="i-2:f3"/>
	<feature f0="i-1:f3"/>
	<feature f0="i+1:f3"/>
	<feature f0="i+2:f3"/>

	<feature f0="i-1:f4"/>
	<feature f0="i+1:f4"/>

	<feature f0="i-1:f2"/>
	<feature f0="i+1:f2"/>
	<feature f0="i-1:p"/>
	<feature f0="i+1:p"/>
	<feature f0="i-1:a"/>
	<feature f0="i+1:a"/>
	<feature f0="i-1:n"/>
	<feature f0="i-2:n"/>

	<!-- 2-gram features -->
	<feature f0="i-1:f3" f1="i:f3"/>
	<feature f0="i:f3"   f1="i+1:f3"/>
	<feature f0="i+1:f3" f1="i+2:f3"/>

	<feature f0="i:f3"   f1="i:p"/>
	<feature f0="i+1:f3" f1="i:p"/>

	<feature f0="i-2:p" f1="i-1:p"/>
	<feature f0="i+1:a" f1="i+2:a"/>

	<!-- 3-gram features -->
	<feature f0="i-3:n" f1="i-2:n" f2="i+1:a"/>
	<feature f0="i+1:a" f1="i+2:a" f2="i+3:a"/>

	<feature f0="i:sf3"   f1="i-1:n" f2="i:p"/>
	<feature f0="i-1:sf3" f1="i-1:n" f2="i-1:p"/>

    <!-- affix features -->
	<feature f0="i:sf3"/>
	<feature f0="i+1:pf3"/>

	<feature f0="i:sf3"   f1="i:f3"/>
	<feature f0="i-1:sf3" f1="i:f3"/>

    <!-- orthographic features -->
	<feature f0="i:orth"/>
	<feature f0="i+1:orth"/>

    <!-- distributional semantics features -->
	<feature f0="i:dsw0"/>
	<feature f0="i+1:dsw0"/>
	<feature f0="i+2:dsw0"/>
	<feature f0="i-2:dsw0"/>

    <feature f0="i_h:m"/>
    <feature f0="i_h:p"/>
</feature_template>
```