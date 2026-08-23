from collections import defaultdict, Counter

# Training data: (word, POS tag)
training_data = [
    ("the", "DT"),
    ("cat", "NN"),
    ("dog", "NN"),
    ("runs", "VBZ"),
    ("eats", "VBZ"),
    ("a", "DT"),
    ("boy", "NN"),
    ("girl", "NN"),
    ("plays", "VBZ"),
    ("book", "NN")
]

# Store possible tags for each word
word_tags = defaultdict(Counter)

for word, tag in training_data:
    word_tags[word][tag] += 1

# Function for stochastic POS tagging
def pos_tag(sentence):
    words = sentence.lower().split()
    result = []

    for word in words:
        if word in word_tags:
            # Select the most probable POS tag
            tag = word_tags[word].most_common(1)[0][0]
        else:
            # Assign unknown words as nouns
            tag = "NN"

        result.append((word, tag))

    return result


# Input
sentence = input("Enter a sentence: ")

# Perform POS tagging
tags = pos_tag(sentence)

# Display result
print("\nPOS Tags:")
for word, tag in tags:
    print(word, "->", tag)
