# <p align = 'center'>**HamsterCare - Smart Hamster Care System**</p>

## Table of Contents
- [Introduction](#introduction)
- [Source Code & Documentation](#source-code--documentation)
  - [Project Structure](#project-structure)
  - [Main Components](#main-components)
    - [Backend (Golang/Gin)](#backend-golanggin)
    - [Frontend (Flutter)](#frontend-flutter)
    - [IoT (ESP32/YoloBit)](#iot-esp32yolobit)
- [Features](#features)
  - [Environmental Monitoring & Control](#️-environmental-monitoring--control)
  - [Automated Water Management](#-automated-water-management)
  - [Smart Control & Notifications](#-smart-control--notifications)
- [Technical Architecture](#technical-architecture)
  - [Frontend](#frontend-flutter-1)
  - [Backend](#backend)
  - [IoT Components](#iot-components)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Frontend Installation](#frontend-installation)
  - [Backend Installation](#backend-installation)

## Introduction

The demand for pet ownership has been steadily increasing, with hamsters becoming increasingly popular due to their small size and adorable appearance. However, raising hamsters presents significant challenges as they require strict environmental conditions to thrive and are highly susceptible to illness.

Traditional pet care methods rely heavily on human intervention, which can be prone to oversight and potentially harmful to these delicate creatures. To address this, HamsterCare provides an automated IoT solution for monitoring and maintaining optimal living conditions for hamsters.

## Source Code & Documentation

For the complete source code and detailed documentation, please visit our main repository:
- 🔗 [HamsterCare Project Repository](https://github.com/jncmtam/DADN-SE)
- 📚 [Full Documentation](/docs/report.pdf)


### Project Structure
```
DADN-SE/
├── hamsBE/              # Backend source code (Golang)
│   ├── api/             # API endpoints & routing
│   │   ├── routes/      # Route handlers (auth, user, admin)
│   │   └── router.go    # Main router setup
│   ├── internal/        # Core implementation
│   │   ├── model/       # Data models
│   │   ├── service/     # Business logic
│   │   ├── repository/  # Database operations
│   │   ├── middleware/  # JWT auth
│   │   ├── websocket/   # Real-time updates
│   │   ├── mqtt/        # IoT communication
│   │   ├── database/    # DB connection & migrations
│   │   ├── cache/       # Caching layer
│   │   └── utils/       # Helper functions
│   └── docs/            # API documentation
├── hamsFE/              # Frontend source code (Flutter)
│   ├── lib/             # Application code
│   │   ├── views/       # UI screens & widgets
│   │   ├── models/      # Data models
│   │   └── controllers/ # Business logic
│   ├── assets/          # Images & resources
│   └── test/            # Unit & widget tests
├── hamsIoT/             # IoT source code (ESP32)
│   ├── src/             # Source code
│   │   └── yolobit/     # YoloBit implementation
│   └── images/          # Wiring diagrams
└── mosquitto/           # MQTT broker configuration
```

### Main Components

#### Backend (Golang/Gin)
- RESTful API endpoints for device control and monitoring
- Real-time WebSocket communication for live updates
- MQTT client for IoT device communication
- JWT authentication and authorization
- PostgreSQL database integration

#### Frontend (Flutter)
- Cross-platform mobile application
- Real-time data visualization
- Device control interface
- User authentication and profile management
- Push notifications for alerts

#### IoT (ESP32/YoloBit)
- Temperature and humidity monitoring (DHT11)
- Light intensity sensing
- Water level detection
- Device control:
  - Cooling fan
  - LED lighting
  - Water pump
  - Smart lock


## Features

### 🌡️ Environmental Monitoring & Control
- Real-time monitoring of temperature, humidity, and light levels
- Automated environmental adjustments based on sensor data
- Temperature control with automatic fan activation (>30°C)
- Smart lighting system that adjusts based on ambient light levels

### 💧 Automated Water Management
- Continuous water level monitoring
- Automatic water refill system
- Remote water system control via mobile app

### 📱 Smart Control & Notifications
- Real-time alerts for environmental changes
- Instant notifications for device status changes
- Remote device control through mobile application
- Dual control modes:
  - **Automatic Mode**: Device operation based on sensor data and user-defined rules
  - **Manual Mode**: Direct device control through the app

## Technical Architecture

### Frontend (Flutter)
- Cross-platform mobile application (iOS & Android)
- Material Design UI components
- Real-time data visualization with FL Chart
- WebSocket for live updates
- Local notifications
- Secure storage for authentication
- Image handling for profiles and documentation

### Backend
- Built with Golang and Gin framework
- PostgreSQL database for data persistence
- Real-time communication via WebSocket and MQTT
- JWT authentication and authorization

### IoT Components
- Temperature and humidity sensors
- Light intensity sensors
- Distance sensors for water level
- Controllable devices:
  - Mini cooling fan
  - LED lighting system
  - Water pump
  - Smart lock

## Getting Started

### Prerequisites
- Go (1.23.0 or later)
- PostgreSQL
- MQTT Broker
- Flutter (3.5.3 or later)

### Frontend Installation

#### Step 1: Install Flutter
Ensure you have Flutter installed on your system. If not, follow the official Flutter installation guide at https://flutter.dev/docs/get-started/install

Verify your installation:
```bash
flutter --version
```

#### Step 2: Install Dependencies
```bash
cd hamsFE
flutter pub get
```

Key dependencies include:
- google_fonts
- flutter_svg
- http
- flutter_secure_storage
- web_socket_channel
- fl_chart
- flutter_local_notifications
- image_picker

#### Step 3: Configure Environment
The app is configured to connect to the backend at `localhost:8080`. To modify this:
1. Open `lib/views/constants.dart`
2. Update the `apiUrl` constant with your backend URL

#### Step 4: Run the Application
```bash
flutter run
```

This will launch the app on your connected device or emulator.

Supported platforms:
- Android
- iOS
- Web
- macOS
- Linux
- Windows

Note: For iOS and macOS development, ensure you have Xcode installed and CocoaPods dependencies are up to date:
```bash
cd ios/ # or macos/
pod install
```

### Backend Installation

#### Step 1: Install Go Dependencies
```bash
cd hamsBE
go mod tidy
```

#### Step 2: Configure Environment
Create or modify the `.env` file with your configuration:

```bash
# Go
PORT=8080

# PostgreSQL config
DB_HOST=localhost
DB_PORT=5432
DB_USER=hamster
DB_PASSWORD=hamster
DB_NAME=hamster

# Security
JWT_SECRET_KEY=<your_jwt_secret_key>

# MQTT Broker (e.g., 10.28.129.171:1883 or mqtt.example.com:1883)
MQTT_BROKER=<your_mqtt_broker_address>

# Email for notifications and OTP
EMAIL=<your_email_address>
SENDGRID_API_KEY=<your_sendgrid_api_key>
```

#### Step 3: Run the Server

Standard mode:
```bash
go run main.go
```

Development mode with hot-reload:
```bash
air
```

Using Docker (optional):
```bash
docker-compose up --build
```

The backend server will be accessible at `http://localhost:8080`
