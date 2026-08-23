from collections import defaultdict
import random

# Training text
text = "I like machine learning. I like natural language processing."

# Convert text into words
words = text.lower().replace(".", "").split()

# Create bigram model
bigram = defaultdict(list)

for i in range(len(words) - 1):
    bigram[words[i]].append(words[i + 1])

# Generate text
word = "i"
generated = [word]

for _ in range(10):
    if word in bigram:
        word = random.choice(bigram[word])
        generated.append(word)
    else:
        break

print("Generated Text:")
print(" ".join(generated))
