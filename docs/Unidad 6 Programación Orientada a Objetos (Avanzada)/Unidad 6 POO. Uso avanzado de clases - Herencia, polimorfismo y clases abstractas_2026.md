

# Unidad 6 - POO. Uso avanzado de clases: Herencia, polimorfismo y clases abstractas e interfaces

## 1. Introducción a la herencia

 Las **clases** representan un **tipo de dato complejo** y están compuestas por ***atributos*** y **métodos**. A diferencia de los arrays, las clases agrupan datos de diferentes  tipos que se denominan atributos y también métodos que nos permiten  trabajar con esos atributos.

Una **clase** por tanto, especifica las características comunes de un conjunto de **objetos**. Sin embargo, cuando queramos utilizar ese tipo de dato en nuestros  programas tendremos que crear un objeto. De esta forma los programas que escribas estarán formados por un conjunto de **clases** a partir de las cuales irás creando **objetos** que se interrelacionarán unos con otros. En muchos casos también se  habla de las clases como de las plantillas o planos a partir de los  cuales se crean los objetos.

Además de ellos, veremos que las clases nos van a permitir organizar  nuestros programas de otra manera. Es a lo que vamos a llamar  **programación orientada a objetos (POO)**. La **herencia** es uno de los conceptos fundamentales que introduce la programación orientada a objetos. La idea fundamental es permitir crear nuevas clases aprovechando las características (atributos y métodos) de otras clases ya creadas evitando así tener que volver a definir esas características (**reutilización**).

A una clase que hereda de otra se le llama **subclase o clase hija** y aquella de la que se hereda es conocida como **superclase o clase padre**. También se puede hablar en general de **clases descendientes** o **clases ascendientes**. Al heredar, la subclase adquiere todas las características (atributos y métodos) de su superclase, aunque algunas de ellas pueden ser sobrescritas o modificadas dentro de la subclase (a eso se le suele llamar **especialización**).

Una clase puede heredar de otra que a su vez ha podido heredar de una tercera y así sucesivamente. Esto significa que las clases van tomando todas las características de sus clases ascendientes (no sólo de su superclase o clase padre inmediata) a lo largo de toda la rama del árbol de la jerarquía de clases en la que se encuentre.

Imagina que quieres modelar el funcionamiento de algunos vehículos para trabajar con ellos en un programa de simulación. Lo primero que haces es pensar en una clase **Vehículo** que tendrá un conjunto de atributos (por ejemplo: posición actual, velocidad actual y velocidad máxima que puede alcanzar el vehículo) y de métodos (por ejemplo: detener, acelerar, frenar, establecerDirección, establecer sentido).

Dado que vas a trabajar con muchos tipos de vehículos, no tendrás suficiente con esas características, así que seguramente vas a necesitar nuevas clases que las incorporen. Pero las características básicas que has definido en la clase **Vehículo** van a ser compartidas por cualquier nuevo vehículo que vayas a modelar. Esto significa que si creas otra clase podrías heredar de **Vehículo** todas esos atributos y propiedades y tan solo tendrías que añadir las nuevas.

Si vas a trabajar con vehículos que se desplazan por tierra, agua y aire, tendrás que idear nuevas clases con características adicionales. Por ejemplo, podrías crear una clase **VehiculoTerrestre**, que herede las características de **Vehículo**, pero que también incorpore atributos como el número de ruedas o la altura de los bajos). A su vez, podría idearse una nueva clase que herede de **VehiculoTerrestre** y que incorpore nuevos atributos y métodos como, por ejemplo, una clase **Coche**. Y así sucesivamente con toda la jerarquía de clases heredadas que consideres oportunas para representar lo mejor posible el entorno y la información sobre la que van a trabajar tus programas.os a utilizar los mismos  elementos que hemos utilizado hasta ahora pero organizados en base a  clases.

![CapturaTutorialHerenciaYPolimorfismo1_0](img/CapturaTutorialHerenciaYPolimorfismo1_0.png)

### 1.1 Creación y utilización de clases heredadas

¿Cómo se indica en Java que una clase hereda de otra? Para indicar que una clase hereda de otra es necesario utilizar la palabra reservada `extends` junto con el nombre de la clase de la que se quieren heredar sus características:

```java
class <NombreClase> extends <nombreSuperClase> {
...
} 
```

En el ejemplo anterior de los vehículos, la clase **VehiculoTerrestre** podría quedar así al ser declarada:



```java
class VehiculoTerrestre extends Vehículo {
...
} 
```



Y en el caso de la clase **Coche**:



```java
java
class Coche extends VehículoTerrestre {
...
}
```



En unidades posteriores estudiarás detalladamente cómo crear una **jerarquía de clases** y qué relación existe entre la herencia y los distintos modificadores de clases, atributos y métodos. Por ahora es suficiente con que entiendas el concepto de herencia y sepas reconocer cuándo una clase hereda de otra (uso de la palabra reservada `extends`).

![PROG06_CONT_R61_Object](img/PROG06_CONT_R61_Object.png)

Puedes comprobar que en las bibliotecas proporcionadas por Java aparecen jerarquías bastante complejas de clases heredadas en las cuales se han ido aprovechando cada uno de los miembros de una clase base para ir construyendo las distintas clases derivadas añadiendo (y a veces modificando) poco a poco nueva funcionalidad. Eso suele suceder en cualquier proyecto de software conforme se van a analizando, descomponiendo y modelando los datos con los que hay que trabajar. La idea es poder representar de una manera eficiente toda la información que es manipulada por el sistema que se desea automatizar. Una jerarquía de clases suele ser una buena forma de hacerlo.

En el caso de Java, cualquier clase con la que trabajes tendrá un ascendiente. Si en la declaración de clase no indicas la clase de la que se hereda (no se incluye un `extends`), el compilador considerará automáticamente que se hereda de la clase `Object`, que es la clase que se encuentra en el nivel superior de toda la jerarquía de clases en Java (y que es la única que no hereda de nadie).

También irás viendo al estudiar distintos componentes de las bibliotecas de Java (por ejemplo en el caso de las interfaces gráficas) que para poder crear objetos basados en las clases proporcionadas por esas bibliotecas tendrás que crear tus propias clases que hereden de algunas de esas clases. Para ellos tendrás que hacer uso de la palabra reservada `extends`.

**En Java todas las clases son descendientes (de manera explícita o implícita) de la clase `Object`.**

??? tip "Comparación entre lenguajes: Herencia"

    === "Java"
        ```java
        java class Vehiculo {} 
        class Coche extends Vehiculo {}
        ```
    === "Python"
        ```python
        class Vehiculo:
            pass
    
        class Coche(Vehiculo):
            pass
        ```
    === "Kotlin"
        ```kotlin
        open class Vehiculo
        class Coche : Vehiculo()
        ```







## 2. La Herencia

  Como ya has estudiado, la **herencia** es el mecanismo que permite definir una nueva clase a partir de otra, pudiendo añadir nuevas características, sin tener que volver a escribir todo el código de la clase base.

  ![PROG09_CONT_R20_JerarquiaSuperclaseSubclase](img/PROG09_CONT_R20_JerarquiaSuperclaseSubclase.1.png)


  La clase de la que se hereda suele ser llamada clase padre. A la clase que hereda se le suele llamar clase hija.

  Una clase derivada puede ser a su vez **clase padre** de otra que herede de ella y así sucesivamente dando lugar a una **jerarquía de clases**, excepto aquellas que estén en la parte de arriba de la jerarquía (sólo serán **clases padre**) o en la parte de abajo (sólo serán **clases hijas**).

  Una **clase hija** no tiene acceso a los miembros **privados** de su **clase padre**, tan solo a los **públicos** (como cualquier parte del código tendría) y los **protegidos** (a los que sólo tienen acceso las **clases derivadas** y las del mismo **paquete**). Aquellos miembros que sean privados en la clase base también habrán sido heredados, pero el acceso a ellos estará restringido al propio funcionamiento de la **superclase** y sólo se podrá acceder a ellos si la **superclase** ha dejado algún medio indirecto para hacerlo (por ejemplo a través de algún método).

  Todos los miembros de la **superclase**, tanto atributos como métodos, son heredados por la subclase. Algunos de estos miembros heredados podrán ser **redefinidos** o **sobrescritos** (**overriden**) y también podrán añadirse nuevos miembros. De alguna manera podría decirse que estás “ampliando” la **clase base** con características adicionales o modificando algunas de ellas (proceso de **especialización**).

  Una clase derivada extiende la funcionalidad de la clase base sin tener que volver a escribir el código de la clase base.

  La idea de la herencia no es complicar los programas, sino todo lo contrario: **simplificarlos al máximo**. Procurar que haya que escribir la menor cantidad posible de código repetitivo e intentar facilitar en lo posible la realización de cambios (bien para corregir errores bien para incrementar la funcionalidad).

### 2.1 Sintaxis de la herencia

  En Java la **herencia** se indica mediante la palabra reservada **`extends`**:

  ```java
  [modificador] class ClasePadre {
      …
  }
  
  [modificador] class ClaseHija extends ClasePadre {
      …
  }
  ```

  

  Imagina que tienes una clase **Persona** que contiene atributos como **nombre**, **apellidos** y **fecha de nacimiento**:

  

  ```java
  public class Persona {
       String nombre;
       String apellidos;
       LocalDate fechaNacim;
       …
  }
  ```
  ![PROG09_CONT_R21_ClasePersona](img/PROG09_CONT_R21_ClasePersona.png)

  Es posible que, más adelante, necesites una clase **Alumno** que compartirá esos atributos (dado que todo alumno es una persona, pero con algunas características específicas que lo **especializan**). En tal caso tendrías la posibilidad de crear una clase **Alumno** que repitiera todos esos atributos o bien **heredar** de la clase **Persona**:

  

  ```java
  public class Alumno extends Persona {
       String grupo;
       double notaMedia; 
       …
  }
  ```

  



![PROG09_CONT_R22_ClaseAlumno](img/PROG09_CONT_R22_ClaseAlumno.png)

  A partir de ahora, un objeto de la clase **`Alumno`** contendrá los atributos **`grupo`** y **`notaMedia`** (propios de la clase **`Alumno`**), pero también **`nombre`**, **`apellidos`** y **`fechaNacim`** (propios de su **clase base** **`Persona`** y que por tanto ha heredado).

#### Ejercicio 1

  **Imagina que también necesitas una clase** **Profesor, que contará con atributos como** **nombre,** **apellidos,** **fecha de nacimiento,** **salario y** **especialidad. ¿Cómo crearías esa nueva clase y qué atributos le añadirías?**

  

  

### 2.2 Acceso a miembros heredados

Como ya has visto anteriormente, no es posible acceder a miembros **privados** de una superclase. Para poder acceder a ellos podrías pensar en hacerlos **públicos**, pero entonces estarías dando la opción de acceder a ellos a cualquier objeto externo y es probable que tampoco sea eso lo deseable. Para ello se inventó el modificador **`protected`** (**protegido**) que permite el **acceso desde clases heredadas**, pero no desde fuera de las clases (estrictamente hablando, desde fuera del **paquete**), que serían como miembros **privados**.

En la unidad dedicada a la utilización de clases ya estudiaste los posibles modificadores de acceso que podía tener un miembro: **sin modificador** (acceso **de paquete**), **público**, **privado** o **protegido**. Aquí tienes de nuevo el resumen:

**Cuadro de niveles accesibilidad a los atributos de una clase**

|                               | **Misma clase** | **Subclase** | **Mismo paquete** | **Otro paquete** |
| :---------------------------- | :-------------- | :----------- | :---------------- | :--------------- |
| **Sin modificador (paquete)** | X               |              | X                 |                  |
| **public**                    | X               | X            | X                 | X                |
| **private**                   | X               |              |                   |                  |
| **protected**                 | X               | X            | X                 |                  |

Si en el ejemplo anterior de la clase **`Persona`** se hubieran definido sus atributos como **`private`**:Si en el ejemplo anterior de la clase Persona se hubieran definido sus atributos como private:

```java
public class Persona {
     private String nombre;
     private String apellidos;
     …
}
```


![PROG09_CONT_R23_JerarquiaPersonaProfesorAlumno](img/PROG09_CONT_R23_JerarquiaPersonaProfesorAlumno.png)

Al definir la clase **`Alumno`** como heredera de **`Persona`**, no habrías tenido acceso a esos atributos, pudiendo ocasionar un grave problema de operatividad al intentar manipular esa información. Por tanto, en estos casos lo más recomendable habría sido declarar esos atributos como **`protected`** o bien sin modificador (para que también tengan acceso a ellos otras clases del mismo paquete, si es que se considera oportuno):

```java
public class Persona {
     protected String nombre;
     protected String apellidos;
     …
}
```

??? note "Comparación entre lenguajes: Acceso protegido"

    Sólo en aquellos casos en los que se desea explícitamente que un miembro de una clase no pueda ser accesible desde una clase derivada debería utilizarse el modificador **`private`**. En el resto de casos es recomendable utilizar **`protected`**, o bien no indicar modificador (acceso a nivel de **paquete**).



#### Ejercicio 2

**Rescribe las clases** **`Alumno` y** **`Profesor` utilizando el modificador** **`protected` para sus atributos del mismo modo que se ha hecho para su superclase** **`Persona`**

!!! tip "Comparación entre lenguajes: Acceso protegido"

    === "Java"
    
        ```java
        public class Persona { 
    
        protected String nombre; 
    
        } 
    
        class Alumno extends Persona {
    
        // acceso a nombre permitido
    
        }
        ```
    
    === "Python"
        ```python
        class Persona:
            def __init__(self):
                self._nombre = ""  # Convención para "protegido"
                class Alumno(Persona):
            def __init__(self):
                super().__init__()
                # acceso a self._nombre permitido
        
        ```
    
    === "Kotlin"
    
        ```kotlin
            open class Persona {
                protected var nombre: String = ""
            }
            class Alumno : Persona() {
                // acceso a nombre permitido
            }
        ```
### 2.3 Utilización de miembros heredados (I). Atributos

Los **atributos heredados** por una clase son, a efectos prácticos, iguales que aquellos que sean definidos específicamente en la nueva **clase derivada**.

En el ejemplo anterior la clase **`Persona`** disponía de tres atributos y la clase **`Alumno`**, que heredaba de ella, añadía dos atributos más. Desde un punto de vista funcional podrías considerar que la clase **`Alumno`** tiene cinco atributos: tres por ser **`Persona`** (**nombre**, **apellidos**, **fecha de nacimiento**) y otros dos más por ser **`Alumno`**(**grupo** y **nota media**).

#### Ejercicio 3

**Dadas las clases** **`Alumno` y** **`Profesor` que has utilizado anteriormente, implementa métodos** **get y** **set en las clases** **`Alumno` y** **`Profesor` para trabajar con sus cinco atributos (tres heredados más dos específicos).**

#### 2.3.1 Utilización de miembros heredados (II). Métodos

Del mismo modo que se heredan los **atributos**, también se heredan los **métodos**, convirtiéndose a partir de ese momento en otros **métodos** más de la **clase derivada**, junto a los que hayan sido definidos específicamente.

En el ejemplo de la clase **`Persona`**, si dispusiéramos de métodos **get** y **set** para cada uno de sus tres atributos (**`nombre`**, **`apellidos`**, **`fechaNacim`**), tendrías seis métodos que podrían ser heredados por sus **clases derivadas**. Podrías decir entonces que la clase **`Alumno`**, derivada de **`Persona`**, tiene diez métodos:

- Seis por ser **`Persona`** (**`getNombre`**, **`getApellidos`**, **`getFechaNacim`**, **`setNombre`**, **`setApellidos`**, **`setFechaNacim`**).
- Oros cuatro más por ser **`Alumno`** (**`getGrupo`**, **`setGrupo`**, **`getNotaMedia`**, **`setNotaMedia`**).

Sin embargo, sólo tendrías que definir esos cuatro últimos (los **específicos**) pues los **genéricos** ya los has heredado de la **superclase**.

#### Ejercicio 4

**Dadas las clases** **`Persona`,** **`Alumno` y** **`Profesor` que has utilizado anteriormente, implementa métodos** **get y** **set en la clase** **`Persona` para trabajar con sus tres atributos y en las clases** **`Alumno` y** **`Profesor` para manipular sus cinco atributos (tres heredados más dos específicos), teniendo en cuenta que los métodos que ya hayas definido para** **`Persona` van a ser heredados en** **`Alumno` y en** **`Profesor`.**

### 2.4 Redefinición de métodos heredados

Una clase puede **redefinir** algunos de los métodos que ha heredado de su **clase base**. En tal caso, el nuevo método (**especializado**) sustituye al **heredado**. Este procedimiento también es conocido como de **sobrescritura de métodos**.

![descarga (1)](img/descarga (1).webp)

En cualquier caso, aunque un método sea **sobrescrito** o **redefinido**, aún es posible acceder a él a través de la referencia **`super`**, aunque sólo se podrá acceder a métodos de la **clase padre** y no a métodos de clases superiores en la **jerarquía de herencia**.

Los **métodos redefinidos** pueden **ampliar su accesibilidad** con respecto a la que ofrezca el método original de la **superclase**, pero **nunca restringirla**. Por ejemplo, si un método es declarado como **`protected`** o **de paquete** en la clase base, podría ser redefinido como **`public`** en una clase derivada.

!!! note ""
    Los **métodos estáticos** o de clase no pueden ser sobrescritos. Los originales de la clase base permanecen inalterables a través de toda la **jerarquía de herencia**.

En el ejemplo de la clase **`Alumno`**, podrían redefinirse algunos de los métodos heredados. Por ejemplo, imagina que el método **`getApellidos`** devuelva la cadena "Alumno:" junto con los apellidos del alumno. En tal caso habría que rescribir ese método para realizara esa modificación:


=== "Java"
    ```java
    public String getApellidos() {
        return "Alumno: " + apellidos;
    }
    ```
=== "Python"

    ```python
    class Alumno(Persona):
        def __init__(self, nombre, apellidos, fecha_nacim, grupo, nota_media):
            super().__init__(nombre, apellidos, fecha_nacim)
            self.grupo = grupo
            self.nota_media = nota_media
    
    ```
=== "Kotlin"

    ```kotlin
    class Alumno(nombre: String, apellidos: String, fechaNacim: LocalDate, val grupo: String, val notaMedia: Double) :
            Persona(nombre, apellidos, fechaNacim)
    ```

Cuando sobrescribas un método heredado en Java puedes incluir la **anotación** **`@Override`**. Esto indicará al compilador que tu intención es **sobrescribir el método de la clase padre**. De este modo, si te equivocas (por ejemplo, al escribir el nombre del método) y no lo estás realmente sobrescribiendo, el compilador producirá un error y así podrás darte cuenta del fallo. En cualquier caso, no es necesario indicar **`@Override`**, pero puede resultar de ayuda a la hora de localizar este tipo de errores (crees que has sobrescrito un **método heredado** y al confundirte en una letra estás realmente creando un nuevo método diferente). En el caso del ejemplo anterior quedaría:

=== "Java"
    ```java
    @Override
    public String getApellidos()
    ```



#### Ejercicio 5

**Dadas las clases** **`Persona`,** **`Alumno` y** **`Profesor` que has utilizado anteriormente, redefine el método** **`getNombre` para que devuelva la cadena** **“`Alumno:`“, junto con el nombre del alumno, si se trata de un objeto de la clase** **`Alumno` o bien** **“`Profesor` “, junto con el nombre del profesor, si se trata de un objeto de la clase** **`Profesor`.**

!!! tip "Comparación entre lenguajes: Sobrescritura de métodos"
    === "Java"

        ```java
        @Override
        public String getNombre()
        { 
        return "Alumno: " + nombre; 
        }
        ```
    
    === "Python"
    
        ```python
        def get_nombre(self):
            return f"Alumno: {self._nombre}"
        ```
    
    === "Kotlin"
    
        ```kotlin
        override fun getNombre(): String {
            return "Alumno: $nombre"
        }
        ```

### 2.5 Ampliación de métodos heredados

Hasta ahora, has visto que para **redefinir** o **sustituir** un **método** de una **superclase** es suficiente con crear otro método en la **subclase** que tenga el mismo nombre que el método que se desea **sobrescribir**. Pero, en otras ocasiones, puede que lo que necesites no sea sustituir completamente el comportamiento del método de la superclase, sino simplemente **ampliarlo**.

Para poder hacer esto necesitas poder **preservar el comportamiento antiguo** (el de la **superclase**) y **añadir el nuevo** (el de la **subclase**). Para ello, puedes invocar desde el método “**ampliador**” de la **clase derivada** al método “**ampliado**” de la clase superior (teniendo ambos métodos el mismo nombre). ¿Cómo se puede conseguir eso? Puedes hacerlo mediante el uso de la referencia **`super`**.

La palabra reservada **`super`** es una referencia a la **clase padre** de la clase en la que te encuentres en cada momento (es algo similar a **`this`**, que representaba una referencia a la **clase actual**). De esta manera, podrías invocar a cualquier método de tu **superclase** (si es que se tiene acceso a él).

Por ejemplo, imagina que la clase **`Persona`** dispone de un método que permite mostrar el contenido de algunos datos personales de los objetos de este tipo (**nombre**, **apellidos**, etc.). Por otro lado, la clase **`Alumno`** también necesita un método similar, pero que muestre también su información especializada (**grupo**, **nota media**, etc.). ¿Cómo podrías aprovechar el método de la **superclase** para no tener que volver a escribir su contenido en la subclase?

Podría hacerse de una manera tan sencilla como la siguiente:

=== "Java"

    ```java
    public void mostrar() {
        super.mostrar();     // Llamada al método “mostrar” de la superclase
        // A continuación mostramos la información “especializada” de esta subclase
        System.out.printf("Grupo: %s\n", this.grupo);
        System.out.printf("Nota media: %5.2f\n", this.notaMedia); 
    }
    ```

Este tipo de **ampliaciones de métodos** resultan especialmente útiles por ejemplo en el caso de los **constructores**, donde se podría ir llamando a los **constructores** de cada **superclase** encadenadamente hasta el **constructor** de la clase en la **cúspide de la jerarquía** (el **constructor** de la clase **`Object`**).

#### Ejercicio 6

**Dadas las clases** **`Persona`,** **`Alumno` y** **`Profesor`, define un método** **toString para la clase** **`Persona`, que devuelva una cadena de caracteres con el contenido de los atributos (datos personales) de un objeto de la clase** **`Persona`. A continuación, define sendos métodos** **toString especializados para las clases** **`Alumno` y** **`Profesor` que “amplíen” la funcionalidad del método** **original de la clase** **`Persona`.**





!!! tip "Comparación entre lenguajes: Llamada al método de la superclase"
    === "Java"

        ```java
        public void mostrar() { 
        super.mostrar(); 
        }
        ```
    
    === "Python"
    
        ```python
        def mostrar(self):
            super().mostrar()
        ```
    
    === "Kotlin"
    
        ```kotlin
        override fun mostrar() {
            super.mostrar()
            }
        ```

### 2.6 Constructores y herencia

Recuerda que cuando estudiaste los **constructores** viste que un **constructor** de una clase puede llamar a otro **constructor** de la misma clase, previamente definido, a través de la referencia **`this`**. En estos casos, la utilización de **`this`** sólo podía hacerse en la primera línea de código del **constructor**.

Como ya has visto, un **constructor** de una **clase derivada** puede hacer algo parecido para llamar al **constructor** de su **clase base** mediante el uso de la palabra **`super`**. De esta manera, el **constructor** de una **clase derivada** puede llamar primero al **constructor** de su **superclase** para que inicialice los **atributos heredados** y posteriormente se inicializarán los **atributos específicos** de la clase: los no heredados. Nuevamente, esta llamada también **debe ser la primera sentencia de un constructor** (con la única excepción de que exista una llamada a otro constructor de la clase mediante **`this`**).

Si no se incluye una llamada a **`super()`** dentro del **constructor**, el compilador incluye automáticamente una llamada al constructor por defecto de **clase base** (llamada a `super()`). Esto da lugar a una **llamada en cadena de constructores de superclase** hasta llegar a la clase más alta de la jerarquía (que en Java es la clase **`Object`**).

En el caso del **constructor por defecto** (el que crea el compilador si el programador no ha escrito ninguno), el compilador añade lo primero de todo, antes de la inicialización de los atributos a sus valores por defecto, una llamada al constructor de la **clase base** mediante la referencia **`super`**.

A la hora de destruir un objeto (método **`finalize`**) es importante llamar a los finalizadores en el **orden inverso** a como fueron llamados los constructores (p**rimero se liberan los recursos de la clase derivada y después los de la clase base** mediante la llamada **`super.finalize()`**).

Si la clase **`Persona`** tuviera un constructor de este tipo:


=== "Java"
    ```java
    public Persona(String nombre, String apellidos, LocalDate fechaNacim) {
        this.nombe = nombre;
        this.apellidos = apellidos;
        this.fechaNacim = LocalDate;
    }
    ```

Podrías llamarlo desde un constructor de una clase derivada (por ejemplo **`Alumno`**) de la siguiente forma:

=== "Java"
    ```java
    public Alumno(String nombre, String apellidos, LocalDate fechaNacim, String grupo, double notaMedia) {
        super(nombre, apellidos, fechaNacim);
        this.grupo = grupo;
        this.notaMedia = notaMedia;
    }
    ```

En realidad se trata de otro recurso más para optimizar la **reutilización de código**, en este caso el del **constructor**, que aunque no es heredado, sí puedes invocarlo para no tener que rescribirlo.

#### Ejercicio 7

Escribe un constructor para la clase **Profesor** que realice una llamada al constructor de su clase base para inicializar sus atributos heredados. Los atributos específicos (no heredados) sí deberán ser inicializados en el propio constructor de la clase **Profesor**.

!!! tip "Comparación entre lenguajes: Constructores y herencia"

=== "Java"

    ```java
    public Alumno(String nombre, String apellidos, LocalDate fechaNacim, String grupo, double notaMedia) 
    { 
        super(nombre, apellidos, fechaNacim); 
        this.grupo = grupo; 
        this.notaMedia = notaMedia; 
    }
    ```



### 2.7 Herencia múltiple

En determinados casos podrías considerar la posibilidad de que se necesite **heredar de más de una clase**, para así disponer de los miembros de dos (o más) clases disjuntas (que no derivan una de la otra). La **herencia múltiple** permite hacer eso: recoger las distintas características (atributos y métodos) de clases diferentes formando una nueva clase derivada de varias clases base.

El problema en estos casos es la posibilidad que existe de que se produzcan ambigüedades, así, si tuviéramos miembros con el mismo identificador en clases base diferentes, en tal caso, ¿qué miembro se hereda? Para evitar esto, los compiladores suelen solicitar que ante casos de ambigüedad, se especifique de manera explícita la clase de la cual se quiere utilizar un determinado miembro que pueda ser ambiguo.

Ahora bien, la posibilidad de **herencia múltiple** no está disponible en todos los lenguajes orientados a objetos, ¿lo estará en Java? La respuesta es negativa.





!!! tip "Comparación entre lenguajes: Herencia múltiple"

    === "Java"
    
        ```java
        // No permitido
        // class Coche extends Vehiculo, Motor { } 
        // Se usan interfaces para simular herencia múltiple


        ```


    === "Python"
    
        ```python
        # Permitido
        class Coche(Vehiculo, Motor):
            pass
        ```
    
    === "Kotlin"
    
        ```kotlin
        // No permitido directamente
        // class Coche : Vehiculo(), Motor()
        // Se usan interfaces para simular herencia múltiple
        ```

 




## 3. Clases abstractas

En determinadas ocasiones, es posible que necesites definir una clase que represente un concepto lo suficientemente abstracto como para que nunca vayan a existir instancias de ella (objetos). ¿Tendría eso sentido? ¿Qué utilidad podría tener?

Imagina una aplicación para un **centro educativo** que utilice las clases de ejemplo **`Alumno`** y **`Profesor`**, ambas subclases de **Persona**. Es más que probable que esa aplicación nunca llegue a necesitar objetos de la clase **`Persona`**, pues serían demasiado genéricos como para poder ser utilizados (no contendrían suficiente información específica). Podrías llegar entonces a la conclusión de que la clase **Persona** ha resultado de utilidad como **clase base** para construir otras clases que hereden de ella, pero no como una **clase instanciable** de la cual vayan a existir objetos. A este tipo de clases se les llama **clases abstractas**.

📢En algunos casos puede resultar útil disponer de clases que nunca serán instanciadas, sino que proporcionan un marco o modelo a seguir por sus clases derivadas dentro de una jerarquía de **herencia**. Son las **clases abstractas**.

La posibilidad de declarar **clases abstractas** es una de las características más útiles de los **lenguajes orientados a objetos**, pues permiten dar unas líneas generales de cómo es una clase sin tener que implementar todos sus métodos o implementando solamente algunos de ellos. Esto resulta especialmente útil cuando las distintas **clases derivadas** deban proporcionar los mismos métodos indicados en la clase **base abstracta**, pero su i**mplementación sea específica** para cada **subclase**.

Imagina que estás trabajando en un entorno de **manipulación de objetos gráficos** y necesitas trabajar con **líneas**, **círculos**, **rectángulos**, etc. Estos objetos tendrán en común algunos atributos que representen su estado (**ubicación**, **color del contorno**, **color de relleno**, etc.) y algunos métodos que modelen su comportamiento (**dibujar**, **rellenar con un color**, **escalar**, **desplazar**, **rotar**, etc.). Algunos de ellos serán comunes para todos ellos (por ejemplo la **ubicación** o el **desplazamiento**) y sin embargo otros (como por ejemplo **dibujar**) necesitarán una implementación específica dependiendo del tipo de objeto.

Pero, en cualquier caso, todos ellos necesitan esos métodos (tanto un **círculo** como un **rectángulo** necesitan el método **dibujar**, aunque se lleven a cabo de manera diferente). En este caso resultaría muy útil disponer de una **clase abstracta** **objeto gráfico** donde se definirían las **líneas generales** (algunos atributos concretos comunes, algunos métodos concretos comunes implementados y algunos métodos genéricos comunes sin implementar) de un objeto gráfico y más adelante, según se vayan definiendo **clases especializadas** (**líneas**, **círculos**, **rectángulos**), se irán concretando en cada **subclase** aquellos métodos que se dejaron sin implementar en **la clase abstracta**.





### 3.1. Declaración de una clase abstracta

Ya has visto que una **clase abstracta** es una clase que no se puede instanciar, es decir, que no se pueden crear objetos a partir de ella. La idea es permitir que otras clases deriven de ella, proporcionando un **modelo genérico** y algunos **métodos de utilidad general**.



Las **clases abstractas** se declaran mediante el modificador **`abstract`**:

=== "Java"

    ```java
    [modificador_acceso] abstract class nombreClase  [herencia] [interfaces] {
    
    }
    ```

Una clase puede contener en su interior métodos declarados como **`abstract`** (métodos para los cuales sólo se indica la cabecera, pero no se proporciona su implementación). En tal caso, la clase tendrá que ser necesariamente también **`abstract`**. Esos métodos tendrán que ser posteriormente implementados en sus **clases derivadas**.

Por otro lado, una clase también puede contener **métodos totalmente implementados** (**no abstractos**), los cuales serán heredados por sus **clases derivadas** y podrán ser utilizados sin necesidad de definirlos (pues ya están implementados).

Cuando trabajes con **clases abstractas** debes tener en cuenta:

- Una **clase abstracta** sólo puede usarse para crear nuevas clases derivadas. No se puede hacer un **new** de una **clase abstracta**. Se produciría un **error de compilación**.
- Una **clase abstracta** puede contener **métodos totalmente definidos** (**no abstractos**) y **métodos sin definir** (**métodos abstractos**).



#### Ejercicio 8

Basándote en la jerarquía de clases de ejemplo (`Persona`, `Alumno`, `Profesor`), que ya has utilizado en otras ocasiones, **modifica lo que consideres oportuno para que `Persona` sea, a partir de ahora, una clase abstracta (no instanciable) y las otras dos clases sigan siendo clases derivadas de ella, pero sí instanciables**.

!!! tip "Clases abstractas"

    === "Java"
    
        ```java
        java public abstract class Persona { // ... }
        ```
    
    === "Python"
    
        ```python
        from abc import ABC, abstractmethod
        class Persona(ABC):
        @abstractmethod
        def mostrar(self):
            pass
        ```
    
    === "Kotlin"
    
        ```kotlin
        abstract class Persona {
            abstract fun mostrar()
            }
        ```

### 3.2. Métodos abstractos

Un **método abstracto** es un método cuya implementación no se define, sino que se declara únicamente su **interfaz** (cabecera) para que su cuerpo sea implementado más adelante en una **clase derivada**.


![PROG09_CONT_R39_Abstracto2](img/PROG09_CONT_R39_Abstracto2.jpg)

Un método se declara como abstracto mediante el uso del modificador **abstract** (como en las **clases abstractas**):



```java
[modificador_acceso] abstract  <tipo> <nombreMetodo> ([parámetros]) [excepciones]; 
```



Estos métodos tendrán que ser <u>**obligatoriamente redefinidos** (en realidad “definidos”, pues aún no tienen contenido) en las **clases derivadas**. Si en una **clase derivada** se deja algún **método abstracto sin implementar**, esa **clase derivada** será también una **clase abstracta**</u>.

📣 Cuando una clase contiene un **método abstracto** tiene que declararse como **abstracta** obligatoriamente

Imagina que tienes una clase **Empleado** genérica para diversos tipos de empleado y tres **clases derivadas**: **EmpleadoFijo** (tiene un salario fijo más ciertos complementos), **EmpleadoTemporal** (salario fijo más otros complementos diferentes) y **EmpleadoComercial** (una parte de salario fijo y unas comisiones por cada operación). La clase **Empleado** podría contener un **método abstracto** **calcularNomina**, pues sabes que ese método será necesario para cualquier tipo de empleado (todo empleado cobra una nómina). Sin embargo el cálculo en sí de la nómina será diferente si se trata de un empleado fijo, un empleado temporal o un empleado comercial, y será dentro de las clases especializadas de **Empleado** (**EmpleadoFijo¸** **EmpleadoTemporal**, **EmpleadoComercial**) donde se implementen de manera específica el cálculo de las mismas.



Debes tener en cuenta al trabajar con métodos abstractos:

- Un **método abstracto** implica que la clase a la que pertenece tiene que ser **abstracta**, pero eso no significa que todos los métodos de esa clase tengan que ser abstractos.
- Un **método abstracto** no puede ser **privado** (no se podría implementar, dado que las **clases derivadas** no tendrían acceso a él).
- Los **métodos abstractos** no pueden ser **estáticos**, pues los **métodos estáticos** no pueden ser redefinidos (y los **métodos abstractos** necesitan ser redefinidos).

#### Ejercicio 9

**Basándote en la jerarquía de clases `Persona`, `Alumno`, `Profesor`, crea un método abstracto llamado mostrar para la clase `Persona`. Dependiendo del tipo de persona (alumno o profesor) el método mostrar tendrá que mostrar unos u otros datos personales (habrá que hacer implementaciones específicas en cada clase derivada).**

**Una vez hecho esto, implementa completamente las tres clases (con todos sus atributos y métodos) y utilízalas en un pequeño programa de ejemplo que cree un objeto de tipo `Alumno` y otro de tipo `Profesor`, los rellene con información y muestre esa información en la pantalla a través del método `mostrar`.**



### 3.3. Clases y métodos finales

En unidades anteriores has visto el modificador **`final`**, aunque sólo lo has utilizado por ahora para **atributos** y **variables** (por ejemplo para declarar **atributos constantes**, que una vez que toman un valor ya no pueden ser modificados). Pero este modificador también puede ser utilizado con clases y con métodos (con un comportamiento que no es exactamente igual, aunque puede encontrarse cierta analogía: no se permite heredar o no se permite redefinir).



**Una clase declarada como `final` no puede ser heredada**, es decir, **no puede tener clases derivadas**. La jerarquía de clases a la que pertenece acaba en ella (no tendrá clases hijas):

```java
[modificador_acceso] final class nombreClase  [herencia] [interfaces]
```

Un método también puede ser declarado como final, en tal caso, ese método no podrá ser redefinido en una clase derivada:

```java
[modificador_acceso] final <tipo> <nombreMetodo> ([parámetros]) [excepciones]
```

📣 Si intentas redefinir un método **`final`** en una subclase se producirá un **error de compilación**.

Además de en la declaración de atributos, clases y métodos, el modificador **`final`** también podría aparecer acompañando a un método de un parámetro. En tal caso no se podrá modificar el valor del parámetro dentro del código del método. Por ejemplo: **`public final metodoEscribir (int par1, final int par2)`**.



!!! info "Debes conocer"

    Dada la gran cantidad de contextos diferentes en los que se puede encontrar el modificador **`final`**, vale la pena que hagas un repaso de todos los lugares donde puede aparecer y cuál sería su función en cada uno.

!!! tip "Comparación entre lenguajes: Clases y métodos finales/no heredables"
    === "Java"

        ```java
        public final class ClaseFinal { } public final void metodoFinal() { }
        ```
    
    === "Python"
    
        ```python
        No hay equivalente directo para clases
            # Se puede usar convenciones o decoradores personalizados
        ```
    
    === "Kotlin"
    
        ```kotlin
        final class ClaseFinal { }
        // En Kotlin los métodos son final por defecto
        // Para permitir sobrescritura se usa 'open'
        open fun metodoSobrescribible() { }
        ```





## 4. Interfaces

Has visto cómo la **herencia** permite definir **especializaciones** (o **extensiones**) de una **clase base** que ya existe sin tener que volver a repetir de todo el código de ésta. Este mecanismo da la oportunidad de que la nueva **clase especializada** (o **extendida**) disponga de toda la **interfaz** que tiene su clase base.

También has estudiado cómo los **métodos abstractos** permiten establecer una **interfaz** para marcar las **líneas generales de un comportamiento común de** **superclase** que deberían compartir de todas las **subclases**.


![PROG09_CONT_R45_Piramide_feudal](img/PROG09_CONT_R45_Piramide_feudal.jpg)

Si llevamos al límente esta idea de **interfaz**, podrías llegar a tener una **clase abstracta** donde todos sus métodos fueran abstractos. De este modo estarías dando únicamente el **marco de comportamiento**, sin ningún método implementado, de las posibles **subclases** que heredarán de esa **clase abstracta**. La idea de una **interfaz** (o **interface**) es precisamente ésa: **disponer de un mecanismo que permita especificar cuál debe ser el comportamiento que deben tener todos los objetos que formen parte de una determinada clasificación** (no necesariamente jerárquica).

Una **interfaz** consiste principalmente en una lista de declaraciones de métodos sin implementar, que caracterizan un determinado comportamiento. Si se desea que una clase tenga ese comportamiento, tendrá que implementar esos métodos establecidos en la **interfaz**. En este caso no se trata de una relación de **herencia** (la clase **A** es una especialización de la clase **B**, o la subclase **A** es del tipo de la superclase **B**), sino más bien una relación "de implementación de comportamientos" (la clase **A** implementa los métodos establecidos en la **interfaz** **B**, o los comportamientos indicados por **B** son llevados a cabo por **A**; pero no que **A** sea de clase **B**).

Imagina que estás diseñando una aplicación que trabaja con clases que representan distintos tipos de animales. Algunas de las acciones que quieres que lleven a cabo están relacionadas con el hecho de que algunos animales sean **depredadores** (por ejemplo: **observar** una **presa** , **perseguirla** , **comérsela** , etc.) o sean **presas** ( **observar** , **huir** , **esconderse** , etc.). Si creas la clase **León** , esta clase podría implementar una interfaz **Depredador** , mientras que otras clases como **Gacela** implementarían las acciones de la interfaz **Presa** . Por otro lado, podrías tener también el caso de la clase **Rana** , que implementaría las acciones de la interfaz **Depredador** (pues es cazador de pequeños insectos), pero también la de **Presa** (pues puede ser cazado y necesita las acciones necesarias para protegerse).


![PROG09_CONT_R46_InterfacesDepredadorPresa](img/PROG09_CONT_R46_InterfacesDepredadorPresa.png)

### 4.1 Concepto de interfaz

Una **interfaz** en Java consiste esencialmente en una lista de declaraciones de métodos sin implementar, junto con un conjunto de constantes.

Estos métodos sin implementar indican un **comportamiento**, un tipo de conducta, aunque no especifican cómo será ese **comportamiento** (**implementación**), pues eso dependerá de las características específicas de cada clase que decida implementar esa **interfaz**. Podría decirse que una **interfaz** se encarga de establecer qué **comportamientos** hay que tener (qué **métodos**), pero no dice nada de cómo deben llevarse a cabo esos **comportamientos** (**implementación**). Se indica sólo la **forma**, no la **implementación**.


![PROG09_CONT_R48_Coche](img/PROG09_CONT_R48_Coche.jpg)

En cierto modo podrías imaginar el concepto de **interfaz** como un **guión** que dice: "éste es el protocolo de comunicación que deben presentar todas las clases que implementen esta interfaz". Se proporciona una lista de **métodos públicos** y, si quieres dotar a tu clase de esa **interfaz**, tendrás que definir todos y cada uno de esos **métodos públicos**.

En conclusión: **una interfaz se encarga de establecer unas líneas generales sobre los comportamientos (métodos) que deberían tener los objetos de toda clase que implemente esa interfaz, es decir, que no indican lo que el objeto es** (de eso se encarga la clase y sus **superclases**)**, sino acciones (capacidades) que el objeto debería ser capaz de realizar**. Es por esto que el nombre de muchas interfaces en Java termina con sufijos del tipo "-**able**", "-**or**", "**-ente**" y cosas del estilo, que significan algo así como **capacidad o habilidad** para hacer o ser receptores de algo (**configurable**, **serializable**, **modificable**, **clonable**, **ejecutable**, **administrador**, **servidor, buscador**, etc.), dando así la idea de que se tiene la capacidad de llevar a cabo el conjunto de acciones especificadas en la **interfaz**.

Imagínate por ejemplo la clase **Coche**, **subclase** de **Vehículo**. Los coches son **vehículos a motor**, lo cual implica una serie de acciones como, por ejemplo, **arrancar el motor** o **detener el motor**. Esa acción no la puedes heredar de **Vehículo**, pues no todos los vehículos tienen porqué ser a motor (piensa por ejemplo en una clase **Bicicleta** o un **coche eléctrico**), y no puedes heredar de otra clase pues ya heredas de **Vehículo**. Una solución podría ser crear una **interfaz Arrancable**, que proporcione los métodos típicos de un **objeto a motor** (no necesariamente vehículos). De este modo la clase **Coche** sigue siendo subclase de **Vehículo**, pero también implementaría los comportamientos de la interfaz **Arrancable**, los cuales podrían ser también implementados por otras clases, hereden o no de **Vehículo** (por ejemplo una clase **Motocicleta** o bien una clase **Motosierra**). La clase **Coche** implementará su método **arrancar** de una manera, la clase **Motocicleta** lo hará de otra (aunque bastante parecida) y la clase **Motosierra** de otra forma probablemente muy diferente, pero todos tendrán su propia versión del método **arrancar** como parte de la interfaz **Arrancable**.

Según esta concepción, podrías hacerte la siguiente pregunta: **¿podrá una clase implementar varias interfaces?** La respuesta en este caso sí es afirmativa.

📣 **Una clase puede adoptar distintos modelos de comportamiento establecidos en diferentes interfaces. Es decir una clase puede implementar varias interfaces.**

#### 4.1.1 ¿Clase abstracta o interfaz?

Observando el concepto de **interfaz** que se acaba de proponer, podría caerse en la tentación de pensar que es prácticamente lo mismo que una **clase abstracta** en la que **todos sus métodos sean abstractos**.

Es cierto que en ese sentido existe un gran **parecido formal** entre una **clase abstracta** y una **interfaz**, pudiéndose en ocasiones utilizar indistintamente una u otra para obtener un mismo fin. Pero, a pesar de ese gran parecido, existen algunas diferencias, no sólo formales, sino también conceptuales, muy importantes:

- **Una clase no puede heredar de varias clases**, aunque sean abstractas (**herencia múltiple**). Sin embargo sí puede **implementar una o varias interfaces** y además seguir heredando de una clase.
- **Una interfaz no puede definir métodos** (**no implementa su contenido**), tan solo los declara o enumera.
- **Una interfaz puede hacer que dos clases tengan un mismo comportamiento** independientemente de sus ubicaciones en una determinada jerarquía de clases (no tienen que heredar las dos de una misma superclase, pues no siempre es posible según la naturaleza y propiedades de cada clase).
- **Una interfaz permite establecer un comportamiento de clase sin apenas dar detalles**, pues esos detalles aún no son conocidos (dependerán del modo en que cada clase decida implementar la **interfaz**).
- **Las interfaces tienen su propia jerarquía**, diferente e independiente de la jerarquía de clases.

De todo esto puede deducirse que **una clase abstracta proporciona una interfaz disponible sólo a través de la herencia**. Sólo quien herede de esa **clase abstracta** dispondrá de esa **interfaz**. Si una clase no pertenece a esa misma jerarquía (no hereda de ella) no podrá tener esa **interfaz**. Eso significa que para poder disponer de la **interfaz** podrías:



![PROG09_CONT_R52_ComposicionAbstracta](img/PROG09_CONT_R52_ComposicionAbstracta.jpg)

1. Volver a escribirla para esa jerarquía de clases. Lo cual no parece una buena solución.
2. Hacer que la clase herede de la superclase que proporciona la **interfaz** que te interesa, sacándola de su jerarquía original y convirtiéndola en **clase derivada** de algo de lo que conceptualmente no debería ser una **subclase**. Es decir, estarías forzando una relación "**es un**" cuando en realidad lo más probable es que esa relación no exista. Tampoco parece la mejor forma de resolver el problema.

Sin embargo, **una interfaz sí puede ser implementada por cualquier clase**, permitiendo que clases que no tengan ninguna relación entre sí (pertenecen a distintas jerarquías) puedan compartir un determinado comportamiento (una interfaz) sin tener que forzar una relación de herencia que no existe entre ellas.

A partir de ahora podemos hablar de otra posible relación entre clases: la de **compartir un determinado comportamiento (interfaz)** . Dos clases podrían tener en común un determinado conjunto de comportamientos sin que necesariamente exista una relación jerárquica entre ellas. Tan solo cuando haya realmente una relación de tipo " **es un** " se producirá **herencia** .





#### Recomendación

Si sólo vas a proporcionar una lista de **métodos abstractos** (**interfaz**), sin definiciones de métodos ni atributos de objeto, suele ser recomendable definir una **interfaz** antes que **clase abstracta**. Es más, cuando vayas a definir una supuesta **clase base**, puedes comenzar declarándola como **interfaz** y sólo cuando veas que necesitas definir métodos o variables miembro, puedes entonces convertirla en **clase abstracta** (no instanciable) o incluso en una **clase instanciable**.



!!! note "Comparación entre lenguajes: Interfaces"
    === "Java"

        ```java
        public interface Depredador { 
        void cazar(); 
        }
        ```
    
    === "Python"


        ```python
        from abc import ABC, abstractmethod
        class Depredador(ABC):
        @abstractmethod
        def cazar(self):
            pass
        ```



    === "Kotlin"
    
        ```kotlin
        interface Depredador {
            fun cazar()
        }
        ```

 4.2 Definición de interfaces

La **declaración de una interfaz** en Java es similar a la declaración de una clase, aunque con algunas variaciones:

- Se utiliza la palabra reservada `interface` en lugar de `class`.
- Puede utilizarse el modificador `public`. Si incluye este modificador la **interfaz** debe tener el mismo nombre que el archivo .java en el que se encuentra (exactamente igual que sucedía con las clases). Si no se indica el modificador `public`, el acceso será por omisión o "**de paquete**" (como sucedía con las clases).
- Todos los **miembros** de la **interfaz** (atributos y métodos) son `public` de manera implícita. No es necesario indicar el modificador `public`, aunque puede hacerse.
- Todos los **atributos** son de tipo `final` y `public` (tampoco es necesario especificarlo), es decir, **constantes** y **públicos**. Hay que darles un **valor inicial**.
- Todos los **métodos** son **abstractos** también de manera implícita (tampoco hay que indicarlo). No tienen cuerpo, tan solo la cabecera.

Como puedes observar, una **interfaz** consiste esencialmente en una lista de **atributos finales** (**constantes**) y **métodos abstractos** (**sin implementar**). Su sintaxis quedaría entonces:



```java
[public] interface <NombreInterfaz> {
                [public] [final] <tipo1> <atributo1>= <valor1>;
                [public] [final] <tipo2> <atributo2>= <valor2>;
                ...
                [public] [abstract] <tipo_devuelto1>  <nombreMetodo1> ([lista_parámetros]);
                [public] [abstract] <tipo_devuelto2>  <nombreMetodo2> ([lista_parámetros]);
                ...          
}
```

Si te fijas, la declaración de los métodos termina en punto y coma, pues no tienen cuerpo, al igual que sucede con los **métodos abstractos** de las **clases abstractas**.

El ejemplo de la interfaz **Depredador** que hemos visto antes podría quedar entonces así:

```java
public interface Depredador {
    void localizar(Animal presa);
    void cazar(Animal presa);
    ...
} 
```

![img/PROG09_CONT_R54_Cocodrilo](img/PROG09_CONT_R54_Cocodrilo.jpg)

Serán las clases que implementen esta interfaz (**León**, **Leopardo**, **Cocodrilo**, **Rana**, **Lagarto**, **Hombre**, etc.) las que definan cada uno de los métodos por dentro.

#### Ejercicio 10

Crea una interfaz en Java cuyo nombre sea **Imprimible** y que contenga algunos métodos útiles para mostrar el contenido de una clase:

1. Método **devolverContenidoString**, que crea un `String` con una representación de todo el contenido público (o que se decida que deba ser mostrado) del objeto y lo devuelve. El formato será una lista de pares "nombre=valor" de cada atributo separado por comas y la lista completa encerrada entre llaves: "{<nombre_atributo_1>=<valor_atributo_1>, ..., <nombre_atributo_n>=<valor__atributo_n>}".
2. Método **devolverContenidoArrayList**, que crea un `ArrayList` de `String` con una representación de todo el contenido público (o que se decida que deba ser mostrado) del objeto y lo devuelve.
3. Método **devolverContenidoHashtable**, similar al anterior, pero en lugar devolver en un `ArrayList` los valores de los atributos, se devuelve en una `Hashtable` en forma de pares (nombre, valor).

### 4.3 Implementación de interfaces

Como ya has visto, todas las clases que implementan una determinada **interfaz** están obligadas a proporcionar una **definición (implementación) de los métodos de esa interfaz**, adoptando el modelo de comportamiento propuesto por ésta.

Dada una **interfaz**, cualquier clase puede especificar dicha **interfaz** mediante el mecanismo denominado **implementación de interfaces**. Para ello se utiliza la palabra reservada `implements`:

```java
class NombreClase implements NombreInterfaz {
```

De esta manera, la clase está diciendo algo así como "**la interfaz indica los métodos que debo implementar, pero voy a ser yo (la clase) quien los implemente**".

Es posible indicar varios nombres de **interfaces** separándolos por comas:

```java
class NombreClase implements NombreInterfaz1, NombreInterfaz2,... {
```

Cuando una clase implementa una **interfaz**, tiene que redefinir sus métodos nuevamente con **acceso público**. Con otro tipo de acceso se producirá un **error de compilación**. Es decir, que del mismo modo que no se podían restringir permisos de acceso en la **herencia de clases**, tampoco se puede hacer en la **implementación de interfaces**.

Una vez implementada una **interfaz** en una clase, los métodos de esa interfaz tienen exactamente el mismo tratamiento que cualquier otro método, sin ninguna diferencia, pudiendo ser invocados, heredados, redefinidos, etc.

En el ejemplo de los depredadores, al definir la clase **León**, habría que indicar que implementa la **interfaz** **Depredador**:

```java
class Leon implements Depredador {
```

Y en su interior habría que implementar aquellos métodos que contenga la **interfaz**:

```java
// Implementación del método localizar para un león
void localizar(Animal presa) { 
    ...
} 
```

En el caso de clases que pudieran ser a la vez **Depredador** y **Presa**, tendrían que implementar ambas interfaces, como podría suceder con la clase **Rana**:

```java
class Rana implements Depredador, Presa {
```

Y en su interior habría que implementar aquellos métodos que contengan ambas **interfaces** , tanto las de **Depredador** ( **localizar** , **cazar** , etc.) como las de **Presa** ( **observar** , **huir** , etc.).

**Ejercicio 11**

Haz que las clases `Alumno` y `Profesor` implementen la interfaz `Imprimible` que se ha escrito en el ejercicio anterior.



!!! inf "Comparación entre lenguajes: Implementación de interfaces"

=== "Java"

    ```java
    class Leon implements Depredador { 
        public void localizar(Animal presa) { } 
    }
    ```

=== "Python"
    

    ```python
    class Leon(Depredador):
        def localizar(self, presa):
            pass
    ```


=== "Kotlin"
    
    ```kotlin
    class Leon : Depredador {
        override fun localizar(presa: Animal) { }
    }
    ```

### 4.4 Simulación de la herencia múltiple mediante el uso de interfaces

Una **interfaz** no tiene **espacio de almacenamiento** asociado (no se van a declarar objetos de un tipo de interfaz), es decir, no tiene **implementación**.

En algunas ocasiones es posible que interese representar la situación de que "una clase **X** es de tipo **A**, de tipo **B**, y de tipo **C**", siendo **A**, **B**, **C** **clases disjuntas** (no heredan unas de otras). Hemos visto que sería un caso de **herencia múltiple** que Java no permite.

Para poder simular algo así, podrías definir tres **interfaces** **A**, **B**, **C** que indiquen los comportamientos (métodos) que se deberían tener según se pertenezca a una supuesta clase **A**, **B**, o **C**, pero sin implementar ningún método concreto ni atributos de objeto (sólo interfaz).


![PROG09_CONT_R63_InterfacesMultiplesDepredadorPresa](img/PROG09_CONT_R63_InterfacesMultiplesDepredadorPresa.png)

De esta manera la clase **X** podría a la vez:

1. Implementar las interfaces **A**, **B**, **C**, que la dotarían de los comportamientos que deseaba heredar de las clases **A**, **B**, **C**.
2. Heredar de otra clase **Y**, que le proporcionaría determinadas características dentro de su taxonomía o jerarquía de objeto (atributos, métodos implementados y métodos abstractos).

En el ejemplo que hemos visto de las interfaces **Depredador** y **Presa**, tendrías un ejemplo de esto: la clase **Rana**, que es subclase de **Anfibio**, implementa una serie de **comportamientos** propios de un **Depredador** y, a la vez, otros más propios de una **Presa**. Esos **comportamientos** (**métodos**) no forman parte de la **superclase** **Anfibio**, sino de las **interfaces**. Si se decide que la clase **Rana** debe de llevar a cabo algunos otros **comportamientos adicionales**, podrían añadirse a una **nueva interfaz** y la clase **Rana** **implementaría** una tercera **interfaz**.

De este modo, con el mecanismo "**una herencia pero varias interfaces**", podrían conseguirse resultados similares a los obtenidos con la **herencia múltiple**.

Ahora bien, del mismo modo que sucedía con la **herencia múltiple**, puede darse el problema de la **colisión de nombres** al implementar dos **interfaces** que tengan un **método con el mismo identificador**. En tal caso puede suceder lo siguiente:

- Si los dos métodos tienen **diferentes parámetros** no habrá problema aunque tengan el mismo nombre pues se realiza una **sobrecarga** de métodos.
- Si los dos métodos tienen **un valor de retorno de un tipo diferente**, se producirá un **error de compilación** (al igual que sucede en la sobrecarga cuando la única diferencia entre dos métodos es ésa).

Si los dos métodos son **exactamente iguales en identificador, parámetros y tipo devuelto** , entonces solamente se podrá **implementar uno de los dos métodos** . En realidad se trata de un solo método pues ambos tienen la misma interfaz (mismo identificador, mismos parámetros y mismo tipo devuelto).

#### Recomendación

La utilización de nombres idénticos en diferentes **interfaces** que pueden ser implementadas a la vez por una misma clase puede causar, además del problema de la **colisión de nombres**, dificultades de **legibilidad** en el código, pudiendo dar lugar a confusiones. Si es posible intenta evitar que se produzcan este tipo de situaciones.



### 4.5 Herencia de interfaces

Las **interfaces**, al igual que las **clases**, también permiten la **herencia**. Para indicar que una **interfaz** hereda de otra se indica nuevamente con la palabra reservada `extends`. Pero en este caso sí se permite la **herencia múltiple de interfaces**. Si se hereda de más de una **interfaz** se indica con la lista de **interfaces** separadas por comas.

Por ejemplo, dadas las interfaces **InterfazUno** e **InterfazDos**:

```java
public interface InterfazUno {

    // Métodos y constantes de la interfaz Uno

}
```

```java
public interface InterfazDos {

    // Métodos y constantes de la interfaz Dos

}
```

Podría definirse una nueva **interfaz** que heredara de ambas:

```java
public interface InterfazCompleja extends InterfazUno, InterfazDos {

    // Métodos y constantes de la interfaz compleja

}
```

!!! Note "Comparación entre lenguajes: Herencia de interfaces"

    === "Java"
    
        ```java
        public interface InterfazCompleja extends InterfazUno, InterfazDos { }
        ```
    
    === "Python"
        
        ```python
        class InterfazCompleja(InterfazUno, InterfazDos):
            pass
        ```
    
    === "Kotlin"
        
        ```kotlin
            interface InterfazCompleja : InterfazUno, InterfazDos
        ```

​    
## 5. Interfaces para comparar objetos

Hasta ahora hemos visto que las clases Arrays y Collections disponen de un conjunto de operaciones típicas asociadas que son habituales:

- Ordenar listas y arrays.
- Desordenar listas y arrays.
- Búsqueda binaria en listas y arrays.
- Conversión de arrays a listas y de listas a array.
- Partir cadenas y almacenar el resultado en un array.

Estos algoritmos están recogidos como métodos estáticos de las `clases java.util.Collections` y `java.util.Arrays.`

Uno de estos métodos es el **método sort**. Permite ordenar los elementos pero únicamente funciona con objetos de la clase String, no con otro tipo de objetos.

Los algoritmos de ordenación ordenan los elementos en orden natural, siempre que Java sepa como ordenarlos. Los tipos "ordenables" de forma natural son los enteros, las cadenas (orden alfabético) y las fechas, y por defecto su orden es ascendente. Con el resto de clases, hay que facilitar un mecanismo para que se pueda producir esa ordenación.

En este apartado, vamos a ver cómo hacerlo en Java y lo aplicaremos a los ArrayList pero funcionará igual con los Arrays. En concreto, estudiaremos **las interfaces Comparable y Comparator**; cómo se implementan y cómo se utilizan.

### 5.1 Interfaz Comparable (I)

En Java hay dos mecanismos para cambiar la forma en la que los elementos se ordenan. Imaginemos que los alumnos los tenemos almacenados en una lista llamada "ListaAlumnos" y necesitamos ordenarlos por nombre.



```java
public class Alumno {
    String nombre;
    String apellidos;
    String [] telefono = new String [3];
    int edad;
}
```



La primera forma de ordenar una lista consiste en crear un **procedimiento bien definido para poder decidir dados 2 valores su orden relativo**. Es decir, si uno de los valores es menor, igual o mayor que el otro. El orden impuesto en ese procedimiento se conoce como orden natural de la clase.

Como hemos visto, no todas las clases tienen ese orden natural. **Para que una clase sea ordenable deberá implementar la interfaz comparable**.

La interfaz comparable tendrá un **único método**, el método **compareTo**. Con definir ese método será suficiente para que el método sort funcione:



```java
public interface Comparable<T> {
    public int compareTo(T otro);
}
```



En este caso, se utiliza <T> para indicar que es una interfaz generíca para un tipo (Type) o clase concreta. El método compareTo se definirá para toda la clase. Se usará un entero en vez de un boolean porque tenemos 3 casos diferentes para distinguir: menor, igual o mayor.

Por convenio, compareTo recibirá un objeto y devolverá:

- Un valor negativo para indicar que el objeto es menor que el pasado como parámetro.
- 0 cuando sean iguales.
- Un valor mayor que 0 para indicar que es mayor que el pasado como parámetro.



```java
// Comparar objetos
if (s1.compareTo(s2) < 0) {
    System.out.println("s1 es menor que s2");
}
```



En este caso, se utiliza <T> para indicar que es un interfaz genérica para un tipo (Type) o clase concreta:



```java
public class Alumno implements Comparable<Alumno> {
    String nombre;
    String apellidos;
    String [] telefono = new String [3];
    int edad;
    @Override
    public int compareTo(Alumno o) {

        return this.nombre.compareTo(o.nombre);
    }
}
```



Aquí podemos ver como implementamos el método comparable directamente. Este va a realizar una ordenación ascendente, de menor a mayor.

Si queremos realizar una ordenación de mayor a menor lo podemos realizar así:



```java
public class Alumno implements Comparable<Alumno> {
    String nombre;
    String apellidos;
    String [] telefono = new String [3];
    int edad;
    @Override
    public int compareTo(Alumno o) {

		if (this.nombre.compareTo(o.nombre)==0)
			return 0;
		else if(this.nombre.compareTo(o.nombre)>0)
			return -1;
		else
			return 1;
    }
}
```



Y utilizando la misma estrategia podemos realizar una ordenación por cualquier otro criterio de la clase Alumno.

El funcionamiento del método `compareTo` es el mismo que el método compare de la interfaz `Comparator`: si la clase que se pasa por parámetro es igual al objeto, se tendría que retornar 0; si es menor o anterior, se debería retornar un número menor que cero; si es mayor o posterior, se debería retornar un número mayor que 0.

Ordenar ahora la lista de artículos es sencillo, fíjate que fácil: "`Collections.sort(Alumnos);`"



```java
public class Main {

    public static void main(String[] args) {

        ArrayList<Alumno> Alumnos = new ArrayList<Alumno>();
        Alumno a1 = new Alumno();
        Alumno a2 = new Alumno();
        Alumno a3 = new Alumno();
        Alumno a4 = new Alumno();
        Alumno a5 = new Alumno();
        Alumno a6 = new Alumno();
        a3.nombre="Loren";
        a4.nombre ="Alejo";
        a1.nombre = "Miquel Josep";
        a1.apellidos = "Garcia";
        a1.edad = 25;
        a1.telefono[0] = "961712222";
        a1.telefono[1] = "961702299";
        a2.nombre="Pepe";
        a5.nombre="Manu";
        a5.apellidos="Romero";
        a5.edad=40;
        a6.nombre="Jose";
        a6.apellidos="Abad";
        a6.edad=30;

        Alumnos.add(a1);
        Alumnos.add(a2);
        Alumnos.add(a3);
        Alumnos.add(a4);
        Alumnos.add(a5);
        Alumnos.add(a6);

        System.out.println("Impresión normal");
        System.out.println("************************************");
        for(Alumno a: Alumnos)
            System.out.println(a.nombre);
        System.out.println("************************************");
        System.out.println("Impresión ordenada");
        // Realizamos la ordenación.
        Collections.sort(Alumnos);
        for(Alumno a: Alumnos)
            System.out.println(a.nombre);
    }

}
```



Del ejemplo anterior se pueden mencionar 3 cosas importantes:

- La interfaz `Comparable` es genérica y para que funcione sin problemas hay que indicar la clase sobre la que se permite la comparación. En este caso, el objeto `Alumno` debe compararse consigo mismo.
- El método `compareTo` **solo admite un parámetro**, dado que comparará el objeto actual con el objeto que se pasa por parámetro.
- Dentro de compareTo tenemos que comparar 2 cadenas de caracteres. Para ello, utilizaremos el método compareTo de la clase String.
- Si queremos comparar otros valores, deberemos redefinir la función compareTo en la clase que implementamos la interfaz Comparable.

Como ya se ha comentado, si el objeto que se pasa por parámetro es igual al objeto, se retornará 0; si es menor, se retornará un número menor que cero; si es mayor, se retornará un número mayor que 0.

Ordenar ahora la lista de artículos es tan sencillo como ejecutar la siguiente línea de código: "`Collections.sort(Alumnos);`"

!!! Example "Comparación entre lenguajes: Interfaz Comparable"

    === "Java"
        ```java 
        public class Alumno implements Comparable<Alumno> { 
            @Override public int compareTo(Alumno o) { 
                return this.nombre.compareTo(o.nombre);
                } 
            }
        ```
    === "Python"
        ```python
        class Alumno:
            def __lt__(self, other):
                return self.nombre < other.nombre
            # También se pueden definir __le__, __gt__, __ge__, __eq__, __ne__
        ```
    
    === "Kotlin"
        ```kotlin
        class Alumno : Comparable<Alumno> {
            override fun compareTo(other: Alumno): Int {
                return this.nombre.compareTo(other.nombre)
            }
        }
        ```



### 5. 2 Interfaz Comparator (I)

Con la interfaz comparable definimos el orden natural de ordenación, pero ¿se podría cambiar ese orden de ordenación? Hay casos en los que nos puede interesar cambiar la forma de ordenar los elementos. Esto es especialmente útil cuando el tipo de objeto que se almacena no es un simple número, sino algo más complejo, un Alumno por ejemplo. Podríamos ordenarlo por la edad del alumno.

Para indicarle a una colección cómo tiene que ordenar los elementos, debemos decirle cuándo un elemento va antes o después que otro, y cuándo son iguales. Para ello, utilizamos la interfaz genérica `java.util.Comparator`, usada en algoritmos de ordenación.

**Se trata de crear una clase que implemente dicha interfaz**. Dicha interfaz requiere de un único método que debe calcular si un objeto pasado por parámetro es mayor, menor o igual que otro del mismo tipo.

Veamos un ejemplo general de cómo implementar un comparador para una hipotética clase "`Objeto`":



```java
class ComparadorDeObjetos implements Comparator<Clase> {
    public int compare(Objeto o1, Objeto o2) {
        ...
    }    
}
```



La interfaz `Comparator` obliga a implementar un único método, es el método compare, el cual tiene dos parámetros: los dos elementos a comparar. Las reglas son sencillas, a la hora de personalizar dicho método:

- Si el primer objeto (`o1`) es menor que el segundo (`o2`), debe retornar un número entero negativo.
- Si el primer objeto (`o1`) es mayor que el segundo (`o2`), debe retornar un número entero positivo.
- Si ambos son iguales, debe retornar 0.

A veces, cuando el orden que deben tener los elementos es diferente al orden real (por ejemplo cuando ordenamos los números en orden inverso), la definición de antes puede ser un poco liosa, así que es recomendable en tales casos pensar de la siguiente forma:

- Si el primer objeto (`o1`) debe ir antes que el segundo objeto (`o2`), retornar entero negativo.
- Si el primer objeto (`o1`) debe ir después que el segundo objeto (`o2`), retornar entero positivo.
- Si ambos son iguales, debe retornar 0.

Una vez creado el comparador simplemente tenemos que pasarlo como parámetro en el momento de la creación de la colección, y los datos internamente mantendrán dicha ordenación:



```java
Collections.sort(ListaObjetos, new comparadorObjetos());
```



!!! Example "Comparación entre lenguajes: Interfaz Comparator"

=== "Java"
    ```java 
    class ComparadorAlumnos implements Comparator<Alumno> { 
        public int compare(Alumno a1, Alumno a2) { 
        return a1.edad - a2.edad; 
        } 
    } // Uso: Collections.sort(alumnos, new ComparadorAlumnos());`

    ```
=== "Python"
    ```python
    from functools import cmp_to_key
    
    def comparar_alumnos(a1, a2):
        return a1.edad - a2.edad
    
    alumnos.sort(key=cmp_to_key(comparar_alumnos))
    # O usar una lambda para criterios simples:
    alumnos.sort(key=lambda a: a.edad)
    ```

=== "Kotlin"
    ```kotlin
    val comparador = Comparator<Alumno> { a1, a2 ->
        a1.edad - a2.edad
    }
    alumnos.sortWith(comparador)
    // O más simple:
    alumnos.sortedBy { it.edad }
    ```




## 6. Polimorfismo

El **polimorfismo** es otro de los grandes pilares sobre los que se sustenta la **Programación Orientada** **a Objetos** (junto con la **encapsulación** y la **herencia**). Se trata nuevamente de otra forma más de establecer diferencias entre interfaz e implementación, es decir, entre **el qué** y **el cómo**.

![PROG09_CONT_R66_FormasVariadas](img/PROG09_CONT_R66_FormasVariadas.jpg)

La **encapsulación** te ha permitido agrupar **características** (**atributos**) y **comportamientos** (**métodos**) dentro de una misma unidad (**clase**), pudiendo darles un mayor o menor componente de **visibilidad**, y permitiendo separar al máximo posible la **interfaz** de la **implementación**. Por otro lado la **herencia** te ha proporcionado la posibilidad de tratar a los objetos como pertenecientes a una **jerarquía de clases**. Esta capacidad va a ser fundamental a la hora de poder manipular muchos posibles objetos de clases diferentes como si fueran de la misma clase (**polimorfismo**).

El **polimorfismo** te va a permitir mejorar la **organización** y la **legibilidad** del código así como la posibilidad de desarrollar aplicaciones que sean más fáciles de ampliar a la hora de incorporar nuevas funcionalidades. Si la implementación y la utilización de las clases es lo suficientemente genérica y extensible será más sencillo poder volver a este código para incluir nuevos requerimientos.

### 6.1 Concepto de Polimorfismo

El **polimorfismo** consiste en la capacidad de poder utilizar una referencia a un objeto de una determinada clase como si fuera de otra clase (en concreto una **subclase**). Es una manera de decir que una clase podría tener varias (poli) formas (morfismo).

Un método "**polimórfico**" ofrece la posibilidad de ser distinguido (saber a qué clase pertenece) en **tiempo de ejecución** en lugar de en **tiempo de compilación**. Para poder hacer algo así es necesario utilizar métodos que pertenecen a una **superclase** y que en cada **subclase** se implementan de una forma en particular. En **tiempo de compilación** se invocará al método sin saber exactamente si será el de una subclase u otra (pues se está invocando al de la **superclase**). Sólo en **tiempo de ejecución** (una vez instanciada una u otra **subclase**) se conocerá realmente qué método (de qué **subclase**) es el que finalmente va a ser invocado.

Esta forma de trabajar te va a permitir hasta cierto punto "desentenderte" del tipo de objeto **específico** (**subclase**) para centrarte en el tipo de objeto **genérico** (**superclase**). De este modo podrás manipular objetos hasta cierto punto "desconocidos" en tiempo de compilación y que sólo durante la ejecución del programa se sabrá exactamente de qué tipo de objeto (**subclase**) se trata.

📣 El **polimorfismo** ofrece la **posibilidad de que toda referencia a un objeto de una superclase pueda tomar la forma de una referencia a un objeto de una de sus subclases**. Esto te va a permitir escribir programas que procesen objetos de clases que formen parte de la misma jerarquía como si todos fueran objetos de sus **superclases**.

📣 El **polimorfismo** puede llevarse a cabo tanto con **superclases** (abstractas o no) como con **interfaces**.

Dada una **superclase** **X**, con un método **m**, y dos **subclases** **A** y **B**, que redefinen ese método **m**, podrías declarar un objeto **O** de tipo **X** que en durante la **ejecución** podrá ser de tipo **A** o de tipo **B** (algo desconocido en **tiempo de compilación**). Esto significa que al invocarse el método **m** de **X** (**superclase**), se estará en realidad invocando al método **m** de **A** o de **B** (alguna de sus **subclases**). Por ejemplo:



```java
// Declaración de una referencia a un objeto de tipo X
ClaseX obj;  // Objeto de tipo X (superclase)
...

// Zona del programa donde se instancia un objeto de tipo A (subclase) y se le asigna a la referencia obj.

// La variable obj adquiere la forma de la subclase A.
obj = ClaseA();
...

// Otra zona del programa.

// Aquí se instancia un objeto de tipo B (subclase) y se le asigna a la referencia obj.

// La variable obj adquiere la forma de la subclase B.
obj = ClaseB();
...

// Zona donde se utiliza el método m sin saber realmente qué subclase se está utilizando.

// (Sólo se sabrá durante la ejecución del programa)
obj.m()  // Llamada al método m (sin saber si será el método m de A o de B).
...
```



Imagina que estás trabajando con las clases `Alumno` y `Profesor` y que en determinada zona del código podrías tener objetos, tanto de un tipo como de otro, pero eso sólo se sabrá según vaya discurriendo la ejecución del programa. En algunos casos, es posible que un determinado objeto pudiera ser de la clase `Alumno` y en otros de la clase `Profesor`, pero en cualquier caso serán objetos de la clase `Persona`. Eso significa que la llamada a un método de la clase `Persona` (por ejemplo `devolverContenidoString`) en realidad será en unos casos a un método (con el mismo nombre) de la clase `Alumno` y, en otros, a un método (con el mismo nombre también) de la clase `Profesor`. Esto será posible hacerlo gracias a la **ligadura dinámica**.

!!! Example "Comparación entre lenguajes: Polimorfismo"
    
    === "Java"
        ```java 
        Persona p = new Alumno(); 
        // Polimorfismo p.mostrar(); 
        // Se ejecuta Alumno.mostrar()`

        ```
    === "Python"
        ```python
        p = Alumno()  # Polimorfismo implícito
        p.mostrar()   # Se ejecuta Alumno.mostrar()
        ```

    === "Kotlin"
        ```kotlin
        val p: Persona = Alumno() // Polimorfismo
        p.mostrar() // Se ejecuta Alumno.mostrar()
        ```


### 6.2 Ligadura dinámica

La conexión que tiene lugar durante una llamada a un método suele ser llamada **ligadura**, **vinculación** o **enlace** (en inglés **binding**). Si esta **vinculación** se lleva a cabo durante el proceso de compilación, se le suele llamar **ligadura estática** (también conocido como **vinculación temprana**). En los lenguajes tradicionales, no orientados a objetos, ésta es la única forma de poder resolver la **ligadura** (en **tiempo de compilación**). Sin embargo, en los **lenguajes orientados a objetos** existe otra posibilidad: la **ligadura dinámica** (también conocida como **vinculación tardía, enlace tardío** o **late binding**).

La **ligadura dinámica** hace posible que sea el **tipo de objeto** instanciado (obtenido mediante el **constructor** finalmente utilizado para crear el objeto) y no el **tipo de la referencia** (el tipo indicado en la declaración de la variable que apuntará al objeto) lo que determine qué versión del método va a ser invocada. El **tipo de objeto** al que apunta la variable de tipo referencia sólo podrá ser conocido durante la **ejecución** del programa y por eso el **polimorfismo** necesita la **ligadura dinámica**.

En el ejemplo anterior de la clase **X** y sus **subclases** **A** y **B**, la llamada al método **m** sólo puede resolverse mediante ligadura dinámica, pues es imposible saber en tiempo de compilación si el método **m** que debe ser invocado será el definido en la subclase **A** o el definido en la subclase B:



```java
// Llamada al método m (sin saber si será el método m de A o de B).
obj.m()  // Esta llamada será resuelta en tiempo de ejecución (ligadura dinámica)
```



**Ejercicio 12**

Imagínate una clase que represente a **instrumento musical** genérico (**Instrumento**) y dos subclases que representen tipos de instrumentos específicos (por ejemplo **Flauta** y **Piano**). Todas las clases tendrán un método **tocarNota**, que será específico para cada subclase.

Haz un pequeño programa de ejemplo en Java que utilice el **polimorfismo** (referencias a la **superclase** que se convierten en instancias específicas de **subclases**) y la **ligadura dinámica** (llamadas a un método que aún no están resueltas en **tiempo de compilación**) con estas clases que representan instrumentos musicales. Puedes implementar el método **tocarNota** mediante la escritura de un mensaje en pantalla.

### 6.3 Limitaciones de la ligadura dinámica

Como has podido comprobar, el **polimorfismo** se basa en la utilización de **referencias** de un tipo más "amplio" (**superclases**) que los objetos a los que luego realmente van a apuntar (**subclases**). Ahora bien, existe una importante **restricción** en el uso de esta capacidad, pues el tipo de referencia limita cuáles son los métodos que se pueden utilizar y los atributos a los que se pueden acceder.

No se puede acceder a los **miembros específicos** de una **subclase** a través de una **referencia** a una **superclase**. Sólo se pueden utilizar los miembros declarados en la **superclase**, aunque la definición que finalmente se utilice en su ejecución será la de la **subclase**.

En el ejemplo de las clases **Persona** , **Profesor** y **Alumno** , el **polimorfismo** nos permitiría declarar variables de tipo **Persona** y más tarde hacer con ellas referencia a objetos de tipo **Profesor** o **Alumno** , pero no deberíamos intentar acceder con esa variable a métodos que sean específicos de la clase **Profesor** o de la clase **Alumno** , tan solo a métodos que sabemos que van a existir seguro en ambos tipos de objetos (métodos de la **superclase** **Persona** ).

**Ejercicio 13**

Haz un pequeño programa en Java en el que se declare una variable de tipo `Persona`, se pidan algunos datos sobre esa persona (**nombre**, **apellidos** y si es **alumno** o si es **profesor**), y se muestren nuevamente esos datos en pantalla, teniendo en cuenta que esa variable no puede ser instanciada como un objeto de tipo `Persona` (es una **clase abstracta**) y que tendrás que instanciarla como `Alumno` o como `Profesor`. Recuerda que para poder recuperar sus datos necesitarás hacer uso de la **ligadura dinámica** y que tan solo deberías acceder a métodos que sean de la **superclase**.

!!! Example "Comparación entre lenguajes: Limitaciones del polimorfismo"
    
    === "Java"
        ```java 
        Persona p = new Alumno(); 
        // p.getGrupo(); 
        // Error: no se puede acceder a método específico de Alumno
        ```
    === "Python"
        ```python
        p = Alumno()
        p.get_grupo()  # Funciona en Python (tipado dinámico)
        ```

    === "Kotlin"
        ```kotlin
        val p: Persona = Alumno()
        // p.grupo // Error: no se puede acceder a propiedad específica de Alumno
        ```




### 6.4 Interfaces y polimorfismo

Es posible también llevar a cabo el **polimorfismo** mediante el uso de **interfaces**. Un objeto puede tener una referencia cuyo tipo sea una **interfaz**, pero para que el compilador te lo permita, la clase cuyo **constructor** se utilice para crear el objeto deberá implementar esa **interfaz** (bien por si misma o bien porque la implemente alguna **superclase**). Un objeto cuya referencia sea de tipo **interfaz** sólo puede utilizar aquellos métodos definidos en la **interfaz**, es decir, que no podrán utilizarse los atributos y métodos específicos de su clase, tan solo los de la **interfaz**.

Las referencias de tipo **interfaz** permiten unificar de una manera bastante estricta la forma de utilizarse de objetos que pertenezcan a clases muy diferentes (pero que todas ellas implementan la misma **interfaz**). De este modo podrías hacer referencia a diferentes objetos que no tienen ninguna relación jerárquica entre sí utilizando la misma variable (referencia a la **interfaz**). Lo único que los distintos objetos tendrían en común es que implementan la misma **interfaz**. En este caso sólo podrás llamar a los métodos de la **interfaz** y no a los específicos de las clases.

![xPROG09_CONT_R72_BotonArranque.jpg.pagespeed.ic.XBGxZZs9qz](img/xPROG09_CONT_R72_BotonArranque.jpg.pagespeed.ic.XBGxZZs9qz.webp)

Por ejemplo, si tenías una variable de tipo referencia a la interfaz **Arrancable**, podrías instanciar objetos de tipo **Coche** o **Motosierra** y asignarlos a esa referencia (teniendo en cuenta que ambas clases no tienen una relación de herencia). Sin embargo, tan solo podrás usar en ambos casos los métodos y los atributos de la interfaz **Arrancable** (por ejemplo **arrancar**) y no los de **Coche** o los de **Motosierra** (sólo los genéricos, nunca los específicos).

En el caso de las clases `Persona`, `Alumno` y `Profesor`, podrías declarar, por ejemplo, variables del tipo `Imprimible`:



```java
Imprimible obj;                 // Imprimible es una interfaz y no una clase
```



Con este tipo de referencia podrías luego apuntar a objetos tanto de tipo **Profesor** como de tipo **Alumno**, pues ambos implementan la interfaz **Imprimible**:



```java
// En algunas circunstancias podría suceder esto:
obj = new  Alumno(nombre, apellidos, fecha, grupo, nota); // Polimorfismo con interfaces
...
// En otras circunstancias podría suceder esto:
obj = new  Profesor(nombre, apellidos, fecha, especialidad, salario); // Polimorfismo con interfaces
...
```



Y más adelante hacer uso de la **ligadura dinámica**:



```java
// Llamadas sólo a métodos de la interfaz
String contenido;
contenido = obj.devolverContenidoString();  // Ligadura dinámica con interfaces
```



!!! Example "Comparación entre lenguajes: Polimorfismo con interfaces"
   
    === "Java"
        ```java 
        Imprimible obj = new Alumno(); String s = obj.devolverContenidoString();

        ```
    === "Python"
        ```python
        obj: Imprimible = Alumno()  # Notación de tipo (opcional)
        s = obj.devolver_contenido_string()
        ```

    === "Kotlin"
        ```kotlin
        val obj: Imprimible = Alumno()
        val s = obj.devolverContenidoString()
        ```




### 6.5 Conversión de Objetos

Como ya has visto, en principio no se puede acceder a los **miembros específicos** de una **subclase** a través de una **referencia** a una **superclase**. Si deseas tener acceso a todos los métodos y atributos específicos del objeto **subclase** tendrás que realizar una **conversión explícita** (**casting**) que convierta la referencia más general (**superclase**) en la del tipo específico del objeto (**subclase**).


![PROG09_CONT_R73_CambioSentido](img/PROG09_CONT_R73_CambioSentido.gif)

Para que puedas realizar conversiones entre distintas clases es obligatorio que exista una relación de **herencia** entre ellas (una debe ser clase derivada de la otra). Se realizará una **conversión implícita o automática** de **subclase** a **superclase** siempre que sea necesario, pues un objeto de tipo **subclase** siempre contendrá toda la información necesaria para ser considerado un objeto de la **superclase**.

Ahora bien, la conversión en sentido contrario (de **superclase** a **subclase**) debe hacerse de forma **explícita** y según el caso podría dar lugar a errores por falta de información (atributos) o de métodos. En tales casos se produce una ****excepción\**** de tipo **`ClassCastException`**.

Por ejemplo, imagina que tienes una clase **A** y una clase **B**, **subclase** de **A**:



```java
class ClaseA {
     public int atrib1;
} 

class ClaseB extends ClaseA {
     public int atrib2;
} 
```



A continuación declaras una variable referencia a la clase **A** (**superclase**) pero sin embargo le asignas una referencia a un objeto de la clase **B** (**subclase**) haciendo uso del **polimorfismo**:



```java
ClaseA obj;          // Referencia a objetos de la clase A
obj = new ClaseB();  // Referencia a objetos clase A, pero apunta realmente a objeto clase B (polimorfismo)
```



El objeto que acabas de crear como **instancia de la clase B** (**subclase** de **A**) contiene más información que la que la referencia **obj** te permite en principio acceder sin que el compilador genere un error (pues es de clase **A**). En concreto los objetos de la clase **B** disponen de **atrib1** y **atrib2**, mientras que los objetos de la clase **A** sólo de **atrib1**. Para acceder a esa información adicional de la clase especializada (**atrib2**) tendrás que realizar una **conversión explícita** (**casting**):



```java
// Casting del tipo A al tipo B (funcionará bien porque el objeto es realmente del tipo B)
ClaseB objetoClaseB = (ClaseB) obj; 
System.out.printf("obj.atrib2 = %d\n", objetoClaseB.atrib2);
```



Sin embargo si se hubiera tratado de una **instancia de la clase A** y hubieras intentado acceder al miembro **atrib2**, se habría producido una **excepción** de tipo **`ClassCastException`**:



```java
ClaseA obj;          // Referencia a objetos de la clase A
obj = new ClaseA();  // Referencia a objetos de la clase A, y apunta realmente a un objeto de la clase A

// Casting del tipo A al tipo B (puede dar problemas porque el objeto es realmente del tipo A)
// Convendría usar la sentencia instanceof
ClaseB objetoClaseB = (ClaseB) obj; 
// Funciona (la clase A tiene atrib1)
System.out.printf("obj.atrib1 = %d\n", obj.atrib1); 

// ¡Error en ejecución! (la clase A no tiene atrib2). Producirá una ClassCastException.
System.out.printf ("obj.atrib2 = %d\n", objetoClaseB.atrib2); 
```



!!! Example "Comparación entre lenguajes: Conversión de objetos"

    === "Java"
        ```java 
        // Casting explícito if (obj instanceof ClaseB) { ClaseB b = (ClaseB) obj; }`

        ```
    === "Python"
        ```python
        # Casting generalmente no necesario en Python
        if isinstance(obj, ClaseB):
            b = obj  # Ya es de tipo ClaseB
        ```

    === "Kotlin"
        ```kotlin
        // Casting seguro con 'as?'
        val b = obj as? ClaseB
        if (b != null) {
            // Usar b
        }
        // O con 'is'
        if (obj is ClaseB) {
            // obj se convierte automáticamente a ClaseB en este scope
        }
        ```




## 7. La clase Object en Java

Todas las clases en Java son descendientes (directos o indirectos) de la clase **`Object`**. Esta clase define los **estados y comportamientos básicos que deben tener todos los objetos**. Entre estos comportamientos, se encuentran:

- La posibilidad de compararse.
- La capacidad de convertirse a cadenas.
- La habilidad de devolver la clase del objeto.

![PROG09_CONT_R32_Object](img/PROG09_CONT_R32_Object.png)

Entre los métodos que incorpora la clase **`Object`** y que por tanto hereda cualquier clase en Java tienes:

Principales métodos de la clase Object

| Método                         | Descripción                                                  |
| :----------------------------- | :----------------------------------------------------------- |
| **`Object()`**                 | Constructor.                                                 |
| **`clone()`**                  | Método **clonador**: crea y devuelve una copia del objeto ("clona" el objeto). |
| ~~**`void finalize()`**~~      | ~~Método llamado por el **recolector de basura** cuando considera que no queda ninguna referencia a este objeto.~~ |
| **`int hashCode()`**           | Devuelve un código **hash** para el objeto.                  |
| **`toString()`**               | Devuelve una representación del objeto en forma de **`String`**. |
| **boolean equals(Object obj)** | Indica si un objeto es igual o no al objeto pasado como parámetro. |

La clase **`Object`** representa la **superclase** que se encuentra en la cúspide de la **jerarquía de herencia** en Java. Cualquier clase (incluso las que tú implementes) acaban heredando de ella.


![PROG09_CONT_R33_JerarquiaClasesJava](img/PROG09_CONT_R33_JerarquiaClasesJava.jpg)

!!! info "Para saber más"

    Para obtener más información sobre la clase **`Object`**, sus métodos y propiedades, puedes consultar la documentación de la API de **Java** en el sitio web de Oracle. [Documentación de la clase **`Object`**.](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html)

!!! Example "Comparación entre lenguajes: Clase base universal"
    
    === "Java"

        ```java 
        // Todas las clases heredan de Object class MiClase { }
        // implícitamente extiende Object`

        ```
    === "Python"
        ```python
        # Todas las clases heredan de object
        class MiClase:  # implícitamente extiende object
            pass
        ```

    === "Kotlin"
        ```kotlin
        // Todas las clases heredan de Any
        class MiClase  // implícitamente extiende Any
        ```




### 7.1 El método equals

Cuando explicamos las clases, ya vimos como se podía reescribir el método toString. Ahora sabemos que un método que se hereda de la clase Object y que podemos reescribirlos para que muestre la información de nuestras clases siguiendo el formato que nos interesa.

También hemos visto que el operador "==" funcionaba correctamente con los tipos primitivos pero no con los objetos. Dos objetos solo son iguales cuando hacen referencia al mismo objeto. Si hacen referencia a 2 objetos diferentes, aunque tengan el mismo contenido, se consideran diferentes.

![2019-01-27_10_29_00-Window](img/2019-01-27_10_29_00-Window.png)

En este caso, por ejemplo, p1 y p2 serán diferentes, hacen referencia a 2 objetos con el mismo contenido, miestras que p2 y p3 serán iguales, hacen referencia al mismo objeto.

Cuando hemos trabajado con objetos de la clase String y queríamos comparar si tenían el mismo contenido hemos usado el método equals.

Ahora vemos, que **el método equals se hereda de la clase Object y nos va a permitir comparar el estado de 2 objetos**. Podemos comparar si todos los atributos de 2 objetos son iguales pero, igual que hacíamos con toString, **tendremos que reescribirlo**.

!!! info "Debes conocer"

    Para que métodos como **cotains(Object o), indexOf(Object o) o remove(Object o)** funcionen correctamente, **equals debe estar correctamente definido** para la clase que estamos comparando.

### 7.2 Reescribir el método equals

Para reescribir el método equals se debe seguir la estructura utilizada en el siguiente ejemplo realizado para la clase punto:



```java
public boolean equals(Object o) {
    if (o instanceof Punto) {
        Punto objeto = (Punto) o;
        return x == objeto.x && y == objeto.y;
    }
    return false;
}
```



Tened en cuenta que:

- El parámetro del método equals es de la clase Object. Por ello, al hacer la llamada podemos pasarle un objeto de cualquier clase.
- Para compararlo con objetos de la clase que nos interesa hay que convertirlo a esa clase realizando un casting igual que hacíamos con números enteros y double.



```java
Punto objeto = (Punto) o;
```



- Antes de hacer el casting debemos comprobar si el objeto es de esa clase para evitar excepciones. Utilizaremos la sentencia instanceof

  

```java
  if (o instanceof Punto) {
```

  

- Podemos devolver directamente la comparación. No necesitamos un if-else.

  La versión genérica para cualquier clase quedaría:

  

  ```java
  public boolean equals(Object o) {
      if (o instanceof <clase>) {
          <clase> <name> = (<clase>) o;
          <Comparamos los atributos que nos interesan y hacemos el return>
      }
      return false;
  }
  ```

  

!!! Example "Comparación entre lenguajes: Método equals"

    === "Java"

        ```java 
        @Override 
        public boolean equals(Object o) { 
            if (o instanceof Punto) { 
                Punto p = (Punto) o; 
                return this.x == p.x && this.y == p.y; 
                } 
            return false; 
            }

        ```
    === "Python"

        ```python
        def __eq__(self, other):
            if isinstance(other, Punto):
                return self.x == other.x and self.y == other.y
            return False
        ```

    === "Kotlin"

        ```kotlin
         // En Kotlin, data classes generan automáticamente equals, hashCode, toString
        data class Punto(val x: Int, val y: Int)
        // Si no es data class:
        override 
        fun equals(other: Any?): Boolean {
            if (other is Punto) {
                return this.x == other.x && this.y == other.y
            }
            return false
        }
        ```

