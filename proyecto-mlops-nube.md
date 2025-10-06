---
layout: project
title: MLOps en la Nube
subtitle: API Flask contenedorizada y desplegada en Azure con CI/CD
permalink: /mlops-nube/
repo: https://github.com/eagomezdaza/Mod10-Evaluacion_Modular
dataset: Breast Cancer Wisconsin (30 features, 2 clases)
stack: Python · Flask · Docker · GitHub Actions · Azure
tags: [Flask, Docker, Azure, CI/CD]
---

## Tecnologías usadas
<div class="d-flex flex-wrap gap-2 mb-3">
  <span class="badge bg-primary">Python</span>
  <span class="badge bg-info text-dark">Flask</span>
  <span class="badge bg-secondary">Docker</span>
  <span class="badge bg-warning text-dark">GitHub Actions</span>
  <span class="badge bg-dark">Azure</span>
</div>

## Resumen
Proyecto **MLOps** que implementa una API REST con **Flask** para exponer un modelo de clasificación de cáncer de mama entrenado con el dataset *Breast Cancer Wisconsin*.  
El flujo completo integra **entrenamiento reproducible**, **contenedorización con Docker**, **automatización CI/CD con GitHub Actions** y **despliegue en Azure Container Apps**.  
Incluye validación de entradas, logging estructurado y métricas para monitoreo.

---

## Cómo ejecutar localmente
1. Clonar el repositorio:
   ```bash
   git clone https://github.com/eagomezdaza/Mod10-Evaluacion_Modular
   cd Mod10-Evaluacion_Modular
   ```
2. Entrenar el modelo:
   ```bash
   make train
   ```
3. Ejecutar la API:
   ```bash
   make run
   ```
   Acceso local en `http://127.0.0.1:5000`

4. Construir y ejecutar contenedor Docker:
   ```bash
   make build
   make run-docker
   ```

---

## Endpoints principales
| Método | Endpoint | Descripción |
|:-------|:----------|:-------------|
| `GET` | `/health` | Estado del modelo y metadatos |
| `POST` | `/predict` | Predicción a partir de 30 features |
| `GET` | `/metrics` | Exposición de métricas Prometheus |

> Ejemplo:  
> ```bash
> curl -X POST http://127.0.0.1:5000/predict \
>   -H "Content-Type: application/json" \
>   -d @tests/data/sample.json
> ```

---

## Despliegue en Azure
El pipeline de **GitHub Actions** automatiza pruebas, construcción y publicación de la imagen Docker en **Azure Container Registry (ACR)**, seguido del despliegue en **Azure Container Apps (ACA)**.

### Pasos principales
1. `make push RG=rg-evalmod ACR=acrevalmod`  
   → Publica la imagen en el registro.  
2. `make update-aca RG=rg-evalmod ACR=acrevalmod`  
   → Actualiza el contenedor en producción.  
3. Monitoreo con:
   ```bash
   az containerapp logs show -g rg-evalmod -n evalmod-api --follow
   ```

---

## Métricas de despliegue
| Métrica        | Valor |
|---------------:|:-----:|
| Latencia p95   | 120 ms |
| Throughput     | 50 req/s |
| Uptime         | 99.9 % |
| Tamaño imagen  | 186 MB |

> Valores medidos con monitoreo básico de contenedor en Azure.

---

## Capturas de referencia
<div class="gallery row g-3">
  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/mlops/pipeline-actions.png' | relative_url }}"
           alt="Pipeline GitHub Actions" loading="lazy" decoding="async">
      <figcaption class="figure-caption">Pipeline automatizado en GitHub Actions — ejecución de pruebas, build y deploy hacia Azure.</figcaption>
    </figure>
  </div>
  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/mlops/azure-deploy.png' | relative_url }}"
           alt="Despliegue en Azure Container Apps" loading="lazy" decoding="async">
      <figcaption class="figure-caption">Despliegue exitoso del contenedor en Azure Container Apps con endpoint público.</figcaption>
    </figure>
  </div>

  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/mlops/logs-monitor.png' | relative_url }}"
           alt="Monitoreo de logs en Azure" loading="lazy" decoding="async">
      <figcaption class="figure-caption">Logs JSON estructurados y métricas de rendimiento accesibles desde Azure Monitor.</figcaption>
    </figure>
  </div>
  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/mlops/container-status.png' | relative_url }}"
           alt="Estado del contenedor" loading="lazy" decoding="async">
      <figcaption class="figure-caption">Verificación del estado HEALTHY del contenedor y métricas de disponibilidad.</figcaption>
    </figure>
  </div>
</div>

---

## Conclusiones
- Se logró un **pipeline CI/CD funcional** con despliegue automatizado en la nube.  
- La **contenedorización** garantiza portabilidad y reproducibilidad del entorno.  
- El sistema mantiene **alta disponibilidad (>99.9%)** y baja latencia.  
- La integración con **Prometheus** y **Azure Logs** facilita el monitoreo en producción.

---

## Próximos pasos
- Incorporar **observabilidad avanzada** (Prometheus + Grafana).  
- Implementar **rollback automatizado** ante fallos de despliegue.  
- Extender las pruebas unitarias y de integración con **pytest** y *API contracts*.  
- Publicar guía de despliegue y métricas de rendimiento.

---
