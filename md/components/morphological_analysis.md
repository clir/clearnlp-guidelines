# Morphological Analyzer
Our morphological analyzer generates lemmas (root forms) of word tokens. It is a rule-based analyzer inspired by the [WordNet morphy](http://wordnet.princeton.edu/man/morphy.7WN.html) although it uses a larger dictionary gathered from various sources and slightly more advanced heuristics. Furthermore, our analyzer normalizes numbers, redundant punctuation, URLs, etc. (see the examples below), which is found to be useful for several NLP tasks. Currently, our morphological analyzer supports only English.

### Decoding
A dictionary must be added before running the morphological analyzer. See the how to add models page for the instructions of adding our dictionary to your system.

	java com.clearnlp.nlp.engine.NLPDecode -z morph -c <filename> -i <filepath> [-ie <regex> -oe <string>]
	 
	 -c <filename> : configuration file (required)
	 -i <filepath> : input path (required)
	 -ie <regex> : input file extension (default: .*)
	 -oe <string> : output file extension (default: labeled)
	 
* Here is a sample configuration file: [config\_en\_morph.xml](https://github.com/clearnlp/clearnlp/blob/master/src/main/resources/configure/config_en_morph.xml), or you can see the [configuration page](../formats/configuration_file_format.md).

		<configuration>
		    <model>general-en</model>
		    <language>en</language>

		    <reader type="column">
		        <column index="1" field="form"/>
		        <column index="2" field="pos"/>
		    </reader>
		</configuration>

* The input path (`-i`) can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension (`-ie`) under the specific directory are processed.
* The input file extension (`-ie`) can be either a string or a [regular expression](http://docs.oracle.com/javase/6/docs/api/java/util/regex/Pattern.html) specifying the extension of the input files. The default value (`.*`) implies files with any extension. This option is used only when the input path (`-i`) points to a directory.
* The output file extension (`-oe`) gets appended to input filenames, and used to generate corresponding output files.

The following command takes an input file ([morph-sample.txt](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/morph-sample.txt)) and generates an output file ([morph-sample.txt.morph](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/morph-sample.txt.morph)) in the [morph format](../formats/data_format.md).

### Normalization
Ordinals and cardinals are normalized to `#ord#` and `#crd#`, respectively.

	1st         CD    #ord#
	12nd        CD    #ord#
	23rd        CD    #ord#
	34th        CD    #ord#
	first       CD    #ord#
	third       CD    #ord#
	fourth      CD    #ord#
	zero        CD    #crd#
	ten         CD    #crd#
	eleven      CD    #crd#
	fourteen    CD    #crd#
	
Numeric expressions are normalized to 0.

	10%                    XX    0
	$10                    XX    0
	A.01                   XX    a.0
	A:01                   XX    a:0
	A/01                   XX    a/0
	.01                    XX    0
	12.34                  XX    0
	12,34,56               XX    0
	12-34-56               XX    0
	12/34/46               XX    0
	$10.23,45:67-89/10%    XX    0
	
Redundant punctuation chracters are collapsed.

	.!?-*=~,                                                    XX    .!?-*=~,
	..!!??--**==~~,,                                            XX    ..!!??--**==~~,,
	...!!!???---***===[[user:jdchoi77]],,,                      XX    ..!!??--**==~~,,
	....!!!!????----****====[[user:jdchoi77|1384441338]],,,,    XX    ..!!??--**==~~,,
	
URLs are normalized to `#url#`.

	http://www.google.com         XX    #url#
	www.google.com                XX    #url#
	mailto:somebody@google.com    XX    #url#
	some-body@google+.com         XX    #url#
	
### Training
Here are some guidelines for training ClearNLP components:

* [Add components to ClearNLP](../training/add_component_to_clearnlp.md)
* [Feature Extraction] (../training/FeatureExtraction.md)

If you are experience any problem, please feel free to contatct the owner of ClearNLP: [support@clearnlp.com](mailto:support@clearnlp.com)