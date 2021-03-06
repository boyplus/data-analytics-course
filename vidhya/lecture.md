# Module 1 : Introduction to Nataural Language Processing

### Data types : Structured and Unstructured

#### 1.Structure Dataset

- Fixed dimensions
- Well organized
- Tabular data, key-value pairs -> ex.data base, excel (column and row), json

#### 2.Unstructured Dataset

- No fixed dimensions, no structure
- audios, videos, images, text

#### Text dataset

- Example of text data
  - Social media: tweets, posts, comments
  - Conversations: messgaes, emails, charts
  - Articles: news, blogs, transcripts
- Words arranged in a meaningful manner
- Written form of language
- Grammar and defined structures

#### Process of Nataural Langiage Processing (NLP)

**Text data -> NLP -> Information and insights**

- Deriving useful information from text
- Applied NLP : NLP + Human Interaction

---

#### Business Use Case 1

Improve smartphone sales with Audience Insights

NLP Solution

- Analyze : social media data
- Identify : most talked issues, semtiments
- Model : cause of negative sentiment

----

#### Business Use Case 2

Automic Categorization of Customer Queries

NLP Solution:

- Analyze : top keyword and phrases
- Map : keywords and department descriptions
- Model : rules for automatic categorization

---

#### Business Use Case 3

Identify Patients at Risk of Cancer

A hospital wants to create a model to early detect the patients at risk

NLP Solution

- Analyze: history of patients and drug prescibed
- Identify : entities from their history
- Business rules to classify the risk levele of patients

---

# Module 2 : Learn to use Regular Expression

> Simply put, regular expression or regex is a requence of character(s) mainly used to find and replace patterns in a string or file. Hence, they are pretty handy in NLP tasks.

Some of the common uses of regular expressions are:

- Search a string
- Finding a string
- Replace part of string



#### What are Regular Expressions

- Patterns of special characters having an associated textual meaning (ex: "\d" : "numbers")
  - John's salary is $**500**, he lives in the block **5** of the **3**rd Manhatten street. He was born in the year **1990**.
- Wild card expressions for matchingm searching and parsing strings.
- USed fir writting rule-based information mining systems.



#### Applications of Regular Expressions

- Segmentation of words from sentences
- Segmentation of sentences from parapgrahs.
- Text cleaning - noise removal
- Information retrival from texts (ex - chatbots / news data sets / search engine queries)



#### Examples of Regular Expressions

**Group and Ranges**

- . : any character except new line (\n)
- (a|b) : a or b
- (...) : group
- [abc] Range (a or b or c)
- [^abc] Not (a or b or c)
- [a-q] : lower case letter from a to q
- [A-Q] Upper case letter from A to Q
- [0-7] Digit from 0 to 7

**Quantifiers**

- *(0 or more)
- +(1 or more)
- ? (0 or 1)
- {3} Exactly 3
- {3,} 3 or more
- {3,5} 3 or 4 or 5

**Character Classes**

- /s White space
- /S Not shite space
- /d Digit
- /D Not digit
- /w Word
- /W Not word

**Special Characters**

- \n new line
- \t Tab



#### Regular Expression Functions

- match: find the first occurence of pattern in the string
- search: locates the pattern in string
- findall: find all occurences of patterns in the string
- sub: ssearch and replace
- split: split the text by the given regular expression pattern



#### Regular expression in python

```python
import re
string = "Tiger is the nationla animal of India"
pattern = "Tiger"
result = re.match(pattern,string).group(0)
# Tiger

string = "The national animal of India is Tiger"
pattern = "Tiger"
result = re.search(pattern,string).group(0)
# Tiger

string = "national animal is tiger and national sport is hockey"
pattern = "national"
result = re.findall(pattern,string)
# ['national','national']
```

```python
import re
text = "John 34-3456 12-05-2007, XYZ 56-4532 11-11-2011"
date_pattern = r'\d{2}-\d{2}-\d{4}'
# pattern is two digits number - two digits numer - 4 digits number
re.findall(date_pattern,text)
# ['12-05-2007','11-11-2011']

text = "this is;a,sample,text,string"
pattern = r'[;,\s]'
# pattern is ; or , or white space (from group and ranges)
re.split(pattern,text)
# ['this','is','a','sample','text','string']

text = "cricket is a popular sport in India"
pattern = "India"
replacement = "the world"
re.sub(pattern,replacement,text)
# 'Cricket is a popular sport in the world'

```



## Module3 First Step of NLP - Text Processing

### Tokenization and Text Normalization

**Corpus** -> Collection of text documents

Corpus > Documents > Paragraphs > Sentences > Tokens

Tokens : Smaller unit of a text (words, phrasesm ngrams)

Ngrams : combinations of N words / Character together

**Example**

Sentence: I love my phone

Unigrams (n = 1) : I, Love, my, phone

Bigrams (n=2) : I love, love my, my phone

Trigrams (n = 3) : I love my, love my phone

**Tokenization**

- Process of spliting a text object into smaller units (tokens)
- Smaller Units: words, numbers, symbols, ngrams, characters
- White space tokenizer / Unigram tokenizer
  - Sentence : "I went to New-York to play football"
  - Tokens : "I", "went", "to", "New-York", "to", "play", "football"
- Regular expression tokenizer
  - Sentence: "Football,Cricket;Golf Tennis"
  - re.split(r'[,;\s],line')
  - Tokens: "Football","Cricket","Golf","Tennis"

**Normalization**

- Morpheme : base form of a word
- Structure of token : <prefix> <morpheme> <suffix>
  - Example: Aninationalist : Anti + national + ist
- Normalization : Process of converting a token into its base form (morpheme)
- Helpful in reducing data dimensionality, text cleaning
- Types : Stemming and Lemmatization



**Normalization : Stemming**

- Elementary rule based process of removal of inflectional forms from a token

- Outputs the stem of a word

  - Example : "laughing", "laughed", "laughs", "laugh" >>> "laugh"

- May generate **non-meaningful** terms

  - Example : "his team are not winning"

  - > hi team are not winn

<table>
  <tr>
    <th>Form</th>
    <th>Suffix</th>
    <th>Stem</th>
  </tr>
  <tr>
    <td>Studies</td>
    <td>-es</td>
    <td>studi</td>
  </tr>
  <tr>
    <td>Studying</td>
    <td>-ing</td>
    <td>study</td>
  </tr>
</table>



**Normalization : Lemmatization**

- Systematic process for reducing a token to its lemma
- Makes use of vocabularym word structure, part of speech tags and grammar relations
- Example
  - am, are, is >> be
  - running, ran, run, rans >> run
- Running, 'verb' >> run
- Running, 'noun' >> running



### Part of Speech Tagging and Grammar Parsing

#### Part of Speech Tags

- Defines the syntactic context and role of words in the sentence
- Common POS Tags : Nouns, Verbs, Adjectives, Adverbs
- Example
  - Sentence : David has purchased a new laptop from Apple Store
    - ???			noun + verb + (adjective) noun
- Defined by their relationship with the adjacent words
- Machine learning or Rule based process
- Uses
  - Text cleaning
  - Feature engineering tasks
  - Word sense disambiguation
- Example
  - Sentence1 : Please **book** my flight for NewTork
  - Sentence2 : I like to read a **book** on NewYork



#### Constiruency Grammar

- Constituents : Words / phrases / group of words
- Constituency Grammar : Organize any sentence into constituents using their properties
- Properties : Part of Speech Tags / Noun Phrases / Verb Phrases

Sentence : <subject> <context> <object>

<subject> The cats / The digs / They

<context> are running / are barking / are eating

<obj> in the park / happliy / since the morning



#### Dependency Grammar

- Words of a sentence depends on which other words (dependencies)
  - Example : Modifiers (barking dog)
- Organize words of a sentence according to their dependencies
- All the word are directly or indirectly linked to the root using links
- These dependencies represents relationship among the words in a sentence

