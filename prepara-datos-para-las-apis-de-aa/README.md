# APIs de Inteligencia Artificial en Google Cloud: Lab de desafío (GSP323)

## 🎯 Objetivo
Integrar múltiples **APIs de AI/ML de Google Cloud** en un flujo de trabajo, aplicando visión, lenguaje y traducción para resolver un reto práctico.

---

## 🛠️ Pasos principales

1. **Configurar entorno**
   - Activar APIs necesarias:
     ```bash
     gcloud services enable vision.googleapis.com
     gcloud services enable translate.googleapis.com
     gcloud services enable language.googleapis.com
     ```
   - Crear bucket en Cloud Storage para subir archivos de prueba:
     ```bash
     gsutil mb -l us-central1 gs://my-ai-bucket-jacob/
     ```

2. **Usar la API de Vision**
   - Subir una imagen al bucket.
   - Ejecutar detección de etiquetas:
     ```bash
     gcloud ml vision detect-labels gs://my-ai-bucket-jacob/image.jpg
     ```
   - Resultado: lista de objetos/entidades detectadas en la imagen.

3. **Usar la API de Natural Language**
   - Crear archivo `text.txt` con una descripción.
   - Analizar sentimiento y entidades:
     ```bash
     gcloud ml language analyze-entities --content="El servicio es rápido y confiable"
     gcloud ml language analyze-sentiment --content="El servicio es rápido y confiable"
     ```
   - Resultado: entidades clave y polaridad del texto.

4. **Usar la API de Translate**
   - Traducir texto detectado:
     ```bash
     gcloud ml translate text "El servicio es rápido y confiable" --target=en
     ```
   - Resultado: traducción al inglés.

5. **Integrar flujo completo**
   - Imagen → etiquetas con Vision.  
   - Texto → análisis con Natural Language.  
   - Texto → traducción con Translate.  
   - Documentar resultados en Cloud Storage o en consola.

---

## 🔐 Buenas prácticas aplicadas
- Activación selectiva de APIs para evitar costos innecesarios.  
- Uso de **Cloud Storage** como repositorio central de datos.  
- Separación clara de cada API para modularidad.  
- Ejemplo de integración de **visión, lenguaje y traducción** en un solo flujo.  

---

## 📊 Resultado
Se completó un flujo de desafío que integra **Vision API, Natural Language API y Translate API**.  
El sistema detecta objetos en imágenes, analiza texto y traduce resultados, mostrando cómo combinar servicios de AI en Google Cloud.

---

## 💡 Conclusión
Este lab demuestra cómo **integrar múltiples APIs de AI** en un flujo práctico.  
Es aplicable a proyectos de **automatización, análisis de contenido multimedia, chatbots multilingües y sistemas inteligentes**, reforzando tu perfil en **IA aplicada en la nube**.
