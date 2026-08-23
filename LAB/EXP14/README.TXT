# Check subject-verb agreement

def check_agreement(sentence):
    words = sentence.lower().split()

    # Simple agreement rules
    singular_subjects = ["boy", "girl", "cat", "dog"]
    plural_subjects = ["boys", "girls", "cats", "dogs"]

    singular_verbs = ["runs", "eats", "plays", "likes"]
    plural_verbs = ["run", "eat", "play", "like"]

    if len(words) != 2:
        return "Invalid sentence"

    subject = words[0]
    verb = words[1]

    # Singular subject must use singular verb
    if subject in singular_subjects:
        if verb in singular_verbs:
            return "Agreement Correct"
        else:
            return "Agreement Incorrect"

    # Plural subject must use plural verb
    elif subject in plural_subjects:
        if verb in plural_verbs:
            return "Agreement Correct"
        else:
            return "Agreement Incorrect"

    else:
        return "Unknown subject"


# Input
sentence = input("Enter a sentence: ")

# Check agreement
result = check_agreement(sentence)

print(result)
