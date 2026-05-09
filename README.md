CAPA EDGE (hardware)
├── ESP32 DevKitC V4 — firmware C++ / Arduino-ESP-IDF
├── SHT31 (I2C) — temperatura + humedad ambiental
├── DS18B20 impermeable (1-Wire) — temperatura interna junto al medicamento
└── MC-38 reed switch (opcional) — detección apertura de refrigerador

CAPA EDGE (software local)
├── Python + Flask — suscriptor MQTT, validación de umbrales, buffer offline
└── SQLite — persistencia local ante pérdida de conectividad

CAPA BROKER
└── EMQX Cloud Serverless — MQTT sobre TLS 1.2/1.3, token por dispositivo

CAPA BACKEND
├── Python + FastAPI — API REST, lógica de negocio, JWT + RBAC
├── PostgreSQL — persistencia central con hash encadenado SHA-256
└── Deploy: Railway (FastAPI + PostgreSQL)

CAPA IA
├── Python + scikit-learn — entrenamiento Random Forest
└── Clasificación: normal / riesgo_preventivo / excursión_crítica

CAPA FRONTEND
├── Angular (recomendado si ya lo dominas) O React + Vite
├── Librería gráficas: Apache ECharts (Angular) o Recharts (React)
└── Deploy: Vercel (React/Angular estático)

SEGURIDAD (alineamiento, no certificación)
├── ISO/IEC 30141:2024 — arquitectura de referencia IoT
├── OWASP IoT Security Testing Guide v1.0.0
└── OWASP Web Security Testing Guide v4.2

TRAZABILIDAD (sin blockchain)
└── SHA-256 + previous_hash + timestamp + payload → PostgreSQL
