# Models

## Contents

* [General domain](#general-domain).
* [Medical domain](#medical-domain).
* [Bioinformations domain](#bioinformations-domain).

## Genreal Domain

The general models are trained on [OntoNotes 5.0](https://catalog.ldc.upenn.edu/LDC2013T19), [English Web Treebank](https://catalog.ldc.upenn.edu/LDC2012T13), and [QuestionBank](http://www.computing.dcu.ie/~jjudge/qtreebank/). The followings show the distribution of each genre in our training data.

| OntoNotes 5.0              | Sentence Counts | Token Counts |
| -------------------------- | --------------: | -----------: |
| Broadcasting conversations | 10,822          | 171,101      |
| Broadcasting news          | 10,822          | 206,020      |
| News magazines             | 6,672           | 163,627      |
| Newswires                  | 34,434          | 875,738      |
| Religious texts            | 21,418          | 296,432      |
| Telephone conversations    | 8,963           | 85,444       |
| Web texts                  | 12,447          | 284,948      |

| Engilsh Web Treebank | Sentence Counts | Token Counts |
| -------------------- | --------------: | -----------: |
| Answers              | 2,699           | 43,916       |
| Email                | 2,983           | 44,168       |
| Newsgroup            | 1,995           | 37,714       |
| Reviews              | 2,915           | 44,337       |
| Weblog               | 1,753           | 38,770       |

| QuestionBank | Sentence Counts | Token Counts |
| ------------ | --------------: | -----------: |
| Questions    | 3,199           | 29,715       |


### Without Maven

1. Download the following models for the tasks you want to process.
 * Dictionary: [clearnlp-dictionary-1.0.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-dictionary/1.0/clearnlp-dictionary-1.0.jar) (required)
 * Part-of-speech tagging: [clearnlp-general-en-pos-1.1.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-general-en-pos/1.1/clearnlp-general-en-pos-1.1.jar)
 * Dependency parsing: [clearnlp-general-en-dep-1.2.jar](http://search.maven.org/remotecontent?filepath=com/clearnlp/clearnlp-general-en-dep/1.2/clearnlp-general-en-dep-1.2.jar)

2. Add all jar files to your Java classpath. If you are using the bash shell, it is something like the followings:
		
		export CLASSPATH=clearnlp-dictionary-x.x.jar:\\
                 		 clearnlp-general-en-pos-x.x.jar:\\
                 		 clearnlp-general-en-dep-x.X.jar:\\
                 		 clearnlp-general-en-srl-x.x.jar:more_jar_files...
                 		 
### With Maven

Add the following lines to your 'pom.xml'.

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
		
## Medical Domain


## Bioinformatics Domain

Coming soon...

<!--The medical models are trained on various corpora, collected by the MiPACQ, SHARP, and THYME projects. The followings show the distribution of each genre in our training data.

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
		</dependencies>-->