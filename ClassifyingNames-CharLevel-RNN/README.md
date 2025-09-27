# Descripción
- Este notebook muestra una arquitectura RNN que recibe un nombre/apellido como input, y el modelo clasifica el idioma.

# Procesamiento de datos
- Se aplica una normalización NFD de \*unicodedata\* en las palabras para remover las tildes.
- Los nombres se convierten en vectores OHE a nivel de caracter.

# Entrenamiento
