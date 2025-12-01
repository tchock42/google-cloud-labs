# Mejora la confiabilidad y la escalabilidad de las aplicaciones con el Balanceo de cargas interno (GSP216)

## 🎯 Objetivo
Configurar un **Internal TCP/UDP Load Balancer** en Google Cloud para distribuir tráfico entre instancias dentro de una VPC, mejorando la confiabilidad y escalabilidad de aplicaciones internas.

---

## 🛠️ Pasos principales

1. **Configurar región y zona por defecto**
   ```bash
   gcloud config set compute/region us-central1
   gcloud config set compute/zone us-central1-a


2. **Crear una VPC personalizada
  ```bash
  gcloud compute networks create internal-vpc --subnet-mode=custom
  gcloud compute networks subnets create internal-subnet \
  --network=internal-vpc \
  --range=10.0.0.0/24 \
  --region=us-central1
  ```
3. **Crear instancias de backend
- Crear dos VMs dentro de la subred:
  ```bash
  gcloud compute instances create backend-1 \
  --zone=us-central1-a \
  --subnet=internal-subnet \
  --tags=internal-backend
  
  gcloud compute instances create backend-2 \
  --zone=us-central1-b \
  --subnet=internal-subnet \
  --tags=internal-backend
  ```
- Instalar un servicio simple (ej. servidor HTTP en puerto 80).
4. **Configurar reglas de firewall
- Permitir tráfico interno en puerto 80:
  ```bash
  gcloud compute firewall-rules create allow-internal-http \
  --network=internal-vpc \
  --allow tcp:80 \
  --source-ranges=10.0.0.0/24 \
  --target-tags=internal-backend
  ```
5. **Crear el balanceador interno
- Crear un backend service con las instancias.
- Crear un forwarding rule interno con IP privada:
  ```bash
  gcloud compute forwarding-rules create internal-lb-rule \
  --region us-central1 \
  --ports 80 \
  --address <INTERNAL_IP> \
  --backend-service internal-backend-service \
  --subnet internal-subnet
  ```
6. **Probar el balanceador
- Crear una VM cliente dentro de la misma VPC.
- Desde esa VM, ejecutar:
  ```bash
  curl http://<INTERNAL_IP>
  ```
- Verificar que el tráfico se distribuye entre backend-1 y backend-2.

## 🔐 Buenas prácticas aplicadas
- Uso de IP interna para evitar exposición pública.
- Configuración de firewall con rangos internos específicos.
- Separación clara de frontend (forwarding rule) y backend (instance group).
- Ideal para microservicios internos y aplicaciones empresariales seguras.

## 📊 Resultado
Se configuró un Internal TCP/UDP Load Balancer que distribuye tráfico entre dos instancias dentro de la misma VPC. El balanceador responde en una IP privada y reparte las solicitudes de forma automática.

## 💡 Reflexión
Este lab demuestra cómo implementar alta disponibilidad y escalabilidad interna en Google Cloud.
Es aplicable a arquitecturas de microservicios, aplicaciones internas y sistemas corporativos que requieren balanceo seguro sin exposición a internet.
