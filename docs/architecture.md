graph TB
    subgraph "Presentation Layer"
        A[User] -->|PDF/Text| B[Telegram Bot Interface]
        B -->|File Upload| C[File Handler]
        B -->|Message| D[Message Router]
    end
    
    subgraph "Orchestration Layer - n8n Workflow Engine"
        C --> E[Webhook Processor]
        D --> E
        E --> F[Event Manager]
        F --> G[State Handler]
        G --> H[API Gateway]
    end
    
    subgraph "AI Processing Layer"
        H -->|PDF Text| I[Resume Parser AI]
        I -->|Structured Data| J[Data Transformer]
        H -->|Job Post| K[Email Generator AI]
        H -->|Job Post| L[Subject Line AI]
        K --> M[HTML Formatter]
        L --> M
    end
    
    subgraph "Integration Layer"
        M --> N[Gmail SMTP]
        J --> O[Google Sheets API]
        N --> P[Email Delivery]
        O --> Q[Data Persistence]
    end
    
    subgraph "Data Layer"
        O --> R[(Sheet1: Resume DB)]
        O --> S[(Sheet2: Application Tracker)]
        E --> T[(n8n SQLite DB)]
    end
    
    subgraph "Notification Layer"
        P --> U[Success Handler]
        Q --> U
        U --> B
        B --> A
    end
    
    style A fill:#e1f5ff
    style B fill:#fff3e0
    style E fill:#f3e5f5
    style I fill:#e8f5e9
    style K fill:#e8f5e9
    style L fill:#e8f5e9
    style N fill:#fff9c4
    style O fill:#fff9c4
    style R fill:#ffebee
    style S fill:#ffebee
    style T fill:#ffebee
