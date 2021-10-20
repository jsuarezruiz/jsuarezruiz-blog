## Más novedades de .NET 6, PriorityQueue 

Diría que es hasta sorprendente tras ver durante años diferentes implementaciones de PriorityQueue incluidas algunas usadas interamente en Frameworks de Microsoft, que nunca ha existido algo público directamente expuesto en .NET. Esto ha sido así hasta la llegada de .NET 6. En este artículo vamos a conocer las posibilidades de **PriorityQueue**.

## Queue

Para explicar las novedades introducidas vamos a crear una pequeña clase que nos permita trabajar con personas.

```
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}
```

Vamos a comenzar trabajando con **Queue**. Se trata de una estructura de datos genérica en la que los elementos se recuperan en el orden en que se añaden.

```
var persons = new Queue<Person>();

persons.Enqueue(new Person() { Name = "Javier" });
persons.Enqueue(new Person() { Name = "David" });
persons.Enqueue(new Person() { Name = "Pedro" });
persons.Enqueue(new Person() { Name = "Jesus" });
```

Vamos a utilizar el método TryDequeue que quita el elemento situado al principio y lo copia en el parámetro de salida.

```
while (persons.TryDequeue(out var person))
{
    Console.WriteLine($"{person.Name}");
}
```

La salida será algo como:
* Javier
* David
* Pedro
* Jesus

Justo lo que esperábamos y ya conocíamos, elementos ordenados obteniendo en cada momento el primero del principio de la colección.

Ahora imagina que quieres utilizar otro criterio para priorizar el orden en el que aparecen los elementos, independientemente del orden en que se pongan en cola.

Digamos que en nuestro ejemplo, cada persona tiene una edad y queremos ordenar usando ese criterio.

## PriorityQueue

Podemos usar la nueva clase PriorityQueue con ese objetivo, usar otro criterio para priorizar.

Añadimos varias personas a un PriorityQueue:

```
var prioritizedAgents = new PriorityQueue<Person, int>();

prioritizedAgents.Enqueue(new Person() { Name = "Javier" }, 36);
prioritizedAgents.Enqueue(new Person() { Name = "David" }, 45);
prioritizedAgents.Enqueue(new Person() { Name = "Pedro" }, 41); 
prioritizedAgents.Enqueue(new Person() { Name = "Jesus" }, 33);
```

Como podemos ver en el ejemplo anterior, se especifica el tipo a añadir en la cola y un segundo tipo, que se usarará para la priorización.

En nuestro caso, tenemos una cola de personas y la prioridad es la edad donde se usa un int.

```
while (prioritizedAgents.TryDequeue(out var person, out var age))
{
    Console.WriteLine($"{person.Name}, age {age}");
}
```

¿Cuál es el resultado?

* Jesus, age 33
* Javier, age 36
* Pedro, age 41
* David, age 45

Las personas ordenadas por edad. Hay que tener en cuenta el orden relativo a como se añadieron a la cola. Al priorizar,**un valor más bajo otorga una prioridad más alta**.

Por supuesto, el tipo utilizado para definir la prioridad no tiene que ser un número; puede ser cualquier cosa que implemente **IComparer**.

Estamos ante una novedad excelente para problemas en los que las estructuras de datos se procesan según el orden y además otro parámetro que otorga prioridad.

## Más información

* Documentación .NET: [PriorityQueue](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.priorityqueue-2?view=net-6.0)