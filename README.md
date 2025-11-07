🎲 Dotty Game (Usogui: Tower of Karma Inspired)

A simple command-line guessing game inspired by the psychological duel between Baku Madarame and Suteguma Satoru in Usogui: Tower of Karma.
In this game, both the User and the AI must guess the correct sum of their hidden numbers — but beware, making an impossible guess will cost you the game instantly.

---

🧩 How the Game Works

1. The User chooses a number between "1" and "10".
2. The AI secretly chooses its own number in the same range.
3. Both take turns guessing what the sum of their two numbers might be.
4. The first to guess the correct sum wins.
5. But if you guess an impossible number, you lose immediately.

---

⚖️ Rules

1. Your guess cannot be less than or equal to your chosen number — that would make it an impossible guess.
2. Your guess cannot exceed "20" or your "(choice + 10)" — again, impossible.
3. “Impossible” is judged from your own perspective, not the AI’s.
   - Example:
      - If you chose "10" and the AI chose "1",
      - and you guessed "15", this is still possible for you, even though the true sum is lower.

---

🧠 Example Gameplay

Enter a number in the range 1 to 10: 7
Enter your guess: 13
!-- Incorrect Guess --!
AI guesses: 15
AI was wrong.
Enter your guess: 11
!-- You Won --!

---

🕹️ Features

- Interactive command-line gameplay
- Intelligent AI with dynamic possible-guess pruning
- “Dramatic typing” effect for dialogue pacing
- Clear win/loss feedback
- Faithful recreation of Usogui’s logical tension

---

🧱 Code Structure

Component| Description
Player| Handles user input, choice, and validation of guesses
Ai| Chooses hidden number, manages possible guesses, and plays optimally
Game| Controls flow: setup, turns, and win/loss conditions
Helper Functions| Utility functions for validation, range management, and styled printing

---

🚀 Running the Game

Requirements

- Python 3.8 or higher
- No external dependencies (only built-in libraries)

Run Command

python Dotty_game.py

---

🧩 Notes

- To exit early, use Ctrl + D (EOF).
- The AI’s reasoning process is intentionally semi-random to keep the game unpredictable.
- Try experimenting with different choices to see how strategy evolves!

---

📜 License

This project is released under the MIT License.
Feel free to modify or expand upon it — credit appreciated.

---

💡 Inspiration

Inspired by Usogui, a psychological manga by Toshio Sako, known for its intricate mind games and logic duels. I simply took a part of one of its arc.