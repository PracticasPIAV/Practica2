# Práctica 2 - Transformaciones Geométricas

**Autores:** Alejandro Bolaños García y David García Díaz

## Introducción
Esta práctica tiene como objetivo desarrollar una aplicación en Python que realice transformaciones geométricas en imágenes, utilizando una interfaz de usuario con barras de control (trackbars) para modificar parámetros como rotación, escala y traslación en tiempo real. El propósito es permitir que el usuario ajuste estos valores y observe las transformaciones directamente sobre la imagen mediante la biblioteca OpenCV.

## Desarrollo

### Ejercicio 1a: Transformaciones de Imagen en Tiempo Real
Este ejercicio consiste en aplicar transformaciones afines (rotación, escalado y traslación) a una imagen en tiempo real. Para ello, se carga una imagen y se utiliza una ventana de OpenCV que incorpora trackbars que permiten ajustar los parámetros de:

- **Rotación**: Controla el ángulo de rotación de la imagen en grados, aplicando una matriz de rotación sobre el centro de la imagen.
- **Traslación**: Permite desplazar la imagen horizontal y verticalmente.
- **Escalado**: Ajusta el tamaño de la imagen, permitiendo la modificación uniforme o independiente en los ejes X e Y.

Cada vez que el usuario mueve una barra, el programa recalcula la matriz de transformación y actualiza la imagen. Esta funcionalidad se implementa mediante una combinación de funciones de callback que responden a los eventos de las trackbars y una función principal de actualización.

### Ejercicio 1b: Proyección de una Imagen en Ventana
En el segundo ejercicio se aborda el trazado de una ventana de proyección sobre la imagen y la proyección de la imagen dentro de esta ventana. La implementación permite al usuario seleccionar un área de interés de la imagen, que luego es proyectada según los parámetros configurados.

### Ejercicio 1c: Aplicación de Distorsión de Lente
El tercer ejercicio aplica distorsiones de lente a una imagen utilizando una interfaz de usuario interactiva con trackbars para modificar los coeficientes de distorsión radial (K1 y K2). Cada vez que el usuario ajusta un valor, el programa recalcula la distorsión y la muestra en tiempo real. Esta funcionalidad permite experimentar con los efectos de distorsión típicos de diferentes tipos de lentes.

## Opcionales
En esta sección se presentan características adicionales que fueron implementadas para aumentar la funcionalidad de la aplicación y enriquecer la experiencia del usuario:

- **Marcar Punto de Giro con el Ratón**: Se permite al usuario seleccionar el punto de giro para las rotaciones mediante un clic en la imagen. Esto proporciona mayor control sobre las rotaciones al poder establecer el centro de rotación en cualquier punto de la imagen.
  
- **Traslación de la Imagen Arrastrando con el Ratón**: El usuario puede hacer clic y arrastrar la imagen para moverla en la pantalla, permitiendo una traslación manual y en tiempo real. Esta funcionalidad mejora la precisión en el posicionamiento de la imagen.

- **Aplicación de Transformaciones a Imágenes y Video**: El programa fue adaptado para trabajar tanto con imágenes estáticas como con video en tiempo real. Cuando se activa el modo de video, el programa captura y transforma cada cuadro, permitiendo al usuario ajustar los parámetros de transformación en un flujo de video.

- **Reflexión de la Imagen Respecto a una Línea**:
  - **Reflejo en Eje Vertical**: La imagen se divide en dos mitades verticales, donde una mitad refleja la otra, creando un efecto de simetría horizontal.
  - **Reflejo en Eje Horizontal**: La imagen se divide en mitades superior e inferior, reflejando una mitad sobre la otra para crear una simetría vertical.
  - **Reflejo en Diagonal Principal**: Este reflejo se realiza intercambiando los píxeles de la imagen a lo largo de la diagonal principal, produciendo un efecto de simetría diagonal.

- **Transformación Afín mediante Selección de Puntos**: Este opcional permite seleccionar tres puntos en la imagen original y tres puntos en una imagen de destino. Utilizando estos puntos, se calcula una matriz de transformación afín que alinea la imagen de origen con la de destino, aplicando una combinación de traslación, rotación y escalado que ajusta la imagen en función de los puntos seleccionados por el usuario.

- **Cálculo de la Imagen Especular**: En este apartado se calcula la imagen especular de una imagen original, creando un reflejo horizontal. Este efecto se consigue mediante la función de OpenCV `cv.flip`, que voltea la imagen sobre su eje vertical, mostrando la imagen original y su versión especular en ventanas separadas.

## Conclusión
Esta práctica resultó en el desarrollo de una herramienta interactiva que permite aplicar y visualizar transformaciones geométricas en imágenes, fortaleciendo nuestro entendimiento sobre matrices de transformación y el uso de interfaces interactivas.

Durante el desarrollo, nos enfrentamos a algunos desafíos específicos. En el ejercicio de reflexión diagonal, encontramos que para lograr el reflejo a lo largo de la diagonal principal era necesario que la imagen fuera cuadrada. Esto implicó un ajuste de tamaño en aquellos casos donde la imagen original no lo era, de modo que se pudiera aplicar el reflejo de manera adecuada.

Otro problema surgió en el apartado 1c, en la proyección de la imagen. Inicialmente, los puntos seleccionados por el usuario seguían un orden de asociación predeterminado a las esquinas, lo cual dificultaba la formación de un rectángulo para que se proyectara la imagen. Para resolver esto, modificamos la lógica de asignación para que cada punto de selección se asociara automáticamente a la esquina más cercana que no hubiese sido asignada previamente. Esto optimizó la proyección, facilitando una correspondencia precisa entre la imagen de origen y la proyectada.
