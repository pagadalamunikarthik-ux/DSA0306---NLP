# Transformation-Based Tagging

# Initial tagging: assume every word is a noun
sentence = input("Enter a sentence: ")
words = sentence.split()

tags = ["NN"] * len(words)

# Transformation rules
for i, word in enumerate(words):
    w = word.lower().strip(".,!?")

    # Rule 1: Determiners
    if w in ["a", "an", "the"]:
        tags[i] = "DT"

    # Rule 2: Pronouns
    elif w in ["i", "you", "he", "she", "we", "they", "it"]:
        tags[i] = "PRP"

    # Rule 3: Words ending with -ing
    elif w.endswith("ing"):
        tags[i] = "VBG"

    # Rule 4: Words ending with -ed
    elif w.endswith("ed"):
        tags[i] = "VBD"

    # Rule 5: Words ending with -ly
    elif w.endswith("ly"):
        tags[i] = "RB"

# Display final tags
print("\nFinal POS Tags:")
for word, tag in zip(words, tags):
    print(word, "->", tag)
