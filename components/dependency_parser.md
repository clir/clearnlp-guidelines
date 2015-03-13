# Dependency Parser

Our dependency parser uses a transition-based, non-projective parsing algorithm coupled with bootstrapping. Our parsing algorithm is guaranteed to run in O(n) for projective parsing and in an expected linear time for non-projective parsing. For greedy parsing, it takes about 2ms per sentence on an Intel Xeon 2.57GHz machine
for the generation of both projective and non-projective trees. For non-greedy parsing, it uses selectional branching, which takes about 9ms per sentence, but gives the state-of-the-art accuracy (about 93% of an unlabeled attachment score on WSJ). See the following papers for more details about our parsing approach.

* [Getting the Most out of Transition-based Dependency Parsing](http://aclweb.org/anthology-new/P/P11/P11-2121.pdf), Jinho D. Choi, Martha Palmer, Proceedings of the 49th Annual Meeting of the Association for Computational Linguistics: Human Language Technologies (ACL:HLT'11), 687-692, Portland, Oregon, 2011.
* [Transition-based Dependency Parsing with Selectional Branching](http://aclweb.org/anthology/P/P13/P13-1104.pdf), Jinho D. Choi, Andrew McCallum, Proceedings of the 51st Annual Meeting of the Association for Computational Linguistics (ACL'13), 1052-1062, Sofia, Bulgaria, 2013.

### Decoding
A dictionary, a part-of-speech tagging model, and a dependency parsing model must be added before running the dependency parser. See the [how to add models](getting_started/add_models.md) page for the instructions of adding these models to your system.

	java com.clearnlp.nlp.engine.NLPDecode -z dep -c <filename> -i <filepath> [-ie <regex> -oe <string>]
	 
	 -c <filename> : configuration file (required)
	 -i <filepath> : input path (required)
	 -ie <regex> : input file extension (default: .*)
	 -oe <string> : output file extension (default: labeled)

* Here is a sample configuration file: [config\_en\_dep.xml](https://github.com/clearnlp/clearnlp/blob/master/src/main/resources/configure/config_en_dep.xml), or you can see the [configuration page](../formats/configuration_file_format.md).

		<configuration>
		    <model>general-en</model>
		    <language>en</language>

		    <reader type="raw">
		        <column index="1" field="id"/>
		        <column index="2" field="form"/>
		        <column index="3" field="lemma"/>
		        <column index="4" field="pos"/>
		        <column index="5" field="feats"/>
		    </reader>
		</configuration>
		
* The input path (`-i`) can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension (`-ie`) under the specific directory are processed.
* The input file extension (`-ie`) can be either a string or a regular expression specifying the extension of the input files. The default value (`.*`) implies files with any extension. This option is used only when the input path (`-i`) points to a directory.
* The output file extension (`-oe`) gets appended to input filenames, and used to generate corresponding output files.

The following command takes an input file ([iphone5.txt](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/iphone5.txt)) and generates an output file ([iphone5.txt.dep](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/iphone5.txt.dep)) in the dep format. Please make sure to use the [-XX:+UseConcMarkSweepGC](http://www.oracle.com/technetwork/java/javase/gc-tuning-6-140523.html) option for JVM, which reduces the memory usage into a half.

	java -XX:+UseConcMarkSweepGC -Xmx3g com.clearnlp.nlp.engine.NLPDecode -z dep -c config_en_dep.xml -i iphone5.txt -oe dep
	
### Training
Here are some guidelines for training ClearNLP components:

* [Add components to ClearNLP](../training/add_component_to_clearnlp.md)
* [Feature Extraction] (../training/FeatureExtraction.md)

If you are experience any problem, please feel free to contatct the owner of ClearNLP: [support@clearnlp.com](mailto:support@clearnlp.com)