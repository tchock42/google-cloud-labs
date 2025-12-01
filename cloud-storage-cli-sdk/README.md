# Cloud Storage: Qwik Start - CLI/SDK (GSP074)

## 🎯 Objetivo
Aprender a crear buckets de Cloud Storage, subir y administrar objetos usando la **CLI (`gsutil`)** y el **SDK de Google Cloud**.

---

## 🛠️ Pasos principales

1. **Configurar proyecto y autenticación**
   - Verificar que el proyecto está activo:
     ```bash
     gcloud config list project
     ```
   - Autenticarse en Cloud Shell:
     ```bash
     gcloud auth list
     ```

2. **Crear un bucket**
   - Usar `gsutil` para crear un bucket único:
     ```bash
     gsutil mb -l us-central1 gs://my-bucket-jacob/
     ```
   - Parámetros:
     - `-l`: región (ej. `us-central1`)
     - Nombre único global: `gs://my-bucket-jacob/`

3. **Subir objetos al bucket**
   - Crear un archivo de prueba:
     ```bash
     echo "Hola desde Cloud Storage!" > test.txt
     ```
   - Subirlo:
     ```bash
     gsutil cp test.txt gs://my-bucket-jacob/
     ```

4. **Listar y descargar objetos**
   - Listar contenido:
     ```bash
     gsutil ls gs://my-bucket-jacob/
     ```
   - Descargar archivo:
     ```bash
     gsutil cp gs://my-bucket-jacob/test.txt .
     ```

5. **Usar el SDK (Python ejemplo)**
   - Instalar librería:
     ```bash
     pip install google-cloud-storage
     ```
   - Código básico:
     ```python
     from google.cloud import storage

     client = storage.Client()
     bucket = client.get_bucket("my-bucket-jacob")
     blob = bucket.blob("test.txt")
     blob.download_to_filename("downloaded_test.txt")
     print("Archivo descargado con éxito!")
     ```

---

## 🔐 Buenas prácticas aplicadas
- Uso de **nombres únicos de bucket** para evitar conflictos globales.  
- Autenticación segura con `gcloud auth`.  
- Separación de responsabilidades entre CLI (operaciones rápidas) y SDK (automatización).  

---

## 📊 Resultado
Se creó un bucket en Cloud Storage, se subieron y descargaron objetos usando `gsutil`, y se probó el acceso mediante el SDK de Python.

---

## 💡 Reflexión
Este lab demuestra cómo integrar **almacenamiento en la nube** en flujos de trabajo automatizados.  
Es aplicable a proyectos de **backup, hosting de archivos estáticos, y pipelines de datos**, reforzando tu perfil en **automatización y APIs seguras**.
