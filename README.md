# 🟤 Clasificación Automática de Granos de Cacao por Madurez y Calidad

Este proyecto aborda el desarrollo de un sistema automático de clasificación de granos de cacao utilizando técnicas avanzadas de visión por computador. El objetivo principal es identificar correctamente cinco clases de grano según su madurez y calidad, comparando redes neuronales profundas (YOLOv8) con modelos clásicos como KNN, SVM y Random Forest.

🌱 Contexto del Dataset

El conjunto de datos utilizado en este proyecto fue construido a partir de imágenes reales de granos de cacao recolectadas en distintas etapas del desarrollo del fruto. El articulo con la descripción del dataset se puede encontrar https://zenodo.org/records/7968315 propuesto en colaboración por el profesor Juan Felipe Restrepo Arias docente de la universidad Eafit. Estas imágenes fueron capturadas en condiciones de laboratorio y de campo, y representan cinco categorías clave:
	•	C1 (0–2 meses): Granos inmaduros, de color verde claro, tamaño pequeño y textura lisa.
	•	C2 (2–4 meses): Granos en transición, más grandes, con tonalidades verde oscuro o amarillentas.
	•	C3 (4–6 meses): Granos maduros, de mayor tamaño, con cambios visibles en textura y color.
	•	C4 (>6 meses): Granos completamente maduros, oscuros, con signos externos de fermentación o endurecimiento.
	•	A (Abortos): Granos defectuosos que no completaron su proceso de desarrollo, comúnmente más pequeños, secos o deformes.

Las imágenes están organizadas en carpetas por clase, y las anotaciones se encuentran en formato COCO (.json). Este dataset simula un escenario real en el que es necesario automatizar la clasificación de frutos para procesos de selección, exportación o evaluación genética.

El desequilibrio en el número de muestras por clase (especialmente en la clase A) refleja un escenario realista, donde los casos anómalos son menos frecuentes, y plantea un desafío adicional para los modelos de clasificación.
---

## 🎯 Objetivos

- Detectar y clasificar automáticamente granos de cacao en diferentes etapas de madurez.
- Comparar el desempeño de modelos tradicionales de clasificación con una arquitectura de detección moderna (YOLOv8).
- Generar un pipeline completo de entrenamiento, evaluación y visualización de resultados.
- Construir un dataset estructurado a partir de imágenes reales y anotaciones en formato COCO.

---

## 🧪 Clases del Proyecto

| Etiqueta | Descripción           |
|---------:|------------------------|
| `C1`     | Granos de 0–2 meses    |
| `C2`     | Granos de 2–4 meses    |
| `C3`     | Granos de 4–6 meses    |
| `C4`     | Granos de más de 6 meses |
| `A`      | Granos anómalos (abortos)

---

## 🧠 Modelos Evaluados

| Modelo          | Tipo                     |
|------------------|--------------------------|
| `YOLOv8`         | Red neuronal convolucional para detección de objetos (Ultralytics)  
| `KNN`            | Clasificación por vecinos más cercanos  
| `SVM`            | Máquinas de vectores de soporte (kernel lineal)  
| `Random Forest`  | Ensamble de árboles de decisión  

---

## 📊 Resultados

Los modelos fueron evaluados usando **matrices de confusión normalizadas**, **accuracy** y **precisión por clase**. A continuación, una comparación de las precisiones por clase:

| Modelo         | C1   | C2   | C3   | C4   | A    |
|----------------|------|------|------|------|------|
| **KNN**        | 87%  | 38%  | 44%  | 33%  | 0%   |
| **SVM**        | 90%  | 54%  | 29%  | 39%  | 0%   |
| **Random Forest** | 89% | 35% | 46% | 43% | 0%   |
| **YOLOv8**     | 87%  | 91%  | 98%  | 81%  | 70%  |

> 🏆 **YOLOv8 superó a todos los modelos clásicos**, especialmente en clases difíciles como `C2`, `C3`, `C4` y `A`.

---

## 🗂️ Estructura del Proyecto

```
project/
├── dataset/
│   ├── annotations/             # Anotaciones en formato COCO JSON
│   ├── Images_C1/…/Images_A/    # Carpetas con imágenes por clase
├── Dataset-YOLO/                # Dataset listo para YOLOv8
│   ├── images/train/val/
│   ├── labels/train/val/
│   └── data.yaml
├── confusion_matrices/          # Imágenes de matrices por modelo
├── notebooks/
│   ├── Clasificacion_yolo.ipynb
│   └── Clasificacion_modelos.ipynb
├── runs/detect/train*/          # Resultados del entrenamiento YOLO
```

---

## 📈 Métricas para YOLOv8

- `mAP@50`: 94.5%  
- `mAP@50-95`: 86.4%  
- `Precision`: ↑ hasta 78%  
- `Recall`: ↑ hasta 77%  
- Mejor clase detectada: `C3` con 98% de precisión  
- Único modelo que logró clasificar `A` con 70% de precisión

---

## ⚙️ Tecnologías Usadas

- **Python 3.11**
- **YOLOv8 (Ultralytics)**
- **Scikit-learn**
- **OpenCV, Pandas, NumPy**
- **Matplotlib & Seaborn**


---

## ✅ Conclusiones

- YOLOv8 es altamente efectivo para tareas de clasificación visual con clases visualmente similares.
- Los modelos clásicos pueden ser útiles, pero no alcanzan el nivel de generalización de una red convolucional.
- El modelo es escalable y puede adaptarse a otros productos agrícolas o sistemas de control de calidad.

---

## 📬 Contacto

Autor: **Sebastián Gómez Zapata**  
Proyecto académico - Visión Artificial  
Universidad **Nacional de Colombia sede Medellín**  
Correo: **segomezz@unal.edu.co**
