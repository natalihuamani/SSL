-----2------Preprocesar hello2.c, no compilar, y generar hello2.i. 

C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc hello2.c
hello2.c: In function 'main':
hello2.c:10:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]
  prontf("La respuesta es %d\n");
  ^~~~~~
hello2.c:10:2: error: expected declaration or statement at end of input

C:\Users\Naty\eclipse-workspace\DD-FasesErrores> gcc -E hello2.c > hello2.i

----5----Preprocesar hello3.c, no compilar, y generar hello3.i.

C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc -E hello3.c > hello3.i

---6--- Compilar el resultado y generar hello3.s, no ensamblar

C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc hello3.c
hello3.c: In function 'main':
hello3.c:4:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]
  prontf("La respuesta es %d\n");
  ^~~~~~
hello3.c:4:2: error: expected declaration or statement at end of input


C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc -S hello3.c
hello3.c: In function 'main':
hello3.c:4:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]
  prontf("La respuesta es %d\n");
  ^~~~~~
hello3.c:4:2: error: expected declaration or statement at end of input


---7-- Corregir en el nuevo archivo hello4.c y empezar de nuevo, generar hello4.s, no ensamblar

C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc hello4.c
hello4.c: In function 'main':
hello4.c:5:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]
  prontf("La respuesta es %d\n");
  ^~~~~~
C:\Users\Naty\AppData\Local\Temp\ccde0qHh.o:hello4.c:(.text+0x1c): referencia a `prontf' sin definir
collect2.exe: error: ld returned 1 exit status

C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc -E hello4.c > hello4.i

C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc -S hello4.c
hello4.c: In function 'main':
hello4.c:5:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]
  prontf("La respuesta es %d\n");
  ^~~~~~

---9---- Ensamblar hello4.s en hello4.o, no vincular
C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc -c hello4.c
hello4.c: In function 'main':
hello4.c:5:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]
  prontf("La respuesta es %d\n");
  ^~~~~~


--10-- Vincular hello4.o con la biblioteca estándar y generar el ejecutable

C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc -o hello4 hello4.o
hello4.o:hello4.c:(.text+0x1c): referencia a `prontf' sin definir
collect2.exe: error: ld returned 1 exit status



--11-- Corregir en hello5.c y generar el ejecutable.
C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc hello5.c


--13-- Corregir en hello6.c y empezar de nuevo.

C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc hello6.c

--14-- 4.Escribir hello7.c, una nueva variante:

C:\Users\Naty\eclipse-workspace\DD-FasesErrores>gcc hello7.c
hello7.c: In function 'main':
hello7.c:3:2: warning: implicit declaration of function 'printf' [-Wimplicit-function-declaration]
  printf("La respuesta es %d\n", i);
  ^~~~~~
hello7.c:3:2: warning: incompatible implicit declaration of built-in function 'printf'
hello7.c:3:2: note: include '<stdio.h>' or provide a declaration of 'printf'
 
 
--15-- Porque funciona

C proporcionará automáticamente una declaración implícita para una función si no hay un prototipo en el alcance (como debido a la omisión de #include <stdio.h>). La declaración implícita sería:

int printf();

Lo que significa que printf es una función que devuelve un int y puede tomar cualquier cantidad de argumentos.
    

