## 📧 Contacto

https://www.linkedin.com/in/gerardomayel/

Link del proyecto: https://github.com/GerardoMayel/etl-clima/edit/main/README.md

# 🌤️ ETL-Clima

![Python](https://img.shields.io/badge/python-3.9+-blue.svg)
![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-2.7.1-green.svg)
![PySpark](https://img.shields.io/badge/PySpark-3.2.0-orange.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

Un pipeline ETL automatizado que recolecta datos meteorológicos de la Ciudad de México utilizando Apache Airflow y PySpark. El proyecto implementa una arquitectura moderna de datos siguiendo el paradigma medallión (Bronze, Silver, Gold).

## 📊 Arquitectura del Proyecto

```
etl-clima/
│
├── .github/
│   └── workflows/
│       └── deploy.yml          # Configuración de CI/CD
│
├── dags/
│   ├── utils/
│   │   └── spark_operations.py # Operaciones de PySpark
│   └── weather_etl.py         # DAG principal de Airflow
│
├── config/
│   └── airflow.cfg           # Configuración de Airflow
│
├── .env.example              # Template de variables de ambiente
├── .gitignore               # Archivos ignorados por Git
├── docker-compose.yaml      # Configuración de servicios
├── Dockerfile              # Imagen personalizada de Airflow
├── requirements.txt        # Dependencias de Python
└── README.md              # Este archivo
```

## 🌟 Características

- 🔄 ETL automatizado que se ejecuta diariamente a las 5:00 AM
- 🌡️ Recolección de datos meteorológicos de OpenWeatherMap API
- 📊 Procesamiento de datos usando PySpark
- 🏆 Arquitectura medallión (Bronze → Silver → Gold)
- 📧 Notificaciones por correo electrónico
- 🐳 Completamente dockerizado
- 🔐 Manejo seguro de credenciales
- 🔄 Integración continua con GitHub Actions

## 🏗️ Arquitectura de Datos

### Bronze Layer
- Datos crudos sin procesar de la API
- Formato JSON
- Preservación histórica completa

### Silver Layer
- Datos estructurados y limpios
- Esquema optimizado
- Tracking temporal
- Datos enriquecidos

### Gold Layer
- Datos agregados listos para análisis
- Métricas calculadas
- KPIs principales
- Vista única y actualizada

## 🚀 Instalación

1. **Clonar el repositorio**
```bash
git clone https://github.com/GerardoMayel/etl-clima.git
cd etl-clima
```

2. **Configurar variables de ambiente**
```bash
cp .env.example .env
# Editar .env con tus credenciales
```

3. **Levantar servicios con Docker**
```bash
docker-compose up -d
```

4. **Verificar la instalación**
```bash
docker-compose ps
```

## 🔑 Configuración de Credenciales

1. Obtener API Key de [OpenWeatherMap](https://openweathermap.org/api)
2. Configurar credenciales SMTP para notificaciones
3. Actualizar archivo `.env`:
```env
OPENWEATHER_API_KEY=tu_api_key
SMTP_USER=geramfernandez@gmail.com
SMTP_PASSWORD=tu_password
```

## 📈 Monitoreo y Logs

- **UI de Airflow**: http://localhost:8080
- **Logs**: Disponibles en la UI de Airflow
- **Notificaciones**: Configuradas por correo electrónico

## 🔄 Pipeline ETL

```mermaid
graph LR
    A[OpenWeather API] -->|Fetch Data| B[Bronze Layer]
    B -->|Process| C[Silver Layer]
    C -->|Aggregate| D[Gold Layer]
    D -->|Notify| E[Email Report]
```

## 📊 Métricas Principales

- Temperatura actual
- Temperatura promedio histórica
- Total de registros procesados
- Última fecha de ejecución
- Estadísticas de procesamiento

## 🛠️ Tecnologías Utilizadas

- Apache Airflow
- PySpark
- Docker
- Python 3.9+
- PostgreSQL
- GitHub Actions

## 📝 Contribución

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/newfeature`)
3. Commit tus cambios (`git commit -m 'First Commit'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📜 Licencia

Distribuido bajo la licencia MIT. Ver `LICENSE` para más información.


## 🙏 Agradecimientos

- [Apache Airflow](https://airflow.apache.org/)
- [OpenWeatherMap](https://openweathermap.org/)
- [Apache Spark](https://spark.apache.org/)
