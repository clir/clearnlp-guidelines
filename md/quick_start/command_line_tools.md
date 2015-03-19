# Command-Line Tools

## Contents

* [Decoding](#decoding).
* [Training](#training).

## Decoding

The following shows the command to run the NLP pipeline for part-of-speech tagging, morphological analysis, dependency parsing, or semantic role labeling: `pos`, `morph`, `dep`, `srl`.

	java edu.emory.clir.clearnlp.bin.NLPDecode -mode <mode> -c <filename> -i <filepath> [-ie <string> -oe <string>]

	-mode <mode>  : pos|morph|dep|srl
	-c <filename> : configuration file (required)
	-i <filepath> : input path (required)
	-ie <string>  : input file extension (default: *)
	-oe <string>  : output file extension (default: cnlp)

* A sample configuration file can be found here: [config_decode.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode.xml) (see [configuraiton format](../formats/configuration_format.md)).
* The input path `-i` can point to either a file or a directory. When the input path points to a file, only the specific file is processed. When the input path points to a directory, all files with the input file extension `-ie` under the specific directory are processed.
* The input file extension `-ie` specifies the extension of the input files. The default value `*` implies files with any extension. This option is used only when the input path `-i` points to a directory.
* The output file extension `-oe` is appended to each input filename, and generates the corresponding output file.

The following command takes the input file ([clearnlp.txt](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt)) and the configuration file ([config_decode.xml](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/config_decode.xml)), performs the NLP pipeline for dependency parsing (`dep`), and generates the output file ([clearnlp.txt.cnlp](https://github.com/clir/clearnlp/blob/master/src/main/resources/samples/clearnlp.txt.cnlp)).

	$ java -Xmx4g -XX:+UseConcMarkSweepGC java edu.emory.clir.clearnlp.bin.NLPDecode -mode dep -c config_decode.xml -i clearnlp.txt
	Loading dependency parsing models.
	Loading part-of-speech tagging models.
	Decoding:
	clearnlp.txt

* Make sure to use the [`-XX:+UseConcMarkSweepGC`](http://www.oracle.com/technetwork/java/tuning-139912.html) option for JVM, which reduces the memory usage into a half.
* Add the log4j configuration file ([log4j.properties](https://github.com/clir/clearnlp/blob/master/src/main/resources/configure/log4j.properties)) to your classpath.
* Use our [visualization tool](http://nlp.mathcs.emory.edu/clearnlp/demo/demo.html) to view the output.

## Training 

To train fill in the following variables and run:

`-Xmx40g` : Replace 40g (40 gigabytes) with how much memory you want to allocate  
`-mode $MODE` : The built-in `pos`, `morph`, `dep`, and `srl` modes perform part-of-speech tagging, morphological analysis, dependency parsing, and semantic role labeling respectively  
`-t $TRN `:  Training data (Required full path to train files. Use `-te` to specify training file extension)  
`-d $DEV` :  Development data (Required full path to the development files. Use `-de` to specify dev file extension)  
`-c $CONFIG` : Training configuration file (required) [Training Guidelines] (https://github.com/clir/clearnlp-guidelines/blob/master/md/formats/configuration/config_train.md)  
`-f $FEATURE` : Feature XML files (required) [Feature Guidelines] (FeatureExtraction.md)  
`-m $MODEL` : Model path (optional)  
`-threads` : Number of threads to use (default = 1) 



	java -Xmx40g -XX:+UseConcMarkSweepGC edu.emory.clir.clearnlp.bin.NLPTrain -mode $MODE -t $TRN -d $DEV -c $CONFIG -f $FEATURE #-m $MODEL
