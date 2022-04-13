# terminal-wordle
Fully randomized wordle in python

The projects works in terminal.
If you want to use it as part of your code check LICENSE.


```
import sys
from random_word import RandomWords
word = ""

def get_word():
    """
    generating a random word and returning if not None
    """
    global word
    r = RandomWords()
    w = r.get_random_word(minLength=5, maxLength=5)
    if w is None:
        get_word()
    word = w

def game_over():
    global word
    print("\n/////////\nGame over\n/////////\n\nThe word was "+word)

def check_win(guess):
    global word
    gl = list(guess)
    wl = list(word)
    if(gl == wl):
        print("\n////////\nYou won\n////////")
        sys.exit()
    else:
        for i in range(5):
            if(gl[i] == wl[i]):
                print(gl[i]+": in correct place")
            elif(gl[i] in wl):
                print(gl[i]+": in the word but incorrect place")
            else:
                print(gl[i]+": not in the word")

def game_start():
    global word
    get_word()
    i = 0
    print("Wordle")
    print("But more fun")
    while(i!=6):
        guess = str(input("\nGuess the 5 letters word\n"))
        if(len(guess)!=5):
            i = i-1
        else:
            i = i+1
            check_win(guess)
    game_over()

if __name__ == "__main__":
    game_start()
e
```
