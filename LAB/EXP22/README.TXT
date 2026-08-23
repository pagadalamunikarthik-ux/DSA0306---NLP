import re

def reference_resolution(text):
    sentences = re.split(r'[.!?]', text)
    nouns = []

    print("\nReference Resolution:")

    for sentence in sentences:
        words = sentence.strip().split()

        for word in words:
            clean_word = word.lower().strip(",.!?")

            # Check for pronouns
            if clean_word in ["he", "she", "it", "they", "him", "her", "them"]:
                if nouns:
                    print(clean_word, "->", nouns[-1])

            # Store possible nouns
            elif clean_word not in [
                "the", "a", "an", "is", "was", "are",
                "and", "then", "to", "with"
            ]:
                nouns.append(clean_word)


# Input
text = input("Enter a text: ")

# Perform reference resolution
reference_resolution(text)
