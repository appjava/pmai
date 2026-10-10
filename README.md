# 🌱 PMAI - Plataforma Web de Monitoreo Agroecológico Inteligente

[![Estado](https://img.shields.io/badge/Estado-En%20Desarrollo-yellow)](https://pmai-saas.web.app)
[![Licencia](https://img.shields.io/badge/Licencia-MIT-green)](LICENSE)

PMAI es una solución SaaS diseñada para pequeños productores agroecológicos y PyMEs agrícolas en Colombia. Permite monitorear variables ambientales (humedad, temperatura, luminosidad) en tiempo real, configurar alertas tempranas y generar reportes de sostenibilidad, incluso en entornos con conectividad limitada.

🔗 **Demo en vivo:** [https://pmai-saas.web.app](https://pmai-saas.web.app)

## 🚀 Características Principales (MVP)
- ✅ Dashboard interactivo Mobile-First.
- ✅ Gestión de espacios de cultivo y dispositivos IoT.
- ✅ Motor de alertas por correo electrónico basado en umbrales configurables.
- ✅ Arquitectura tolerante a fallos de conectividad (Local-first).
- ✅ Reportes básicos de sostenibilidad en PDF/CSV.

## 🛠️ Stack Tecnológico
- **Frontend:** React.js, TypeScript, Vite, Tailwind CSS
- **Backend:** Python, FastAPI
- **Base de Datos:** SQLite (Desarrollo) / PostgreSQL + Supabase (Producción)
- **Infraestructura:** Firebase Hosting, GitHub Actions (CI/CD)

## 🤖 Integración con Qwen (Roadmap)

PMAI integrará el modelo Qwen de Alibaba Cloud para:
- **Análisis predictivo de cultivos**: Predicción de necesidades de riego basada en patrones históricos
- **Asistente virtual agroecológico**: Chatbot en español que responde preguntas técnicas a productores
- **Generación automática de reportes**: Resúmenes ejecutivos en lenguaje natural a partir de datos de sensores
- **Detección de anomalías**: Identificación temprana de plagas o enfermedades mediante análisis de patrones

*Tecnología: Qwen-7B-Chat fine-tuned con datos agroecológicos colombianos*

## 👨‍💻 Autor
**Jaime Alberto Valencia Abadía**  
Tecnólogo en Análisis y Desarrollo de Software (SENA) | Ingeniero Mecánico  
📧 java8934692@soy.sena.edu.co | 🔗 [IngJAVA.dev](https://ingjava.dev)

## 📄 Documentación del Proyecto
Este proyecto forma parte de mi fase productiva en el SENA y está siendo preparado para postulación al Fondo Emprender. La documentación técnica completa (IEEE 830, Ficha Técnica, DOFA) se encuentra en la carpeta `/docs`.