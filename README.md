# **Análisis de Supervivencia en el Titanic: Proyecto de Machine Learning**

## **1. Introducción y Objetivos del Proyecto (Comprensión del Negocio)**  
Este proyecto tiene como objetivo predecir la supervivencia de los pasajeros del Titanic basándonos en características como edad, género, clase del boleto, entre otros.  
El análisis sigue el modelo CRISP-DM para garantizar un enfoque estructurado.  

### **Objetivo del Negocio**  
- Determinar los factores más influyentes en la probabilidad de supervivencia.  
- Crear un modelo predictivo que permita clasificar a los pasajeros como sobrevivientes o no sobrevivientes.  

---

## **2. Comprensión de los Datos**  
El dataset utilizado proviene del [desafío Titanic de Kaggle](https://www.kaggle.com/c/titanic).  

### **Descripción de los Datos**  
- **Columnas principales**:  
  - `PassengerId`: Identificador único del pasajero.  
  - `Survived`: 0 = No sobrevivió, 1 = Sobrevivió.  
  - `Pclass`: Clase del boleto (1, 2, 3).  
  - `Sex`: Género.  
  - `Age`: Edad.  
  - `Fare`: Tarifa pagada.  
  - `Embarked`: Puerto de embarque (`C`, `Q`, `S`).  

### **Exploración inicial**  
- Dimensiones del dataset.  
- Valores nulos o faltantes.  

---

## **3. Preparación de los Datos**  
Se realizaron las siguientes tareas:  
1. **Limpieza**:  
   - Imputación de valores faltantes en las columnas `Age` y `Embarked`.  
   - Eliminación de columnas irrelevantes (`PassengerId`, `Name`, `Ticket`, `Cabin`).  
2. **Transformación**:  
   - Codificación de variables categóricas (`Sex`, `Embarked`).      
3. **Creación de nuevas características**:  
   - Creación de variable `FamilySize` basada en `SibSp` y `Parch`.
   - Creación de variable `IsAlone` para indicar las personas que viajan solas, partiendo de `FamilySize`.
   - Creación de varibale `Family_Size_Ordinal` que captura la influencia del tamaño de la familia en la predicción. 

---

## **4. Modelado**  
Se utilizaron los siguientes modelos de Machine Learning:  
1. **Regresión Logística**  
2. **K-Nearest Neighbors (KNN)**  
3. **Random Forest**    

### **Metodología**  
- División del dataset en conjuntos de entrenamiento (67%) y prueba (33%).  
- Evaluación mediante validación cruzada.  

### **Métricas de evaluación**  
- Precisión (`Accuracy`).  
- Matriz de confusión.  
- Área bajo la curva ROC (AUC-ROC).  

---

## **5. Evaluación de Resultados**

### **Análisis General**  
Se evaluaron varios modelos y técnicas de optimización para maximizar el rendimiento predictivo.  

### **5.1 Métricas Incluidas**  
- **Precisión**: Porcentaje de predicciones correctas sobre el total.  
- **AUC-ROC**: Mide la capacidad del modelo para distinguir entre clases.  
- **Recall (Sensibilidad)**: Capacidad del modelo para identificar correctamente los sobrevivientes.  
- **F1-Score**: Equilibrio entre precisión y sensibilidad.  
- **Log Loss**: Pérdida logarítmica, útil para modelos probabilísticos. 

### **5.2 Comparativo de Resultados**  

| Técnica                  | Precisión | AUC-ROC | Recall | F1-Score | Log Loss | Comentarios                                   |  
|--------------------------|-----------|---------|--------|----------|----------|---------------------------------------------|  
| **Modelo Base**          | 78.3%     | 0.83    | 0.62   | 0.70     | 0.62     | Sin optimizaciones adicionales.             |  
| **PCA**                  | 78.9%     | 0.83    | 0.62   | 0.69     | 0.52     | Ligera pérdida de rendimiento.              |  
| **Tratamiento Outliers** | 77.2%     | 0.83    | 0.63   | 0.77     | 0.62     | Mejor resultado en todas las métricas.      |  

---

### **Conclusión Final de Evaluación**  
Tras evaluar las técnicas aplicadas (**Modelo Base**, **PCA** y **Tratamiento Outliers**), se identificaron las siguientes características principales de cada modelo:

1. **Modelo Base**  
   - Ofrece un rendimiento equilibrado sin necesidad de transformaciones adicionales.  
   - Métricas clave: **Precisión (78.3%)**, **AUC-ROC (0.83)**, **F1-Score (0.70)** y **Log Loss (0.62)**.  
   - Es una solución competitiva y sencilla, ideal si se prioriza simplicidad.

2. **PCA**  
   - Destaca por la mayor **precisión (78.9%)** y la mejor calibración de predicciones, con el menor **Log Loss (0.52)**.  
   - Métricas clave: **AUC-ROC (0.83)**, **Recall (0.62)** y **F1-Score (0.69)**.  
   - Es ideal si se busca confianza en las probabilidades y un modelo optimizado para precisión.

3. **Tratamiento Outliers**  
   - Es la mejor opción para minimizar falsos negativos, logrando el mayor **recall (0.63)** y **F1-Score (0.77)**.  
   - Métricas clave: **Precisión (77.2%)**, **AUC-ROC (0.83)** y **Log Loss (0.62)**.  
   - Recomendado para escenarios en los que clasificar erróneamente casos positivos tiene un alto costo.

### Modelo Seleccionado
La elección depende de los objetivos específicos:  
- **Tratamiento Outliers** es preferible para maximizar el recall y el F1-Score.  
- **PCA** es adecuado si la prioridad es precisión y predicciones bien calibradas.  
- **Modelo Base** es una alternativa válida por su simplicidad y buen desempeño general.
  
---

### **Conclusiones**  
- A partir de los datos utilizados y mediante la utilización de técnicas avanzadas de Machine Learning, se pudo concluir que la supervivencia de los pasajeros de Titanic dependío significativamente de factores sociales y económicos, ya que variables relacionadas con tamaño de la familia, clase del boleto y tarifa pagadas aportaron información relevante para la predictibilidad del modelo.  
- Este proyecto demuestró la utilidad de Machine Learning para el análisis predictivo de situaciones reales que pueden ser llevadas a diferentes contextos.  

---

## **6. Estructura del Repositorio**  
- `Desafio-Titanic-4.ipynb/`: Contiene los Jupyter Notebooks con el análisis detallado.  
- `README.md`: Documentación del proyecto.  

---

## **7. Créditos**  
- Dataset: [Kaggle Titanic Challenge](https://www.kaggle.com/c/titanic).  
- Autor: Eliana Méndez.  
- Mentor: Agradecimientos especiales a Zurisadai Velazquez Manzanero, por la oportunidad de hacer parte de ésta iniciativa en la que nos compartió conocimiento valioso, por toda su entrega desinteresada para seguir aportando a nuestro crecimiento.
