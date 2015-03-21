#summary PropBank data format.

== PropBank data format ==

A PropBank file contains PropBank instances (one instance per line), where each instance is represented by the following format.

{{{
<instance> ::= <tree_path> <tree_id> <predicate_id> <annotator_id> <lemma>-<type> <roleset_id> <aspects>( <argument>)+
<argument> ::= <terminal_id>:<height>-<label>

<tree_path>    ::= path to the Treebank file
<tree_id>      ::= index of the tree containing the predicate (starts with 0, indicating the 1st tree in <tree_path>)
<predicate_id> ::= terminal ID of the predicate (starts with 0, indicating the 1st terminal node of the tree)
<annotator_id> ::= ID of the annotator
<lemma>        ::= lemma of the predicate
<type>         ::= type of the predicate (a: adjective, n: noun, v: verb)
<roleset_id>   ::= sense ID of the predicate
<aspects>      ::= no longer used (default: -----)
<terminal_id>  ::= ID of the 1st terminal node in this argument
<height>       ::= height of this argument phrase from its 1st terminal node
<label>        ::= PropBank label
}}}

Here is an example of a PropBank file ([http://clearnlp.googlecode.com/git/src/main/resources/sample/wsj_0001.prop wsj_0001.prop]).  The first instance indicates a verb-predicate "join" (`join-v`) whose roleset ID is "join.01", which is the 9th terminal node (`predicate_id = 8`) of the 1st tree (`tree_id = 0`) in the Treebank file, [http://clearnlp.googlecode.com/git/src/main/resources/sample/wsj_0001.parse wsj_0001.parse].
{{{
wsj_0001.parse 0 8 gold join-v join.01 ----- 0:2-ARG0 7:0-ARGM-MOD 8:0-rel 9:1-ARG1 11:1-ARGM-PRD 15:1-ARGM-TMP
wsj_0001.parse 1 2 gold be-v be.01 ----- 0:1-ARG1 2:0-rel 3:2-ARG2
wsj_0001.parse 1 10 gold publish-v publish.01 ----- 10:0-rel 11:0-ARG0
}}}

The argument "`9:1-ARG1`" indicates the phrase, "`(NP (DT the) (NN board))`", in the tree (see below) because "`(DT the)`" is the 10th terminal node and "`(NP (DT the) (NN board))`" has a height 1 from this terminal node.

{{{
(TOP (S (NP-SBJ (NP (NNP Pierre)
                    (NNP Vinken))
                (, ,)
                (ADJP (NML (CD 61)
                           (NNS years))
                      (JJ old))
                (, ,))
        (VP (MD will)
            (VP (VB join)
                (NP (DT the)
                    (NN board))
                (PP-CLR (IN as)
                        (NP (DT a)
                            (JJ nonexecutive)
                            (NN director)))
                (NP-TMP (NNP Nov.)
                        (CD 29))))
        (. .)))
}}}