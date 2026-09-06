from transformers import pipeline

# Load GPT-2 model
generator = pipeline("text-generation", model="gpt2")

# Get input prompt
prompt = input("Enter your prompt: ")

# Generate text
result = generator(
    prompt,
    max_new_tokens=50,
    num_return_sequences=1
)

print("\nGenerated Text:")
print(result[0]["generated_text"])
