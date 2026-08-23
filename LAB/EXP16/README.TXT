import spacy

# Load the English language model
nlp = spacy.load("en_core_web_sm")

# Input text
text = input("Enter a sentence: ")

# Process the text
doc = nlp(text)

# Display named entities
print("\nNamed Entities:")

for ent in doc.ents:
    print(ent.text, "->", ent.label_)
