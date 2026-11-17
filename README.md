<div align="center">

<img src="assets/ephysics_logo.png" alt="E-Physics Logo" width="260" />

# Physics Simulation Workshop — Edition #01
### **E-Physics (`E-ΦSICS`) • EMINES – Mohammed VI Polytechnic University (UM6P)**

*“From equations to reality — the physics journey begins here ⚛️”*

[![Workshop Setup & Downloads](https://img.shields.io/badge/Workshop_Portal-txt.ma%2Fworkshop1-2563eb?style=for-the-badge&logo=rocket&logoColor=white)](https://txt.ma/workshop1/)
[![YouTube Channel](https://img.shields.io/badge/YouTube-@EminesEPHYSICS-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@EminesEPHYSICS)
[![Instagram](https://img.shields.io/badge/Instagram-@emines.physics-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/emines.physics/)
[![Python 3.13+](https://img.shields.io/badge/Python-3.13+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)

</div>

---

## ⚛️ About E-Physics (`E-ΦSICS`)

**E-Physics** is the first student-led physics club at **Mohammed VI Polytechnic University (UM6P)**, founded in **2025** at **EMINES – School of Industrial Management** in Ben Guerir, Morocco.

Our mission is to make physics something we don't just study on paper, but **experiment with, question, simulate, and share**. Created by students and open to everyone curious about science, E-Physics bridges theoretical foundations with hands-on experimentation and computation:

- 🔬 **Hands-On Laboratory Sessions (*Lab Days*)** — Discovering experimental equipment, building setups, and testing physical laws in the lab.
- 💻 **Scientific & Technical Workshops** — Interactive computational physics sessions where equations come alive through code and real-time visualization.
- 🎙️ **Research Talks & Conferences** — Hosting researchers and guest speakers (such as ultrafast/femtosecond quantum physics conferences at EMINES) to explore frontier science.
- 🌌 **Collaborative Outreach & Science Media** — Partnering across clubs (including joint astronomy/astrophysics initiatives with **E-ASTRO**) and sharing short-form experiments, recaps, and explainers on [YouTube](https://www.youtube.com/@EminesEPHYSICS) and [Instagram](https://www.instagram.com/emines.physics/).

---

## 🎯 About This Workshop

Welcome to the official repository for **E-Physics Workshop #01: Interactive Physics Simulations**.

In classical coursework, physical systems are often restricted to idealized cases that admit closed-form analytical solutions. In real science and engineering, most systems—from multi-body gravitational orbits to arbitrary wave excitations—must be solved **numerically**.

This workshop introduces a universal **4-step computational physics recipe** and applies it across three progressively richer physical systems:

```
┌────────────────────────────────────────────────────────────────────────────┐
│                     THE E-PHYSICS SIMULATION RECIPE                        │
├──────────────────┬──────────────────┬───────────────────┬──────────────────┤
│ 1. SYSTEM &      │ 2. PHYSICAL      │ 3. NUMERICAL      │ 4. REAL-TIME     │
│    STATE (S)     │    MODEL         │    DISCRETIZATION │    VISUALIZATION │
│                  │                  │                   │                  │
│ Identify degrees │ Express ODEs /   │ Step forward in   │ Render motion in │
│ of freedom,      │ PDEs, initial    │ time (dt) & space │ Pygame /         │
│ coordinates, &   │ states, and      │ (dx): Euler,      │ Matplotlib &     │
│ parameters.      │ boundary rules.  │ Verlet, FDTD.     │ synthesize audio.│
└──────────────────┴──────────────────┴───────────────────┴──────────────────┘
```

---

## 📂 Repository Structure

The repository is organized into two parallel tracks so participants can code along live during the workshop and compare their work against reference implementations afterward:

```text
PhysicsSimulationWorkshop/
├── assets/
│   └── ephysics_logo.png                  # Official E-Physics (E-ΦSICS) club logo
├── notebooks/                             # 🛠️ Participant Exercise Notebooks (with `...` placeholders)
│   ├── 1. Bouncing ball.ipynb             # Sim 01: 2D kinematics, gravity & wall collisions
│   ├── 2. N Body.ipynb                    # Sim 02: Newtonian N-body gravity & symplectic integration
│   └── 3. Wave on a chord.ipynb           # Sim 03: 1D wave equation PDE, animations & sound synthesis
└── notebooks solutions/                   # ✅ Complete Reference Solutions (ready to run)
    ├── 1. Bouncing ball.ipynb             # Sim 01: Full solution
    ├── 2. N Body.ipynb                    # Sim 02: Full solution
    └── 3. Wave on a chord.ipynb           # Sim 03: Full solution
```

> [!NOTE]
> **Self-Contained Participant Bundles (`txt.ma/workshop1`)**
> During the live workshop, participants download a pre-packaged, zero-setup archive for their operating system from **[https://txt.ma/workshop1/](https://txt.ma/workshop1/)**. In addition to these notebooks, that archive bundles an automated `uv` environment installer (`setup.bat` / `setup.sh`), `pyproject.toml`, and the `workshop_utils/` helper package (demo videos, logos, Matplotlib window-backend selector `find_backend.py`, and WAV audio synthesizer `export_sound.py`).

---

## 📓 Deep Dive: How the Notebooks Work

Each notebook is structured as an interactive tutorial combining physical derivations, numerical analysis, and live graphical/audio output.

| # | Notebook | Physical Domain | Governing Equations | Numerical Method | Visualization & Output |
| :-: | :--- | :--- | :--- | :--- | :--- |
| **01** | **`1. Bouncing ball.ipynb`** | 2D Kinematics & Inelastic Collisions | $\dfrac{d\vec{r}}{dt} = \vec{v}, \quad \dfrac{d\vec{v}}{dt} = \vec{a}$ | **Semi-Implicit (Symplectic) Euler** | Real-time 60 FPS `pygame` window |
| **02** | **`2. N Body.ipynb`** | Celestial Mechanics & Gravitation | $\vec{a}_i = \sum_{j \neq i} G m_j \dfrac{\vec{r}_j - \vec{r}_i}{\|\vec{r}_j - \vec{r}_i\|^3}$ | **Explicit Euler** vs. **Velocity-Verlet** | Real-time `pygame` orbital trails + `matplotlib` energy drift plot |
| **03** | **`3. Wave on a chord.ipynb`** | Continuum Mechanics & Acoustics | $\dfrac{\partial^2 u}{\partial t^2} = c^2 \dfrac{\partial^2 u}{\partial x^2}$ | **Finite-Difference Time-Domain (FDTD)** | `matplotlib.animation` real-time wave + `.wav` audio synthesis |

---

### 1️⃣ Notebook 1: Simulating a Bouncing Ball (`1. Bouncing ball.ipynb`)

A gentle, concrete introduction to time-stepping simulations using a ball of radius $R = 40\text{ px}$ moving inside a $1000 \times 600\text{ px}$ enclosure at $60\text{ FPS}$ ($\Delta t = 1/60\text{ s}$).

#### Physics & State Representation
- **State Vector:** $\mathcal{S} = (x, y, v_x, v_y)$, where positions are measured in pixels and time in seconds (with screen coordinate $+y$ pointing downward).
- **Two Dynamical Regimes:**
  1. **Constant Velocity (`gravity=False`):** $\vec{a} = (0, 0)$ — the ball travels in straight lines between wall reflections.
  2. **Uniform Gravity (`gravity=True`):** $a_x = 0,\; a_y = g = 980.0\text{ px/s}^2$.
- **Boundary Constraints & Energy Dissipation:**
  - The center of the ball is constrained to $x \in [R, W - R]$ and $y \in [R, H - R]$.
  - Whenever the ball crosses a wall, its position is clamped to the boundary and the normal velocity component is reversed and multiplied by the **coefficient of restitution** $e = 0.9$:
    $$v_x \leftarrow -\text{restitution} \cdot v_x \quad (\text{left/right walls}), \qquad v_y \leftarrow -\text{restitution} \cdot v_y \quad (\text{top/bottom walls})$$

#### How the Numerical Integration Works
Because acceleration is the second derivative of position, advancing one timestep requires two first-order updates. The notebook uses **Semi-Implicit Euler** (updating velocity *before* position):

$$\vec{v}_{n+1} = \vec{v}_n + \vec{a}_n \,\Delta t, \qquad \vec{r}_{n+1} = \vec{r}_n + \vec{v}_{n+1} \,\Delta t$$

Using the newly updated velocity $\vec{v}_{n+1}$ to advance position $\vec{r}_{n+1}$ is symplectic and prevents the artificial energy gain that plagues standard explicit Euler in oscillatory/bouncing systems.

#### What You Implement in `notebooks/1. Bouncing ball.ipynb`
1. Define the valid coordinate bounds `x_min`, `x_max`, `y_min`, and `y_max` accounting for the ball's `radius`.
2. Complete `advance(x, y, vx, vy, gravity)` for both `gravity=False` and `gravity=True`, including wall-collision velocity reversals.
3. Run `run_demo(gravity=False)` and `run_demo(gravity=True)` to compare both regimes in separate Pygame windows.

---

### 2️⃣ Notebook 2: Simulating the N-Body Problem (`2. N Body.ipynb`)

Moves from a single particle in an external field to an interacting **many-body gravitational system** ($N = 3$ bodies by default), demonstrating why higher-order symplectic integrators are essential in computational astrophysics.

#### Physics & State Representation
- **State Vector:** $\mathcal{S} = \{ (\vec{r}_i, \vec{v}_i) \mid i \in [\![0, N-1]\!] \}$, stored as NumPy arrays `positions` and `velocities` of shape `(N, 2)` with masses `masses` of shape `(N,)`.
- **Gravitational Acceleration:** Each body $i$ experiences the vector sum of Newtonian gravitational pulls from all other bodies $j \neq i$:
  $$\vec{a}_i = \sum_{j \neq i} G m_j \frac{\vec{r}_j - \vec{r}_i}{\|\vec{r}_j - \vec{r}_i\|^3}$$
- **Total Mechanical Energy & Conservation Diagnostic:**
  Because gravity is a conservative central force, total mechanical energy $E = K + U$ should remain constant:
  $$E = \sum_{i=0}^{N-1} \frac{1}{2} m_i v_i^2 - \sum_{i=0}^{N-1} \sum_{j \neq i} \frac{1}{2} G \frac{m_i m_j}{\|\vec{r}_j - \vec{r}_i\|}$$
  The simulation tracks the **relative energy drift** at every frame:
  $$\delta E(t) = \frac{E(t) - E(0)}{|E(0)|}$$

#### Built-in 3-Body Periodic Choreographies
The notebook includes three famous periodic solutions to the 3-body problem that you can switch between by uncommenting:
1. **Figure-Eight Orbit (Chenciner & Montgomery, 2000):** Three equal masses chase one another along a single figure-eight curve with zero total angular momentum.
2. **Lagrange Equilateral Triangle:** Three equal masses rotating in a rigid equilateral triangle configuration at speed $v = \sqrt{G m / (\sqrt{3} R)}$.
3. **Broucke A7 Periodic Orbit:** An intricate periodic 3-body choreography discovered by Roger Broucke.
4. **Custom Initial Conditions:** Design your own multi-body system!

#### Numerical Integrators: Explicit Euler vs. Velocity-Verlet
Participants implement and compare two time-integration algorithms side by side:
- **Explicit Euler (`euler_step`):**
  $$\vec{r}_{n+1} = \vec{r}_n + \vec{v}_n \,\Delta t, \qquad \vec{v}_{n+1} = \vec{v}_n + \vec{a}(\vec{r}_n) \,\Delta t$$
  First-order accurate ($\mathcal{O}(\Delta t)$); injects numerical energy at every step, causing periodic 3-body orbits to rapidly destabilize and fly apart.
- **Velocity-Verlet (`verlet_step`):**
  $$\vec{r}_{n+1} = \vec{r}_n + \vec{v}_n \,\Delta t + \frac{1}{2}\vec{a}_n \,\Delta t^2, \qquad \vec{a}_{n+1} = \vec{a}(\vec{r}_{n+1}), \qquad \vec{v}_{n+1} = \vec{v}_n + \frac{1}{2}(\vec{a}_n + \vec{a}_{n+1})\,\Delta t$$
  Second-order accurate ($\mathcal{O}(\Delta t^2)$) and **symplectic**; requires one extra force evaluation per step but keeps relative energy drift $\delta E(t)$ bounded and minuscule over long runs.

#### Coordinate Mapping, Substepping & Visualization
- **World-to-Screen Transform (`world_to_screen`):** Maps continuous physical coordinates $(x, y)$ in a viewport of width $L = \text{WORLD\_WIDTH}$ to pixel coordinates $(x_{\text{screen}}, y_{\text{screen}})$ centered in the $W \times H$ Pygame window with an inverted vertical axis:
  $$s = \frac{\min(W, H)}{L}, \qquad x_{\text{screen}} = \frac{W}{2} + s x, \qquad y_{\text{screen}} = \frac{H}{2} - s y$$
- **Physics Substeps:** Runs `substeps_per_frame = max(1, round(1 / (fps * timescale * dt)))` integration steps per rendered frame (`dt = 0.001`, `fps = 30`), recording the last `TRAIL_LENGTH = 500` positions in a `collections.deque` to draw smooth orbital trails and live HUD telemetry (`method | t | Relative drift`).
- **Post-Run Analysis:** Plots $\delta E(t) = (E - E_0)/|E_0|$ vs. simulation time in a separate Matplotlib window.

---

### 3️⃣ Notebook 3: Simulating Waves on a Chord (`3. Wave on a chord.ipynb`)

Extends the simulation recipe from ordinary differential equations (ODEs) for discrete particles to a **partial differential equation (PDE)** governing a continuous medium: transverse waves on a taut musical string of length $L$ with fixed endpoints.

#### Physics & Continuous State Representation
- **Physical Parameters:**
  - String length $L = 1.0\text{ m}$, tension $T = 120.0\text{ N}$, linear mass density $\mu = 0.005\text{ kg/m}$.
  - **Wave propagation speed:** $c = \sqrt{T / \mu} \approx 154.92\text{ m/s}$.
  - **Fundamental frequency:** $f_1 = \dfrac{c}{2L} \approx 77.46\text{ Hz}$ (close to musical note $\text{D\#}_2$).
- **Governing 1D Wave Equation & Boundary Conditions:**
  $$\frac{\partial^2 u}{\partial t^2} = c^2 \frac{\partial^2 u}{\partial x^2}, \qquad \forall t > 0:\; u(0, t) = u(L, t) = 0 \quad (\text{fixed ends})$$
- **Functional Initial State:** At $t = 0$, the state of the chord is defined by two spatial functions over $[0, L]$:
  - Initial displacement profile: $u(x, 0) = f(x)$
  - Initial transverse velocity profile: $\dfrac{\partial u}{\partial t}(x, 0) = g(x)$

#### Four Built-in Wave Excitations
1. **Traveling Pulse (`One wave`):** A localized $\sin^2$ wave packet centered at `initial_pos = 0.5` paired with an analytical initial velocity $g(x)$ so the pulse travels cleanly in one direction.
2. **Plucked String (`Pluck` — Default):** Piecewise-linear triangular displacement peaked at $x = \text{peak} = 0.2\text{ m}$ released from rest ($g(x) = 0$), modeling an acoustic guitar pluck.
3. **Hammer Strike (`Hammer`):** Flat initial string ($f(x) = 0$) struck at $x = 0.5\text{ m}$ over width $0.05\text{ m}$ with initial speed $g(x) = 50\text{ m/s}$, modeling a piano hammer strike.
4. **Standing Wave (`Standing`):** Pure harmonic mode $f(x) = A \sin((n_{\text{knots}} - 1)\pi x / L)$ with $g(x) = 0$.

#### Space–Time Grid Discretization & FDTD Scheme
- **Grid Geometry:** Discretizes $x \in [0, L]$ into $N_x = 1000$ points ($\Delta x = L / (N_x - 1)$) and $t \in [0, \text{duration}]$ into $N_t = 20{,}000$ points ($\Delta t = \text{duration} / (N_t - 1)$), storing $u[i, j] \approx u(i\,\Delta x, j\,\Delta t)$ in a $1000 \times 20{,}000$ `float64` array (~160 MB).
- **Courant–Friedrichs–Lewy (CFL) Stability Number:**
  $$K = \left(\frac{c\,\Delta t}{\Delta x}\right)^2, \qquad \sqrt{K} \approx 0.77 < 1$$
  Keeping the Courant number $\sqrt{K} \le 1$ guarantees that the numerical domain of dependence contains the physical wave cone.
- **Second-Order Central Difference Evolution (`advance_simulation`):**
  - **First step ($j = 0 \to 1$)** via second-order Taylor series incorporating $g(x)$:
    $$u_i^1 = u_i^0 + g(x_i)\,\Delta t + \frac{K}{2}\left(u_{i+1}^0 + u_{i-1}^0 - 2u_i^0\right)$$
  - **Subsequent steps ($j \ge 1 \to j + 1$)** via the explicit leapfrog stencil:
    $$u_i^{j+1} = 2u_i^j - u_i^{j-1} + K\left(u_{i+1}^j + u_{i-1}^j - 2u_i^j\right)$$
  - Implemented without Python `for`-loops over space using fast **NumPy array slicing** (`u[1:-1, j+1]`, `u[2:, j]`, `u[:-2, j]`).

#### Real-Time Slow-Motion Animation & Acoustic WAV Synthesis
- **Slow-Motion Animation (`FuncAnimation`):** Because a $155\text{ m/s}$ wave crosses a $1\text{ m}$ string in milliseconds, the Matplotlib animation slows time down by `time_scale = 250x` at $30\text{ FPS}$, advancing `advance_per_frame = 1 / (time_scale * fps * dt)` timesteps per visual frame.
- **Hear Your Simulation (`export_sound.generate_sound`):** The final section runs a $3\text{ s}$ simulation ($N_t = 1{,}000{,}000$ steps), records the displacement waveform $u(x_{\text{pickup}}, t)$ at a virtual pickup (`pickup_location = 0.15`), applies exponential damping, exports `wave_output.wav`, and embeds an interactive `IPython.display.Audio` player so you can listen to the timbre of your simulated string!

---

## 🚀 Installation & Setup Guide

### Option A: Official Zero-Setup Workshop Bundle (Recommended for Participants)

If you are attending the workshop (or want a completely self-contained environment with all helper utilities, demo videos, and an isolated Python runtime without installing Python or Git manually), use our official setup portal:

👉 **[Physics Simulation Workshop — Installation & Setup Guide (`https://txt.ma/workshop1/`)](https://txt.ma/workshop1/)**

1. **Download & Extract:** Download the archive matching your OS from [`txt.ma/workshop1`](https://txt.ma/workshop1/):
   - **Windows 64-bit (`x86_64`):** `Physics-Workshop-Windows-x64.zip` (~16.0 MB)
   - **macOS Apple Silicon (`ARM64 • M1–M4`):** `Physics-Workshop-macOS-arm64.zip` (~15.1 MB)
   - **macOS Intel (`x86_64`):** `Physics-Workshop-macOS-x64.zip` (~18.6 MB)
   - **Linux 64-bit (`x86_64`):** `Physics-Workshop-Linux-x64.zip` (~17.8 MB)
   > ⚠️ **Important:** Extract the `.zip` archive completely into a normal folder before running anything. Do **not** open files from inside the compressed ZIP preview.
2. **Run the Automated Setup Script:**
   - **Windows:** Double-click `setup.bat` (if Windows SmartScreen prompts, click *More info → Run anyway*).
   - **macOS / Linux:** Open a terminal in the extracted folder and run:
     ```bash
     bash setup.sh
     ```
   *(This uses a bundled `uv` binary to provision an isolated Python `3.13.5` virtual environment in `.venv/` with `numpy`, `matplotlib`, `pygame-ce`, and `jupyter`.)*
3. **Open in VS Code:**
   - Launch [Visual Studio Code](https://code.visualstudio.com/) with the **Python** and **Jupyter** extensions installed.
   - Go to **File → Open Folder…** (`Ctrl+K Ctrl+O` / `Cmd+O`) and open the extracted workshop folder.
4. **Select the `.venv` Interpreter / Kernel:**
   - Open the Command Palette (`Ctrl+Shift+P` / `Cmd+Shift+P`) → **Python: Select Interpreter** → select the `.venv` interpreter labeled **Workspace** (`.\.venv\Scripts\python.exe` or `./.venv/bin/python`).
   - Open any notebook in `notebooks/` (or `notebooks solutions/`), ensure `.venv` is selected as the kernel in the top-right corner, and run cells with `Shift+Enter`!

---

### Option B: Running Directly from This Git Repository

If you clone this repository directly with `git`:

```bash
git clone https://github.com/E-Physics/PhysicsSimulationWorkshop.git
cd PhysicsSimulationWorkshop
```

1. **Create a Virtual Environment & Install Dependencies:**
   Using [`uv`](https://docs.astral.sh/uv/) (fastest):
   ```bash
   uv venv --python 3.13
   uv pip install numpy matplotlib pygame-ce jupyter ipykernel numba
   ```
   Or using standard `venv` + `pip`:
   ```bash
   python -m venv .venv
   # Windows (PowerShell):
   .\.venv\Scripts\Activate.ps1
   # macOS / Linux:
   source .venv/bin/activate

   pip install numpy matplotlib pygame-ce jupyter ipykernel numba
   ```

2. **Note on `workshop_utils` When Cloning from GitHub:**
   - **Notebook 1 (`1. Bouncing ball.ipynb`)** only requires `pygame` and runs out of the box.
   - **Notebooks 2 & 3 (`2. N Body.ipynb` and `3. Wave on a chord.ipynb`)** import `workshop_utils` (`find_backend` to select a desktop GUI backend like `TkAgg` for Matplotlib, and `export_sound` for `.wav` synthesis in Notebook 3). If you cloned this Git repo without the `workshop_utils/` folder from the [`txt.ma/workshop1`](https://txt.ma/workshop1/) bundle, either copy `workshop_utils/` from the workshop ZIP into the repository root, or replace `find_backend.use_window_backend(matplotlib)` with `matplotlib.use("TkAgg")`.

---

## 🛠️ Troubleshooting FAQ

| Issue | Cause | Solution |
| :--- | :--- | :--- |
| **`uv` permission denied / Gatekeeper block on macOS** | macOS quarantines downloaded binaries or ZIP wasn't extracted. | Extract the ZIP fully, then run `xattr -dr com.apple.quarantine .` inside the folder and re-run `bash setup.sh`. |
| **`ModuleNotFoundError: No module named 'pygame'` (or `matplotlib`)** | VS Code is using your global system Python instead of `.venv`. | Press `Ctrl+Shift+P` → `Python: Select Interpreter` (or click the top-right notebook kernel picker) and choose the `.venv` **Workspace** environment. |
| **Next notebook cell stays stuck (`[*]`) after running simulation** | `pygame` and `matplotlib` open interactive desktop windows that block the kernel until closed. | Check your taskbar/dock for the open simulation window (`E-Physics Workshop — ...` or `Figure 1`) and close it before running the next cell. |
| **Pygame / Matplotlib window does not appear** | Running inside a browser editor (`vscode.dev` / `github.dev`) or headless SSH session. | Run the notebooks in the **desktop Visual Studio Code** app on a machine with a graphical display. |

---

## 🌐 Connect with E-Physics

Stay updated on our upcoming workshops, *Lab Days*, conferences, and student research projects:

- 🌍 **Workshop #01 Setup & Downloads Portal:** [https://txt.ma/workshop1/](https://txt.ma/workshop1/)
- ▶️ **YouTube Channel:** [Emines E-PHYSICS (`@EminesEPHYSICS`)](https://www.youtube.com/@EminesEPHYSICS)
- 📸 **Instagram:** [@emines.physics](https://www.instagram.com/emines.physics/)
- 🏛️ **Institution:** EMINES – School of Industrial Management, Mohammed VI Polytechnic University (UM6P), Ben Guerir, Morocco

<div align="center">
  <br />
  <sub><b>© E-Physics Club (`E-ΦSICS`) • EMINES – UM6P • Physics Simulation Workshop</b></sub>
</div>
