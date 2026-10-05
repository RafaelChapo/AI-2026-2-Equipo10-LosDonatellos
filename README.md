# AI-2026-2-Equipo10-LosDonatellos
Primer avance del grupo 10 para el curso de agentes inteligentes.
# Michi · Gemelo Digital de Alimentador Inteligente

## 1. Problema y Usuarios Afectados
Los dueños de gatos domésticos esterilizados enfrentan dificultades para regular las porciones de comida cuando están fuera del hogar. Los dispensadores automáticos convencionales suministran porciones rígidas sin considerar variaciones fisiológicas diarias (temperatura ambiente, actividad física o saciedad previa). Esto deriva en sobrepeso felino, ansiedad nocturna por hambre y desperdicio de alimento descompuesto en el plato.

## 2. Modo Base y Tecnicas Comparadas
El entorno simula el balance calorico diario con base en la formula RER = 70 * (peso ^ 0.75) y dinamicas horarias de saciedad:
* **Modo Base (Horario Fijo):** Dispensa porciones estaticas a horas predefinidas (8:00 y 20:00), ciego a la actividad, peso o estado del plato.
* **Tecnica 1 - Agente Reflejo Simple:** Monitorea la regla reactiva: si las horas con plato vacio superan 4, sirve una racion de contingencia sin modelo predictivo ni memoria.
* **Tecnica 2 - Agente Basado en Utilidad:** Evalua porciones candidatas mediante proyecciones de su modelo interno fisiologico para maximizar la funcion de utilidad:
  U(g) = -alfa * (|peso - ideal| / 0.1) - beta * hambre - gamma * (desperdicio / 50)

## 3. Tabla de Resultados Comparativos
Promedios tras validacion Monte Carlo (20 corridas independientes, 14 dias de simulacion):

| Tecnica / Agente | Bienestar Acumulado (U) | Desviacion Peso Final (kg) | Desperdicio Total (g) | Episodios Hambre Extrema | Tiempo Computo (ms) | Corridas |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Modo Base** | -124.5 +/- 8.2 | 0.320 +/- 0.045 | 145 +/- 18 | 4.2 +/- 0.8 | < 1 ms | 20 |
| **Agente Reflejo** | -86.3 +/- 6.1 | 0.185 +/- 0.030 | 92 +/- 12 | 1.6 +/- 0.5 | < 1 ms | 20 |
| **Basado en Utilidad** | **-42.1 +/- 4.3** | **0.048 +/- 0.015** | **24 +/- 6** | **0.1 +/- 0.3** | ~2.4 ms | 20 |

## 4. Instrucciones de Ejecucion
No requiere instalacion ni dependencias locales de backend:
1. Abrir directamente el archivo index.html en cualquier navegador web moderno.
2. O acceder a la version desplegada en produccion mediante:
   https://ai-2026-2-equipo10-losdonatellos.onrender.com/

## 5. Declaracion de Codigo IA vs. Modificaciones Propias
* **Codigo generado con asistencia de IA:**
  * Estructura inicial del modelo matematico fisiologico (RER felino y dinamica de deficit energetico).
  * Funcion generadora del avatar procedural SVG de Michi y visualizacion con Chart.js via CDN.
* **Modificaciones y adaptaciones del equipo:**
  * Formulacion y calibracion de la funcion de utilidad multiobjetivo U(g) junto con sus factores de escala.
  * Implementacion del generador pseudoaleatorio reproducible (mulberry32) con cinta de azar compartida para comparacion equitativa.
  * Consolidacion de toda la aplicacion en un unico archivo plano (index.html) y rediseño minimalista de la interfaz de usuario.

## 6. Integrantes y Roles
* **Rafael del Piero Chapoñan Chunga:** Arquitectura del gemelo digital, integracion del agente de utilidad y despliegue en GitHub Pages.
* **Alanis Zuzet Crisanto Alzamora:** Modelado matematico fisiologico, balance calorico y calibracion de ponderadores de utilidad (alfa, beta, gamma).
* **Sebastian Paolo Tapia Garcia:** Diseño de la interfaz de usuario, interactividad de controles y generacion de graficos con Chart.js e implementacion de agentes de referencia (Modo Base y Reflejo Simple).
