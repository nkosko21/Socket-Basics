Client.py is broken into three main functions, main(), analyze_guess(), and remove_guess(). 

Main() takes in the inputs from the user, checks for flags, creates the socket accordingly, and enters a while loop where it keeps guessing until a flag or error is found, upon which the socket is closed. When the server sends back a "retry" message, main() calls analyze_guess() and proceeds to guess the first remaining word from the official word list.

Analyze_guess() contains the guessing strategy. The strategy goes through the marks of the previous guess, adds any letters that are incorrect into an incorrect list, and letters that are correct but in the wrong position to a correct list, and adds any letters that were in the correct position to the final guess. It then sends the correct and incorrect list to remove_guess().

remove_guess() takes in a list of correct and incorrect letters, and proceeds to parse through the official word list and remove words that do not contain correct letters and removes words that contain incorrect letters. In addition to this, the method removes words that do not have the same letters in the same positions as the final guess.

The main challenge in this assignment was the guessing strategy. Implementing a simple guessing strategy was easy, but then I was faced with the problem of double letters. When the correct word has multiple of the same letter, such as bloom or thats, one of the o's or t's can be guessed and shown to be correct, leading to the program to think that is the only letter of its kind. My work around was to not remove a word from the word list if it contained a correct letter in the correct place, and also contained that same letter somewhere else in the word. This is evened out in the main() method where a word is removed from the word list as soon as it is guessed.

I tested my code by running it nearly a hundred times with every combination of different flags to make sure none of them came back with any errors.