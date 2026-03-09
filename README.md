# Challenge-Telecom-X-Par2
# 📄✨ Informe Final 
**Telecom X – Parte 2: Predicción de Cancelación**

---

## 🧩 Introducción

Este informe analiza los **factores que afectan la cancelación de clientes** (churn) y evalúa el desempeño de los modelos predictivos. Se entrenaron **4 modelos de clasificación** con y sin balanceo:

- 🔹 **Regresión Logística (Normal)**  
  - Lineal e interpretable.  
  - Sin balanceo: favorece la clase mayoritaria, bajo recall en churn.

- 🔹 **Random Forest (Normal)**  
  - Ensamble de árboles de decisión.  
  - Sin balanceo: buen desempeño en clase “No”, pero bajo recall en “Sí”.

- 🔹 **Regresión Logística (Balanceada)**  
  - Ajuste de pesos (`class_weight='balanced'`).  
  - Mejora la detección de la clase minoritaria sin alterar los datos.

- 🔹 **Regresión Logística (Balanceada + SMOTE)**  
  - Combina balanceo de pesos y sobremuestreo sintético.  
  - Mayor recall para churn, manteniendo interpretabilidad.

**💡 Resumen:** Todos son clasificadores supervisados; la diferencia está en el tipo de modelo y el uso de técnicas de balanceo para la clase minoritaria.

---

## 🎯 Objetivo

Identificar los factores clave que afectan la cancelación de clientes y proponer estrategias de retención basadas en resultados predictivos.

---

## 📊 Resumen Ejecutivo de Modelos

| Modelo | Clase | Precisión | Recall | F1-score | Accuracy | Resumen |
|--------|-------|-----------|--------|----------|----------|---------|
| **Logística Normal** | No | 0.84 | 0.90 | 0.87 | 0.80 | Detecta bien clientes que permanecen, pero pierde casi la mitad de los que cancelan. |
| | Sí | 0.65 | 0.52 | 0.58 | 0.80 | Bajo recall para churn. |
| **Random Forest Normal** | No | 0.83 | 0.90 | 0.87 | 0.79 | Similar a logística normal, buen desempeño en “No”. |
| | Sí | 0.64 | 0.50 | 0.56 | 0.79 | Bajo recall para churn. |
| **Logística Balanceada** | No | 0.91 | 0.73 | 0.81 | 0.75 | Alta precisión en “No”, sacrificando recall. |
| | Sí | 0.52 | 0.80 | 0.63 | 0.75 | Mejor recall en churn. |
| **Logística Balanceada + SMOTE** | No | 0.88 | 0.79 | - | 0.76 | Buen desempeño en “No”, algunos falsos positivos. |
| | Sí | 0.54 | 0.69 | - | 0.76 | Mejor recall en churn, precisión moderada. |

---

## 🔍 Factores que más influyen en la cancelación

- ⏱ **Tiempo de permanencia:** Churn ocurre principalmente en clientes < 10 meses.  
- 🌐 **Tipo de internet:** Fibra óptica aumenta riesgo.  
- 📺 **Servicios de streaming:** Uso de TV y películas incrementa churn.  
- 📄 **Tipo de contrato:** Mensual → mayor probabilidad de abandono.  
- 💰 **Valor mensual y gasto acumulado:** Clientes de alto gasto son más estables.  
- 🛡 **Antigüedad del contrato:** Reduce riesgo de cancelación.

**💡 Insight:** SMOTE y balanceo aumentan el recall de la clase “Sí” a 0.69, detectando más clientes en riesgo.

---

## 🎯 Recomendaciones – Estrategias de Retención

1. **Onboarding y contratos largos**  
   - Incentivar contratos anuales/bianuales y monitoreo de calidad del servicio.  
   - Enfocarse en clientes con contratos < 10 meses.

2. **Optimizar métodos de pago**  
   - Promover pagos automáticos y alertas proactivas a clientes con pagos manuales.

3. **Protección de segmentos vulnerables**  
   - Adultos mayores (+60), clientes sin pareja o soporte técnico.  
   - Estrategias: soporte personalizado y paquetes de valor agregado.

4. **Gestión de valor y streaming**  
   - Clientes de mayor gasto son más leales.  
   - Analizar uso de streaming y ajustar oferta o experiencia.

5. **Modelo recomendado**  
   - **Regresión Logística Balanceada + SMOTE**  
   - Detecta mejor clientes en riesgo (recall 0.69) manteniendo interpretabilidad.

---

## 🏁 Conclusión

El **modelo de Regresión Logística Balanceada con SMOTE** es el más recomendable para predecir cancelaciones.  

- **Ventaja clave:** Maximiza la detección de clientes que realmente abandonan (recall de 0.69).  
- **Interpretabilidad:** Permite identificar factores específicos (fibra óptica, tiempo de contrato, gasto mensual) y diseñar estrategias de retención focalizadas.  
- **Estrategia:** Priorizar intervención temprana, contratos largos, automatización de pagos y monitorización de clientes en riesgo.

**🔥 Justificación:**  
Aunque la precisión de la clase “Sí” baja ligeramente (0.54 vs 0.65), el aumento en recall asegura que más clientes que realmente cancelarían sean detectados, evitando pérdidas críticas y optimizando recursos de retención.
