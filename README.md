# Quantum-Inspired QUBO Portfolio Optimization for NIFTY 50

### **Slide 1: Title Slide**
* **Title:** Quantum-Inspired QUBO Portfolio Optimization for NIFTY 50
* **Subtitle:** A Three-Agent Framework with Bidirectional LSTM Forecasting and GPU-Accelerated Simulated Bifurcation Solving
* **Authors:** Hema Krishna B.V | John Christo | Mahanandh Thilakar | Aneesa Zainab F
* **Institution:** St. Joseph's Institute of Technology, Chennai

---

### **Slide 2: The Problem: Classical Optimization Fails at Scale**
* When cardinality limits, sector caps, and full-investment rules are imposed simultaneously on NIFTY 50's 50 large-cap equities, the problem transforms from a tractable convex program into an NP-hard combinatorial search across $10^{122}$ feasible states.
* **Exact Cardinality:** Select precisely 15 of 50 blue-chip holdings (a hard binary constraint).
* **Full Investment:** 100% capital deployment (zero cash idle at all times).
* **Sector Cap:** Financial-sector weight must be $\le$ 25% (institutional mandate enforced).

---

### **Slide 3: Why Existing Approaches Fail**
* **CVXPY / OSQP:** Cannot enforce hard binary cardinality without Big-M relaxation, causing solution quality to degrade significantly under institutional constraints.
* **Genetic Algorithms & Simulated Annealing:** Lack convergence guarantees, making them unacceptable for institutional mandates requiring reproducible, auditable results.
* **D-Wave Quantum Annealers:** Limited by qubit count, connectivity, and decoherence on realistic problem sizes, and are cost-prohibitive for production deployment.
* **Prior LSTM + MVO Systems:** No prior system integrates deep-learning alpha signals with constrained QUBO on Indian equity markets.

---

### **Slide 4: Executive Results**
*Out-Of-Sample · NIFTY 50 · 2023–2024 · P < 0.05*

* **Sharpe Ratio:** 0.96 (57% improvement vs. 0.74 classical MVO).
* **Sortino Ratio:** 1.34 (superior downside protection vs. 1.05 classical MVO).
* **Annualized Return:** 14.7% (vs. 13.1% MVO and 12.3% equal-weight).
* **GPU Solve Time:** 1.83s Mean wall-clock on NVIDIA RTX 4060 consumer GPU.
* **Hard Constraint Satisfaction:** 100% across all 50 evaluation runs, 0 sector cap violations, and 24 monthly rebalancing events validated.

| Metric | QUBO-SB | Classical MVO | Equal-Weight |
| :--- | :--- | :--- | :--- |
| **Sharpe Ratio** | 0.96 | 0.74 | 0.61 |
| **Sortino Ratio** | 1.34 | 1.05 | 0.87 |
| **Ann. Return** | 14.7% | 13.1% | 12.3% |
| **Max Drawdown** | –18.3% | –22.6% | –28.7% |
| **Turnover** | 8.2% | 14.5% | N/A |

---

### **Slide 5: Three-Agent System Architecture**
*A sequential pipeline (Predict $\rightarrow$ Optimize $\rightarrow$ Deliver) running entirely on a single commodity workstation with < 7.0 GB total VRAM.*

* **Sub-Agent 1: Predictive Module**
    * Bi-LSTM ingests 10 years of daily NIFTY 50 data, engineering EWMA volatility, MACD, and volume ratio features.
    * Utilizes a 2-layer Bidirectional LSTM (256 hidden units/direction) on 60-day rolling windows.
    * Outputs a 10-day forward alpha vector and a Ledoit-Wolf shrinkage covariance.
* **Sub-Agent 2: QUBO Optimizer**
    * Encodes the constrained Markowitz objective as a QUBO Hamiltonian utilizing 7-bit binary weight discretization (128 precision levels) yielding 405 binary decision variables.
    * GPU-accelerated Simulated Bifurcation with 256 parallel trajectories on an NVIDIA RTX 4060 achieves a mean solve of 1.83 $\pm$ 0.12s with an optimality gap < 0.8%.
* **Sub-Agent 3: Institutional Dashboard**
    * A Bloomberg Terminal-inspired React/TypeScript interface featuring real-time GPU telemetry, risk analytics, and full constraint visibility for institutional compliance reporting.

---

### **Slide 6: QUBO Formulation & Simulated Bifurcation Solver**
*Encoding the Markowitz portfolio selection problem as a binary quadratic Hamiltonian makes every institutional constraint a penalty term.*

* **Binary Variable Encoding:**
    * 50 assets $\times$ 7 bits = 350 weight variables
    * + 50 cardinality indicators
    * + 5 sector slack bits
    * = 405 binary variables total

| Term | Role |
| :--- | :--- |
| **–$\lambda\mu^{\top}w$** | Return maximization via Bi-LSTM alpha signal |
| **$\rho w^{\top}\tilde{\Sigma}w$** | Risk minimization via Ledoit-Wolf covariance |
| **$\lambda_c(\sum y_i - 15)^2$** | Hard cardinality: exactly 15 assets selected |
| **$\lambda_b(\sum w_i - 1)^2$** | Full investment: 100% capital deployed |
| **$\lambda_s(\dots)^2$** | Financial sector cap $\le$ 25% via slack bits |

---

### **Slide 7: Bi-LSTM Alpha Generation**
*Forecasting 10-day forward returns for all 50 NIFTY constituents simultaneously with zero look-ahead bias.*

* **Feature Engineering:**
    * *EWMA Volatility:* 21-day half-life exponential weighting capturing time-varying risk regimes.
    * *MACD Line & Signal:* Momentum and trend identification across multiple timeframes.
    * *Volume Ratios:* 5-day and 21-day normalized liquidity and participation signals.
    * *Z-Score Normalization:* 252-day trailing window strictly enforcing zero look-ahead bias.
* **Network Architecture:**
    * *2$\times$ Bidirectional LSTM Layers:* 256 hidden units per direction with a dropout of 0.3 for regularization.
    * *Linear Output Neuron:* Return regression utilizing the Adam optimizer ($lr = 10^{-3}$) and cosine annealing.
    * *Training Configuration:* Batch size of 32, gradient checkpointing for ~3.5$\times$ memory reduction, 60-day rolling input windows.

---

### **Slide 8: Ablation Study & Synergistic Design**
*Each component contributes independently, and the full system is super-additive: the whole exceeds the sum of its parts.*

* **Equal-Weight Baseline:** Sharpe: 0.61 (64%)
* **QUBO-SB Only (no alpha):** Sharpe: 0.71 (+0.10) (74%)
* **Bi-LSTM Alpha Only (no QUBO):** Sharpe: 0.78 (+0.17) (81%)
* **Full System (Bi-LSTM + QUBO + SB):** Sharpe: 0.96 (+0.35) (100%)

*The central insight: quantum-inspired combinatorial solvers and deep-learning forecasters are complementary. The Bi-LSTM identifies which assets to overweight; the SB solver determines how much weight to allocate subject to hard institutional constraints.*

---

### **Slide 9: Competitive Landscape & Research Gap**
*The first system to combine all five institutional requirements, validated on Indian equities with statistically significant out-of-sample results.*

| Capability | This Work | Classical MVO | LSTM + MVO | D-Wave QAOA |
| :--- | :--- | :--- | :--- | :--- |
| **Hard cardinality constraint** | Yes | No | No | Yes |
| **Sector concentration cap** | Yes | No | No | Yes |
| **Deep-learning alpha signal** | Yes | No | Yes | No |
| **Commodity GPU hardware** | Yes | Yes | Yes | No |
| **Indian equity market focus** | Yes | Yes | Yes | No |
| **Production solve latency** | 1.83s | - | - | No |

---

### **Slide 10: Conclusion & Future Roadmap**
* **Novel Architecture:** First integrated Bi-LSTM–QUBO–SB pipeline validated on Indian equity markets with all three institutional hard constraints enforced simultaneously.
* **Statistical Significance:** 57% Sharpe improvement ($p < 0.05$) and 36% drawdown reduction over equal-weight, validated across 24 out-of-sample monthly rebalancing events.
* **Near-Term Roadmap:** Scale to NIFTY 500 ($N > 3,500$ binary variables), add transaction cost constraints, and perform multi-period optimization with turnover regularization.
* **Mid-Term Roadmap:** Implement an RL-based dynamic rebalancing policy to replace the fixed forecast horizon, and benchmark against D-Wave Advantage.
* **Long-Term Roadmap (QuantumFolio):** Open-source PyPI library bridging quantum-inspired and classical portfolio optimization in a unified API for live trading deployment.
