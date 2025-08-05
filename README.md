# This program acts as a simple calculator.
# It takes two numbers and an operation from the user,
# then performs the calculation and displays the result.

def calculate():
    """
    Prompts the user for two numbers and an operation,
    then performs the calculation and prints the result.
    Includes error handling for invalid inputs.
    """
    print("Welcome to the Simple Python Calculator!")

    # Get the first number from the user
    while True:
        try:
            num1_str = input("Enter the first number: ")
            num1 = float(num1_str) # Convert input to a float to handle decimals
            break # Exit loop if input is valid
        except ValueError:
            print("Invalid input. Please enter a valid number.")

    # Get the second number from the user
    while True:
        try:
            num2_str = input("Enter the second number: ")
            num2 = float(num2_str) # Convert input to a float
            break # Exit loop if input is valid
        except ValueError:
            print("Invalid input. Please enter a valid number.")

    # Get the mathematical operation from the user
    while True:
        operation = input("Enter the operation (+, -, *, /): ")
        if operation in ['+', '-', '*', '/']:
            break # Exit loop if operation is valid
        else:
            print("Invalid operation. Please choose from +, -, *, /.")

    result = None # Initialize result variable
    equation_str = f"{num1_str} {operation} {num2_str}" # String for displaying the equation

    # Perform the calculation based on the chosen operation
    if operation == '+':
        result = num1 + num2
    elif operation == '-':
        result = num1 - num2
    elif operation == '*':
        result = num1 * num2
    elif operation == '/':
        # Handle division by zero error
        if num2 == 0:
            print("Error: Division by zero is not allowed.")
            return # Exit the function if division by zero occurs
        else:
            result = num1 / num2

    # Print the result in the specified format
    if result is not None:
        # Format the result to avoid unnecessary .0 if it's a whole number
        if result == int(result):
            result = int(result)
        print(f"{equation_str} = {result}")

# Call the calculate function to run the program
calculate()
