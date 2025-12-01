# Cloud Run Functions: Qwik Start - Línea de Comandos (GSP080)

## 🎯 Objetivo
Aprender a crear y desplegar una **Cloud Function** en Google Cloud usando la línea de comandos (`gcloud`), y exponerla vía **Cloud Run Functions** de manera serverless.

---

## 🛠️ Pasos principales

1. **Configurar proyecto y región**
   ```bash
   gcloud config set project <PROJECT_ID>
   gcloud config set functions/region us-central1

2. Crear el código de la función
- Crear archivo index.js:
  ```javascript
    exports.helloWorld = (req, res) => {
      res.send("¡Hola desde Cloud Run Functions!");
    };

- Crear archivo package.json:
  ```bash
  {
    "name": "hello-world",
    "version": "1.0.0",
    "dependencies": {}
  }

3. Desplegar la función
  ```bash
    gcloud functions deploy helloWorld \
      --runtime nodejs18 \
      --trigger-http \
      --allow-unauthenticated
  ```
4. Obtener la URL de la función
   ```bash
   gcloud functions describe helloWorld --region us-central1

- Copiar la URL pública y probar con:
  ```bash
  curl https://REGION-PROJECT_ID.cloudfunctions.net/helloWorld
##🔐 Buenas prácticas aplicadas
- Uso de --allow-unauthenticated solo en entornos de prueba; en producción se recomienda IAM o API Gateway.
- Separación clara de código (index.js) y dependencias (package.json).
- Configuración explícita de región para evitar despliegues accidentales en zonas no deseadas.

##📊 Resultado
Se desplegó una Cloud Function en Google Cloud que responde a solicitudes HTTP con un mensaje simple. La función corre en un entorno serverless, escalando automáticamente según la demanda.

##💡 Conclusiones
Este lab demuestra cómo crear y desplegar funciones ligeras en la nube usando la CLI.
Es aplicable a proyectos de APIs rápidas, microservicios, automatización de tareas y procesamiento de eventos, reforzando tu perfil en arquitecturas modernas y seguras.
---
