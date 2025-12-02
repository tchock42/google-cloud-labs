# Cloud Speech-to-Text API: Qwik Start (GSP119)

## 🎯 Objetivo
Aprender a usar la **Cloud Speech-to-Text API** para transcribir archivos de audio en texto, aplicando reconocimiento automático de voz.

---

## 🛠️ Pasos principales

1. **Configurar entorno**
   - Activar la API:
     ```bash
     gcloud services enable speech.googleapis.com
     ```
   - Verificar proyecto activo:
     ```bash
     gcloud config list project
     ```

2. **Preparar archivo de audio**
   - Subir un archivo `.wav` o `.flac` a Cloud Storage:
     ```bash
     gsutil cp audio_sample.flac gs://my-speech-bucket-jacob/
     ```

3. **Instalar cliente de Python**
   ```bash
   pip install google-cloud-speech

4. **Crear script de transcripción**
- Archivo transcribe.py:
  ```bash
  from google.cloud import speech_v1p1beta1 as speech

  client = speech.SpeechClient()

  gcs_uri = "gs://my-speech-bucket-jacob/audio_sample.flac"

  audio = speech.RecognitionAudio(uri=gcs_uri)
  config = speech.RecognitionConfig(
    encoding=speech.RecognitionConfig.AudioEncoding.FLAC,
    sample_rate_hertz=16000,
    language_code="es-ES"
  )

  response = client.recognize(config=config, audio=audio)

  for result in response.results:
    print("Transcripción:", result.alternatives[0].transcript)
  ```
  5. **Ejecutar el script**
  ```bash
  python transcribe.py
  ```
- Resultado: texto transcrito del archivo de audio.
## 🔐 Buenas prácticas aplicadas
- Uso de Cloud Storage para manejar archivos de audio grandes.
- Configuración explícita de encoding, sample_rate y language_code para mejorar precisión.
- Separación clara de configuración y ejecución en el script.
## 📊 Resultado
Se transcribió un archivo de audio en texto usando la Cloud Speech-to-Text API, mostrando cómo convertir voz en datos estructurados.💡 ReflexiónEste lab demuestra cómo aplicar reconocimiento de voz en la nube para convertir audio en texto.
Es aplicable a proyectos de chatbots, asistentes virtuales, análisis de llamadas y accesibilidad, reforzando tu perfil en IA aplicada y automatización cloud.
## 💡 Reflexión
Este lab demuestra cómo aplicar reconocimiento de voz en la nube para convertir audio en texto.
Es aplicable a proyectos de chatbots, asistentes virtuales, análisis de llamadas y accesibilidad, reforzando tu perfil en IA aplicada y automatización cloud.
---
