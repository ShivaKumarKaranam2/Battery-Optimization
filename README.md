# AI Battery Optimization System

A comprehensive AI-powered battery optimization platform for electric vehicles, consisting of a Java backend with machine learning services and a React TypeScript frontend for visualization and user interaction.

## Project Structure

```
AI_BATTERY_OPTIMIZATION/
├── backend/            # Java Spring Boot backend with ML models
│   ├── src/main/java/com/ev/AI_battery/service/
│   │   ├── BatteryTelemetryService.java
│   │   ├── BatteryMlService.java
│   │   ├── RULCalculator.java
│   │   ├── SoHCalculator.java
│   │   ├── TelemetryNormalizationService.java
│   │   ├── TelemetryValidator.java
│   │   ├── TelemetryCsvParser.java
│   │   └── VehicleDocumentParser.java
│   ├── src/main/java/com/ev/AI_battery/service/
│   │   ├── VehicleService.java
│   │   ├── AuthService.java
│   │   ├── OpenChargeMapService.java
│   │   └── StationRecommendationService.java
│   ├── pom.xml
│   ├── mvnw
│   ├── requirements.txt
│   ├── shap_explainer.py
│   ├── xgboost_predictor.py
│   ├── README_XGBOOST.md
│   ├── .mvn/
│   ├── .gitignore
│   └── .gitattributes
│
└── frontend/           # React + TypeScript frontend
    ├── src/components/
    │   ├── vehicle/
    │   │   ├── VehicleCard.tsx
    │   │   ├── VehicleForm.tsx
    │   │   └── VehicleDocumentUpload.tsx
    │   ├── stations/
    │   │   ├── StationCard.tsx
    │   │   ├── StationList.tsx
    │   │   └── StationDetailModal.tsx
    │   ├── BatteryExplanation.tsx
    │   ├── BatteryExplanationDashboard.tsx
    │   ├── ExplanationHistory.tsx
    │   ├── LogChargingSessionModal.tsx
    │   ├── PrivateRoute.tsx
    │   └── Navbar.tsx
    ├── src/pages/
    │   ├── LandingPage.tsx
    │   ├── Dashboard.tsx
    │   ├── BatteryHealthPage.tsx
    │   ├── ChargingOptimizationPage.tsx
    │   ├── ChargingHistoryPage.tsx
    │   ├── VehicleSetupPage.tsx
    │   ├── StationListPage.tsx
    │   └── AiCoachingPage.tsx
    ├── src/services/
    │   ├── api.ts
    │   ├── vehicleService.ts
    │   ├── batteryExplanationService.ts
    │   ├── chargingSessionService.ts
    │   ├── stationService.ts
    │   └── telemetryService.ts
    ├── src/hooks/
    │   ├── useStations.ts
    │   └── useGeolocation.ts
    ├── src/types/
    │   ├── chargingSession.ts
    │   ├── vehicle.ts
    │   └── station.ts
    ├── src/index.css
    ├── App.tsx
    ├── main.tsx
    ├── vite.config.ts
    ├── package.json
    ├── tsconfig.json
    ├── tsconfig.app.json
    ├── tsconfig.node.json
    ├── eslint.config.js
    ├── .gitignore
    └── index.html
```

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                    AI BATTERY OPTIMIZATION                     │
├─────────────────────┬──────────────────────────────────────┤
│                     BACKEND (Java)                              │
│  ┌─────────────────────┐  REST API  ┌─────────────────────┐  │
│  │  ML & Prediction    │  ──────────▶│  Frontend (React)   │  │
│  │  - XGBoost RUL      │            │  - Battery Dashboard│  │
│  │  - SoH Calculation  │            │  - Charging Optmzn  │  │
│  │  - Telemetry NV     │            │  - Vehicle Mgmt     │  │
│  └─────────────────────┘            └─────────────────────┘  │
│           │                                      │              │
│  ┌─────────────────────┐                │              │
│  │  Data Processing    │                │              │
│  │  - CSV Parsing      │                │              │
│  │  - Normalization    │                │              │
│  │  - Validation       │                │              │
│  └─────────────────────┘                │              │
│                                        ▼              │
│  ┌─────────────────────┐                ┌──────────────┐ │
│  │  External Services  │  ────────────▶│  OpenChargeMap│ │
│  │  - Station Reco     │                │  API          │ │
│  │  - Map Data         │                └──────────────┘ │
│  └─────────────────────┘                             │     │
└─────────────────────────────────────────────────────────────┘
                    ▲
                    │
┌─────────────────────┐
│    DATABASE/FILES   │
│  - Telemetry CSV    │
│  - Model Artifacts  │
│  - Shap Explanations│
└─────────────────────┘
```

## Use Case Diagram

```mermaid
usecase "Manage Battery Health" { actor "User"; usecase "View SoH Status"; usecase "View RUL Prediction"; usecase "Analyze Telemetry"; }
usecase "Optimize Charging" { actor "User"; usecase "Start Charging Session"; usecase "End Charging Session"; usecase "View Charging History"; }
usecase "Vehicle Management" { actor "User"; usecase "Add Vehicle"; usecase "Upload Documents"; usecase "View Vehicle Details"; }
usecase "Station Recommendation" { actor "User"; usecase "Find Charging Stations"; usecase "Filter by Connector"; usecase "Estimate Charging Time"; }
```

## Key Features

### Backend (Java Spring Boot)
- **Battery State of Health (SoH) Calculation**: Advanced algorithms to estimate battery health
- **Remaining Useful Life (RUL) Prediction**: XGBoost-based predictive modeling
- **Telemetry Processing**: Real-time data normalization, validation, and CSV parsing
- **Machine Learning Services**: XGBoost model serving with SHAP feature explanations
- **Vehicle Document Parsing**: PDF/Document processing for vehicle registration and compliance
- **OpenChargeMap Integration**: External charging station data and recommendations
- **Station Recommendation Service**: AI-powered charging station selection

### Frontend (React + TypeScript)
- **Battery Health Dashboard**: Visualize SoH, RUL, and key metrics
- **Charging Optimization**: Start/stop charging sessions with real-time updates
- **Vehicle Management**: Add vehicles, upload documents, view specifications
- **Charging Station Finder**: Search and filter charging stations
- **Telemetry Visualization**: Real-time battery performance charts
- **AI Coaching**: Personalized battery care recommendations
- **Responsive Design**: Mobile-friendly interface

## Running Commands

### Backend Setup

```bash
# Navigate to backend directory
cd backend

# Install dependencies and run with Maven
./mvnw spring-boot:run

# Or using Maven directly
mvn spring-boot:run
```

The backend will start on `http://localhost:8080` by default.

### Frontend Setup

```bash
# Navigate to frontend directory
cd frontend

# Install npm dependencies
npm install

# Start development server
npm run dev

# The frontend will be available at http://localhost:5173 (default Vite port)
```

### Full Stack Development

```bash
# Start both backend and frontend in separate terminals
# Terminal 1:
cd backend && ./mvnw spring-boot:run

# Terminal 2:
cd frontend && npm run dev
```

## Technology Stack

### Backend
- **Language**: Java 17
- **Framework**: Spring Boot
- **Build Tool**: Apache Maven
- **ML Libraries**: XGBoost, SHAP (Python support via requirements.txt)
- **Services**: RESTful API, External API integration (OpenChargeMap)

### Frontend
- **Language**: TypeScript
- **Framework**: React 18
- **Build Tool**: Vite
- **UI Components**: Custom components with Tailwind-friendly CSS
- **Routing**: React Router
- **State Management**: React hooks (useStations, useGeolocation)

## Development Notes

- The backend ML services (`BatteryMlService`, `RULCalculator`, `SoHCalculator`) use XGBoost models for predictive analytics
- Telemetry data is normalized via `TelemetryNormalizationService` before ML processing
- SHAP explanations (`shap_explainer.py`) provide interpretability for model predictions
- Frontend communicates with backend via REST API defined in `src/services/api.ts`
- CORS configuration should allow frontend domain during development