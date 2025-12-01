# Cloud SQL for MySQL: Qwik Start (GSP151)

## 🎯 Objetivo
Aprender a crear una instancia de Cloud SQL para MySQL, conectarse desde Cloud Shell y realizar operaciones básicas de SQL.

## 🛠️ Pasos principales
1. **Crear instancia de Cloud SQL**
   - Navegar a `SQL` en la consola.
   - Seleccionar motor **MySQL**.
   - Configurar:
     - Instance ID: `myinstance`
     - Versión: MySQL 8
     - Edición: Enterprise
     - Preset: Development (4 vCPU, 16 GB RAM, 100 GB Storage, Single zone)
   - Generar y guardar la contraseña del usuario root.

2. **Conectarse desde Cloud Shell**
   - Abrir Cloud Shell.
   - Ejecutar:
     ```bash
     gcloud sql connect myinstance --user=root
     ```
   - Ingresar la contraseña generada.

3. **Crear base de datos y cargar datos**
   - Dentro del cliente `mysql`:
     ```sql
     CREATE DATABASE guestbook;
     USE guestbook;
     CREATE TABLE entries (id INT AUTO_INCREMENT PRIMARY KEY, guestName VARCHAR(255), content VARCHAR(255));
     INSERT INTO entries (guestName, content) VALUES ('Jacob', 'Primera entrada en Cloud SQL!');
     SELECT * FROM entries;
     ```

## 🔐 Buenas prácticas aplicadas
- Uso de **Cloud Shell** para evitar credenciales locales inseguras.
- Configuración mínima de recursos para un entorno de desarrollo.
- Separación de roles y contraseñas seguras.

## 📊 Resultado
Se creó una instancia de MySQL en Cloud SQL, se conectó desde Cloud Shell y se insertaron datos en una tabla de prueba.

## 💡 Conclusiones
Este lab demuestra cómo levantar rápidamente una base de datos gestionada en la nube, aplicable a proyectos de **aplicaciones web con backend MySQL**. Es un paso clave para integrar bases de datos seguras y escalables en arquitecturas modernas.
