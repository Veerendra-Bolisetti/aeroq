<p align="center">
  <img src="https://img.shields.io/badge/AeroQ-Quantum%20Flight%20Optimisation-00d4ff?style=for-the-badge&logo=airplaydisplay&logoColor=white" alt="AeroQ Banner"/>
</p>

<h1 align="center">✈️ AeroQ</h1>
<h3 align="center"><em>Quantum-Assisted Low-Emission Flight Path Optimisation</em></h3>
<p align="center"><strong>"Optimising the route, not just the distance."</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/FastAPI-0.115-009688?style=flat-square&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/React-18+-61DAFB?style=flat-square&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/Vite-8.3-646CFF?style=flat-square&logo=vite&logoColor=white" />
  <img src="https://img.shields.io/badge/Quantum-QAOA%20Simulator-7b61ff?style=flat-square&logo=atom&logoColor=white" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/🏆_Hackathon-INNOVATION%20TECHIES-ff6f00?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Use_Case-Aviation%20Emissions%20%26%20Flight--Path%20Optimisation-00e676?style=for-the-badge" />
</p>

<p align="center">
  <a href="#-problem-statement">Problem</a> •
  <a href="#-our-solution">Solution</a> •
  <a href="#-key-features">Features</a> •
  <a href="#%EF%B8%8F-architecture">Architecture</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-getting-started">Setup</a> •
  <a href="#-demo-scenarios">Demos</a> •
  <a href="#-team">Team</a>
</p>

---

## 🌍 Problem Statement

Aviation accounts for **~2.5% of global CO₂ emissions**, and flight path planning remains largely dependent on classical shortest-distance algorithms that fail to account for multi-dimensional factors like:

- 🌬️ **Wind conditions** (headwinds, tailwinds, crosswinds)
- 🚦 **Airspace congestion** and traffic delays
- 🛑 **Restricted zones** and no-fly areas
- ⛽ **Fuel efficiency** vs. distance trade-offs
- 🌧️ **Weather penalties** and atmospheric conditions

Traditional route planners optimise for **distance alone** — but the shortest path is rarely the greenest or most efficient path.

## 💡 Our Solution

**AeroQ** is a quantum-assisted flight path optimisation platform that leverages **hybrid quantum-classical algorithms** to find routes that minimise a **multi-objective cost function** balancing distance, fuel consumption, CO₂ emissions, congestion, delay, and weather factors simultaneously.

### How It Works

```
┌──────────────────────────────────────────────────────────────────┐
│                    AeroQ Hybrid Pipeline                        │
│                                                                  │
│  ┌─────────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐  │
│  │  Classical   │──▶│  QUBO    │──▶│ Quantum  │──▶│Classical │  │
│  │Preprocessing│   │ Encoding │   │  Solver  │   │Post-Proc │  │
│  └─────────────┘   └──────────┘   └──────────┘   └──────────┘  │
│                                                                  │
│  Graph Reduction   Path→Binary    QAOA / SA     Validation &    │
│  & Pruning         Variables      Simulation    Improvement     │
└──────────────────────────────────────────────────────────────────┘
```

1. **Classical Preprocessing** — Reduces the airspace graph by pruning restricted edges and irrelevant nodes
2. **QUBO Encoding** — Converts the path-selection problem into a Quadratic Unconstrained Binary Optimisation matrix
3. **Quantum Solver** — Solves the QUBO using QAOA (Quantum Approximate Optimisation Algorithm) statevector simulation for small instances, or quantum-inspired simulated annealing for larger ones
4. **Classical Post-Processing** — Validates feasibility and applies local improvement heuristics

---

## 🚀 Key Features

### 🧮 Quantum Computing
- **QAOA Statevector Simulation** — Full quantum circuit simulation for up to 12 qubits
- **QUBO Formulation** — Transparent encoding of path-selection as binary optimisation
- **Brute-Force Exact Solver** — For small instances (≤16 variables) to verify quantum results
- **Quantum-Inspired Fallback** — Simulated annealing for larger problem instances

### 📊 Multi-Objective Optimisation
- **6-factor cost function**: Distance, Fuel, Emissions, Congestion, Delay, Weather
- **Configurable weights** — Tune the importance of each factor via sliders
- **Sensitivity analysis** — See how changing one weight affects the optimal route

### 🌐 Interactive Dashboard
| Page | Description |
|------|-------------|
| **Dashboard** | One-click demo with live pipeline progress, route visualisation, and metrics |
| **Scenario Lab** | Configure custom flight scenarios with different aircraft, winds, and restrictions |
| **Quantum Lab** | Explore QUBO matrices, solver details, and quantum simulation internals |
| **Comparison** | Side-by-side classical vs. hybrid vs. quantum results across multiple scenarios |
| **Sensitivity** | Interactive weight sensitivity analysis with real-time charts |
| **About** | Technical documentation, methodology transparency, and disclaimers |

### 🌿 Emissions Analysis
- CO₂ emissions calculated using **ICAO-simplified methodology** (3.16 kg CO₂/kg jet fuel)
- Detailed emissions breakdown per route
- Fuel/CO₂ reduction percentages comparing classical vs. hybrid approaches
- Full methodology transparency with documented assumptions

---

## 🏗️ Architecture

```
aeroq/
├── backend/                      # Python FastAPI Backend
│   ├── app/
│   │   ├── main.py               # FastAPI application entry point
│   │   ├── api/
│   │   │   └── routes.py         # REST API endpoints
│   │   ├── models/
│   │   │   └── schemas.py        # Pydantic data models
│   │   ├── quantum/
│   │   │   ├── qubo.py           # QUBO formulation & classical solvers
│   │   │   └── simulator.py      # QAOA quantum circuit simulator
│   │   ├── optimization/
│   │   │   ├── classical.py      # Dijkstra & A* optimisers
│   │   │   └── hybrid.py         # Hybrid quantum-classical pipeline
│   │   ├── emissions/
│   │   │   └── model.py          # CO₂ & fuel emissions calculator
│   │   ├── simulation/
│   │   │   └── scenarios.py      # Preset demo scenarios
│   │   └── services/
│   │       ├── pipeline.py       # End-to-end orchestrator
│   │       ├── graph_generator.py# Synthetic airspace graph builder
│   │       ├── cost_function.py  # Multi-objective cost function
│   │       └── explainer.py      # Route explanation generator
│   ├── tests/
│   │   ├── test_core.py          # Core algorithm tests
│   │   └── test_api.py           # API endpoint tests
│   └── requirements.txt
│
├── frontend/                     # React + Vite Frontend
│   ├── src/
│   │   ├── App.jsx               # Main app with sidebar navigation
│   │   ├── pages/
│   │   │   ├── Dashboard.jsx     # Main demo dashboard
│   │   │   ├── ScenarioLab.jsx   # Custom scenario configuration
│   │   │   ├── QuantumLab.jsx    # Quantum internals explorer
│   │   │   ├── Comparison.jsx    # Multi-scenario comparison
│   │   │   ├── Sensitivity.jsx   # Weight sensitivity analysis
│   │   │   └── About.jsx         # Documentation & methodology
│   │   ├── services/             # API client
│   │   ├── index.css             # Design system & styling
│   │   └── main.ts               # Entry point
│   └── package.json
│
└── README.md
```

---

## 🔧 Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Backend** | Python 3.10+ | Core logic & API |
| **API Framework** | FastAPI 0.115 | REST API with auto-docs |
| **Data Validation** | Pydantic 2.9 | Schema validation & serialization |
| **Graph Algorithms** | NetworkX 3.3 | Airspace graph & classical optimisation |
| **Quantum Simulation** | NumPy + Custom QAOA | Statevector quantum circuit simulation |
| **Scientific Computing** | SciPy 1.14 | Numerical methods |
| **Visualisation (backend)** | Plotly 5.24 | Data generation for charts |
| **Frontend** | React + Vite 8.3 | Interactive UI |
| **Charts (frontend)** | react-plotly.js | Interactive data visualisation |
| **Icons** | Lucide React | UI icons |
| **Routing** | React Router DOM 7 | Client-side navigation |
| **Testing** | pytest + httpx | Unit & integration tests |

---

## 🚀 Getting Started

### Prerequisites

- **Python 3.10+** — [Download](https://www.python.org/downloads/)
- **Node.js 18+** — [Download](https://nodejs.org/)
- **Git** — [Download](https://git-scm.com/)

### 1. Clone the Repository

```bash
git clone https://github.com/Veerendra-Bolisetti/aeroq.git
cd aeroq
```

### 2. Backend Setup

```bash
# Navigate to backend
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run the backend server
uvicorn app.main:app --reload --port 8000
```

The API will be available at `http://localhost:8000` with interactive docs at `http://localhost:8000/docs`.

### 3. Frontend Setup

```bash
# Navigate to frontend (from project root)
cd frontend

# Install dependencies
npm install

# Run the development server
npm run dev
```

The frontend will be available at `http://localhost:5173`.

### 4. Run Tests

```bash
cd backend
pytest tests/ -v
```

---

## 🎮 Demo Scenarios

AeroQ ships with **5 preset scenarios** that demonstrate different optimisation challenges:

| Scenario | Conditions | Key Challenge |
|----------|-----------|---------------|
| **A: Normal Conditions** | Calm wind, low congestion, no restrictions | Baseline comparison |
| **B: High Congestion** | Severe congestion, high delay sensitivity | Route around busy corridors |
| **C: Strong Headwind** | Wide-body aircraft, strong headwinds, weather penalty | Fuel efficiency under adverse conditions |
| **D: Restricted Airspace** | 3 restricted zones, crosswind, 3× emissions weight | Navigate around no-fly zones |
| **E: Multi-Route** | Regional aircraft, tailwind, balanced weights | Balanced multi-objective optimisation |

---

## 📐 The Math Behind AeroQ

### Multi-Objective Cost Function

```
Cost(route) = w₁·Distance + w₂·Fuel + w₃·Emissions + w₄·Congestion + w₅·Delay + w₆·Weather
```

Each weight (w₁–w₆) is user-configurable, enabling exploration of different optimisation priorities.

### QUBO Formulation

The path-selection problem is encoded as:

```
min  xᵀQx

subject to:  Σ xᵢ = 1  (exactly one path selected)
```

Where:
- `xᵢ ∈ {0, 1}` — binary variable for each candidate path
- `Q[i][i] = cost_i - P` — diagonal: path cost minus penalty
- `Q[i][j] = 2P` — off-diagonal: constraint penalty terms
- `P` — penalty weight enforcing the exactly-one constraint

### QAOA (Quantum Approximate Optimisation Algorithm)

For problems with ≤12 binary variables, AeroQ runs a genuine QAOA simulation:

1. Initialise uniform superposition |+⟩ⁿ
2. Apply `p` alternating layers of:
   - **Cost unitary**: `exp(-iγC)` — encodes the objective
   - **Mixer unitary**: `exp(-iβB)` — enables state exploration
3. Optimise parameters (γ, β) via classical search
4. Sample the most probable state as the solution

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|---------|-------------|
| `GET` | `/api/health` | Health check |
| `GET` | `/api/scenarios` | List all preset scenarios |
| `GET` | `/api/scenarios/{id}` | Get specific scenario config |
| `POST` | `/api/optimize` | Run full optimisation pipeline |
| `POST` | `/api/optimize/demo` | Run demo with default scenario |
| `POST` | `/api/graph` | Generate airspace graph |
| `GET` | `/api/cost-function` | Get cost function formula |
| `GET` | `/api/emissions/methodology` | Get emissions methodology |
| `POST` | `/api/sensitivity` | Run weight sensitivity analysis |
| `POST` | `/api/experiment` | Run quantum vs classical experiments |
| `POST` | `/api/scenario-comparison` | Compare all preset scenarios |

---

## 📊 Results & Insights

AeroQ demonstrates that the hybrid quantum-classical approach can find routes with:

- ✅ **Lower objective scores** by considering multiple factors simultaneously
- ✅ **Reduced fuel consumption** through wind-aware routing
- ✅ **Lower CO₂ emissions** via emissions-weighted optimisation
- ✅ **Congestion avoidance** by routing around busy corridors
- ✅ **Restricted zone compliance** while maintaining route feasibility

> **Note**: All results are from **synthetic simulations** using demonstration data. They illustrate the potential of the approach but do not claim quantum advantage on production-scale problems.

---

## 🔮 Future Scope

- 🛰️ **Real-world integration** with live ATC & weather data APIs
- ⚛️ **Actual quantum hardware** execution via IBM Qiskit / Google Cirq
- 🗺️ **Real airspace data** from aviation databases (EUROCONTROL, FAA)
- 📈 **Scalability** — edge-level QUBO formulations for larger graphs
- 🤖 **ML-enhanced** wind prediction & demand forecasting
- 🌐 **Multi-aircraft fleet** optimisation & conflict resolution
- 📱 **Mobile-responsive** interface for pilots & dispatchers

---

## ⚠️ Disclaimer

> **This prototype is a research and simulation demonstrator.**
> It does **NOT** provide certified aviation navigation, air-traffic-control, flight planning, or operational safety advice.
> All data (waypoints, routes, emissions) is **synthetic** and for demonstration purposes only.
> Do **NOT** use for real flight planning, regulatory compliance, or carbon accounting.

---

## 👥 Team — INNOVATION TECHIES

| Role | Name | Contact |
|------|------|---------|
| **🎯 Team Lead** | **Bolisetti Veera Venkata Satyanarayana** | 📧 satyanarayanabolisetti76@gmail.com |
| **👨‍💻 Team Member** | **Chikatla Valli Vruksha Shirendra** | — |

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <sub>Built with ❤️ by <strong>INNOVATION TECHIES</strong> for the Hackathon</sub><br/>
  <strong>✈️ AeroQ — Optimising the route, not just the distance. ✈️</strong>
</p>
