# Angular

## Typescript

En typescript se puede inferir tipos. Ej:

    ```
        const username = "Ale"
        const username:string = "Ale"
    ```
Esto resulta muy útil para no tener bugs, ya que inmediatamente te avisa como error si pusiste algo mal.
Es posible poner doble tipo de tipado:

    ```
        const username:string!number = 27;
    ```
De esta manera, con el tipado tenemos feedback inmediato desde el codigo sin necesidad de ir al navegador para ver que es lo que esta fallando.

En angular es común trabajar con POO y clases (class)

    ```
        class Person {
            age:number;
            lastName:string;

            contructor(age:number;lastName:string) {
                this.age = age;
                this.lastName: lastName;
            }
        }
    ```

El this. hace referencia a un atributo de la clase. Los atributos por si solos no estan inicializados, se inicializan en el constructor.

Alguna de las cosas que se pueden realizar en angular es poner las variables mandadas por el constructor como privadas o publicas. Por ejemplo: si yo desde afuera quisiera consultar la edad o el apellido, podria hacerlo de la siguiente manera:

    ```
        const ale = newPerson(25,"Ibañez");
        <!-- realizo la consulta de la edad -->
        ale.age;
    ```

Por defecto las variables son publicas asi que no hace falta modificar nada para que esto sea asi, pero si yo quisiera ponerla como privada simplemente basta con anteponer el termino private al nombre de la variable, asi solo la clase tenga acceso a ella.

    ```
    class Person {
        private age:number;
    }
        const ale = newPerson(25,"Ibañez");
        <!-- ahora ale.age da error. solo se puede consultar dentro de la clase -->
        ale.age;

        <!-- Otra manera de realizar exactamente lo mismo pero con menos lineas es hacerlo desde el constructor -->

    class Person {
        constructor(private age:number, public lastName:string)
    }

    <!-- Declaramos y asignamos en la misma linea, pero al realizarlo de esta manera si hay que aclarar si es public o private -->
    ```

Podemos especificar que tipo de datos va a devolver la funcion de manera explicita, poniendolo luego de los parametros y antes de la flecha de arrow function

    ```
        const suma(a:number, b:number):number => {

        }
    ```

## String Interpolation

Es la forma como entre doble llave puedes implementar experesiones dentro de ellas y obtener un resultado.
Ejemplo: 

    ```
        <!-- Esto es un h1 normal -->
        <h1>Hola mundo </h1>

        <!-- El contenido es un string manipulable -->
        <h1>{{Hola mundo}}</h1>


        <!-- Otro ejemplo -->
        <p>{{3+3}}</p>
        <!-- Esto imprime 6 :o -->
    ```

Otros ejemplos:

        ```
        <!-- app.components.ts  -->

        export class appComponent {
            name:"Ale";
            age:25;
            img="link url de la img";
        }

        <!-- Si estas variables estuvieran como private no se podria -->
    ```

    ```
        <!-- app.components.html -->
        <p>Hola, soy {{name}} y tengo {{age}}</p>
    ```

## Property Binding

Property binding o enlace de propiedades ayuda a establecer valores para las propiedades HTML.
Modifica las propiedades nativas de HTML y le envia estados que estamos controlando con nuestro componente

Diferencias entre *string interpolation* y *property binding*
-property binding: es especifico para las propiedades y para manipular objetos. ([[]])
-string interpolation: es para contenido. ({{}})

Ejemplos:

    ```
        <!-- app.components.ts  -->

        export class appComponent {
            name = "ale";
            btnDisabled = true;
            age = 25;

            Person = {
                name = "Omar"
                age = 59;
                avatar = "linkImg"
            }
        }
    ```

    ```
        <!-- app.components.html  -->

        <button [Disabled]="btnDisabled">Enviar</button>

        <input type="text" [value]="name"/>

        <!-- Y ahora con los datos del objeto -->
        <input [value] = "person.name"/>
        <img src="person.avatar"/>
    ```

*En HTML se cierran los atributos con []*