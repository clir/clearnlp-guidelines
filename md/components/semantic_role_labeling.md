# Semantic Role Labeler
Our semantic role labeler uses a higher-order argument pruning algorithm that significantly improves recall from the first-order argument pruning algorithm, yet keeps a similar labeling complexity in practice. Our labeler takes about 0.45 milliseconds for labeling all arguments of each predicate on an Intel Xeon 2.57GHz machine and shows state-of-the-art accuracy compared to other dependency-based labeling approaches. See [how to run command-line tools](../quick_start/command_line_tools.md) for more details about decoding.

* [Optimization of Natural Language Processing Components for Robustness and Scalability](http://www.mathcs.emory.edu/~choi/doc/thesis-2012.pdf), Jinho D. Choi, Ph.D. Thesis, University of Colorado Boulder, Computer Science and Cognitive Science, 2012.
* [Transition-based Semantic Role Labeling Using Predicate Argument Clustering](http://aclweb.org/anthology/W11-0906), Jinho D. Choi, Martha Palmer, In Proceedings of the ACL Workshop on Relational Models of Semantics (RELMS'11), 37–45, 2011.

## Training

### Configuration

The following shows a sample configuration file: [config\_train_srl.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_train_srl.xml) (see [how to train](../quick_start/train.md)).

```
<configuration>
    <language>english</language>

    <global>
        <distributional_semantics>brown-rcv1.clean.tokenized-CoNLL03.txt-c1000-freq1.txt.xz</distributional_semantics>
    </global>

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

    <srl>
        <trainer algorithm="adagrad" type="svm" labelCutoff="4" featureCutoff="2" alpha="0.02" rho="0.1" average="false"/>
        <trainer algorithm="adagrad" type="svm" labelCutoff="4" featureCutoff="3" alpha="0.02" rho="0.1" average="false"/>
        <bootstraps>true</bootstraps>
        <max_depth>4</max_depth>
        <max_height>3</max_height>
    </srl>
</configuration>
```

| Element | Description |
| :-----: | :---------- |
| `<srl>` | Specifies the configuration for semantic role labeling.<ul><li>`max_depth`: the maximum depth of descendents to be considered for argument candidates.</li><li>`max_height`: the maximu height of ancestors to be considered for argument candidates.</li> |

### Feature template

The following shows a sample feature template file: [feature\_en_srl.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/features/feature_en_srl.xml) (see [feature template](../formats/feature_template.md)).

```
<!--Feature template for semantic role labeling in English -->
<feature_template>
	<!-- basic features -->
	<feature f0="i:m"/>
	<feature f0="j:m"/>
	<feature f0="i:p"/>
	<feature f0="j:p"/>

	<feature f0="i:p" f1="i:d"/>
	<feature f0="j:p" f1="j:d"/>

	<feature f0="i:m" f1="j:p"/>
	<feature f0="i:p" f1="j:m"/>
	<feature f0="i:m" f1="j:m"/>
	<feature f0="i:d" f1="j:d"/>

	<!-- 1-gram features -->
	<feature f0="j-1:p"/>
	<feature f0="j_lmd:p"/>
	<feature f0="j_lns:p"/>
	<feature f0="j_rns:p"/>

	<feature f0="j-1:m"/>
	<feature f0="j+1:m"/>
	<feature f0="j_rns:m"/>
	<feature f0="j_rmd:m"/>

	<feature f0="i-1:p"/>
	<feature f0="i+1:p"/>
	<feature f0="i_h:p"/>
	<feature f0="i_lmd:p"/>
	<feature f0="i_rmd:p"/>

	<feature f0="i-1:m"/>
	<feature f0="i+1:m"/>

	<!-- 2-gram features -->
	<feature f0="i_lmd:p" f1="i:p"/>
	<feature f0="i+1:p"   f1="i:m"/>

	<feature f0="j_rns:p" f1="j:p"/>
	<feature f0="j_lmd:p" f1="j:p"/>
	<feature f0="j_lmd:m" f1="j:p"/>
	<feature f0="j_lns:m" f1="j:p"/>
	<feature f0="j_rmd:p" f1="j:m"/>

	<feature f0="j_h:m"   f1="j:d"/>
	<feature f0="j_lmd:m" f1="j:d"/>
	<feature f0="j_rmd:m" f1="j:d"/>
	<feature f0="j_lmd:p" f1="j:d"/>
	<feature f0="j_rmd:p" f1="j:d"/>

	<!-- path features -->
	<feature f0="j:path.p"/>
	<feature f0="j:path.d" f1="i:p"/>
	<feature f0="j:path.t" f1="i:p"/>

	<!-- subcategorization features -->
	<feature f0="i:subcat.l.d"/>
	<feature f0="i:subcat.r.d"/>
	<feature f0="i:subcat.r.d" f1="i:m"/>
	<feature f0="i_h:subcat.l.d"/>
	<feature f0="i_h:subcat.r.d"/>

	<!-- argument features -->
	<feature f0="i:m" f1="i:argn0"/>
	<feature f0="i:m" f1="i:argn1"/>
	<feature f0="i:m" f1="i:argn0" f2="i:argn1"/>

	<!-- extra features -->
	<feature f0="i:ds.d"/>
	<feature f0="j:t" note="distance from P"/>

	<feature f0="i:dsw0"/>
    <feature f0="j:dsw0"/>

	<!-- binary features -->
	<feature f0="j:b0" note="j is a dependent of P"/>
	<feature f0="j:b1" note="P is a dependent of j"/>
</feature_template>
```
