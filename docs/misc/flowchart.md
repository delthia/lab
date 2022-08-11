```mermaid
flowchart TD
A([Inicio]) --> B[Encender el led]
B --> |Esperar 1000ms| C[Apagar el led]
C --> |Esperar 1000ms| B
```