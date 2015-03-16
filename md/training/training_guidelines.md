# Training 

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
