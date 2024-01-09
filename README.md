# Bagels_Game
import random

def generate_secret_number():
    return [random.randint(0, 9) for _ in range(3)]

def get_user_guess():
    while True:
        user_input = input("Enter your guess (3 digits): ")
        if user_input.isdigit() and len(user_input) == 3:
            return [int(digit) for digit in user_input]
        else:
            print("Invalid input. Please enter a 3-digit number.")

def provide_feedback(secret_number, user_guess):
    feedback = []
    for i in range(3):
        if user_guess[i] == secret_number[i]:
            feedback.append("Fermi")
        elif user_guess[i] in secret_number:
            feedback.append("Pico")
    if not feedback:
        feedback.append("Bagels")
    return feedback

def display_feedback(feedback):
    if feedback:
        print(" ".join(feedback))
    else:
        print("Bagels")

def play_game():
    print("Bagels, a deductive logic game.")
    print("By PRADYUSH MOHAPATRA(22410133332)")
    print("I am thinking of a 3-digit number. Try to guess what it is.")
    print("Here are some clues:")
    print("When I say: That means:")
    print("Pico\tOne digit is correct but in the wrong position.")
    print("Fermi\tOne digit is correct and in the right position.")
    print("Bagels\tNo digit is correct.")

    secret_number = generate_secret_number()
    attempts = 0

    while attempts < 10:
        attempts += 1
        print(f"\nGuess #{attempts}:")
        user_guess = get_user_guess()

        if user_guess == secret_number:
            print("You got it!")
            break

        feedback = provide_feedback(secret_number, user_guess)
        display_feedback(feedback)

    print("\nThanks for playing!")

if __name__ == "__main__":
    play_game()
