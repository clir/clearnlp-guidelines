# Models

## Contents

* [Dictionary](#dictionary).
* [General domain](#general-domain).
* [Medical domain](#medical-domain).
* [Bioinformations domain](#bioinformatics-domain).
* Include all dependenices: [pom.xml](https://github.com/clir/clearnlp-tutorial/blob/master/pom.xml).

## Dictionary

Dictionaries are required by several components in ClearNLP.  The general dictionary contains general morphology information and the global lexica contains knowledge-base as well as distributional semantics information.

#### Without Maven

* Download the following models and add them to your Java classpath.
 * General dictionary: [clearnlp-dictionary-3.1.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-dictionary/3.1/clearnlp-dictionary-3.1.jar).
 * Global lexica: [clearnlp-global-lexica-3.1.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-global-lexica/3.1/clearnlp-global-lexica-3.1.jar).

 ```
 export CLASSPATH=clearnlp-dictionary-3.1.jar:\\
                     clearnlp-global-lexica-3.1.jar:.
 ```

#### With Maven

* Add the following lines to your `pom.xml`.

 ```
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-dictionary</artifactId>
      <version>3.1</version>
 </dependency>
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-global-lexica</artifactId>
      <version>3.1</version>
 </dependency>
<dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-general-en-ner-gazetteer</artifactId>
      <version>3.0</version>
    </dependency>
 ```

## General Domain

The general models are trained on [OntoNotes 5.0](https://catalog.ldc.upenn.edu/LDC2013T19), [English Web Treebank](https://catalog.ldc.upenn.edu/LDC2012T13), and [QuestionBank](http://www.computing.dcu.ie/~jjudge/qtreebank/).

| OntoNotes 5.0              | Sentence Counts | Token Counts |
| -------------------------- | --------------: | -----------: |
| Broadcasting conversations | 10,822          | 171,101      |
| Broadcasting news          | 10,344          | 206,020      |
| News magazines             | 6,672           | 163,627      |
| Newswires                  | 34,434          | 875,800      |
| Religious texts            | 21,418          | 296,432      |
| Telephone conversations    | 8,963           | 85,444       |
| Web texts                  | 12,447          | 284,951      |

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

* Download the following models and add them to your Java classpath.
 * Part-of-speech tagging: [clearnlp-general-en-pos-3.2.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-general-en-pos/3.2/clearnlp-general-en-pos-3.2.jar).
 * Dependency parsing: [clearnlp-general-en-dep-3.2.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-general-en-dep/3.2/clearnlp-general-en-dep-3.2.jar).
 * Named entity recognition: [clearnlp-general-en-ner-3.1.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-general-en-ner/3.1/clearnlp-general-en-ner-3.1.jar).
 * Named entity gazetteers: [clearnlp-general-en-ner-gazetteer-3.0.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-general-en-ner-gazetteer/3.0/clearnlp-general-en-ner-gazetteer-3.0.jar).

 ```
export CLASSPATH=clearnlp-general-en-pos-3.2.jar:\\
                     clearnlp-general-en-dep-3.2.jar:\\
                     clearnlp-general-en-ner-3.1.jar:\\
                     clearnlp-general-en-ner-gazetteer-3.0:\\
 ```                 		 

#### With Maven

* Add the following lines to your `pom.xml`.

 ```
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-general-en-pos</artifactId>
      <version>3.2</version>
 </dependency>
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-general-en-dep</artifactId>
      <version>3.2</version>
 </dependency>
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-general-en-ner</artifactId>
      <version>3.1</version>
 </dependency>
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-general-en-ner-gazetteer</artifactId>
      <version>3.0</version>
 </dependency>
 ```

## Medical Domain

The medical models are trained on [MiPACQ](http://clear.colorado.edu/compsem/index.php?page=endendsystems&sub=mipacq), [SHARP](http://informatics.mayo.edu/sharp/index.php/Main_Page), and [THYME](http://clear.colorado.edu/compsem/index.php?page=endendsystems&sub=temporal) corpora.

| MiPACQ              | Sentence Counts | Token Counts |
| ------------------- | --------------: | -----------: |
| Clinical questions  | 1,600           |  30,138      |
| Medpedia articles   | 2,796           |  49,922      |
| Clinical notes      | 8,383           | 113,164      |
| Pathological notes  | 1,205           |  21,353      |

| SHARP                      | Sentence Counts | Token Counts |
| -------------------------- | --------------: | -----------: |
| Seattle group health notes |  7,205          |  94,474      |
| Clinical notes             |  6,807          |  93,914      |
| Stratified                 |  4,320          |  43,536      |
| Stratified SGH             | 13,668          | 139,424      |

| THYME                          | Sentence Counts | Token Counts |
| ------------------------------ | --------------: | -----------: |
| Clinical & patheological notes | 26,734          | 388,371      |
| Braincancer                    | 18,700          | 225,486      |

#### Without Maven

* Download the following models and add them to your Java classpath.
 * Part-of-speech tagging: [clearnlp-medical-en-pos-3.1.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-medical-en-pos/3.1/clearnlp-medical-en-pos-3.1.jar).
 * Dependency parsing: [clearnlp-medical-en-dep-3.1.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-medical-en-dep/3.1/clearnlp-medical-en-dep-3.1.jar).

 ```
 export CLASSPATH=clearnlp-medical-en-pos-3.1.jar:\\
                     clearnlp-medical-en-dep-3.1.jar:.
 ```
                 		 
#### With Maven

* Add the following lines to your `pom.xml`.

 ```
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-medical-en-pos</artifactId>
      <version>3.1</version>
 </dependency>
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-medical-en-dep</artifactId>
      <version>3.1</version>
 </dependency>
 ```
 
## Bioinformatics Domain

The bioinformaitcs models are trained on [CRAFT](http://bionlp-corpora.sourceforge.net/CRAFT/) Treebank.

| CRAFT          | Sentence Counts | Token Counts |
| -------------- | --------------: | -----------: |
| Training data  | 16,297          |  452,769     |

#### Without Maven

1. Download the following models and add them to your Java classpath.
 * Part-of-speech tagging: [clearnlp-bioinformatics-en-pos-3.1.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-bioinformatics-en-pos/3.1/clearnlp-bioinformatics-en-pos-3.1.jar).
 * Dependency parsing: [clearnlp-bioinformatics-en-dep-3.1.jar](http://search.maven.org/remotecontent?filepath=edu/emory/clir/clearnlp-bioinformatics-en-dep/3.1/clearnlp-bioinformatics-en-dep-3.1.jar).

 ```		
export CLASSPATH=clearnlp-bioinformatics-en-pos-3.1.jar:\\
                     clearnlp-bioinformatics-en-dep-3.1.jar:.
 ```
                 		 
#### With Maven

* Add the following lines to your `pom.xml`.

 ```
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-bioinformatics-en-pos</artifactId>
      <version>3.1</version>
 </dependency>
 <dependency>
      <groupId>edu.emory.clir</groupId>
      <artifactId>clearnlp-bioinformatics-en-dep</artifactId>
      <version>3.1</version>
 </dependency>
 ```