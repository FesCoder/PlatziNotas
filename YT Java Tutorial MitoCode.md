![MitoCode_logo](src/Tutorial_Java_MitoCode/MitoCode_logo.png)
# Java Tutorial MitoCode
Índice
-
- [Tutorial Java SE]
    - [36- Colecciones + iterador](#36-colecciones--iterador)
    - [37- ArrayList](#37--arraylist)
    - [38- LinkedList](#38--linkedlist-o-listas-enlazadas)
    - [39- HashMap](#39--hashmap)
    - [40- HashSet](#40--hashset)
    - [41- Exceptions](#41--exceptions)
    - [42- Jerarquía de Exceptions](#42--jerarquía-de-exceptions)
    - [43- Lanzar Exceptions - Throw y Throws](#43--lanzar-exceptions---throw-ythrows)
    - [44- Exceptions personalizadas](#44--exceptions-personalizadas)
    - [45- Files](#45--files)
    - [46 -Lectura de Archivos](#46--lectura-de-archivos)
    - [47- Escritura de Archivos]
    - [48- try with resources]
    - [49- Conexión a Base de Datos]
    - [50- Insercción a BD con parámetros]
    - [51- Listar de BD]
    - [52- Patrón DAO]
    - [53- Interfaces gráficas SWING]
    - [54- JPanel Swing]
    - [55- JButton Swing]
    - [56- Paleta Swing]
    - [57- Hilos]



    - [1- Paradigma Funcional](#paradigma-funcional)
    - [2- Lambda](#lambda)

---

## 36- Colecciones + iterador
Una coleccion de objetos es un objeto que se puede almacenar un número variable de elementos, siendo cada elemento otro objeto. Podriamos verlo como una caja que contiene mas cajas dentro.
Puede haber distintos tipos de colecciones de tamaño flexible, es decir que se pueden encoger o agrandar según las nececidades.

![36_Colecciones_e_iterador_01](src/Tutorial_Java_MitoCode/36_Colecciones_e_iterador_01.png)

Entonces teniendo esta imagen podemos decir que nosotros vamos a utilizar una Clase en particular que implementa una interfaz para poder empezar la agrupación de elementos.  
`List<String> lista = new ArrayList();`  
En esta linea de código podemos decir que declaramos el objeto llamado ***lista*** pertenece a la interfaz Lista de tipo String, y que a su vez estamos generando una instancia de la
clase ArrayList.

El Iterator instanciado es un objeto que nos permite recorrer una lista.  
`Iterator<String> iterator = lista.iterator();`  
y con este objeto podemos hacer lo siguiente:  
~~~
while(iterador.hasNext()){
    System.out.println(iterador.next());
}
~~~
Ambas hacen lo mismo, pero es mas práctico con un for para recorrer la lista, esto fue a modo de demostración.
~~~
for(String s : lista){
    System.out.println(s);
}
~~~
Esto es importante porque cuando trabajemos con BD, en muchas ocaciones vamos a requerir traer una lista, lo mas recomendable es traer esa lista en base a una coleccion de objetos y la
mejor manera de trabajar esta coleccion es por medio de listas.

---

## 37- ArrayList
ArrayList viene de la interfaz Lista, y ésta de Collection e Iterable (Se ve en la imagen de la clase anterior).  
Se explica que para mejorar el rendimiento del sistema, si se sabe la cantidad de espacio de memoria que se le puede asignar a la lista, es decir la cantidad de objetos que va a almacenar
conviene declararlo al instanciar el ArrayList y asi nos ahorramos tiempo y procesos a la hora de la ejecución.  
`List<Integer> lista = new ArrayList(10);`

Al utilizar listas tenemos a disposicion determinados métodos, por ejemplo el `get(int index)` que se le pasa una referencia del elemento que queremos.
- `add()` Para agregar a una coleccion
- `clear()` Limpiar todo el arreglo
- `contains()` Si se encuentra en el arreglo
- `isEmpty()` Para ver si esta vacio el array
- `iterator()` Recorrerlo como si fuera un iterador
- `size` Obtener el tamaño  
Y muchos más.

---

## 38- LinkedList o Listas enlazadas
Una lista enlazada tiene la particularidad de que sus elementos tienen una referencia con su próximo.  
![38_LinkedList_01](src/Tutorial_Java_MitoCode/38_LinkedList_01.png)

Y lo podemos declarar asi:  
`List lista = new LinkedList();`  
Tambien podriamos poner de que tipo es esa lista, pero al no declararlo podemos agregar objetos de varios tipos.  
`List<Integer> lista = new LinkedList();`  
Ó apoyandonos en la clase directamente:  
`LinkedList lista = new LinkedList();`

Veamos en que situaciónes es conveniente usar el LinkedList antes que un ArrayList  
Tiempos que tardan en ejecutar el agregado, lectura y eliminación de la lista.  
![38_LinkedList_02](src/Tutorial_Java_MitoCode/38_LinkedList_02.png)  
La diferencia sustancial es la obtencion del elemento de parte del ArrayList, porque? porque en LinkedList tenemos referencias uno con el otro, entonces cuando quiero obtener un elemento
en el ArrayList simplemente voy directo a él, mientras que el LinkedList tiene que recorrer toda la lista.  
Y en el agregado y eliminación es más rapida el LinkedList. Ahí sus diferencias y cuando conviene usar cada uno.

---

## 39- HashMap
Hashmap (Diccionario)  
Básicamente este tipo de dato nos va a permitir tener varios elementos pero a cada elemento le vamos a poder asociar una KEY.  
Declaración:  
`Map diccionario = new HashMap();`  
Ó mediante la Clase  
`HashMap diccionario = new HashMap();`

![39_HashMap_01](src/Tutorial_Java_MitoCode/39_HashMap_01.png)

Para agregar valores a nuestro diccionario en vez de utilizar como en el ArrayList el método `add()` lo hacemos con el método `put()` al cual le pasamos 2 argumentos, el KEY y el VALOR.  
Se pueden acceder a estos elementos usando la función `diccionario.get()` pasandole la KEY y nos devuelve el valor.  
Tambien podemos ver si existe una KEY o un VALOR en nuestro diccionario usando el método `containsKey()` ó `containsValue()`, devuelve un booleano.  
Y demas funciones que se pueden investigar.

Se usan mucho cuando se necesita pasar parametros a librerias para reportes, se usan el objeto que tenga la relación key-value.

---

## 40- HashSet
Se destaca por no tener un orden en la lista, siempre es aleatorio y no permite valores repetidos (si guardarlos pero no los devuelve al leer los elementos).

![40_HashSet_01](src/Tutorial_Java_MitoCode/40_HashSet_01.png)

![40_HashSet_02](src/Tutorial_Java_MitoCode/40_HashSet_02.png)

---

## 41- Exceptions
Una Exception notifica cuando hay algun error en el proceso.  
Para poder manejarlas utilizamos el try-catch-finally  
En este ejemplo se trata de divir un numero por cero y la exception es tratada y reportada.  
![41_Exceptions_01](src/Tutorial_Java_MitoCode/41_Exceptions_01.png)

---

## 42- Jerarquía de Exceptions
Cuando tratas de capturar una exception de nivel mayor no es necesario ni posible capturar otra de nivel inferior ya que la superior lo abarca y trata.  
Esta es la jerarquia y algunas exceptions.  
![42_jerarquia_exceptions_01](src/Tutorial_Java_MitoCode/42_jerarquia_exceptions_01.png)

![42_jerarquia_exceptions_02](src/Tutorial_Java_MitoCode/42_jerarquia_exceptions_02.png)

![42_jerarquia_exceptions_03](src/Tutorial_Java_MitoCode/42_jerarquia_exceptions_03.png)

---

## 43- Lanzar Exceptions - Throw yThrows
Aqui veremos como delegar una Exception a un método que está un nivel superior.  
Cuando desarrollamos aplicativos o sistemas se manejan las programaciones por capas, es decir que esta modularizado, y no necesariamente se manejan los errores donde se producen.  
A veces se tratan los errores en un nivel superior mucho mas arriba y donde la capa inferior unicamente tenga que informar que ha ocurrido un error.  

![43_Throw_Throws_01](src/Tutorial_Java_MitoCode/43_Throw_Throws_01.png)

`throw e` o `throw new NombreException` (para lanzar una nueva excepción)  
la **e** es la instancia de una clase que necesita throw, esta arroja la exception, el mensaje va a la capa superior (en este caso al método 2) y a su vez el método 3 tiene que
ser implementado con `throws Exception`, que **Exception** es la espificación de la clase, con este indicamos que puede transferir una exception.

---

## 44- Exceptions personalizadas
En algunos sistemas tenemos alguna lógica de negocio en particular en donde tenemos que manejar ciertas situaciones o errores, errores propios, personalizables y pueden servir para
ordenar nuestro código.

Por ejemplo vamos a verificar la edad que el usuario ingrese una edad valida y poder avisar al usuario caso que suceda una excepción. Es decir una edad muy grande 200 o 500 por ejemplo.

Entonces empezamos por crear una Clase EdadException.  
![44_Excepciones_personalizadas_01](src/Tutorial_Java_MitoCode/44_Excepciones_personalizadas_01.png)

Aquí la lógica del proceso y lanzamientos de exceptions de 2 maneras diferentes  
![44_Excepciones_personalizadas_02](src/Tutorial_Java_MitoCode/44_Excepciones_personalizadas_02.png)

![44_Excepciones_personalizadas_03](src/Tutorial_Java_MitoCode/44_Excepciones_personalizadas_03.png)

---

## 45- Files
Manejo de archivos desde Java.  
![45_Files_01](src/Tutorial_Java_MitoCode/45_Files_01.png)

Para empezar a manipular un archivo en Java es necesario hacer la referencia  
`File archivo = new File()` y se importa la libreria.  
Y le enviamos como parametro la ruta del archivo.

La clase tiene varios métodos para el manejo, `canRead()`, `canWrite()`, `canExecute()`, `delete()`, `exists()` y más.  
Es buena práctica siempre preguntar si existe o no dicho archivo.  
Con `mkdir()` podemos crear el directorio si no existe, con `mkdirs()` crea todos las carpetas en la ruta escrita que faltan.  
Con `renameTo(new File("Ruta de archivo"))` renombra al file con el contenido identico.  

![45_Files_02](src/Tutorial_Java_MitoCode/45_Files_02.png)

---

## 46- Lectura de archivos
Lectura de archivos planos, sin embargo hay que tener en cuenta que cuando hablamos de lectura de archivos, debemos pensar en que tipo de archivo es.  
Si estamos leyendo una imagen por ejemplo, es común que se encuentra guardada en una base de datos o en un repositorio en formato de Bytes.

![46- Lectura_de_archivos_01](src/Tutorial_Java_MitoCode/46- Lectura_de_archivos_01.png)

Y para este tipo de lectura seria mas conveniente una clase que sea de tipo `Stream`.  
Ahora nos vamos a trabajar con texto plano, un .txt, leer el contenido y mostrarlo en consola.  
Para esto necesito apoyarme en una clase llamada `FileReader()` que captura el archivo y en `BufferedReader()` para poder recorrer el contenido del archivo.  

![46- Lectura_de_archivos_02](src/Tutorial_Java_MitoCode/46- Lectura_de_archivos_02.png)

Tambien podriamos hacerlo con la clase `FileInputStream` y nos ayudamos con `Scanner` de la siguiente manera.  

![46- Lectura_de_archivos_03](src/Tutorial_Java_MitoCode/46- Lectura_de_archivos_03.png)

## 47- Escritura de archivos



















---

## Paradigma Funcional
El paradigma funcional es un subtipo del paradigma de programación Declarativa, basada en el uso de funciones matemáticas en contraste con la programación Imperativa.

Es decir, el principal fin de la programación Declarativa es tener una sintaxis de decirle al programa **que** es lo que necesitamos, sin embargo en contraste a la programación
Imperativa es decirle al lenguaje de programación **como** lo necesitamos.

Por ejemplo, para un lenguaje de programación Declarativa, nosotros le indicamos todas las sentencias a un determinado problema, por ejemplo el lenguaje **SQL**, si quiero todos los
usuarios que empiecen con la letra 'A', puedo decirlo asi:
~~~
SELECT * FROM users WHERE nombre like 'A%';
~~~
Decimos que es lo que queremos pero no como traerlo internamente al objetivo.

En contraparte, la Imperativa, si quiero lograr el mismo resultado, tendria que darle instrucción paso a paso para poder obtener el resultado.  
Por ejemplo, si me pidieran el promedio tendria que colocar un número, otro, otro y otro, sumarlos todos y dividirlos entre la cantidad de números.  
Es Imperativa porque le estoy indicando todos los pasos para lograr el objetivo.

![01_paradigma_funcional_01](src/Tutorial_Java_MitoCode/01_paradigma_funcional_01.png)

Entonces, volviendo al paradigma funcional, nos permite tener una semantica más limpia, acá entran las lambdas, y también se apoya en la recursión, porque básicamente para poder
abstraer muchas funcionalidades es necesario apoyarse en la reutilización de los mismos métodos.

Lenguajes de programación Declarativa (QUE) e Imperativa (COMO)  
![01_paradigma_funcional_02](src/Tutorial_Java_MitoCode/01_paradigma_funcional_02.png)

Java 8 se basa en un fuerte simbolo conocido como ***Lambdas***  
Las Lambdas basicamente son funciones anónimas, muy escenciales para entender la programación declarativa y presente la siguiente estructura `parámetros =>(operador) expresión`

![01_paradigma_funcional_03](src/Tutorial_Java_MitoCode/01_paradigma_funcional_03.png)

---

## Lambda
Una expresión Lambda es un método anónimo que no necesita de un identificador para ser invocado.