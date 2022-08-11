# Haciendo parpadear un LED. Primer proyecto con Arduino

<figure markdown>
  ![parpadeo led - gif](https://dummyimage.com/600x400/f5f5f5/aaaaaa&text=%E2%80%93%20Image%20%E2%80%93)
  <figcaption>LED parpadeando - Resultado</figcaption>
</figure>

El objetivo de esta guía será tener una primera experiencia con arduino, tanto en lado del hardware como en el del software; es decir, esta guía abarca tanto como montar un circuito básico con arduino como programar este circuito para que funcione como nosotos deseamos.

<figure markdown>
  ```mermaid
  flowchart TD
  A([Inicio]) --> B[Encender el led]
  B --> |Esperar 1000ms| C[Apagar el led]
  C --> |Esperar 1000ms| B
  ```
  <figcaption>Esquema de flujo del programa</figcaption>
</figure>

```arduino title="parpadeo_led.ino" linenums="1"
const int led = 13;  // El led está conectado al pin 13

void setup () { // Función Inicial (1)
  pinMode(led, OUTPUT);  // El led es una salida
}

void loop () {  // Bucle Principal (2)
  digitalWrite(led, HIGH);  // Encender el led
  delay(1000);  // Esperar 1000ms (1 segundo)
  digitalWrite(led, LOW); // Apagar el led
  delay(1000);  // Esperar 1000ms (1 segundo)
}
```

1. El `void setup` es la función inicial de arduino, que se ejecuta una sola vez al inicio del programa, al arrancar o reiniciar el arduino
2. El `void loop` es la función principal de arduino, que se ejecuta en bucle desde que se arranca el arduino, justo después del `void setup`. En esta función escribiremos aquellas instrucciones que queremos que se ejecuten repetidamente mientras que el arduino esté encendido

Ahora que conocemos el código del programa y tenemos el circuito montado, podemos conectar el arduino al ordenador con el cable USB tipo B y cargar el programa tocando en la flecha :material-arrow-right-bold-circle: en el ide de arduino o con el atajo de teclado ++ctrl+u++

<small>
  :octicons-light-bulb-16:
  **Tip:** Puedes hacer clic en el icono :material-check-circle: para verificar el programa antes de subirlo. El IDE nunca cargará un programa erróneo, ya que no se podrá compilar, pero de esta manera puedes comprobar el programa sin tener que conectar el Arduino al ordenador.
</small>