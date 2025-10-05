---
layout: project
title: Iris — API Flask
subtitle: Clasificación Iris servida como API REST contenedorizada
permalink: /proyecto-iris/
repo: https://github.com/eagomezdaza/iris-flask-docker-api
stack: Flask · Docker · scikit-learn · pytest (si aplica)
tags: [Flask, Docker, scikit-learn]
---

## Resumen
Modelo de clasificación Iris entrenado con scikit-learn y servido como API REST. Incluye validaciones, manejo de errores y pruebas.

## Ejecutar localmente
```bash
git clone https://github.com/eagomezdaza/iris-flask-docker-api
cd iris-flask-docker-api
docker build -t iris-api .
docker run -p 8000:8000 iris-api