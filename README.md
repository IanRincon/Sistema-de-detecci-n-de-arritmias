# Sistema de detección temprana de arritmias

El presente repositorio contiene el dieseño del sistema de detección temprana de arritmias desarrollado en el trabajo de tesis "Sistema de detección de arritmias tempranas con redes neuronales e IoT" para la maestría en tecnologías de internet de la Universidad de Colima.

Se presenta una arquitectura IoT para el despliegue de un modelo de redes neuronales optimizado para trabajar en un entorno IoT. La arquitectura general es del estilo edge - fog - Cloud, con el objetivo de mejorar los tiempos de respuesta. Se utilizan 2 modelos principalmente:

- Modelo optimizado para entorno IoT: se despliega sobre el nodo fog; optimiza espacio en memoria, así como uso de memoria RAM, manteniendo métricas decentes de clasificación de arritmias.

- Modelo optimizado en detección: se despliega sobre el nodo cloud; tiene como prioridad optimizar las métricas sin importar el computo necesario.

Esta división de tareas, garantiza que se pueda obtener una alerta temprana. El umbral del modelo fog busca maximizar la sensibilidad del modelo, ya que en el contexto médico es preferible una falsa emergencia a tener una emergencia que nuna se detectó; por su parte, desde el nodo cloud se realiza una inferencia más precisa que permite validar el riesgo.

Debido a que se trata de un prototipo, un despliegue en producción real implica una etapa de calibración en los dispositivos físicos que se estarían utilizando con el fin de reducir las falsas alarmas. En el siguiente diagrama se muestra la arquitectura general del sistema; en donde la capa física que involucra el sensor receptor y el smartphone que genera las alertas están construidos en contenedores Docker.

<p align="center">
  <img width="700" height="500" alt="Diagrama de arquitectura IoT multiprotocolo" src="https://github.com/user-attachments/assets/abf0d3e3-5edb-4279-b16d-7dd4172edc77" />
</p>
