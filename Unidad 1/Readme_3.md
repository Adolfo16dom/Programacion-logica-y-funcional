;; EJERCICIOS DE LISP: car, cdr y condicionales 

;; Ejercicio 1: Primer elemento de una lista
;;  Implementa una funcion que devuelva el primer elemento de una lista dada.
(defun primer-elemento (lista)
  (if (null lista)
      nil
      (car lista)))

;; Ejercicio 2: Segundo elemento de una lista
;;  Escribe una funcion que devuelva el segundo elemento de una lista.
(defun segundo-elemento (lista)
  (if (or (null lista) (null (cdr lista)))
      nil
      (car (cdr lista))))

;; Ejercicio 3: Ultimo elemento de una lista
;; Escribe una funcion que devuelva el ultimo elemento de una lista.
(defun ultimo-elemento (lista)
  (cond
    ((null lista) nil)
    ((null (cdr lista)) (car lista))
    (t (ultimo-elemento (cdr lista)))))

;; Ejercicio 4: Longitud de una lista
;; Implementa una funcion que calcule la cantidad de elementos en una lista.
(defun longitud-lista (lista)
  (if (null lista)
      0
      (+ 1 (longitud-lista (cdr lista)))))

;; Ejercicio 5: Suma de una lista de numeros
;;  Crea una funcion que sume todos los elementos de una lista de numeros.
(defun suma-lista (lista)
  (if (null lista)
      0
      (+ (car lista) (suma-lista (cdr lista)))))

