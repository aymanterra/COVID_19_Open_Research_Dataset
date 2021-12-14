# COVID_19_Open_Research_Dataset
COVID-19 Open Research Dataset
Clustering analysis on Open Research Dataset CORD 19

## Overview
In response to the COVID-19 pandemic, the White House and a coalition of leading research groups
have prepared the COVID-19 Open Research Dataset (CORD-19). CORD-19 is a resource of over
57,000 scholarly articles, including over 45,000 with full text, about COVID-19, SARS-CoV-2, and
related coronaviruses. This freely available dataset is provided to the global research community. As
a big data community, how can we help researchers to easily find the related research papers
easily?
You can find the dataset and the main challenge on kaggle
https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge

## Goals
Given the large number of literature and the rapid spread of COVID-19, it is difficult for health
professionals to keep up with new information on the virus. Can clustering similar research articles
together simplify the search for related publications? How can the content of the clusters be
qualified? And over each cluster how can we recommend the most similar papers leveraging
clustering?

## Requirements
you are required to find out the best way to cluster the research papers using the research
papers details in the JSON file with the metadata in the CSV file, then you should build a
neighborhood recommender system to receive the title of research paper and recommend
the most N similar papers to it based on its cluster. So you should find a way to represent
the papers in vectors and cluster them then build a neighbourhood recommender system
on the clusters.

### Required Steps
#### 1. Read the dataset using spark:
The dataset is 8GB so we don’t expect you can manage the whole entire dataset on your local machine.

#### 2. Do exploratory data analysis:
Do the EDA to understand your data and extract insights help you in feature
engineering ,Document your insights

#### 3. Preparation and Cleaning the data:
- Joining the json file with the metadata in the csv file
- Handling Nulls.
- Handling Duplications.
- Keep Only the english documents

#### 4. Preprocessing:
Our main goal is to clean and preprocess the txt to prepare it to represent it in
vectors. It is a mandatory step in NLP projects to preprocess the text. You can have
a look in this article to explore some of well known preprocessing steps
https://towardsdatascience.com/nlp-text-preprocessing-a-practical-guide-and-template-d80874676e79

##### Required preprocessing
1. Remove stop words.
2. Remove custom stop words, Research papers will often frequently use words that don't actually contribute to the meaning and are not considered everyday stopwords and should be removed to enhance the accuracy.
        custom_stop_words = [ 'doi', 'preprint', 'copyright', 'peer', 'reviewed', 'org', 'https', 'et', 'al', 'author', 'figure','rights', 'reserved', 'permission', 'used', 'using', 'biorxiv', 'medrxiv', 'license', 'fig', 'fig.', 'al.', Elsevier', 'PMC', 'CZI', 'www']
3. Remove Punctuation, use this Regex
        '!()-[]{};:'"\,<>./?@#$%^&*_~'
4. convert text to lower case.

#### 5. Vectorization:
convert the data into a format that can be handled by our algorithms. For this purpose we can use *Word2vec*.

#### 6. Clustering (Not implemented yet)
Apply clustering algorithm on the data and choose the best k you decide from the *elbow* method. You can use *PCA* to reduce the dimensions while still keeping *95\%* variance for better performance and hopefully remove some noise/outliers.

#### 7. Recommender system (Not implemented yet)
Build a very basic recommender system:
- Create a function with the signature *recommendPaper(paper_title,N)* where N is the number of recommended papers in the list and it returns the recommendation list.
- Recommend top N recommendation list based on the most similar(*cosine similarity*) papers to it with respect to the cluster it belongs.
