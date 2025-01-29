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
| **PCA**                  | 74.5%     | 0.81    | 0.63   | 0.68     | 0.xx     | Ligera pérdida de rendimiento.              |  
| **Tratamiento Outliers** | 78.6%     | 0.83    | 0.64   | 0.78     | 0.62     | Mejor resultado en todas las métricas.      |  

---

### **5.3 Gráficos del Mejor Modelo**  
El mejor modelo, **Random Forest con tratamiento de outliers**, logró el mayor rendimiento. Los gráficos más relevantes incluyen:  
1. **Curva ROC**: Comparación entre el modelo base y el modelo optimizado.  
2. **Matriz de Confusión**: Desglose de verdaderos positivos, verdaderos negativos, falsos positivos y falsos negativos.  
3. **Importancia de las Características**: Variables más influyentes después de las optimizaciones.  
4. **Distribución de Predicciones Probabilísticas**: Muestra cómo el modelo ajustado asigna probabilidades más confiables.  

---

### **Conclusión Final de Evaluación**  
El tratamiento de outliers fue la técnica más efectiva, logrando:  
- **AUC-ROC**: Incremento del 0.84 al 0.87.  
- **Recall**: Mejor detección de sobrevivientes, pasando del 0.78 al 0.81.  
- **Log Loss**: Reducción significativa, indicando un modelo más confiable para probabilidades.  

---

## **6. Despliegue y Conclusión**  
El modelo final se implementó en un script ejecutable que permite cargar nuevos datos y predecir la supervivencia.  

### **Conclusiones**  
- La supervivencia depende significativamente de factores sociales y económicos.  
- Este proyecto demuestra la utilidad de Machine Learning para el análisis predictivo.  

### **Próximos pasos**  
- Optimización adicional del modelo.  
- Considerar datos adicionales para enriquecer el análisis.  

---

## **7. Estructura del Repositorio**  
- `notebooks/`: Contiene los Jupyter Notebooks con el análisis detallado.  
- `data/`: Dataset original y procesado.  
- `scripts/`: Scripts Python para preprocesamiento y predicción.  
- `models/`: Modelos entrenados guardados como archivos `.pkl`.  
- `README.md`: Documentación del proyecto.  

---

## **8. Créditos**  
- Dataset: [Kaggle Titanic Challenge](https://www.kaggle.com/c/titanic).  
- Autor: Eliana Méndez.  
