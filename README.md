# 🤖 Enterprise RAG Agent: DeepSeek + Flowise on VPS

> **Despliegue de un Agente de IA con Arquitectura RAG (Retrieval-Augmented Generation) en infraestructura propia.**

Este proyecto implementa un sistema de consultas automatizado capaz de leer documentación corporativa privada y responder preguntas precisas utilizando el modelo **DeepSeek-V3** orquestado a través de **FlowiseAI**.

## 🛠️ Tech Stack & Architecture

* **Orquestación:** [FlowiseAI](https://flowiseai.com/) (Low-Code LLM Builder).
* **LLM Engine:** DeepSeek Chat 
* **Vectorización:** OpenAI Embeddings (`text-embedding-ada-002`).
* **Memoria:** In-Memory Vector Store (Prototipado rápido).
* **Infraestructura:**
    * Hetzner Cloud VPS (Ubuntu Linux).
    * Docker & Docker Compose.
    * Gestión de permisos de usuario (`non-root` execution).

## 🚀 Desafíos Técnicos Resueltos

1.  **Infraestructura como Código:** Despliegue contenerizado mediante `docker-compose.yml` con persistencia de volúmenes.
2.  **Seguridad Linux:** Configuración de entorno de ejecución con usuario dedicado  para evitar vulnerabilidades de root y gestión de permisos `chown`.
3.  **Networking:** Gestión de UFW Firewall y exposición de puertos seguros.
4.  **Integración RAG:** Configuración de `Base URL` personalizada para enrutar peticiones de Flowise hacia la API de DeepSeek, logrando un coste 10x menor que GPT-4 con rendimiento similar.
## 🧠 Skills Matrix

Este proyecto ha servido para validar y consolidar las siguientes competencias técnicas y profesionales:

### 🛠️ Hard Skills (Tecnologías)
* **AI Engineering:** Implementación de arquitectura **RAG** (Retrieval-Augmented Generation), gestión de **Embeddings** y configuración de parámetros de inferencia en LLMs (Temperature tuning).
* **LLM Integration:** Integración de API de **DeepSeek** como alternativa eficiente en costes frente a modelos propietarios estándar (OpenAI).
* **Containerization:** Orquestación de servicios con **Docker** y **Docker Compose**, gestión de volúmenes persistentes y redes internas.
* **Linux System Administration:** Despliegue en VPS remoto (Hetzner), gestión de usuarios y permisos (`chown/chmod`), y configuración de seguridad de red con **UFW Firewall**.
* **No-Code/Low-Code Logic:** Diseño de flujos lógicos complejos y cadenas de procesamiento de datos utilizando **FlowiseAI**.

### 🤝 Soft Skills (Metodologías)
* **Root Cause Analysis:** Capacidad demostrada para diagnosticar y resolver errores críticos de despliegue (CrashLoopBackOff, Logs debugging) en entornos de producción.
* **Security Mindset:** Aplicación del principio de "mínimo privilegio" ejecutando servicios con usuarios dedicados no-root.
* **Cost Optimization:** Selección estratégica de modelos (DeepSeek) para maximizar el rendimiento reduciendo costes operativos.
* **Documentation:** Capacidad para traducir arquitectura técnica en documentación funcional clara.

## 📋 Cómo replicar (Deploy)

### 1. Configuración del VPS
El proyecto corre sobre un contenedor Docker aislado.

```bash
# Clonar repositorio y levantar servicios
git clone [https://github.com/tu-usuario/flowise-rag-deploy.git](https://github.com/tu-usuario/flowise-rag-deploy.git)
cd flowise-rag-deploy
docker compose up -d