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

## 📋 Cómo replicar (Deploy)

### 1. Configuración del VPS
El proyecto corre sobre un contenedor Docker aislado.

```bash
# Clonar repositorio y levantar servicios
git clone [https://github.com/tu-usuario/flowise-rag-deploy.git](https://github.com/tu-usuario/flowise-rag-deploy.git)
cd flowise-rag-deploy
docker compose up -d