# Movie_Similarity_and_Clustering
We will quantify the similarity of movies based on their plot summaries available on IMDb and Wikipedia, then separate them into groups, also known as clusters. We will create a dendrogram to represent how closely the movies are related to each other.

1. Total movies: 100

2. Has title, genre, wiki plot and imdb plot

3. The dataset we imported currently contains two columns titled wiki_plot and imdb_plot. They are the plot found for the movies on Wikipedia and IMDb, respectively. The text in the two columns is similar, however, they are often written in different tones and thus provide context on a movie in a different manner of linguistic expression. Further, sometimes the text in one column may mention a feature of the plot that is not present in the other column.
Let us combine both the columns to avoid the overheads in computation associated with extra columns to process.

4. Tokenization is the process by which we break down articles into individual sentences or words, as needed. Besides the tokenization method provided by NLTK, we might have to perform additional filtration to remove tokens which are entirely numeric values or punctuation (words that are present in the English dictionary.)
Stemming is the process by which we bring down a word from its different forms to the root word. This helps us establish meaning to different forms of the same words without having to deal with each form separately. For example, the words 'fishing', 'fished', and 'fisher' all get stemmed to the word 'fish'.
But we may have to use the two functions repeatedly one after the other to handle a large amount of data, hence we can think of wrapping them in a function and passing the text to be tokenized and stemmed as the function argument. Then we can pass the new wrapping function, which shall perform both tokenizing and stemming instead of just tokenizing, as the tokenizer argument while creating the TF-IDF vector of the text.

5. TfidfVectorizer:  max_df=0.8, max_features=200000, min_df=0.2, stop_words='english', use_idf=True, tokenizer=tokenize_and_stem, ngram_range= (1,3)
(Weights assignment)
Ngram is the combination of 1, 2 and 3 words taken at once as tokens.

6. Kmeans clustering: from notes, inertia is used to check optimum number of clusters.

7. We then check for the cosine similarity between the movies based on the term weights.
The cosine similarity between the two points is simply the cosine of this angle. Cosine is a trigonometric function that, in this case, helps you describe the orientation of two points. If two points were 90 degrees apart, that is if they were on the x-axis and y-axis of this graph as far away from each other as they can be in this graph quadrant, their cosine similarity would be zero, because cos(90)=0. If two points were 0 degrees apart, that is if they existed along the same line, their cosine similarity would 1, because cos (0) =1.
 
But note that you are dealing with similarity here and not distance. The highest value, 1, is reserved for the two points that are most close together, while the lowest value, 0, is reserved for the two points that are the least close together. This is the exact opposite of Euclidean distance, in which the lowest values describe the points closest together. To remedy this confusion, most programming environments calculate cosine distance by simply subtracting the cosine similarity from one. So, cosine distance is simply 1−cos(θ).
Which one to go for: Euclidean distance accounts for magnitude while cosine distance does not. Another way of putting this is that cosine distance measures whether the relationship among your various features is the same, regardless of how much of any one thing is present. This fact would be true if one of your points was (1,2) and the other was (300,600) as well.
(Suppose a movie plot is huge and has 300 words of same term, other movie plot is relatively very small and has 1 word of that term, they can be related, difference in count is mainly because of the difference in plot sizes)
Cosine distance is sometimes particularly good for text-related data. Often texts are of quite different lengths. If words have vastly different counts but exist in the text in roughly the same proportion, cosine distance will not worry about the raw counts, only their proportional relationships to each other. Otherwise, as with Euclidean distance you might wind up saying something like, “All the long texts are similar, and all the short texts are similar.” With text, it is often better to use the distance measure that disregards differences in magnitude and focuses on the proportions of features.
However, if you know your sample texts are all roughly the same size (or if you have subdivided all your texts into equally-sized “chunks,” a common pre-processing step), you might prefer to account for relatively small differences in magnitude by using Euclidean distance. For non-text data where the size of the sample is unlikely to affect the features, Euclidean distance is sometimes preferred.

8. We shall now create a tree-like diagram (called a dendrogram) of the movie titles to help us understand the level of similarity between them visually. Dendrograms help visualize the results of hierarchical clustering, which is an alternative to k-means clustering. Two pairs of movies at the same level of hierarchical clustering are expected to have similar strength of similarity between the corresponding pairs of movies.

9. The lower the similarity distance between any two movies, the lower their linkage will make an intercept on the y-axis. For instance, the lowest dendrogram linkage we shall discover will be between the movies, it is a Wonderful Life and A Place in the Sun. This indicates that the movies are remarkably like each other in their plots.
