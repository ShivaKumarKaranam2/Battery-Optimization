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

```mermaid
flowchart TD
    backend[Backend<br/>(Java Spring Boot)] -->|REST API| frontend[Frontend<br/>(React)]
    
    backend -->|ML & Prediction| ml[ML Services]
    ml -->|XGBoost RUL| rul[RUL Calculator]
    ml -->|SoH Calculation| soh[SoH Calculator]
    ml -->|Telemetry NV| telemetry[Telemetry Normalization]
    
    backend -->|Data Processing| processing[CSV Parsing & Validation]
    processing -->|Normalized Data| telemetry
    
    backend -->|External Services| external[OpenChargeMap API]
    external -->|Station Data| backend
    
    backend -->|Database/Files| storage[(Storage)]
    storage -->|Telemetry CSV| telemetry
    storage -->|Model Artifacts| ml
    storage -->|SHAP Explanations| shap[shap_explainer.py]
    
    classDef backend fill:#f9f,stroke:#333,stroke-width:2px
    classDef frontend fill:#bbf,stroke:#333,stroke-width:2px
    classDef ml fill:#cfc,stroke:#333,stroke-width:2px
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