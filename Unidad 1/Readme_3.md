> ### EJERCICIOS DE LISP: car, cdr y condicionales 
1. La función **primer-elemento** toma una lista como entrada y devuelve su primer elemento utilizando *car*, que extrae la cabeza de la lista. Si la lista está vacía (*null lista*), devuelve *nil*, indicando que no hay elementos en la lista. De lo contrario, simplemente retorna el primer elemento.

2. La función **segundo-elemento** primero verifica si la lista es *nil* o si no tiene al menos dos elementos (*null (cdr lista)*). En estos casos, devuelve *nil*. Si la lista tiene al menos dos elementos, usa *cdr* para obtener la lista sin el primer elemento y luego *car* para devolver el primer elemento de esa nueva lista, que corresponde al segundo elemento original.

3. La función **ultimo-elemento** utiliza recursión para recorrer la lista hasta encontrar el último elemento. Si la lista está vacía, devuelve *nil*. Si *cdr lista* es *nil*, significa que solo queda un elemento en la lista, por lo que lo retorna con *car lista*. En caso contrario, sigue llamándose recursivamente con *cdr lista* hasta encontrar el último elemento.

4. La función **longitud-lista** calcula la cantidad de elementos en una lista de manera recursiva. Si la lista está vacía, devuelve *0*. Si no, suma `1` al resultado de llamar a *longitud-lista* sobre *cdr lista*, lo que va reduciendo la lista hasta que sea vacía, acumulando el número total de elementos en la pila de llamadas.

5. La función **suma-lista** devuelve la suma de todos los elementos de una lista de números. Si la lista está vacía, devuelve *0*. Si no, usa *car* para obtener el primer número y lo suma al resultado de la llamada recursiva a *suma-lista* con *cdr lista*, lo que reduce la lista hasta que todos los elementos han sido sumados.

6. La función **pertenece** verifica si un elemento está en la lista. Si la lista está vacía, devuelve *no pertenece a la lista* porque el elemento no puede estar presente. Si *car lista* es igual al elemento buscado, devuelve *pertenece a la lista*. De lo contrario, llama recursivamente a *pertenece* con *cdr lista*, buscando el elemento en el resto de la lista.

7. La función **invertir-lista** invierte el orden de los elementos de una lista de forma recursiva. Si la lista está vacía, devuelve *nil*. En cada llamada, *cdr lista* se invierte primero, y luego se agrega *car lista* al final con *append*, construyendo la lista invertida de atrás hacia adelante.

8. La función **eliminar-ocurrencias** recorre la lista y elimina todas las apariciones de un elemento específico. Si la lista está vacía, devuelve *nil*. Si *car lista* es igual al elemento a eliminar, lo descarta y sigue con *cdr lista*. Si no, usa *cons* para mantener el primer elemento y lo combina con la llamada recursiva a *eliminar-ocurrencias* en el resto de la lista.

9. La función **enesimo-elemento** obtiene el elemento en la posición *n* de una lista. Si la lista está vacía, devuelve *nil*. Si *n* es *0*, devuelve *car lista* porque es el primer elemento. En otro caso, resta *1* a *n* y llama recursivamente a *enesimo-elemento* con *cdr lista*, reduciendo *n* hasta que alcanza *0* y devuelve el elemento deseado.

10. La función **concatenar-listas** une dos listas. Si *lista1* está vacía, devuelve *lista2*. En otro caso, toma *car lista1*, lo une con *cons* al resultado de llamar recursivamente *concatenar-listas* sobre *cdr lista1* y *lista2*, construyendo la lista final elemento por elemento.

```Lisp
EJERCICIOS DE LISP: car, cdr y condicionales 

; Ejercicio 1: Primer elemento de una lista
; Implementa una funcion que devuelva el primer elemento de una lista dada.
; (primer-elemento '(1 2 3 4))
(defun primer-elemento (lista)
  (if (null lista)
      nil
      (car lista)))

; Ejercicio 2: Segundo elemento de una lista
; Escribe una funcion que devuelva el segundo elemento de una lista.
; (segundo-elemento '(1 2 3 4))
(defun segundo-elemento (lista)
  (if (or (null lista) (null (cdr lista)))
      nil
      (car (cdr lista))))

; Ejercicio 3: Ultimo elemento de una lista
; Escribe una funcion que devuelva el ultimo elemento de una lista.
; (ultimo-elemento '(1 2 3 4))
(defun ultimo-elemento (lista)
  (cond
    ((null lista) nil)
    ((null (cdr lista)) (car lista))
    (t (ultimo-elemento (cdr lista)))))

; Ejercicio 4: Longitud de una lista
; Implementa una funcion que calcule la cantidad de elementos en una lista.
; (longitud-lista '(1 2 3 4))
(defun longitud-lista (lista)
  (if (null lista)
      0
      (+ 1 (longitud-lista (cdr lista)))))

; Ejercicio 5: Suma de una lista de numeros
; Crea una funcion que sume todos los elementos de una lista de numeros.
; (suma-lista '(1 2 3 4))
(defun suma-lista (lista)
  (if (null lista)
      0
      (+ (car lista) (suma-lista (cdr lista)))))

; Ejercicio 6: Verificar si un elemento esta en una lista
; Escribe una funcion que determine si un elemento esta en una lista.
; (pertenece 3 '(1 2 3 4))
(defun pertenece (elem lista)
  (cond
    ((null lista) (format t "No pertenece a la lista"))
    ((equal elem (car lista)) (format t "Si pertene a la lista"))
    (t (pertenece elem (cdr lista)))))

; Ejercicio 7: Invertir una lista
; Escribe una funcion para invertir el orden de los elementos de una lista.
; (invertir-lista '(1 2 3 4))
(defun invertir-lista (lista)
  (if (null lista)
      nil
      (append (invertir-lista (cdr lista)) (list (car lista)))))

; Ejercicio 8: Eliminar todas las ocurrencias de un elemento
; Implementa una funcion que elimine todas las ocurrencias de un elemento en una lista.
; (eliminar-ocurrencias 2 '(1 2 3 2 4)) 
(defun eliminar-ocurrencias (elem lista)
  (cond
    ((null lista) nil)
    ((equal elem (car lista)) (eliminar-ocurrencias elem (cdr lista)))
    (t (cons (car lista) (eliminar-ocurrencias elem (cdr lista))))))

; Ejercicio 9: Obtener el enesimo elemento de una lista
; Escribe una funcion que devuelva el elemento enesimo de una lista.
; (enesimo-elemento 2 '(10 20 30 40)) 
(defun enesimo-elemento (n lista)
  (cond
    ((null lista) nil)
    ((= n 0) (car lista))
    (t (enesimo-elemento (- n 1) (cdr lista)))))

; Ejercicio 10: Concatenar dos listas
; Implementa una funcion que concatene dos listas.
; (concatenar-listas '(1 2) '(3 4))
(defun concatenar-listas (lista1 lista2)
  (if (null lista1)
      lista2
      (cons (car lista1) (concatenar-listas (cdr lista1) lista2))))
```
