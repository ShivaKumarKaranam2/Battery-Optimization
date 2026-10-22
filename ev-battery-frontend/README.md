# Battery Optimization System

A comprehensive AI-powered battery optimization system for electric vehicles.

## Overview

This project implements advanced battery management and optimization techniques using machine learning models and real-time telemetry data. The system includes:

- **AI Battery Prediction**: Machine learning models (XGBoost, RUL calculator, SoH calculator) for battery state prediction
- **Telemetry Processing**: Real-time data normalization and validation
- **Vehicle Services**: Vehicle service integration and document parsing
- **Charging Optimization**: Intelligent charging session management

## Architecture

The system consists of two main components:

1. **AI-battery** (`AI-battery/`): Java-based backend with Spring Boot, ML services, and battery analytics
2. **EV Battery Frontend** (`ev-battery-frontend/`): React + TypeScript frontend for visualization and user interaction

## Features

- Battery State of Health (SoH) calculation
- Remaining Useful Life (RUL) prediction
- Charging session optimization
- Vehicle document processing
- Real-time telemetry monitoring
- Station recommendation services

## Getting Started

### Backend (AI-battery)

```bash
cd AI-battery
./mvnw spring-boot:run
```

### Frontend (ev-battery-frontend)

```bash
cd ev-battery-frontend
npm install
npm run dev
```

## Technologies

- Java 17, Spring Boot
- XGBoost, Python ML models
- React 18, TypeScript, Vite
- Apache Maven
```
