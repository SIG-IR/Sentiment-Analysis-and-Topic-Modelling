# Sentiment-Analysis-and-Topic-Modelling
SIGIR lecture on sentiment analysis, topic models, and nlp/ml libraries

## Sentiment Analysis
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
Easy Tasks in Sentiment Analysis: Is the text positive or negative?
Medium Tasks in Sentiment Analysis: Score the text sentiment from -1 to 1
Hard Tasks in Sentiment Analysis: WHY does the user feel the way s/he does?

## Process:
1) Scrape
2) Clean
3) Feature Extraction
4) Classification

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


### Recall
How many of total relevant documents were retrieved?

### F-score:
Harmonic Mean of Recall and Precision:
![formula for f-score](https://cloud.githubusercontent.com/assets/7456865/19134136/cb2b5894-8b21-11e6-8413-5512f6d6d43a.png)



