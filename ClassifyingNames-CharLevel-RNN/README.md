# Notebook:
- ¡Click aquí![./RNN_CharClass_Notebook.ipynb]

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
### Hiperparámetros:
- optimizer: Adam, learning_rate=0.005
- épocas: 10
- loss: CrossEntropyLoss

### Loss por época:
- Época 0, Loss: 1.2199156235862563
- Época 1, Loss: 0.9265171012914961
- Época 2, Loss: 0.8386138929322388
- Época 3, Loss: 0.7645445569479238
- Época 4, Loss: 0.7211768871980158
- Época 5, Loss: 0.6841448155828057
- Época 6, Loss: 0.644633860119062
- Época 7, Loss: 0.6286840989935805
- Época 8, Loss: 0.6137491022880329
- Época 9, Loss: 0.5802114986051294

# Prueba
Aquí muestro un ejemplo de test, donde le paso al modelo el apellido "Ramirez", y lo clasifica en un idioma:
![ImagenResultado](https://github.com/DianaMLlamocaZ/SEQUENCE_MODELS_LEARNING/blob/main/ClassifyingNames-CharLevel-RNN/img_resultados/Resultado_prueba.JPG)

Aquí, se ve que el modelo predice "Spanish". Lo cual es correcto.
