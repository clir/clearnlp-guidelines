# Dependency Parsing

## English Treebank

### Distribution

| Set      | Splits | Sentences |  Tokens |
|:---------|:------:|----------:|--------:|
| Train    | 2-21   |    39,832 | 950,028 |
| Develop  |   22   |     1,700 |  40,117 |
| Evaluate |   23   |     2,416 |  56,684 |

### Accuracy: Y & M

| Approach | UAS* | LAS* | UAS | LAS | Note |
|:---------|:-----|:-----|:----|:----|:-----|
| [Honnibal et al., 2013](http://www.aclweb.org/anthology/W13-3518)  | 91.0  | 88.9 | - | - | T
| [Zhang & Clark, 2008](http://www.aclweb.org/anthology/D08-1059)    | 91.4  | -    | - | - | T
| [Huang & Sagae, 2010](http://www.aclweb.org/anthology/P10-1110)    | 92.1  | -    | - | - | T 
| [Zhang & Nivre, 2011](http://aclweb.org/anthology/P11-2033)        | 92.9  | 91.8 | - | - | T
| [Qian & Liu, 2013](http://aclweb.org/anthology/Q/Q13/Q13-1004.pdf) | 93.17 | -    | - | - | B&B

* Head-fidning rules: [Yamada & Matsumoto, 2003](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&uact=8&ved=0CC4QFjAC&url=http%3A%2F%2Fciteseerx.ist.psu.edu%2Fviewdoc%2Fdownload%3Fdoi%3D10.1.1.100.2289%26rep%3Drep1%26type%3Dpdf&ei=KA8VVZKdO8n2oATBw4D4DQ&usg=AFQjCNGG0ApOwP68rCvj3CfnntuzeCEESg&sig2=wrofSoRcJNsljPnwAK3HvQ&bvm=bv.89381419,d.cGU).
* Depenency conversion: [Penn2Malt](http://stp.lingfil.uu.se/~nivre/research/Penn2Malt.html).
* [Goldberg & Nivre, 2012](http://www.aclweb.org/anthology/C12-1059) has results only including puncutation.

### Accuracy: Stanford

| Approach | UAS* | LAS* | UAS | LAS | Note |
|:---------|:-----|:-----|:----|:----|:-----|
| [Honnibal et al., 2013](http://www.aclweb.org/anthology/W13-3518)  | 91.1  | 88.9  | - | - | T
| [Goldberg et al,, 2014](http://aclweb.org/anthology/Q14-1010)      | 91.77 | 89.53 | - | - | T
| [Chen & Manning, 2014](http://aclweb.org/anthology/D14-1082)       | 91.8  | 89.6  | - | - | T
| [Zhang & Nivre, 2011](http://aclweb.org/anthology/P11-2033)        | 93.5  | 91.9  | - | - | T

* Depenency conversion: [Stanford](http://nlp.stanford.edu/software/stanford-dependencies.shtml).

## Chinese Treebank

### Distribution

| Set      | Splits             | Sentences | Tokens  |
|:---------|:-------------------|----------:|--------:|
| Train    | 1-815, 1001-1136   |    16,091 | 437,990 |
| Develop  | 900-931, 1148-1151 |       803 |  20,454 |
| Evaluate | 816-885, 1137-1147 |     1,910 |  50,315 |

* These distributions are derived from [Chinese Treebank 8.0](https://catalog.ldc.upenn.edu/LDC2013T21).

### Accuracy

| Approach | UAS* | LAS* | UAS | LAS | Note |
|:---------|:-----|:-----|:----|:----|:-----|
| [Chen & Manning, 2014](http://aclweb.org/anthology/D14-1082)    | 83.9  | 82.4  | - | - | T
| [Zhang & Clark, 2008](http://www.aclweb.org/anthology/D08-1059) | 84.3  | -     | - | - | T
| [Huang & Sagae, 2010](http://www.aclweb.org/anthology/P10-1110) | 85.20 | -     | - | - | T 
| [Zhang & Nivre, 2011](http://aclweb.org/anthology/P11-2033)     | 86.0  | 84.4  | - | - | T
| [Qian & Liu, 2013](http://aclweb.org/anthology/Q/Q13/Q13-1004.pdf) | 87.25 | -     | - | - | B&B

* Gold-standard segmentation and POS tags are used.
* Head-fidning rules: [Zhang & Clark, 2008](http://www.aclweb.org/anthology/D08-1059).
* Dependency conversion: [Penn2Malt](http://stp.lingfil.uu.se/~nivre/research/Penn2Malt.html).






**http://aclweb.org/anthology/Q/Q13/Q13-1012.pdf**
http://aclweb.org/anthology/Q/Q13/Q13-1025.pdf

http://aclweb.org/anthology/P/P14/P14-1125.pdf
http://aclweb.org/anthology/P/P14/P14-1130.pdf
http://aclweb.org/anthology/P/P14/P14-2107.pdf
http://aclweb.org/anthology/P/P14/P14-2106.pdf
http://aclweb.org/anthology/P/P13/P13-1014.pdf
http://aclweb.org/anthology/P/P13/P13-2020.pdf
http://aclweb.org/anthology/P/P13/P13-2019.pdf
http://aclweb.org/anthology/D/D14/D14-1099.pdf
http://aclweb.org/anthology/D/D14/D14-1081.pdf
http://aclweb.org/anthology/C/C12/C12-2077.pdf
http://aclweb.org/anthology/C/C12/C12-1188.pdf
http://aclweb.org/anthology/C/C12/C12-1106.pdf
http://aclweb.org/anthology/C/C12/C12-1103.pdf
http://aclweb.org/anthology/C/C12/C12-1078.pdf
http://aclweb.org/anthology/C/C14/C14-1078.pdf
http://aclweb.org/anthology/C/C14/C14-1076.pdf
http://www.aclweb.org/anthology/C12-1059
http://www.aclweb.org/anthology/W09-3825
http://ir.hit.edu.cn/~car/papers/acl13-chpar.pdf
http://www.aclweb.org/anthology/P11-1139
http://www.aclweb.org/anthology/D12-1132