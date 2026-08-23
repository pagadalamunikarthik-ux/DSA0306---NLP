import nltk
from nltk import word_tokenize, pos_tag, RegexpParser

# Input sentence
sentence = input("Enter a sentence: ")

# Tokenize the sentence
words = word_tokenize(sentence)

# Perform POS tagging
tagged_words = pos_tag(words)

# Define grammar for noun phrases
grammar = """
    NP: {<DT>?<JJ>*<NN.*>+}
"""

# Create a chunk parser
parser = RegexpParser(grammar)

# Parse the sentence
tree = parser.parse(tagged_words)

print("\nSyntax Tree:")
print(tree)

print("\nNoun Phrases and Their Meanings:")

# Extract noun phrases
for subtree in tree.subtrees():
    if subtree.label() == "NP":
        phrase = " ".join(word for word, tag in subtree.leaves())

        # Simple semantic interpretation
        print(phrase, "-> Entity/Object")
