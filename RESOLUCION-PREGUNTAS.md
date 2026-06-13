**Preguntas a responder**

1. **¿Por qué necesitamos Loki además de Prometheus si ya tenemos /metrics?**

Las metricas nos dicen cuando y cuánto falla el sistema de forma numérica, pero no el por qué. Necesitamos Loki porque Prometheus solo mide el rendimiento general, mientras que los logs de Loki guardan el historial detallado para saber exactamente qué causó el error dentro de la aplicación.

2. **¿Qué ventaja aporta que las fuentes de datos de Grafana estén aprovisionadas como código y no creadas a mano?**

La ventaja es que eliminas el error humano y las configuraaciones manuales propensas a fallos. Al dejar las fuentes escritas en código, el entorno se vuelve completamente replicable, permitiendo que cualquiera levante todo el sistema listo para funcionar con un solo comando.


3. **El panel "CPU contenedor" y el panel "CPU host" pueden mostrar valores muy distintos. ¿Por qué? ¿Cuál usarías para alertar sobre una aplicación concreta?**

El host mide el esfuerzo de toda la máquina con todos sus procesos, mientras que el contenedor solo mide lo que consume esa app especifica. Para alertar sobre una aplicación concreta se usa la del contenedor, ya que la del host podría dar falsos positivos por culpa de servicios ajenos.


4. **¿Qué diferencia hay entre el evaluation interval y el pending period de una alarma?**

El evaluation interval es la frecuencia con la que el sistema pasa a revisar si se cumple la condición de la alarma. El pending period es el tiempo que esa condición debe mantenerse activa antes de disparar la notificación, evitando así falsas alarmas por picos momentáneos.