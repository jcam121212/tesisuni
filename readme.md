# Proyecto Tesis UNI

## 📂 Estructura del repositorio
- **data/raw/** → Dataset original (1000 frases políticas en español).
- **notebooks/** → EDA y fine-tuning BETO.
- **src/web/** → Prototipo en Flask.
- **src/beto_gpu/** → Documentación del modelo fine-tuned.
- **logs/** → Resultados y métricas.
- **README.md** → Documento principal.

## 📊 Dataset
- **Fuente:** Dataset propio recopilado y etiquetado manualmente.
- **Clases:** 4 categorías de retórica política.
- **Formato:** CSV y XLSX.

## 🧠 Modelos
- **Baseline:** Modelo simple (Naive Bayes, Regresión logística).
- **Fine-tuned BETO:**  
  - Modelo base: `dccuchile/bert-base-spanish-wwm-cased`  
  - Épocas: 5  
  - Batch size: 8  
  - Learning rate: 3e-5  
  - Métrica principal: Accuracy y F1-score  

## 📈 Resultados
- Baseline: Accuracy ≈ 0.65  
- BETO Fine-tuned: Accuracy ≈ 0.88, F1 ≈ 0.87  

## 🌐 Prototipo Web
- Implementado en Flask.  
- Permite ingresar frases políticas y clasificarlas automáticamente.
