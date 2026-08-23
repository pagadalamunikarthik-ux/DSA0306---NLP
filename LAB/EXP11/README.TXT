# Simple Top-Down Parser

grammar = {
    "S": [["NP", "VP"]],
    "NP": [["Det", "N"]],
    "VP": [["V", "NP"]],
    "Det": [["the"], ["a"]],
    "N": [["cat"], ["dog"]],
    "V": [["sees"], ["likes"]]
}

def parse(symbol, words, position):
    # Terminal symbol
    if symbol not in grammar:
        if position < len(words) and symbol == words[position]:
            return position + 1
        return None

    # Non-terminal symbol
    for rule in grammar[symbol]:
        pos = position

        for item in rule:
            pos = parse(item, words, pos)

            if pos is None:
                break

        if pos is not None:
            return pos

    return None


# Input
sentence = input("Enter a sentence: ").lower()
words = sentence.split()

# Start parsing from S
result = parse("S", words, 0)

if result == len(words):
    print("Sentence Accepted")
else:
    print("Sentence Rejected")
