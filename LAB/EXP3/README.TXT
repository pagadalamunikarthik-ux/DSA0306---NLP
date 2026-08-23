import nltk
from nltk.stem import PorterStemmer
from nltk.tokenize import word_tokenize

# Download required resources
nltk.download('punkt')
nltk.download('punkt_tab')

# Create stemmer
stemmer = PorterStemmer()

# Input sentence
text = input("Enter a sentence: ")

# Tokenize the sentence
words = word_tokenize(text)

# Perform morphological analysis
print("\nMorphological Analysis:")
for word in words:
    if word.isalpha():
        stem = stemmer.stem(word)
        print(word, "->", stem)
