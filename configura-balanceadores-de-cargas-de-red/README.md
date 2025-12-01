# Configuración de Balanceadores de Carga de Red (GSP007)

## 🎯 Objetivo
Aprender a configurar un **Network Load Balancer (NLB)** en Google Cloud para distribuir tráfico TCP/UDP entre múltiples instancias de VM.  
Un NLB opera en **capa 4 (L4)**, manejando tráfico según IP y puertos sin inspeccionar el contenido.

---

## 🛠️ Pasos principales
1. **Configurar región y zona por defecto**
   ```bash
   gcloud config set compute/region us-central1
   gcloud config set compute/zone us-central1-a

2. **Crear múltiples instancias de servidor web
- Crear dos VMs con Apache/Nginx instalados.
- Ejemplo:
  ```bash
  gcloud compute instances create www1 --zone=us-central1-a --tags=web
  gcloud compute instances create www2 --zone=us-central1-b --tags=web
- Instalar servidor web y configurar página de prueba en cada VM

3. **Configurar el servicio de balanceo
- Crear un target pool que agrupe las instancias:
  ```bash
  gcloud compute target-pools create www-pool --region us-central1 --instances www1,www2
4. **Crear regla de reenvío (forwarding rule)
- Asignar una IP externa y redirigir tráfico al pool:
  ```bash
  gcloud compute forwarding-rules create www-rule \
  --region us-central1 \
  --ports 80 \
  --target-pool www-pool
  
5. **Probar el balanceador
- Obtener la IP externa de la regla:
  ```bash
  gcloud compute forwarding-rules describe www-rule --region us-central1

- Acceder vía navegador o curl y verificar que el tráfico se distribuye entre www1 y www2.

##🔐 Buenas prácticas aplicadas
- Uso de instancias en diferentes zonas para alta disponibilidad.
- Configuración de firewall rules para permitir tráfico HTTP (puerto 80).
- Separación de roles y etiquetas para administración clara.

##📊 Resultado
Se configuró un Network Load Balancer que distribuye tráfico HTTP entre dos instancias de VM en distintas zonas. El balanceador responde en una IP externa y reparte las solicitudes de forma automática.

##💡 Configuración
Este lab demuestra cómo implementar alta disponibilidad y escalabilidad en Google Cloud usando balanceo de carga en capa 4.
Es aplicable a proyectos que requieren distribuir tráfico de red de manera eficiente, como aplicaciones web, APIs y servicios backend.

---

