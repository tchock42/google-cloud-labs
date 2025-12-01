# Dataproc: Qwik Start - Consola (GSP103)

## 🎯 Objetivo
Aprender a crear un **cluster de Dataproc** desde la consola de Google Cloud, ejecutar un job de ejemplo (Hadoop/Spark) y administrar el ciclo de vida del cluster.

---

## 🛠️ Pasos principales

1. **Habilitar APIs necesarias**
   - Desde la consola, activar:
     - Dataproc API
     - Cloud Storage API

2. **Crear bucket de Cloud Storage**
   - Usar Cloud Storage para staging y resultados:
     - Navegar a **Storage → Buckets → Create**.
     - Nombre único global: `dataproc-bucket-jacob`.

3. **Crear un cluster de Dataproc**
   - Ir a **Dataproc → Clusters → Create Cluster**.
   - Configuración básica:
     - Nombre: `dataproc-cluster`
     - Región: `us-central1`
     - Zona: `us-central1-a`
     - Número de nodos: 1 master + 2 workers
   - Guardar y crear.

4. **Ejecutar un job de ejemplo**
   - Ir a **Jobs → Submit Job**.
   - Configuración:
     - Tipo: **Hadoop**
     - Clase principal: `org.apache.hadoop.examples.WordCount`
     - Jar: `file:///usr/lib/hadoop/hadoop-examples.jar`
     - Argumentos: `gs://dataflow-samples/shakespeare/kinglear.txt gs://dataproc-bucket-jacob/output`
   - Ejecutar y esperar resultados.

5. **Ver resultados**
   - Ir a **Cloud Storage → Buckets → dataproc-bucket-jacob/output**.
   - Abrir archivo de salida y verificar conteo de palabras.

6. **Eliminar recursos**
   - Ir a **Dataproc → Clusters → Delete** para eliminar el cluster.
   - Eliminar bucket si ya no se necesita.

---

## 🔐 Buenas prácticas aplicadas
- Uso de **Cloud Storage** para staging y resultados.  
- Eliminación del cluster al finalizar para evitar costos innecesarios.  
- Configuración mínima de nodos para pruebas rápidas.  
- Separación clara de **infraestructura (cluster)** y **datos (bucket)**.  

---

## 📊 Resultado
Se creó un cluster de Dataproc desde la consola, se ejecutó un job de **WordCount** con Hadoop y se almacenaron los resultados en Cloud Storage.

---

## 💡 Conclusiones
Este lab demuestra cómo usar **Dataproc para procesamiento distribuido** en la nube.  
Es aplicable a proyectos de **ETL, análisis de grandes volúmenes de datos y machine learning**, reforzando tu perfil en **data engineering y cloud automation**.
