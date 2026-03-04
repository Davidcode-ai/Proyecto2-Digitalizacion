# 🏭 SCADA Digital Twin: Integración IT/OT en Tiempo Real

Este proyecto es un simulador industrial (Gemelo Digital) que integra Tecnologías de Operación (OT) calculando físicas complejas en tiempo real, con un panel de Tecnologías de la Información (IT) para su monitorización y control.

## 📥 Descarga rápida (Para el profesor)
Para evaluar el proyecto sin instalar Python ni dependencias:
1. Ve a la sección **[Releases]** a la derecha de esta página.
2. Descarga el archivo **`panel_fabrica_pro.exe`**.
3. Haz doble clic para ejecutar la simulación.

---

## 🔄 Criterio 5b: El Ciclo de Vida del Dato en el Proyecto
El sistema ha sido diseñado respetando el ciclo de vida del dato industrial desde su origen hasta su almacenamiento:

1. **Captura (Generación):** El motor físico en segundo plano genera telemetría (Temperatura, RPM, Presión de Gas, Carga) a 30 FPS simulando el comportamiento de sensores reales en planta.
2. **Almacenamiento/Transmisión:** Los datos se transmiten mediante memoria compartida (RAM) simulando un bus industrial ultrarrápido, evitando los cuellos de botella de escritura en disco duro.
3. **Procesamiento:** El sistema IT lee la memoria, evalúa si los valores superan los umbrales seguros predefinidos y calcula los porcentajes de riesgo.
4. **Visualización:** El dato en crudo se transforma en información útil visualizándose en el dashboard a través de gráficas de tendencias continuas (Matplotlib) y barras de estado (CustomTkinter).
5. **Acción y Registro (Archivado):** Si el dato indica un estado crítico, el sistema ejecuta una acción de bloqueo de seguridad y archiva el suceso en el *Datalogger* global con la hora exacta para futuras auditorías.

---

## 🚀 Cómo probar el software (Guía de Evaluación)

Sigue estos pasos para auditar todas las funcionalidades del sistema:

1. **Acceso:** Ejecuta el simulador. Lee las normas de seguridad en la pantalla inicial, marca la casilla de aceptación y pulsa "INICIAR SIMULACIÓN".
2. **Monitorización (Vista Macro):** En el Mapa de Planta, observa el estado nominal de las máquinas y el *Registro de Sucesos* (Datalogger) en la parte inferior.
3. **Operación (Vista Micro):** Haz clic en "HORNO DE FUNDICIÓN". Activa la "Válvula Principal" para encenderlo.
4. **Inyección de Fallos:** Activa el interruptor rojo "Romper Tubería Gas". 
5. **Respuesta IT/OT:** Observa cómo la gráfica térmica se dispara. El sistema pasará a estado de ALERTA (amarillo) y luego a PELIGRO (rojo). Al superar los 1200ºC, el sistema OT colapsará y el sistema IT bloqueará la pantalla por seguridad.
6. **Reparación:** Pulsa el botón "PROCEDER A REPARACIÓN". La máquina se reiniciará. Vuelve al mapa y comprueba cómo el *Datalogger* ha registrado la incidencia.
