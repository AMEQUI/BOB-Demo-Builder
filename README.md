## IBM Bob Demo Builder — Industrial IoT Predictive Maintenance Mock-Mode Demo

[IBM Bob](https://www.ibm.com/products/bob)[IBM watsonx.ai](https://www.ibm.com/products/watsonx-ai)[IBM Carbon Design System](https://carbondesignsystem.com/)  
An end-to-end, locally runnable demonstration generated with **IBM Pre-Sales Demo Builder**. It shows how a predictive-maintenance AI agent can monitor synthetic industrial IoT telemetry, identify likely equipment failures, explain its findings, and create a mock maintenance work order without requiring cloud credentials or access to client systems.

> **Demo environment:** Mock mode only. The application uses synthetic data, runs locally, and does not call a live watsonx.ai service or a production maintenance platform.

### 🎯 Demonstration Scenario

- **Industry:** Manufacturing and industrial operations.
- **Persona:** Plant reliability engineer or maintenance operations specialist.
- **Problem:** Unexpected failures in presses, CNC equipment, conveyors, or related assets can interrupt production and increase maintenance cost.
- **AI action:** The simulated agent analyzes deterministic sensor telemetry, identifies anomaly patterns, estimates failure risk, and recommends a maintenance response.
- **Wow moment:** The presenter selects a predefined equipment scenario, runs the analysis, reviews the failure explanation and confidence score, and creates a mock work order with recommended parts and technicians.
- **Outcome:** A complete, client-credible workflow can be demonstrated offline with zero external credentials and no client data.

### 🚀 Run the Demo

#### One-click startup

**Windows**

```powershell
.\START_DEMO.ps1
```

or double-click:

```text
START_DEMO.bat
```

**Linux or macOS**

```bash
chmod +x start_demo.sh
./start_demo.sh
```

When both services are ready, open:

- **Frontend:** http://localhost:5173
- **Backend API:** http://127.0.0.1:8000
- **FastAPI documentation:** http://127.0.0.1:8000/docs

Keep the backend and frontend terminal processes running while presenting the demo.

#### Manual startup

**Terminal 1: Backend**

```bash
python -m venv backend/venv
```

Windows PowerShell:

```powershell
.\backend\venv\Scripts\Activate.ps1
python -m pip install -r backend\requirements.txt
cd backend
uvicorn main:app --reload --port 8000
```

Linux or macOS:

```bash
source backend/venv/bin/activate
python -m pip install -r backend/requirements.txt
cd backend
uvicorn main:app --reload --port 8000
```

**Terminal 2: Frontend**

```bash
cd frontend
npm install
npm run dev -- --port 5173
```

### ✨ Demo Capabilities

- **Synthetic telemetry:** Deterministic factory-equipment sensor data for repeatable demonstrations.
- **Preset scenarios:** Preconfigured normal and failure conditions that avoid presenter typing during the live flow.
- **Agent reasoning:** A mock reasoning sequence that turns telemetry signals into an anomaly assessment, likely failure type, confidence score, and recommended action.
- **Maintenance workflow:** Mock work-order creation with suggested maintenance timing, parts, and technician information.
- **Results view:** Operational and business-impact indicators based on the selected scenario.
- **Architecture view:** A visual explanation of the mock-mode solution and the path to a live IBM watsonx deployment.
- **IBM user experience:** React interface based on IBM Carbon Design System v11 and IBM Plex typography.

### 🧭 Recommended Demo Flow

1. Open the **Dashboard** and explain that all displayed data is synthetic.
2. Review the operational problem and the monitored equipment population.
3. Select one of the preset scenarios in the **AI Agent / Solution** view.
4. Run the analysis and review the detected anomaly, failure type, confidence score, and recommendation.
5. Create the mock maintenance work order.
6. Open **Results** to explain the expected operational impact.
7. Finish with **Architecture** and describe how mock services could be replaced by live IBM and enterprise integrations during a pilot.

For the timed presenter narrative and preflight checklist, see [`DEMO_SCRIPT.md`](DEMO_SCRIPT.md).

### 🧱 Solution Stack

| Layer | Technology | Purpose in this demo |
|---|---|---|
| Frontend | React, Vite, `@carbon/react` v11 | Carbon-styled, accessible demonstration UI |
| Backend | Python, FastAPI, Uvicorn, Pydantic | Local API, scenario orchestration, and response models |
| AI simulation | Mock reasoning engine | Repeatable anomaly findings and recommendations with zero credentials |
| Data | Synthetic deterministic IoT telemetry | Safe and reproducible equipment scenarios |
| Live expansion path | IBM watsonx.ai, Granite models, enterprise maintenance integration | Target architecture for a future pilot, not invoked in mock mode |

### 📂 Repository Contents

```text
BOB-Demo-Builder/
│
├── .bob/                              # IBM Bob workspace rules, skills, and MCP configuration
├── backend/                           # FastAPI service and mock AI/data services
│   ├── main.py                        # Backend application entry point
│   ├── agent.py                       # Mock predictive-maintenance reasoning engine
│   ├── synthetic_data_service.py      # Deterministic synthetic IoT telemetry
│   ├── requirements.txt               # Python dependencies
│   └── tests/                         # Backend unit and integration tests
│
├── frontend/                          # React + Vite + Carbon user interface
│   ├── src/                           # Pages, components, styles, and API integration
│   ├── index.html                     # Frontend entry page
│   └── package.json                   # Node.js dependencies and scripts
│
├── scripts/
│   ├── check-compliance.sh            # Linux/macOS compliance validation
│   └── check-compliance.ps1           # Windows compliance validation
│
├── ARCHITECTURE.md                    # Solution architecture and integration boundaries
├── PILOT_PLAN.md                      # Path from mock demo to a working pilot
├── DEMO_SCRIPT.md                     # Preflight checklist and presenter walkthrough
├── START_DEMO.bat                     # Windows one-click launcher
├── START_DEMO.ps1                     # Windows PowerShell launcher
├── start_demo.sh                      # Linux/macOS launcher
├── .env.example                       # Placeholder environment variables only
├── .gitignore                         # Secrets, local state, build output, and tooling exclusions
└── README.md                          # Project overview and operating instructions
```

> The generated file set may vary slightly between IBM Bob runs. If a file has a different name, use the equivalent launcher or documentation artifact produced in this repository.

### 🧪 Compliance and Verification

Run the appropriate compliance script before presenting or committing changes.

**Windows**

```powershell
powershell.exe -ExecutionPolicy Bypass -File .\scripts\check-compliance.ps1
```

**Linux or macOS**

```bash
chmod +x scripts/check-compliance.sh
./scripts/check-compliance.sh
```

The verification should confirm:

- No PII or real client data is present.
- No API keys, passwords, tokens, or credentials are hardcoded.
- `.env.example` contains placeholders only.
- Mock mode works without external credentials.
- The visible demo banner identifies the application as a demonstration using synthetic data.
- IBM Carbon Design System v11 and IBM Plex typography are used for the UI.
- The required narrative assets are present: `README.md`, `ARCHITECTURE.md`, `PILOT_PLAN.md`, and `DEMO_SCRIPT.md`.
- The frontend, backend, preset scenarios, charts, loading states, and mock work-order path operate without blocking errors.

### 🔐 Security and Data Handling

- Never commit `.env`, personal access tokens, API keys, certificates, or local IBM Bob/MCP credentials.
- Use `.env.example` only to document variable names with non-secret placeholder values.
- Use synthetic data exclusively. Do not copy real client telemetry, names, identifiers, operational metrics, or system extracts into this repository.
- Treat all external integrations shown in the architecture as simulated unless a separate, approved pilot explicitly enables them.
- Review generated code and content before presenting it. IBM Bob output is non-deterministic and remains subject to human validation.

### 🛠️ Troubleshooting

#### `http://localhost:5173` refuses to connect

Verify Node.js and npm, reinstall the frontend dependencies, and restart Vite:

```powershell
node -v
npm.cmd -v
cd frontend
npm.cmd install
npm.cmd run dev -- --port 5173
```

#### Backend does not start

From the repository root:

```powershell
python -m pip install -r backend\requirements.txt
cd backend
python -m uvicorn main:app --reload --port 8000
```

#### Port already in use

Stop the process holding port `5173` or `8000`, or start the affected service on another port. If the frontend port changes, use the URL printed by Vite in the terminal.

#### IBM Bob workflow pauses or times out

Resume the existing Agentic Sidebar session with:

```text
continue
```

For build or runtime errors, paste the complete terminal output into IBM Bob. For visual defects, attach a screenshot and describe the expected result.

### 📚 Supporting Documents

- [`ARCHITECTURE.md`](ARCHITECTURE.md): Components, data flow, mock boundaries, and live expansion path.
- [`PILOT_PLAN.md`](PILOT_PLAN.md): Proposed transition from the local mock demo to an instrumented pilot.
- [`DEMO_SCRIPT.md`](DEMO_SCRIPT.md): Presenter preflight checks, timed walkthrough, and closing narrative.

### ⚠️ Disclaimer

This repository is a **demonstration asset**, not a production predictive-maintenance system. All equipment, telemetry, findings, maintenance recommendations, users, organizations, and business outcomes are synthetic or illustrative. AI-generated recommendations must not be used to operate equipment or authorize maintenance without review by qualified personnel and the applicable operational controls.
