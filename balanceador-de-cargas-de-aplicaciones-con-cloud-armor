Documentación del Lab GSP215 – Balanceador de cargas de aplicaciones con Cloud Armor
# Balanceador de cargas de aplicaciones con Cloud Armor (GSP215)

## 🎯 Objetivo
Aprender a configurar un **HTTP(S) Load Balancer** en Google Cloud y protegerlo con **Cloud Armor**, aplicando políticas de seguridad para mitigar ataques y controlar accesos.

## 🛠️ Pasos principales

1. **Configurar región y zona por defecto**
   ```bash
   gcloud config set compute/region us-central1
   gcloud config set compute/zone us-central1-a

2. **Crear instancias de backend
 - Crear dos VMs con Apache/Nginx y páginas de prueba distintas:
 ```bash
  gcloud compute instances create app1 --zone=us-central1-a --tags=http-server
  gcloud compute instances create app2 --zone=us-central1-b --tags=http-server
  ```
3. **Configurar firewall para permitir tráfico HTTP:
  ```bash
  gcloud compute firewall-rules create allow-http \
  --allow tcp:80 \
  --target-tags=http-server
  ```
3. **Configurar el Load Balancer
- Crear un instance group con las VMs.
- Crear un backend service asociado al grupo.
- Crear un URL map y un target HTTP proxy.
- Crear una global forwarding rule para exponer el balanceador:
  ```bash
  gcloud compute forwarding-rules create http-rule \
  --global \
  --target-http-proxy http-lb-proxy \
  --ports 80
  ```
4. **Configurar políticas de Cloud Armor
- Crear una política de seguridad:
  ```bash
  gcloud compute security-policies create my-security-policy \
  --description "Política de protección contra ataques comunes"
  ```
- Añadir reglas de protección:
  - Bloquear tráfico de una IP específica:
  ```bash
  gcloud compute security-policies rules create 1000 \
  --security-policy my-security-policy \
  --src-ip-ranges=203.0.113.0/24 \
  --action=deny-403
  ```
- Permitir tráfico legítimo:
  ```bash
  gcloud compute security-policies rules create 2000 \
  --security-policy my-security-policy \
  --action=allow
  ```
5. **Asociar la política al backend service
  ```bash
  gcloud compute backend-services update my-backend-service \
  --security-policy=my-security-policy \
  --global
  ```

6. **Probar el balanceador con Cloud Armor
- Acceder a la IP externa del Load Balancer.
- Verificar que tráfico legítimo pasa y tráfico bloqueado recibe error 403.

##🔐 Buenas prácticas aplicadas
- Uso de Cloud Armor para mitigar ataques DDoS y aplicar reglas de seguridad.
- Configuración de deny rules específicas para IPs sospechosas.
- Principio de menor privilegio en firewall y políticas.
- Separación clara entre infraestructura (Load Balancer) y seguridad (Cloud Armor).

## 📊 Resultado
Se configuró un HTTP(S) Load Balancer protegido con Cloud Armor, capaz de distribuir tráfico entre instancias y aplicar políticas de seguridad para bloquear accesos maliciosos.

## 💡 Conclusiones
Este lab demuestra cómo combinar alta disponibilidad y seguridad en Google Cloud.
Es aplicable a proyectos de aplicaciones web, APIs y microservicios que requieren balanceo global con protección avanzada contra ataques.
