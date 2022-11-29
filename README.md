# Problema:

Desarrollar un juego donde el usuario debe adivinar una palabra sorteada previamente entre 10 posibles opciones. Para ello, se sabe que el juego termina cuando el usuario descubre la última letra, o bien, se llega al máximo de intentos fallidos, en este caso 6.

Un intento fallido se produce cuando el usuario ingresa un carácter que no se encuentra en la palabra. Las letras que aún no han sido descubiertas serán identificadas en pantalla mediante un guión bajo (“_”). A su vez, se indicará la cantidad de intentos fallidos.

# Aclaraciones:
- La aplicación puede tener sus entradas y salidas por medio de la consola. No es necesario desarrollar una interfaz gráfica.
- Recuerden que aquí lo importante es el manejo de variables, estructuras de control, funciones y la resolución del problema.

# RESOLUCION DEL PROBLEMA:

```
import random

palabras = ['hola','juan','juguete','teclado','piso','raton','niño','patineta','celular','pantalla']

MAX_FALLAS = 6

palabra_sorteada = random.randint(0,10)

elegida = palabras[palabra_sorteada]

print('palabra_sorteada: ', elegida)

print('Elegir Palabra')

intentos_fallidos = 0

GANO = False

acertadas = []

largo_palabra_elegida = len(elegida)

while(intentos_fallidos < MAX_FALLAS and not GANO):

    letra = input('INGRESAR LETRA : ')

    if letra in elegida:
        print('acerto letra!')
        result = '' 
        acertadas.append(letra)
        for l in elegida:
            if l in acertadas:
                result = result + l
            else:
                result = result + '_'
        print('RESULTADO HASTA EL MOMENTO: ', result)
        print('largo acertadas: ', len(acertadas))
        print('largo PALABRA ELEGIDA: ', largo_palabra_elegida)
        if '_' not in result:
            print('GANO.!')        
            GANO = True    
    else:
        print('FALLO!')
        intentos_fallidos = intentos_fallidos +1
        print('Cantidad de Fallos al momento: ', intentos_fallidos)


if intentos_fallidos == MAX_FALLAS:
    print('USTED AH PERDIDO **')
elif GANO:
    print('USTED AH GANADO--!')

print('FIN DEL PROGRAMA! :)')
```