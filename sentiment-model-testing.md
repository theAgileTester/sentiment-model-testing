# Mini Project: Sentiment Model Testing – HuggingFace

**Model:** [cardiffnlp/twitter-roberta-base-sentiment-latest](https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment-latest)  
**Platform:** HuggingFace Hosted Inference  
**Task:** Sentiment Analysis (Negative / Neutral / Positive)  

---

## 1️⃣ Objective
Test and evaluate a pre-trained sentiment analysis model to identify potential weaknesses, edge cases, and areas where it may misclassify inputs, from an AI Tester perspective.

---

## 2️⃣ Test Categories

- **Normal / clear sentiment inputs**  
- **Negation handling** (`not`, `don’t`, `never`)  
- **Irony / sarcasm**  
- **Mixed sentiment** (positive + negative in same sentence)  
- **Short / vague texts**  
- **Emojis and informal expressions**  

---

## 3️⃣ Edge-case Test Cases and Observations

| Input | Expected | Model Output | Score | Observation / Issue |
|-------|---------|--------------|-------|------------------|
| I love this product! | Positive | Positive | 0.98 | Correctly classified |
| This is the worst service ever. | Negative | Negative | 0.95 | Correctly classified |
| I don’t hate it. | Positive | Neutral | 0.58 | Negation not fully captured |
| Oh great, another delay. Just perfect. | Negative | Positive | 0.60 | Model fails to detect irony / sarcasm |
| The camera is amazing but the battery life is terrible. | Mixed | Positive | 0.65 | Mixed sentiment compressed to single label |
| Meh. | Neutral | Negative | 0.40 | Short / ambiguous text misinterpreted |
| I love this app! ❤️ | Positive | Positive | 0.93 | Emoji handled correctly |
| I hate hate hate this. | Negative | Negative | 0.88 | Repeated emphasis correctly recognized |
| Not bad at all. | Positive | Neutral | 0.55 | Negation not fully captured |
| Could be better, could be worse. | Neutral | Neutral | 0.50 | Correct, but low confidence |

---

## 4️⃣ Tester Insights

- **Strengths:**
  - Clear, direct sentiment inputs classified accurately
  - Emojis are generally handled well
  - Repeated emphasis detected correctly

- **Weaknesses / Risks:**
  - Negation (“don’t hate this”, “not bad”) can be misclassified
  - Irony / sarcasm often misclassified
  - Mixed sentiment (positive + negative) is compressed to a single label
  - Short / vague statements sometimes misinterpreted

- **Recommendations for AI Tester / Deployment:**
  - Include edge-case examples in testing suite
  - Consider multi-label sentiment approach for mixed sentiment
  - Include emoji, informal and sarcastic text in model evaluation
  - Monitor confidence scores; flag low-confidence predictions

---

## 5️⃣ Key Takeaways (CV / Portfolio Ready)

- Conducted **bias and edge-case testing** for sentiment model  
- Evaluated **negation, irony, mixed sentiment, and emoji handling**  
- Identified potential **misclassification risks** in real-world social media data  
- Produced a **mini tester report** highlighting model weaknesses and recommendations
