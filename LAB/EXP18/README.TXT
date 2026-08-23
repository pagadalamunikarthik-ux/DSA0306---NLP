import re

def parse_fopc(expression):
    # Remove extra spaces
    expression = expression.strip()

    # Pattern for Predicate(Argument)
    pattern = r'^(forall|exists)\s+([a-zA-Z])\s*:\s*([A-Za-z]+)\(([a-zA-Z]+)\)$'

    match = re.match(pattern, expression)

    if match:
        quantifier = match.group(1)
        variable = match.group(2)
        predicate = match.group(3)
        argument = match.group(4)

        print("\nFOPC Expression:")
        print("Quantifier :", quantifier)
        print("Variable   :", variable)
        print("Predicate  :", predicate)
        print("Argument   :", argument)

        return True

    return False


# Input
expression = input("Enter a FOPC expression: ")

# Parse expression
if parse_fopc(expression):
    print("\nValid FOPC Expression")
else:
    print("\nInvalid FOPC Expression")
