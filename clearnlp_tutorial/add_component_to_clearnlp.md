# Add component to ClearNLP

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
> State files has an OracelType(Ground truth input) and a LabelType(the way to produce label)
	1. Overwite all abstract methods according the functionality of your component
	2. You can pass in a dictionary to the constructor if needed