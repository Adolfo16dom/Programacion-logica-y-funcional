# PROGRAMACIÓN LÓGICA Y FUNCINAL 
## UNIDAD 1

> ### Funciones de areas y volumenes 
```Lisp
;; -----------------   AREAS ----------------------------
(defun area_cuadrado( lado )
(setq c (* lado lado)) 
(princ c)   
)

(defun area_rectangulo(base altura )
(setq c (* base altura)) 
(princ c)   
)

(defun area_triangulo( base altura )
(/ (* base altura) 2.0))

(defun area_circulo( radio )
(setq c (* radio radio 3.1416)) 
(princ c)   
)

(defun area_trapecio( b1 b2 h )
(setq c (/ (* (+ b1 b2) h) 2)) 
(princ c)   
)
;; ---------------- VOLUMENES ------------------------
(defun vol_cubo( lado )
(setq c (* lado lado lado)) 
(princ c)   
)

(defun vol_prisma_rectangular(base altura ancho )
(setq c (* base altura ancho)) 
(princ c)   
)

(defun vol_cilindro( radio altura )
(setq c (* radio radio altura 3.1416)) 
(princ c)   
)

(defun vol_esfera( radio )
(setq c (/ (* (* radio radio radio) 3.1416 4) 3)) 
(princ c)   
)

(defun vol_piramide( base altura )
(setq c (/ (* base altura) 3)) 
(princ c)   
)
``` 

> ### Adivinar el número 
```Lisp
(defun guess-my-number ()
(ash (+ *small* *big*) -1)

)

(defun smaller()
(setf *big* (1- (guess-my-number)))
(guess-my-number)
)

(defun bigger ()
(setf *small* (1+ (guess-my-number)))
(guess-my-number)
)

(defun start-over ()
(defparameter *small* 1)
(defparameter *big* 100)
(guess-my-number)
)
```

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


