### **Convergence Rate ([[Batch Gradient Descent]], convex cost like MSE)**

- **Convex cost function (like MSE):** Think of a nice smooth bowl-shaped curve. No sudden cliffs.
    
- **Fixed [[Learning Rate]]** You step down the bowl at a steady pace.
    
- **Eventually reaches optimum:** You _will_ end up at the bottom (the best solution).
    
- **Speed of reaching close to optimum:**
    
    - To get within **ϵ** (say, "close enough") of the bottom, it takes about **O(1/ϵ)** steps. ([[Computational Complexity]])
    
    - If you want **10× more precision** (make tolerance 10× smaller), expect **10× more steps**.
        

---

### **Easy to Remember Shortcut**

- **Accuracy costs time.**
    
- If you want the algorithm **10× more accurate**, it’ll be **10× slower**.
    
- Gradient Descent isn’t fast near the end — it crawls.