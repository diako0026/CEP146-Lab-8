**The Input Feeder (reading the cards), the Decision Node (making predictions), and the Tracker (adjusting the weights).**

# Lab 8: How a Neural Network Learns


## Part A: Training Phase

I started the training phase with 0 tokens for all features. Below is the weight tracker showing how my predictions improved and how I adjusted the weights (tokens) when I made mistakes.

| Card | Food | Service | Price | My Prediction | Actual Answer | Correct? | Weight Adjustments (Tokens) | 
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | 
| **1** | Great | Poor | Cheap | Like | Like | Yes | Food: 1, Service: 0, Price: 0 |
| **2** | Bad | Great | Expensive | DISLIKE | DISLIKE | Yes | Food: 2, Services: 0, Price: 0 |
| **3** | Good | Okay | Moderate | LIKE | LIKE | Yes | Food: 3, Services: 0, Price: 0 |
| **4** | Poor | Poor | Cheap | DISLIKE | DISLIKE | Yes | Food: 4, Services: 0, Price: 0 |
| **5** | Excellent | Excellent | Expensive | LIKE | LIKE | Yes | Food: 4, Services: 0, Price: 0 |
| **6** | Okay | Bad | Moderate | LIKE | DiSLIKE | No | **Mistakes:** Guessed LIKE. **Correction:** ADDED 1 token to Price. (Food: 5, Price: 1) |
| **7** | Great | Okay | cheap | LIKE | LIKE | Yes | Food: 6, Price: 1 |
| **8** | Poor | Excellent | Expensive | LIKE | DISLIKE | No | **Mistake:** Guessed LIKE for Service. **Correction:** Food is more important: (Food: 7, Price: 2) |
| **9** | Excellent | Poor | Moderate | LIKE | LIKE | Yes | Food: 8, Price: 2 |
| **10** | Okay | Okay | Expensive | DISLIKE | DISLIKE | Yes | Food: 8, Price: 3 |

**Final Weights after Training:**
Food (8 tokens) > Price (3 tokens) > Service (0 tokens).

---

## Part B: Testing Phase


Using the weights I learned from the training phase, I tested the 3 new cards:

**Card 11:** Food: Good, Service: Excellent, Price: Cheap ➔ Prediction: LIKE. (Because Food and Price are good). Actual: LIKE

**Card 12:** Food: Bad, Service: Bad, Price: Expensive ➔ Prediction: DISLIKE. (All features are bad). Actual: DISLIKE

**Card 13:** Food: Excellent, Service: Great, Price: Moderate ➔ Prediction: LIKE. (Food is excellent, which has the highest weight). **Actual: LIKE**

Since I worked alone, I compared my results with the main theory. My simulation proved that the system learns best when it realizes which feature has the highest impact (in this case, Food) and adjusts its decisions based on that.

---

## Reflection Discussion

**1.** How did your predictions improve?
At the beginning, I was mostly just guessing based on common sense. But after tracking the tokens, the Decision Node started to understand the actual pattern. By the end of the training phase, my predictions improved a lot because I knew exactly how much weight to give to Food compared to Service.

**2.** How did "weights" (tokens) help you learn?
The tokens were really helpful because they gave me a visual way to see which feature was more important. When I got a prediction wrong (like in Card 6), physically adding a token to the correct feature felt like the system was actually learning from its mistakes.

**3.** What would happen with more layers or inputs?
I think if we had more layers, the AI could understand more complex combinations of features. With more inputs (like adding "Restaurant Atmosphere"), the decisions would be more accurate, but it would also make the training process much longer and harder to track.

**4.** How does this reflect how real AI works?
This simulation is a simple version of how Backpropagation works in real AI. When a real neural network makes a wrong guess, it gets feedback and changes its internal math (weights) to fix the error. Our tokens were basically a physical version of the mathematical weights a real AI uses to learn.
