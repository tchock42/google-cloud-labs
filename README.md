# Google Cloud Labs Documentation

Este repositorio recopila y documenta los laboratorios más relevantes que completé en la plataforma de Google Cloud.  
El objetivo es mostrar mi aprendizaje práctico en **infraestructura, seguridad, bases de datos y despliegue de aplicaciones en la nube**, aplicable a proyectos reales.

---

## 📑 Índice de Labs

1. **Cloud IAM: Qwik Start**
   - Asignar un rol a un segundo usuario
   - Quitar los roles asignados asociados con Cloud IAM
   👉 [Ver documentación](cloud-iam/README.md)

2. **Autenticación de usuarios: Identity-Aware Proxy**
   - Mostrar una página de bienvenida
   - Acceder a la información de identidad del usuario que brinda IAP
   - Usar la verificación criptográfica para impedir que se falsifique la información de identidad del usuario
   👉 [Ver documentación](autenticacion-de-usuarios-identity-aware-proxy/README.md)

3. **Cloud SQL for MySQL: Qwik Start**  
   - Crear instancia de MySQL en Cloud SQL  
   - Conexión desde Cloud Shell  
   - Operaciones básicas de SQL  
   👉 [Ver documentación](cloud-sql-mysql/README.md)

4. **Cloud Monitoring**
   - Crear una instnacia de Compute Engine
   - Agregar un servidor HTTP Apache2 a la instancia
   - Crear una política de alertas
   - Crear un panel y un gráfico
   - Consultar los registros
   👉 [Ver documentación](cloud-monitoring/README.md)

5. **Configura balanceadores de carga de red**  
   - Crear varias instancias de servidor wev
   - Configurar el servicio de balanceo de cargas
   - Crear el grupo de destino y regla de reenvío
   - Enviar tráfico a las instancias
   👉 [Ver documentación](configura-balanceadores-de-cargas-de-red/README.md)

6. **Configura balanceadores de cargas de aplicaciones**  
   - Crear varias instancias de servicor web
   - Crear un balanceador de cargas de aplicaciones
   - Probar el tráfico enviado a las instancias
   👉 [Ver documentación](configurar-balanceador-de-cargas-de-aplicaciones/README.md)

7. **Usar un balanceador de cargas de aplicaciones internas**  
   - Crear un entorno virtual
   - Crear un grupo administrado de backend
   - Configurar el balanceador de cargas interno
   - Probar el balanceador de cargas
   👉 [Ver documentación](usar-un-balanceador-de-cargas-de-aplicaciones-interno/README.md)

8. **Cloud Storage - CLI/SDK**
   - Crear un bucket
   - Subir, descargar, copiar y mostrar objetos del bucket
   👉 [Ver documentación](cloud-storage-cli-sdk/README.md)

9. **Cloud Run Function - Línea de comandos
    - Crear una función e implementarla
    - Probar la funcón
    👉 [Ver documentación](cloud-run-function-linea-de-comandos/README.md)

10. **Pub/Sub - Python**
    - Configurar Pub/Sub
    - Crear una suscripción y publicar un mensaje en el topic
    👉 [Ver documentación](pub-sub-python/README.md)

11. **Proteger máquinas virtuales con Chrome Enterprise Premium**
    - Habilitar el reenvío de TCP de IAP
    - Probar conectividad de instancias de linux y windows
    - Configurar reglas de firewall para BCE
    - Otorgar permisos para usar el reenvío de TCP en IAP y progar la tunelización mediante SSH y RDP
    👉 [Ver documentación](protege-maquinas-virtuales-con-chrome-enterprise-premium/README.md)

12. **Redes VPC: Control de acceso**
    - Crear servidores de red VPC y controlar acceso HTTP externo a los servidores a través de reglas de firewall etiquetadas
    - Explorar roles de IAM y cuentas de servicio
    👉 [Ver documentación](redes-de-vpc-como%20controlar-acceso/README.md)
      
13. **Balanceadores de cargas de aplicaciones con Cloud Armor**
    - Crear reglas de firewall de HTTP y de verificación de estado
    - Configurar dos plantillas de instancias y dos grupos de instancias administrados
    - Configurar un balanceador de cargas de aplicaciones con IPv4 e IPv6
    - Someter un balanceador de cargas de aplicaciones a una prueba de esfuerzo
    - Agregar una dirección IP a la lista de bloqueo para restringir el acceso a un balanceador de cargas de aplicaciones
    👉 [Ver documentación](cloud-armor/README.md)

14. **Dataproc: Qwik Start (Consola)**
    - Crear un cluster de Dataproc
    - Ejecutar un job de ejemplo y administrar el ciclo de vida del cluster
    👉 [Ver documentación](dataproc-consola/README.md)

15. **Dataflow: Qwik Start (plantillas)**
    - Seleccionar plantillas de gcloud y ejecutar un job
    - Verificar el estado del pipeline y ver sus resultados
   👉 [Ver documentación](dataflow-plantillas/README.md)
      
16. **Dataflow - Python**
    - Crear un bucket de Cloud Storage para almacenar los resultados de una canalización de Dataflow
    - Instalar el SDK de Apache Beam para Python
    - Ejecutar una canalización de Dataflow de forma remota
    👉 [Ver documentación](dataflow-python/README.md)

17. **API de Cloud Natural Language: Qwik Start**
    - Crear una clave de API
    - Usar la API de Cloud Natural Language para extraer “entidades” (p. ej., personas, lugares y eventos) de un fragmento de texto
    👉 [Ver documentación](api-de-cloud-natural-language/README.md)

18. **API de Speech-to-Text: Qwik Start**
    - Crear una clave de API
    - Crear una solicitud a la API de Speech-to-Text
    - Llamar a la API de Speech-to-Text
    👉 [Ver documentación](api-de-speech-to-text/README.md)

19. **Video Intelligence API: Qwik Start**
    - Configurar la autorización de una cuenta de servicio personalizada
    - Enviar una solicitud para anotar un video a la API de Video Intelligence
    👉 [Ver documentación](video-intelligence-api/README.md)
---

## 🚀 Cómo usar este repositorio
- Cada carpeta dentro de `labs/` contiene un **README.md** con:
  - Objetivo del lab  
  - Pasos principales  
  - Buenas prácticas aplicadas  
  - Resultado y reflexión  

---

## 💡 Conclusión general
Estos labs muestran mi capacidad de:
- **Aprender y aplicar rápidamente tecnologías cloud**.  
- **Documentar procesos técnicos con claridad y profesionalismo**.  
- **Conectar conceptos de laboratorio con escenarios reales de trabajo**.  

---

