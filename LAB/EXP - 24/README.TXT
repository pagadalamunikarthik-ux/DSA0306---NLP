def dialog_act(text):
    text = text.lower()

    if any(x in text for x in ["hello", "hi", "hey"]):
        return "Greeting"

    elif "?" in text:
        return "Question"

    elif any(x in text for x in ["please", "can you", "could you"]):
        return "Request"

    elif any(x in text for x in ["thank", "thanks"]):
        return "Thanking"

    elif any(x in text for x in ["sorry", "apologize"]):
        return "Apology"

    elif any(x in text for x in ["bye", "goodbye"]):
        return "Goodbye"

    elif any(x in text for x in ["yes", "okay", "sure"]):
        return "Agreement"

    else:
        return "Statement"


n = int(input("Enter number of sentences: "))

for i in range(n):
    s = input("Enter sentence: ")
    print("Dialog Act:", dialog_act(s))
