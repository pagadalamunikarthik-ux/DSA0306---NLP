import nltk
from nltk import word_tokenize, pos_tag

# Download required resources
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger_eng') # Changed to download 'averaged_perceptron_tagger_eng'

# Input text
text = input("Enter a sentence: ")

# Tokenize the sentence
words = word_tokenize(text)

# Perform POS tagging
tags = pos_tag(words)

# Display the result
print("\nPart-of-Speech Tags:")
for word, tag in tags:
    print(word, "->", tag)
