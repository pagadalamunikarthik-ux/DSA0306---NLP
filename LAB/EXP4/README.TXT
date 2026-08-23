def pluralize(word):
    state = "START"

    # State 1: words ending in s, x, z, ch, sh
    if word.endswith(("s", "x", "z", "ch", "sh")):
        state = "ADD_ES"

    # State 2: words ending in consonant + y
    elif word.endswith("y") and len(word) > 1 and word[-2] not in "aeiou":
        state = "CHANGE_Y_TO_IES"

    # State 3: normal words
    else:
        state = "ADD_S"

    # State transitions
    if state == "ADD_ES":
        return word + "es"

    elif state == "CHANGE_Y_TO_IES":
        return word[:-1] + "ies"

    elif state == "ADD_S":
        return word + "s"


# Input
word = input("Enter an English noun: ")

# Generate plural form
plural = pluralize(word)

print("Plural form:", plural)
