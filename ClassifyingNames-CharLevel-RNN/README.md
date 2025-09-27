# Descripción
- Este notebook muestra una arquitectura RNN que recibe un nombre/apellido como input, y el modelo clasifica el idioma.

# Procesamiento de datos
- Se aplica una normalización NFD de \unicodedata\ en las palabras para remover las tildes.
- Los nombres se convierten en vectores OHE a nivel de caracter.
- Tamaño de cada vector por caracter: 58 (incluyendo los caracteres en minúsculas, mayúsculas y otros símbolos adicionales) 

# División de datos
- train_set: 85%
- test_set: 15%

# Arquitectura de la red
- 1 RNN layer
- 1 Linear Layer
- Softmax 
  
# Entrenamiento
## Hiperparámetros:
- optimizer: Adam, learning_rate=0.005
- épocas: 10
- loss: CrossEntropyLoss

