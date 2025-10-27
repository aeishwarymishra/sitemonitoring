```mermaid
graph TB
    subgraph "Data Ingestion Layer"
        D1[Drone/Camera Feeds]
        D2[IoT Sensors<br>(vibration, temperature, humidity)]
        D3[BIM & CAD Drawings]
        D4[Project Schedules (Primavera/MSP)]
        D5[Manual Inputs<br>(inspection reports, checklists)]
    end

    subgraph "Data Processing & Storage"
        I1[Edge Device / On-site Gateway]
        P1[ETL + Preprocessing<br>(images, time-series, metadata)]
        DB[(Data Lake: S3/R2 + PostgreSQL + VectorDB)]
    end

    subgraph "AI/ML Layer"
        CV1[Computer Vision Models<br>• Object Detection (YOLOv8)<br>• Crack/Defect Segmentation (SAM/CrackSAM)<br>• Progress Estimation (Mask R-CNN)<br>• PPE/Safety Detection]
        ML1[Predictive Models<br>• Schedule Deviation<br>• Cost/Delay Risk<br>• Equipment Utilization]
        LLM[LLM-based Report Generator<br>• Summarize daily progress<br>• Extract insights from logs]
    end

    subgraph "Application Layer"
        A1[Dashboard (Web/Tablet)]
        A2[Alerts & Reports (Email, WhatsApp, Slack)]
        A3[BIM Viewer Integration (IFC/GLTF)]
        A4[Digital Twin Synchronization]
    end

    D1 --> I1 --> P1 --> DB
    D2 --> I1
    D3 --> DB
    D4 --> DB
    D5 --> DB
    DB --> CV1 --> ML1 --> LLM --> A1
    ML1 --> A2
    CV1 --> A3
    LLM --> A4
```
