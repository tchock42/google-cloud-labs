# Redes de VPC: Cómo controlar el acceso (GSP213)

## 🎯 Objetivo
Aprender a configurar reglas de firewall en una **VPC Network** para controlar el acceso a instancias de VM, permitiendo o bloqueando tráfico según protocolos, puertos y rangos de IP.

---

## 🛠️ Pasos principales

1. **Configurar región y zona por defecto**
   ```bash
   gcloud config set compute/region us-central1
   gcloud config set compute/zone us-central1-a
2. **Crear una VPC personalizada
   ```bash
   gcloud compute networks create my-vpc --subnet-mode=custom
   gcloud compute networks subnets create my-subnet \
   --network=my-vpc \
   --range=10.0.0.0/24 \
   --region=us-central1
   ```
3. **Crear instancias de VPC
   - Crear dos VMs dentro de la subred
     ```bash
     gcloud compute instances create vm-1 \
     --zone=us-central1-a \
     --subnet=my-subnet \
     --tags=allow-ssh

     gcloud compute instances create vm-2 \
     --zone=us-central1-a \
     --subnet=my-subnet \
     --tags=allow-http 
     ```
4. **Configurar reglas de firewall
   - Permitir tráfico SSH (puerto 22) solo a instancias con tag allow-ssh:
    ```bash
    gcloud compute firewall-rules create allow-ssh \
    --network=my-vpc \
    --allow tcp:22 \
    --target-tags=allow-ssh
    ```
- Permitir tráfico HTTP (puerto 80) solo a instancias con tag allow-http:
    ```bash
    gcloud compute firewall-rules create allow-http \
    --network=my-vpc \
    --allow tcp:80 \
    --target-tags=allow-http
    ```
- Bloquear tráfico ICMP (ping) para reforzar seguridad:
    ```bash
    gcloud compute firewall-rules create deny-icmp \
    --network=my-vpc \
    --priority=1000 \
    --action=DENY \
    --rules=icmp
    ```

5. **Probar conectividad
- Conectarse vía SSH a vm-1 y verificar acceso.
- Probar acceso HTTP a vm-2.
- Intentar hacer ping y confirmar que está bloqueado.

## 🔐 Buenas prácticas aplicadas
- Uso de tags para aplicar reglas de firewall de forma granular.
- Configuración de reglas de deny para reforzar seguridad.
- Principio de menor privilegio: solo se habilitan los puertos necesarios.
- Separación de roles y servicios en distintas instancias.

## 📊 Resultado
Se creó una VPC personalizada con reglas de firewall que controlan el acceso a instancias de VM. Se permitió tráfico SSH y HTTP de manera selectiva, y se bloqueó ICMP para mayor seguridad.

## 💡 Concluciones
Este lab demuestra cómo implementar seguridad en redes VPC mediante reglas de firewall.
Es aplicable a proyectos que requieren control granular de tráfico, segmentación de servicios y cumplimiento de políticas de seguridad.

---
