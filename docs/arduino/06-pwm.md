# PWM. "Salidas analógicas"

```arduino
for (i = 0; i<10; i++) {    // Contar de 0 a 9 (1)
    analogWrite(led, i);
}
```

1.  Para hacer un bucle for, deberemos especificar el valor inicial, el valor final, y si contar hacia arriba o hacia abajo

```arduino title="pwm.ino" linenums="1"
const int led = 9;  // Debe de ser un pin marcado con ~

void setup () {
    pinMode(led, OUTPUT);
}

void loop () {
    for(i=0; i<255; i++) {
        analogWrite(led, i);
        delay(20);
    }
    for(i=254; i>0; i--) {
        analogWrite(led, i);
        delay(20);
    }
}
```