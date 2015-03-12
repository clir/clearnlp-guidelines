
  

# Feature Extraction 
Features are stored as a xml file in the src/main/resource folder. The format is the following: 
	
	 
	<feature template>
	
		<!-- 1-gram features -->
		<feature f0="i:f2"/>
		
		<!-- 2-gram features-->
		<feature f0="i-1:f3" f1="i:f3"/>

		<!-- 3-gram features-->
		<feature f0="i-1:f3" f1="i+1:f3" f2="i+2:f3" visible="false"/>
	
	<feature template/>
	 
**f0** to **fn** represents n-grams   
'**i**' represents the index of the word (EX: i-1 represents the previous word)  
'**:**' represents a mapping to a specfic word feature in the table below  
If **visible="false"** the feature is not used

Examples:   
	**\<feature f0="i:f">** The word form of this word   
	**\<feature f0="i-2:f2"/>** The simplified word form of the previous previous word
 




| Word Feature Key  | Feature Meaning  | Example |
|:------------- |:---------------:| :---------------------:|
| f    | Word form | **\<feature f0="i:f">** |
| f2      | Simplified word form      | **\<feature f0="i-2:f2"/>** |
| f3 | Lowercased simplified word form        |  **\<feature f0="i-2:f3" f1="i-1:f3"/>** |
| m | Word lemma        | **\<feature f0="i:m">**  |
| f4 | Word shape | 	**\<feature f0="i+1:f4"/>**|
| pf | Prefix        |  **\<feature f0="i:pf1" visible="false"/>** |
| sf | Suffix        |  **\<feature f0="i:sf1"/>** |
| p | POS tag     		|  **\<feature f0="i-1:p"/>** |
| n | Named entity tag |  **\<feature f0="i-1:n"/>**|
| d | Label        | **\<feature f0="i-1:l"/>** |
| v | Valency        | **\<feature f0="i-1:v"/>**|
| lv | Left valency        |  **\<feature f0="i-1:lv"/>**|
| rv | Right valency      | **\<feature f0="i-1:rv"/>** |
| b | If first or last token | 	**\<feature f0="i:b1" note="input is the last token"/>** |
| ft | Value of specific feature |  **\<feature f0="i:ft=f14"/>** |
| orth | Orthographic features |  **\<feature f0="i:orth"/>**|


