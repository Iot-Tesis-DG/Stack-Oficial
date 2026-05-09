```text
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CAPA EDGE — HARDWARE EMBEBIDO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── ESP32 DevKitC V4
│   └── Firmware en C++ (Arduino-ESP-IDF)
├── SHT31 (I2C) — temperatura + humedad ambiental
├── DS18B20 impermeable (1-Wire) — temperatura
│   interna junto al medicamento
└── MC-38 reed switch (opcional) — apertura refrigerador

  ► Buffer offline en SPIFFS/LittleFS del ESP32
  ► Sin capa Flask/SQLite local

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CAPA BROKER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
└── EMQX Cloud Serverless
    ├── MQTT sobre TLS 1.2/1.3
    └── Token por dispositivo

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CAPA BACKEND — FastAPI + DDD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── Python + FastAPI
│   ├── Arquitectura interna: Domain-Driven Design
│   │   ├── Domain Layer
│   │   │   ├── Entidades: LecturaTermica,
│   │   │   │   AlertaTermica, RegistroTrazabilidad
│   │   │   └── Value Objects: RangoTermico,
│   │   │       NivelRiesgo, HashEncadenado
│   │   ├── Application Layer — casos de uso:
│   │   │   ClasificarRiesgoTermico, GenerarAlerta,
│   │   │   RegistrarHashEncadenado, ExportarReporteBPA
│   │   ├── Infrastructure Layer — repositorios
│   │   │   PostgreSQL, cliente MQTT EMQX
│   │   └── Interface Layer — routers FastAPI (REST)
│   ├── JWT + RBAC
│   └── Inferencia Random Forest integrada en
│       Application Layer
├── PostgreSQL (Railway)
│   ├── Histórico de lecturas térmicas
│   └── Hash encadenado SHA-256 + previous_hash
└── Deploy: Railway Hobby

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CAPA IA
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── Python + scikit-learn
├── Modelo: Random Forest
└── Output: normal / riesgo_preventivo / excursión_crítica

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CAPA FRONTEND — React + DDD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── React 19 + Vite + TypeScript
│   ├── Arquitectura interna: Domain-Driven Design
│   │   ├── Domain Layer — tipos e interfaces:
│   │   │   LecturaTermica, AlertaTermica,
│   │   │   NivelRiesgo, RegistroTrazabilidad
│   │   ├── Application Layer — hooks/servicios:
│   │   │   useMonitoreoTermico, useAlertas,
│   │   │   useTrazabilidad
│   │   ├── Infrastructure Layer — clientes API:
│   │   │   FastAPI REST client, WebSocket client
│   │   └── Presentation Layer — componentes React:
│   │       DashboardPage, HistorialPage,
│   │       AlertasPage, ReporteBPAPage
├── Shadcn/ui — componentes UI accesibles
├── Apache ECharts (echarts-for-react) — gráficas
│   de temperatura en tiempo real e historial
├── WebSocket / SSE — actualización en vivo
└── Deploy: Vercel

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SEGURIDAD (alineamiento técnico, no certificación)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── ISO/IEC 30141:2024 — arquitectura de referencia IoT
├── OWASP IoT Security Testing Guide v1.0.0
└── OWASP Web Security Testing Guide v4.2

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TRAZABILIDAD DIGITAL VERIFICABLE (sin blockchain)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
└── SHA-256 + previous_hash + timestamp + payload
    → PostgreSQL (Railway)
```
