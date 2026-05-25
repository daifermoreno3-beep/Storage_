# Funciones Integradas (Built-in) de Python

Python viene con una serie de funciones listas para usar, sin necesidad de importar ningún módulo externo. Aquí tienes la lista **completa** de las ~71 funciones built-in, cada una con descripción y ejemplo:

---

## 1. Entrada y Salida (I/O)

### `print(*objects)`
Imprime texto, variables o cualquier objeto en la consola.
```python
print("Hola, mundo!")        # Hola, mundo!
print("Suma:", 3 + 2)        # Suma: 5
```

### `input(prompt)`
Muestra un mensaje al usuario y lee la entrada desde el teclado como string.
```python
nombre = input("¿Cómo te llamas? ")
print("Hola,", nombre)
```

### `open(file, mode)`
Abre un archivo para leerlo, escribirlo o añadirle contenido.
```python
with open("archivo.txt", "w") as f:
    f.write("Hola desde Python")
```

---

## 2. Matemáticas y Números

### `abs(x)`
Devuelve el valor absoluto de un número (sin signo negativo).
```python
abs(-7)      # 7
abs(3.14)    # 3.14
```

### `round(number, ndigits)`
Redondea un número a la cantidad de decimales especificada.
```python
round(3.7)       # 4
round(3.14159, 2)  # 3.14
```

### `sum(iterable)`
Suma todos los elementos de una lista, tupla o iterable.
```python
sum([1, 2, 3, 4])    # 10
sum((10, 20, 30))    # 60
```

### `min(*args)`
Devuelve el valor más pequeño de un iterable o de una lista de argumentos.
```python
min([5, 3, 8, 1])    # 1
min(10, 20, 5)       # 5
```

### `max(*args)`
Devuelve el valor más grande.
```python
max([5, 3, 8, 1])    # 8
max(10, 20, 5)       # 20
```

### `pow(base, exp)`
Eleva un número (base) a una potencia (exp). Equivale a `base ** exp`.
```python
pow(2, 10)    # 1024
pow(3, 3)     # 27
```

### `divmod(a, b)`
Devuelve una tupla con el cociente y el resto de una división `(a // b, a % b)`.
```python
divmod(17, 5)    # (3, 2)  → 17 / 5 = 3 con resto 2
```

---

## 3. Conversión de Tipos de Datos

### `int(x)`
Convierte un valor a un número entero.
```python
int("42")      # 42
int(3.99)      # 3  (trunca, no redondea)
int("1010", 2) # 10 (convierte de binario a decimal)
```

### `float(x)`
Convierte un valor a un número decimal (de coma flotante).
```python
float("3.14")    # 3.14
float(7)         # 7.0
```

### `complex(real, imag)`
Crea un número complejo de la forma `real + imag*j`.
```python
complex(2, 3)     # (2+3j)
complex("4+5j")   # (4+5j)
```

### `str(object)`
Convierte un objeto a una cadena de texto (string).
```python
str(100)      # '100'
str(True)     # 'True'
str([1,2,3])  # '[1, 2, 3]'
```

### `bool(x)`
Convierte un valor a un booleano (`True` o `False`).
```python
bool(0)      # False
bool(1)      # True
bool("")     # False
bool("hola") # True
```

### `bytes(source)`
Crea un objeto de bytes **inmutable**. Útil para trabajar con datos binarios.
```python
bytes(4)             # b'\x00\x00\x00\x00'
bytes("hola", "utf-8")  # b'hola'
```

### `bytearray(source)`
Crea un objeto de bytes **mutable**, similar a `bytes` pero modificable.
```python
ba = bytearray(b"hola")
ba[0] = 72           # Modifica el primer byte
print(ba)            # bytearray(b'Hola')
```

### `memoryview(obj)`
Crea una vista de memoria de un objeto tipo `bytes` o `bytearray` sin copiarlo.
```python
datos = bytearray(b"Python")
vista = memoryview(datos)
print(vista[0])    # 80  (código ASCII de 'P')
```

### `list(iterable)`
Crea una lista a partir de un iterable (como una tupla o un string).
```python
list("abc")        # ['a', 'b', 'c']
list((1, 2, 3))    # [1, 2, 3]
list(range(5))     # [0, 1, 2, 3, 4]
```

### `tuple(iterable)`
Crea una tupla.
```python
tuple([1, 2, 3])    # (1, 2, 3)
tuple("hola")       # ('h', 'o', 'l', 'a')
```

### `dict(**kwarg)`
Crea un diccionario (pares clave-valor).
```python
dict(nombre="Ana", edad=30)    # {'nombre': 'Ana', 'edad': 30}
dict([("a", 1), ("b", 2)])     # {'a': 1, 'b': 2}
```

### `set(iterable)`
Crea un conjunto (colección sin elementos duplicados).
```python
set([1, 2, 2, 3, 3, 3])    # {1, 2, 3}
set("banana")               # {'b', 'a', 'n'}
```

### `frozenset(iterable)`
Crea un conjunto **inmutable** (no se puede modificar tras su creación).
```python
fs = frozenset([1, 2, 3, 2])
print(fs)    # frozenset({1, 2, 3})
```

---

## 4. Texto y Caracteres

### `chr(i)`
Devuelve el carácter Unicode correspondiente al número entero `i`.
```python
chr(65)     # 'A'
chr(97)     # 'a'
chr(8364)   # '€'
```

### `ord(c)`
Devuelve el código Unicode de un carácter.
```python
ord('A')    # 65
ord('€')    # 8364
```

### `ascii(object)`
Devuelve una representación del objeto usando solo caracteres ASCII, escapando los demás.
```python
ascii("café")     # "'caf\\xe9'"
ascii([1, "ñ"])   # "[1, '\\xf1']"
```

### `repr(object)`
Devuelve una representación "oficial" y reproducible del objeto (útil para depuración).
```python
repr("hola\nmundo")    # "'hola\\nmundo'"
repr([1, 2, 3])        # '[1, 2, 3]'
```

### `bin(x)`
Convierte un entero a su representación en binario como string.
```python
bin(5)     # '0b101'
bin(255)   # '0b11111111'
```

### `oct(x)`
Convierte un entero a su representación en octal como string.
```python
oct(8)     # '0o10'
oct(64)    # '0o100'
```

### `hex(x)`
Convierte un entero a su representación en hexadecimal como string.
```python
hex(255)    # '0xff'
hex(16)     # '0x10'
```

### `format(value, format_spec)`
Formatea un valor según una especificación concreta (útil para números y fechas).
```python
format(3.14159, ".2f")    # '3.14'
format(1000000, ",")      # '1,000,000'
format(42, "08b")         # '00101010'  (binario con 8 dígitos)
```

---

## 5. Secuencias e Iteradores

### `len(s)`
Devuelve la longitud (número de elementos) de un objeto (lista, texto, diccionario).
```python
len("Python")       # 6
len([1, 2, 3])      # 3
len({"a": 1, "b": 2})  # 2
```

### `range(start, stop, step)`
Genera una secuencia de números. Muy usado en bucles `for`.
```python
list(range(5))         # [0, 1, 2, 3, 4]
list(range(2, 10, 2))  # [2, 4, 6, 8]
```

### `enumerate(iterable)`
Devuelve un objeto enumerador que contiene pares (índice, valor).
```python
frutas = ["manzana", "pera", "uva"]
for i, fruta in enumerate(frutas):
    print(i, fruta)
# 0 manzana
# 1 pera
# 2 uva
```

### `zip(*iterables)`
Agrupa elementos de varios iterables, creando tuplas de elementos en la misma posición.
```python
nombres = ["Ana", "Luis", "Eva"]
edades  = [30, 25, 28]
list(zip(nombres, edades))
# [('Ana', 30), ('Luis', 25), ('Eva', 28)]
```

### `map(function, iterable)`
Aplica una función a cada elemento de un iterable y devuelve un nuevo iterable.
```python
list(map(str.upper, ["hola", "mundo"]))  # ['HOLA', 'MUNDO']
list(map(lambda x: x**2, [1, 2, 3, 4])) # [1, 4, 9, 16]
```

### `filter(function, iterable)`
Filtra elementos de un iterable, dejando solo aquellos para los que la función devuelva `True`.
```python
numeros = [1, 2, 3, 4, 5, 6]
list(filter(lambda x: x % 2 == 0, numeros))  # [2, 4, 6]
```

### `sorted(iterable)`
Devuelve una nueva lista con los elementos ordenados.
```python
sorted([3, 1, 4, 1, 5])               # [1, 1, 3, 4, 5]
sorted(["banana", "apple", "cherry"])  # ['apple', 'banana', 'cherry']
sorted([3, 1, 4], reverse=True)        # [4, 3, 1]
```

### `reversed(seq)`
Devuelve un iterador que recorre la secuencia al revés.
```python
list(reversed([1, 2, 3, 4]))    # [4, 3, 2, 1]
list(reversed("Python"))        # ['n', 'o', 'h', 't', 'y', 'P']
```

### `iter(object)`
Crea y devuelve un iterador a partir de un objeto iterable.
```python
it = iter([10, 20, 30])
next(it)    # 10
next(it)    # 20
```

### `next(iterator)`
Obtiene el siguiente elemento de un iterador. Lanza `StopIteration` al agotarse.
```python
it = iter([1, 2, 3])
next(it)           # 1
next(it)           # 2
next(it, "fin")    # 3  (con valor por defecto si se agota)
```

### `slice(start, stop, step)`
Crea un objeto `slice` reutilizable, equivalente a la sintaxis `[start:stop:step]`.
```python
s = slice(1, 5, 2)
lista = [0, 1, 2, 3, 4, 5]
lista[s]    # [1, 3]
```

### `any(iterable)`
Devuelve `True` si al menos un elemento del iterable es verdadero.
```python
any([False, False, True])    # True
any([0, 0, 0])               # False
any([])                      # False
```

### `all(iterable)`
Devuelve `True` si todos los elementos del iterable son verdaderos.
```python
all([True, True, True])     # True
all([True, False, True])    # False
all([])                     # True
```

---

## 6. Orientación a Objetos y Clases

### `type(object)`
Devuelve el tipo o clase de un objeto.
```python
type(42)         # <class 'int'>
type("hola")     # <class 'str'>
type([1, 2, 3])  # <class 'list'>
```

### `isinstance(object, classinfo)`
Comprueba si un objeto es de una clase específica.
```python
isinstance(42, int)       # True
isinstance("hola", str)   # True
isinstance(3.14, int)     # False
```

### `issubclass(class, classinfo)`
Comprueba si una clase es subclase de otra.
```python
class Animal: pass
class Perro(Animal): pass

issubclass(Perro, Animal)   # True
issubclass(Animal, Perro)   # False
```

### `object()`
Crea una instancia del objeto base de Python (clase raíz de todas las clases).
```python
obj = object()
type(obj)    # <class 'object'>
```

### `super()`
Se utiliza en una clase hija para llamar a métodos de su clase padre.
```python
class Animal:
    def hablar(self):
        return "..."

class Perro(Animal):
    def hablar(self):
        base = super().hablar()
        return f"{base} ¡Guau!"

Perro().hablar()    # '... ¡Guau!'
```

### `callable(object)`
Devuelve `True` si el objeto puede ser llamado como una función.
```python
callable(print)      # True
callable(42)         # False
callable(lambda: x)  # True
```

### `classmethod(function)`
Decorador que convierte un método en método de clase (recibe `cls` en lugar de `self`).
```python
class Contador:
    total = 0

    @classmethod
    def incrementar(cls):
        cls.total += 1

Contador.incrementar()
print(Contador.total)    # 1
```

### `staticmethod(function)`
Decorador que convierte un método en método estático (no recibe `self` ni `cls`).
```python
class Matematica:
    @staticmethod
    def sumar(a, b):
        return a + b

Matematica.sumar(3, 4)    # 7
```

### `property(fget, fset, fdel)`
Crea una propiedad gestionada en una clase (getters, setters, deleters).
```python
class Temperatura:
    def __init__(self, celsius):
        self._celsius = celsius

    @property
    def fahrenheit(self):
        return self._celsius * 9/5 + 32

t = Temperatura(100)
t.fahrenheit    # 212.0
```

### `dir(object)`
Devuelve una lista con todos los atributos y métodos disponibles de un objeto.
```python
dir([])      # ['append', 'clear', 'copy', 'count', ...]
dir(str)     # ['capitalize', 'center', 'count', ...]
```

### `vars(object)`
Devuelve el diccionario `__dict__` de un objeto con sus atributos y valores.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

p = Persona("Ana", 30)
vars(p)    # {'nombre': 'Ana', 'edad': 30}
```

### `hasattr(object, name)`
Comprueba si un objeto tiene un atributo con el nombre especificado.
```python
class Auto:
    color = "rojo"

hasattr(Auto, "color")    # True
hasattr(Auto, "precio")   # False
```

### `getattr(object, name)`
Obtiene el valor de un atributo de un objeto.
```python
class Auto:
    color = "rojo"

getattr(Auto, "color")              # 'rojo'
getattr(Auto, "precio", "N/A")     # 'N/A'  (valor por defecto)
```

### `setattr(object, name, value)`
Establece el valor de un atributo en un objeto.
```python
class Auto:
    pass

a = Auto()
setattr(a, "color", "azul")
print(a.color)    # azul
```

### `delattr(object, name)`
Elimina un atributo de un objeto.
```python
class Auto:
    color = "rojo"

a = Auto()
a.color = "verde"
delattr(a, "color")
# a.color ahora hereda el valor de clase: 'rojo'
```

---

## 7. Variables y Entorno de Ejecución

### `id(object)`
Devuelve la dirección de memoria única de un objeto (su "identificador").
```python
x = 42
id(x)        # p.ej. 140234567890  (varía según ejecución)
id("hola")   # un número diferente
```

### `hash(object)`
Devuelve el valor hash (un número identificador interno) de un objeto inmutable.
```python
hash("python")    # p.ej. 2230730083
hash(42)          # 42
hash((1, 2, 3))   # un número fijo
```

### `globals()`
Devuelve un diccionario con todas las variables globales actuales.
```python
x = 10
"x" in globals()    # True
globals()["x"]      # 10
```

### `locals()`
Devuelve un diccionario con todas las variables locales actuales.
```python
def mi_funcion():
    a = 1
    b = 2
    print(locals())    # {'a': 1, 'b': 2}

mi_funcion()
```

### `eval(expression)`
Evalúa y ejecuta una expresión de Python en formato de texto.
```python
eval("2 + 2")            # 4
eval("len([1, 2, 3])")   # 3
```

### `exec(object)`
Ejecuta código Python dinámico más complejo (como bloques enteros de código).
```python
codigo = """
for i in range(3):
    print(i)
"""
exec(codigo)
# 0
# 1
# 2
```

### `compile(source, filename, mode)`
Compila código fuente Python a bytecode, listo para ejecutar con `eval()` o `exec()`.
```python
codigo = compile("x + y", "<string>", "eval")
eval(codigo, {"x": 10, "y": 5})    # 15
```

---

## 8. Depuración y Ayuda

### `help(object)`
Muestra la documentación oficial y ayuda interactiva sobre un módulo, función o clase.
```python
help(print)
# Help on built-in function print in module builtins:
# print(*args, sep=' ', end='\n', file=None, flush=False)
#     Prints the values to a stream...
```

### `breakpoint()`
Activa el depurador interactivo (pdb) en el punto donde se llama. Disponible desde Python 3.7.
```python
def calcular(x, y):
    resultado = x + y
    breakpoint()      # La ejecución se pausa aquí para depurar
    return resultado
```

### `__import__(name)`
Importa un módulo de forma dinámica mediante su nombre como string.
```python
math = __import__("math")
math.sqrt(16)    # 4.0

# Forma recomendada con importlib:
# import importlib
# math = importlib.import_module("math")
```

---

## 9. Programación Asíncrona *(Python 3.10+)*

### `aiter(async_iterable)`
Devuelve un iterador asíncrono a partir de un objeto iterable asíncrono.
```python
import asyncio

class MiRango:
    def __init__(self, n): self.n = n
    def __aiter__(self): self.i = 0; return self
    async def __anext__(self):
        if self.i >= self.n: raise StopAsyncIteration
        self.i += 1; return self.i

async def main():
    async for val in aiter(MiRango(3)):
        print(val)    # 1, 2, 3

asyncio.run(main())
```

### `anext(async_iterator)`
Obtiene el siguiente valor de un iterador asíncrono. Equivale a `await __anext__()`.
```python
import asyncio

async def main():
    it = aiter(MiRango(3))
    print(await anext(it))    # 1
    print(await anext(it))    # 2

asyncio.run(main())
```

---

> **Tip:** Puedes escribir `help(nombre_de_funcion)` en la consola de Python para ver la explicación oficial y completa de cualquier función, por ejemplo: `help(print)`.
>
> También puedes ejecutar `dir(__builtins__)` para ver el listado completo de funciones built-in disponibles en tu versión de Python.
