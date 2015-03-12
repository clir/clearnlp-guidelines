# Add Components to ClearNLP

## Setup

In order to add any additional componenet to ClearNLP, you will have to clone the entire clearnlp repo to your local machine.
	
	cd ~/TARGET_DIRECTORY_PATH/
	git clone https://github.com/clir/clearnlp.git

There are **five** parts of the component that your have to setup/initialize to integrate the componenet with ClearNLP:
	
	1. COLLECT: Collect lexicon before training
	2. TRAIN: Train the componenet model
	3. BOOTSTRAP: Decode on train data to pick up error cases for model improvement
	4. EVALUATE: Test componenet model on development data
	5. DECODE: Decode
> These are declared enums for componenets ( ... .component.utils.CFlag)

## Tutorial

1. Create a package (Name of your component) under ... .clearnlp.component.mode

2. Create a component state java file (ie. SeqState extends AbstractLRState/AbstractState)

	1. Overwite all abstract methods according the functionality of your component
	2. You can pass in a dictionary to the constructor if needed
	3. ***clearOracle: For clearing predefined information to avoid confusing data during feature extraction

	> - State files has an OracelType(Ground truth input) and a LabelType(the way to produce label)
	> - Extend AbstractLRState if you are doing equence classification from left to right (i.e. POSTagging or NameEntityRecognition) else extend AbstractState
	
	Demo Code: [clearnlp.component.mode.sequence.SeqState](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/component/mode/sequence/SeqState.java)

3. Creat a component evaluattion java file (ie. SeqEval enxtends AbstractEval)

	1. ***countCorrect: 

	Demo code: [clearnlp.component.mode.sequence.SeqEval](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/component/mode/sequence/SeqEval.java)

4. Creat a component train configuration java file (ie. SeqTrainConfiguration extends AbstractTrainConfiguration)

	Demo code: [clearnlp.component.mode.sequence.SeqTrainConfiguration](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/component/mode/sequence/SeqTrainConfiguration.java)

5. Creat a component feature extractor java file (ie. SeqFeatureExtractor enxtends CommonFeatureExtractor)

	Demo code: [clearnlp.component.mode.sequence.SeqFeatureExtractor](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/component/mode/sequence/SeqFeatureExtractor.java)

6. Creat a component (abstract) classifier java file (ie. AbstractSeqClassifier & DefaultSeqClassifier)

	Demo code: [clearnlp.component.mode.sequence.AbstractSequenceClassifier](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/component/mode/sequence/AbstractSequenceClassifier.java)
	
	Demo code: [clearnlp.component.mode.sequence.DefaultSequenceClassifier](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/component/mode/sequence/DefaultSequenceClassifier.java)

7. Creat a component trainer java file (ie. SeqTrainer extends AbstractNLPTrainer)

	Demo code: [clearnlp.component.mode.sequence.SeqTrainer](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/component/mode/sequence/SeqTrainer.java)

8. Modify ... .clearnlp.nlp.NLPUtils

	Source code: [clearnlp.nlp.NLPUtils](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/nlp/NLPUtils.java)

9. Modify ... clearnlp.bin.NLPDecode

	Source code: [clearnlp.bin.NLPDecode](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/bin/NLPDecode.java)

10. Test out and run the newly added component

		java  -Xmx8g -XX:+UseConcMarkSweepGC edu.emory.clir.clearnlp.bin.NLPTrain -c CONFIG -f FEATURE -mode MODE -t TRAINDATA -d DEVDATA
		
## Note
This tutorial shows how to add components to ClearNLP by creating a sequence classifier component to ClearNLP. Due to the similiarity between sequence classifier and POS classifer, the tutorial above simply replicates [clearnlp.component.mode.pos](https://github.com/clir/clearnlp/tree/master/src/main/java/edu/emory/clir/clearnlp/component/mode/pos) and rewrites the exisiting component into a sequence classifier. 

If you were going to add a component that structurally different from any existing component in ClearNLP, you will have to create most of the abstract classes (ie. AbstractEval, AbstractState, etc). However you do have to make sure to implement the **five** parts of the ClearNLP component mentioned above.