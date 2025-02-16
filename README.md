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

