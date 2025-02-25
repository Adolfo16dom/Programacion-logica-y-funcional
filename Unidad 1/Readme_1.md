# PROGRAMACIÓN LÓGICA Y FUNCINAL 
## UNIDAD 1

> ### Funciones de areas y volumenes 
```Lisp
;; -----------------   AREAS ----------------------------
(defun area_cuadrado()
(format t "Ingresa el lado del cuadrado:")
(setq lado (read))
(setq c (* lado lado))   
)

(defun area_rectangulo()
(format t "Ingresa la base del rectangulo:")
(setq base (read))
(format t "Ingresa la altura del rectanfulo:")
(setq altura (read))
(setq c (* base altura))    
)

(defun area_triangulo()
(format t "Ingresa la base del triangulo:")
(setq base (read))
(format t "Ingresa la altura del triangulo:")
(setq altura (read))
(/ (* base altura) 2.0))

(defun area_circulo()
(format t "Ingresa el radio del circulo:")
(setq radio (read))
(setq c (* radio radio 3.1416)) 
)

(defun area_trapecio()
(format t "Ingresa la primera base del trapecio:")
(setq b1 (read))
(format t "Ingresa la segunda base del trapecio:")
(setq  b2 (read))
(format t "Ingresa la altura del trapecio:")
(setq h (read))
(setq c (/ (* (+ b1 b2) h) 2))
)
;; ---------------- VOLUMENES ------------------------
(defun vol_cubo()
(format t "Ingresa el lado del cubo:")
(setq lado (read))
(setq c (* lado lado lado))
)

(defun vol_prisma_rectangular()
(format t "Ingresa la base del prisma rectangular:")
(setq base (read))
(format t "Ingresa la altura del prisma rectangular:")
(setq  altura (read))
(format t "Ingresa el ancho del prisma rectangular:")
(setq ancho (read))
(setq c (* base altura ancho)) 
)

(defun vol_cilindro()
(format t "Ingresa el radio del cilindro:")
(setq radio (read))
(format t "Ingresa la altura del cilindro:")
(setq altura (read))
(setq c (* radio radio altura 3.1416))   
)

(defun vol_esfera()
(format t "Ingresa el radio de la esfera:")
(setq radio (read))
(setq c (/ (* (* radio radio radio) 3.1416 4) 3))   
)

(defun vol_piramide()
(format t "Ingresa la base de la piramide:")
(setq base (read))
(format t "Ingresa la altura de la piramide:")
(setq altura (read))
(setq c (/ (* base altura) 3))   
)
``` 
### Cálculo de Áreas

Para calcular el área de un cuadrado, definí la función area_cuadrado, que recibe el lado como parámetro. Multiplico el valor del lado por sí mismo y lo almaceno en la variable c con set. Finalmente, utilizo princ para imprimir el resultado.

El cálculo del área de un rectángulo se hace en la función area_rectangulo, donde recibo la base y la altura como parámetros. Multiplico estos valores y almaceno el resultado en c, que posteriormente se imprime.

Para el triángulo, utilizo la función area_triangulo, que también recibe base y altura, pero en este caso, divido el producto de ambos entre 2.0. A diferencia de otras funciones, aquí no utilizo setq ni princ, simplemente retorno el resultado directamente.

El área del círculo se calcula en area_circulo, donde recibo el radio, lo elevo al cuadrado y lo multiplico por 3.1416, una aproximación de π. Guardo este resultado en c y lo imprimo.

Finalmente, para calcular el área de un trapecio, uso la función area_trapecio, que recibe las bases b1 y b2, además de la altura. Primero sumo ambas bases, luego multiplico por la altura y divido entre 2. El resultado se almacena en c y se imprime.

### Cálculo de Volúmenes

En cuanto a los volúmenes, la función vol_cubo calcula el volumen de un cubo recibiendo el lado como parámetro. Para obtener el resultado, elevo el lado al cubo y lo almaceno en c, que luego imprimo con princ.

Para calcular el volumen de un prisma rectangular, utilizo vol_prisma_rectangular, donde recibo la base, la altura y el ancho. Multiplico estos valores y los almaceno en c antes de imprimir el resultado.

El volumen del cilindro se obtiene en vol_cilindro, donde recibo el radio y la altura. Elevo el radio al cuadrado, lo multiplico por la altura y por 3.1416. El resultado se guarda en c y se imprime.

La función vol_esfera calcula el volumen de una esfera recibiendo el radio como parámetro. Elevo el radio al cubo, multiplico por 4 * π y luego divido entre 3. Finalmente, almaceno el resultado en c y lo imprimo.

Por último, para calcular el volumen de una pirámide, utilizo vol_piramide, que recibe la base y la altura. Multiplico ambos valores y divido entre 3, almacenando el resultado en c antes de imprimirlo.


> ### Adivinar el número 
```Lisp
(defun guess-my-number ()
(ash (+ *small* *big*) -1))

(defun smaller()
(setf *big* (1- (guess-my-number)))
(guess-my-number))

(defun bigger ()
(setf *small* (1+ (guess-my-number)))
(guess-my-number))

(defun start-over ()
(defparameter *small* 1)
(defparameter *big* 100)
(guess-my-number))
```

La función guess-my-number calcula la suposición de la computadora basándose en el rango actual de búsqueda. Se suman los valores small y big y los divido por 2 usando la función ash con -1, lo que equivale a hacer un desplazamiento aritmético a la derecha es decir, dividir por 2. De esta manera, siempre tomo el punto medio del rango actual como la siguiente suposición.

La función smaller actualiza big para que sea uno menos que la suposición actual (guess-my-number). Esto significa que descarto la mitad superior del rango y me concentro en la mitad inferior. Luego, llamo nuevamente a guess-my-number para hacer una nueva suposición.

La función bigger aumento small en 1, lo que significa que descarto la mitad inferior del rango y continúo buscando en la mitad superior. Luego, llamo nuevamente a guess-my-number para hacer la siguiente suposición.

Esta función start-over reinicia el juego, estableciendo un nuevo rango de búsqueda de 1 a 100. Primero, se define small como 1 y big como 100, lo que significa que el número a adivinar debe estar en ese rango. Luego, llamo a guess-my-number para que la computadora haga su primera suposición con estos valores iniciales.



> ### Funciones para sacar el factorial y fibonnaci
```Lisp
(defun facto(x)
(if (= x 0)
1
(* x (facto (- x 1))))
)

(defun fibo(x)
(if (< x 2)
1
(+ (fibo(- x 1)) (fibo(- x 2))))

)
```
La función facto(x) calcula el factorial de un número de manera recursiva. Si el valor de x es 0, la función devuelve 1 como caso base, ya que el factorial de 0 es 1. En cualquier otro caso, la función multiplica x por la llamada recursiva facto(x - 1), reduciendo el valor de x hasta que alcance 0. De esta manera, los valores se van multiplicando al regresar en la recursión, obteniendo finalmente el factorial del número dado.

Por otro lado, la función fibo(x) calcula el número de Fibonacci en la posición x utilizando una estructura recursiva. Si x es menor que 2, retorna 1 como caso base, ya que los dos primeros números de Fibonacci son 1. En cualquier otro caso, la función suma fibo(x - 1) + fibo(x - 2), llamándose a sí misma recursivamente para obtener los dos valores anteriores en la serie. Por ejemplo, si llamamos a fibo(5), la función descompone el problema en fibo(4) + fibo(3), y a su vez cada uno de estos valores se desglosa hasta alcanzar los casos base.

> ### Funciones (Potencias con sumas y divisiones con restas)
```Lisp
;;Potencias con sumas
(defun potencia_suma (base exponente)
(if (= exponente 0)
    1 
    (multiplicar base (potencia_suma base (- exponente 1)))))
(defun multiplicar (a b)
(if (= b 0)
    0
    (+ a (multiplicar a (- b 1)))))


;; Y dividir con restas
(defun division_resta (dividendo divisor)
    (if (< dividendo divisor) 
    0                      
    (+ 1 (division_resta (- dividendo divisor) divisor))
    
    )
) 
```
La función potencia_suma(base, exponente) calcula la potencia de un número utilizando puras sumas. Si el exponente es 0, la función retorna 1, ya que cualquier número elevado a la potencia de 0 es 1. En cualquier otro caso, la función multiplica la base por el resultado de potencia_suma(base, exponente - 1), reduciendo el exponente hasta alcanzar el caso base. Sin embargo, en lugar de utilizar la multiplicación directa, usa la función multiplicar(a, b), la cual se basa en sumas repetitivas para calcular el producto de dos números. Esta última función verifica si b es 0 y, de ser así, retorna 0 como caso base. Si b es mayor que 0, suma a a la llamada recursiva multiplicar(a, b - 1), lo que significa que se va sumando a tantas veces como indique b.

Por otro lado, la función division_resta(dividendo, divisor) realiza la división de manera recursiva utilizando restas sucesivas. Si el dividendo es menor que el divisor, significa que no se puede seguir restando, por lo que retorna 0 como caso base, indicando que la división ha terminado. En cualquier otro caso, la función resta el divisor del dividendo y suma 1 a la llamada recursiva division_resta(dividendo - divisor, divisor), representando así el número de veces que el divisor cabe dentro del dividendo.

> ### Ejercicios con car y cdr
```Lisp
 Lista: (a b c d e) → Extraer d
  (cadddr '(a b c d e))

  Lista: ((1 2) (3 4) (5 6)) → Extraer 5
  (caaddr '((1 2) (3 4) (5 6)))

  Lista: ((a b) (c d) (e f)) → Extraer e
  (caaddr '((a b) (c d) (e f)))

  Lista: ((x y) ((p q) (r s)) (z w)) → Extraer z
  (car (cadddr '((x y) (p q) (r s) (z w))))

  Lista: ((1 (2 3)) (4 (5 6))) → Extraer 6
  (cadr (cadadr '((1 (2 3)) (4 (5 6)))))

  Lista: (((a b) c) d e) → Extraer c
  (cadar '(((a b) c) d e))

  Lista: (((1 2) 3) ((4 5) 6)) → Extraer 6
  (cadadr '(((1 2) 3) ((4 5) 6)))

  Lista: ((p (q (r s))) t u) → Extraer (r s)
  (car (cdadar '((p (q (r s))) t u)))

  Lista: (((a) b) (c (d e)) f) → Extraer d
  (car (cadadr '(((a) b) (c (d e)) f)))

  Lista: ((1 (2 (3 4))) (5 6)) → Extraer 3
  (caar (cdadar '((1 (2 (3 4))) (5 6))))

  Lista: (((x) (y)) ((z) (w))) → Extraer (w)
  (cadadr'(((x) (y)) ((z) (w))))
  
  Lista: ((a (b (c d))) (e f)) → Extraer c
  (caar (cdadar'((a (b (c d))) (e f))))

  Lista: ((1 (2 (3 (4 5)))) (6 7)) → Extraer 4
  (caadar (cdadar '((1 (2 (3 (4 5)))) (6 7))))

  Lista: (((a b) c) ((d e) f) ((g h) i)) → Extraer g
  (car (caaddr '(((a b) c) ((d e) f) ((g h) i))))

  Lista: (((x y) (z w)) ((p q) (r s))) → Extraer r
   (car (cadadr '(((x y) (z w)) ((p q) (r s)))))

  Lista: ((1 (2 (3 (4 (5 6))))) (7 8)) → Extraer 5
  (caar (cdadar (cdadar '((1 (2 (3 (4 (5 6))))) (7 8)))))

  Lista: ((a (b (c (d e)))) (f g)) → Extraer d
  (caadar (cdadar '((a (b (c (d e)))) (f g))))

  Lista: (((1 2) (3 4)) ((5 6) (7 8))) → Extraer 7
  (car (cadadr '(((1 2) (3 4)) ((5 6) (7 8)))))

  Lista: ((x (y (z (w v))))) → Extraer w
  (caadar (cdadar '((x (y (z (w v)))))))

  Lista: (((a b c) (d e f)) ((g h i) (j k l))) → Extraer j
  (car (cadadr '(((a b c) (d e f)) ((g h i) (j k l)))))

```

> ### Funciones primitivas de CLISP 
 
#### Funciones Matemáticas

- `expt`  
  Eleva un número a una potencia.  
  Ejemplo:
  ```lisp
  (expt 2 3)  ; 8
  ```

- `sqrt`  
  Devuelve la raíz cuadrada de un número.  
  Ejemplo:
  ```lisp
  (sqrt 9)  ; 3
  ```

- `mod`  
  Resto de una división.  
  Ejemplo:
  ```lisp
  (mod 5 3)  ; 2
  ```

#### Funciones Lógicas

- `and`  
  Devuelve `T` (verdadero) si todos los argumentos son verdaderos.  
  Ejemplo:
  ```lisp
  (and t nil)  ; nil
  ```

- `or`  
  Devuelve `T` si alguno de los argumentos es verdadero.  
  Ejemplo:
  ```lisp
  (or nil t)  ; t
  ```

- `not`  
  Devuelve el valor contrario de un booleano.  
  Ejemplo:
  ```lisp
  (not nil)  ; t
  ```

- `zerop`  
  Verifica si el número es cero.  
  Ejemplo:
  ```lisp
  (zerop 0)  ; t
  ```

- `evenp`  
  Verifica si el número es par.  
  Ejemplo:
  ```lisp
  (evenp 4)  ; t
  ```

- `oddp`  
  Verifica si el número es impar.  
  Ejemplo:
  ```lisp
  (oddp 3)  ; t
  ```

#### Funciones de Control de Flujo

- `if`  
  Estructura condicional.  
  Ejemplo:
  ```lisp
  (if (> 2 1) 'greater 'lesser)  ; greater
  ```

- `cond`  
  Estructura condicional con múltiples condiciones.  
  Ejemplo:
  ```lisp
  (cond ((> 2 3) 'too-large)
        ((> 2 1) 'greater)
        (t 'lesser))
  ```

- `when`  
  Una forma corta de `if` para condiciones verdaderas.  
  Ejemplo:
  ```lisp
  (when (> 2 1) (print "True"))
  ```

- `loop`  
  Estructura de bucle.  
  Ejemplo:
  ```lisp
  (loop for i from 1 to 5 do (print i))
  ```

#### Funciones de Manejo de Listas

- `car`  
  Devuelve el primer elemento de una lista.  
  Ejemplo:
  ```lisp
  (car '(1 2 3))  ; 1
  ```

- `cdr`  
  Devuelve la lista sin el primer elemento.  
  Ejemplo:
  ```lisp
  (cdr '(1 2 3))  ; (2 3)
  ```

- `cons`  
  Crea una nueva lista a partir de un elemento y una lista.  
  Ejemplo:
  ```lisp
  (cons 1 '(2 3))  ; (1 2 3)
  ```

- `list`  
  Crea una lista a partir de los elementos dados.  
  Ejemplo:
  ```lisp
  (list 1 2 3)  ; (1 2 3)
  ```

- `length`  
  Devuelve la longitud de una lista.  
  Ejemplo:
  ```lisp
  (length '(1 2 3))  ; 3
  ```

- `append`  
  Combina dos o más listas.  
  Ejemplo:
  ```lisp
  (append '(1 2) '(3 4))  ; (1 2 3 4)
  ```

#### Funciones de Manejo de Símbolos y Variables

- `setq`  
  Asigna un valor a una variable.  
  Ejemplo:
  ```lisp
  (setq x 10)
  ```

- `defvar`  
  Define una variable global.  
  Ejemplo:
  ```lisp
  (defvar y 20)
  ```

- `let`  
  Define variables locales dentro de un bloque de código.  
  Ejemplo:
  ```lisp
  (let ((x 10) (y 20))
    (+ x y))  ; 30
  ```

- `symbolp`  
  Verifica si un objeto es un símbolo.  
  Ejemplo:
  ```lisp
  (symbolp 'x)  ; t
  ```

#### Funciones de Entrada/Salida

- `princ`  
  Imprime un valor sin salto de línea.  
  Ejemplo:
  ```lisp
  (princ "Hello, World!")  ; Imprime sin salto de línea
  ```

- `print`  
  Imprime un valor con salto de línea.  
  Ejemplo:
  ```lisp
  (print "Hello, World!")  ; Imprime con salto de línea
  ```

- `read`  
  Lee una expresión del input estándar.  
  Ejemplo:
  ```lisp
  (setq x (read))  ; Lee una entrada
  ```


