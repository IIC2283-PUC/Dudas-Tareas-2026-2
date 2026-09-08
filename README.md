# Dudas-Tareas — IIC2283 Diseño y Análisis de Algoritmos, 2026-2

En la sección de [Issues](https://github.com/IIC2283-PUC/Dudas-Tareas-2026-2/issues) pueden
hacer preguntas sobre las tareas del curso.

**Antes de preguntar, revisa las [Preguntas frecuentes](#preguntas-frecuentes) más abajo.**
Están armadas con las dudas que más se repitieron en los semestres anteriores.

---

## Cómo obtener tu repositorio

Inscríbete **una sola vez para todo el semestre** en este link:

### 👉 [Inscripción IIC2283 2026-2](https://github.com/IIC2283-PUC/inscripcion-2026-2/issues/new?template=inscripcion.yml)

Necesitas una cuenta de GitHub. Completas tu nombre y número de alumno, y en menos de un
minuto recibes un comentario con el link a tu repositorio privado, más una invitación por
correo que tienes que aceptar.

Tu usuario de GitHub se toma automáticamente de la cuenta con la que envías el formulario,
así que **no lo escribas**: usa la cuenta que vas a ocupar durante todo el semestre.

Para las tareas siguientes no tienes que hacer nada: los repositorios se crean solos con
los datos de esta inscripción.

> **Importante:** sin inscribirte no tienes repositorio, y sin repositorio no hay forma de
> corregir tu tarea.

---

## Reglas

1. **No** se pueden publicar soluciones a las tareas, aunque sean parciales. Esto incluye
   código, pseudocódigo, o links a algoritmos que resuelvan alguna parte de la tarea. Issues
   que no cumplan con esta regla serán eliminadas.

2. No se asegura que se responderán dudas fuera de horario hábil.

3. Si una pregunta está repetida, esta se cerrará y se redirigirá a la original.

4. Una _issue_ se etiquetará como Resuelto cuando el alumno que la hizo confirme que su duda
   fue resuelta o hayan pasado 2 días desde la última respuesta.

---

## Preguntas frecuentes

### Entrega

<details>
<summary><b>¿Qué archivos tengo que entregar?</b></summary>

Solo los archivos de solución: `t1p1.py` y `t1p2.py` (y sus equivalentes en T2 y T3). Cada
uno debe ser **autosuficiente**: toda la solución de ese problema va en ese único archivo.

El `.gitignore` del repositorio está hecho a propósito para ignorar cualquier otro `.py`, así
que archivos como `test.py` o `main.py` no se suben ni se consideran. No lo modifiques para
saltarte esto.

Tu identidad ya quedó registrada al inscribirte, así que no necesitas poner tu nombre en
ningún archivo.
</details>

<details>
<summary><b>¿Puedo cambiar el código base que viene en el repositorio?</b></summary>

Sí. El código base de cada problema puede modificarse en su totalidad, o reemplazarse
completo, a discreción de cada estudiante. Lo único que importa es que el archivo lea de la
entrada estándar e imprima el resultado esperado.
</details>

<details>
<summary><b>¿Cómo entrego?</b></summary>

Haciendo push de la última versión de tus soluciones a la rama principal de tu repositorio.
Se corrige el **último commit anterior al plazo de entrega**. No hay que enviar nada por
correo ni por Canvas.
</details>

<details>
<summary><b>¿Qué pasa si entrego atrasado o uso el cupón de atraso?</b></summary>

Toda entrega posterior a las 48 horas del plazo no es válida, **incluso usando cupón**: en
ese caso el descuento es de 6.0.
</details>

### Input y output

<details>
<summary><b>¿Qué significa que se testea con <i>standard input</i> y <i>standard output</i>?</b></summary>

Que tu programa se ejecuta así:

```bash
python3 t1pX.py < input_YY.txt
```

El archivo de test entra por la entrada estándar: lo lees con `input()` línea por línea, o
con `sys.stdin`, la que prefieras. La respuesta la imprimes normalmente por consola con
`print()` o `sys.stdout`.

**No escribas archivos de salida.** Los `input_YY.txt` son solo los casos de prueba que se
te entregan; tu código no debe abrirlos ni crear ningún `output.txt`.
</details>

<details>
<summary><b>Imprimir con <code>print()</code> me multiplica el tiempo de ejecución. ¿Eso me perjudica?</b></summary>

No. En la corrección el output se redirige a un archivo:

```bash
python3 t1pX.py < input_YY.txt > output_YY.txt
```

Así el costo de imprimir en consola no cuenta dentro de tu tiempo. Tú de todas formas debes
imprimir de forma normal por consola, no escribir el archivo desde tu código.
</details>

<details>
<summary><b><code>diff</code> me marca diferencias aunque mi output se ve igual (terminadores de línea)</b></summary>

Es el clásico problema de CRLF vs LF al trabajar en Windows. No te preocupes: la corrección
normaliza ambos archivos antes de compararlos, quitando espacios, tabs y `\r` al final de
cada línea, y recién ahí ejecuta el `diff`:

```sh
awk 'NF{gsub(/[ \t\r]+$/, ""); print $0}' "$tu_output" > "${tu_output}_norm"
```

Si quieres reproducirlo localmente, `diff -b` o `diff --strip-trailing-cr` te dan el mismo
resultado.
</details>

### Librerías y código externo

<details>
<summary><b>¿Puedo usar librerías de la biblioteca estándar de Python?</b></summary>

Sí, cualquiera de la
[Standard Library](https://docs.python.org/3/library/index.html): `math`, `random`,
`bisect`, `heapq`, `collections`, `functools` (incluido `lru_cache`), etc.

Si el enunciado pide una complejidad determinada, usar una función de la librería estándar
está bien siempre que la complejidad se cumpla — por ejemplo `math.gcd` tiene la misma
complejidad que el algoritmo de Euclides visto en clases, y en la práctica es más rápido.
</details>

<details>
<summary><b>¿Puedo usar NumPy u otra librería externa?</b></summary>

**No.** Solo la librería estándar. En particular no se permite NumPy, tampoco para FFT: si
la tarea necesita FFT, el código base trae una implementación que puedes usar tal cual.

Si crees necesitar alguna librería adicional, pregunta **antes** de usarla.
</details>

<details>
<summary><b>¿Puedo usar código de internet o de una IA?</b></summary>

Sí, siempre que lo cites textualmente. Basta con dejar el comentario en el código o una nota
en tu `README.md` diciendo qué parte no es tuya y de dónde salió. No se exige un formato de
documentación especial.
</details>

<details>
<summary><b>¿Qué versión de Python tengo que usar?</b></summary>

La indicada en el enunciado. Si tienes una versión más nueva no debería haber problema: no
hay diferencias significativas entre las versiones recientes mientras uses solo la librería
estándar.
</details>

### Corrección

<details>
<summary><b>Mi solución cumple la complejidad pedida pero se pasa del tiempo en algunos casos. ¿Pierdo toda la pregunta?</b></summary>

No. **Cada caso de prueba se evalúa de forma independiente**, así que solo los casos que se
pasan del tiempo se consideran incorrectos; los demás siguen sumando.

De los casos de prueba de cada tarea, aproximadamente 5 a 10 usan las restricciones al
máximo y el resto son bastante menos exigentes, justamente para que no tengan que
preocuparse por microoptimizaciones.
</details>

<details>
<summary><b>¿Qué significan los veredictos?</b></summary>

| | Significado |
|---|---|
| `OK` | Respuesta correcta dentro del tiempo |
| `WA` | La respuesta no coincide con la esperada |
| `TLE` | Se pasó del tiempo límite |
| `CE` / `RE` | El programa se cayó (error de sintaxis, import prohibido, excepción) |
</details>

<details>
<summary><b>¿Y si mi problema admite varias respuestas correctas?</b></summary>

En esos casos la corrección no compara contra un output exacto, sino que valida tu respuesta
con un verificador propio. Basta con que tu respuesta sea válida según el enunciado.
</details>

---

## Tips

1. Una buena forma de resolver los ejercicios propuestos es inicialmente intentar una
   solución que solo resuelva el problema, sin importar la eficiencia. Luego, una vez que
   tengan una solución que funcione, plantearse qué partes del algoritmo se pueden mejorar
   para llegar a la complejidad solicitada.

2. A veces, la misma complejidad logra dar indicios de qué es lo que se debe hacer. Por
   ejemplo, si se pide un algoritmo de complejidad `O(n log n)`, es probable que se deba usar
   un algoritmo de ordenamiento o alguna variante de dividir y conquistar.

3. Si tienen dudas sobre el enunciado, no duden en preguntar. Es preferible a que se hagan
   suposiciones incorrectas.

4. Se recomienda plantearse cómo realizar ciertas operaciones de forma más rápida.

5. Generar testcases de forma propia puede ser una buena forma de entender el problema. Esto
   además les ayudará a saber cómo escala su algoritmo con respecto al tamaño de la entrada.

6. Un algoritmo recursivo puede ser más fácil de entender, pero en general es menos eficiente
   que su versión iterativa. Siempre que sea posible, se recomienda implementar la versión
   iterativa.

7. Siempre que sea posible, usar funciones y estructuras de datos que ya están implementadas
   en Python, ya que estas suelen ser más eficientes que las implementaciones propias. Por
   ejemplo, si necesitan ordenar una lista, usar el método `sort` (o la función `sorted`) en
   vez de implementar su propio algoritmo de ordenamiento, o si necesitan realizar una cola,
   usar `collections.deque`.
