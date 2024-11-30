# CodeAlpha_Python_Programming.
import random

word_list = ["python", "java", "javascript", "hangman", "programming", "code"]

chosen_word = random.choice(word_list)

word_length = len(chosen_word)  
display = ["_"] * word_length  
guessed_letters = []  
max_incorrect_guesses = 6  
incorrect_guesses = 0  

while incorrect_guesses < max_incorrect_guesses and "_" in display:
    print(f"Word to guess: {' '.join(display)}")
    guess = input("Guess a letter: ").lower()  

    
    if guess in guessed_letters:
        print(f"You already guessed '{guess}'. Try again!")
        continue
    
    guessed_letters.append(guess)  
    
    
    if guess in chosen_word:
        for position in range(word_length):
            if chosen_word[position] == guess:
                display[position] = guess
        print(f"Good guess: {guess}")
    else:
        incorrect_guesses += 1
        print(f"Wrong guess. You have {max_incorrect_guesses - incorrect_guesses} attempts left.")
    
    print("\n")  

if "_" not in display:
    print(f"Congratulations! You guessed the word: {chosen_word}")
else:
    print(f"Game over! The word was: {chosen_word}")
