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




### Feature Extraction
### Classification






