# System Architecture - simple-lms

## Overview

simple-lms is built on a modern stack with a clear separation of concerns between frontend and backend components. The system uses a distributed architecture with separate repositories for documentation, backend API, and frontend application.

## Architecture Diagram

```mermaid
graph TD
    subgraph "Frontend (Netlify)"
        A[React Application] --> |API Calls| G[API Gateway]
        A --> |Authentication| B[Firebase Auth]
    end
    
    subgraph "Backend (Render.com)"
        G --> C[Express.js API]
        C --> D[Business Logic]
        D --> E[Data Access Layer]
        E --> F[MongoDB Atlas]
    end
    
    subgraph "External Services"
        B --> C
        C --> H[Google Calendar API]
        I[AI Service] --> |RAG| J[Vector DB]
        C --> I
    end
    
    subgraph "Data Storage"
        F --> K[Users Collection]
        F --> L[Courses Collection]
        F --> M[Resources Collection]
        F --> N[Classes Collection]
        F --> O[Cohorts Collection]
    end
```

## Component Architecture

### Frontend Architecture

```mermaid
graph TD
    A[App Entry] --> B[Router]
    B --> C[Auth Provider]
    C --> D[Layout Components]
    
    D --> E[Admin Dashboard]
    D --> F[Teacher Dashboard]
    D --> G[Student Dashboard]
    
    E --> H[User Management]
    E --> I[Course Management]
    E --> J[System Analytics]
    
    F --> K[Class Management]
    F --> L[Resource Management]
    F --> M[Student Progress]
    
    G --> N[My Courses]
    G --> O[My Resources]
    G --> P[My Calendar]
    G --> Q[AI Assistant]
    
    subgraph "Shared Components"
        R[Navigation]
        S[Form Components]
        T[Data Tables]
        U[Modal Dialogs]
        V[Calendar View]
    end
```

### Backend Architecture

```mermaid
graph TD
    A[Express App] --> B[Middleware]
    B --> C[Auth Middleware]
    B --> D[Routes]
    
    D --> E[User Routes]
    D --> F[Course Routes]
    D --> G[Resource Routes]
    D --> H[Class Routes]
    D --> I[Cohort Routes]
    D --> J[Calendar Routes]
    D --> K[AI Assistant Routes]
    
    E --> L[User Controllers]
    F --> M[Course Controllers]
    G --> N[Resource Controllers]
    H --> O[Class Controllers]
    I --> P[Cohort Controllers]
    J --> Q[Calendar Controllers]
    K --> R[AI Assistant Controllers]
    
    L --> S[Data Access Layer]
    M --> S
    N --> S
    O --> S
    P --> S
    Q --> S
    R --> S
    
    S --> T[MongoDB Interface]
```

### Database Schema

```mermaid
erDiagram
    USER {
        string id PK
        string firebaseId
        string email
        string name
        enum role
        date createdAt
        date updatedAt
    }
    
    COURSE {
        string id PK
        string title
        string description
        array resources
        array classes
        date createdAt
        date updatedAt
    }
    
    RESOURCE {
        string id PK
        string title
        string description
        string type
        string url
        date createdAt
        date updatedAt
    }
    
    CLASS {
        string id PK
        string title
        string description
        string courseId FK
        date scheduledDate
        array resources
        date createdAt
        date updatedAt
    }
    
    COHORT {
        string id PK
        string name
        string description
        array studentIds
        array courseIds
        date startDate
        date endDate
        date createdAt
        date updatedAt
    }
    
    CALENDAR_EVENT {
        string id PK
        string title
        string description
        date startTime
        date endTime
        string googleCalendarId
        enum eventType
        string referenceId
        date createdAt
        date updatedAt
    }

    USER ||--o{ COHORT : "assigned to"
    COHORT ||--o{ COURSE : "includes"
    COURSE ||--o{ CLASS : "contains"
    COURSE ||--o{ RESOURCE : "has"
    CLASS ||--o{ RESOURCE : "uses"
    CLASS ||--o{ CALENDAR_EVENT : "scheduled as"
```

## Technology Stack

### Frontend
- **Framework**: React with Vite
- **Language**: TypeScript
- **Styling**: Tailwind CSS 4
- **State Management**: React Context API
- **Routing**: React Router
- **Authentication**: Firebase Auth Client SDK
- **HTTP Client**: Axios
- **Testing**: Jest + React Testing Library
- **Hosting**: Netlify

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Language**: TypeScript
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: Firebase Admin SDK
- **API Documentation**: Swagger/OpenAPI
- **Testing**: Jest + Supertest
- **Hosting**: Render.com

### External Services
- **Authentication**: Firebase Authentication
- **Calendar Integration**: Google Calendar API
- **AI Assistant**: (Post-MVP) Vector Database + LLM Service

## Repository Structure

### Documentation Repository (simple-lms-docs)

```
simple-lms-docs/
├── README.md
├── PRD.md
├── ARCHITECTURE.md
├── ELEVATOR-PITCH.md
├── EXECUTIVE-SUMMARY.md
├── TECHNICAL-SUMMARY.md
├── MARKET-RESEARCH.md
├── PLAN.md
├── TASKS.md
└── assets/
    └── diagrams/
```

### Backend Repository (simple-lms-be)

```
simple-lms-be/
├── README.md
├── src/
│   ├── config/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   ├── utils/
│   └── index.ts
├── tests/
├── package.json
├── tsconfig.json
└── .env.example
```

### Frontend Repository (simple-lms-fe)

```
simple-lms-fe/
├── README.md
├── src/
│   ├── assets/
│   ├── components/
│   │   ├── common/
│   │   ├── admin/
│   │   ├── teacher/
│   │   └── student/
│   ├── contexts/
│   ├── hooks/
│   ├── pages/
│   ├── services/
│   ├── types/
│   ├── utils/
│   ├── App.tsx
│   └── main.tsx
├── public/
├── index.html
├── vite.config.ts
├── package.json
├── tsconfig.json
└── tailwind.config.js
```

## Deployment Architecture

```mermaid
flowchart TD
    A[GitHub Repositories] --> B[CI/CD Pipelines]
    
    B --> C[Backend CI/CD]
    B --> D[Frontend CI/CD]
    
    C --> E[Build & Test]
    E --> F[Deploy to Render.com]
    
    D --> G[Build & Test]
    G --> H[Deploy to Netlify]
    
    F --> I[Production Backend API]
    H --> J[Production Frontend App]
    
    I --> K[MongoDB Atlas]
    J --> I
    J --> L[Firebase Auth]
```

## Security Architecture

```mermaid
flowchart TD
    A[User] --> B[Firebase Auth]
    B --> C[JWT Token]
    C --> D[Frontend App]
    D --> E[API Gateway]
    
    E --> F[Auth Middleware]
    F --> G[Role-Based Access Control]
    G --> H[API Endpoints]
    
    H --> I[Data Validation]
    I --> J[Business Logic]
    J --> K[Data Access Layer]
    K --> L[MongoDB]
    
    subgraph "Security Measures"
        M[HTTPS Encryption]
        N[Input Sanitization]
        O[Rate Limiting]
        P[CORS Policy]
        Q[Environment Secrets]
    end
```

## Data Flow Architecture

```mermaid
sequenceDiagram
    actor User
    participant Frontend
    participant Firebase
    participant API
    participant DB as MongoDB
    participant Calendar as Google Calendar
    
    User->>Frontend: Login Request
    Frontend->>Firebase: Authenticate
    Firebase-->>Frontend: Auth Token
    Frontend->>API: API Request + Token
    API->>Firebase: Verify Token
    Firebase-->>API: Token Valid
    API->>DB: Database Query
    DB-->>API: Query Result
    API-->>Frontend: API Response
    Frontend-->>User: Display Data
    
    opt Calendar Integration
        User->>Frontend: Calendar Action
        Frontend->>API: Calendar Request
        API->>Calendar: Calendar API Call
        Calendar-->>API: Calendar Response
        API-->>Frontend: Updated Calendar Data
        Frontend-->>User: Display Calendar
    end
    
    opt AI Assistant (Post-MVP)
        User->>Frontend: Ask Question
        Frontend->>API: Question + Context
        API->>DB: Retrieve Relevant Content
        DB-->>API: Content for RAG
        API->>API: Generate AI Response
        API-->>Frontend: AI Answer
        Frontend-->>User: Display Answer
    end
```

## Resilience and Scaling

The architecture is designed to be resilient and scalable:

1. **Horizontal Scaling**: Both frontend and backend can be scaled horizontally
2. **Database Scaling**: MongoDB Atlas provides automated scaling options
3. **Caching**: Implement strategic caching for frequently accessed data
4. **Error Handling**: Comprehensive error handling and retry mechanisms
5. **Monitoring**: Integration with monitoring tools for performance tracking
6. **Backup**: Regular automated backups of database content

## Future Architectural Considerations

1. **Microservices**: Potential to break down the monolithic backend into microservices
2. **Container Orchestration**: Kubernetes for more complex deployment needs
3. **Event-Driven Architecture**: Implement message queues for asynchronous processing
4. **Edge Caching**: CDN integration for global performance improvements
5. **Advanced AI Features**: Dedicated AI infrastructure for the assistant feature
