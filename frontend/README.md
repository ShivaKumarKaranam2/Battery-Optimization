# Frontend: AI Battery Optimization

React + TypeScript + Vite frontend for the AI Battery Optimization system. Provides a comprehensive user interface for battery management, charging optimization, and vehicle monitoring.

## Overview

This frontend component connects to the Java Spring Boot backend to provide real-time battery monitoring, charging session management, and vehicle diagnostics. Built with React 18, TypeScript, and Vite for fast development and production builds.

## Project Structure

```
frontend/
├── src/
│   ├── components/         # Reusable UI components
│   │   ├── vehicle/        # Vehicle-related components
│   │   │   ├── VehicleCard.tsx
│   │   │   ├── VehicleForm.tsx
│   │   │   └── VehicleDocumentUpload.tsx
│   │   ├── stations/       # Charging station components
│   │   │   ├── StationCard.tsx
│   │   │   ├── StationList.tsx
│   │   │   └── StationDetailModal.tsx
│   │   ├── BatteryExplanation.tsx   # AI explanation display
│   │   ├── BatteryExplanationDashboard.tsx  # Dashboard view
│   │   ├── ExplanationHistory.tsx     # History of explanations
│   │   ├── LogChargingSessionModal.tsx  # Charging session logging
│   │   └── PrivateRoute.tsx           # Authentication routing
│   │   └── Navbar.tsx                 # Navigation bar
│   ├── pages/              # Page-level components
│   │   ├── LandingPage.tsx          # Landing/home page
│   │   ├── Dashboard.tsx            # Main dashboard
│   │   ├── BatteryHealthPage.tsx    # Battery health visualization
│   │   ├── ChargingOptimizationPage.tsx  # Charging optimization
│   │   ├── ChargingHistoryPage.tsx  # Charging history
│   │   ├── VehicleSetupPage.tsx     # Vehicle configuration
│   │   ├── StationListPage.tsx      # Station listing
│   │   └── AiCoachingPage.tsx       # AI coaching recommendations
│   ├── services/           # API services
│   │   ├── api.ts               # API client configuration
│   │   ├── vehicleService.ts      # Vehicle API calls
│   │   ├── batteryExplanationService.ts  # Battery explanation API
│   │   ├── chargingSessionService.ts   # Charging session API
│   │   ├── stationService.ts        # Station API calls
│   │   └── telemetryService.ts     # Telemetry data API
│   ├── hooks/              # Custom React hooks
│   │   ├── useStations.ts         # Station data fetching
│   │   └── useGeolocation.ts      # Geolocation tracking
│   ├── types/              # TypeScript type definitions
│   │   ├── chargingSession.ts     # Charging session types
│   │   ├── vehicle.ts             # Vehicle types
│   │   └── station.ts             # Station types
│   ├── index.css           # Global styles
│   ├── App.tsx             # Root component
│   └── main.tsx            # Entry point
├── index.html              # HTML template
├── vite.config.ts          # Vite configuration
├── package.json            # Dependencies and scripts
├── package-lock.json       # Locked dependencies
├── tsconfig.json           # TypeScript config
├── tsconfig.app.json       # App TypeScript config
├── tsconfig.node.json      # Node TypeScript config
├── eslint.config.js        # ESLint configuration
├── .gitignore              # Git ignore rules
└── README.md               # This file
```

## API Integration

The frontend communicates with the backend REST API at `http://localhost:8080`. Key endpoints:

- `GET /api/vehicles` - List all vehicles
- `POST /api/vehicles` - Add new vehicle
- `GET /api/vehicles/{id}` - Get vehicle details
- `POST /api/telemetry` - Submit telemetry data
- `GET /api/telemetry/history` - Get telemetry history
- `POST /api/charging-sessions` - Start charging session
- `POST /api/charging-sessions/{id}/end` - End charging session
- `GET /api/stations` - List charging stations
- `GET /api/battery/soh` - Get battery state of health
- `GET /api/battery/rul` - Get remaining useful life prediction

## Getting Started

### Prerequisites

- Node.js (v18 or higher)
- npm or yarn
- Backend running on `http://localhost:8080`

### Installation

```bash
# Install dependencies
npm install

# Start development server
npm run dev
```

The development server starts at `http://localhost:5173` by default (Vite default).

### Available Scripts

| Script | Description |
|--------|-------------|
| `npm run dev` | Start development server with HMR |
| `npm run build` | Build for production |
| `npm run lint` | Run ESLint |
| `npm run preview` | Preview production build |

### Production Build

```bash
npm run build
```

Output is generated in the `dist` directory.

## Component Guide

### Dashboard (`Dashboard.tsx`)
Main dashboard displaying:
- Current battery status overview
- Quick charging session controls
- Recent telemetry trends
- Station recommendations

### Battery Health Page (`BatteryHealthPage.tsx`)
- SoH gauge and progress bar
- RUL prediction display
- Historical health data chart
- Degradation analysis

### Charging Optimization Page (`ChargingOptimizationPage.tsx`)
- Start/stop charging sessions
- Real-time charging status
- Estimated full charge time
- Charging pattern analysis

### Vehicle Setup (`VehicleSetupPage.tsx`)
- Add new vehicle
- Upload vehicle documents
- View vehicle specifications
- Document validation status

### Station List (`StationListPage.tsx`)
- Search charging stations
- Filter by connector type
- View station details
- Get directions integration

### AI Coaching (`AiCoachingPage.tsx`)
- Personalized battery care recommendations
- Charging habit analysis
- Efficiency tips
- Predictive maintenance alerts

## Technologies

- **React 18** with TypeScript for type-safe development
- **Vite** for fast HMR and optimized builds
- **React Router** for page navigation
- **ESLint** for code quality and type-aware linting
- **Axios** (via api.ts) for API communication
- **CSS Modules/Scoped Styles** for component styling

## API Service Details

### `api.ts`
Base API configuration with base URL, interceptors for authentication and error handling.

### `vehicleService.ts`
- `getVehicles()` - Fetch all vehicles
- `createVehicle(vehicle)` - Create new vehicle
- `updateVehicle(id, data)` - Update vehicle
- `deleteVehicle(id)` - Delete vehicle

### `batteryExplanationService.ts`
- `getExplanation(data)` - Get AI explanation for battery status
- `getFeatureImportance()` - Get SHAP feature importance

### `chargingSessionService.ts`
- `startSession(vehicleId)` - Start charging session
- `endSession(sessionId)` - End charging session
- `getHistory()` - Get charging history

### `stationService.ts`
- `searchStations(filters)` - Search stations with filters
- `getStationDetails(id)` - Get detailed station info

### `telemetryService.ts`
- `submitTelemetry(data)` - Submit real-time telemetry
- `getHistory()` - Get telemetry history

## Development

### Adding New Components

1. Create component in `src/components/`
2. Add types in `src/types/` if needed
3. Create API service in `src/services/` if backend interaction needed
4. Add page in `src/pages/` for routing
5. Update `App.tsx` routing if necessary

### Styling

- Component-scoped CSS files in `src/components/` and `src/pages/`
- ESLint configured for type-aware linting
- Tailwind CSS not configured but vanilla CSS available

## Deployment

```bash
# Build production version
npm run build

# The dist/ folder contains static files for deployment
# Can be deployed to any static hosting (Netlify, Vercel, etc.)
```