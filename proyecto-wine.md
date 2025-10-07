---
layout: project
title: Wine — Clasificación
subtitle: Clasificación de vinos con scikit-learn y validación cruzada
permalink: /proyecto-wine/
repo: https://github.com/eagomezdaza/proyecto-wine
dataset: UCI Wine dataset (13 features, 3 clases)
stack: Python · scikit-learn · pandas · matplotlib · Colab
tags: [Python, scikit-learn, CV]
---

## Tecnologías usadas
<div class="d-flex flex-wrap gap-2 mb-3">
  <span class="badge bg-primary">Python</span>
  <span class="badge bg-info text-dark">scikit-learn</span>
  <span class="badge bg-secondary">pandas</span>
  <span class="badge bg-success">matplotlib</span>
  <span class="badge bg-dark">Google Colab</span>
</div>

## Resumen
Proyecto de aprendizaje supervisado para clasificar tipos de vino utilizando el dataset **Wine** de UCI.  
Incluye análisis exploratorio, preprocesamiento (escalado y codificación), validación cruzada y comparación de modelos.


## Cómo ejecutar
1. Abre el repositorio: <a href="https://github.com/eagomezdaza/proyecto-wine" target="_blank" rel="noopener">proyecto-wine</a>  
2. Ejecuta el notebook en Google Colab o localmente:

```bash
git clone https://github.com/eagomezdaza/proyecto-wine
cd proyecto-wine
pip install -r requirements.txt
jupyter notebook
```

## Métricas

<div class="table-responsive">

| Modelo                    | Accuracy | F1-macro | Precision | Recall |
|:--------------------------|---------:|---------:|----------:|-------:|
| Regresión Logística (OVR) | 0.97     | 0.96     | 0.97      | 0.96   |
| SVM (RBF)                 | 0.96     | 0.95     | 0.96      | 0.95   |
| Random Forest             | 0.98     | 0.97     | 0.98      | 0.97   |
{: .table .table-sm .table-hover .align-middle }

</div>

> Las métricas se calcularon con validación cruzada estratificada (`cv=5`) y evaluación independiente en conjunto de prueba (30%).


## Capturas de resultados

<div class="gallery row g-3">
  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/wine/confusion-matrix.png' | relative_url }}"
           alt="Matriz de confusión" loading="lazy" decoding="async">
      <figcaption class="figure-caption">
        Matriz de confusión — desempeño por clase
      </figcaption>
    </figure>
  </div>

  <div class="col-md-6">
    <figure class="figure w-100">
      <img class="img-fluid rounded shadow capture"
           src="{{ '/assets/images/wine/roc-curves.png' | relative_url }}"
           alt="Curvas ROC" loading="lazy" decoding="async">
      <figcaption class="figure-caption">
        Curvas ROC (OVR) para las tres clases
      </figcaption>
    </figure>
  </div>
</div>

## Conclusiones
- **Random Forest** mostró el mejor rendimiento general con AUC > 0.97 en todas las clases.  
- El **escalado de variables** benefició especialmente a los modelos lineales (SVM, Logística).  
- Los resultados validan la robustez del pipeline y la correcta separación de clases en el espacio multivariado.


## Próximos pasos
- Implementar **GridSearchCV** para afinar hiperparámetros.  
- Agregar interpretabilidad con **SHAP** y análisis de importancia de variables.  
- Documentar resultados comparativos en formato reproducible (`.ipynb` y `.html`).

