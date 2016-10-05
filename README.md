# Sentiment Analysis
###What is sentiment analysis? <br>

Sentiment analysis is the process by which we use statistical techniques in order to gauge/understand opinions and sentiment of a piece of text. <br>

### Example: Movie Reviews  <br>
• Unbelievably disappointing, directors should kill themselves  <br>
• Amazing movie, great plot twist and action scenes!  <br>
• Wow Nicholas Cage is really bad  <br>

### Example: Twitter Sentiment
Connor et al '10
Twitter Sentiment vs Gallup Poll of Consumer Confidence
![Image of Twitter Sentiment](https://cloud.githubusercontent.com/assets/7456865/19132943/8a9fb33e-8b1b-11e6-9a6f-270d7203e1a8.png)

### Example: Product Reviews
![Image of product review](https://cloud.githubusercontent.com/assets/7456865/19133130/5b2c5eb2-8b1c-11e6-8867-8eadcaca58ca.png)

## Tasks
- Easy Tasks in Sentiment Analysis: Is the text positive or negative?
- Medium Tasks in Sentiment Analysis: Score the text sentiment from -1 to 1
- Hard Tasks in Sentiment Analysis: WHY does the user feel the way s/he does?

## Process:
1. Scrape
2. Clean
3. Feature Extraction
4. Classification

### Scrape
You (usually) have to scrape your data, usually from the web. We can use BeautifulSoup to scrape data OR call it from a web API.

```python 
def main(query):
	url = "http://www.rottentomatoes.com/search/?search="
	raw_string = re.compile(r' ')
	fullQuery = raw_string.sub('+', query)
	r = requests.post(url + fullQuery)
	soup = bs(r.content)
	if soup.find('ul',{'class':"results_ul"}):
		tags = soup.findAll('li',{'class':"media_block bottom_divider clearfix"})
		results = {}
		for tag in tags:
			info = MovieSearchResult(tag)
			resultNum = str(tags.index(tag) + 1)
...
```

### Clean
- html markup
- Tokenize
- n-gram?
- Capitalization
- Punctuation
- Lemmatize vs Stem?

```
<p>
This film isn't for all people. That's to say about a lot of movies in
general of course, but this one in particular brings up a big clashing
point between critics; What do we want to see in our movies? What is
more important, to portray a fictional setting for the sake of giving
people a mind blowing visual experience or to amuse and amaze them with
clever plot twists and intelligent dialogs?<br><br>First lets analyze what exactly this film is made of. Basically, the
whole thing is just one epic fighting scene after another. Most
</p>

```

### Feature Extraction

- Emojis?
- Unigrams
- Linguistic Tokens:  Noun, nounphrases,adjectives, adverbs are usually used to express sentiment
![sentiment features](https://cloud.githubusercontent.com/assets/7456865/19133823/fea2bbba-8b1f-11e6-8ef7-cd22a497a0e1.png)

### Classification

Now we have our features. How do we categorize these?

"In machine learning and statistics, classification is the problem of identifying to which of a set of categories (sub-populations) a new observation belongs, on the basis of a training set of data containing observations (or instances) whose category membership is known. " - Wikipedia

Popular Classifiers: Naive-Bayes, Linear Regression, SVM, Random Forest, etc

Classifiers are either supervised, unsupervised, semi-supervised.

#### Splitting

You should split your training set.

#### Cross-Validation

Average your scores across 10 folds. k-fold cross validation.

## Evaluation of Success

### Precision:
How many of the retrieved documents are relevant?
Precision @ 10: How many of the top 10 documents you retrieve are good?


### Recall
How many of total relevant documents were retrieved?
Recall @ 10: How many of the actual top 10 documents did you retrieve?

### F-score:
Harmonic Mean of Recall and Precision:
![formula for f-score](https://cloud.githubusercontent.com/assets/7456865/19134136/cb2b5894-8b21-11e6-8413-5512f6d6d43a.png)

# Latent Dirichlet Allocation

Generative statistical model that groups similar documents together. NOT supervised, there is no training data!

![LDA image](http://deliveryimages.acm.org/10.1145/2140000/2133826/figs/f1.jpg)

## Process

1. Go through each document, and randomly assign each word in the document to one of the K topics. <br>
2. Go through each word w in d <br>
3. Calculate p(topic t | document d) = the proportion of words in document d that are currently assigned to topic t <br>
4. p(word w | topic t) = the proportion of assignments to topic t over all documents that come from this word w. <br>
5. Reassign w a new topic, where you choose topic t with probability p(topic t | document d) * p(word w | topic t) this is essentially the probability that topic t generated word w <br>

# Using LDA or Sentiment Analysis for projects

### Few libraries available:

1. coreNLP
2. gensim
3. nltk

Sentiment Analysis NLTK tutorial with NB and tokenization: http://www.nltk.org/howto/sentiment.html
Gensim LDA: https://radimrehurek.com/gensim/models/ldamodel.html





