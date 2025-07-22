# Dotty_game.py

This game is inspired from a facinating event in the manga Usogui, Tower of Karma. In this game both Baku madarame and Suteguma Satoru were to guess the sum of number of beads they have, so they can win the chance to play surpassing the leader.

#Game:

User would choose a number from [1-10], lets call it "choice".
Now one by one, both Ai and User would make guess on what the sum can be.
The winner would be decided when the correct sum is guessed, or someone guesses an impossible number.
#Rules:-

The guessed number cannot be less than or equal to the choice they made. This would result in immediate failure as the guess cannot be impossible number.
Similarly, the guess cannot be more than 20 or more then choice+10. As otherwise, its an impossible number.
The Verdict whether a number is impossible or not is totaly based on player's prespective not Both of their's. Means: If user choice was, 10. and Ai choice was, 1. And user made the guess 15. Then it would be an incorrect answer, not impossible choice. As, from user's prespective, 15 is possible.
