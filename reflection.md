# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?
**
When I first ran the Streamlit app, it looked like a simple number-guessing game, but something immediately felt off. The interface worked, but the hints didn’t make sense: it always told me to “Go HIGHER!” even when my guess was already too high. I also realized the secret number kept changing every time I clicked a button, which made it impossible to actually win. On top of that, the “Show hint” checkbox didn’t behave correctly because it didn’t consistently hide or reveal the hint after it was displayed. The main bugs were the reversed hint logic and the fact that the secret number wasn’t persisting between interactions.**
---

## 2. How did you use AI as a teammate?
**
I used GitHub Copilot in VS Code as my main AI tool, along with ChatGPT-style assistance for explanations and debugging ideas. One helpful suggestion from AI was refactoring the guessing logic into a separate logic_utils.py file; Copilot even suggested function structure and docstrings, and after writing pytest cases, everything passed, confirming it worked. However, one misleading suggestion was when Copilot recommended adding a “key” to the checkbox to fix the state issue. I tested that idea by implementing it and manually toggling the checkbox, but nothing changed — the real issue was that the hint only displayed during submission. That experience reminded me that AI suggestions still need to be tested carefully.**
---

## 3. Debugging and testing your fixes

**I considered a bug fixed only after I couldn’t reproduce the issue anymore and my tests confirmed the behavior was correct. For example, after fixing the hint logic, I wrote three pytest tests that checked high, low, and correct guesses using the check_guess function. Running python3 -m pytest showed all tests passed, which confirmed the logic was now correct. I also manually interacted with the UI multiple times, checking and unchecking the hint box to make sure it behaved properly. AI helped by suggesting I store values in st.session_state, which improved both my debugging and my understanding of how the app handled state.**
---

## 4. What did you learn about Streamlit and state?

**The secret number kept changing because Streamlit reruns the entire script every time a user interacts with a widget. Since the random number was generated at the top level of the script, it created a new number on every rerun. I now understand reruns as Streamlit re-executing the script from top to bottom whenever something changes in the UI. Session state acts like memory — it stores values so they don’t reset each time the script runs again. The fix was wrapping the random number generation in a conditional check so it only runs if "secret" is not already in st.session_state, which finally made the game stable.**
---

## 5. Looking ahead: your developer habits

One habit I want to keep using is writing tests immediately after fixing logic bugs. It made debugging more concrete and helped me confirm that my fixes actually worked instead of just “looking” correct. Next time I work with AI, I’ll be more intentional about questioning its suggestions before implementing them, especially when they relate to state or architecture. This project changed how I see AI-generated code — it’s a strong collaborator for brainstorming and scaffolding, but it doesn’t replace careful reading, testing, and reasoning.
