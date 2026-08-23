import nltk
from nltk import PCFG
from nltk.parse import ViterbiParser

# Define Probabilistic Context-Free Grammar
grammar = PCFG.fromstring("""
S -> NP VP [1.0]
NP -> Det N [0.6]
NP -> NP PP [0.4]
VP -> V NP [0.7]
VP -> VP PP [0.3]
PP -> P NP [1.0]
Det -> 'the' [0.5]
Det -> 'a' [0.5]
N -> 'boy' [0.5]
N -> 'dog' [0.5]
V -> 'saw' [1.0]
P -> 'with' [1.0]
""")

# Create Viterbi parser
parser = ViterbiParser(grammar)

# Input sentence
sentence = input("Enter a sentence: ").lower().split()

# Generate the most probable parse
try:
    trees = list(parser.parse(sentence))

    if trees:
        print("\nMost Probable Parse Tree:")
        print(trees[0])
        print("\nProbability:", trees[0].prob())
    else:
        print("No valid parse found.")

except ValueError:
    print("Sentence cannot be parsed using the given grammar.")
