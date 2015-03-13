# How to add models
## Genreal domain
The general models are trained on various corpora, mostly from the [OntoNotes 5.0](https://catalog.ldc.upenn.edu/docs/LDC2013T19/OntoNotes-Release-5.0.pdf) and more. The followings show the distribution of each genre in our training data.

* Broadcasting conversations: 10,826 sentences, 171,120 tokens
* Broadcasting news: 10,349 sentences, 206,057 tokens
* News magazines: 6,672 sentences, 163,627 tokens
* Newswires: 34,492 sentences, 876,399 tokens
* Religious texts: 21,419 sentences, 296,437 tokens
* Telephone conversations: 8,969 sentences, 85,463 tokens
* Web-texts: 12,452 sentences, 284,975 tokens

#### Without Maven
1. Download the following models for the tasks you want to process.
	- Dictionary: [clearnlp-dictionary-1.0.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-dictionary/1.0/clearnlp-dictionary-1.0.jar) (required)
	- Part-of-speech tagging: [clearnlp-general-en-pos-1.1.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-general-en-pos/1.1/clearnlp-general-en-pos-1.1.jar)
	- Dependency parsing: [clearnlp-general-en-dep-1.2.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-general-en-dep/1.2/clearnlp-general-en-dep-1.2.jar)
	- Semantic role labeling: [clearnlp-general-en-srl-1.1.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-general-en-srl/1.1/clearnlp-general-en-srl-1.1.jar)

2. Add all jar files to your Java classpath. If you are using the bash shell, it is something like the followings:
		
		export CLASSPATH=clearnlp-dictionary-x.x.jar:\\
                 		 clearnlp-general-en-pos-x.x.jar:\\
                 		 clearnlp-general-en-dep-x.X.jar:\\
                 		 clearnlp-general-en-srl-x.x.jar:more_jar_files...
                 		 
#### With Maven
All models can be retrieved from [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Cclearnlp-general-en). Add the following lines to your 'pom.xml'.

		<dependencies>
  		...
			<dependency>
		    	<groupId>com.clearnlp</groupId>
		    	<artifactId>clearnlp-dictionary</artifactId>
		    	<version>1.0</version>
		  	</dependency>
		  	<dependency>
		    	<groupId>com.clearnlp</groupId>
		    	<artifactId>clearnlp-general-en-pos</artifactId>
		    	<version>1.1</version>
		  	</dependency>
		  	<dependency>
		    	<groupId>com.clearnlp</groupId>
		    	<artifactId>clearnlp-general-en-dep</artifactId>
		    	<version>1.2</version>
		  	</dependency>
		  	<dependency>
		    	<groupId>com.clearnlp</groupId>
		    	<artifactId>clearnlp-general-en-srl</artifactId>
		    	<version>1.1</version>
		  	</dependency>
		...
		</dependencies>
		
## Medical domain
The medical models are trained on various corpora, collected by the MiPACQ, SHARP, and THYME projects. The followings show the distribution of each genre in our training data.

* MiPACQ: Clinical questions: 1,600 sentences, 30,138 tokens
* MiPACQ: Medpedia articles: 2,796 sentences, 49,922 tokens
* MiPACQ: clinical notes: 8,001 sentences, 107,191 tokens
* MiPACQ: pathological notes: 1,225 sentences, 21,581 tokens
* SHARP: Seattle group health clinical notes: 5,020 sentences, 61,124 tokens
* SHARP: Seattle group health pathological notes: 2,294 sentences, 34,384 tokens
* SHARP clinical notes: 6,787 sentences, 94,205 tokens
* SHARP stratified: 4,312 sentences, 43,023 tokens
* SHARP stratified SGH: 13,432 sentences, 139,266 tokens
* TEMPREL clinical notes: 18,927 sentences, 255,604 tokens
* TEMPREL pathological notes: 4,400 sentences, 80,064 tokens

#### Without Maven
1. Download the following models for the tasks you want to process.
	- Dictionary: [clearnlp-dictionary-1.0.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-dictionary/1.0/clearnlp-dictionary-1.0.jar) (required)
	- Part-of-speech tagging: [clearnlp-medical-en-pos-1.0.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-medical-en-pos/1.0/clearnlp-medical-en-pos-1.0.jar)
	- Dependency parsing: [clearnlp-medical-en-dep-1.0.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-medical-en-dep/1.0/clearnlp-medical-en-dep-1.0.jar)
	- Semantic role labeling: [clearnlp-medical-en-srl-1.0.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-medical-en-srl/1.0/clearnlp-medical-en-srl-1.0.jar)

2. Add all jar files to your Java classpath. If you are using the bash shell, it is something like the followings:

		export CLASSPATH=clearnlp-dictionary-1.0.jar:\\
                 		 clearnlp-medical-en-pos-x.x.jar:\\
                		 clearnlp-medical-en-dep-x.x.jar:\\
                 		 clearnlp-medical-en-srl-x.x.jar:more_jar_files...
                 		 
#### With Maven
All models can be retrieved from [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Cclearnlp-medical-en). Add the following lines to your 'pom.xml'.

		<dependencies>
  		...
		 	<dependency>
		    	<groupId>com.clearnlp</groupId>
		    	<artifactId>clearnlp-dictionary</artifactId>
		    	<version>1.0</version>
		  	</dependency>
		  	<dependency>
		    	<groupId>com.clearnlp</groupId>
		    	<artifactId>clearnlp-medical-en-pos</artifactId>
		    	<version>1.0</version>
		  	</dependency>
		  	<dependency>
		    	<groupId>com.clearnlp</groupId>
		    	<artifactId>clearnlp-medical-en-dep</artifactId>
		    	<version>1.0</version>
		  	</dependency>
		  	<dependency>
		    	<groupId>com.clearnlp</groupId>
		    	<artifactId>clearnlp-medical-en-srl</artifactId>
		    	<version>1.0</version>
		  	</dependency>
		...
		</dependencies>
		
		