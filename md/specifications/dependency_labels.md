# ClearNLP Dependency Labels

## Current Labels

| Label         | Description                       | Since |
|:------------- |:----------------------------------|:-----:|
| ACL           | Clausal modifier of noun          | 3.1.0 |
| ACOMP         | Adjectival complement             | 1.0.0 |
| ADVCL         | Adverbial clause modifier         | 1.0.0 |
| ADVMOD        | Adverbial modifier                | 1.0.0 |
| AGENT         | Agent                             | 1.0.0 |
| AMOD          | Adjectival modifier               | 1.0.0 |
| APPOS         | Appositional modifier             | 1.0.0 |
| ATTR          | Attribute                         | 1.0.0 |
| AUX           | Auxiliary                         | 1.0.0 |
| AUXPASS       | Auxiliary (passive)               | 1.0.0 |
| CASE          | Case marker                       | 3.1.0 |
| CC            | Coordinating conjunction          | 1.0.0 |
| CCOMP         | Clausal complement                | 1.0.0 |
| COMPOUND      | Compound modifier                 | 3.1.0 |
| CONJ          | Conjunct                          | 1.0.0 |
| CSUBJ         | Clausal subject                   | 1.0.0 |
| CSUBJPASS     | Clausal subject (passive)         | 1.0.0 |
| DATIVE        | Dative                            | 3.1.0 |
| DEP           | Unclassified dependent            | 1.0.0 |
| DET           | Determiner                        | 1.0.0 |
| DOBJ          | Direct Object                     | 1.0.0 |
| EXPL          | Expletive                         | 1.0.0 |
| INTJ          | Interjection                      | 1.0.0 |
| MARK          | Marker                            | 1.0.0 |
| META          | Meta modifier                     | 1.0.0 |
| NEG           | Negation modifier                 | 1.0.0 |
| NOUNMOD       | Modifier of nominal               | 3.1.0 |
| NPMOD         | Noun phrase as adverbial modifier | 3.1.0 |
| NSUBJ         | Nominal subject                   | 1.0.0 |
| NSUBJPASS     | Nominal subject (passive)         | 1.0.0 |
| NUMMOD        | Number modifier                   | 3.1.0 |
| OPRD          | Object predicate                  | 1.0.0 |
| PARATAXIS     | Parataxis                         | 1.0.0 |
| PCOMP         | Complement of preposition         | 1.0.0 |
| POBJ          | Object of preposition             | 1.0.0 |
| POSS          | Possession modifier               | 1.0.0 |
| PRECONJ       | Pre-correlative conjunction       | 1.0.0 |
| PREDET        | Pre-determiner                    | 1.0.0 |
| PREP          | Prepositional modifier            | 1.0.0 |
| PRT           | Particle                          | 1.0.0 |
| PUNCT         | Punctuation                       | 1.0.0 |
| QUANTMOD      | Modifier of quantifier            | 1.0.0 |
| RELCL         | Relative clause modifier          | 3.1.0 |
| ROOT          | Root                              | 1.0.0 |
| XCOMP         | Open clausal complement           | 1.0.0 |


## Deprecated Labels

| Label         | Description                       | Since | Notes |
|:------------- |:----------------------------------|:-----:|:------|
| COMPLM        | Complementizer                    | 3.0.0 | Replaced to `mark`     |
| INFMOD        | Infinitival modifier              | 3.0.0 | Replaced to `acl`      |
| PARTMOD       | Participal modifier               | 3.0.0 | Replaced to `acl`      |
| HMOD          | Modifier in hyphenation           | 3.1.0 | Replaced to `compound` |
| HYPH          | Hyphen                            | 3.1.0 | Replaced to `punct` |
| IOBJ          | Indirect object                   | 3.1.0 | Replaced to `dative`   |
| NUM           | Number modifier                   | 3.1.0 | Replaced to `nummod`   |
| NUMBER        | Number compound modifier          | 3.1.0 | Replaced to `compound` |
| NMOD          | Modifier of nominal               | 3.1.0 | Replaced to `nounmod` |
| NN            | Noun compound modifier            | 3.1.0 | Replaced to `compound` |
| NPADVMOD      | Noun phrase as adverbial modifier | 3.1.0 | Replaced to `npmod`    |
| POSSESSIVE    | Possessive modifier               | 3.1.0 | Replaced to `case`     |
| RCMOD         | Relative clause modifier          | 3.1.0 | Replaced to `relcl`    |


## Subjects

### Nominal subject

A nominal subject (`nsubj`) is a non-clausal constituent in the subject position of an active verb.

### Nominal subject (passive)

A nominal passive subject (`nsubjpass`) is a non-clausal constituent in the subject position of a passive verb.

### Clausal subject

A clausal subject (`csubj`) is a clause in the subject position of an active verb.

### Clausal subject (passive)

A clausal passive subject (`csubjpass`) is a clause in the subject position of a passive verb. 

### Agent

An agent (`agent`) is the complement of a passive verb that is the surface subject of its active form.

### Expletive

An expletive (`expl`) is an existential there in the subject position.

## Objects

### Direct object

A direct object (`dobj`) is a noun phrase that is the accusative object of a (di)transitive verb.

### Dative

A dative (`dative`) is a nominal or prepositional object of dative-shifting verb.

### Attribute

An attribute (`attr`) is a noun phrase that is a non-VP predicate usually following a copula verb.

### Object predicate

An object predicate (`oprd`) is a non-VP predicate in a small clause that functions like the predicate of an object.

## Complements

### Clausal complement

A clausal complement (`ccomp`) is a clause with an internal subject that modifies the head of an `ADJP|ADVP|NML|NP|WHNP|VP|SINV|SQ`. 

### Open clausal complement

An open clausal complement (`xcomp`) is a clause without an internal subject that modifies the head of an `ADJP|ADVP|VP|SINV|SQ`.

### Adjectival complement

An adjectival complement (`acomp`) is an adjective phrase that modifies the head of a `VP|SINV|SQ`, that is usually a verb.

## Nominals

### Appositional modifier

An appositional modifier (`appos`) of an `NML|NP` is a noun phrase immediately preceded by another noun phrase, which gives additional information to its preceding noun phrase.

### Clausal modifier

A finite or non-finite clausal modifier (`acl`) is either an infinitival modifier is an infinitive clause or phrase that modifies the head of a noun phrase, or a participial modifier is a clause or phrase whose head is a verb in a participial form (e.g., gerund, past participle) that modifies the head of a noun phrase, or a complement.

### Releative clause modifier

A relative clause modifier (`relcl`) is a either relative clause or a reduced relative clause that modifies the head of an `NML|NP|WHNP`.

### Determiner

A determiner (`det`) is a word token whose pos tag is `DT|WDT|WP` that modifies the head of a noun phrase.

### Pre-determiner

A predeterminer (`predet`) is a word token whose pos tag is PDT that modifies the head of a noun phrase.

### Numeric modifier

A numeric modifier (`nummod`) is any number or quantifier phrase that modifies the head of a noun phrase.

### Adjectival modifier

An adjectival modifier (`amod`) is an adjective or an adjective phrase that modifies the meaning of another word, usually a noun.

### Possession modifier

A possession modifier (`poss`) is either a possessive determiner (PRP$) or a NML|NP|WHNP containing a possessive ending that modifies the head of a ADJP|NML|NP|QP|WHNP.

### Modifier of nominal

A modifier of nominal (`nmod`) is any unclassified dependent that modifies the head of a noun phrase.

## Adverbials

### Adverbial modifier

An adverbial modifier (`advmod`) is an adverb or an adverb phrase that modifies the meaning of another word.

### Adverbial clause modifier

An adverbial clause modifier (`advcl`) is a clause that acts like an adverbial modifier.

## Negation modifier

A negation modifier (`neg`) is an adverb that gives negative meaning to its head.

## Noun phrase as adverbial modifier

An adverbial noun phrase modifier (`npmod`) is a noun phrase that acts like an adverbial modifier.

## Prepositions

### Object of a preposition

An object of a preposition (`pobj`) is a noun phrase that modifies the head of a prepositional phrase, which is usually a preposition but can be a verb in a participial form such as `VBG`.

### Complement of a preposition

A complement of a preposition (`pcomp`) is any dependent that is not a `pobj` but modifies the head of a prepositional phrase.

## Coordination

### Conjunct

A conjunct (`conj`) is a dependent of the leftmost conjunct in coordination.

### Coordinating conjunction

A coordinating conjunction (`cc`) is a dependent of the leftmost conjunct in coordination.

### Pre-correlative conjunction

A pre-correlative conjunction (`preconj`) is the first part of a correlative conjunction that becomes a dependent of thefirst conjunct in coordination.

### Prepositional modifier

A prepositional modifier (`prep`) is any prepositional phrase that modifies the meaning of its head.

## Auxiliaries

### Auxiliary

An auxiliary (`aux`) is an auxiliary or modal verb that gives further information about the main verb (e.g., tense, aspect).

### Auxiliary (passive)

A passive auxiliary (`auxpass`) is an auxiliary verb, be, become, or get, that modifies a passive verb.

## Compund words

### Compound

A compound (`compound`) is either a noun modifying the head of noun phrase, a number modifying the head of quantifier phrase, or a hyphenated word (or a preposition modifying the head of the prepositioanl phrase).

### Particle

A particle (`prt`) is a preposition in a phrasal verb that forms a verb-particle construction.

### Case marker

A case marker (`case`) is either a possessive marker, ...

### Marker

A marker (`mark`) is either a subordinating conjunction (e.g., although, because, while) that introduces an adverbial clause modifier, or a subordinating conjunction, if, that, or whether, that introduces a clausal complement.

## Miscellaneous

### Unclassified dependent

An unclassified dependent (`dep`) is a dependent that does not satisfy conditions for any other dependency.

### Meta modifier

A meta modifier (`meta`) is code (1), embedded (2), or meta (3) information that is randomly inserted in a phrase￼￼￼or clause.

### Parenthetical modifier

A parenthetical modifier (`parataxis`) is an embedded chunk, often but not necessarily surrounded by parentheticalnotations (e.g,. brackets, quotes, commas, etc.), which gives side information to its head.

### Punctuation

Any punctuation (`punct`) is assigned the dependency label PUNCT.

### Root

A root (`root`) is the root of a tree that does not depend on any node in the tree but the artificial root node.