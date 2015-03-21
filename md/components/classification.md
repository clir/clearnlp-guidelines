#summary Liblinear package for NLP applications.

= Liblinear for Natural Language Processing =

ClearNLP provides its own implementation of [http://www.csie.ntu.edu.tw/~cjlin/liblinear/ Liblinear], a linear classification package for large-scale data.  Our version of Liblinear accepts string features and labels as input, which is useful for NLP applications.

== Training ==

{{{
java com.googlecode.clearnlp.run.LiblinearTrain -i <filename> -m <filename>
[-nf <integer> -nl <integer> -nt <integer> -v <byte> -s <byte> -c <double> -e <double> -b <double>]

-i  <filename> : the training file (input; required)
-m  <filename> : the model file (output; required)
-v  <byte>     : the type of vector space (default: 1)
                 0: sparse vector space
                 1: string vector space
-nf <integer>  : feature frequency cutoff (exclusive, default: 0), string vector space only
-nl <integer>  : label frequency cutoff (exclusive, default: 0), string vector space only
-nt <integer>  : the number of threads to be used (default: 1)
-s  <byte>     : the type of solver (default: 0)
                 0: L2-regularized L1-loss support vector classification (dual)
                 1: L2-regularized L2-loss support vector classification (dual)
                 2: L2-regularized logistic regression (dual)
-c  <double>   : the cost (default: 0.1)
-e  <double>   : the tolerance of termination criterion (default: 0.1)
-b  <double>   : the bias (default: 0)
}}}

A training file contains training instances (one instance per line), where each instance is represented by the following format.

{{{
if -v is set to 0: <label> (<index>[:weight])+
    <label>  ::= integer
    <index>  ::= feature index  (integer > 0)
    <weight> ::= feature weight (double)

if -v is set to 1: <label> (<type>:<value>[:weight])+
    <label>  ::= string
    <type>   ::= feature type   (string)
    <value>  ::= feature value  (string)
    <weight> ::= feature weight (double)
}}}

Here is an example of a training file containing instances of logical OR ([http://clearnlp.googlecode.com/git/src/main/resources/sample/liblinear-sparse-nonbinarized.txt liblinear-sparse-nonbinarized.txt]), where the sparse vector space is used (`-v` is set to 0) and features are not binarized.  There are two labels, 0 and 1, and two features, indexes 1 and 2, where each feature is assigned with a weight, 0.0 or 1.0.  Although this example uses only two labels, more labels can be used for multi-classification.

{{{
0 1:0.0 2:0.0
1 1:1.0 2:0.0
1 1:0.0 2:1.0
1 1:1.0 2:1.0
}}}

When features are binarized, the above example can be represented as follows ([http://clearnlp.googlecode.com/git/src/main/resources/sample/liblinear-sparse-binarized.txt liblinear-sparse-binarized.txt]).  There are four features, indexes 1 to 4, where indexes 1 and 2 are equivalent to 1:1.0 and 1:0.0 and indexes 3 and 4 are equivalent to 2:1.0 and 2:0.0 from the above example, respectively.

{{{
0 2 4
1 1 4
1 2 3
1 1 3
}}}

Here is a different example of a training file ([http://clearnlp.googlecode.com/git/src/main/resources/sample/liblinear-string-noweight.txt liblinear-string-noweight.txt]), where the string vector space is used (`-v` is set to 1) and features have no weight.  There are two labels, male and female, and two feature types, firstname and lastname, where each feature type is assigned with a value (e.g., Jinho, Choi).

{{{
male firstname:Jinho lastname:Choi
male firstname:James lastname:Martin
female firstname:Martha lastname:Palmer
female firstname:Tamara lastname:Sumner
}}}

When weight are used, the above example can be represented as follows ([http://clearnlp.googlecode.com/git/src/main/resources/sample/liblinear-string-weight.txt liblinear-string-weight.txt]), where all firstnames get a weight of 0.8 and all lastnames get a weight of 0.3.

{{{
male firstname:Jinho:0.8 lastname:Choi:0.3
male firstname:James:0.8 lastname:Martin:0.3
female firstname:Martha:0.8 lastname:Palmer:0.3
female firstname:Tamara:0.8 lastname:Sumner:0.3
}}}

The following commands show how to build Liblinear models using default parameter values and training files above.

{{{
java com.googlecode.clearnlp.run.LiblinearTrain -v 0 -i liblinear-sparse-nonbinarized.txt -m liblinear-sparse-nonbinarized.mod
java com.googlecode.clearnlp.run.LiblinearTrain -v 0 -i liblinear-sparse-binarized.txt -m liblinear-sparse-binarized.mod
java com.googlecode.clearnlp.run.LiblinearTrain -v 1 -i liblinear-string-noweight.txt -m liblinear-string-noweight.mod
java com.googlecode.clearnlp.run.LiblinearTrain -v 1 -i liblinear-string-weight.txt -m liblinear-string-weight.mod
}}}

When `-nl` and `-nf` options are used, labels and features that occur less than the specific values are not used for training.  When `-nt` option is used, multiple threads are used for training, which is useful for multi-classification.  See the [http://www.csie.ntu.edu.tw/~cjlin/liblinear/ Liblinear] page for details about the other options.

== Predicting ==

{{{
java com.googlecode.clearnlp.run.LiblinearPredict -i <filename> -m <filename> -o <filename> [-v <byte>]

-i <filename> : the input file (input; required)
-m <filename> : the model file (input; required)
-o <filename> : the output file (output; required)
-v <byte>     : the type of vector space (default: 1)
                0: sparse vector space
                1: string vector space
}}}

An input file follows the same format as a training file although the label column (1st column) can be filled with any dummy value.  When true labels are used, it prints the overall accuracy of predictions at the end.  The following commands show how to predict instances in the training files using models built from the above examples (obviously, this is purely for demo; in practice, you would never use the same training files for prediction).

{{{
java com.googlecode.clearnlp.run.LiblinearPredict -v 0 -m liblinear-sparse-nonbinarized.mod -i liblinear-sparse-nonbinarized.txt -o liblinear-sparse-nonbinarized.out
java com.googlecode.clearnlp.run.LiblinearPredict -v 0 -m liblinear-sparse-binarized.mod -i liblinear-sparse-binarized.txt -o liblinear-sparse-binarized.out
java com.googlecode.clearnlp.run.LiblinearPredict -v 1 -m liblinear-string-noweight.mod -i liblinear-string-noweight.txt -o liblinear-string-noweight.out
java com.googlecode.clearnlp.run.LiblinearPredict -v 1 -m liblinear-string-weight.mod -i liblinear-string-weight.txt -o liblinear-string-weight.out
}}}

An output file contains predictions (one prediction per line), where the first and second columns show predicted labels and their probabilities, respectively.  The following shows the output from the first command above (using `liblinear-sparse-nonbinarized.mod`).

{{{
0 0.0
1 0.2
1 0.2
1 0.4
}}}