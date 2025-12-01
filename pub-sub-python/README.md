# Pub/Sub: Qwik Start - Python (GSP094)

## 🎯 Objetivo
Aprender a crear un **topic** y una **subscription** en Pub/Sub, publicar mensajes desde Python y recibirlos de forma asíncrona.

---

## 🛠️ Pasos principales

1. **Configurar proyecto y entorno**
   - Verificar proyecto activo:
     ```bash
     gcloud config list project
     ```
   - Activar APIs necesarias:
     ```bash
     gcloud services enable pubsub.googleapis.com
     ```

2. **Crear un topic y una suscripción**
   ```bash
   gcloud pubsub topics create my-topic
   gcloud pubsub subscriptions create my-sub --topic my-topic

3. **Instalar librería de Pub/Sub para Python
  ```bash
  pip install google-cloud-pubsub
  ````

4. **Publicar mensajes (publisher.py)
```bash
from google.cloud import pubsub_v1

project_id = "YOUR_PROJECT_ID"
topic_id = "my-topic"

publisher = pubsub_v1.PublisherClient()
topic_path = publisher.topic_path(project_id, topic_id)

data = "Hola desde Pub/Sub!".encode("utf-8")
future = publisher.publish(topic_path, data)
print(f"Mensaje publicado: {future.result()}")
```
5. **Recibir mensajes (subscriber.py)
```bash
from google.cloud import pubsub_v1

project_id = "YOUR_PROJECT_ID"
subscription_id = "my-sub"

subscriber = pubsub_v1.SubscriberClient()
subscription_path = subscriber.subscription_path(project_id, subscription_id)

def callback(message):
    print(f"Mensaje recibido: {message.data.decode('utf-8')}")
    message.ack()

streaming_pull_future = subscriber.subscribe(subscription_path, callback=callback)
print(f"Escuchando mensajes en {subscription_path}...")

with subscriber:
    try:
        streaming_pull_future.result()
    except KeyboardInterrupt:
        streaming_pull_future.cancel()
```

6. **Probar flujo completo
- Ejecutar publisher.py para enviar mensajes.
- Ejecutar subscriber.py para recibirlos en tiempo real.

## 🔐 Buenas prácticas aplicadas
- Uso de acknowledgement (message.ack()) para evitar reprocesamiento.
- Separación de responsabilidades entre publisher y subscriber.
- Configuración explícita de proyecto y recursos para evitar errores de contexto.

## 📊 Resultado
Se creó un topic y una subscription en Pub/Sub, se publicaron mensajes desde Python y se recibieron de manera asíncrona con callbacks.

## 💡 Reflexión
Este lab demuestra cómo implementar comunicación asíncrona y desacoplada entre servicios en Google Cloud.
Es aplicable a arquitecturas de microservicios, pipelines de datos y sistemas event-driven, reforzando tu perfil en integración y automatización cloud.

---
