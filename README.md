# Hangman-game
Hangman Game 🎮  Python Mini Project – Text-Based Hangman!  Goal: Build a simple console-based game where a player guesses the hidden word letter by letter with a limit of 6 wrong guesses.  Concepts Used: • random module • while loop • if-else conditions • Strings &amp; Lists  
#Hangman Code
import random
words = ["apple", "grape", "mango", "peach", "lemon"]
secret_word = random.choice(words)
guessed_letters = []
tries = 6
print("Welcome to Hangman!")
print("_ " * len(secret_word))
while tries > 0:
    guess = input("Guess a letter: ").lower()

    if not guess.isalpha() or len(guess) != 1:
        print("Please enter a single letter.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess in secret_word:
        print("Correct!")
    else:
        tries -= 1
        print(f"Wrong! You have {tries} tries left.")

   
    display_word = ""
    for letter in secret_word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print(display_word.strip())

    #output
    if all(letter in guessed_letters for letter in secret_word):
        print("Congratulations! You guessed the word:", secret_word)
        break
else:
    print("You ran out of tries. The word was:", secret_word)
    
