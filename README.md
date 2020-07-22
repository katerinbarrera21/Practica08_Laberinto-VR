# Practica08_Laberinto-VR

1.	Crear la GVR Camera Rig

Durante este paso, crearemos la cámara VR incluyendo el GvrEditorEmulator en la escena y configurando la cámara.

1.	Agregue el objeto prefab GvrEditorEmulator a la escena.
2.	Convierta el objeto Main Camera en un elemento hijo del objeto GvrEditorEmulator.
3.	Restablece el componente Transformar del objeto Main Camera
4.	Mueva el objeto GvrEditorEmulator a una ubicación conveniente para el desarrollo, por ejemplo, Posición: 0, 3, 35 y Rotación: 0, 180, 0.
5.	Ingrese al modo de juego y use Alt + Mouse y Ctrl + Mouse para rotar e inclinar el ángulo de visión de la cámara. 





2.	Preparando la escena para la interacción
Durante este paso, prepararemos la escena para la interacción configurando el puntero, el emisor de rayos y el sistema de eventos, y luego probaremos el sistema de punto de referencia incluido (waypoint).

1.	Agregue el objeto prefab GvrReticlePointer a la escena como elemento secundario del objeto del Main Camera.
2.	Aumente el valor de Distancia máxima de retícula para el GvrReticlePointer del
valor predeterminado de 10 a 20. 
3.	Agregue el script GvrPointerPhysicsRaycaster como componente en el objeto Main Camera.
4.	Agregue el objeto prefab GvrEventSystem a la escena.
5.	Ingrese al modo de juego y navegue por la escena haciendo clic en los puntos de referencia.
 






3.	Hacer que los objetos del juego sean interactivos

Durante este paso haremos que la Moneda, la Llave y la Puerta sean interactivas añadiéndoles componentes de disparadores y eventos.

1.	Localiza y selecciona el objeto Coin en la jerarquía.
2.	Verifique que tenga un componente Collider.
3.	Agregue el script Coin proporcionado como componente.
4.	Agregue un dispardor de evento (Event Trigger) como componente.
5.	Agregue el evento PointerClick al componente Event Trigger.
6.	Asigne el componente del script Coin al campo de objeto del evento Pointer Click.
7.	Asigne el método Coin.OnCoinClicked () como la función para el evento Pointer Click.
8.	Ingrese al modo de juego, haga clic en la moneda y verifique que el mensaje 'Coin.OnCoinClicked ()' esté impreso en la ventana de la consola.
 


9.	Repita el mismo proceso para el objeto del juego Key pero use el script Key y el método Key.OnKeyClicked ().
 

















10.	Repita el mismo proceso para el primer objeto principal del juego de Puerta, pero use el script de Puerta y el método Door.OnDoorClicked ().
 

4.	Hacer la interfaz de usuario interactiva
Durante este paso, haremos que el objeto SignPost sea interactivo al agregarle componentes de disparadores y eventos. El proceso es casi idéntico al que hicimos con la moneda, la llave y la puerta en el paso anterior, pero no necesitamos un colisionador para interactuar con los objetos del juego de la interfaz de usuario. En su lugar, debemos verificar que el objeto del juego Canvas tenga un componente Graphic Raycaster, y debido a que estamos usando GVR, reemplazaremos el Graphic Raycaster de Unity con el GvrPointerGraphicRaycaster de Google VR.

1.	Localiza y selecciona el objeto del juego SignPost en la jerarquía.
2.	Elimine el componente Graphic Raycaster que se agrega automáticamente al crear un nuevo objeto.
3.	Agregue el script GvrPointerGraphicRaycaster como componente.
4.	Agregue el script SignPost proporcionado como componente.
5.	Agregue un Event Trigger como componente.
6.	Agregue el evento PointerClick al componente Event Trigger.
7.	Asigne el componente script SignPost al campo de objeto del evento Pointer Click.
8.	Asigne el método SignPost.ResetScene () como la función para el evento Pointer Click.
9.	Ingrese al modo de juego, haga clic en SignPost y verifique que el mensaje 'SignPost.ResetScene ()' esté impreso en la ventana de la consola. 
 


5.	Programando el comportamiento de la moneda (coin)
Durante este paso, programaremos el comportamiento de la moneda para que, cuando se haga clic en una moneda (coin), se reproduzca un sonido, muestre un efecto de "poof" y desaparezca.

1.	Hay un mínimo de cinco monedas en el laberinto. Cuando se hace clic en una moneda, se reproduce un efecto de sonido en la ubicación de esa moneda.Cuando se hace clic en una moneda, esa moneda se elimina de la jerarquía de la escena.
2.	Abra el script de Coin y lea todo el script, incluidos todos los comentarios.
3.	Dedique un tiempo a comprender el comportamiento del objeto prefab CoinPoof proporcionado. Puede hacer esto, por ejemplo, ingresando al modo de juego y arrastrando un objeto prefab CoinPoof a la escena.
 
4.	Programe el comportamiento de la moneda completando todos los comentarios TODO en el script

 


6.	Programando el comportamiento de la llave (key)
Durante este paso, programaremos el comportamiento de la llave (key) para que, cuando se haga clic en la llave, reproduzca un sonido, muestre un efecto de "poof" y desaparezca.

1.	Hay un mínimo de una llave en el laberinto. Cuando se hace clic en la llave, se reproduce un efecto de sonido en la ubicación de la llave. Cuando se hace clic en la llave, la llave se elimina de la jerarquía de la escena. Cuando se hace clic en la llave, la puerta se desbloquea.
2.	Abra el script key y lea completo, incluidos todos los comentarios.
3.	Dedique un tiempo a comprender el comportamiento del objeto prefab KeyPoof proporcionado. Puede hacer esto, por ejemplo, ingresando al modo de juego y arrastrando un objeto prefab KeyPoof a la escena.
 
4.	Programe el comportamiento key completando todos los comentarios TODO en el script. 

7.	Programando el comportamiento de la puerta (door) 

Durante este paso, programaremos el comportamiento de la puerta (door) para que cuando se haga clic en la llave (key), la Puerta se desbloquee y cuando se haga clic en la Puerta, se escuche un sonido y comience a girar a una posición de apertura. 

1.	La puerta evita que el usuario navegue al objeto SignPost hasta que se haya abierto. Cuando comienza el juego, la puerta está bloqueada y cerrada. La puerta no se puede abrir cuando está bloqueada. La puerta solo puede desbloquearse haciendo clic en la llave. Cuando se hace clic y se desbloquea la puerta, la puerta comienza a abrirse. Cuando la puerta comienza a abrirse, se reproduce un efecto de sonido en la ubicación de la puerta. La puerta se anima a una posición de abierta solo por código, es decir, no mediante el uso de animación y controlador de animador.
2.	Abra el script Door y lea todo el script, incluidos todos los comentarios. 
3.	Agregue un componente AudioSource al primer objeto padre Door y desactive la propiedad Play On Awake. 
4.	Asigne el audio Door_Opening al campo AudioClip.
5.	Programe el comportamiento de la puerta completando todos los comentarios TODO en el script.
VARIABLES: 
 

Método void Start 
 
Método void Update 
 


Método void OnDoorClicked 
 
Método void  Unlock
 


 

8.	Programando el comportamiento del SignPost

Durante este paso, programaremos el comportamiento de SignPost para que cuando se haga clic en SignPost se reinicie el juego.

1.	El SignPost no se puede ver ni interactuar antes de que se abra la puerta. Cuando se hace clic en SignPost, la escena se restablece a su estado inicial para que el juego se pueda volver a jugar.
2.	Abra el script SignPost y lea todo el script, incluidos todos los comentarios.
3.	Programe el comportamiento SignPost completando todos los comentarios TODO en el script. 

9.	Programando el comportamiento de la Puerta

1.	La puerta evita que el usuario navegue hasta SignPost hasta que se haya abierto.

SignPost

•	El cartel no se puede ver ni interactuar antes de que se abra la puerta.

1.	Use los objetos de juego Maze para diseñar un laberinto.
2.	Mueva el jugador, es decir, el objeto del juego GvrEditorEmulator, a la ubicación de inicio deseada.
3.	Agregue más Waypoints para que el jugador pueda navegar a todas las partes del Laberinto.
4.	Agrega más monedas para que el jugador tenga muchas monedas para coleccionar.
5.	Mueva la llave a una ubicación para que sea un tanto difícil para el jugador encontrarla.
6.	Agregue paredes (cubos) para asegurarse de que los usuarios tengan que navegar para encontrar la llave y las monedas.


 
10.	Crear la funcionalidad del juego
Durante este paso, armaremos todo y convertiremos nuestro proyecto en un juego real. 
Laberinto
•	El laberinto está diseñado de tal manera que el usuario no puede identificar una ruta a la llave desde la posición de inicio.

Waypoints
•	Los puntos de referencia se colocan en todo el laberinto de tal manera que los usuarios pueden navegar desde la posición inicial a todos los objetos del juego con los que se puede interactuar, es decir, todas las monedas, la llave, la puerta y el SignPost.

Monedas

•	Hay un mínimo de cinco monedas en el laberinto.

Llave

•	Hay un mínimo de una clave en el laberinto.

  
APK
     
GitHub (usuario y URL del repositorio de la práctica
Katerinbarrera21
https://github.com/katerinbarrera21/Practica08_Laberinto-VR.git
RESULTADO(S) OBTENIDO(S):
La evidencia del correcto diseño de la escena.
La evidencia del correcto funcionamiento de la aplicación.
Desarrolla e integra módulos interactivos virtuales.
CONCLUSIONES:

Se implemento escenarios de realidad virtual usando la herramienta Unity.
Se experimento con aplicaciones de realidad virtual.

Se refuerzan los conocimientos adquiridos durante las sesiones de clase.


RECOMENDACIONES:

N/A

Nombre de estudiante: ____Katherine Barrera_______

Firma de estudiante: _____ _________

