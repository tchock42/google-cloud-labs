# Cloud Monitoring: Qwik Start (GSP089)

## 🎯 Objetivo
Aprender a configurar **Cloud Monitoring** en Google Cloud para visualizar métricas de recursos, crear dashboards personalizados y definir alertas básicas.

---

## 🛠️ Pasos principales

1. **Habilitar APIs necesarias**
   - Asegúrate de que el proyecto tenga habilitado:
     - Cloud Monitoring API
     - Cloud Logging API

2. **Acceder a Cloud Monitoring**
   - Desde la consola, ir a `Monitoring`.
   - Se crea automáticamente un **Workspace** asociado al proyecto.

3. **Explorar métricas de VM**
   - Crear una instancia de Compute Engine (ej. `monitoring-vm`).
   - Instalar el **Cloud Ops Agent** para recolectar métricas de CPU, memoria y disco.
   - Validar que las métricas aparecen en Monitoring → Metrics Explorer.

4. **Crear un Dashboard**
   - En Monitoring → Dashboards → Create Dashboard.
   - Añadir gráficos como:
     - Uso de CPU
     - Memoria utilizada
     - Latencia de red
   - Guardar el dashboard con nombre: `VM Monitoring Dashboard`.

5. **Configurar una alerta**
   - Monitoring → Alerting → Create Policy.
   - Condición: CPU usage > 80% durante 5 minutos.
   - Notificación: Email o Pub/Sub.
   - Guardar la política de alerta.

---

## 🔐 Buenas prácticas aplicadas
- Uso de **principio de menor privilegio** en IAM para acceso a Monitoring.
- Configuración de alertas proactivas para evitar incidentes.
- Dashboards personalizados para observabilidad clara.

---

## 📊 Resultado
- Se creó un **Workspace de Monitoring**.  
- Se visualizaron métricas de una VM en tiempo real.  
- Se configuró un dashboard con métricas clave.  
- Se definió una política de alerta para CPU alta.  

---

## 💡 Conclusiones
Este lab demuestra cómo implementar **observabilidad en la nube** con Google Cloud.  
La capacidad de crear dashboards y alertas es esencial en proyectos de **DevOps, SRE y arquitecturas escalables**, ya que permite detectar problemas antes de que impacten al usuario final.
