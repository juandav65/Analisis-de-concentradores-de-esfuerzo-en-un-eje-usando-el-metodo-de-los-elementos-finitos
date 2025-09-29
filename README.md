# Análisis de Concentradores de Esfuerzo en un Eje usando el Método de los Elementos Finitos

## 📌 Autores
- Nagem Samir Merheb Suarez – [nmerheb@unal.edu.co](mailto:nmerheb@unal.edu.co)  
- Jose David Garzón Gonzalez – [jogarzong@unal.edu.co](mailto:jogarzong@unal.edu.co)  
- Juan David Medina Perez – [jmedinape@unal.edu.co](mailto:jmedinape@unal.edu.co)  
- Alejandro Perdomo Delgado – [alperdomod@unal.edu.co](mailto:alperdomod@unal.edu.co)  

**Profesores:** Diego Alexander Garzón Alvarado, Diego Alfredo Quexada Rodriguez  
**Universidad Nacional de Colombia – Facultad de Ingeniería (2025)**

---

## 📖 Descripción del Proyecto
Este proyecto aborda el estudio de **concentradores de esfuerzo en ejes** mediante el **Método de los Elementos Finitos (MEF)**.  
El objetivo principal es comparar los resultados obtenidos con los **coeficientes de Peterson** para evaluar la precisión y confiabilidad de ambos enfoques en el diseño mecánico.

El trabajo se enfoca en:
- Ejes con concentradores a torsión y flexión.  
- Simulación mediante **Ansys**.  
- Validación a través de **parametrización geométrica**, **convergencia de malla** y análisis comparativo.

---

## 🎯 Objetivos

### Objetivo General
Determinar los esfuerzos en distintos concentradores de ejes mediante el MEF y compararlos con los coeficientes de Peterson.

### Objetivos Específicos
- Diagramar el factor de concentración de esfuerzos sobre 4 secciones distintas de ejes obtenidas en simulación.  
- Calcular el error entre los resultados teóricos y los simulados.  
- Analizar concentradores en ejes estriados.  

---

## 🌍 Relevancia e Impacto
El estudio contribuye a:
- Optimizar el diseño de componentes mecánicos para evitar fallas prematuras.  
- Reducir costos de producción y mantenimiento.  
- Mejorar la seguridad y confiabilidad en sectores como **automotriz, aeroespacial y manufactura**.  

---

## 📚 Contenidos Aplicados
- **Análisis de Esfuerzos** (normal, cortante y teorías de falla).  
- **Método de Elementos Finitos (MEF)** en 3D.  
- **Optimización geométrica** (radios de filete, chaveteros).  
- **Parametrización y convergencia de malla**.  

---

## ⚙️ Metodología
1. **Modelado CAD** del eje y concentrador.  
2. **Parametrización** de radios de filete/chaveteros.  
3. **Simulación en Ansys** con condiciones de frontera:  
   - Empotramiento en un extremo.  
   - Momento torsor o flector en el eje.  
4. **Enmallado refinado** en zonas críticas.  
5. **Simulación paramétrica** variando geometrías.  
6. **Optimización** y comparación con teoría.  

---

## 🔬 Casos de Estudio

### 1. Eje Escalonado a Torsión
- Simulación de filetes con radios variables (0.8mm – 9mm).  
- Comparación de **Kt teórico vs Kt simulado**.  
- Conclusión: la teoría predice bien para r/d > 0.1, pero diverge cuando los radios son menores a 1 mm.

### 2. Eje con Dos Concentradores
- Análisis de interacción entre dos filetes.  
- Variación de la distancia entre concentradores.  

### 3. Eje Macizo con Filete en la Mitad
- Estudio de un eje con hendidura central.  
- Obtención de curvas esfuerzo cortante vs radio de filete.  

### 4. Chavetero a Flexión
- Análisis de esfuerzos en un eje con chavetero bajo momento flector.  
- Resultados muestran que aumentar el radio de base disminuye la concentración de esfuerzos.  

---

## 📊 Resultados y Conclusiones
- El **comportamiento general de Kt** sigue una tendencia exponencial.  
- **Errores <5%** en radios grandes, pero aumentan cuando r/d < 0.05.  
- El **MEF valida y complementa** las aproximaciones teóricas, mostrando límites donde la teoría no refleja la realidad física.  
- Diseños con **radios mayores en filetes y chaveteros** reducen considerablemente la concentración de esfuerzos.  

---

## 📑 Referencias
1. Beer, F. P., & Johnston, E. R. *Mecánica de materiales*. McGraw Hill, 2010.  
2. Universidad Nacional de Colombia. *Diseño de ejes*, 2024-1s.  
3. Pilkey, W. D., & Pilkey, D. F. *Peterson’s Stress Concentration Factors*. Wiley, 2008.  
4. Ye, R., Novovic, M., & Bowen, P. *Effect of multiple keyway notches on fracture behaviour...*, Eng. Fracture Mechanics, 2022.  

---

## 🛠️ Tecnologías Usadas
- **Ansys** (MEF, mallado y simulación).  
- **CAD 3D** para modelado geométrico. 
