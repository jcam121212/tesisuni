# Sistema Clasificador BETO Fine-Tuned para Análisis Retórico en Frases Políticas (Ad-hominem, Framing, Lógica y Retórica Vacía) – Versión 3.0

## 🧩 Actualización V3.0 — Pipeline de Datos y Entrenamiento

Esta versión consolida un pipeline experimental más sólido y reproducible para la
clasificación automática de estrategias retóricas en frases políticas en español.

Principales cambios respecto a versiones anteriores:

- **Depuración exhaustiva del corpus**
  - Normalización de texto y corrección de problemas de codificación.
  - Eliminación de duplicados y casi duplicados.
  - Enmascarado de nombres propios y actores políticos mediante tokens neutros
    (p. ej., `[POLITICO]`, `[PARTIDO]`) para reducir el sobreajuste a figuras
    específicas.

- **Particionado sin fuga de información**
  - Asignación de un `group_id` para agrupar frases similares o provenientes de
    la misma fuente.
  - Generación de 5 folds con `StratifiedGroupKFold`, garantizando:
    - estratificación por clase (mismas proporciones de etiquetas en cada fold);
    - no mezclar frases del mismo grupo entre entrenamiento y prueba.

- **Comparación clara entre modelos**
  - **Baseline clásico:** TF-IDF + Regresión Logística multinomial.
  - **Modelo propuesto:** BETO fine-tuned como clasificador de 4 etiquetas.

- **Evaluación rigurosa**
  - Validación cruzada en 5 folds sobre el corpus depurado.
  - Hold-out interno (Fold 4) para análisis detallado.
  - Hold-out externo (“humano”): frases inéditas, redactadas manualmente.
  - Métricas: Accuracy, F1-macro, matriz de confusión e inspección de errores.

**Usuarios expertos asociados al proyecto**

- Elizabeth Ramírez (periodista)  
- Jim Delgado (politólogo, jefe de prensa Antauro Humala)

Los resultados muestran una separación muy nítida entre las clases retóricas
(Ad-hominem, Framing binario, Lógica/Logos y Retórica vacía), sin evidencia de
sobreajuste por duplicidad de muestras ni fuga de información entre entrenamiento
y prueba.

---

## 📂 Estructura del repositorio

```text
.
├─ data/
│  ├─ processed/
│  │  ├─ corpus_clean_v3_folds.csv   # corpus depurado con etiquetas, group_id y fold
│  │  └─ holdout_humano.csv          # frases inéditas para evaluación externa
│  └─ raw/                            # datos sin procesar (no versionados en git)
├─ models/
│  └─ beto_v3_final_fold0/           # modelo BETO fine-tuned + tokenizer
├─ notebooks/
│  ├─ 1_depurando_dataset_v3.ipynb
│  ├─ 2_baseline_tfidf_lr_v3.ipynb
│  ├─ 3_fine_tuning_v3.ipynb
│  ├─ 4_inferencia_beto_v3.ipynb
│  ├─ 5_analisis_resultados_beto_v3.ipynb
│  └─ 6_slices_analisis_beto_v3.ipynb
├─ src/
│  ├─ web/         # prototipo web / frontend (Flask o similar)
│  └─ beto_gpu/    # código y documentación relacionados al entrenamiento en GPU
├─ logs/           # métricas y registros de entrenamiento/validación
└─ README.md       # este documento
