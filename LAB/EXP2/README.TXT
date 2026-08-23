def finite_automaton(string):
    state = 'q0'

    for ch in string:
        if state == 'q0':
            if ch == 'a':
                state = 'q1'
            else:
                state = 'q0'

        elif state == 'q1':
            if ch == 'b':
                state = 'q2'
            elif ch == 'a':
                state = 'q1'
            else:
                state = 'q0'

        elif state == 'q2':
            if ch == 'a':
                state = 'q1'
            else:
                state = 'q0'

    return state == 'q2'


# Input
string = input("Enter a string: ")

# Check the string
if finite_automaton(string):
    print("Accepted")
else:
    print("Rejected")
