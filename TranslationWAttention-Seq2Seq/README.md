# Notebook

# Descripción
En este repositorio, creé un modelo de arquitectura *sequence to sequence* para la tarea de traducción de francés a inglés, utilizando el mecanismo de atención aditiva (Bahdanau) en el decoder.
- **Encoder:** El encoder toma la secuencia de tokens, y genera los hidden states para cada time step.
- **Decoder:** El decoder, para cada time step, toma los hidden states generados por el decoder y calcula los *attention weight scores* utilizando el mecanismo de atención aditiva de Bahdanau.
- **Attention mechanism:**  
<div align="center">
  <img src="./IMG/BahdanauAttention.png">
</div>

# Preprocesamiento de datos
- **Data:** Las oraciones, con las que se entrenó al modelo, tienen, como máximo, un *length* de 10. Esto se realizó con el objetivo de crear un diccionario que contenga las palabras del vocabulario para el mapeo a su token correspondiente.
- **Normalización:** Al normalizar las oraciones, tomé en cuenta algunos signos de puntuación. De esta manera, me aseguro de que a cada signo de puntuación se le asigne un token. Token que será representado por un vector de 'n' dimensiones a través de la Embedding Layer.
- 
