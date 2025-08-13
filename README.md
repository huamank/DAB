# DAB
Este repositorio contiene un ejemplo de uso de **Databricks Asset Bundles (DAB)**, con notebooks y configuración para desplegar en Databricks usando CI/CD.

---

##  Estructura del repositorio

- **`databricks.yml`**  
  Archivo de configuración principal de DAB. Define el bundle, inclusión de recursos, targets (como `dev`, `qas`, `prod`), y rutas en el workspace.

- **`.github/workflows/`**  
  Contiene los flujos para GitHub Actions, donde se configura el pipeline de **validación**, **despliegue** e **ejecución** de bundles en Databricks.

- **`resources/`**  
  Carpeta para archivos de configuración adicionales, como definiciones de jobs, clusters, etc.

- **`src/notebooks/`**  
  Donde están los notebooks (en formato `.py` o `.ipynb`) que conforman el código ubicado dentro del bundle.

---

##  ¿Cómo funciona el flujo?

1. **Validación del bundle**  
   Se usa el comando:
   ```sh
   databricks bundle validate --target <entorno>

  para comprobar consistencia, definir contenido y estructura adecuados.

2.	**Despliegue del bundle**
    
  	```sh
   databricks bundle deploy --target <entorno>

  se sincroniza el contenido al workspace de Databricks, configurando notebooks, jobs, clusters, etc.

3. **Despliegue del bundle**

  Si está definido un job dentro del bundle:
    ```sh
    databricks bundle run <job_key> --target <entorno>
