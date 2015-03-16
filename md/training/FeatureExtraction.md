
  

# Feature Extraction 
Features are stored as a xml file in the src/main/resource folder. The following is a table of word or node features used in part of speech tagging and dependency parsing.  

| Word/Node Features  | Feature Representations  | Feature Meanings |
|:------------- |:---------------| :---------------------|
| f    | Word form | The word itself |
| f2      | Simplified word form | The word with digits and punctuations (max length 2) collapsed. Example: `$1234 tomorrow!!!...` becomes `0 tomorrow!!..`|
| f3 | Lowercased simplified word form|  Lowered case of above|
| m | Word lemma | Dictionary form or canonical form Example: running, runs, run, ran have the lemma of run  |
| f4 | Word shape | Mapping of word to a representation (max repetition = 2) that uses the attributes upper case = `'A'`, lower case = `'a'`, digit = `'1'`, punctuation = `'.'`, and all others = `'x'`. Example `TOM` becomes `AA` or `GPA 4.0 !!!` becomes `AAx1.1x..`  |
| pf | Prefix        | Prefix of a word (The # coming after pf represents prefix length) Example: `pf4` of `important` is `impo`   |
| sf | Suffix        | Suffix of a word (The # coming after sf represents suffix length) Example: `sf4` of `important` is `tant` |
| p  | POS tag        | Part of speech tag Example: `NN`, `JJ`, `VB`|
| n | Named entity tag | Named entity tag Example: `Person`, `Location`|
| d |  Dependency label| See dependency label documentation |
| v | Valency | Returns `"0"` if node in dependency tree has no children, `"<"` if node only has left substree, `">"` if node only has right subtree or `"<>"` for both |
| lv | Left valency | Return size of left subtree |
| rv | Right valency | Return size of right subtree  |
| b | If first or last word | Use `b0` as a feature for the first word or `b1` as a feature for the last   |
| ft | Value of specific feature | Mapping to a specific feature #. Example `ft14` represents a mapping to 14th feature used   |
| orth | Orthographic features | Checks if the word is all digits or punctuations or just contains a single digit or punctuation. Checks if the first word is upper case or if all letters are upper cased/lowercased.  |
| ds | Children features | Considers all children dependency labels of a node in dependency tree as a feature   |
| ds2 | Grandchildren features |Considers all grandchildren dependency labels of a node in dependency tree as a feature   |
| a | Ambiguity class | Considers the classes of a unseen node based on previous classes seen in the current data set. Example: If we are trying to classify the POS of the following words: `"ran away."` in the sentence `"He ran away."` Given that we have seen `"away"` as `RB` or `VBD` we take these classes into account to determine the POS for `"ran"`.  |
| lmd | Left most child | Considers the left most child of the current node in the dependency tree if exist (The # coming after lmd represents the order) Example: `lmd2` is the second left most child |
| lns | Left nearest sibling |Considers the left nearest sibling of the current node in the dependency tree if exist (The # coming after lns represents the order) Example: `lns2` is the second left nearest sibling |
| rmd | Right most child |Considers the right most child of the current node in the dependency tree if exist (The # coming after lns represents the order) Example: `rmd3` is the third right most child |
| rns | Right nearest sibling|Considers the right nearest sibling of the current node in the dependency tree if exist (The # coming after lns represents the order) Example: `rns4` is the fourth right nearest sibling|


##Feature Template 
The following is an example of the POS feature template.
	 
	<feature template>
	
		<!-- 1-gram features -->
		<feature f0="i:f2"/>
		
		<!-- 2-gram features-->
		<feature f0="i-1:f3" f1="i:f3"/>

		<!-- 3-gram features-->
		<feature f0="i-1:f3" f1="i+1:f3" f2="i+2:f3" visible="false"/>
	
	<feature template/>

We can represent the n-grams by using `<feature f0= ""  f1= "" />` where `f0` ... `fn` represents a sequence of features.  
`i` represents the index of the word (Example: `i-1` represents the previous word).   
`visible="false"` means the feature is not currently being used  
`:` represents a mapping to a specfic word feature in the table above.  

  
 
The following is an example of the dependency tree feature template.  
 
 	<feature template>
 	 
 	<feature f0="i_h:d"/>
    <feature f0="j_h:d"/>
    <feature f0="i_lmd2:d"/>
    <feature f0="k-1:p" f1="j:p"/>

 	</feature template/>

For features used in dependency parsing `i` represents the left node, `j` represents the right node, and `k` represents a potential third node in the tree.  
`_` is used with `rmd`, `lmd`, `rns`, and `lns`. 
  
  
Other Examples:   
	`<feature f0="i:f">` The word form of this word   
	`<feature f0="i-2:f2"/>` The simplified word form of the previous previous word   
	`<feature f0="i-2:f3" f1="i-1:f3"/>` The lower cased simplified word form of the previous previous word and lower cased simplified word form of the previous word.  
	`<feature f0="i_lmd2:d"/>` The dependency label of the second left most child of this word/node

	
| Word/Node Features  | Feature Meanings  | Usage Examples |
|:------------- |:---------------:| :---------------------:|
| f    | Word form | `<feature f0="i:f">` |
| f2      | Simplified word form      | `<feature f0="i-2:f2"/>` |
| f3 | Lowercased simplified word form| `<feature f0="i-2:f3" f1="i-1:f3"/>` |
| m | Word lemma        | `<feature f0="i:m">` |
| f4 | Word shape | `<feature f0="i+1:f4"/>`|
| pf | Prefix        |  `<feature f0="i:pf1"/>` |
| sf | Suffix        |  `<feature f0="i:sf1"/>` |
| p | POS tag     		|  `<feature f0="i-1:p"/>` |
| n | Named entity tag |  `<feature f0="i-1:n"/>`|
| d | Label        | `<feature f0="i-1:l"/>`|
| v | Valency        | `<feature f0="i-1:v"/>`|
| lv | Left valency        |  `<feature f0="i-1:lv"/>`|
| rv | Right valency      | `<feature f0="i-1:rv"/>` |
| b | If first or last token | 	`<feature f0="i:b1" note="input is the last token"/>` |
| ft | Value of specific feature |  `<feature f0="i:ft=f14"/>` |
| orth | Orthographic features |  `<feature f0="i:orth"/>`|
| ds | Children features |  `<feature f0="i:ds"/>`|
| ds2 | Grandchildren features |  `<feature f0="i:ds2"/>`|
| a | Ambiguity class | `<feature f0="i+1:a" f1="i+2:a"/>`|
| lmd | Left most child | `<feature f0="i_lmd2"/>`|
| lns | Left nearest sibling | `<feature f0="i_lns"/>`|
| rmd | Right most child | `<feature f0="i_rmd"/>`|
| rns | Right nearest sibling| `<feature f0="i_rns2"/>`|
 


