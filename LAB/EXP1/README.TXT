import re

text = "My phone number is 9876543210 and my email is student@gmail.com."

# Search for phone number
phone = re.search(r'\d{10}', text)

# Search for email address
email = re.search(r'[\w.-]+@[\w.-]+\.\w+', text)

if phone:
    print("Phone Number:", phone.group())

if email:
    print("Email Address:", email.group())
