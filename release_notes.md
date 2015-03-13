# ClearNLP Release Notes

### Version 2.0.2 (1/27/2014)
* There was a bug related to the rule-based post-processing of dependency parsing for English. This is fixed now.

### Version 2.0.1 (11/28/2013)
* There were some errors in the training data for the general models, which caused to produce too many unclassified dependencies. All general models are updated (see [how to add models](getting_started/add_models.md)).
* Constructors are added to [EnglishMPAnalyzer](https://github.com/clearnlp/clearnlp/blob/master/src/main/java/com/clearnlp/component/morph/EnglishMPAnalyzer.java) and [EnglishTokenizer](https://github.com/clearnlp/clearnlp/blob/master/src/main/java/com/clearnlp/tokenization/EnglishTokenizer.java); they can accept the dictionary file as an InputStream.
	- new EnglishMPAnalyzer(new BufferedInputStream(new FileInputStream("dictionary_filename")));
	- new EnglishTokenizer(new BufferedInputStream(new FileInputStream("dictionary_filename")));
* There was a bug in semantic role labeler causing a null point exception (see [post](https://groups.google.com/forum/#!topic/clearnlp/yNfnJyc68mM)). This is fixed now.

### Version 2.0.0 (11/14/2013)
* The official site is moved from Google Code to Wikispaces. You can simply type [clearnlp.com](http://clearnlp.com/) on your browser to access the webpage.
* All repositories are moved from Google Code to Github.
* This version is developed on Java 7.
* The top level package name is changed from `com.googlecode.clearnlp` to `com.clearnlp`.
* All NLP components are now thread-safe (see [demo](demo/clearnlp_demo.md)).
* All models including our dictionary can be retrieved from the [Maven central](http://search.maven.org/#search%7Cga%7C1%7Ccom.clearnlp) (see [how to add models](getting_started/add_models.md)). These models take almost 50% less memory than before during decoding without compromising accuracy.
* The POS tagger now performs morphological analysis simultaneously. If you are using both the POS tagger and the morphological analyzer, you can take out morphological analysis from your pipeline (see [demo](demo/clearnlp_demo.md)).
* The morphological analyzer covers much more token types than before.
* Bugfixes:
	- The morphological analyzer did not lemmatize some plural nouns correctly.
	- The sentence segmenter did not process the very last sentence unless there was a period.

### Previous versions
* [Versions 1.0.0 ~ 1.4.2](https://code.google.com/p/clearnlp/wiki/ReleaseNotes)
