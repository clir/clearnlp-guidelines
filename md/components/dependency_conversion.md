# Constituent-to-Dependency Conversion

Our constituent-to-dependency converter takes the [Penn Treebank](http://www.cis.upenn.edu/~treebank/) style constituent trees as input and generates the Emory style dependency trees as output. Here are some of the key features of our dependency conversion.

* Generates rich dependency labels similar to the [Stanford dependency labels](http://nlp.stanford.edu/software/stanford-dependencies.shtml).
* Allows users to customize their own head-finding rules.
* Produces long-distance dependencies by remapping empty categories in constituent trees.
* Produces secondary dependencies caused by several linguistic phenomena.
* Preserves function tags as features of individual dependency nodes.

Our dependency conversion has been tested on various Treebanks and shown robust results across different corpora. See the following documents for more details.

* [ClearNLP dependency labels](../dependency/dependency_guidelines.md): latest version.
* [Guidelines for the CLEAR Style Constituent to Dependency Conversion](http://www.mathcs.emory.edu/~choi/doc/clear-dependency-2012.pdf), Jinho D. Choi, Martha Palmer, Technical report 01-12: Institute of Cognitive Science, University of Colorado Boulder, 2012.

## Decoding

The dictionary must be added before running the converter. See [how to add models](../quick_start/models.md) for the instructions of adding our dictionary to your system.

	java edu.emory.clir.clearnlp.bin.C2DConvert -h <filename> -i <filepath> [-l <language> -r -n -oe <string> -pe <string> -re <string>]

	-h <filename> : headrule file (required)
	-i <filepath> : input path (required)
	-l <language> : language (default: english)
	-r <boolean>  : if set, traverse parse files recursively
	-n <boolean>  : if set, normalize empty category indices
	-oe <string>  : output file extension (default: dep)
	-pe <string>  : parse file extension (default: parse)
	-re <string>  : propbank file extension (default: prop)

* A headrule file `-h` can be found here: [headrule\_en\_stanford.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/headrules/headrule_en_stanford.txt) (see [headrule file format](../formats/headrule_format.md)).
* The input path `-i` can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension `-pe|re` under the specific directory are processed.
* The langauge `-l` specifies the input language. See [TLanguage](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/util/lang/TLanguage.java) for all supported languages.
* The output file extension `-oe` is appended to each parse filename, and generates the corresponding output file.
* The parse file extension `-pe` specifies the extension of the Treebank files. This option is used only when the input path `-i` points to a directory.
* The parse file extension `-re` specifies the extension of the PropBank files. This option is used only when the input path `-i` points to a directory.
		
The following command takes the input file ([wsj\_0001.parse](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/wsj_0001.parse)) and the headrule file ([headrule\_en\_stanford.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/headrules/headrule_en_stanford.txt)), and generates the output file ([wsj\_0001.parse.dep](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/wsj_0001.parse.dep)).

	java edu.emory.clir.clearnlp.bin.C2DConvert -h headrule_en_stanford.txt -i wsj_0001.parse

## Input

Each tree must start with an empty clause (example 1) or the `TOP` clause (example 2).

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
				
## Output

Each field is delimited by a tab character and each tree is delimited by a blank line. See [data format](../formats/data_format.md) for more details about the format of the converted dependency trees.

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