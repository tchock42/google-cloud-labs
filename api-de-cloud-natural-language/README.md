# Cloud Natural Language API: Qwik Start (GSP097)

## 🎯 Objetivo
Aprender a usar la **Cloud Natural Language API** para analizar texto, extrayendo entidades, sentimientos y estructura sintáctica.

---

## 🛠️ Pasos principales

1. **Configurar entorno**
   - Activar la API:
     ```bash
     gcloud services enable language.googleapis.com
     ```
   - Verificar proyecto activo:
     ```bash
     gcloud config list project
     ```

2. **Instalar cliente de Python**
   ```bash
   pip install google-cloud-language

3. Crear script de análisis
- Archivo analyze.py:
  ```bash
  from google.cloud import language_v1
  
  client = language_v1.LanguageServiceClient()
  
  text = "Google Cloud ofrece servicios escalables y seguros."
  document = {"content": text, "type_": language_v1.Document.Type.PLAIN_TEXT}
  
  # Análisis de entidades
  entities = client.analyze_entities(request={"document": document})
  for entity in entities.entities:
      print(f"Entidad: {entity.name}, Tipo: {entity.type_}")
  
  # Análisis de sentimiento
  sentiment = client.analyze_sentiment(request={"document": document})
  print(f"Sentimiento: score={sentiment.document_sentiment.score}, magnitude={sentiment.document_sentiment.magnitude}")
  ```
4. Ejecutar el script
  ```bash
  python analyze.py
  ```
- Resultado: lista de entidades detectadas y análisis de sentimiento del texto.
# 🔐 Buenas prácticas aplicadas- Uso de Document.Type.PLAIN_TEXT para asegurar formato correcto.
- Separación de análisis de entidades y sentimiento.
- Configuración explícita de proyecto y API para evitar errores.
# 📊 Resultado
Se analizó un texto con la Cloud Natural Language API, obteniendo entidades clave y sentimiento asociado.
#💡 ReflexiónEste lab demuestra cómo aplicar NLP en la nube para extraer información útil de texto.
Es aplicable a proyectos de chatbots, análisis de reseñas, clasificación de documentos y sistemas inteligentes, reforzando tu perfil en IA aplicada y automatización cloud.
---
