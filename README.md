# Ejercicio de laboratorio: Piedra, Papel o Tijeras
**Autor**: Fermín Cruz   **Fecha última modificación**: 12/09/2024

En este proyecto vamos a implementar el juego de "Piedra, Papel o Tijeras". Empezaremos implementando funciones para resolver cada uno de los pasos del juego, y después implementaremos la mecánica del juego haciendo uso de dichas funciones. 

El juego consiste en elegir entre las opciones ``piedra``, ``papel`` o ``tijeras``. El adversario (el ordenador) elegirá también una de estas opciones. Ambos jugadores eligen a la vez, sin saber lo que elegirá el contrario. Para determinar quien 
gana una ronda, se siguen estas reglas:

* La piedra gana a las tijeras.
* Las tijeras ganan al papel.
* El papel gana a la piedra.
* Si los dos jugadores escogen la misma opción, se produce un empate.

El juego se puede jugar al mejor de varias rondas, de manera que en cada ronda suma un punto el ganador (si no hay empate), y gana el primero en llegar a un número de puntos determinado.

### Preparación del proyecto

Cree una carpeta ``src``, y dentro de esta un módulo ``piedra_papel_tijeras.py`` y un módulo ``piedra_papel_tijeras_test.py``.

### Ejercicio 1: Implementación de funciones

#### Apartado a

Añada al módulo ``piedra_papel_tijeras.py`` una función ``ordenador_decide_jugada`` como la mostrada a continuación:

```python
import random

def ordenador_decide_jugada():
    ''' 
    Elige aleatoriamente entre piedra, papel o tijeras y devuelve la elección.     
    '''
    opciones = ["piedra", "papel", "tijeras"]
    res = random.choice(opciones)
    return res
```

En el módulo ``piedra_papel_tijeras_test.py``, añada el siguiente código:

```python
from piedra_papel_tijeras import *

def test_ordenador_decide_jugada():
    '''
    Test para la función ordenador_decide_jugada.
    '''
    print("Testeando ordenador_decide_jugada...")
    eleccion = ordenador_decide_jugada()
    print("El ordenador eligió:", eleccion)
    print()

# Función principal
if __name__ == "__main__":
    test_ordenador_decide_jugada()
```

Ejecute el módulo ``piedra_papel_tijeras_test.py``. Debe observar por consola un mensaje indicando la elección realizada por el ordenador. 

#### Apartado b

Con ayuda de su profesor, ejecute paso a paso el módulo ``piedra_papel_tijeras_test.py`` en modo depuración. Trate de entender detenidamente el flujo de ejecución. Observe también el resultado de la llamada ``random.choice(opciones)``. ¿Qué hace esa función?

#### Apartado c

Añada al módulo ``piedra_papel_tijeras.py`` una función ``usuario_decide_jugada`` como la mostrada a continuación:

```python
def usuario_decide_jugada():
    ''' 
    Pide al usuario que elija entre piedra, papel o tijeras y devuelve la elección.     
    '''
    eleccion_usuario = input("Elige piedra, papel o tijeras: ")    
    return eleccion_usuario
```

En el módulo ``piedra_papel_tijeras_test.py``, sustituya el código completo por este otro:

```python
from piedra_papel_tijeras import *

def test_ordenador_decide_jugada():
    '''
    Test para la función ordenador_decide_jugada.
    '''
    print("Testeando ordenador_decide_jugada...")
    eleccion = ordenador_decide_jugada()
    print("El ordenador eligió:", eleccion)
    print()

def test_usuario_decide_jugada():
    '''
    Test para la función usuario_decide_jugada.
    '''
    print("Testeando usuario_decide_jugada...")
    eleccion = usuario_decide_jugada()
    print("El usuario eligió:", eleccion)
    print()

# Función principal
if __name__ == "__main__":
    #test_ordenador_decide_jugada()
    test_usuario_decide_jugada()
```

Observe que hemos añadido una nueva función ``test_usuario_decide_jugada``, y una nueva llamada a esta función dentro de la función principal. También hemos comentado la anterior llamada a ``test_ordenador_decide_jugada``.

Ejecute el módulo ``piedra_papel_tijeras_test.py``. El programa le solicitará que escoja entre piedra, papel o tijeras. Escriba la opción que desee y pulse *Enter*.

#### Apartado d

Añada al módulo ``piedra_papel_tijeras.py`` la siguiente función:

```python
def determina_ganador(jugada_usuario, jugada_ordenador):
    if jugada_usuario == jugada_ordenador:
        return "Empate"
    elif jugada_usuario == "piedra" and jugada_ordenador == "tijeras":
        return "Ganaste"
    elif jugada_usuario == "tijera" and jugada_ordenador == "papel":
        return "Ganaste"
    elif  jugada_usuario == "papel" and jugada_ordenador == "piedra":
        return "Ganaste"
    else:
        return "Perdiste"
```

En el módulo ``piedra_papel_tijeras_test.py``, sustituya el código completo por este otro:

```python
from piedra_papel_tijeras import *

def test_ordenador_decide_jugada():
    '''
    Test para la función ordenador_decide_jugada.
    '''
    print("Testeando ordenador_decide_jugada...")
    eleccion = ordenador_decide_jugada()
    print("El ordenador eligió:", eleccion)
    print()

def test_usuario_decide_jugada():
    '''
    Test para la función usuario_decide_jugada.
    '''
    print("Testeando usuario_decide_jugada...")
    eleccion = usuario_decide_jugada()
    print("El usuario eligió:", eleccion)
    print()

def test_determina_ganador(eleccion_jugador, eleccion_ordenador):
    '''
    Test para la función determina_ganador.
    '''
    print("Testeando determina_ganador...")        
    print(f"Jugador: {eleccion_jugador} vs. Ordenador: {eleccion_ordenador}")
    resultado = determina_ganador(eleccion_jugador, eleccion_ordenador)
    print("Resultado:", resultado)
    print()

# Función principal
if __name__ == "__main__":
    #test_ordenador_decide_jugada()
    #test_usuario_decide_jugada()
    test_determina_ganador("piedra", "tijeras")
    test_determina_ganador("piedra", "papel")
    test_determina_ganador("piedra", "piedra")
    test_determina_ganador("tijeras", "tijeras")
    test_determina_ganador("tijeras", "papel")
    test_determina_ganador("tijeras", "piedra")
    test_determina_ganador("papel", "tijeras")
    test_determina_ganador("papel", "papel")
    test_determina_ganador("papel", "piedra")
```

Observe que hemos añadido una nueva función ``test_determina_ganador``, y nuevas llamadas a esta función para probar todas las combinaciones posibles de jugadas del usuario y el ordenador.

Ejecute el módulo ``piedra_papel_tijeras_test.py``. Revise el resultado de cada una de las jugadas probadas. **Uno de los resultados obtenidos no es correcto**, trate de identificarlo.

Haciendo uso del depurador, trata de localizar el error en la implementación de la función ``determina_ganador`` y corrígelo.

### Ejercicio 2

#### Apartado a

Implemente en el módulo ``piedra_papel_tijeras.py`` una función ``jugar``, sin parámetros, que lleve a cabo una ronda del juego. Siga los siguientes pasos:

* Muestre un mensaje de bienvenida
* Haga que el ordenador decida su jugada
* Haga que el jugador decida su jugada
* Muestre un mensaje indicando la elección del ordenador
* Determine quién es el ganador
* Muestre un mensaje con el resultado de la ronda.

Añada el siguiente código al final del módulo ``piedra_papel_tijeras.py``:

```python
if __name__ == "__main__":
    jugar()
```

De esta forma, al ejecutar el módulo ``piedra_papel_tijeras.py`` se invocará a la función ``jugar`` y se debe llevar a cabo una ronda del juego. Ejecute el módulo.

#### Apartado b

Prueba a ejecutar el juego e introducir una opción errónea cuando el programa le pregunte por su jugada (es decir, introduzca un texto que no sea ninguna de las opciones sugeridas). ¿Qué ocurre? 

Vamos a cambiar la implementación de la función ``usuario_decide_jugada`` para que siga solicitando al usuario que escoja una opción hasta que introduzca una de las opciones propuestas:

```python
def usuario_decide_jugada():
    ''' 
    Pide al usuario que elija entre piedra, papel o tijeras y devuelve la elección.     
    '''
    eleccion_usuario = input("Elige piedra, papel o tijeras: ")
    while eleccion_usuario not in ["piedra", "papel", "tijeras"]:
        eleccion_usuario = input("Opción no válida, por favor elige piedra, papel o tijeras: ")
    return eleccion_usuario
```

Para entender este nuevo código, ejecute el juego en modo depuración. Cuando el juego le solicite que elija una opción, introduzca un texto incorrecto, y observe cómo avanza el flujo de ejecución.

#### Apartado c

Haciendo uso de la ejecución en modo depuración, ¿serías capaz de ganarle siempre al ordenador? 

### Ejercicio 3 (avanzado)

Se quiere implementar una versión del juego a tres puntos. Es decir, se jugarán varias rondas del juego, de manera que en cada ronda el jugador que gane sumará un punto (si hay empate, ningún jugador se suma un punto). El primer jugador que llegue a tres puntos gana la partida. 

¿Serías capaz de implementar esta versión del juego en una función ``jugar_torneo``? 