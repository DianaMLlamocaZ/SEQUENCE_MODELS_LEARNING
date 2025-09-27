# Descripción
- En este notebook, implemento un modelo recurrente cuyo objetivo es generar nuevas palabras dado un idioma.

# Procesamiento de datos
- Dado que el modelo funciona a nivel de caracter, cada palabra se representa por un tensor cuyos elementos son vectores en formato one hot encoding.
- De la misma forma, la 'etiqueta' de clase (idioma) también se represeenta mediante un vector OHE.

# Arquitectura de la red
- 1 hidden layer: i2h (de aquí se obtiene el hidden state)
- 1 linear layer: i2i (capa lineal que procesa genera el 'output')
- 1 final linear layer: o2o (capa cuyo input_size=hidden_size+output_size y su salida es un conjunto de neuronas igual al size del vocabulario con softmax)

  **Imagen de la arquitectura de la red:**
  
  ![Imagen](https://github.com/DianaMLlamocaZ/SEQUENCE_MODELS_LEARNING/blob/main/GeneratingNames-CharLevel-RNN/img_data/arquitectura.png)

# Entrenamiento:
Cada caracter es generado de manera 'secuencial', uno por uno, en cada time step.
Así, la velocidad de 'entrenamiento' y 'predicción' está dada por el tamaño de la palabra a generase, pues el output del paso anterior debe pasarse al siguiente para que la red continúe con el entrenamiento.

Sin embargo, se debe tener en cuenta que, además del vector OHE que representa a cada caracter, se le debe añadir (concatenar) el vector que presenta a la categoría (idioma) y el vector hidden state generado.


### Hiperparámetros:
- Épocas: 100000
- Learning rate: 0.0005
- Loss: CrossEntropy (muchos caracteres como posibles predicciones)
  
