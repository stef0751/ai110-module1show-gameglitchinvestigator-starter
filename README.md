# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [X] Describe the game's purpose: a simple number‑guessing app built with Streamlit where the player tries to match a randomly chosen secret, with difficulty‑based ranges, limited attempts and a scoring system.
- [X] Detail which bugs you found: the hint logic was inverted (every “Too High” guess produced “Go HIGHER!”) and the show‑hint control behaved like a one‑time flag, so toggling the checkbox after a guess didn’t hide/show the existing hint.
- [X] Explain what fixes you applied: swapped the hint messages in check_guess and moved all game logic into logic_utils.py for testability; added session‑state tracking of the last hint and a post‑submit display block so the checkbox truly toggles hint visibility.

## 📸 Demo
- [X] Screenshot
<img width="991" height="916" alt="Screenshot 2026-03-04 at 10 30 04 PM" src="https://github.com/user-attachments/assets/59af803f-551f-4690-b83e-89b12dbaeb1f" />
