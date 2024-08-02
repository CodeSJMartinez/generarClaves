# generarClaves
Mini proyecto en Python adecuado para alguien que ya tiene experiencia en desarrollo web con HTML, CSS, y JavaScript. Vamos a crear una aplicación sencilla que simule un generador de contraseñas. Este proyecto es ideal para introducir a alguien al lenguaje Python, ya que utiliza conceptos básicos como variables, funciones, bucles, y bibliotecas.

# Proyecto: Generador de Contraseñas en Python

## Objetivo

Queremos crear un programa que pueda generar contraseñas aleatorias. Estas contraseñas deben ser seguras, es decir, deben incluir letras mayúsculas, letras minúsculas, números y símbolos especiales.

## Conceptos Básicos

Antes de empezar, hay algunos conceptos importantes que debemos conocer:

- **Lenguaje de Programación**: Python es un lenguaje que permite decirle a la computadora qué hacer. Es como darle instrucciones paso a paso.

- **Variables**: Son como cajitas donde guardamos información que podemos usar más tarde.

- **Funciones**: Son como recetas o instrucciones que realizamos varias veces. Le damos algunos ingredientes y nos devuelve un resultado.

- **Bibliotecas**: Son colecciones de funciones y código que alguien más escribió y que podemos usar para facilitarnos el trabajo.

## Paso a Paso

Vamos a construir nuestro generador de contraseñas siguiendo estos pasos:

### 1. Configurar el Entorno de Trabajo

Primero, necesitamos asegurarnos de que tenemos Python instalado en nuestra computadora. Puedes comprobarlo escribiendo `python --version` en la terminal o en el símbolo del sistema. Si no lo tienes, puedes descargarlo e instalarlo desde [python.org](https://www.python.org).

### 2. Crear un Archivo de Python

Crea un archivo nuevo llamado `generar_clave.py`. Este archivo es donde escribiremos nuestro código.

### 3. Importar la Biblioteca Necesaria

Para generar caracteres aleatorios, utilizaremos la biblioteca `random`. Esta biblioteca tiene funciones que nos permiten elegir cosas al azar, como números o letras.

```python
import random
import string
```
*random:* Nos ayuda a seleccionar cosas de manera aleatoria.

*string:* Nos da acceso a conjuntos de caracteres como letras y números.

### 4. Definir los Caracteres de la Contraseña
Ahora, vamos a definir los diferentes tipos de caracteres que queremos en nuestras contraseñas:

```python
letras_mayusculas = string.ascii_uppercase  # ABCDEFGHIJKLMNOPQRSTUVWXYZ
letras_minusculas = string.ascii_lowercase  # abcdefghijklmnopqrstuvwxyz
numeros = string.digits                    # 0123456789
simbolos = string.punctuation              # !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
```

string.ascii_uppercase: Nos da todas las letras mayúsculas del alfabeto.

string.ascii_lowercase: Nos da todas las letras minúsculas.

string.digits: Nos da todos los dígitos del 0 al 9.

string.punctuation: Nos da símbolos especiales como !, @, #, etc.

### 5. Crear una Función para Generar la Contraseña
La función es como una receta que sigue pasos para generar una contraseña.

```python
def generar_contraseña(longitud=12):
    # Asegurarse de incluir al menos un carácter de cada tipo
    caracteres = (
        random.choice(letras_mayusculas) +
        random.choice(letras_minusculas) +
        random.choice(numeros) +
        random.choice(simbolos)
    )
    
    # Completar el resto de la contraseña de manera aleatoria
    if longitud > 4:
        caracteres += ''.join(random.choices(letras_mayusculas + letras_minusculas + numeros + simbolos, k=longitud-4))
    
    # Mezclar los caracteres
    caracteres = list(caracteres)
    random.shuffle(caracteres)
    return ''.join(caracteres)
```

Desglose de la Función:

def generar_contraseña(longitud=12):: Definimos una función llamada generar_contraseña que toma un número (longitud) que indica cuántos caracteres queremos en nuestra contraseña. Por defecto, la longitud es 12.

random.choice(...): Elige un elemento aleatorio de los caracteres dados.

caracteres = (...): Creamos un inicio de contraseña con al menos un carácter de cada tipo para garantizar la seguridad.

random.choices(..., k=longitud-4): Elige al azar k caracteres adicionales para completar la longitud deseada.

random.shuffle(caracteres): Mezcla los caracteres para que no sigan un orden predecible.

return ''.join(caracteres): Une todos los caracteres mezclados en una cadena de texto, que es nuestra contraseña.

### 6. Ejecutar el Programa
Finalmente, queremos que el programa pregunte al usuario cuántos caracteres quiere en su contraseña y luego la genere y la muestre.

```python
if __name__ == "__main__":
    longitud = int(input("Introduce la longitud deseada para la contraseña: "))
    contraseña = generar_contraseña(longitud)
    print(f"Contraseña generada: {contraseña}")
```

Desglose del Código:

if __name__ == "__main__":: Este es un bloque especial que dice "haz esto solo si este archivo se está ejecutando directamente", y no cuando se importa desde otro archivo.

input("Introduce la longitud deseada para la contraseña: "): Pide al usuario que escriba cuántos caracteres debe tener la contraseña.

int(...): Convierte el valor de entrada del usuario a un número entero.

print(...): Muestra la contraseña generada en la pantalla.

Recuerda
Hemos creado un generador de contraseñas que utiliza caracteres aleatorios de diferentes tipos para asegurar la seguridad de las contraseñas. Al dividir el proyecto en pasos pequeños, hemos utilizado funciones, variables y bibliotecas de Python para lograr nuestro objetivo.

Este ejercicio no solo te da una contraseña aleatoria, sino que también te enseña cómo pensar en términos de problemas más grandes y dividirlos en partes manejables, un concepto fundamental en la programación y la resolución de problemas.