# Part-of-speech Tagger
Our part-of-speech tagger uses the generalized model of our previous approach, dynamic model selection, which is no longer used because the generalized model by itself performs as well as the dynamic model selection approach for most real-life applications and takes only 50% of RAM. Our POS tagger processes about 39K tokens per second on an Intel Xeon 2.57GHz machine and shows state-of-the-art accuracy, especially on out-of-domain data. See the following paper for more details about our tagging approach.

* [Fast and Robust Part-of-Speech Tagging Using Dynamic Model Selection](http://aclweb.org/anthology-new/P/P12/P12-2071.pdf), Jinho D. Choi, Martha Palmer, Proceedings of the 50th Annual Meeting of the Association for Computational Linguistics (ACL'12), 363-367, Jeju, Korea, 2012.

### Decoding
A dictionary and a part-of-speech tagging model must be added before running the POS tagger. See the [how to add models](../getting_started/add_models.md) page for the instructions of adding these models to your system.

	java com.clearnlp.nlp.engine.NLPDecode -z pos -c <filename> -i <filepath> [-ie <regex> -oe <string>]
	 
	 -c <filename> : configuration file (required)
	 -i <filepath> : input path (required)
	 -ie <regex> : input file extension (default: .*)
	 -oe <string> : output file extension (default: labeled)
	 
* Here is a sample configuration file: [config\_en\_dep.xml](https://github.com/clearnlp/clearnlp/blob/master/src/main/resources/configure/config_en_pos.xml), or you can see the [configuration page](../formats/configuration_file_format.md).

		<configuration>
		    <model>general-en</model>
		    <language>en</language>
		    
		    <reader type="raw">
		        <column index="1" field="form"/>
		    </reader>
		</configuration>
		
* The input path (`-i`) can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension (`-ie`) under the specific directory are processed.
* The input file extension (`-ie`) can be either a string or a [regular expression](http://docs.oracle.com/javase/6/docs/api/java/util/regex/Pattern.html) specifying the extension of the input files. The default value (`.*`) implies files with any extension. This option is used only when the input path (`-i`) points to a directory.
* The output file extension (`-oe`) gets appended to input filenames, and used to generate corresponding output files.

he following command takes an input file ([iphone5.txt](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/iphone5.txt)) and generates an output file ([iphone5.txt.pos](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/iphone5.txt.pos)) in the [morph format](../formats/data_format.md); our POS tagger generates the POS tag and the lemma of each token simultaneously. Please make sure to use the [-XX:+UseConcMarkSweepGC](http://www.oracle.com/technetwork/java/javase/gc-tuning-6-140523.html) option for JVM, which reduces the memory usage into a half.

	java -XX:+UseConcMarkSweepGC -Xmx1g com.clearnlp.nlp.engine.NLPDecode -z pos -c config_en_pos.xml -i iphone5.txt -oe pos
	
### Training
Here are some guidelines for training ClearNLP components:

* [Add components to ClearNLP](../training/add_component_to_clearnlp.md)
* [Feature Extraction] (../training/FeatureExtraction.md)

If you are experience any problem, please feel free to contatct the owner of ClearNLP: [support@clearnlp.com](mailto:support@clearnlp.com)