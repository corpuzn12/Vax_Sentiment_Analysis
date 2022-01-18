## **Overview**
<p> 
The CDC has officially confirmed the first US case of the Omicron variant earlier this month and the urgency to reach the remaining 80 million unvaccinated Americans is back at the forefront. However, the sentiments of these individuals range from distrust to blind faith towards more holistic approaches against COVID-19 and thus, it might be relevant for government agencies to analyze the most candid sentiments of the public towards vaccines in order to vaccinate those who remain hesitant.<p/>

The fear of side effects and the desire to “wait and see if vaccines are safe” were cited as the top two concerns of a group of unvaccinated individuals that the Census Household Pulse surveyed in July of 2021. Given that enough time has passed since the vaccine roll outs occurred, it might be interesting to know if the perception of vaccines became more positive over time.<p/>


## **The Dataset** 
<p/>
To answer this inquiry, a dataset of tweets about Pfizer was sourced from Kaggle.This dataset contains 10,919 tweets and includes 9 features such as user_name, user_location, user_followers, date, text, hashtags, retweets, favorites and more. These tweets  were collected between December 2020 and November 2021. Only the “date” and “text” features were used in the NLP analysis portion of this project.

## **Methodology**
In analysing this dataset, several unsupervised learning techniques were used to gradually build a timeline around some terms of interest that were then cross referenced with events that we knew occurred between December 2020 and November 2021.

### **Wrangling and Pre-processing Methods** 
The duplicate tweets were removed and the remaining tweets were stripped of links, emojies as well as words like “covid”, “dose” and “vaccine” before being lemmatized. Next, the lemmatized corpora was tokenized and processed further to create a
document term matrix object.
<p/>

### **Time Series Analysis of Term Frequency**
**Vaccine Brands.** A time series analysis of the brand names was conducted to estimate the baseline level of chatter involving these terms between December 2020 and November 2021. If the resulting graph only included sparse interest for these terms, it would have been difficult to connect the proxy terms with the available historical data which we intended to use in validating the associated sentiment for these proxy terms. Fortunately, these terms were mentioned enough in the corpora that it was appropriate
to proceed.Pfizer in this analysis was represented by the term “thank_pfizerbiontech”.
<p/>

**Negative and Positive Proxy Terms.** The same approach was applied to a combined set of certain proxy terms just to see how these sentiments behaved relative to each other. However, dedicated time series graphs were also created separately for the negative and positive terms to ensure that the signals of these terms were not being conflated from one another.
<p/>

### **Semantic Contribution Analysis**

The TF/IDF approach was used to capture the ‘semantic contribution’ of the terms in the dtm where the results for the terms “bad” and “adverse” as well as “igottheshot” and “thank_science” were specifically analyzed and cross-referenced with historical data.
<p/>

**Time Series Analysis of TF-IDF Score.**  To observe linearly in time the fluctuations of TF-IDF scores for the terms that were tracked earlier, additional time series analysis graphs were created.These graphs were also used to cross reference with historical
data and to compare the level of semantic contribution between the negative and positive proxy terms.
<p/>

### **Topic Modeling** <p/>
To contextualize any overarching themes in the whole corpora, topic modeling was used.
<p/>

### **Word Embeddings**
To further vet the proxy terms that were tracked in the previous analysis, word embeddings approach was used. Specifically, if a term was closely associated with either a vaccine brand and/or some of the other negative or positive proxy tems in our list, then the term was considered a good tracker for negative or positive sentiment.
<p/>

### **Valence Aware Dictionary and sEntiment Reasoner (VADER) Lexicon**
The VADER package was used to generate sentiment scores for each entry and the resulting distribution of compound scores over time. was compared with the other time series graphs from the previous techniques in order to further validate our working timeline.
