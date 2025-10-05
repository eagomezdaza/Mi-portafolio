---
layout: project
title: Iris — API Flask
subtitle: Clasificación Iris servida como API REST contenedorizada
permalink: /proyecto-iris/
repo: https://github.com/eagomezdaza/iris-flask-docker-api
stack: Flask · Docker · scikit-learn
tags: [Flask, Docker, scikit-learn]
---

## Tecnologías usadas
<div class="d-flex flex-wrap gap-2 mb-3">
  <span class="badge bg-primary">Flask</span>
  <span class="badge bg-info text-dark">Docker</span>
  <span class="badge bg-secondary">scikit-learn</span>
</div>

## Resumen
Modelo de clasificación **Iris** entrenado con **scikit-learn** y expuesto como **API REST**.  
Incluye validaciones, manejo de errores y ejecución reproducible en contenedor **Docker**.

## Cómo ejecutar
```bash
git clone https://github.com/eagomezdaza/iris-flask-docker-api
cd iris-flask-docker-api
docker build -t iris-api .
docker run -p 8000:8000 iris-api
```

---

## Métricas del modelo
| Métrica  | Valor |
|---------:|:-----:|
| Accuracy | 0.97  |
| F1-score | 0.97  |
| Precision | 0.96 |
| Recall | 0.97 |

> Evaluación sobre conjunto de prueba (30%) con modelo SVM lineal.

---

## Capturas de resultados
> Coloca las imágenes en:
> `assets/images/iris/endpoint-health.png`  
> `assets/images/iris/predict-sample.png`

<div class="row g-3">
  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded border" src="/Mi-portafolio/assets/images/iris/endpoint-health.png" alt="Endpoint /health">
      <figcaption class="figure-caption">Respuesta del endpoint <code>/health</code></figcaption>
    </figure>
  </div>
  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded border" src="/Mi-portafolio/assets/images/iris/predict-sample.png" alt="Endpoint /predict">
      <figcaption class="figure-caption">Ejemplo de solicitud <code>/predict</code></figcaption>
    </figure>
  </div>
</div>

---

## Conclusiones
- API ligera y portable con dependencias bien aisladas.  
- Validación robusta de entrada JSON y manejo controlado de errores.  
- Modelo simple pero eficiente para demostración de flujo MLOps.

---

## Próximos pasos
- Agregar endpoint `/version` para trazabilidad del modelo.  
- Incluir métricas de rendimiento y logs estructurados.  
- Explorar despliegue en Azure Container Apps o Railway.
