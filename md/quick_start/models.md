# Models

## Contents

* [Dictionary](#dictionary).
* [General domain](#general-domain).
* [Medical domain](#medical-domain).
* [Bioinformations domain](#bioinformatics-domain).

## Dictionary

The dictionary is required for many components in ClearNLP.

#### Without Maven

1. Download [clearnlp-dictionary-3.0.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-dictionary/3.0/clearnlp-dictionary-3.0.jar), and add it to your Java classpath.
		
		export CLASSPATH=clearnlp-dictionary-3.0.jar:.
                 		 
#### With Maven

* Add the following lines to your `pom.xml`.

		<dependency>
		  <groupId>edu.emory.clir</groupId>
		  <artifactId>clearnlp-dictionary</artifactId>
		  <version>3.0</version>
		</dependency>

## Genreal Domain

The general models are trained on [OntoNotes 5.0](https://catalog.ldc.upenn.edu/LDC2013T19), [English Web Treebank](https://catalog.ldc.upenn.edu/LDC2012T13), and [QuestionBank](http://www.computing.dcu.ie/~jjudge/qtreebank/).

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

#### Without Maven

1. Download the following models for the tasks you want to process.
 * Part-of-speech tagging: [clearnlp-general-en-pos-3.1.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-general-en-pos/3.1/clearnlp-general-en-pos-3.1.jar).
 * Dependency parsing: [clearnlp-general-en-dep-3.1.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-general-en-dep/3.1/clearnlp-general-en-dep-3.1.jar).

2. Add all jar files to your Java classpath.
		
		export CLASSPATH=clearnlp-general-en-pos-3.1.jar:\\
                 		 clearnlp-general-en-dep-3.1.jar:.
                 		 
#### With Maven

* Add the following lines to your `pom.xml`.

		<dependency>
		  <groupId>edu.emory.clir</groupId>
		  <artifactId>clearnlp-general-en-pos</artifactId>
		  <version>3.1</version>
		</dependency>
		<dependency>
		  <groupId>edu.emory.clir</groupId>
		  <artifactId>clearnlp-general-en-dep</artifactId>
		  <version>3.1</version>
		</dependency>
		
## Medical Domain

The medical models are trained on [MiPACQ](http://clear.colorado.edu/compsem/index.php?page=endendsystems&sub=mipacq), [SHARP](http://informatics.mayo.edu/sharp/index.php/Main_Page), and [THYME](http://clear.colorado.edu/compsem/index.php?page=endendsystems&sub=temporal) corpora.

| MiPACQ              | Sentence Counts | Token Counts |
| ------------------- | --------------: | -----------: |
| Clinical questions  | 1,600           |  30,138      |
| Medpedia articles   | 2,796           |  49,922      |
| Clinical notes      | 8,382           | 113,160      |
| Pathological notes  | 1,204           |  21,342      |

| SHARP                      | Sentence Counts | Token Counts |
| -------------------------- | --------------: | -----------: |
| Seattle group health notes |  7,205          |  94,445      |
| Clinical notes             |  6,807          |  93,914      |
| Stratified                 |  4,320          |  43,536      |
| Stratified SGH             | 13,668          | 139,423      |

| THYME                          | Sentence Counts | Token Counts |
| ------------------------------ | --------------: | -----------: |
| Clinical & patheological notes | 26,730          | 388,275      |
| Braincancer                    | 18,689          | 225,258      |

#### Without Maven

1. Download the following models for the tasks you want to process.
 * Part-of-speech tagging: [clearnlp-medical-en-pos-3.0.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-medical-en-pos/3.0/clearnlp-medical-en-pos-3.0.jar).
 * Dependency parsing: [clearnlp-medical-en-dep-3.0.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-medical-en-dep/3.0/clearnlp-medical-en-dep-3.0.jar).

2. Add all jar files to your Java classpath. If you are using the bash shell, it is something like the followings:
		
		export CLASSPATH=clearnlp-medical-en-pos-3.0.jar:\\
                 		 clearnlp-medical-en-dep-3.0.jar:.
                 		 
#### With Maven

* Add the following lines to your `pom.xml`.

		<dependency>
		  <groupId>edu.emory.clir</groupId>
		  <artifactId>clearnlp-medical-en-pos</artifactId>
		  <version>3.0</version>
		</dependency>
		<dependency>
		  <groupId>edu.emory.clir</groupId>
		  <artifactId>clearnlp-medical-en-dep</artifactId>
		  <version>3.0</version>
		</dependency>

## Bioinformatics Domain

The bioinformaitcs models are trained on [CRAFT](http://bionlp-corpora.sourceforge.net/CRAFT/) Treebank.

| CRAFT          | Sentence Counts | Token Counts |
| -------------- | --------------: | -----------: |
| Training data  | 16,297          |  452,769     |

#### Without Maven

1. Download the following models for the tasks you want to process.
 * Part-of-speech tagging: [clearnlp-bioinformatics-en-pos-3.0.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-bioinformatics-en-pos/3.0/clearnlp-bioinformatics-en-pos-3.0.jar).
 * Dependency parsing: [clearnlp-bioinformatics-en-dep-3.0.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-bioinformatics-en-dep/3.0/clearnlp-bioinformatics-en-dep-3.0.jar).

2. Add all jar files to your Java classpath. If you are using the bash shell, it is something like the followings:
		
		export CLASSPATH=clearnlp-bioinformatics-en-pos-3.0.jar:\\
                 		 clearnlp-bioinformatics-en-dep-3.0.jar:.
                 		 
#### With Maven

* Add the following lines to your `pom.xml`.

		<dependency>
		  <groupId>edu.emory.clir</groupId>
		  <artifactId>clearnlp-bioinformatics-en-pos</artifactId>
		  <version>3.0</version>
		</dependency>
		<dependency>
		  <groupId>edu.emory.clir</groupId>
		  <artifactId>clearnlp-bioinformatics-en-dep</artifactId>
		  <version>3.0</version>
		</dependency>
