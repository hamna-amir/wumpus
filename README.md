# wumpus
Web-based Dynamic Pathfinding Agent that acts as a Knowledge-Based Agent.
# Wumpus World Logic Agent

A React-based simulation of the classic Wumpus World AI problem. This project features a custom propositional logic inference engine that uses Resolution Refutation to help an agent safely navigate a grid, avoid pits and the Wumpus, and locate the gold.

## Features

* **Logic Inference Engine:** Implements a resolution-based refutation system to prove the safety of adjacent cells.
* **Dynamic World Generation:** Automatically generates a new environment with randomized pits, Wumpus location, and gold placement.
* **Interactive Simulation:** Move manually to test your own logic, or enable "Auto-mode" to watch the agent make decisions based on its Knowledge Base (KB).
* **Real-time Logging:** View the internal reasoning process (TELL/ASK operations) of the agent as it navigates the grid.
* **Visual Feedback:** A responsive grid interface that tracks visited, safe, and dangerous cells.

## Tech Stack

* **Framework:** React (using functional components and hooks)
* **State Management:** `useState`, `useRef` (for the non-rendering mutable Knowledge Base)
* **Styling:** CSS-in-JS (Inline styles)

## Getting Started

### Prerequisites
* [Node.js](https://nodejs.org/) (v16 or higher)
* npm or yarn

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/yourusername/wumpus-world-solver.git
    cd wumpus-world-solver
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Run the application:**
    ```bash
    npm start
    ```

4.  **Open in Browser:**
    The app will typically run at `http://localhost:3000`.

## How the Logic Works

The core of this project is a `KnowledgeBase` class that manages the agent's understanding of the world.

* **CNF Conversion:** The agent stores percepts (Breeze, Stench) as clauses in Conjunctive Normal Form (CNF).
* **Biconditional Logic:** When a percept is detected, the agent maps it to potential hazards (Pits or Wumpus) using biconditional rules (e.g., `Breeze ⟺ P_neighbor1 ∨ P_neighbor2 ...`).
* **Resolution Refutation:** To determine if a cell is safe, the agent asks: "Is it possible for a Pit or Wumpus to be here?". It does this by adding the negation of the safety statement to the KB and attempting to derive a contradiction (an empty clause). If a contradiction is found, the agent proves the cell is safe.

## Usage

1.  **New World:** Click "New World" to generate a fresh grid.
2.  **Step:** Manually move the agent step-by-step to observe how the inference engine reacts to new percepts.
3.  **Auto:** Toggle "Auto" to allow the agent to continuously process its surroundings and make logical decisions until it finds the gold, gets stuck, or perishes.

