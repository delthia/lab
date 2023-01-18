# ¿Qué es Arduino?

Arduino es una plataforma de microcontroladores, pequeñas placas que podemos programar para interactuar con diferentes componentes mediante entradas y salidas digitales o analógicas.

La placa más común para aprender a utilizar esta plataforma es el Arduino UNO, que aunque es bastante básica, tiene todo lo necesario para empezar, incluyendo un conversor USB a Serie, para que podamos programarla desde el USB de nuestro ordenador, y su procesador, el atmega 328P se encuentra en un zócalo, para que podamos reemplazarlo en caso de que falle.

Hoy en día existen otras placas con más funcionalidades y precios más competitivos, como el esp32, que por un precio menor incluye conectividad wifi, bluetooth, es más compacto, tiene un mayor número de entradas y salidas e incluso incluye un par de salidas analógicas, pero ya que tradicionalmente se suele aprender con el arduino uno, y es más sencillo al trabajar a 5V, en lugar de a 3V como otras placas, será lo que utilicemos.

## El Arduino UNO
Es posible que esta sea la placa más versátil para empezar. Tiene suficientes entradas y salidas para la mayoría de proyectos y es compatible con muchos _shields_.
<figure markdown>
  ![Pinout Arduino UNO](https://docs.arduino.cc/static/2b141eb1cfe6f465a949c203e4af1b5f/A000066-pinout.png)
  <figcaption>Pinout del Arduino UNO R3. Fuente: <a href="https://docs.arduino.cc/hardware/uno-rev3" target="_blank">arduino.cc</a></figcaption>
</figure>

## La protoboard
La protoboard es una herramienta muy útil que nos permite conectar componentes entre sí. Es un lugar en el que podemos colocar los componentes para conectarlos al Arduino
