# Headrule File Format
A headrule file contains head-finding rules for all phrases (or clauses) in constituent trees. Each line consists of a head-finding rule for a phrase type defined in the following format:

	<tag>\t<direction=l|r>\t<rule>(;<rule>)*

* `<tag>`: phrasal/clausal level constituent tag (e.g., `S`, `VP`, `NP`).
* `<direction>: l` - find the leftmost constituent, `r` - find the rightmost constituent.
* `<rule>`: constituent/function tag rules in [Java regular expression](http://download.oracle.com/javase/6/docs/api/java/util/regex/Pattern.html) format.

Here is a head-finding rule for a noun phrase (`NP`) extracted from our headrule file, [headrule\_en\_stanford.txt](https://github.com/clearnlp/clearnlp/blob/master/src/main/resources/headrule/headrule_en_stanford.txt).

	NP  r  NN.*|NML;NX;PRP;FW;CD;NP;-NOM;QP|JJ.*|VB.*;ADJP;S;SBAR;.*
	
* For a noun phrase, it first searches for the rightmost constituent whose tag is `NN.*|NML`, which covers {`NN`, `NNS`, `NNP`, `NNPS`, `NML`}. The rightmost constituent with any of these tags becomes the head of this noun phrase. If such a constituent does not exist, it searches for the rightmost constituent whose tag is `NX`. This procedure is repeated until the head is found. By default, the rightmost constituent with any tag (`.*`) becomes the head of this phrase.
* '-' is used to indicate a function tag. After searching for a constituent whose tag is NP, it searches for any constituent with the function tag `NOM`.
* See the [Penn Treebank tags](http://bulba.sdsu.edu/jeanette/thesis/PennTags.html) for more details about the constituent and function tags.