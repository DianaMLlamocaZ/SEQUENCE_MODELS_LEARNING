# Notebook

# Descripción
En este repositorio, creé un modelo de arquitectura *sequence to sequence* para la tarea de traducción de francés a inglés, utilizando el mecanismo de atención en el decoder.
- **Encoder:** El encoder toma la secuencia de tokens, y genera los hidden states para cada time step.
- **Decoder:** El decoder, para cada time step, toma los hidden states generados por el decoder y calcula los *attention weight scores* utilizando el mecanismo de atención de Bahdanau.


