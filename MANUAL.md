# Trading Journal Manual

## 1. What this repository currently contains

This repository currently provides a detailed project specification (the `prompts/app_spec.txt` file) that describes a planned Spring Boot + React trading journal application, including its features, architecture, data model, and API surface.【F:prompts/app_spec.txt†L1-L383】 The specification covers how the app should behave, the intended technology stack, and the sequence of implementation steps, but there is no runnable application code in this repository yet.【F:prompts/app_spec.txt†L1-L383】

If you are looking for application source code or runnable services, they are not present in the current repo state. The steps below explain how the project is expected to run once implemented according to the specification.

## 2. High-level app purpose and flow

The app is a single-user cryptocurrency trading journal and execution platform. It tracks trades and positions, imports trade history from exchanges, and provides dashboards and analytics for performance and trade analysis.【F:prompts/app_spec.txt†L5-L158】 Users authenticate, connect exchange accounts, execute trades, review positions and trade history, and generate analytics reports from the data stored in PostgreSQL.【F:prompts/app_spec.txt†L39-L304】

## 3. Technology stack (frontend and backend)

### Frontend

The frontend is specified as a React application with Tailwind CSS for styling, using either React Context or Redux Toolkit for state management, Axios for HTTP requests, and Recharts or Chart.js for data visualization.【F:prompts/app_spec.txt†L10-L18】 The UI layout is a responsive shell with a collapsible sidebar, a main content area, and key pages like Portfolio, Trade, Analytics, Exchanges, and Settings.【F:prompts/app_spec.txt†L301-L331】

### Backend

The backend is specified as a Java 17+ Spring Boot 3.x application built with Maven. It uses Spring Security with JWT for authentication, SLF4J + Logback for logging, and integrates with exchanges through REST APIs (KuCoin, MEXC, Phemex).【F:prompts/app_spec.txt†L19-L38】 The backend persists data in PostgreSQL using Spring Data JPA + Hibernate and database migrations with Flyway.【F:prompts/app_spec.txt†L24-L28】

### Database

The data model includes tables for users, exchange connections, trades, trade tags, positions, orders, user settings, and strategies, all designed around the trading journal use cases.【F:prompts/app_spec.txt†L161-L268】

## 4. Expected runtime architecture

Once implemented, the project would run as a typical “React frontend + Spring Boot backend + PostgreSQL database” stack:

1. **Frontend** (React) runs as a separate Node.js dev server for development, serving the SPA and calling backend REST APIs via Axios.【F:prompts/app_spec.txt†L10-L18】
2. **Backend** (Spring Boot) runs as a Java service, exposing REST endpoints for auth, trades, positions, orders, analytics, and settings.【F:prompts/app_spec.txt†L270-L298】
3. **Database** (PostgreSQL) persists user data and trading records accessed by the backend via Spring Data JPA.【F:prompts/app_spec.txt†L24-L28】

## 5. Expected setup requirements

The specification lists the tools needed to run the project locally:

- Java 17+
- Maven 3.8+
- Node.js 18+ / npm
- PostgreSQL 14+
- Git【F:prompts/app_spec.txt†L41-L47】

## 6. Expected run steps (once code exists)

The spec does not include actual scripts or commands, but an implementation based on the stack above typically follows these steps:

1. **Start PostgreSQL**  
   Create a database and ensure credentials are available to the Spring Boot app (usually via environment variables or `application.yml`).

2. **Run the backend**  
   Use Maven to build and run the Spring Boot service (e.g., `mvn spring-boot:run`). The backend exposes the REST API described in the specification.【F:prompts/app_spec.txt†L270-L298】

3. **Run the frontend**  
   Use npm to install dependencies and start the React dev server (e.g., `npm install` then `npm start`). The React app uses Axios to talk to the backend API.【F:prompts/app_spec.txt†L10-L18】

4. **Connect exchanges**  
   The app expects integration with KuCoin, MEXC, and Phemex via API keys configured in the UI.【F:prompts/app_spec.txt†L124-L148】

Because the code is not present yet, the exact command names/ports are not specified in the repo. When the implementation is added, update this section with concrete scripts and environment variables.

## 7. Backend API surface (planned)

The backend REST API is planned to include endpoints for:

- Authentication (`/api/auth/*`)
- User profile (`/api/users/me`)
- Exchange connections (`/api/exchanges`)
- Positions and orders (`/api/positions`, `/api/orders`)
- Trades and trade imports (`/api/trades`)
- Market data (`/api/market/*`)
- Analytics (`/api/analytics/*`)
- Settings and strategies (`/api/settings`, `/api/strategies`)【F:prompts/app_spec.txt†L270-L298】

## 8. Feature areas (planned)

Key feature areas outlined in the spec include:

- Authentication and session management
- Portfolio and positions overview
- Trade execution and order management
- Trade history and imports from exchanges
- Analytics dashboards and reports
- Exchange configuration and API key management
- User preferences and settings
- Error handling and resilience features【F:prompts/app_spec.txt†L63-L160】

## 9. Implementation roadmap (planned)

The specification defines an eight-step build plan from initial setup through testing and documentation, beginning with authentication and ending with a test/documentation phase.【F:prompts/app_spec.txt†L335-L383】

---

### Next steps

If the codebase is added later, revisit this manual to:

- Document the actual build/run commands.
- List required environment variables.
- Provide real service ports and URLs.
- Add instructions for running tests.
