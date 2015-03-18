# Release Notes

### Version 3.0.1 (3/25/2015)

* Some debugging codes are stripped out.
* Minor changes due to the convenience of API calls.
* Directory paths for staticial models are changed to the top level.

### Version 3.0.0 (3/15/2015)

* ClearNLP is now developed by the [Center for Language and Information Research](http://nlp.mathcs.emory.edu) at [Emory University](http://emory.edu).
* Our maven group ID is changed from `com.clearnlp` to `edu.emory.clir`.
* All our repositories are moved from [github.com/clearnlp](http://github.com/clearnlp/) to [github.com/clir](https://github.com/clir/).
* The version 3.0.0 is written from the scratch. All components in this version show significant speed-up over the previous ones (2-3 times), and the statistical models consume less disk and memory space.
* Staistical models for general, medical, and bioinformatics domains are provided (see [here](../getting_started/models.md); the medical and bioinformatics models will be uploaded by March 25th, 2015).
* The tokenizer preserves non-UTF8 characters as they are; previously, they were converted to their UTF8 equivalent characters (e.g., smart double quotes to `"`).
* The dependency parser is back to greedy parsing, which makes the model size much smaller (about 18 times less disk space) and much faster (about 10K tokens per second in Intel Xeon CPU) without sacrifying much accuracy (about .5% lower).
* This version does not include the semantic role labeler.  There have been many changes in [PropBank](http://verbs.colorado.edu/propbank/) and we decided to spend another month for developing a new semantic role labeler.  The semantic role labeler will be ready in May, 2015.
* We are preparing a named entity recognizer and a coreference resolution system.  These systems will be ready in August, 2015.
* The following guidelines are available now:
 * [How to train staistical models](../training/training_guidelines.md).
 * [How to develop NLP components](../training/training_guidelines.md).


### Previous Versions
* Release notes for preivous versions are available [here](previous_notes.md).
