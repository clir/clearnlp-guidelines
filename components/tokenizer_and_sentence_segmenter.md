# Tokenizer and Sentence Segmenter
Our tokenizer takes a raw text and splits words by their morphological aspects. It also gives an option of grouping tokens into sentences. Our tokenizer is based on the [LDC](https://www.ldc.upenn.edu/) tokenizer used for creating English Treebanks although it uses more robust heuristics. Here are some key features about our tokenizer.

* Emoticons are recognized as one unit (e.g., :-), ^_^).
* Hyperlinks are recognized as one unit (google.com, jinho@gmail.com, index.html).
* Numbers consisting of punctuation are recognized as one unit (e.g., 0.1, 2/3).
* Repeated punctuation are grouped together (e.g., ---, ...).
* Abbreviations are recognized as one unit (e.g., Prof., Ph.D).
* File extensions are not tokenized (e.g., clearnlp.zip, tokenizer.doc).
* Units are tokenized (e.g., 1 kg, 2 cm).
* Usernames including periods are recognized as one unit (e.g., jinho.choi).

Currently our tokenizer supports only English.

### Decoding
A dictionary must be added before running the tokenizer. See the [how to add models](../getting_started/add_models.md) page for the instructions of adding our dictionary to your system.

	java com.clearnlp.run.Tokenizer -i <filepath> [-ie <regex> -oe <string> -if <string> -of <string> -l <language> -twit]
	 
	 -i <filepath>   : input path (required)
	 -ie <regex>     : input file extension (default: .*)
	 -oe <string>    : output file extension (default: tok)
	 -if <string>    : input format (default: raw)
	 -of <string>    : input format (default: line)
	 -l <language>   : language (default: en)
	 -twit <boolean> : if set, do not tokenize special punctuation used in twitter
	 
* The input path (`-i`) can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension (`-ie`) under the specific directory are processed.
* The input file extension (`-ie`) can be either a string or a r[egular expression](http://docs.oracle.com/javase/6/docs/api/java/util/regex/Pattern.html) specifying the extension of the input files. The default value (`.*`) implies files with any extension. This option is used only when the input path (`-i`) points to a directory.
* The output file extension (`-oe`) gets appended to input filenames, and used to generate corresponding output files.
* The input format can be either `raw` or `line`. If the raw format is chosen, the tokenizer automatically groups tokens into sentences. If the line format is chosen, the tokenizer treats each line as one sentence (see the [data format](../formats/data_format.md) page).
* The output format can be either `line` or `tok` (see the [data format](../formats/data_format.md) page).
* The language (`-l`) indicates the language of the constituent trees to be convereted. Currently, our conversion supports only English (`en`).
* If the `twit` option is used, special punctuation such as & and # used in twitter are not tokenized.

The following command takes a sample input file ([iphone5.txt](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/iphone5.txt)) and generates an output file ([iphone5.txt.tok](https://github.com/clearnlp/clearnlp-demo/blob/master/src/main/resources/sample/iphone5.txt.tok)) in the [line format](../formats/data_format.md).

	java com.clearnlp.run.Tokenizer -i iphone5.txt
	
### Training
Here are some guidelines for training ClearNLP components:

* [Add components to ClearNLP](../training/add_component_to_clearnlp.md)
* [Feature Extraction] (../training/FeatureExtraction.md)

If you are experience any problem, please feel free to contatct the owner of ClearNLP: [support@clearnlp.com](mailto:support@clearnlp.com)