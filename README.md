# Proyecto: Plataforma con Python, Streamlit y Bases de Datos Vectoriales

## Descripción General
Este proyecto es una aplicación diseñada para ofrecer una interfaz amigable para gestionar modelos de IA y bases de datos vectoriales. La aplicación utiliza un enfoque modular y seguro para integrar componentes como validación de correo electrónico, almacenamiento de datos vectoriales, y selección de modelos de machine learning.



## Características Principales

1. **Framework Principal**: 
   - Se utiliza **Python puro** junto con **Streamlit** para la interfaz de usuario amigable.

2. **Bases de Datos**:
   - **Firebase**: Para almacenar validaciones de correos electrónicos en la página de cuentas.
   - **Chromadb**: Para bases de datos vectoriales que almacenan embeddings representados como vectores numéricos.

3. **Modelos**:
   - **Embeddings de OpenAI**: Base de datos vectorial para embeddings generados por OpenAI.
   - **Embeddings de Ollama**: Embeddings generados por modelos locales de Ollama.

4. **Tunelización Segura**:
   - **Ngrok**: Creación de un túnel seguro (puerto `4040`) para compartir la aplicación sin vulnerabilidades.

5. **Selector de Modelos**:
   - Opción para elegir entre:
     - OpenAI
     - Grok
     - Modelos locales personalizados.

6. **Personalización**:
   - Actualización sencilla del token de Ngrok en `ngrok.yml`.
   - Selección de modelo predeterminado desde el archivo `.env`.

## Instalación

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/tu-repo/tu-proyecto.git
   cd tu-proyecto
   ```

2. Crear un entorno virtual e instalar dependencias:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. Configurar variables de entorno:
   - Crear un archivo `.env`:
     ```env
     MODEL_LIST=llama3.2,llama3,mistral,tinyllama,phi3,llama2,brxce/stable-diffusion-prompt-generator,gemma2:2b
     ```

4. Configurar Ngrok:
   - Editar el archivo `ngrok.yml` para incluir tu token:
     ```yaml
     authtoken: TU_NGROK_TOKEN
     ```

## Uso

