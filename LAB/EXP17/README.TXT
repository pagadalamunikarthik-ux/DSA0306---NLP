import nltk
from nltk.corpus import wordnet as wn

# Download WordNet
nltk.download('wordnet')

# Input word
word = input("Enter a word: ")

# Retrieve synsets
synsets = wn.synsets(word)

print("\nSynsets and Meanings:")

for syn in synsets:
    print("\nSynset:", syn.name())
    print("Definition:", syn.definition())
    print("Examples:", syn.examples())
