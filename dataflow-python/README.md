# Dataflow: Qwik Start - Python (GSP207)

## 🎯 Objetivo
Aprender a crear un pipeline básico con **Apache Beam (Python SDK)** y ejecutarlo en **Cloud Dataflow**, procesando datos de entrada y escribiendo resultados en Cloud Storage.

---

## 🛠️ Pasos principales

1. **Configurar entorno**
   - Activar APIs necesarias:
     ```bash
     gcloud services enable dataflow.googleapis.com
     gcloud services enable storage.googleapis.com
     ```
   - Crear un bucket de Cloud Storage para staging y resultados:
     ```bash
     gsutil mb -l us-central1 gs://my-dataflow-bucket-jacob/
     ```

2. **Instalar dependencias**
   - En Cloud Shell:
     ```bash
     pip install apache-beam[gcp]
     ```

3. **Crear pipeline en Python**
   - Archivo `wordcount.py`:
     ```python
     import apache_beam as beam
     from apache_beam.options.pipeline_options import PipelineOptions

     options = PipelineOptions(
         runner='DataflowRunner',
         project='YOUR_PROJECT_ID',
         temp_location='gs://my-dataflow-bucket-jacob/temp',
         region='us-central1'
     )

     with beam.Pipeline(options=options) as p:
         (p
          | 'ReadInput' >> beam.io.ReadFromText('gs://dataflow-samples/shakespeare/kinglear.txt')
          | 'SplitWords' >> beam.FlatMap(lambda line: line.split())
          | 'PairWithOne' >> beam.Map(lambda word: (word, 1))
          | 'CountWords' >> beam.CombinePerKey(sum)
          | 'FormatResults' >> beam.Map(lambda wc: f"{wc[0]}: {wc[1]}")
          | 'WriteOutput' >> beam.io.WriteToText('gs://my-dataflow-bucket-jacob/output/result'))
     ```

4. **Ejecutar el pipeline**
   ```bash
   python wordcount.py

5. Ver resultados
- Revisar en Cloud Storage:
  ```bash
  gsutil cat gs://my-dataflow-bucket-jacob/output/result-00000-of-00001
  ```
- Verificar que aparecen las palabras y sus conteos.

🔐 Buenas prácticas aplicadas
- Uso de bucket dedicado para staging y resultados.
- Separación de pasos en el pipeline con nombres descriptivos.
- Configuración explícita de región y proyecto para evitar errores.
- Uso de DataflowRunner para escalar automáticamente el procesamiento.

📊 Resultado
Se creó y ejecutó un pipeline de WordCount en Dataflow usando Apache Beam en Python. Los resultados se almacenaron en Cloud Storage, mostrando el conteo de palabras del archivo de entrada.

💡 Reflexión
Este lab demuestra cómo implementar pipelines de datos escalables y distribuidos en Google Cloud.
Es aplicable a proyectos de ETL, procesamiento de logs, análisis de texto y flujos de datos en tiempo real, reforzando tu perfil en data engineering y cloud automation.

---

## 📌 Cómo presentarlo en LinkedIn
Ejemplo de publicación:

> 📊 Hoy completé el lab **Dataflow: Qwik Start – Python (GSP207)** en Google Cloud.  
> Aprendí a crear un pipeline con Apache Beam y ejecutarlo en Dataflow, procesando datos de forma escalable.  
> Documenté el proceso en mi GitHub 👉 [enlace al repo]  
> Este conocimiento es clave para proyectos de **data engineering y pipelines en la nube**. 🚀  

---

👉 Te sugiero que este lab lo pongas en tu índice bajo la sección **“Data Engineering y Pipelines”**, junto con **Pub/Sub** y **BigQuery**, para mostrar un bloque sólido de **procesamiento de datos en la nube**.  

¿Quieres que te prepare también la documentación del **lab GSP190: Streaming Dataflow – Python** para complementar este y mostrar que dominas tanto pipelines batch como streaming?


