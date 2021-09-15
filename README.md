This is the code file for my dissertation focussed on understanding user perceptions and experiences of the Oxford Street Brand.

We have provided all the relevant datasets in the file including the raw twitter data (data.csv), processed twitter data (processed_dataset.csv), all relevant lexicons and Belgravia data
for comparison. Warning if file "Twitter Data Pull for Oxford Street.ipynb" is run then this will override the current Twitter data that has been pulled for the Oxford Street District.

To be run in this order:

1) Twitter Data Pull for Oxford Street
This is the Jupyter notebook file for extracting Twitter data using the API. The code is currently setup to search for the bounded box of Oxford Street but can be changed, while you must insert your own bearer token after Twitter API approval. The general code for retrieving this data is from the source https://towardsdatascience.com/an-extensive-guide-to-collecting-tweets-from-twitter-api-v2-for-academic-research-using-python-3-518fcb71df2a by Andrew Edward and does not reflect my own work. I have provided a pre-loaded dataset that can be used, but the solution and key will need to be edited.

2) Data pre-processing, sound and smell class and sentiment analysis
This is the Jupyter notebook file for taking the data extracted from the Twitter API, commencing all the preprocessing steps so that it can be analysed using NLP techniques.
This is followed by classifying the text by a lexicon method to see if the text refers to a sound or smell. The lexicons are from (Quercia et al (2015)) and (Quercia et al (2016)). Finally, sentiment analysis is applied so a column is added to define whether a tweet is positive, negative or neutral. We also graph the tweets by tweet length.

3) Sentiment visualisations
In this file we visualise the sentiments both as a stacked column with each sentiment and also positive/negative sentiment tweets as a proportion of the total.

4) Spatial analysis
In this file we visualise the geolocated tweet data by clusters, with the correct number of clusters defined using the elbow method. These clusters are visualised on OpenStreetMap using the Folium package.

5) Topic analysis
In this file we apply the latent dirichlet allocation technique on our twitter datasets. The coherence score is plotted for each topic and intertopic distance is visualised using the pyLDAvis package. We also plot the distributions in bar graph form.

Subsections of the data used
We note at various points where alternative sub-sections of the data can be applied in each Jupyter notebook file. We have listed these below for your reference.

Smell
twitter_df = twitter_df.loc[twitter_df['smell'] == 'Yes']
Sound
twitter_df = twitter_df.loc[twitter_df['sound'] == 'Yes']
Pre-COVID
twitter_df = twitter_df.loc[twitter_df['created_at'] <= "2020-03-20"]
Post-COVID
twitter_df = twitter_df.loc[twitter_df['created_at'] >= "2020-03-20"]
Just positive tweets
twitter_df = twitter_df.loc[twitter_df['Sentiment'] == 'Positive']
Just negative tweets
twitter_df = twitter_df.loc[twitter_df['Sentiment'] == 'Negative']

