# 🔴🟡 AI Connect Four — Minimax with Alpha-Beta Pruning

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Pygame](https://img.shields.io/badge/GUI-Pygame-red.svg)](https://www.pygame.org/)
[![NumPy](https://img.shields.io/badge/Math-NumPy-013243.svg?logo=numpy&logoColor=white)](https://numpy.org/)
An interactive, graphical Connect Four game featuring an adversarial AI opponent powered by the **Minimax Algorithm** enhanced with **Alpha-Beta Pruning** and a custom **heuristic window evaluation** engine.

---

## 📌 Game Overview

Connect Four is a zero-sum, two-player turn-based board game played on a 6-row by 7-column vertical grid. Players alternate dropping colored tokens into columns. The objective is to be the first to form a horizontal, vertical, or diagonal line of four tokens.

This project implements:

- A responsive graphical user interface rendered via `pygame`.
- Real-time mouse tracking and token drop animations.
- A strategic AI opponent that looks several turns ahead in the game-state decision tree.

---

## 🤖 The AI Engine: Minimax + Alpha-Beta Pruning

### 1. Game State Evaluation Heuristic

When the search tree reaches maximum depth, the board state is evaluated via a sliding 4-cell window (`evaluate_window`) across rows, columns, positive diagonals, and negative diagonals:

- **4 in a row (Win):** $+100$ score
- **3 in a row + 1 empty:** $+5$ score
- **2 in a row + 2 empty:** $+2$ score
- **Opponent 3 in a row threat:** $-4$ penalty (defensive blocking)
- **Center Column Bias:** $+3$ multiplier per token placed in the center column (the most strategically advantageous position in Connect Four).

### 2. Alpha-Beta Pruning Optimization

The standard minimax algorithm evaluates $O(b^d)$ nodes (where $b \approx 7$ is the branching factor and $d$ is the search depth). **Alpha-Beta Pruning** dramatically truncates suboptimal branches without affecting the final move decision:

- **Alpha ($\alpha$):** The minimum score the maximizing player is assured of.
- **Beta ($\beta$):** The maximum score the minimizing player is assured of.
- **Cutoff Condition:** Whenever $\alpha \ge \beta$, remaining branches in that subtree are pruned immediately.

```
                  Max (AI Turn)
                   /         \
                 /             \
          Min (Player)       Min (Player)
          /    |    \         /    |    \
        [+5]  [+2]  [-4]    [+10] [pruned]
```

---

## 🛠️ Technology Stack

| Component                | Library     | Purpose                                     |
| ------------------------ | ----------- | ------------------------------------------- |
| **Programming Language** | Python 3.9+ | Game logic & AI implementation              |
| **Matrix Calculations**  | NumPy       | 2D board state array slicing                |
| **Graphics & Audio**     | Pygame      | Window rendering, events, mouse interaction |

---

## 📂 Project Structure

```
connect_four/
├── main.py          # Pygame application loop, input handling, and board drawing
├── ai.py            # Minimax algorithm, alpha-beta pruning, and position scoring
├── game_rules.py    # Move validation, board transformations, and win conditions
├── Report.docx      # Academic project analysis report
└── README.md        # Documentation
```

---

## 🚀 Installation & Running

### 1. Prerequisites

Ensure you have Python 3.9 or higher installed.

### 2. Clone the Repository

```bash
git clone https://github.com/murattt00/AI-Connect-Four.git
cd AI-Connect-Four
```

### 3. Install Dependencies

```bash
pip install pygame numpy
```

### 4. Launch the Game

```bash
python main.py
```

### 🎮 Controls

- Move your mouse horizontally along the top of the grid to preview drop position.
- Left-click on any column to drop your red token.
- Watch the AI (yellow tokens) calculate its response!

---
