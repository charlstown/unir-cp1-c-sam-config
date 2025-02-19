# 📁 UNIR - unir-cp1-c-sam-config

Este repositorio forma parte del **Caso Práctico 1 - Apartado C - Reto 4** de la Universidad Internacional de La Rioja (UNIR).  
El objetivo es **separar la configuración de CloudFormation** mediante el uso de un archivo `samconfig.toml`, evitando incluir la configuración dentro del código fuente.

Los archivos `Jenkinsfile`, desde donde se realiza la llamada a este repositorio para descargar la configuración, se encuentran en el siguiente repositorio:  

**🔗[unir-cp1-c-aws](https://github.com/charlstown/unir-cp1-c-aws)**

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

## 🚀 Despliegue en CI/CD

El pipeline de Jenkins se encargará de descargar el fichero `samconfig.toml` de la rama correcta en función del entorno en el que se ejecute:

Proceso | unir-cp1-c-aws | unir-cp1-c-sam-config |
|-|-|-|
| **CI** | `develop` | `staging` |
| **CD** | `master` | `production` |
