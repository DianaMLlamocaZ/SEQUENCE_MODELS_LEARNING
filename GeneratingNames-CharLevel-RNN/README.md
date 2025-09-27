# Descripción
- En este notebook, implemento un modelo recurrente cuyo objetivo es generar nuevas palabras dado un idioma.

# Procesamiento de datos
- Dado que el modelo funciona a nivel de caracter, cada palabra se representa por un tensor cuyos elementos son vectores en formato one hot encoding.
- De la misma forma, la 'etiqueta' de clase (idioma) también se represeenta mediante un vector OHE.
- El 'EOS' (end of sentence token) está representado por la posición final del vocabulario.

# Arquitectura de la red
- 1 hidden layer: i2h (de aquí se obtiene el hidden state)
- 1 linear layer: i2i (capa lineal que procesa genera el 'output')
- 1 final linear layer: o2o (capa cuyo input_size=hidden_size+output_size y su salida es un conjunto de neuronas igual al size del vocabulario con softmax)

  **Imagen de la arquitectura de la red:**
  
  ![Imagen](https://github.com/DianaMLlamocaZ/SEQUENCE_MODELS_LEARNING/blob/main/GeneratingNames-CharLevel-RNN/img_data/arquitectura.png)

# Entrenamiento:
Cada caracter es generado de manera 'secuencial', uno por uno, en cada time step.
Así, la velocidad de 'entrenamiento' y 'predicción' está dada por el tamaño de la palabra a generarse, pues el output del paso anterior se debe pasar al siguiente para que la red continúe con el entrenamiento.

Sin embargo, se debe tener en cuenta que, además del vector OHE que representa a cada caracter, se le debe añadir (concatenar) el vector que representa a la categoría (idioma) y el vector hidden state (representa la 'memoria' hasta el time step 't').

Por ello, en vez de usar la RNN layer de Pytorch, implementé una red neuronal recurrente y el cálculo de cada time step manualmente.

**Nota**: En el time step inicial (t=0) el hidden state es un vector OHE de 0's, y en cada paso se va actualizando con el output que genera la red.

### Hiperparámetros:
- Épocas: 100000
- Learning rate: 0.0005
- Loss: CrossEntropy (muchos caracteres como posibles predicciones)
  

# Prueba:
Le paso al modelo la categoría (idioma) y la letra inicial a partir de los cuales va a tener que generar el nombre:

![ImagenResultado]()
