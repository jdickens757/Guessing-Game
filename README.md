# Guessing-Game
Python code
import random

# simple guessing game

#  We get the user input, if it's less than the right number, output.  if it's greater than, same.

#  If the number is matched.  YOU WIN.

#  You only have 10 tries.

# right number will be between 0 and 100


class GuessingGame:

    def __init__(self):

        # generate a random number

        self.attempts = 1

        self.max_attempts = 11

        self.right_number = random.randint(0, 101)

        self.won = False

        self.has_lost = False



    def guess(self):

        # get the user input, then check if it's the right number



        if self.attempts >= self.max_attempts:

            return self.lost()



        try:

            raw_input = input("What is your guess? (%d/%d): " % (self.attempts, self.max_attempts - 1))

            guessed_number = int(raw_input)

        except ValueError:

            print("Please enter a number!")

            if raw_input == "exit":

                print("Goodbye.")

                exit(0)

            return



        if guessed_number < self.right_number:

            print("Too low!")

        elif guessed_number > self.right_number:

            print("Too high!")

        elif guessed_number == self.right_number:

            return self.win()



        self.attempts += 1



    def win(self):

        print("YOU WON!!! THE NUMBER WAS %d" % self.right_number)

        self.won = True



    def lost(self):

        print("Sorry, you lost.  The number was %d." % self.right_number)

        self.has_lost = True



if __name__ == "__main__":

    game = GuessingGame()



    while not game.won:

        if not game.has_lost:

            game.guess()
