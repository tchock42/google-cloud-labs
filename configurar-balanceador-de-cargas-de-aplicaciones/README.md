# Configuración de Balanceadores de Carga de Aplicaciones (GSP155)

## 🎯 Objetivo
Aprender a configurar un **HTTP(S) Load Balancer** en Google Cloud para distribuir tráfico web entre múltiples instancias de backend, con soporte para reglas de contenido y certificados SSL.

---

## 🛠️ Pasos principales

1. **Configurar región y zona por defecto**
   ```bash
   gcloud config set compute/region us-central1
   gcloud config set compute/zone us-central1-a

2. **Crear instancias de backend
- Crear dos VMs con Apache/Nginx instalados y páginas de prueba distintas.
- Ejemplo:
  ```
  gcloud compute instances create app1 --zone=us-central1-a --tags=http-server
  gcloud compute instances create app2 --zone=us-central1-b --tags=http-server
- Configurar firewall para permitir tráfico HTTP (puerto 80):
  ```
  gcloud compute firewall-rules create allow-http --allow tcp:80 --target-tags=http-server
  
3. Configurar un grupo de instancias (backend service)
- Crear un instance group y añadir las VMs.
- Asociar el grupo a un backend service con protocolo HTTP.
  
4. Configurar el frontend (URL map y proxy)
- Crear un URL map que dirija tráfico al backend service.
- Crear un target HTTP proxy asociado al URL map.
- Crear una global forwarding rule que asigne una IP pública al proxy:
  ```bash
  gcloud compute forwarding-rules create http-rule \
  --global \
  --target-http-proxy http-lb-proxy \
  --ports 80


5. Probar el balanceador
- Obtener la IP externa de la regla:
  ```
  gcloud compute forwarding-rules describe http-rule --global
- Acceder vía navegador o curl y verificar que el tráfico se distribuye entre app1 y app2.

##🔐 Buenas prácticas aplicadas
- Uso de instancias en diferentes zonas para alta disponibilidad.
- Configuración de firewall rules específicas para HTTP.
- Separación clara de frontend (proxy, URL map) y backend (instance group).
- Posibilidad de añadir certificados SSL para tráfico seguro (HTTPS).

##📊 Resultado
Se configuró un HTTP(S) Load Balancer global que distribuye tráfico web entre dos instancias de VM. El balanceador responde en una IP externa y reparte las solicitudes de forma automática, con capacidad de escalar y añadir reglas de contenido.

##💡 Conclusiones
Este lab demuestra cómo implementar alta disponibilidad y escalabilidad en capa 7, aplicable a aplicaciones web modernas, APIs y servicios que requieren balanceo inteligente según contenido.
Es un paso clave hacia arquitecturas resilientes y seguras en la nube.
