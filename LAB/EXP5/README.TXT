import nltk
from nltk.stem import PorterStemmer

# Create Porter Stemmer object
stemmer = PorterStemmer()

# List of words
words = ["playing", "played", "plays", "studies", "studying", "connected"]

# Perform stemming
print("Original Word -> Stemmed Word")

for word in words:
    stem = stemmer.stem(word)
    print(word, "->", stem)
