# Dependency Parsing

Our dependency parser uses a transition-based, non-projective parsing algorithm coupled with bootstrapping. It shows a linear-time speed for both projective and non-projective parsing, processing about 15K tokens per second on an Intel Xeon 2.30GHz machine, and shows state-of-the-art accuracy for greedy parsing. See [how to run command-line tools](../quick_start/command_line_tools.md) for more details about decoding.

* [Transition-based Dependency Parsing with Selectional Branching](http://aclweb.org/anthology/P/P13/P13-1104.pdf), Jinho D. Choi, Andrew McCallum, Proceedings of the 51st Annual Meeting of the Association for Computational Linguistics (ACL'13), 1052-1062, Sofia, Bulgaria, 2013.
* [Getting the Most out of Transition-based Dependency Parsing](http://aclweb.org/anthology-new/P/P11/P11-2121.pdf), Jinho D. Choi, Martha Palmer, Proceedings of the 49th Annual Meeting of the Association for Computational Linguistics: Human Language Technologies (ACL:HLT'11), 687-692, Portland, Oregon, 2011.

## Training

### Configuration

The following shows a sample configuration file: [config\_train_dep.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_train_dep.xml) (see [how to train](../quick_start/train.md)).

```
<configuration>
    <language>english</language>

    <global>
        <distributional_semantics>brown-rcv1.clean.tokenized-CoNLL03.txt-c1000-freq1.txt.xz</distributional_semantics>
    </global>

    <reader type="tsv">
        <column index="1"  field="id"/>
        <column index="2"  field="form"/>
        <column index="4"  field="lemma"/>
        <column index="6"  field="pos"/>
        <column index="8"  field="feats"/>
        <column index="9"  field="headId"/>
        <column index="10" field="deprel"/>
    </reader>

    <dep>
        <trainer algorithm="adagrad" type="svm" labelCutoff="4" featureCutoff="3" alpha="0.02" rho="0.1" average="false"/>
        <evaluate_punctuation>false</evaluate_punctuation>
        <bootstraps>true</bootstraps>
        <root_label>root</root_label>
        <beam_size>1</beam_size>
    </dep>
</configuration>
```

| Element | Description |
| :-----: | :---------- |
| `<dep>` | Specifies the configuration for dependency parsing.<ul><li>`evaluate_punctuation`: if `true`, include punctuation for evaluation.</li><li>`beam_size`: the beam size for selectional branching during evaluation.</li><li>`root_label `: the root label.</li></ul> |

### Feature template

The following shows a sample feature template file: [feature\_en_dep.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/features/feature_en_dep.xml) (see [feature template](../formats/feature_template.md)).

```
<!--Feature template for dependency parsing in English -->
<feature_template>
    <!-- basic features -->
    <feature f0="i:m"/>
    <feature f0="j:m"/>
    <feature f0="i:p"/>
    <feature f0="j:p"/>

    <feature f0="i:p" f1="i:m"/>
    <feature f0="j:p" f1="j:m"/>

    <feature f0="i:p" f1="j:p"/>
    <feature f0="i:p" f1="j:m"/>
    <feature f0="i:m" f1="j:p"/>
    <feature f0="i:m" f1="j:m"/>

    <!-- 1-gram features -->
    <feature f0="k-1:m"/>
    <feature f0="i-1:m"/>
    <feature f0="i+1:m"/>
    <feature f0="j-2:m"/>
    <feature f0="j-1:m"/>
    <feature f0="j+1:m"/>
    <feature f0="j+2:m"/>

    <feature f0="i-2:p"/>
    <feature f0="i-1:p"/>
    <feature f0="i+1:p"/>
    <feature f0="i+2:p"/>
    <feature f0="j-1:p"/>
    <feature f0="j+1:p"/>

    <!-- 2-gram features -->
    <feature f0="j+1:p" f1="i:p"/>
    <feature f0="k-1:p" f1="i:p"/>
    <feature f0="k-1:p" f1="j:p"/>

    <feature f0="j-1:p" f1="i:m"/>
    <feature f0="j+1:p" f1="i:m"/>
    <feature f0="j+1:p" f1="j:m"/>
    <feature f0="j+1:m" f1="i:p"/>
    <feature f0="j+1:m" f1="j:p"/>

    <feature f0="i+1:m" f1="i:m"/>
    <feature f0="i+1:m" f1="j:m"/>

    <!-- 3-gram features -->
    <feature f0="i-2:p" f1="i-1:p" f2="i:p"/>
    <feature f0="i-1:p" f1="i:p"   f2="i+1:p"/>
    <feature f0="j-1:p" f1="j:p"   f2="j+1:p"/>
    <feature f0="j:p"   f1="j+1:p" f2="j+2:p"/>

    <feature f0="k-2:p" f1="i:p" f2="j:p"/>
    <feature f0="i-1:p" f1="i:p" f2="j:p"/>
    <feature f0="i+1:p" f1="i:p" f2="j:p"/>
    <feature f0="j-2:p" f1="i:p" f2="j:p"/>
    <feature f0="j-1:p" f1="i:p" f2="j:p"/>
    <feature f0="j+1:p" f1="i:p" f2="j:p"/>
    <feature f0="j+2:p" f1="i:p" f2="j:p"/>
    <feature f0="j+3:p" f1="i:p" f2="j:p"/>

    <!-- valency features -->
    <feature f0="i:va" f1="i:m"/>
    <feature f0="j:va" f1="j:m"/>

    <!-- 2nd-order features -->
    <feature f0="i:d"/>
    <feature f0="j:d"/>
    <feature f0="i_lmd:d"/>

    <feature f0="i_h:m"/>
    <feature f0="i_rmd:m"/>
    <feature f0="j_lmd:m"/>

    <feature f0="i_h:p"/>
    <feature f0="i_rmd:p"/>
    <feature f0="j_lmd:p"/>

    <feature f0="i:d" f1="i:p"/>
    <feature f0="i:d" f1="j:p"/>
    <feature f0="i:d" f1="i:m"/>
    <feature f0="i:d" f1="j:m"/>

    <feature f0="i:d"     f1="i:p" f2="j:p"/>
    <feature f0="i_lmd:d" f1="i:p" f2="j:p"/>
    <feature f0="j_lmd:d" f1="i:p" f2="j:p"/>
    <feature f0="i_lns:d" f1="i:p" f2="j:p"/>

    <feature f0="i_lmd:p" f1="i:p" f2="j:p"/>
    <feature f0="i_rmd:p" f1="i:p" f2="j:p"/>
    <feature f0="j_lmd:p" f1="i:p" f2="j:p"/>

    <feature f0="i:d"     f1="j:p" visible="true"/>
    <feature f0="i_lmd:d" f1="j:p" visible="true"/>
    <feature f0="i_rmd:d" f1="j:p" visible="true"/>

    <feature f0="i_h:p"   f1="j:p" visible="true"/>
    <feature f0="i_lmd:p" f1="j:p" visible="true"/>
    <feature f0="i_rmd:p" f1="j:p" visible="true"/>

    <!-- 3rd-order features -->
    <feature f0="i_h:d"/>
    <feature f0="j_h:d"/>
    <feature f0="i_lmd2:d"/>

    <feature f0="i_h2:m"/>
    <feature f0="i_rmd2:m"/>
    <feature f0="j_lmd2:m"/>

    <feature f0="i_h2:p"/>
    <feature f0="i_rmd2:p"/>
    <feature f0="j_lmd2:p"/>

    <feature f0="i_h:d" f1="i:p"/>
    <feature f0="i_h:d" f1="j:p"/>
    <feature f0="i_h:d" f1="j:m"/>

    <feature f0="i_h:d"    f1="i:p" f2="j:p"/>
    <feature f0="i_lmd2:d" f1="i:p" f2="j:p"/>
    <feature f0="j_lmd2:d" f1="i:p" f2="j:p"/>
    <feature f0="i_lns2:d" f1="i:p" f2="j:p"/>

    <feature f0="i_lmd2:p" f1="i:p" f2="j:p"/>
    <feature f0="j_lmd2:p" f1="i:p" f2="j:p"/>
    <feature f0="i_rmd2:p" f1="i:p" f2="j:p"/>

    <feature f0="i_lmd2:p" f1="i_lmd:p" f2="i:p"/>

    <!-- distributional semantics features -->
    <feature f0="i:dsw0"/>
    <feature f0="j:dsw0"/>
    <feature f0="i+1:dsw0"/>
    <feature f0="j+1:dsw0"/>

    <!-- binary features -->
    <feature f0="i:b0" note="stack is the first token"/>
    <feature f0="j:b1" note="input is the last  token"/>
</feature_template>
```