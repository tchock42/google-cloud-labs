# Dataflow: Qwik Start - Plantillas (GSP192)

## 🎯 Objetivo
Aprender a ejecutar un pipeline de **Dataflow** usando una **plantilla predefinida**, procesando datos de entrada y escribiendo resultados en Cloud Storage sin necesidad de programar.

---

## 🛠️ Pasos principales

1. **Configurar entorno**
   - Activar APIs necesarias:
     ```bash
     gcloud services enable dataflow.googleapis.com
     gcloud services enable storage.googleapis.com
     ```
   - Crear bucket de Cloud Storage para staging y resultados:
     ```bash
     gsutil mb -l us-central1 gs://my-dataflow-template-bucket-jacob/
     ```

2. **Seleccionar una plantilla predefinida**
   - Ejemplo: **WordCount** (conteo de palabras).
   - Plantilla: `gs://dataflow-templates/latest/Word_Count`

3. **Ejecutar la plantilla con gcloud**
   ```bash
   gcloud dataflow jobs run wordcount-job \
     --gcs-location gs://dataflow-templates/latest/Word_Count \
     --region us-central1 \
     --parameters \
       inputFile=gs://dataflow-samples/shakespeare/kinglear.txt,\
       output=gs://my-dataflow-template-bucket-jacob/output/result
4. Monitorea el job
   - Ir a Dataflow → Jobs en la consola.
   - Verificar estado del pipeline y progreso de tareas

5. Ver resultados
   - Revisa en cloud storage
   ```bashg
   sutil cat gs://my-dataflow-template-bucket-jacob/output/result-00000-of-00001
   ```
## 🔐 Buenas prácticas aplicadas- Uso de plantillas predefinidas para acelerar despliegues.
- Separación de staging y resultados en buckets dedicados.
- Configuración explícita de región para evitar costos inesperados.
- Eliminación de recursos al finalizar para optimizar gastos.
📊 ResultadoSe ejecutó un pipeline de WordCount en Dataflow usando una plantilla predefinida. Los resultados se almacenaron en Cloud Storage, mostrando el conteo de palabras del archivo de entrada.💡 ReflexiónEste lab demuestra cómo aprovechar plantillas de Dataflow para ejecutar pipelines sin escribir código.
Es aplicable a proyectos de ETL, análisis de logs y procesamiento batch, reforzando tu perfil en data engineering y automatización cloud.
---
