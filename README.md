# Quantum-Key-Distribution-for-Critical-Infrastructure
# Q-SHIELD: Quantum Key Distribution for Critical Infrastructure

**Team Name:** Algorithmic Edge  
**Project Title:** Q-SHIELD – Quantum Key Distribution for Critical Infrastructure

## 1. Project Overview

Q-SHIELD is a simulation-based project that demonstrates the principles of Quantum Key Distribution (QKD) for secure communication in critical infrastructure.

Critical infrastructure includes power grids, banking systems, government networks, emergency communication systems, and data centres. These systems require secure communication to protect sensitive information from unauthorized access.

Quantum Key Distribution provides a way for two authorized parties to establish shared secret key material using quantum states. Certain eavesdropping attempts can introduce disturbances that can be detected by analysing measurement results.

Our project focuses on the BB84 protocol and demonstrates its workflow through an interactive interface.

## 2. Problem Statement

Traditional communication security relies on cryptographic methods that may face future challenges from advances in quantum computing.

Critical infrastructure requires secure communication mechanisms that can help identify possible interception attempts and support the establishment of secure encryption keys.

Q-SHIELD addresses this problem by demonstrating Quantum Key Distribution and evaluating communication disturbances using the Quantum Bit Error Rate (QBER).

## 3. Proposed Solution

Our proposed solution is an interactive quantum security platform based on the BB84 protocol.

The system represents three main participants:

- **Alice:** The sender who prepares quantum states.
- **Bob:** The receiver who measures the received states.
- **Eve:** A potential eavesdropper who attempts to intercept communication.

The proposed workflow is:

1. Alice generates random bits and selects random bases to prepare quantum states.
2. Bob independently selects measurement bases and measures the received states.
3. Alice and Bob compare their basis choices through an authenticated classical channel.
4. Positions where the bases do not match are discarded.
5. The remaining matching positions form the sifted key.
6. The system estimates QBER using a sample of the sifted key.
7. The observed error rate is evaluated against the configured security criteria.
8. An intercept-resend attack can be simulated to demonstrate how an attack may introduce errors.

The goal is to make quantum communication and its security principles easier to understand through visual demonstrations.

## 4. Technology Stack

| Technology | Purpose |
|---|---|
| React | Building the frontend interface |
| TypeScript | Adding static typing to frontend code |
| Vite | Frontend development and build tooling |
| Tailwind CSS | Styling the user interface |
| Python | Backend programming |
| FastAPI | Creating backend API endpoints |
| Qiskit | Representing quantum circuits and operations |
| Qiskit Aer | Simulating quantum circuits on a classical computer |
| Axios | Sending HTTP requests between frontend and backend, if used |
| Recharts | Displaying charts and metrics, if used |
| Lucide React | Providing interface icons, if used |
| Uvicorn | Running the FastAPI application |

*Note: This is the target technology stack. Keep only the technologies actually used in your current implementation.*

## 5. System Architecture

The proposed architecture consists of three main layers.

### Frontend Layer

The frontend provides the dashboard, user interface, communication visualizations, and security information. It displays results received from the backend.

### Backend Layer

The backend uses Python and FastAPI to handle requests, execute application logic, and communicate with the quantum simulation module.

### Quantum Simulation Layer

Qiskit and Qiskit Aer are used to model quantum circuits, measurements, and protocol behaviour.

### Architecture Workflow

User → React Frontend → FastAPI Backend → Qiskit Simulation → Simulation Results → Frontend Dashboard

The frontend should display validated simulation results rather than generating misleading security values independently.

## 6. BB84 Protocol

BB84 is a foundational Quantum Key Distribution protocol introduced by Charles Bennett and Gilles Brassard in 1984.

It uses two different bases to encode quantum information.

- **Rectilinear basis (+):** Horizontal and vertical polarization states.
- **Diagonal basis (×):** Two diagonal polarization states.

Alice prepares quantum states using randomly selected bits and bases. Bob measures them using randomly selected bases.

When Alice and Bob use matching bases, their results ideally agree under ideal conditions. When they use different bases, Bob's measurement result is random under the ideal BB84 model.

After basis reconciliation, matching positions are retained to form the sifted key.

## 7. Quantum Bit Error Rate (QBER)

QBER is used to estimate the proportion of errors in a tested sample.

Formula:

QBER (%) = (Number of errors in the tested sample / Total number of compared sample bits) × 100

For example, if 5 errors are observed among 100 compared sample bits:

QBER = (5 / 100) × 100 = 5%

This is an illustrative calculation, not a measured result from the project.

A high QBER may indicate channel noise, an eavesdropping attempt, or an implementation issue. QBER alone does not prove the presence of an attacker.

## 8. Eavesdropping Demonstration

In an intercept-resend attack, Eve intercepts quantum states, measures them, and sends replacement states to Bob.

If Eve selects a different basis from Alice, her measurement can disturb the state and introduce errors.

Q-SHIELD aims to compare the protocol's behaviour under normal, noisy, and attack conditions.

If the observed error rate fails the configured security checks, the candidate key should be rejected rather than treated as secure.

## 9. Q-SHIELD Features

The project is designed to include the following components:

- Interactive security dashboard.
- BB84 protocol workflow.
- Alice and Bob communication model.
- Eve intercept-resend attack demonstration.
- QBER calculation and display.
- Ideal and noisy channel comparisons.
- Security status and decision display.
- Quantum circuit visualizations.
- Simulation results and session history, where implemented.

Feature availability depends on the current implementation and testing status.

## 10. Running the Backend

If the repository contains a `backend` directory and the FastAPI application is available as `app.main:app`, use the following commands.

### Step 1: Navigate to the backend

```bash
cd backend
```

### Step 2: Create a virtual environment

```bash
python -m venv .venv
```

### Step 3: Activate the environment

For Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

For Windows Command Prompt:

```bat
.venv\Scripts\activate.bat
```

For macOS or Linux:

```bash
source .venv/bin/activate
```

### Step 4: Install dependencies

If the project includes a `requirements.txt` file:

```bash
pip install -r requirements.txt
```

### Step 5: Start the backend

```bash
python -m uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
```

If FastAPI documentation is enabled, open:

http://127.0.0.1:8000/docs

These instructions assume the stated project structure. Adjust the paths if your actual repository differs.

## 11. Evaluation Plan

The prototype can be evaluated using:

- QBER under ideal, noisy, and intercept-resend conditions.
- Correctness of basis reconciliation and key sifting.
- Consistency across repeated simulation runs.
- Correct communication between frontend and backend.
- Correct display of simulation results.
- Whether the security decision follows the configured protocol checks.

Numerical performance results should be reported only after running and validating the simulation.

## 12. Limitations

- The project is simulation-based and does not represent a physical quantum communication network.
- QBER alone cannot prove that an eavesdropper is present.
- QKD establishes key material; it does not automatically encrypt application messages.
- Practical deployment requires suitable message encryption, authentication, key management, and security validation.
- Real-world QKD systems can have hardware vulnerabilities that are not captured by a basic simulation.

## 13. Future Enhancements

- Complete and validate end-to-end BB84 simulation.
- Integrate frontend and backend components.
- Add configurable channel noise and intercept-resend experiments.
- Improve quantum circuit and measurement visualizations.
- Add session history and evaluation reports.
- Explore suitable error correction and privacy amplification.
- Investigate physical quantum hardware if available and within project scope.

## 14. Project Links

**Live Demo:**  
https://hysterical-quantum-shield-labs.base44.app/

**Google Drive Project Folder:**  
https://drive.google.com/drive/folders/1nGoiUYtc2F9bERQR7PhqexbQweUjK0N6?usp=drive_link

## 15. Team Information

**Team Name:** Algorithmic Edge

**Project:** Q-SHIELD – Quantum Key Distribution for Critical Infrastructure

## 16. Reference

IBM Quantum Learning – Quantum Key Distribution:  
https://qiskit.qotlabs.org/learning/modules/computer-science/quantum-key-distribution

**Disclaimer:** Q-SHIELD is an educational project prototype. It should not be used to protect real critical-infrastructure communications without a complete, independently reviewed implementation and security assessment.
