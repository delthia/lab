# Potenciómetro y LDR. Las entradas analógicas

```arduino title="potenciometro.ino" linenums="1"
const int pot = 0;

void setup () {
    Serial.begin(9600);
}

void loop () {
    Serial.println(analogRead(pot));
    delay(50);
}
```