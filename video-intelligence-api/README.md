# Video Intelligence API: Qwik Start (GSP154)

## 🎯 Objetivo
Aprender a usar la **Cloud Video Intelligence API** para analizar videos, detectando etiquetas, escenas y objetos relevantes.

---

## 🛠️ Pasos principales

1. **Configurar entorno**
   - Activar la API:
     ```bash
     gcloud services enable videointelligence.googleapis.com
     ```
   - Verificar proyecto activo:
     ```bash
     gcloud config list project
     ```

2. **Preparar archivo de video**
   - Subir un video a Cloud Storage:
     ```bash
     gsutil cp sample-video.mp4 gs://my-video-bucket-jacob/
     ```

3. **Instalar cliente de Python**
   ```bash
   pip install google-cloud-videointelligence

4. **Crear script de análisis**
- Archivo analyze_video.py:
  ```bash
    from google.cloud import videointelligence_v1 as videointelligence

    client = videointelligence.VideoIntelligenceServiceClient()
    
    gcs_uri = "gs://my-video-bucket-jacob/sample-video.mp4"
    
    features = [videointelligence.Feature.LABEL_DETECTION]
    
    operation = client.annotate_video(
        request={"features": features, "input_uri": gcs_uri}
    )
    
    print("Procesando video...")
    result = operation.result(timeout=300)
    
    for i, annotation_result in enumerate(result.annotation_results):
        for label in annotation_result.segment_label_annotations:
            print(f"Etiqueta: {label.entity.description}")
            for segment in label.segments:
                start = segment.segment.start_time_offset
                end = segment.segment.end_time_offset
                print(f"  Segmento: {start.seconds}s - {end.seconds}s")
  ```
5. **Ejecutar el script**
  ```bash
  python analyze_video.py
  ```
- Resultado: etiquetas detectadas en el video y los segmentos donde aparecen.
## 🔐 Buenas prácticas aplicadas
- Uso de Cloud Storage para manejar videos grandes.
- Configuración explícita de features (ej. LABEL_DETECTION) para modular análisis.
- Separación clara de carga de datos y procesamiento.
- Control de tiempo de espera (timeout) para videos largos.
## 📊 Resultado
Se analizó un video con la Video Intelligence API, obteniendo etiquetas y segmentos donde aparecen objetos o escenas relevantes.
## 💡 Conclusión
Este lab demuestra cómo aplicar IA en video para extraer información útil de contenido multimedia.
Es aplicable a proyectos de análisis de medios, indexación de videos, seguridad y sistemas inteligentes, reforzando tu perfil en IA aplicada en la nube.
---

¿Quieres que te prepare también una **tabla comparativa entre las tres APIs (NLP, Speech-to-Text y Video Intelligence)** para tu README principal, para que quede claro tu dominio de IA multimodal en Google Cloud?

