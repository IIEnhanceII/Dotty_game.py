import random as r
import time

# ---------------- Player Class ----------------
class Player:
    def __init__(self):
        # Player keeps track of their chosen number, guess, and possible legal guesses
        self.choice = None
        self.guess = None
        self.possible_choices = None

    def user_choice(self):
        """
        Prompt the player to select a number between 1 and 10.
        If input is invalid or outside range, exit the game.
        """
        try:
            self.choice = int(input("Enter a number in the range 1 to 10: "))
            if self.choice not in range(1, 11):
                raise ValueError
        except (ValueError, EOFError):
            printing("Invalid choice. Exiting...")
            raise EOFError

    def user_guess(self, legal_list):
        """
        Player guesses the sum. The guess must be within their legal possible range.
        - If guess is impossible → player loses immediately.
        - If input is invalid → player loses immediately.
        """
        self.possible_choices = legal_list
        try:
            self.guess = int(input("Enter your guess: "))
            if self.guess not in self.possible_choices:
                printing("You made an impossible guess. You lose!")
                return False
        except EOFError:
            printing("\nInput ended. Exiting...")
            raise
        except ValueError:
            printing("Invalid guess (not a number). You lose!")
            return False
        return True


# ---------------- Ai Class ----------------
class Ai:
    def __init__(self):
        """
        AI randomly selects a hidden choice (1–10).
        Based on its choice, it generates its possible guess list.
        """
        self.choice = r.randint(1, 10)
        self.guess = None
        self.list = get_list(self.choice)

    def get_guess(self):
        """
        AI makes a random guess from its remaining possible list.
        """
        self.guess = r.choice(self.list)
        return self.guess


# ---------------- Game Class ----------------
class Game:
    def __init__(self):
        self.player = Player()
        self.ai = Ai()
        self.correct_sum = None  # True sum of both choices
        self.game_over = False

    def setup(self):
        """
        Initializes the game:
        - Player makes their choice.
        - Compute the correct sum (player + AI choices).
        """
        self.player.user_choice()
        self.correct_sum = self.player.choice + self.ai.choice

    def play(self):
        """
        Main game loop:
        - Player and AI alternate making guesses.
        - Guesses are validated against the true sum.
        - First correct guess wins.
        - Invalid (impossible) guesses cause immediate loss.
        """
        try:
            self.setup()
            while not self.game_over:
                # Player's turn
                possible_nums = get_list(self.player.choice)
                valid = self.player.user_guess(possible_nums)
                if not valid:
                    self.game_over = True
                    break

                if self.player.guess == self.correct_sum:
                    printing("!-- You Won --!")
                    break
                else:
                    printing("!-- Incorrect Guess --!")
                    sort_list(self.player.guess, self.ai.list)

                # AI's turn
                ai_guess = self.ai.get_guess()
                print(f"AI guesses: {ai_guess}")
                if ai_guess == self.correct_sum:
                    print("!-- AI Won --!")
                    break
                else:
                    sort_list(ai_guess, self.ai.list)
                    print("AI was wrong.")
        except EOFError:
            print("\nGame ended due to EOF.")
            self.game_over = True


# ---------------- Helper Functions ----------------
def get_list(choice):
    """
    Generate all possible legal guesses for a given choice.
    Rules:
    - Minimum possible sum = choice + 1
    - Maximum possible sum = choice + 10
    - Cap at 19 (since both choices ≤ 10).
    """
    return [x for x in range(choice + 1, min(choice + 11, 20))]

def sort_list(guess, ai_list):
    """
    Update AI's possible guess list based on the given guess.
    - If guess > 10 → remove numbers smaller than (guess - 10).
    - If guess < 10 → remove numbers from guess up to 10.
    - If guess == 10 → remove only 10 if present.
    Also prints AI's reaction to the update.
    """
    removed = 0
    if guess > 10:
        # Remove low-end numbers
        for i in range(1, guess - 10):
            if i in ai_list:
                ai_list.remove(i)
                removed += 1
    elif guess < 10:
        # Remove higher numbers up to 10
        for i in range(guess, 11):
            if i in ai_list:
                ai_list.remove(i)
                removed += 1
    else:  # guess == 10
        if guess in ai_list:
            ai_list.remove(guess)
            removed += 1
    
    # Feedback messages
    if len(ai_list) == 1:
        print("....Was that it?")
    elif removed == 0:
        print("That was a good guess!")
    else:
        print(f"Ai removed {removed} elements from its list")
        
    return ai_list

def printing(comment, delay=0.1):
    """
    Prints a message character-by-character with delay,
    for dramatic effect.
    """
    for char in comment:
        print(char, end="")
        time.sleep(delay)
    print("\n")

# ---------------- Run ----------------
if __name__ == "__main__":
    Game().play()
