# Simple Earley Parser

grammar = {
    "S": [["NP", "VP"]],
    "NP": [["Det", "N"]],
    "VP": [["V", "NP"]],
    "Det": [["the"], ["a"]],
    "N": [["cat"], ["dog"]],
    "V": [["sees"], ["likes"]]
}

def earley_parse(words):
    n = len(words)
    chart = [set() for _ in range(n + 1)]

    # (LHS, RHS, dot position, start position)
    chart[0].add(("S'", ("S",), 0, 0))

    for i in range(n + 1):
        changed = True
        while changed:
            changed = False
            states = list(chart[i])

            for lhs, rhs, dot, start in states:

                # Predictor
                if dot < len(rhs) and rhs[dot] in grammar:
                    B = rhs[dot]
                    for rule in grammar[B]:
                        state = (B, tuple(rule), 0, i)
                        if state not in chart[i]:
                            chart[i].add(state)
                            changed = True

                # Scanner
                elif dot < len(rhs) and i < n:
                    if rhs[dot] == words[i]:
                        chart[i + 1].add((lhs, rhs, dot + 1, start))

                # Completer
                elif dot == len(rhs):
                    for st in list(chart[start]):
                        l2, r2, d2, s2 = st
                        if d2 < len(r2) and r2[d2] == lhs:
                            new_state = (l2, r2, d2 + 1, s2)
                            if new_state not in chart[i]:
                                chart[i].add(new_state)
                                changed = True

    return ("S'", ("S",), 1, 0) in chart[n]


# Input
sentence = input("Enter a sentence: ").lower().split()

if earley_parse(sentence):
    print("Sentence Accepted")
else:
    print("Sentence Rejected")
