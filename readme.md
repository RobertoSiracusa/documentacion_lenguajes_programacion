# Documentación Rust

Python

```
# Descargar e instalar Rust automáticamente
!curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y

# Actualizar el PATH para usar Rust en las siguientes celdas
import os
os.environ['PATH'] += ":/root/.cargo/bin"
```

Python

```
!/root/.cargo/bin/rustc --version
```

### Declaración de Variables:

En Rust, la declaración de variables se realiza mediante la palabra clave `let` y, por defecto, todas las variables son inmutables, lo que significa que su valor no puede cambiar una vez asignado. Para permitir que una variable modifique su contenido, es estrictamente necesario añadir el modificador `mut`, reflejando así el enfoque del lenguaje hacia la seguridad de memoria y el control de datos.

Bash

```
%%bash
cat << 'EOF' > suma.rs
fn main() {
    // Declaración de dos variables numéricas
    let numero1 = 15;
    let numero2 = 25;

    // Suma de las variables
    let resultado = numero1 + numero2;

    // Impresión del resultado en consola
    println!("La suma de {} y {} es: {}", numero1, numero2, resultado);
}
EOF

# Compilar el archivo
rustc suma.rs

# Ejecutar el binario resultante
./suma
```

### Condicional

En Rust, la estructura condicional `if` funciona como una expresión que evalúa una condición booleana sin necesidad de paréntesis. Una de sus mayores ventajas es que, al ser una expresión, puede retornar un valor directamente para ser asignado a una variable, siempre que ambos bloques (`if` y `else`) devuelvan el mismo tipo de dato.

Bash

```
%%bash
cat << 'EOF' > condicional.rs
fn main() {
    let edad = 20;

    // Estructura condicional if / else
    if edad >= 18 {
        println!("Con {} años, la persona es mayor de edad.", edad);
    } else {
        println!("Con {} años, la persona es menor de edad.", edad);
    }
}
EOF

# Compilar el archivo
rustc condicional.rs

# Ejecutar el binario resultante
./condicional
```

### Condicional While

En Rust, el bucle `while` se utiliza para repetir un bloque de código mientras una condición booleana sea verdadera. Es la estructura ideal cuando no se conoce de antemano el número de iteraciones, exigiendo que la variable de control sea marcada como mutable (`mut`) para poder actualizarse dentro del ciclo.

Bash

```
%%bash
cat << 'EOF' > bucle_while.rs
fn main() {
    let mut contador = 1;

    // Bucle while que se ejecuta mientras la condición sea verdadera
    while contador <= 5 {
        println!("El contador actual es: {}", contador);
        contador += 1; // Incrementamos el valor para no crear un bucle infinito
    }

    println!("¡Bucle finalizado!");
}
EOF

# Compilar el archivo
rustc bucle_while.rs

# Ejecutar el binario resultante
./bucle_while
```

### Bucle iterativo For

En Rust, el bucle `for` es la herramienta preferida para iterar sobre colecciones o rangos de números de forma segura y eficiente. En lugar de manejar manualmente un índice, utiliza un iterador que recorre los elementos directamente (por ejemplo, `1..5`), lo que elimina errores comunes como el acceso a índices fuera de los límites del arreglo.

Bash

```
%%bash
cat << 'EOF' > bucle_for.rs
fn main() {
    // Bucle for que itera sobre un rango del 1 al 5
    for i in 1..=5 {
        println!("Iteración número: {}", i);
    }

    println!("¡Bucle for finalizado!");
}
EOF

# Compilar el archivo
rustc bucle_for.rs

# Ejecutar el binario resultante
./bucle_for
```

### Declaración y ejecución de función

En Rust, las funciones se definen con la palabra clave `fn` y utilizan una sintaxis de "flecha" (`->`) para especificar el tipo de retorno. Una característica distintiva es que permiten el retorno implícito: si la última línea de la función no tiene punto y coma, Rust la interpreta automáticamente como el valor que debe devolver la función.

Bash

```
%%bash
cat << 'EOF' > funcion.rs
// Declaración de una función que recibe dos enteros y retorna un entero
fn multiplicar(a: i32, b: i32) -> i32 {
    // En Rust, la última expresión de una función se retorna automáticamente
    // si no lleva punto y coma al final.
    a * b
}

fn main() {
    let num1 = 6;
    let num2 = 7;

    // Llamada a la función y almacenamiento del valor devuelto en una variable
    let resultado = multiplicar(num1, num2);

    // Imprimir el resultado
    println!("El resultado de multiplicar {} y {} es: {}", num1, num2, resultado);
}
EOF

# Compilar el archivo
rustc funcion.rs

# Ejecutar el binario resultante
./funcion
```

### Declaración de Arrays

En Rust, los arrays son colecciones de longitud fija que agrupan elementos del mismo tipo de forma contigua en la memoria. Se definen indicando tanto el tipo de dato como la cantidad de elementos entre corchetes, y son fundamentales cuando se busca un rendimiento óptimo y un control estricto sobre la estructura de los datos sin el costo de memoria de una lista dinámica.

Bash

```
%%bash
cat << 'EOF' > arreglos.rs
fn main() {
    // Declaración de un array con 5 números enteros
    let numeros = [10, 20, 30, 40, 50];

    // Método .len() para saber cuántos elementos tiene el array
    let cantidad = numeros.len();
    println!("El array tiene {} elementos.", cantidad);

    // Método .contains() para buscar un elemento específico
    // Se utiliza & para pasar la referencia del valor que buscamos
    let valor_a_buscar = 30;

    if numeros.contains(&valor_a_buscar) {
        println!("¡El array sí contiene el número {}!", valor_a_buscar);
    } else {
        println!("El array no contiene el número {}.", valor_a_buscar);
    }
}
EOF

# Compilar el archivo
rustc arreglos.rs

# Ejecutar el binario resultante
./arreglos
```

---

# Documentación Go

Python

```
!apt-get update
!apt-get install golang-go -y
```

### Declaración de variables

En Golang, la declaración de variables destaca por su versatilidad al combinar un tipado fuertemente estático con la inferencia de tipos. Aunque se puede utilizar la palabra reservada `var` para definir explícitamente el nombre y el tipo de una variable, el lenguaje brilla por el uso del operador de declaración corta `:=` dentro de las funciones. Este operador permite asignar e inicializar la variable de forma inmediata, delegando al compilador la tarea de deducir automáticamente su tipo de dato según el valor proporcionado, lo que resulta en un código mucho más limpio y ágil de escribir.

Bash

```
%%bash
cat << 'EOF' > suma.go
package main

import "fmt"

func main() {
    // Declaración e inicialización corta de variables numéricas
    numero1 := 15
    numero2 := 25

    // Suma de las variables
    resultado := numero1 + numero2

    // Impresión del resultado en consola
    fmt.Printf("La suma de %d y %d es: %d\n", numero1, numero2, resultado)
}
EOF

# Compilar y ejecutar el archivo en un solo paso
go run suma.go
```

### Condicional IF

La estructura condicional `if` en Golang evalúa expresiones lógicas con una sintaxis directa y minimalista. A diferencia de otros lenguajes, no requiere utilizar paréntesis alrededor de la condición a evaluar, pero a cambio exige de forma estricta y obligatoria el uso de llaves `{}` para delimitar su bloque de código.

Bash

```
%%bash
cat << 'EOF' > condicional.go
package main

import "fmt"

func main() {
    edad := 20

    // Estructura condicional if / else sin paréntesis
    if edad >= 18 {
        fmt.Printf("Con %d años, la persona es mayor de edad.\n", edad)
    } else {
        fmt.Printf("Con %d años, la persona es menor de edad.\n", edad)
    }
}
EOF

# Compilar y ejecutar en un solo paso
go run condicional.go
```

### Condicional While

En Golang, la palabra reservada `while` no existe. En su lugar, el lenguaje utiliza su versátil bucle `for` de manera simplificada, indicando únicamente la condición a evaluar (sin inicialización ni incremento explícito). Esto permite ejecutar un bloque de código repetidamente mientras dicha condición se mantenga verdadera, cumpliendo exactamente la misma función.

Bash

```
%%bash
cat << 'EOF' > bucle_while.go
package main

import "fmt"

func main() {
    contador := 1

    // Bucle for comportándose como un while
    // Se ejecuta mientras la condición sea verdadera
    for contador <= 5 {
        fmt.Printf("El contador actual es: %d\n", contador)
        contador++ // Incrementamos el valor
    }

    fmt.Println("¡Bucle finalizado!")
}
EOF

# Compilar y ejecutar en un solo paso
go run bucle_while.go
```

### Bucle iterativo For

El bucle `for` iterativo tradicional en Golang sigue la estructura clásica de tres partes separadas por punto y coma: inicialización de la variable, condición a evaluar y el paso de incremento. Al igual que en el condicional `if`, su sintaxis omite por completo los paréntesis alrededor de estos elementos, pero mantiene el uso estricto y obligatorio de las llaves `{}` para delimitar el bloque de instrucciones.

Bash

```
%%bash
cat << 'EOF' > bucle_for.go
package main

import "fmt"

func main() {
    // Bucle for tradicional: inicialización; condición; incremento
    for i := 1; i <= 5; i++ {
        fmt.Printf("Iteración número: %d\n", i)
    }

    fmt.Println("¡Bucle for finalizado!")
}
EOF

# Compilar y ejecutar en un solo paso
go run bucle_for.go
```

### Declaración y ejecución de funciones

La declaración de funciones en Golang utiliza la palabra reservada `func` e impone un tipado estricto tanto para los parámetros de entrada como para los valores de retorno. Una de sus características más destacadas en esta estructura es la capacidad nativa de devolver múltiples resultados simultáneamente desde una sola función.

Bash

```
%%bash
cat << 'EOF' > funcion.go
package main

import "fmt"

// Declaración de una función que recibe dos enteros y retorna un entero
func multiplicar(a int, b int) int {
    return a * b
}

func main() {
    num1 := 6
    num2 := 7

    // Llamada a la función y almacenamiento del valor devuelto
    resultado := multiplicar(num1, num2)

    // Imprimir el resultado
    fmt.Printf("El resultado de multiplicar %d y %d es: %d\n", num1, num2, resultado)
}
EOF

# Compilar y ejecutar en un solo paso
go run funcion.go
```

### Declaración de arrays

Los arrays en Golang son estructuras rígidas que almacenan secuencias de elementos de un mismo tipo bajo una longitud fija y predeterminada desde su declaración. Debido a esta limitación de tamaño, en la práctica el lenguaje suele favorecer el uso de slices (porciones dinámicas) para obtener mayor flexibilidad, aunque los arrays puros siguen siendo la base fundamental que los sustenta en memoria.

Bash

```
%%bash
cat << 'EOF' > arreglos.go
package main

import "fmt"

func main() {
    // Declaración de un array de tamaño fijo con 5 números enteros
    numeros := [5]int{10, 20, 30, 40, 50}

    // Función len() para saber cuántos elementos tiene el array
    cantidad := len(numeros)
    fmt.Printf("El array tiene %d elementos.\n", cantidad)

    // Búsqueda de un elemento específico iterando con 'range'
    valorABuscar := 30
    encontrado := false

    // El guion bajo (_) ignora el índice, ya que solo nos interesa el valor
    for _, valor := range numeros {
        if valor == valorABuscar {
            encontrado = true
            break
        }
    }

    if encontrado {
        fmt.Printf("¡El array sí contiene el número %d!\n", valorABuscar)
    } else {
        fmt.Printf("El array no contiene el número %d.\n", valorABuscar)
    }
}
EOF

# Compilar y ejecutar en un solo paso
go run arreglos.go
```