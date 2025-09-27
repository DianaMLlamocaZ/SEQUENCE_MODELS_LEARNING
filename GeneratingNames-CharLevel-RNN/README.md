# Descripción
- En este notebook, implemento un modelo recurrente cuyo objetivo es generar nuevas palabras dado un idioma.

# Procesamiento de datos
- Dado que el modelo funciona a nivel de caracter, cada palabra se representa por un tensor cuyos elementos son vectores en formato one hot encoding.
- De la misma forma, la 'etiqueta' de clase (idioma) también se represeenta mediante un vector OHE.

# Arquitectura de la red
- 1 hidden layer: i2h (de aquí se obtiene el hidden state)
- 1 linear layer: i2i (capa lineal que procesa genera el 'output')
- 1 final linear layer: o2o (capa cuyo input_size=hidden_size+output_size y su salida es un conjunto de neuronas igual al size del vocabulario con softmax)

  Imagen de la arquitectura de la red:
  ![Imagen](https://github.com/DianaMLlamocaZ/SEQUENCE_MODELS_LEARNING/blob/main/GeneratingNames-CharLevel-RNN/img_data/arquitectura.png)
