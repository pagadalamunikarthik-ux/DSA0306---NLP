import re

def pos_tag(sentence):
    words = sentence.split()
    result = []

    for word in words:
        w = word.lower().strip(".,!?")

        # Rule 1: Determiners
        if w in ["a", "an", "the"]:
            tag = "DT"

        # Rule 2: Pronouns
        elif w in ["i", "you", "he", "she", "it", "we", "they"]:
            tag = "PRP"

        # Rule 3: Words ending with -ing
        elif re.match(r".+ing$", w):
            tag = "VBG"

        # Rule 4: Words ending with -ed
        elif re.match(r".+ed$", w):
            tag = "VBD"

        # Rule 5: Adjectives ending with -ful or -ous
        elif re.match(r".+(ful|ous)$", w):
            tag = "JJ"

        # Rule 6: Adverbs ending with -ly
        elif re.match(r".+ly$", w):
            tag = "RB"

        # Rule 7: Words ending with -s
        elif re.match(r".+s$", w):
            tag = "NNS"

        # Rule 8: Default rule
        else:
            tag = "NN"

        result.append((word, tag))

    return result


# Input
sentence = input("Enter a sentence: ")

# Perform POS tagging
tags = pos_tag(sentence)

print("\nPOS Tags:")
for word, tag in tags:
    print(word, "->", tag)
