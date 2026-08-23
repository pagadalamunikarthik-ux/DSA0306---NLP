from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity

# Input text
text = input("Enter a text: ")

# Split text into sentences
sentences = [s.strip() for s in text.split(".") if s.strip()]

if len(sentences) < 2:
    print("Please enter at least two sentences.")
else:
    # Convert sentences into TF-IDF vectors
    vectorizer = TfidfVectorizer()
    vectors = vectorizer.fit_transform(sentences)

    # Calculate similarity between consecutive sentences
    similarities = []

    for i in range(len(sentences) - 1):
        score = cosine_similarity(
            vectors[i], vectors[i + 1]
        )[0][0]
        similarities.append(score)

    # Calculate average coherence score
    coherence_score = sum(similarities) / len(similarities)

    print("\nCoherence Score:", round(coherence_score, 2))

    if coherence_score >= 0.30:
        print("Text is Coherent")
    else:
        print("Text is Less Coherent")
        
