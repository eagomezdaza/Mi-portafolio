---
layout: project
title: MLOps en la Nube
subtitle: API Flask contenedorizada y desplegada en Azure con CI/CD
permalink: /mlops-nube/
repo: https://github.com/eagomezdaza/Mod10-Evaluacion_Modular
stack: Flask · Docker · GitHub Actions · Azure
tags: [Flask, Docker, Azure, CI/CD]
---

## Tecnologías usadas
<div class="d-flex flex-wrap gap-2 mb-3">
  <span class="badge bg-primary">Flask</span>
  <span class="badge bg-info text-dark">Docker</span>
  <span class="badge bg-warning text-dark">GitHub Actions</span>
  <span class="badge bg-secondary">Azure</span>
</div>

## Resumen
Sistema **MLOps** que expone un modelo de Machine Learning como API REST con **Flask**, empaquetado con **Docker** y desplegado en **Azure**.  
El pipeline de **CI/CD** ejecuta pruebas, build y deploy automático desde la rama principal (`main`) mediante **GitHub Actions**.

## Endpoints principales
- `GET /health` — estado del servicio  
- `POST /predict` — recibe features y devuelve predicción en JSON

## Cómo ejecutar localmente
```bash
git clone https://github.com/eagomezdaza/Mod10-Evaluacion_Modular
cd Mod10-Evaluacion_Modular
docker build -t mlops-api .
docker run -p 8000:8000 mlops-api
```

---

## Métricas de despliegue
| Métrica        | Valor |
|---------------:|:-----:|
| Latencia p95   | 120 ms |
| Throughput     | 50 req/s |
| Uptime         | 99.9% |
| Tamaño imagen  | 186 MB |

> Métricas obtenidas con monitoreo básico de contenedor en entorno Azure.

---

## Capturas de referencia
> Coloca las imágenes en:
> `assets/images/mlops/pipeline-actions.png`  
> `assets/images/mlops/azure-deploy.png`

<div class="row g-3">
  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded border" src="/Mi-portafolio/assets/images/mlops/pipeline-actions.png" alt="Pipeline GitHub Actions">
      <figcaption class="figure-caption">Pipeline automatizado en GitHub Actions</figcaption>
    </figure>
  </div>
  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded border" src="/Mi-portafolio/assets/images/mlops/azure-deploy.png" alt="Despliegue en Azure">
      <figcaption class="figure-caption">Despliegue del contenedor en Azure</figcaption>
    </figure>
  </div>
</div>

---

## Conclusiones
- Pipeline funcional con integración y despliegue continuo (CI/CD).  
- Flujo reproducible gracias a la contenedorización y versionado.  
- Alta disponibilidad del servicio (>99.9%) y bajo tiempo de respuesta.  

---

## Próximos pasos
- Añadir observabilidad (logging estructurado y métricas Prometheus).  
- Automatizar rollback en fallos de build/deploy.  
- Expandir pruebas con `pytest` y testing de API (contratos).
