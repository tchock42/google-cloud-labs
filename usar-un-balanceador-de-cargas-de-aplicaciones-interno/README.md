# Configuración de Balanceadores de Carga de Aplicaciones Interno (GSP041)

## 🎯 Objetivo
Aprender a configurar un **Internal HTTP(S) Load Balancer** en Google Cloud para distribuir tráfico web entre instancias dentro de una VPC, sin exponer el servicio públicamente.

---

## 🛠️ Pasos principales

1. **Configurar región y zona por defecto**
```bash
gcloud config set compute/region us-central1
gcloud config set compute/zone us-central1-a
```  
2. **Crear instancias de backend
- Crear dos VMs con Apache/Nginx instalados y páginas de prueba distintas.
- Ejemplo:
```bash
gcloud compute instances create internal-app1 --zone=us-central1-a --tags=internal-http
gcloud compute instances create internal-app2 --zone=us-central1-b --tags=internal-http
```

- Configurar firewall para permitir tráfico HTTP interno:
```bash
gcloud compute firewall-rules create allow-internal-http \
  --allow tcp:80 \
  --source-ranges 10.128.0.0/20 \
  --target-tags=internal-http
```
3. **Crear grupo de instancias (backend service)
- Crear un instance group y añadir las VMs.
- Asociar el grupo a un backend service con protocolo HTTP.

4. **Configurar frontend interno
- Crear un URL map que dirija tráfico al backend service.
- Crear un target HTTP proxy asociado al URL map.
- Crear una forwarding rule interna con IP privada:
  
```bash
gcloud compute forwarding-rules create internal-http-rule \
--region us-central1 \
--ports 80 \
--address <INTERNAL_IP> \
--target-http-proxy internal-http-proxy \
--subnet default
```

5. Probar el balanceador
- Crear una VM cliente dentro de la misma VPC.
- Desde esa VM, ejecutar:
```bash
curl http://<INTERNAL_IP>
```
- Verificar que el tráfico se distribuye entre internal-app1 y internal-app2.

##🔐 Buenas prácticas aplicadas
- Uso de IP interna para evitar exposición pública.
- Configuración de firewall con rangos internos específicos.
- Separación clara de frontend (proxy, URL map) y backend (instance group).
- Ideal para microservicios internos y aplicaciones empresariales seguras.

##📊 Resultado
Se configuró un Internal HTTP(S) Load Balancer que distribuye tráfico web entre dos instancias de VM dentro de la misma VPC. El balanceador responde en una IP privada y reparte las solicitudes de forma automática.

##💡 Conclusiones
Este lab demuestra cómo implementar alta disponibilidad y escalabilidad interna en Google Cloud.
Es aplicable a arquitecturas de microservicios, aplicaciones internas y sistemas corporativos que requieren balanceo seguro sin exposición a internet.

---

