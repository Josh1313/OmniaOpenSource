# Proyecto: Plataforma Inteligente para Gestión de Modelos de IA y Recuperación de Información

## Descripción General
Este proyecto es una aplicación diseñada para potenciar el uso de Modelos de Lenguaje Extenso (LLMs) locales y en la nube, incluyendo OpenAI y Grok, integrados con un sistema de Recuperación de Información (RAG). Ofrece una interfaz amigable desarrollada en **Streamlit**, con capacidades avanzadas para:

- **Gestionar modelos de IA mediante un selector dinámico.**

- **Incorporar bases de datos vectoriales para almacenamiento y recuperación eficiente de información.**

- **Garantizar seguridad y facilidad de uso con tunelización segura y configuración personalizable.**

La aplicación combina potencia y simplicidad para habilitar a desarrolladores, investigadores y usuarios finales en la creación de soluciones basadas en inteligencia artificial.

## Características Principales

1. **Framework Principal**: 
   - **Python puro** junto con **Streamlit** para la interfaz de usuario amigable.

2. **Bases de Datos**:
   - **Firebase**: Para almacenar validaciones de correos electrónicos en la página de cuentas.
   - **Chromadb**: Bases de datos vectoriales que almacenan embeddings representados como vectores numéricos.

3. **Modelos**:
   - **Embeddings de OpenAI**: Base de datos vectorial para embeddings generados por OpenAI.
   - **Embeddings de Ollama**: Embeddings generados por modelos locales de Ollama.

4. 🔒 **Tunelización Segura**:
   - **Ngrok**: Creación de un túnel seguro (puerto `4040`) para compartir la aplicación sin vulnerabilidades.

5. **Selector de Modelos**:
   - **Opción para elegir entre:**
     - OpenAI
     - Grok
     - Modelos locales personalizados.

6. **Personalización**:
   - **Actualización sencilla del token de Ngrok** en `ngrok.yml`.
   - **Selección de modelo predeterminado** desde el archivo `.env`.

## Instalación

1. **Configurar variables de entorno:**
   - Editar archivo `.env` con el siguiente contenido:
     ```env
     MODEL_LIST=llama3.2,llama3,mistral,tinyllama,phi3,llama2,brxce/stable-diffusion-prompt-generator,gemma2:2b
     ```

2. **Configurar Ngrok:**
   - Editar el archivo `ngrok.yml` con tu token:
     ```yaml
     authtoken: YOUR_NGROK_TOKEN
     ```
