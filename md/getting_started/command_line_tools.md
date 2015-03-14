# Command-Line Tools

## NLP Pipeline

* The following shows the command for running the NLP pipeline. The `pos`, `morph`, `dep`, `srl` modes perform the pipeline for part-of-speech tagging, morphological analysis, dependency parsing, and semantic role labeling, respectively.

		java edu.emory.clir.clearnlp.bin.NLPDecode -mode <mode> -c <filename> -i <filepath> [-ie <string> -oe <string>]

		-mode <mode>  : pos|morph|dep|srl
		-c <filename> : configuration file (required)
		-i <filepath> : input path (required)
		-ie <string>  : input file extension (default: *)
		-oe <string>  : output file extension (default: cnlp)
	
* Download the following files and put them under the `clearnlp` directory:<br>[config_decode.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode.xml), [log4j.properties](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/log4j.properties), [clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt).

* The following command takes the input file [clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt), performs dependency parsing (`dep`) using the configuration file [config_decode.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode.xml), and generates the output file [clearnlp.txt.cnlp](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt.cnlp).

		$ java -Xmx4g -XX:+UseConcMarkSweepGC java edu.emory.clir.clearnlp.bin.NLPDecode -mode dep -c config_decode.xml -i clearnlp.txt
		Loading part-of-speech tagging models.
		Loading dependency parsing models.
		Decoding:
		clearnlp.txt
		
* Use our [visualization tool](http://mathcs.emory.edu/~choi/clearnlp/demo/demo.html) to view the output.
