# Modelo Fine-Tuned BETO

Este directorio corresponde al modelo **BETO** fine-tuned con nuestro dataset de 1000 frases políticas en español.

## Hiperparámetros de entrenamiento
- Modelo base: `dccuchile/bert-base-spanish-wwm-cased`
- Épocas: 5
- Batch size: 8 (train y eval)
- Learning rate: 3e-5
- Weight decay: 0.005
- Estrategia de evaluación: por época
- Métrica principal: Accuracy, F1-score

## Descarga del modelo
Debido a su tamaño, los pesos del modelo no están incluidos en este repositorio.  
Se pueden descargar en el siguiente enlace:

👉 [Google Drive / HuggingFace link aquí]

## Uso en Python
```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("usuario/beto_gpu")
model = AutoModelForSequenceClassification.from_pretrained("usuario/beto_gpu")
