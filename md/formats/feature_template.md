# Feature Template

Sample feature templates can be found [here](https://github.com/clir/clearnlp/tree/master/src/main/resources/features).


## Pointers

Three kinds of pointers are available: `i`, `j`, and `k`.

* Part-of-speech tagging: `i` represents the input token.
* Dependency parsing: `i` and `k` represent the top of the stack, and `j` represents the front of the input buffer.
* Semantic role labeling: `i` represents the predicate, and `j` represents the argument candidate.

Each pointer can be followed by an offset `#`.

* `i-#|j-#`: the `#`'th previous token of `i|j`.
* `i+#|j+#`: the `#`'th next token of `i|j`.
* `k-#`: the `#+1`'th top of the stack in dependency parsing.
* `k+#`: the `#`'th front of the deque in dependency parsing.

Finally, each pointer can be followed by a relation (see [`RelationType`](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/feature/type/RelationType.java)).

| Relation | Description | Relation | Description |
|:---------|:------------|:---------|:------------|
| `i_h`    | the head of `i`                    | `i_h2`   | the grand-head of `i` |
| `i_lmd`  | the leftmost dependent of `i`      | `i_lmd2` | the 2nd-leftmost dependent of `i` |
| `i_rmd`  | the rightmost dependent of `i`     | `i_rmd2` | the 2nd-rightmost dependent of `i` |
| `i_lnd`  | the left-nearest dependent of `i`  | `i_lnd2` | the 2nd-left-nearest dependent of `i` |
| `i_rnd`  | the right-nearest dependent of `i` | `i_rnd2` | the 2nd-right-nearest dependent of `i` |
| `i_lns`  | the left-nearest sibling of `i`    | `i_lns2` | the 2nd-left-nearest sibling of `i` |
| `i_rns`  | the right-nearest sibling of `i`   | `i_rns2` | the 2nd-right-nearest sibling of `i` |

## Feature Types

The following shows our built-in feature templates (see [`FieldType`](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/feature/type/FieldType.java)).

| Type  | Description |
|:-----:|:------------|
| `f` | The word form. |
| `f2` | The word form whose digits and symbols are simplified:<br>&#8226; e.g,`"$1234 tomorrow !!!..."`&#8594;`"0 tomorrow!!.."`.<br>&#8226;[`StringUtils#toSimplifiedForm(String)`](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/util/StringUtils.java). |
| `f3` | The decapitalized simplified word form. |
| `f4` | The word shape described [here](http://www.biomedcentral.com/1471-2105/6/S1/S5):<br>&#8226; e.g,`"TOM"`&#8594;`"AA"`, `"GPA 4.0 !!!!"`&#8594;`"AAx1.1x.."`.<br>&#8226;[`StringUtils#getShape(String, 2)`](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/util/StringUtils.java). |
| `pf` | The prefix,`#` coming after `pf` represents the length.<br>&#8226; e.g,`pf4` of `"important"`&#8594;`"impo"`. |
| `sf` | The suffix, `#` coming after `sf` represents the length.<br>&#8226; e.g,`sf4` of `"important"`&#8594;`"tant"`. |
| `m` | The lemma (see [`mophological analysis`](../components/morphological_analysis.md)). |
| `p` | The part-of-speech tag. |
| `n` | The named entity tag. |
| `d` | The dependency label (see [dependency guidelines](../dependency/dependency_guidelines.md)). |
| `v` | The valency, `l|r|a` coming after `v` reprensents the left, right, or both valency.<br>&#8226; e.g,`va` of a node with 1 left dependent and 2+ right dependents&#8594;`"<->>"`.<br>&#8226;[`getValency(DirectionType)`](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/dependency/DEPNode.java). |
| `a` | The ambiguity class described [here](http://aclweb.org/anthology-new/P/P12/P12-2071.pdf), used for part-of-speech tagging. |
| `t` | The distance between `i` and `j` pointers.<br>&#8226; e.g, distance between the predicate `i` and the argument `j` in semantic role labeling. |
| `ft` | An extra feature, `key` coming after `ft=` represents the key of the feature.<br>&#8226; e.g,`ft=pb`&#8594; the PropBank roleset ID. |
| `sc` | The subcategorization,  `l|r|a` coming after `sc` reprensents the left, right, or both subcategorization, and `m|p|n|d` represents the field value accordingly.<br>&#8226; e.g,`sclp` represents the subcategoziation of part-of-speech tags in the left dependents.<br>&#8226;[`getSubcategorization(DirectionType, FieldType)`](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/dependency/DEPNode.java). |
| `ds` | The set of dependent fields, `m|p|n|d` coming after `ds` represents the field value accordingly. |
| `ds2` | The set of grand-dependent fields, `m|p|n|d` coming after `ds` represents the field value accordingly. |
| `orth` | The set of orthographic features.<br>&#8226;[`OrthographicType`](https://github.com/clir/clearnlp/blob/master/src/main/java/edu/emory/clir/clearnlp/feature/common/OrthographicType.java). |
