graph TD
    %% Styling
    classDef ui fill:#e1f5fe,stroke:#01579b,stroke-width:2px;
    classDef logic fill:#fff3e0,stroke:#ff6f00,stroke-width:2px,stroke-dasharray: 5 5;
    classDef core fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px;
    classDef infra fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px;
    classDef user fill:#ffffff,stroke:#000000,stroke-width:2px;

    subgraph User_Layer [User Interface Layer]
        User((👤 Security Engineer)):::user
        Dashboard[💻 Gradio Dashboard<br/><i>Async UI</i>]:::ui
    end

    subgraph Orchestration_Layer [LangGraph Orchestration Engine]
        direction TB
        Start((🚀 Start))
        Monitor[🕵️ Monitor Agent<br/><i>Role: Scanner</i>]:::core
        Verifier[⚖️ Verifier Agent<br/><i>Role: Analyst</i>]:::core
        Gate{⚠️ HITL Approval<br/><i>Interrupt</i>}:::logic
        Fixer[🛠️ Fixer Agent<br/><i>Role: Remediation</i>]:::core
    end

    subgraph MCP_Layer [Model Context Protocol]
        MCPServer[🔌 MCP Server<br/><i>Stdio Subprocess</i>]:::infra
        Tools[🧰 AWS Tools<br/><i>Boto3 SDK</i>]:::infra
    end

    subgraph Cloud_Layer [AWS Infrastructure]
        AWS_S3[(🪣 S3 Buckets)]:::infra
        AWS_EC2[🖥️ EC2 Instances]:::infra
    end

    %% Data Flow
    User -->|Click 'Scan'| Dashboard
    Dashboard -->|Trigger Workflow| Start
    Start --> Monitor
    
    %% Monitoring Flow
    Monitor <-->|MCP: list_resources| MCPServer
    MCPServer <-->|Read-Only API| AWS_S3
    MCPServer <-->|Read-Only API| AWS_EC2
    Monitor -->|Raw Findings| Verifier

    %% Verification Flow
    Verifier -->|Analysis Report| Gate
    Gate -.->|Pause Execution| Dashboard
    Dashboard -->|User Reviews| User
    User -->|Click 'Approve'| Dashboard
    Dashboard -->|Resume Workflow| Gate

    %% Fixing Flow
    Gate -->|Approved?| Fixer
    Fixer <-->|MCP: enable_security| MCPServer
    MCPServer -->|Write API| AWS_S3
    Fixer -->|Final Report| Dashboard
