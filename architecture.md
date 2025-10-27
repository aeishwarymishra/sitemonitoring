```mermaid
flowchart TB
  %% ============ Data Ingestion Layer ============
  subgraph ING["Data Ingestion Layer"]
    D1[Drone / Camera Feeds]
    D2[IoT Sensors (vibration, temp, humidity)]
    D3[BIM and CAD Drawings]
    D4[Project Schedules (Primavera / MSP)]
    D5[Manual Inputs (inspection reports, checklists)]
  end

  %% ============ Processing & Storage ============
  subgraph PROC["Data Processing & Storage"]
    I1[Edge Device / On-site Gateway]
    P1[ETL and Preprocessing (images, time-series, metadata)]
    DB[(Data Lake: Object Storage + PostgreSQL + Vector DB)]
  end

  %% ============ AI / ML Layer ============
  subgraph AI["AI / ML Layer"]
    CV1[Computer Vision: detection, segmentation, progress, PPE]
    ML1[Predictive Models: schedule risk, cost, utilization]
    LLM[LLM Report Generator: daily summaries, insights]
  end

  %% ============ Application Layer ============
  subgraph APP["Application Layer"]
    A1[Web / Tablet Dashboard]
    A2[Alerts and Reports (Email, WhatsApp, Slack)]
    A3[BIM Viewer Integration (IFC / glTF)]
    A4[Digital Twin Sync]
  end

  %% ============ Flows ============
  D1 --> I1
  D2 --> I1
  I1 --> P1 --> DB
  D3 --> DB
  D4 --> DB
  D5 --> DB

  DB --> CV1 --> ML1 --> LLM --> A1
  ML1 --> A2
  CV1 --> A3
  LLM --> A4

```
