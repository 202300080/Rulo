# Documentación Unidad 3

## Descripción general del proyecto
La Unidad 3 se centra en procesamiento de imágenes con OpenCV. El material recorre una secuencia de trabajo que empieza con operaciones básicas de lectura, cambio de espacio de color, suavizado y umbralización, y avanza hacia detección de contornos, análisis geométrico, detección de colores en HSV y aplicación en tiempo real con cámara.

## Notebooks

### Actividad.ipynb
- ¿Para qué sirve? Presenta un enunciado de ejercicios sobre dos imágenes de referencia: img1.jpg e img2.jpg.
- ¿Qué se pide hacer? Cambiar el fondo a rojo, azul y verde; convertir a escala de grises; pasar de BGR a RGB; encontrar un umbral óptimo; reducir la imagen a tamaño 100 y convertirla a grises; y establecer fondo rojo con umbral.
- Técnicas utilizadas: Conversión de color, escala de grises, umbralización y redimensionamiento.
- Flujo general del proceso: El notebook solo describe tareas. Primero pide probar transformaciones básicas sobre ambas imágenes y luego plantea condiciones específicas para que el umbral destaque el sol en la primera imagen y el contorno circular en la segunda.
- Imágenes utilizadas: IMG/img1.jpg e IMG/img2.jpg.
- Resultado esperado: Resolver las transformaciones solicitadas sobre ambas imágenes sin perder los elementos relevantes.

### Actividad2.ipynb
- ¿Para qué sirve? Define tres retos sobre suavizado y contornos.
- ¿Qué se pide hacer? Encontrar el suavizado óptimo para suavizado.png y suavizado_crayola.png; obtener el contorno que muestre todas las figuras en contornos.png; y extraer el contorno de las imágenes del reto 1.
- Técnicas utilizadas: Suavizado, detección de contornos y ajuste visual del borde.
- Flujo general del proceso: El notebook solo enuncia los retos y deja abierta la elección del color y tamaño del contorno para el segundo ejercicio.
- Imágenes utilizadas: IMG/suavizado.png, IMG/suavizado_crayola.png y IMG/contornos.png.
- Resultado esperado: Comparar filtros, elegir el suavizado más adecuado y mostrar contornos visibles de las figuras.

### Cam.ipynb
- ¿Para qué sirve? Implementa procesamiento en tiempo real con la cámara.
- ¿Qué se pide hacer? Mostrar el video de la cámara, detectar un color azul por rango HSV, aislar contornos, dibujar el contorno convexo, contar objetos y después clasificar figuras geométricas dentro de una región seleccionada.
- Técnicas utilizadas: VideoCapture, conversión a HSV, máscara por rango de color, findContours, convexHull, contourArea, arcLength, moments, approxPolyDP, boundingRect y recorte de región de interés.
- Flujo general del proceso: Empieza con un visor básico de cámara. Luego añade detección de azul por umbral en HSV. Después incorpora filtro por área y contorno convexo. Más adelante agrega centroides y un contador visual. Finalmente usa una región recortada, suavizado en escala de grises, umbral de Otsu y aproximación poligonal para clasificar triángulo, cuadrado, rectángulo, pentágono y círculo.
- Imágenes utilizadas: No usa archivos de imagen; trabaja con la cámara en vivo.
- Resultado esperado: Reconocer objetos azules y figuras geométricas en tiempo real dentro del encuadre o de una región seleccionada.

### Controno.ipynb
- ¿Para qué sirve? Explica y compara modos de recuperación de contornos con ejemplos visuales.
- ¿Qué se pide hacer? Convertir imágenes a escala de grises, umbralizarlas y comparar RETR_LIST, RETR_EXTERNAL, RETR_TREE y RETR_CCOMP; después dibujar los contornos sobre dos imágenes de prueba.
- Técnicas utilizadas: Conversión a gris, resize, threshold con OTSU, findContours con distintos modos, drawContours y visualización con matplotlib.
- Flujo general del proceso: Primero carga 4.jpg, la lleva a escala de grises y genera un umbral binario invertido para contar y comparar contornos. Después repite el proceso con Ejemplo1.png y dibuja los contornos resultantes para contrastar los modos de recuperación.
- Imágenes utilizadas: IMG/4.jpg e IMG/Ejemplo1.png.
- Resultado esperado: Entender cómo cambia la detección de contornos según el modo elegido y visualizar los resultados sobre ambas imágenes.

### Detectar_colores.ipynb
- ¿Para qué sirve? Muestra detección de color en HSV y extracción de contornos azules, y además incluye un enunciado de actividad adicional al final.
- ¿Qué se pide hacer? Suavizar una imagen base, convertirla a HSV, generar máscara para azul, encontrar contornos y dibujarlos; después, resolver una actividad sobre rojo y amarillo a partir de HSV.png y extraer contornos por color en contorno2.png y Ejemplo2.png.
- Técnicas utilizadas: GaussianBlur, conversión a HSV, inRange, findContours, drawContours y guardado de resultados con imwrite.
- Flujo general del proceso: Carga Suavizado.png, aplica suavizado gaussiano, detecta un rango de azul en HSV, localiza contornos y guarda una salida llamada Contorno_Azul.png. Luego el notebook presenta el enunciado de una actividad más amplia sobre segmentación por color y comparación de figuras.
- Imágenes utilizadas: IMG/Suavizado.png como entrada; IMG/Contorno_Azul.png como salida generada; y en el enunciado aparecen IMG/HSV.png, IMG/contorno2.png, IMG/Ejemplo2.png y IMG/Figuras.png.
- Resultado esperado: Detectar un color específico en una imagen y producir una versión contorneada; además, servir como base para ejercicios de segmentación por color.

### General.ipynb
- ¿Para qué sirve? Reúne varios temas de la unidad en un solo notebook: conversiones de color, suavizados, umbralización, Canny, contornos y dibujo de figuras.
- ¿Qué se pide hacer? Mostrar varias conversiones de color sobre tres imágenes, comparar varios filtros de suavizado, aplicar umbrales binarios y binarios invertidos, extraer bordes con Canny y detectar contornos sobre una imagen principal.
- Técnicas utilizadas: Conversión de color, filter2D, blur, GaussianBlur, medianBlur, threshold, Canny, findContours, contourArea y dibujo de primitivas gráficas como línea, círculo y elipse.
- Flujo general del proceso: El notebook define funciones para cargar varias imágenes, generar distintas conversiones de color y mostrar sus resultados. Luego aplica una batería de filtros de suavizado sobre una imagen base, produce umbrales para cada salida, calcula bordes con Canny y finalmente detecta y dibuja contornos con RETR_TREE. La parte final añade una figura sintética con line, circle y ellipse.
- Imágenes utilizadas: El código referencia Imagenes/3.jpeg, Imagenes/2.jpeg e Imagenes/1.jpeg. En el workspace visible no existe la carpeta Imagenes; sí existen IMG/ e IMG 2/ con 1.jpeg, 2.jpeg, 3.jpeg y 30.jpeg.
- Resultado esperado: Servir como notebook integrador para comparar las técnicas principales de visión por computadora estudiadas en la unidad.

### Suavizados.ipynb
- ¿Para qué sirve? Compara varias técnicas de suavizado sobre dos imágenes de prueba.
- ¿Qué se pide hacer? Aplicar y comparar convolución, promedio, Gaussiano, mediana y combinaciones de filtros sobre Suavizado.png y Ejemplo1.png.
- Técnicas utilizadas: filter2D, blur, GaussianBlur, medianBlur y combinaciones de suavizado.
- Flujo general del proceso: Carga la primera imagen, la convierte a escala de grises y después a RGB para mostrar los resultados de seis filtros. Repite el mismo análisis con una segunda imagen de referencia.
- Imágenes utilizadas: IMG/Suavizado.png e IMG/Ejemplo1.png.
- Resultado esperado: Observar cómo cambia la nitidez y el nivel de ruido en cada método de suavizado.

## Relación entre notebooks
Actividad.ipynb y Actividad2.ipynb funcionan como enunciados de ejercicios. Suavizados.ipynb, Controno.ipynb y Detectar_colores.ipynb desarrollan bloques temáticos concretos: filtros, contornos y segmentación por color. General.ipynb actúa como resumen integrador de casi toda la unidad. Cam.ipynb lleva esas técnicas a un escenario en tiempo real con cámara y clasificación de figuras.

## Conclusión
La unidad tiene una progresión clara: primero se plantean ejercicios guiados, luego se desarrollan técnicas aisladas y finalmente se combinan en un flujo más completo con cámara y análisis de objetos. El contenido real está centrado en color, suavizado, umbralización y contornos, con una evolución hacia segmentación y reconocimiento de formas.