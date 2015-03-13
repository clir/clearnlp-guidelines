# Constituent-to-Dependency Converter
Our constituent-to-dependency converter takes the [Penn Treebank](http://www.cis.upenn.edu/~treebank/) style constituent trees as input and generates the CLEAR style dependency trees as output. Here are some of the key features of the CLEAR dependency conversion.

* Generates the [Stanford dependency](http://nlp.stanford.edu/software/stanford-dependencies.shtml) labels.
* Allows users to customize their own head-finding rules.
* Produces long-distance dependencies by remapping empty categories in constituent trees.
* Produces secondary dependencies caused by several linguistic phenomena.
* Preserves function tags as features of individual dependency nodes.

The CLEAR dependency conversion has been tested on various Treebanks and shown robust results across different corpora. See the technical report for more details about this conversion.

* [Guidelines for the Clear Style Constituent to Dependency Conversion](https://dl.dropbox.com/u/15060914/publications/ics-12.pdf), Jinho D. Choi, Martha Palmer, Technical report 01-12: Institute of Cognitive Science, University of Colorado Boulder, 2012.

## How to Run
A dictionary must be added before running the converter. See the "[how to add models](getting_started/add_models.md)" page for instructions of how to add our dictionary to your system.

	java com.clearnlp.run.C2DConvert -h <filename> -i <filepath> [-ie <regex> -oe <string> -l <language> -m <string>]
	 
	-h  <filename> : name of a headrule file (required)
	-i  <filepath> : input path (required)
	-ie <regex>    : input file extension (default: .*)
	-oe <string>   : output file extension (default: dep)
	-l  <language> : language (default: en)
	-m  <string>   : merge labels (default: null)

* A headrule file (-h) can be found here: [headrule\_en\_stanford.txt](http://clearnlp.googlecode.com/git/src/main/resources/headrule/headrule_en_stanford.txt). See the [headrule file format](../formats/headrule_file_format.md) page for more details about this file.
* The input path (`-i`) can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension (`-ie`) under the specific directory are processed.
* The input file extension (`-ie`) can be either a string or a [regular expression](http://docs.oracle.com/javase/6/docs/api/java/util/regex/Pattern.html) specifying the extension of the input files. The default value (`.*`) implies files with any extension. This option is used only when the input path (`-i`) points to a directory.
* The output file extension (`-oe`) gets appended to input filenames, and used to generate corresponding output files.
* The language (`-l`) indicates the language of the constituent trees to be convereted. Currently, our conversion supports only English (`en`).
* The `-m` option merges the specified dependency labels to user defined labels. The followings show the format of this option. For instance, if `-m` is specified as `SBJ=nsubj,csubj|OBJ=dobj,iobj`, it relabels {`nsubj`, `csubj`} to `SBJ` and {`dobj`, `idobj`} to `OBJ`.
		
		LABEL  ::= <new_label>=<old_label>[,<old_label>]*
		LABELS ::= LABEL[|LABEL]*
		
The following command takes a sample input file ([wsj\_0001.parse](https://github.com/clearnlp/clearnlp/blob/master/src/main/resources/sample/wsj_0001.parse)) and generates an output file ([wsj\_0001.parse.dep](https://github.com/clearnlp/clearnlp/blob/master/src/main/resources/sample/wsj_0001.parse.dep)) using the headrule file ([headrule\_en\_stanford.txt](http://clearnlp.googlecode.com/git/src/main/resources/headrule/headrule_en_stanford.txt)).

	java com.clearnlp.run.C2DConvert -h headrule_en_stanford.txt -i wsj_0001.parse

### Input file
A sample input file can be found here: [wsj\_0001.parse](https://github.com/clearnlp/clearnlp/blob/master/src/main/resources/sample/wsj_0001.parse). Each tree must start with an empty clause (example 1) or a `TOP` clause (example 2).

* Example 1 

		((S (NP-SBJ (NP (NNP Pierre)
	                (NNP Vinken))
	            (, ,)
	            (ADJP (NML (CD 61)
	                       (NNS years))
	                  (JJ old))
	            (, ,))
    	(VP (MD will)
        	(VP (VB join)
	            (NP (DT the)
	                (NN board))
	            (PP-CLR (IN as)
	                    (NP (DT a)
	                        (JJ nonexecutive)
	                        (NN director)))
	            (NP-TMP (NNP Nov.)
	                    (CD 29))))
    		(. .)))
    		
* Example 2

		(TOP (S (NP-SBJ (NNP Mr.)
		                (NNP Vinken))
		        (VP (VBZ is)
		            (NP-PRD (NP (NN chairman))
		                    (PP (IN of)
		                        (NP (NP (NNP Elsevier)
		                                (NNP N.V.))
		                            (, ,)
		                            (NP (DT the)
		                                (NNP Dutch)
		                                (VBG publishing)
		                                (NN group))))))
				(. .)))
				
### Output file
A sample output file can be found here: [wsj\_0001.parse.dep](https://github.com/clearnlp/clearnlp/blob/master/src/main/resources/sample/wsj_0001.parse.dep). Each field is delimited by a tab character and each tree is delimited by a blank line. See the [data format](../formats/data_format.md) page for more details about the format of the converted dependency trees.

	1       Pierre  pierre  NNP     _       2       nn      _
	2       Vinken  vinken  NNP     _       9       nsubj   _
	3       ,       ,       ,       _       2       punct   _
	4       61      0       CD      _       5       num     _
	5       years   year    NNS     _       6       npadvmod        _
	6       old     old     JJ      _       2       amod    _
	7       ,       ,       ,       _       2       punct   _
	8       will    will    MD      _       9       aux     _
	9       join    join    VB      _       0       root    _
	10      the     the     DT      _       11      det     _
	11      board   board   NN      _       9       dobj    _
	12      as      as      IN      syn=CLR 9       prep    _
	13      a       a       DT      _       15      det     _
	14      nonexecutive    nonexecutive    JJ      _       15      amod    _
	15      director        director        NN      _       12      pobj    _
	16      Nov.    nov.    NNP     sem=TMP 9       npadvmod        _
	17      29      0       CD      _       16      num     _
	18      .       .       .       _       9       punct   _
	 
	1       Mr.     mr.     NNP     _       2       nn      _
	2       Vinken  vinken  NNP     _       3       nsubj   _
	3       is      be      VBZ     _       0       root    _
	4       chairman        chairman        NN      syn=PRD 3       attr    _
	5       of      of      IN      _       4       prep    _
	6       Elsevier        elsevier        NNP     _       7       nn      _
	7       N.V.    n.v.    NNP     _       5       pobj    _
	8       ,       ,       ,       _       7       punct   _
	9       the     the     DT      _       12      det     _
	10      Dutch   dutch   NNP     _       12      nn      _
	11      publishing      publish VBG     _       12      amod    _
	12      group   group   NN      _       7       appos   _
	13      .       .       .       _       3       punct   _