# JavaTutorial
Los Tutoriales de Java son guías prácticas para programadores que desean usar el lenguaje de programación Java para crear aplicaciones. Incluyen cientos de ejemplos completos y de trabajo, y docenas de lecciones. Los grupos de lecciones relacionadas se organizan en "senderos".

## 0. Configurar Github en el entorno de Eclipse

[Tutorial](https://www.youtube.com/watch?v=Y4ca4CSdMsI)

## 1. Getting Started

Ejemplo HelloWorldApp.java

```java
package gettingStarted;

/**
 * The HelloWorldApp class implements an application that
 * simply prints "Hello World!" to standard output.
 */

public class HelloWorldApp {
	
	/**
     * @param args the command line arguments
     */
	public static void main(String[] args) {
		System.out.println("Hello World!"); // Display the string
	}

}

```

## 2. Object-Oriented Programming Concepts

#### Contenido del capitulo

* ¿Qué es un Object?
* ¿Qué es una Class?
* ¿Qué es la Inheritance?
* ¿Qué es una Interface?
* ¿Qué es un Package?

### ¿QUÉ ES UN OBJETO?

Los objetos son clave para comprender *la tecnología orientada a objetos*. Los objetos del mundo real comparten dos características: todos tienen *estado* y *comportamiento*.  Los perros tienen estado (nombre, color, raza, hambre) y comportamiento (ladrar, buscar, mover la cola). Identificar el estado y el comportamiento de los objetos del mundo real es una excelente manera de comenzar a pensar en términos de programación orientada a objetos.

Los objetos de software son conceptualmente similares a los objetos del mundo real: también consisten en estado y comportamiento relacionado ( Figura 2.1 ). Un objeto almacena su estado en *campos (fields)* (variables en algunos lenguajes de programación) y expone su comportamiento a través de *métodos* (funciones en algunos lenguajes de programación). Los métodos operan en el estado interno de un objeto y sirven como el mecanismo principal para la comunicación de objeto a objeto. El acto de ocultar el estado interno y requerir que toda la interacción se realice a través de los métodos de un objeto se conoce como *encapsulación de datos*, un principio fundamental de la programación orientada a objetos.

<img src="https://github.com/adolfodelarosajava/JavaTutorial/blob/master/imgDocumenacion/concepts-object.gif" />

**Figura 2.1** Un objeto de software

Por ejemplo, consideremos una bicicleta ( Figura 2.2 ). Al atribuir el estado (velocidad actual, cadencia actual del pedal y marcha actual) y proporcionar métodos para cambiar ese estado, el objeto mantiene el control de cómo el mundo exterior puede usarlo. Por ejemplo, si la bicicleta solo tiene seis marchas, un método para cambiar de marchas podría rechazar cualquier valor que sea menor que uno o mayor que seis.

<img src="https://github.com/adolfodelarosajava/JavaTutorial/blob/master/imgDocumenacion/concepts-bicycleObject.gif" />

**Figura 2.2** Una bicicleta modelada como un objeto de software

La agrupación de código en objetos de software individuales proporciona una serie de beneficios, que incluyen los siguientes:

1. *Modularidad*. El código fuente de un objeto se puede escribir y mantener independientemente del código fuente de otros objetos. Una vez creado, un objeto se puede pasar fácilmente dentro del sistema.

2. *Ocultar información*. Al interactuar solo con los métodos de un objeto, los detalles de su implementación interna permanecen ocultos del mundo exterior.

3. *Reutilización del código*. Si ya existe un objeto (quizás escrito por otro desarrollador de software), puede usar ese objeto en su programa. Esto permite que los especialistas implementen, prueben y depuren objetos complejos específicos de tareas, en los que puede confiar para ejecutar en su propio código.

4. *Enchufabilidad y facilidad de depuración*. Si un objeto en particular resulta problemático, simplemente puede eliminarlo de su aplicación y conectar un objeto diferente como su reemplazo. Esto es análogo a la solución de problemas mecánicos en el mundo real. Si se rompe un tornillo, debe reemplazar ese tornillo en particular, no toda la máquina.

### ¿QUÉ ES UNA CLASE?

En el mundo real, a menudo encontrarás muchos objetos individuales, todos del mismo tipo. Puede haber miles de otras bicicletas en existencia, todas de la misma marca y modelo. Cada bicicleta se construyó con el mismo conjunto de planos y, por lo tanto, contiene los mismos componentes. En términos orientados a objetos, decimos que su bicicleta es una instancia de la clase de objetos conocidos como bicicletas. Una clase es el plano a partir del cual se crean los objetos individuales.

La siguiente clase `Bicycle` es una posible implementación de una bicicleta:

```java
class Bicycle {

    int cadence = 0;
    int speed = 0;
    int gear = 1;

    void changeCadence(int newValue) {
        cadence = newValue;
    }

    void changeGear(int newValue) {
        gear = newValue;
    }

    void speedUp(int increment) {
        speed = speed + increment;
    }

    void applyBrakes(int decrement) {
        speed = speed - decrement;
    }

    void printStates() {
        System.out.println("cadence:" +
            cadence + " speed:" +
            speed + " gear:" + gear);
    }
}
```

Los campos `cadence`, `speed` y `gear` representan el estado del objeto, y los métodos (tales como `changeCadence`, `changeGear`, y `speedUp`) definen su interacción con el mundo exterior.

Es posible que haya notado que la clase `Bicycle` no contiene un método `main`. Eso es porque no es una aplicación completa; Es solo el modelo para las bicicletas que podrían usarse en una aplicación. La responsabilidad de crear y usar nuevos objetos `Bicycle` pertenece a alguna otra clase en su aplicación.

Aquí hay una clase `BicycleDemo` que crea dos objetos `Bicycle` separados e invoca sus métodos:

```java
class BicycleDemo {
    public static void main(String[] args) {

        // Create two different
        // Bicycle objects
        Bicycle bike1 = new Bicycle();
        Bicycle bike2 = new Bicycle();

        // Invoke methods on
        // those objects
        bike1.changeCadence(50);
        bike1.speedUp(10);
        bike1.changeGear(2);
        bike1.printStates();

        bike2.changeCadence(50);
        bike2.speedUp(10);
        bike2.changeGear(2);
        bike2.changeCadence(40);
        bike2.speedUp(10);
        bike2.changeGear(3);
        bike2.printStates();
    }
}
```

El resultado de esta prueba imprime la cadencia, la velocidad y la marcha del pedal final para las dos bicicletas:

```
cadence:50 speed:10 gear:2
cadence:40 speed:20 gear:3
```

### ¿QUÉ ES LA HERENCIA?

