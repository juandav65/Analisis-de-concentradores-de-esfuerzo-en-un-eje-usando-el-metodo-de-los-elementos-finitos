# Análisis de Concentradores de Esfuerzo en un Eje mediante el Método de los Elementos Finitos

**Universidad Nacional de Colombia — Facultad de Ingeniería**  
**Programa:** Ingeniería Mecánica | **Año:** 2025

---

## Autores

| Nombre | Correo |
|--------|--------|
| Nagem Samir Merheb Suarez | nmerheb@unal.edu.co |
| Jose David Garzón Gonzalez | jogarzong@unal.edu.co |
| Juan David Medina Perez | jmedinape@unal.edu.co |
| Alejandro Perdomo Delgado | alperdomod@unal.edu.co |

**Profesores:** Diego Alexander Garzon Alvarado — Diego Alfredo Quexada Rodriguez

---

## Descripción del Proyecto

Este proyecto analiza los concentradores de esfuerzo en distintas geometrías de ejes mediante el **Método de los Elementos Finitos (MEF)**, comparando los resultados de simulación con los coeficientes teóricos de Peterson. Se busca validar la precisión de ambos modelos y evaluar su confiabilidad en contextos de diseño mecánico real.

El enfoque se centra en **elementos 3D**, concentradores de esfuerzos bajo **falla estática**, usando elementos tipo *brick* en el software **Ansys 2025 R1**.

---

## Objetivos

**General**  
Determinar los esfuerzos en distintos concentradores de esfuerzo en ejes mediante el MEF y compararlos con los coeficientes de Peterson para evaluar la precisión de ambos modelos.

**Específicos**
- Diagramar el factor de concentración de esfuerzos (Kt) sobre 4 secciones de ejes distintas obtenidas a partir de simulación.
- Cuantificar el error entre los resultados teóricos y los obtenidos mediante simulación.
- Realizar el análisis de concentradores de esfuerzos para ejes estriados (chaveteros).

---

## Relevancia e Impacto

El estudio de concentradores de esfuerzo en chaveteros y filetes es crítico en industrias como la **automotriz**, **aeroespacial** y de **manufactura**, donde los ejes y acoplamientos son elementos de alta responsabilidad. Un diseño optimizado:

- Reduce costos de producción y mantenimiento.
- Previene fallas catastróficas en sistemas mecánicos.
- Mejora la fiabilidad y el rendimiento de los equipos.

---

## Metodología

```
1. Modelado Geométrico    → Creación del modelo 3D en CAD
2. Parametrización        → Definición de parámetros geométricos (radio de filete)
3. Análisis MEF           → Importación a Ansys, condiciones de contorno
4. Simulación Paramétrica → Variación del radio (0.15 mm a 1 mm, paso 0.05 mm)
5. Análisis de Resultados → Evaluación de esfuerzos por configuración
6. Optimización           → Identificación del radio que minimiza la concentración
7. Convergencia de Malla  → Validación de independencia de malla
```

---

## Casos Analizados

### 1. Eje Escalonado a Torsión (D/d = 2)

**Configuración:** Radio mayor R = 28 mm, radio menor r = 14 mm.  
**Carga aplicada:** Momento torsor de 100 N·m en dirección axial.  
**Condición de frontera:** Cara de mayor diámetro empotrada (Fixed Support).

**Malla:**
- Cuerpo general: elementos de 0.008 m
- Zona del filete (refinada): elementos de 0.002 m

**Fórmula teórica (Peterson):**

$$K_t = A \left(\frac{r}{28\,\text{mm}}\right)^b$$

Con constantes para D/d = 2: `A = 0.90879`, `b = -0.28598`.

**Resultados:**
- El esfuerzo cortante nominal obtenido por simulación fue de **2.3241×10⁷ Pa**, con un error del **1.8%** respecto al valor teórico (2.32×10⁷ Pa).
- La convergencia de malla se realizó en 3 iteraciones (límite de licencia estudiantil), con una variación final **menor al 2%**.
- El comportamiento de Kt concuerda con la teoría para radios de filete mayores a **3.8 mm** (error < 5%).
- El error crece de forma exponencial cuando el radio del filete cae por debajo de **1 mm**.

| Iteración | Shear Stress (Pa) | Cambio (%) | Nodos  | Elementos |
|-----------|-------------------|------------|--------|-----------|
| 1         | 3.6687×10⁷        | —          | 12,430 | 7,592     |
| 2         | 4.1256×10⁷        | 11.725     | 45,394 | 30,602    |
| 3         | 4.1988×10⁷        | 1.7588     | 97,907 | 67,865    |

**Conclusión:** El modelo teórico predice con certeza los concentradores de esfuerzo para relaciones r/d > 0.1. Para radios menores, la divergencia exponencial indica una limitación física real: no pueden existir concentradores de esfuerzo infinitos como predice la teoría.

---

### 2. Eje con Dos Concentradores de Esfuerzo a Torsión

**Configuración:** Eje con dos filetes, separación paramétrica `a` entre radios grandes.  
**Carga aplicada:** Momento torsor de 100 N·mm.  
**Condición de frontera:** Fixed Support en un extremo.

**Malla:**
- Cuerpo general: elementos de 0.005 m
- Zona de filetes: elementos de 0.001 m

**Simulación paramétrica:** La distancia `a` varía de 15 mm a 100 mm (paso de 5 mm).

**Resultado principal:** El esfuerzo máximo se ubica dentro de los dos concentradores, confirmando la hipótesis de diseño. Los valores de esfuerzo cortante máximo permanecen en el rango de ~0.042 MPa con poca variación respecto a la separación entre concentradores.

| `a` (mm) | Shear Stress Max (MPa) |
|----------|------------------------|
| 15       | 0.043223               |
| 20       | 0.042083               |
| 50       | 0.043395               |
| 100      | 0.042696               |

---

### 3. Eje Macizo con Filete en la Mitad (Torsión)

**Configuración:** Eje macizo con una hendidura o filete central.  
**Carga aplicada:** Momento torsor de 100 N·m.  
**Referencia teórica:** Tabla de concentradores de Pilkey (Peterson's Stress Concentration Factors).

**Fórmula teórica:**

$$K_t = C_1 + C_2\frac{2h}{D} + C_3\left(\frac{2h}{D}\right)^2 + C_4\left(\frac{2h}{D}\right)^3$$

**Resultado:** Se obtuvo la variación del esfuerzo cortante máximo en función del radio del filete `r`, confirmando que el esfuerzo aumenta de forma pronunciada para r < 1 mm.

---

### 4. Chavetero a Flexión (sin coeficientes teóricos de referencia)

**Configuración:** Eje de acero estructural con chavetero estandarizado.  
**Carga aplicada:** Momento flector de 5000 N·m.  
**Condición de frontera:** Fixed Support en un extremo.

**Modelo constitutivo:**

$$F = [K]u \qquad \sigma = E\varepsilon \qquad \sigma = \frac{My}{I}$$

**Malla y convergencia:** Se realizó análisis de convergencia en 4 iteraciones:

| Iteración | Equivalent Stress (Pa) | Cambio (%) | Nodos  | Elementos |
|-----------|------------------------|------------|--------|-----------|
| 1         | 1.4061×10⁹             | —          | 1,357  | 837       |
| 2         | 2.4203×10⁹             | 53.011     | 7,286  | 4,813     |
| 3         | 2.7507×10⁹             | 12.781     | 20,179 | 13,819    |
| 4         | 2.7238×10⁹             | -0.98171   | 35,769 | 24,490    |

**Resultados tabulados (Kc vs r/d):**

| r_c (mm) | σ (MPa)    | K_c  | r_c/d   |
|----------|------------|------|---------|
| 0.15     | 4135.90    | 5.02 | 0.00375 |
| 0.25     | 3290.39    | 4.00 | 0.00625 |
| 0.50     | 2507.76    | 3.05 | 0.01250 |
| 0.75     | 2226.82    | 2.70 | 0.01875 |
| 1.00     | 1992.44    | 2.42 | 0.02500 |

**Tendencia general:**
- Para r_c/d < 0.01: Kc > 3.5, llegando hasta **5.02** (caso más agudo).
- Para r_c/d = 0.025: Kc se estabiliza cerca de **2.4**.
- Un filete mayor suaviza la transición de esfuerzos, reduciendo los picos de concentración.

**Implicación de diseño:** Se recomienda maximizar el radio del filete del chavetero dentro de las restricciones geométricas del ensamble, ya que filetes pequeños incrementan significativamente el riesgo de falla por fatiga.

---

## Herramientas Utilizadas

| Herramienta | Uso |
|-------------|-----|
| **Ansys 2025 R1** (licencia estudiantil) | Simulación MEF y análisis de esfuerzos |
| **Software CAD** | Modelado geométrico 3D de los ejes |
| **Python / Excel** | Procesamiento y graficación de resultados |

**Material:** Acero estructural (propiedades por defecto en Ansys).

---

## Conclusiones Generales

1. **Validación del modelo teórico:** Los resultados de simulación por MEF concuerdan con los coeficientes de Peterson para relaciones r/d > 0.1, con errores menores al 5%.

2. **Limitación del modelo teórico:** Para radios de filete muy pequeños (r/d < 0.05), el error entre simulación y teoría crece exponencialmente. Esto se debe a que la malla no puede capturar adecuadamente gradientes extremos, y la teoría predice concentraciones físicamente inalcanzables.

3. **Efecto del radio del filete:** En todos los casos analizados, aumentar el radio del filete reduce consistentemente el factor de concentración de esfuerzos, mejorando la vida útil del componente.

4. **Convergencia de malla:** Es imprescindible realizar análisis de convergencia antes de confiar en los resultados. En este estudio, la variación entre iteraciones fue inferior al 2% en los casos de torsión y menor al 1% en el caso del chavetero a flexión.

5. **Eje con dos concentradores:** La separación entre concentradores no afecta de manera significativa el esfuerzo máximo, lo que sugiere que la interacción entre filetes es despreciable para las geometrías estudiadas.

---

## Referencias

1. Beer, F. P. & Johnston, E. R. *Mecánica de Materiales*. Mc Graw Hill, 2010.
2. Departamento de Ingeniería Mecánica y Mecatrónica, Universidad Nacional de Colombia. *Diseño de Ejes*. Notas de clase, 2024-1S.
3. Pilkey, W. D. & Pilkey, D. F. *Peterson's Stress Concentration Factors*. John Wiley & Sons, Inc., 2008.
4. Ye, R., Novovic, M. & Bowen, P. "Effect of multiple keyway notches on the fracture behaviour of unirradiated gilsocarbon graphite I: Small-scale sample sizes and FE modelling." *Engineering Fracture Mechanics*, vol. 268, p. 108476, 2022.
