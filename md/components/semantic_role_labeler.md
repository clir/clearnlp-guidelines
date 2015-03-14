# Semantic Role Labeler
Our semantic role labeler uses a higher-order argument pruning algorithm that significantly improves recall from the first-order argument pruning algorithm, yet keeps a similar labeling complexity in practice. Our labeler takes about 0.45 milliseconds for labeling all arguments of each predicate on an Intel Xeon 2.57GHz machine and shows state-of-the-art accuracy compared to other dependency-based labeling approaches. See Chapter 6 of the following paper for more details about our labeling approach.

* [Optimization of Natural Language Processing Components for Robustness and Scalability](https://dl.dropbox.com/u/15060914/publications/thesis-choijd.pdf), Jinho D. Choi, Ph.D. Thesis, University of Colorado Boulder, Computer Science and Cognitive Science, 2012.

### Decoding
A dictionary, a part-of-speech tagging model, a dependency parsing model, and a semantic role labeling model must be added before running the semantic role labeler. See the h[ow to add models](../formats/data_format.md) page for the instructions of adding these models to your system.

	java com.clearnlp.nlp.engine.NLPDecode -z srl -c <filename> -i <filepath> [-ie <regex> -oe <string>]
	 
	 -c <filename> : configuration file (required)
	 -i <filepath> : input path (required)
	 -ie <regex> : input file extension (default: .*)
	 -oe <string> : output file extension (default: labeled)
	 
* Here is a sample configuration file: [config\_en\_srl.xml](https://github.com/clearnlp/clearnlp/blob/master/src/main/resources/configure/config_en_srl.xml), or you can see the [configuration page](../formats/configuration_file_format.md).

		<configuration>
		    <model>general-en</model>
		    <language>en</language>

		    <reader type="raw">
		        <column index="1" field="id"/>
		        <column index="2" field="form"/>
		        <column index="3" field="lemma"/>
		        <column index="4" field="pos"/>
		        <column index="5" field="feats"/>
		        <column index="6" field="headId"/>
		        <column index="7" field="deprel"/>
		    </reader>
		</configuration>

* The input path (`-i`) can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension (`-ie`) under the specific directory are processed.
* The input file extension (`-ie`) can be either a string or a [regular expression](http://docs.oracle.com/javase/6/docs/api/java/util/regex/Pattern.html) specifying the extension of the input files. The default value (`.*`) implies files with any extension. This option is used only when the input path (`-i`) points to a directory.
* The output file extension (`-oe`) gets appended to input filenames, and used to generate corresponding output files.

The following command takes an input file ([iphone5.txt](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/iphone5.txt)) and generates an output file ([iphone5.txt.srl](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/iphone5.txt.srl)) in the srl format. Please make sure to use the [-XX:+UseConcMarkSweepGC](http://www.oracle.com/technetwork/java/javase/gc-tuning-6-140523.html) option for JVM, which reduces the memory usage into a half.

	java -XX:+UseConcMarkSweepGC -Xmx1g com.clearnlp.nlp.engine.NLPDecode -z srl -c config_en_srl.xml -i iphone5.txt -oe srl
	
### Training
Here are some guidelines for training ClearNLP components:

* [Add components to ClearNLP](../training/add_component_to_clearnlp.md)
* [Feature Extraction] (../training/FeatureExtraction.md)

If you are experience any problem, please feel free to contatct the owner of ClearNLP: [support@clearnlp.com](mailto:support@clearnlp.com)
