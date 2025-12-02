# Autenticación de usuarios con Identity-Aware Proxy (GSP499)

## 🎯 Objetivo
Aprender a proteger aplicaciones y recursos en Google Cloud usando **Identity-Aware Proxy (IAP)**, garantizando que solo usuarios autenticados y autorizados puedan acceder.

---

## 🛠️ Pasos principales

1. **Configurar entorno**
   - Activar la API de IAP:
     ```bash
     gcloud services enable iap.googleapis.com
     ```
   - Verificar proyecto activo:
     ```bash
     gcloud config list project
     ```

2. **Crear una aplicación de prueba**
   - Desplegar una aplicación en App Engine o una VM con un servicio web.
   - Ejemplo con App Engine (Python):
     ```bash
     gcloud app create --region=us-central
     gcloud app deploy
     ```

3. **Configurar acceso con IAP**
   - Ir a **Security → Identity-Aware Proxy** en la consola.  
   - Seleccionar la aplicación o recurso desplegado.  
   - Activar **IAP** para proteger el acceso.

4. **Asignar permisos IAM**
   - Conceder el rol `IAP-Secured Web App User` a los usuarios autorizados:
     ```bash
     gcloud projects add-iam-policy-binding $DEVSHELL_PROJECT_ID \
       --member="user:example@gmail.com" \
       --role="roles/iap.webAppUser"
     ```

5. **Probar autenticación**
   - Acceder a la URL de la aplicación.  
   - Verificar que se solicita inicio de sesión con cuenta de Google.  
   - Confirmar que solo usuarios con permisos pueden acceder.

---

## 🔐 Buenas prácticas aplicadas
- **Principio de menor privilegio**: asignar roles solo a usuarios que lo requieren.  
- Eliminación de IPs públicas: acceso controlado únicamente vía IAP.  
- Integración con **IAM** para gestión centralizada de identidades.  
- Auditoría de accesos mediante Cloud Audit Logs.  

---

## 📊 Resultado
Se protegió una aplicación en Google Cloud con **Identity-Aware Proxy**, garantizando que solo usuarios autenticados y autorizados puedan acceder.

---

## 💡 Conclusiones
Este lab demuestra cómo aplicar **seguridad basada en identidad** en la nube.  
Es aplicable a proyectos que requieren **control de accesos, cumplimiento y protección de aplicaciones internas**, reforzando tu perfil en **infraestructura segura y gobernada**.
