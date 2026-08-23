import nltk
from nltk.wsd import lesk
from nltk.tokenize import word_tokenize

# Download required NLTK resources
nltk.download('wordnet')
nltk.download('punkt')

# Input sentence
sentence = input("Enter a sentence: ")
word = input("Enter the word to disambiguate: ")

# Tokenize the sentence
tokens = word_tokenize(sentence)

# Apply Lesk algorithm
sense = lesk(tokens, word)

# Display result
if sense:
    print("\nWord:", word)
    print("Synset:", sense.name())
    print("Meaning:", sense.definition())
    print("Example:", sense.examples())
else:
    print("No sense found.")
