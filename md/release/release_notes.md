# Release Notes

## Version 3.1.1 (5/7/2015)

* Word embedding lexicons are removed from the global lexica, which didn't add much accuracy but took so much RAM space.  Furthermore, the gazetteers for named entity recognition are now separated from the global lexica for better modulation (see [models](../quick_start/models.md) for more details).
* The core dictionary is updated; some past-tense verbs recognized as base verbs are now fixed.
* The named entity recognition model is updated.
* See [`pom.xml`](https://github.com/clir/clearnlp-tutorial/blob/master/pom.xml) for all updated dependencies.

## Version 3.1.0 (4/30/2015)

* A new component for named entity recognition is added, which shows state-of-the-art accuracy on both CoNLL'03 and OntoNotes data (a paper describing our approach is under submission).
* All [statistical models](../quick_start/models.md) are upgraded; the part-of-speech tagger and the dependency parser use features extracted from distributional semantics, which give more robust results on unseen data.
* The dependency parser is trained on data from our new [dependency coversion](../dependency/dependency_guidelines.md) adapting many concenpts from the [universal dependency structures](http://universaldependencies.github.io/docs/) and introducing some new useful labels such as `dative`.

## Version 3.0.2 (3/21/2015)

* Arg4j argument documentation is updated.
* [Javadoc](http://nlp.mathcs.emory.edu/clearnlp/javadoc/) for [`DEPNode`](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/dependency/DEPNode.java) and [`DEPTree`](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/dependency/DEPTree.java) are added.

## Version 3.0.1 (3/17/2015)

* Some debugging codes are stripped out.
* Directory paths for staticial models are changed to the top level.
* Minor changes in configuration classes due to the convenience of API calls.

## Version 3.0.0 (3/15/2015)

* ClearNLP is now developed by the [Center for Language and Information Research](http://nlp.mathcs.emory.edu) at [Emory University](http://emory.edu).
* Our maven group ID is changed from `com.clearnlp` to `edu.emory.clir`.
* All our repositories are moved from [github.com/clearnlp](http://github.com/clearnlp/) to [github.com/clir](https://github.com/clir/).
* The version 3.0.0 is written from the scratch. All components in this version show significant speed-up over the previous ones (2-3 times), and the statistical models consume less disk and memory space.
* Staistical models for general, medical, and bioinformatics domains are provided (see [here](../getting_started/models.md); the medical and bioinformatics models will be uploaded by March 25th, 2015).
* The tokenizer preserves non-UTF8 characters as they are; previously, they were converted to their UTF8 equivalent characters (e.g., smart double quotes to `"`).
* The dependency parser is back to greedy parsing, which makes the model size much smaller (about 18 times less disk space) and much faster (about 10K tokens per second in Intel Xeon CPU) without sacrifying much accuracy (about .5% lower).
* This version does not include the semantic role labeler.  There have been many changes in [PropBank](http://verbs.colorado.edu/propbank/) and we decided to spend another month for developing a new semantic role labeler.  The semantic role labeler will be ready in May, 2015.
* We are preparing a named entity recognizer and a coreference resolution system.  These systems will be ready in August, 2015.
* Better documentation is provided at our [guidelines](https://github.com/clir/clearnlp-guidelines) project for more details about training, decoding, [javadoc](http://nlp.mathcs.emory.edu/clearnlp/javadoc/), etc.


## Previous Versions
* Release notes for preivous versions are available [here](previous_notes.md).
