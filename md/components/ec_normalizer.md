#summary Empty category normalizer.

= Empty Category Normalizer =

The co-indexes of empty categories in the original Penn Treebank are annotated on phrases.  In the following tree, `NP-1` contains an empty category `*` that is linked to `NP-SBJ-1` indicated by the co-index `1`.  On the other hand, gapping is represented by the `=` operation.  For example, `NP-SBJ=1-3` is an antecedent of the empty category `*` in `NP-3` indicated by the co-index `3`, and also has a gapping relation to `NP-SBJ-1` indicated by the gap-index `1`.

{{{
(TOP (S (SBAR-ADV (ADVP (RB Even))
                  (IN though)
                  (S (S (NP-SBJ-1 (DT the)
                                  (CD two)
                                  (NNS buildings))
                        (VP (VBD were)
                            (VP-2 (VBN destroyed)
                                  (NP-1 (-NONE- *)))))
                     (CC and)
                     (S (NP-SBJ=1-3 (NNS lives))
                        (VP=2 (VBN lost)
                              (NP-3 (-NONE- *))))))
        (NP-SBJ (NP (DT the)
                    (NNS people))
                (SBAR (WHNP-4 (WP who))
                      (S (NP-SBJ-4 (-NONE- *T*))
                         (VP (VBD survived)))))
        (VP (MD could)
            (VP (VB go)
                (PP-DIR (IN to)
                        (NP (PRP$ their)
                            (NNS homes)))))
        (. /.)))
}}}

This annotation scheme can be confusing; the co-index in `NP-1` indicates that there is an empty category under this phrase whereas the co-index in `NP-SBJ-1` indicates that this phrase is an antecedent of some empty category.  To reduce the confusion, recent Treebanks (e.g., OntoNotes) start normalizing these empty categories so the co-indexes are annotated on the empty categories themselves (e.g., `*-1`; see the following tree).  This normalization is assumed for several NLP tools (e.g., a constituent-to-dependency converter), so it is important to check what kind of Treebank format your system requires.

{{{
(TOP (S (SBAR-ADV (ADVP (RB Even))
                  (IN though)
                  (S (S (NP-SBJ-1 (DT the)
                                  (CD two)
                                  (NNS buildings))
                        (VP (VBD were)
                            (VP-2 (VBN destroyed)
                                  (NP (-NONE- *-1)))))
                     (CC and)
                     (S (NP-SBJ-3=1 (NNS lives))
                        (VP=2 (VBN lost)
                              (NP (-NONE- *-3))))))
        (NP-SBJ (NP (DT the)
                    (NNS people))
                (SBAR (WHNP-4 (WP who))
                      (S (NP-SBJ (-NONE- *T*-4))
                         (VP (VBD survived)))))
        (VP (MD could)
            (VP (VB go)
                (PP-DIR (IN to)
                        (NP (PRP$ their)
                            (NNS homes)))))
        (. /.)))
}}}

== How to run ==

{{{
java com.googlecode.clearnlp.run.ECNormalize -i <filepath> -o <filepath> [-ie <regex>]

-i  <filepath> : the input path (input; required)
-o  <filepath> : the output path (output; required)
-ie <regex>    : the input file extension (default: .*)
}}}

 * The input path can point to either a file or a directory.  When the input path points to a file, only the specific file is processed.  When the input path points to a directory, all files with the input file extension (`-ie`) under the specific directory are processed.
 * If the input path points to a file, the output path must point to a file.  If the input path points to a directory, the output path must point to a directory, in which case, all outputs are saved in the output directory using the same file names in the input directory.
 * The input file extension can be either a string (e.g., `txt`) or a [http://docs.oracle.com/javase/6/docs/api/java/util/regex/Pattern.html regular expression] specifying the extension of input files.  The default value (`.*`) implies files with any extension.  This option is used only when the input path (`-i`) points to a directory.

The following command takes a sample input file ([http://clearnlp.googlecode.com/git/src/main/resources/sample/ec-normalize-sample.txt ec-normalize-sample.txt]) and generates an output file ([http://clearnlp.googlecode.com/git/src/main/resources/sample/ec-normalize-sample.out ec-normalize-sample.out]).

{{{
java com.googlecode.clearnlp.run.ECNormalize -i ec-normalize-sample.txt -o ec-normalize-sample.out
}}}