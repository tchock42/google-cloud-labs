# Protege máquinas virtuales con Chrome Enterprise Premium (GSP1036)

## 🎯 Objetivo
Aprender a proteger el acceso a instancias de VM en Google Cloud usando **Chrome Enterprise Premium** y **IAP TCP forwarding**, evitando la exposición de IPs públicas y reforzando la seguridad.

---

## 🛠️ Pasos principales

1. **Habilitar IAP TCP Forwarding**
   - Activar la API de IAP en el proyecto:
     ```bash
     gcloud services enable iap.googleapis.com
     ```
   - Configurar permisos para el servicio de IAP.

2. **Crear instancias Linux y Windows**
   - Crear una VM Linux (ej. `secure-linux`) y una VM Windows (ej. `secure-windows`) sin IP pública.
   - Asociar ambas a una VPC interna.

3. **Configurar reglas de firewall**
   - Permitir tráfico interno para SSH (Linux) y RDP (Windows).
   - Bloquear accesos externos directos para reforzar seguridad.

4. **Asignar roles IAM al Service Account**
   - Conceder permisos de **IAP-secured Tunnel User** al usuario/SA que administrará las VMs.
   - Esto asegura que solo identidades autorizadas puedan usar IAP para conectarse.

5. **Probar conectividad con IAP**
   - Conectar a la VM Linux vía IAP:
     ```bash
     gcloud compute ssh secure-linux --tunnel-through-iap
     ```
   - Conectar a la VM Windows vía IAP Desktop (cliente gráfico).

6. **Demostrar túneles seguros**
   - Validar que el acceso se realiza vía túnel IAP (sin IP pública).
   - Probar tanto SSH como RDP para confirmar conectividad segura.

---

## 🔐 Buenas prácticas aplicadas
- **Eliminación de IPs públicas** en las VMs para reducir superficie de ataque.  
- Uso de **IAP TCP forwarding** para acceso seguro y controlado.  
- Configuración de **roles IAM mínimos** (principio de menor privilegio).  
- Integración con **Chrome Enterprise Premium** para gestión centralizada y segura de accesos.  

---

## 📊 Resultado
Se configuraron dos instancias (Linux y Windows) protegidas sin IP pública. El acceso se realizó mediante **IAP TCP forwarding** y Chrome Enterprise Premium, garantizando seguridad y control de identidades.

---

## 💡 Conclusiones
Este lab demuestra cómo reforzar la seguridad de máquinas virtuales en Google Cloud mediante **acceso seguro sin exposición pública**.  
Es aplicable a entornos corporativos que requieren **cumplimiento, auditoría y control de accesos**, integrando IAM, IAP y Chrome Enterprise Premium.
