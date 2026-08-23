from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity

# Collection of documents
documents = [
    "Python is a popular programming language",
    "Machine learning uses algorithms to learn from data",
    "Python is widely used for machine learning",
    "Natural language processing is a field of artificial intelligence",
    "Deep learning is used in artificial intelligence"
]

# Create TF-IDF vectorizer
vectorizer = TfidfVectorizer()

# Convert documents into TF-IDF vectors
tfidf_matrix = vectorizer.fit_transform(documents)

# Input search query
query = input("Enter your search query: ")

# Convert query into TF-IDF vector
query_vector = vectorizer.transform([query])

# Calculate cosine similarity
similarity = cosine_similarity(query_vector, tfidf_matrix)[0]

# Rank documents based on similarity
ranking = similarity.argsort()[::-1]

print("\nDocument Ranking:")

for i in ranking:
    print(f"Document {i + 1}: {similarity[i]:.4f}")
    print(documents[i])
    print()
