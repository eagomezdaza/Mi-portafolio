---
layout: project
title: Iris — API Flask & Docker
subtitle: Clasificación de flores Iris mediante API REST y contenedorización
permalink: /proyecto-iris/
repo: https://github.com/eagomezdaza/iris-flask-docker-api
dataset: Iris Dataset (4 features, 3 clases)
stack: Python · Flask · Docker · scikit-learn · Streamlit
tags: [Python, Flask, Docker, API, CI/CD]
---

## Tecnologías usadas
<div class="d-flex flex-wrap gap-2 mb-3">
  <span class="badge bg-primary">Python</span>
  <span class="badge bg-info text-dark">Flask</span>
  <span class="badge bg-secondary">Docker</span>
  <span class="badge bg-success">scikit-learn</span>
  <span class="badge bg-warning text-dark">Streamlit</span>
  <span class="badge bg-dark">GitHub Actions (CI)</span>
</div>

## Resumen
Implementación de una **API REST para la clasificación de flores Iris** usando **Flask** y **Docker**, con un modelo **Random Forest** entrenado mediante *scikit-learn*.  
El proyecto demuestra un flujo educativo de **MLOps**, abarcando entrenamiento, pruebas automatizadas, contenedorización y despliegue reproducible.  
Incluye una interfaz **Streamlit** para visualización de predicciones y un **pipeline CI** configurado en GitHub Actions.

---

## Cómo ejecutar
1. Clonar el repositorio:
```bash
git clone https://github.com/eagomezdaza/iris-flask-docker-api
cd iris-flask-docker-api
```
2. Instalar dependencias (entorno local):
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
3. Ejecutar la API:
```bash
python app.py
```
Endpoint principal: `http://127.0.0.1:5002`
4. O bien construir y ejecutar el contenedor Docker:
```bash
docker build -t ml-api-iris .
docker run -d --name irisapi -p 5002:5002 ml-api-iris
```
5. Validar su funcionamiento:
```bash
curl -X POST http://127.0.0.1:5002/predict \
     -H "Content-Type: application/json" \
     -d '{"features":[5.1, 3.5, 1.4, 0.2]}'
```

---

## Estructura del proyecto
```
iris-flask-docker-api/
├── app.py
├── train_model.py
├── test_api.py
├── frontend.py
├── modelo.pkl
├── requirements.txt
├── Dockerfile
├── Makefile
├── assets/
│   ├── entrenamiento.png
│   ├── api_local.png
│   ├── docker_run.png
│   ├── streamlit_demo.png
│   └── workflow_ci.png
└── .github/workflows/ci.yml
```

---

<!-- DEBUG TÉCNICO - VERIFICACIÓN COMPLETA -->
<div style="background: #ff6b6b; color: white; padding: 20px; margin: 20px 0; border-radius: 10px;">
  <h4>🔧 DEBUG TÉCNICO - VERIFICACIÓN DE IMÁGENES</h4>
  
  <div style="background: rgba(255,255,255,0.2); padding: 15px; border-radius: 5px; margin: 10px 0;">
    <h5>📁 URLs generadas por Jekyll:</h5>
    <ul>
      <li><strong>entrenamiento.png:</strong> <code>{{ '/assets/images/iris/entrenamiento.png' | relative_url }}</code></li>
      <li><strong>api_local.png:</strong> <code>{{ '/assets/images/iris/api_local.png' | relative_url }}</code></li>
      <li><strong>docker_run.png:</strong> <code>{{ '/assets/images/iris/docker_run.png' | relative_url }}</code></li>
      <li><strong>streamlit_demo.png:</strong> <code>{{ '/assets/images/iris/streamlit_demo.png' | relative_url }}</code></li>
    </ul>
  </div>

  <div style="background: rgba(255,255,255,0.2); padding: 15px; border-radius: 5px; margin: 10px 0;">
    <h5>🔗 Enlaces directos para probar:</h5>
    <ul>
      <li><a href="{{ '/assets/images/iris/entrenamiento.png' | relative_url }}" target="_blank" style="color: #a5d8ff;">Probar entrenamiento.png</a></li>
      <li><a href="{{ '/assets/images/iris/api_local.png' | relative_url }}" target="_blank" style="color: #a5d8ff;">Probar api_local.png</a></li>
      <li><a href="{{ '/assets/images/iris/docker_run.png' | relative_url }}" target="_blank" style="color: #a5d8ff;">Probar docker_run.png</a></li>
      <li><a href="{{ '/assets/images/iris/streamlit_demo.png' | relative_url }}" target="_blank" style="color: #a5d8ff;">Probar streamlit_demo.png</a></li>
    </ul>
  </div>
</div>

## Resultados y evidencias
<div class="gallery row g-3">

  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/iris/entrenamiento.png' | relative_url }}"
           alt="Entrenamiento del modelo" loading="lazy" decoding="async">
      <figcaption class="figure-caption">
        Ejecución del entrenamiento con Random Forest
      </figcaption>
    </figure>
  </div>

  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/iris/api_local.png' | relative_url }}"
           alt="Prueba API local" loading="lazy" decoding="async">
      <figcaption class="figure-caption">
        Prueba de endpoints `/health` y `/predict` en entorno local
      </figcaption>
    </figure>
  </div>

  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/iris/docker_run.png' | relative_url }}"
           alt="Ejecución contenedor Docker" loading="lazy" decoding="async">
      <figcaption class="figure-caption">
        Contenedor Docker saludable (`HEALTHY`) en ejecución
      </figcaption>
    </figure>
  </div>

  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/iris/streamlit_demo.png' | relative_url }}"
           alt="Interfaz Streamlit" loading="lazy" decoding="async">
      <figcaption class="figure-caption">
        Interfaz visual para predicción en Streamlit
      </figcaption>
    </figure>
  </div>

</div>


---

## Conclusiones
- La **API Flask** responde correctamente a los endpoints `/`, `/health` y `/predict`, validando entradas JSON.  
- El flujo **Dockerizado** permite despliegue reproducible y verificación de salud del contenedor.  
- **GitHub Actions** automatiza las pruebas y el build, garantizando integridad continua.  
- La interfaz **Streamlit** facilita la exploración de predicciones y visualiza probabilidades en tiempo real.

---

## Próximos pasos
- Incorporar **autenticación básica** en la API.  
- Publicar la imagen en **Docker Hub**.  
- Integrar despliegue continuo en **Azure Container Apps** o **Render**.  
- Extender el flujo CI/CD con tests de integración.

---
