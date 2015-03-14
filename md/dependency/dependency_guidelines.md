# Dependency Labels


| Label  | Description  | Example |
|:------------- |:---------------:| :-------------|
| ACOMP     | Adjectival complement | Adjective phrase that modifies the head of a `VP` \| `SINV` \| `SQ`, that is usually a verb. Example: "She looks so beautiful" `so beautiful` is the ACOMP of `looks`  |
| ADVCL      | Adverbial clause modifier| Acts like an adverbial modifier (ADVMOD) A subordinate clause or open clause is considered an ADVCL if it doesn't satisfy an other dependency relation. Example: "She came to see me" `to see me` is the ADVCL of `came`|
| ADVMOD | Adverbial modifier | Adverb of adverb phrase that modifies the meaning of another word. Other grammatical categories can also be ADVMOD if they modify adjectives. Example: "I did not know her" `not` is a ADVMOD of `know`  |
| AGENT | AGENT |  Complement of a passive verb that is the surface subject of its active form. Example: "The car was bought by John." `by John` is the agent that is a complement of `bought` (The prep `by` is included as part of AGENT)  |
| AMOD | Adjectival modifier |  Adjective or adjective phrase that modifies the meaning of another word. Example: "A beautiful girl" `beautiful` is AMOD to `girl` |
| APPOS | Appositional modifier  | APPOS of an NMP \| NP is a noun phrase immediately preceded by another noun phrase, which gives additional information to its preceding noun phrase. Example: "John my brother" `my brother` is the APPOS of `John`|
| ATTR | Attribute | Noun phrase that is a non-VP predicate that usually follows a copula verb. Example: "This product is a global brand" `a global brand` is the ATTR of `is`  |
| AUX | Auxiliary |Modal verb that gives further information about the main verb. Example: "I am going to meet her tomorrow" `am going to` is the AUX of `meet` (The prep `to` is considered an AUX)|
| AUXPASS | Auxiliary (passive) | An auxiliary verb, `be`, `become`, or `get`, that modifies a passive verb. Example: "We will `get` married." |
| CC | Coordinating conjunction | Dependent of the leftmost conjunct in coordination. Example: "John, Mary, and Sam" `and` is the CC of `John` |
| CCOMP | Clausal complement |  Clause with an internal subject that modifies `ADJP`\| `ADVP` \| `NML` \| `NP` \| `WHNP` \| `VP` \| `SINV` \| SQ. Example: "She left no matter how I felt" `how I felt` is the CCOMP of `matter` |
| COMPLM | Complementizer |  Subordinating conjunction, if, that, or whether, that introduces a clausal complement. A COMPLM is assigned when a CCOMP is found. Example: "She said that she wanted to go" `that` is the COMPLM of `wanted` |
| CONJ | Conjunct | Dependent of the leftmost conjunct in coordination. Leftmost conjunct becomes head of a coordinated phrase. Example: "John, Mary, and Sam" `Mary` and `Sam` are both conjunctions of `John`|
| CSUBJ | Clausal subject | Clause in the subject position of an active verb. Example: "What I said was true" `What I said` is the CSUBJ of active verb `was`  |
| CSUBJPASS | Clausal subject (passive) | Clause in the subject position of a passive verb. Example: "Whoever misbehaves will be dismissed." `Whoever misbehaves` is the CSUBJPASS of passive verb `dismissed`   |
| DEP | Unclassified dependent |  Dependent that does not satisfy conditions for any other dependency.  |
| DET | Determiner | Word whose POS tag is DT \| WDT \| WP that modifies the head of a noun phrase. Example: "The U.S. military" `The` is the DET of `military`|
| DOBJ | Direct Object | Noun phrase that is the accusative object of a (di)transitive verb. Example: "She bought me these books" `these books` is the DOBJ of `bought` |
| EXPL | Expletive | Existential `there` in subject position. Example: "`There` was an explosion" |
| HMOD | Modifier in hyphenation |  Constituent preceding a hyphen that modifies constituent following the hyphen. Example: "New-York Times" `New` modifies `York`|
| HYPH | Hyphen | Modifies a constituent following the hyphen. Example: "New-York Times" `-` modifies `York`|
| INFMOD | Infinitival modifier | Infinitive clause or phrase that modifies the head of a noun phrase. Example: "I have too much homework to do" `to do` is the INFMOD of `homework` |
| INTJ | Interjection |  Expression made by the speaker of an utterance. Example: "I `um` will throw a party"  |
| IOBJ | Indirect object | Noun phrase that is dative of a ditransitive verb. Example: "She bought me these books" `me` is the IOBJ of `bought` |
| MARK | Marker | Subordinating conjunction that introduces an adverbial clause modifier. Example: (e.g., although, because, while) "She came because she liked me" "`because` she liked me" is the MARK of `liked`  |
| META | Meta modifier |  Code, embedded, or meta information that is randomly inserted in a phrase or clause. Example: `Applause` Thank you |
| NEG | Negation modifier | Adverb that gives negative meaning to its head. Example: "She decided not to come" `not` is the NEG of `come`  |
| NMOD | Modifier of nominal | Any unclassified dependent that modifies the head of a noun phrase.|
| NN | Noun compound modifier | Any noun that modifies the head of a noun phrase. Example: "The US military" `US` is the NN of `military` |
| NPADVMOD | Noun phrase as ADVMOD |  Noun phrase that acts like an adverbial modifier. A noun phrase modifying either an adjective or an adverb is also considered NPADVMOD. Example: "I met her last week" `last week` is the NPADVMOD of `met` |
| NSUBJ | Nominal subject | Non-clausal constituent in the subject position of an active verb. Example: "Earlier was better" `Earlier` is the NSUBJ of the active verb `was` |
| NSUBJPASS | Nominal subject (passive) | Non-clausal constituent in the subject position of an passive verb. Example: "We will get married" `We` is the NSUBJPASS of the passive verb `married` |
| NUM | Number modifier | Any number of quantifier phrase that modifies the head of a noun phrase. Example: "14 degress" `14` is the NUM of `degrees`|
| NUMBER | Number compound modifier | A cardinal number that modifies the head of a quantifier phrase. Example: "Seven million dollars" `Seven` is a NUMBER that modifies `million` |
| OPRD | Object predicate |  A non-VP predicate in a small clause that functions like the predicate of an object. Example: "She calls me her friend" `her friend` is the OPRD and `me` is DOBJ of `calls` |
| PARATAXIS | Parataxis | Embedded chunk, often but not necessarily surrounded by parenthetical notations which gives side information to its head. Example: "She, I mean, Mary was here" `I mean` is PARATAXIS to `was` |
| PARTMOD | Participal modifier | A clause or phrase whose head is a verb in a participial form (e.g., gerund, past participle) that modifies the head of a noun phrase. Example: "I went to the party hosted by her" `hosted by her` is the PARTMOD of `party`  |
| PCOMP | Complement of preposition | Any dependent that is not a `POBJ` but modifies the head of a prepositional phrase. Example: "I agree with what you said" `what you said` is the PCOMP of `with`|
| POBJ | Object of preposition | Noun phrase that modifies the head of a prepositional phrase which is usually a preposition but can be a verb in a participial form such as `VBG`. Example: "On the table" `the table` is the POBJ of `On`  |
| POSS | Possession modifier |  Either a possessive determiner (`PRP$`) or a NML \| NP \| WHNP containing a possessive ending that modifies head of a `ADJP` \| `NML` \| `NP` \| `QP` \| `WHNP` Example: "I bought his car"    `his` is POSS of `car` |
| POSSESSIVE | Possessive modifier | A word token whose POS tag is `POS` that modifies the head of a noun phrase. Example: "John's car" `'s` is POSSESSIVE of `John` |
| PRECONJ | Pre-correlative conjunction |  The first part of a correlative conjunction that becomes a dependent of the first conjunct in the coordination. Example: "Either John or Mary" `Either` is the PRECONJ of `John` |
| PREDET | Predeterminer | A word token whose POS tag is `PDT` that modifies the head of a noun phrase. Example: "Such a beautiful woman" `Such` is the PREDET of `woman`|
| PREP | Prepositional modifier |  Any prepositional phrase that modifies the meaning of its head. Example: "Or just give it to me" `to me` is a PREP of `give`|
| PRT | Particle |  Preposition or phrasal verb that forms a verb-particle construction. Example: "Shut down the machine" `down` is the PRT of `Shut` |
| PUNCT | Punctuation | Any punctuation is PUNCT |
| QUANTMOD | Quantifier phrase modifier | Dependent of the head of a quantifier phrase. Example: "Five to six" `Five` is a QUANTMOD to `six` and `to` is also a QUANTMOD to `six` |
| RCMOD | Relative clause modifier |  Either a relative clause or a reduced relative clause that modifies the head of `NML` \| `NP` \| `WHNP`. Example: "I bought the car that I wanted" `that I wanted` is the RCMOD of `car` |
| ROOT | Root | Root of the tree that does not depend on any node of the tree but the artificial root node whose ID is 0. A tree can have multiple roots if top constituents contains more than on child in the original constituent tree.|
| XCOMP | Open clausal complement |  Clause without an internal subject that modifies the head of an `ADJP` \| `ADVP` \| `VP` \| `SINV` \| `SQ`. Example: "I am ready to go" `to go` is the XCOMP of `ready`|




