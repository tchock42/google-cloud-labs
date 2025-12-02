# Cloud IAM: Qwik Start (GSP064)

## 🎯 Objetivo
Aprender a usar **Cloud Identity and Access Management (IAM)** para asignar roles y permisos a usuarios, controlando el acceso a recursos de Google Cloud.

---

## 🛠️ Pasos principales

1. **Configurar proyecto**
   - Verificar proyecto activo:
     ```bash
     gcloud config list project
     ```

2. **Crear un nuevo usuario (miembro)**
   - En la consola: **IAM & Admin → IAM → Add**.  
   - Especificar correo electrónico del usuario.  
   - Asignar rol inicial (ej. `Viewer`).

3. **Asignar roles adicionales**
   - Desde la consola o CLI:
     ```bash
     gcloud projects add-iam-policy-binding $DEVSHELL_PROJECT_ID \
       --member="user:example@gmail.com" \
       --role="roles/storage.objectViewer"
     ```
   - Esto otorga permisos para ver objetos en Cloud Storage.

4. **Verificar políticas IAM**
   - Listar bindings actuales:
     ```bash
     gcloud projects get-iam-policy $DEVSHELL_PROJECT_ID
     ```
   - Confirmar que el usuario aparece con los roles asignados.

5. **Probar acceso**
   - El usuario inicia sesión y verifica que puede acceder a recursos según los roles otorgados.  
   - Ejemplo: acceso de solo lectura a un bucket de Cloud Storage.

---

## 🔐 Buenas prácticas aplicadas
- **Principio de menor privilegio**: asignar solo los roles necesarios.  
- Uso de **roles predefinidos** en lugar de `Owner` para mayor seguridad.  
- Separación de responsabilidades entre usuarios (ej. Viewer vs Editor).  
- Auditoría de políticas IAM con `get-iam-policy`.  

---

## 📊 Resultado
Se creó un usuario en IAM, se le asignaron roles específicos y se verificó que los permisos funcionen correctamente. Esto demuestra cómo controlar el acceso a recursos en Google Cloud.

---

## 💡 Reflexión
Este lab demuestra cómo aplicar **gestión de identidades y accesos** en la nube.  
Es aplicable a proyectos que requieren **seguridad, cumplimiento y control granular de permisos**, reforzando tu perfil en **infraestructura segura y profesional**.

---


