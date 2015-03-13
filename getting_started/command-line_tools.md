# Using Command-Line Tools
* The following shows the command to run the NLP pipeline. The `pos`, `morph`, `dep`, `srl` modes perform the pipeline for part-of-speech tagging, morphological analysis, dependency parsing, and semantic role labeling, respectively.

		java com.clearnlp.nlp.engine.NLPDecode -z <mode> -c <filename> -i <filepath> [-ie <regex> -oe <string>]

		-z <mode>     : pos|morph|dep|srl
		-c <filename> : configuration file (required)
		-i <filepath> : input path (required)
		-ie <regex>   : input file extension (default: .*)
		-oe <string>  : output file extension (default: labeled)
	
* Download the following files and put them under clearnlp.
	- [config_decode.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode.xml), [log4j.properties](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/log4j.properties), [clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt).
	- If you are using the medical models, replace `<model>general-en</model>` with `<model>medical-en</model>`.

* The following command takes the input file `clearnlp.txt`, performs semantic role labeling (`srl`) using the configuration file `config_decode.xml`, and generates the output file [clearnlp.txt.cnlp](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt.cnlp).

		$ java -Xmx4g -XX:+UseConcMarkSweepGC -Dlog4j.configuration=file:log4j.properties com.clearnlp.nlp.engine.NLPDecode -z srl -c config_decode.xml -i clearnlp.txt
		Loading feature templates.
		Loading models.
		Loading lexica.
		...
		Decoding:
		/Users/YOUR_USERNAME/Desktop/clearnlp.txt
		
* Use our [visualization tool](http://mathcs.emory.edu/~choi/clearnlp/demo/demo.html) to view the output.

