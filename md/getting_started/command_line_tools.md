# Command-Line Tools

## NLP Pipeline

* The following shows the command for running the NLP pipeline. The `pos`, `morph`, `dep`, `srl` modes perform the pipeline for part-of-speech tagging, morphological analysis, dependency parsing, and semantic role labeling, respectively.

		java edu.emory.clir.clearnlp.bin.NLPDecode -mode <mode> -c <filename> -i <filepath> [-ie <string> -oe <string>]

		-mode <mode>  : pos|morph|dep|srl
		-c <filename> : configuration file (required)
		-i <filepath> : input path (required)
		-ie <string>  : input file extension (default: *)
		-oe <string>  : output file extension (default: cnlp)
	
* Download the following files and put them under the `clearnlp` directory ([configuraiton file format](../formats/configuration/config_decode.md)):<br>[config_decode.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode.xml), [log4j.properties](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/log4j.properties), [clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt).

* The following command takes the input file [clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt) and the configuration file [config_decode.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode.xml), performs the NLP pipeline for dependency parsing (`dep`), and generates the output file [clearnlp.txt.cnlp](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt.cnlp).

		$ java -Xmx4g -XX:+UseConcMarkSweepGC java edu.emory.clir.clearnlp.bin.NLPDecode -mode dep -c config_decode.xml -i clearnlp.txt
		Loading dependency parsing models.
		Loading part-of-speech tagging models.
		Decoding:
		clearnlp.txt
		
* Use our [visualization tool](http://nlp.mathcs.emory.edu/clearnlp/demo/demo.html) to view the output.
