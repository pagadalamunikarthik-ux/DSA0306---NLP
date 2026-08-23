import nltk
from nltk import CFG
from nltk.parse import ChartParser

# Define Context-Free Grammar
grammar = CFG.fromstring("""
S -> NP VP
NP -> Det N
VP -> V NP
Det -> 'the' | 'a'
N -> 'cat' | 'dog'
V -> 'sees' | 'likes'
""")

# Create parser
parser = ChartParser(grammar)

# Input sentence
sentence = input("Enter a sentence: ").lower().split()

# Generate parse tree
trees = list(parser.parse(sentence))

if trees:
    print("\nParse Tree:")
    print(trees[0])

    # Display tree graphically
    trees[0].pretty_print()
else:
    print("No parse tree found.")
