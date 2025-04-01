# Capstone Project: AI-Based Trading 

## Project Overview  
This capstone project brings together all prior course concepts to construct and evaluate two distinct trading strategies:
1. A **Manual Strategy**, based on hand-crafted trading rules using technical indicators.
2. A **Strategy Learner**, which uses machine learning to develop a trading policy automatically.

The goal is to compare both strategies against each other and against a buy-and-hold benchmark, gaining insight into human-crafted vs. AI-driven decision-making in quantitative trading.

**Languages/Tools Used:** Python, NumPy, Pandas, Matplotlib  
**Key Concepts:** Algorithmic Trading, Strategy Learning, Reinforcement Learning, Ensemble Learning, Technical Indicators, Model Evaluation

---

## Project Objectives
- Construct a **ManualStrategy** using at least 3 indicators from prior work (e.g., RSI, MACD, Momentum).
- Implement a **StrategyLearner** using:
  - A **Random Forest learner** (classification-based)  
  - An **Optimizer-enhanced learner** to refine feature parameters
- Use both strategies to trade **JPM stock** on defined in-sample and out-of-sample periods
- Conduct experiments to evaluate:
  - Strategy performance comparisons
  - Sensitivity of learned policies to transaction cost impacts
- Visualize and report performance with charts and tables

---

## Data & Constraints
- **Symbol:** JPM  
- **In-sample period:** Jan 1, 2008 – Dec 31, 2009  
- **Out-of-sample period:** Jan 1, 2010 – Dec 31, 2011  
- **Starting capital:** $100,000  
- **Positions allowed:** Long 1000, Short 1000, Neutral (0)  
- **Transaction costs:** $9.95 commission, 0.005 market impact  
- **Benchmark:** Buy-and-hold 1000 shares of JPM on day one, hold throughout

---

## Manual Strategy
- Uses a rule-based system combining 3+ indicators to generate trading signals  
- Entry signals mapped to trades (+1000 for long, -1000 for short)
- Exit signals derived when indicators flip sentiment
- Trades limited to one of three net positions: long, short, or neutral
- Strategy tested and plotted both in-sample and out-of-sample
- Evaluation includes:
  - Portfolio value vs. benchmark (normalized)
  - Entry point markers (blue for long, black for short)
  - Performance table with return, std dev, and mean daily return

---

## Strategy Learner
- Uses same indicators as ManualStrategy for a fair comparison
- Two-part learner:
  - **Random Forest-based classifier (Bag of RTLearners)**  
  - **Optimizer** to refine indicator parameters (e.g., SMA window size)
- Learns in `add_evidence()`, applies trading policy in `testPolicy()`
- Returned trades match the format of the ManualStrategy
- Accounts for impact/commission during learning
- Produces deterministic results in testing (learning OFF)

---

## Experiment 1: Strategy Comparison
- **In-sample and out-of-sample** comparisons of:
  - Strategy Learner
  - Manual Strategy
  - Benchmark
- Chart displays normalized portfolio values over time
- Evaluation focuses on return consistency, volatility, and net gain
- Metrics reported:
  - Cumulative return
  - Average daily return
  - Standard deviation

---

## Experiment 2: Sensitivity to Market Impact
- Explores how different impact values affect trading behavior and performance
- Runs StrategyLearner in-sample with:
  - Impact = 0.0 (ideal)
  - Impact = 0.005 (realistic)
  - Impact = 0.02 (high slippage)
- Two metrics recorded (e.g., number of trades, final portfolio value)
- Results plotted to show degradation in performance and trading frequency

---

## Technical Implementation
- Modular architecture with clearly separated components:
  - `ManualStrategy.py` for rule-based policy
  - `StrategyLearner.py` for ML-based policy
  - `marketsimcode.py` to simulate portfolio value
  - `indicators.py` reused and shared across both strategies
  - `experiment1.py`, `experiment2.py`, and `testproject.py` for orchestration
- Performance-optimized via vectorized computations and batch processing
- `testproject.py` runs all experiments and simulations in < 10 minutes

---

## Value & Learning Outcomes
- Applied **machine learning** to real-world financial strategy development  
- Learned to evaluate and compare algorithmic strategies under transaction costs  
- Gained insight into how **market impact** changes agent behavior  
- Built a reusable trading simulation framework using professional techniques  
- Developed understanding of **discretization**, **state encoding**, and **policy learning**

---

## Repository Access  
Due to academic policy, the full implementation—including learners, indicators, strategy scripts, and experiment code—is stored in a private GitHub repository. **Access available upon request.**
