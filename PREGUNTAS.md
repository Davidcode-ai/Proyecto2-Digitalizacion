# Reflexión Teórica - Proyecto 2

### Ciclo de vida del dato (5b)
**¿Cómo se gestionan los datos desde su generación hasta su eliminación en tu proyecto?**
En este Gemelo Digital, el dato nace en el entorno OT simulado (cálculos de fricción, temperatura e inercia generados a 30 FPS). Estos datos en crudo se transmiten instantáneamente a través de memoria compartida (RAM) al entorno IT. El sistema IT procesa los datos, los normaliza a porcentajes para la interfaz (barras de progreso) y los visualiza en gráficas temporales. Los datos históricos de las gráficas se eliminan de forma rotativa (FIFO) al superar los 100 registros para optimizar la memoria, pero los eventos críticos se persisten en el Datalogger.

**¿Qué estrategia sigues para garantizar la consistencia e integridad de los datos?**
Para evitar interrupciones o bloqueos de lectura/escritura (típicos de archivos locales JSON), el proyecto utiliza un diccionario global en memoria RAM administrado mediante *Threading*. Esto garantiza que el motor físico y la interfaz gráfica accedan a la misma fuente de la verdad de forma síncrona, manteniendo la integridad referencial sin pérdida de paquetes.

---

### Almacenamiento en la nube (5f)
**Si no usas la nube, ¿cómo podrías integrarla en futuras versiones y qué alternativas consideraste?**
Actualmente el proyecto opera en modo local (Edge Computing) para garantizar una latencia cero en la parada de emergencia de las máquinas. Sin embargo, la arquitectura está preparada para integrarse en la nube. 
Se evaluó el uso de bases de datos locales (SQLite), pero de cara a futuras versiones, la propuesta es enviar los datos del Datalogger mediante una API REST a servicios cloud como AWS IoT Core o un almacenamiento NoSQL en la nube (ej. Firebase/MongoDB). Esto permitiría garantizar la disponibilidad de los datos históricos desde cualquier ubicación geográfica, posibilitando a los ingenieros auditar la fábrica en remoto.

---

### Seguridad y regulación (5i)
**¿Qué medidas de seguridad implementaste y qué normativas podrían afectar?**
A nivel de software, se ha implementado un sistema de "Fail-Safe": si una máquina supera los límites críticos de temperatura/carga, el software bloquea los controles operativos para evitar daños mayores, forzando la intervención de mantenimiento.
A nivel normativo, el registro de operarios (visible en el footer del SCADA como `ADMIN_DAW_01`) está sujeto a la GDPR. Para futuras versiones en la nube, se deberá implementar un sistema IAM (Gestión de Identidad y Accesos) cifrando el tráfico mediante TLS y anonimizando los datos de turno del trabajador para no vulnerar su privacidad laboral.

---

### Implicación de las THD en negocio y planta (2e)
**¿Qué impacto tendría tu software en un entorno de negocio o en una planta industrial?**
El impacto en planta es directo: permite pasar de un mantenimiento correctivo (reparar lo roto) a un control preventivo. El operario tiene una visión holística que evita catástrofes físicas.
A nivel de negocio, la reducción de los tiempos de parada no planificados (Downtime) se traduce en un aumento drástico del OEE (Eficiencia General de los Equipos) y, por tanto, en un mayor margen de beneficio, optimizando la toma de decisiones gerenciales mediante los logs de incidencias.

---

### Mejoras en IT y OT (2f)
**¿Cómo puede tu software facilitar la integración entre entornos IT y OT?**
El simulador rompe los silos tradicionales. Convierte el entorno OT (las variables físicas de motores, hornos y cintas transportadoras, que normalmente son sistemas "ciegos" y aislados) en información accesible, estructurada y visual para el entorno IT (el Dashboard del operario). El mayor beneficio en automatización es el bucle de retroalimentación: el sistema IT no solo "lee" pasivamente, sino que es capaz de inyectar comandos activos en el OT para accionar ventiladores o forzar paradas de seguridad automáticas.

---

### Tecnologías Habilitadoras Digitales (2g)
**¿Qué tecnologías habilitadoras digitales (THD) has utilizado o podrías integrar?**
El proyecto se fundamenta directamente en la THD de **Simulación y Gemelos Digitales (Digital Twins)**. Se ha creado una réplica virtual de activos físicos para predecir y monitorizar su comportamiento en condiciones de estrés sin riesgo real.
Para enriquecer la solución, las próximas integraciones lógicas serían el **Internet de las Cosas (IIoT)**, sustituyendo el motor físico simulado por la lectura de sensores reales mediante microcontroladores, y **Big Data / Inteligencia Artificial**, alimentando modelos predictivos con el histórico de la RAM para adivinar averías horas antes de que la temperatura alcance niveles críticos.
