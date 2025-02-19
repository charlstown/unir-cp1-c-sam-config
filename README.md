# 📁 UNIR - unir-cp1-c-sam-config

Este repositorio forma parte del **Caso Práctico 1 - Apartado C - Reto 4** de la Universidad Internacional de La Rioja (UNIR).  
El objetivo es **separar la configuración de CloudFormation** mediante el uso de un archivo `samconfig.toml`, evitando incluir la configuración dentro del código fuente.

## 📌 Descripción

El reto consiste en almacenar la configuración en este repositorio, separado del código de la aplicación.  
Cada entorno tendrá su propia configuración en una rama diferente:

- 🟢 **staging** → Configuración para el entorno de pruebas  
- 🔴 **production** → Configuración para el entorno de producción  

Los pipelines de CI/CD descargarán automáticamente el fichero `samconfig.toml` desde la rama correspondiente en función del entorno en el que se esté desplegando.

## 📂 Estructura del Repositorio

Este repositorio contiene únicamente el archivo de configuración `samconfig.toml`, separado por ramas:

```
📂 todo-list-aws-config
 ├── 🔀 staging (configuración del entorno de staging)
 ├── 🔀 production (configuración del entorno de producción)
```

## 🔗 Relación con otro repositorio

Los archivos `Jenkinsfile`, desde donde se realiza la llamada a este repositorio para descargar la configuración, se encuentran en el siguiente repositorio:  
➡️ **[Enlace al repositorio de JenkinsFile]** (reemplazar con el link real).

## 🚀 Despliegue en CI/CD

El pipeline de Jenkins se encargará de descargar el fichero `samconfig.toml` de la rama correcta en función del entorno en el que se ejecute:

- En la rama `develop` (CI) → Se descarga la configuración desde la rama `staging`.  
- En la rama `master` (CD) → Se descarga la configuración desde la rama `production`.

## ⚠️ Notas

- La configuración solo contiene el nombre de la tabla de la base de datos, ya que otros aspectos como la región se mantienen constantes en ambos entornos.
- Se permite la existencia de una rama `master`, pero **no se usará**.
