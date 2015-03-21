# Morphological Analysis

Our morphological analyzer generates lemmas (root forms) of word tokens. It is a rule-based analyzer inspired by the [WordNet morphy](http://wordnet.princeton.edu/man/morphy.7WN.html) although it uses a larger dictionary gathered from various sources and slightly more advanced heuristics. Furthermore, our analyzer normalizes numbers, redundant punctuation, URLs, etc. (see the examples below), which is found to be useful for several NLP tasks. See [how to run command-line tools](md/quick_start/command_line_tools.md) for more details about decoding and training.

## Normalization

Ordinals and cardinals are normalized to `#ord#` and `#crd#`, respectively.

	1st         CD    #ord#
	12nd        CD    #ord#
	23rd        CD    #ord#
	34th        CD    #ord#
	first       CD    #ord#
	third       CD    #ord#
	fourth      CD    #ord#
	zero        CD    #crd#
	ten         CD    #crd#
	eleven      CD    #crd#
	fourteen    CD    #crd#
	
Numeric expressions are normalized to 0.

	10%                    XX    0
	$10                    XX    0
	A.01                   XX    a.0
	A:01                   XX    a:0
	A/01                   XX    a/0
	.01                    XX    0
	12.34                  XX    0
	12,34,56               XX    0
	12-34-56               XX    0
	12/34/46               XX    0
	$10.23,45:67-89/10%    XX    0
	
Redundant punctuation chracters are collapsed.

	.!?-*=~,                                                    XX    .!?-*=~,
	..!!??--**==~~,,                                            XX    ..!!??--**==~~,,
	...!!!???---***===[[user:jdchoi77]],,,                      XX    ..!!??--**==~~,,
	....!!!!????----****====[[user:jdchoi77|1384441338]],,,,    XX    ..!!??--**==~~,,
	
URLs are normalized to `#url#`.

	http://www.google.com         XX    #url#
	www.google.com                XX    #url#
	mailto:somebody@google.com    XX    #url#
	some-body@google+.com         XX    #url#
