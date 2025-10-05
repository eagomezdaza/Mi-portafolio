---
layout: project
title: MLOps en la Nube
subtitle: API Flask contenedorizada y desplegada en Azure con CI/CD
permalink: /mlops-nube/
repo: https://github.com/eagomezdaza/Mod10-Evaluacion_Modular
stack: Flask · Docker · GitHub Actions · Azure
tags: [Flask, Docker, Azure, CI/CD]
---

## Resumen
Sistema MLOps que expone un modelo de ML como API REST con Flask, se empaqueta con Docker y se despliega en Azure. Pipeline automatizado con GitHub Actions.

## Endpoints típicos
- `GET /health` — estado del servicio  
- `POST /predict` — recibe features y devuelve predicción

## Ejecutar localmente
```bash
git clone https://github.com/eagomezdaza/Mod10-Evaluacion_Modular
cd Mod10-Evaluacion_Modular
docker build -t mlops-api .
docker run -p 8000:8000 mlops-api
