!pip install -q -U google-genai

from google import genai


client = genai.Client(api_key="AQ.Ab8RN6JzUexrV-P8prtDKIDpFAY9bGfyyvQ1pU5PM1W5N1y14w")

prompt = input("Enter your prompt: ")

response = client.models.generate_content(
    model="gemini-3.6-flash",
    contents=prompt
)

print("\nInput:")
print(prompt)

print("\nGenerated Output:")
print(response.text)
