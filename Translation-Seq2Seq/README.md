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
  - Embedding layer: Mapea los input tokens de las oraciones a embedding vectors
  - GRU layer: Capa de GRU para retener la información
  - Dropout: Capa para prevenir el overfitting
    
  - **Nota:** Hidden size --> 128
    
  ![Encoder](https://github.com/DianaMLlamocaZ/SEQUENCE_MODELS_LEARNING/blob/main/Translation-Seq2Seq/img_data/Encoder.JPG)

- **Decoder:**
  - Embedding layer: Mapea los inputs predichos por el decoder a embedding vectors.
  - ReLU activation funciona: Luego de generarse los embeddings, a estos se les aplica la ReLU activation function.
  - GRU layer: Capa para retener la información.
  - Linear layer: Mapeo de dimensiones del hidden size al tamaño del vocabulario (cantidad de palabras presentes).
  - Adicionalmente, para la etapa de 'inferencia', los outputs del decoder deben pasar por una softmax function para convertir los logits predichos a probabilidades.
    
  ![Decoder](https://github.com/DianaMLlamocaZ/SEQUENCE_MODELS_LEARNING/blob/main/Translation-Seq2Seq/img_data/Decoder.JPG)

# Entrenamiento
- El encoder genera el 'context vector' luego de procesar la secuencia a traducirse.
- En el time step inicial del decoder, este recibe el 'context vector' y el token 'sos' para indicar el inicio de la predicción (traducción).
- Durante cada predicción del decoder, se usa el token predicho por el modelo mismo como el siguiente input.
- Hiperparámetros:
    - hidden_size: 128
    - batch_size: 32
    - optimizers Adam para el encoder y decoder:
      - optimizer encoder --> learning_rate: 0.001
      - optimizer decoder --> learning_rate: 0.001
     
- **Nota:** En el loss se debe ignorar el índice que representa al PAD token. 

# Prueba
