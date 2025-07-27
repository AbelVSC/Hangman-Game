# Hangman-Game
This is one of my personal CS projects. I made a hangman game through python which can be played right in the python terminal. It uses a text file where I stored around 94000+ words.

# About
This game is a word game where you have to guess the spelling of the full word. You will be presented few spaces where you should write your letter. You should keep on guessing each letter of the word until you get to the full word itself.

# Instructions to Play
1. Download the Hangman Word game.py file and make sure words.txt is in the same folder.
2. Make sure python is installed.
3. Open your python terminal.
4. Navigate to the python file and click it.
5. Then you will be able to play.

# Code
Below is the code:

```python
print("######################################## 🎉WELCOME TO HANGMAN🎉 ########################################")
print("Please make a choice")
print("""Your choices are as follows:
Choice 1: Play Game
Choice 2: Exit the game""")
choice=int(input("Enter your choice number: "))
def hangman():
  word = random.choice(word_bank)
  guessedWord = ['_'] * len(word)
  attempts = 15
  while attempts > 0:
    print('\nCurrent word: ',' '.join(guessedWord))
    guess = input('Guess a letter: ').lower()   
    if guess in word:
      for i in range(len(word)):
        if word[i] == guess:
          guessedWord[i] = guess
      print('Great guess!')
    else:
      attempts -= 1
      print('Wrong guess! Attempts left: ',attempts)
    if '_' not in guessedWord:
      print('\nCongratulations🎉🎉!! You guessed the word: ',word)
      break
  if attempts == 0 and '_' in guessedWord:
    print('\nYou\'ve run out of attempts! The word was: ',word)
while True:
  if choice==1:
    import random
    with open('words.txt') as file:
      word_bank = [line.strip().lower() for line in file if line.strip()]
    hangman()
  elif choice==2:
    print("""Exiting the game
See you later👋""")
    break
  while True:
      print("""\nDo you want to continue?
Press (Y/y) to continue or (N/n) to exit""")
      dec=input("Enter your decision: ").lower()
      if dec=='y':
        hangman()
      elif dec!='y':
        print("Thank You for playing the game😊 See you next time👋")
        break
  break
