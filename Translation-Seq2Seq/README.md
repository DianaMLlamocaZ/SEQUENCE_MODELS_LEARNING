# Notebook
[TranslationSeq2Seq.ipynb](./TranslationSeq2Seq.ipynb)

# Descripción
En este notebook, implementé un modelo (con la arquitectura seq2seq) para traducción de francés a inglés.
Para ello, creé 2 redes recurrentes (GRUs):
- **Encoder:** Genera el context vector (hidden state del último time step del encoder) que será el hidden state inicial del decoder.
- **Decoder:** Recibe, inicialmente, el token 'sos' (como input) y el context vector (como hidden state inicial).
  Posteriormente, para el entrenamiento, usé Teacher Forcing y, para la inferencia, el decoder utiliza sus propias predicciones para generar el siguiente input.

# Procesamiento de datos
- Normalización de oraciones: minúscula, considerar algunos signos de puntuación, remover símbolos del francés que no están presentes en el inglés.
- Creación de objetos que representan a los idiomas, con atributos para mapear palabras a índices (útiles para generar embeddings)
- Generación de DataLoaders: batch_size=32

# Arquitectura de la red
- **Encoder:**
  - Embedding layer
  - GRU layer
  - Dropout
  **Nota:** Hidden size --> 128
    
  ![Encoder](https://github.com/DianaMLlamocaZ/SEQUENCE_MODELS_LEARNING/blob/main/Translation-Seq2Seq/img_data/Encoder.JPG)
# Entrenamiento

# Prueba
