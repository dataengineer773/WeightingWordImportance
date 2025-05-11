We want a bag of words, but with words weighted by their importance to an observation, Compare the frequency of the word in a document (a tweet, movie review, speech transcript, etc.) with
the frequency of the word in all other documents using term frequency-inverse document frequency (tfidf). scikit-learn makes this easy with TfidfVectorizer, Just as in Recipe 6.9, the output is a spare matrix. However, if we want to view the output as a dense
matrix, we can use .toarray, vocabulary_ shows us the word of each feature, The more a word appears in a document, the more likely it is that the word is important to that
document. For example, if the word economy appears frequently, it is evidence that the document might
be about economics. We call this term frequency (tf).
In contrast, if a word appears in many documents, it is likely less important to any individual document.
For example, if every document in some text data contains the word after then it is probably an
unimportant word. We call this document frequency (df).
By combining these two statistics, we can assign a score to every word representing how important that
word is in a document. Specifically, we multiply tf to the inverse of document frequency (idf), where t is a word and d is a document. There are a number of variations in how tf and idf are calculated.
In scikit-learn, tf is simply the number of times a word appears in the document and idf is calculated as where nd
is the number of documents and df(d,t) is term, t’s document frequency (i.e., number of
documents where the term appears).
By default, scikit-learn then normalizes the tf-idf vectors using the Euclidean norm (L2 norm). The
higher the resulting value, the more important the word is to a document
