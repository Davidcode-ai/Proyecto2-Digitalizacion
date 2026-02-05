# Proyecto: Monitorización de Temperatura (Simulación IT/OT)

## 📌 Descripción
Este es mi proyecto para el módulo de Digitalización. El objetivo es simular un entorno industrial básico usando Python.

La idea es demostrar cómo podemos recoger datos de una máquina (OT) y procesarlos en un ordenador (IT) para detectar problemas antes de que ocurran.

## ⚙️ ¿Cómo funciona?
El proyecto tiene dos partes principales:

1.  **El Sensor (OT):** Un script de Python que simula ser un sensor de temperatura. Genera datos numéricos continuamente y simula "picos" de calor o averías.
2.  **El Analista (IT):** Un segundo script que lee esos datos en tiempo real. Usa una lógica sencilla (pequeña IA) para decidir si la temperatura es normal o si hay peligro.

## 🛠️ Tecnologías
* Lenguaje: **Python**
* Datos: Generación aleatoria y guardado en **JSON/CSV**
* Objetivo: Mantenimiento Predictivo

## 🚀 Estado del proyecto
- [x] Definición de la idea
- [ ] Programación del script del sensor
- [ ] Programación de la lógica de alertas
