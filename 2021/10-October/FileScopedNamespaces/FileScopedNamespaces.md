# [C# 10] File Scoped Namespaces

Seguimos repasando novedades de C# 10. En esta ocasión, vamos a centrarnos en **File Scoped Namespaces**.

## Declaración normal de namespaces (hasta ahora)

Imagina que creamos una clase Person.cs con el siguiente contenido.

```
using System;

namespace FileScopedNamespaceSample
{
    public class Person
    {
        public string Name { get; set; }
        public int Age { get; set; }
    }
}
```
La clase Person.cs se encuentra en el namespace FileScopedNamespaceSample. Cuando se observa el fragmento de código anterior, se puede ver que la declaración del espacio de nombres normal necesita un par de corchetes.

_¿Y si pudiesemos simplificar esto?_.

## File Scoped Namespaces

A continuación, veremos un fragmento de código que muestra una declaración de espacio de nombres de ámbito de archivo (File Scoped Namespace) que es posible con C# 10. 

```
using System;

namespace FileScopedNamespaceSample;
    
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}
```
Como puedes ver, después del espacio de nombres se agrega un punto y coma, y no corchetes como con una declaración de espacio de nombres clásica. Este espacio de nombres de ámbito de archivo significa que todos los tipos de este archivo, como clases e interfaces, están en el espacio de nombres FileScopedNamespaceSample.

Es posible igualmente colocar la declaración del espacio de nombres en la parte superior del archivo, encima de la directivas using.

```
namespace FileScopedNamespaceSample;
   
using System;

public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}
```

Pero no es posible colocar la declaración del namespace al final del archivo.

También es importante destacar que solo podemos declarar un espacio de nombres de ámbito de archivo por archivo. Por lo general, la mayoría de las clases C# tienen solo un espacio de nombres, por lo que no hay problema.

Pero, _¿qué sucede si deseas declarar más de un espacio de nombres en un solo archivo?_.

Esto no es algo posible con espacios de nombres de ámbito de archivo. Si intentas agregar otro espacio de nombres con ámbito de archivo en el mismo archivo, obtendrás un error en el IDE.

Los espacios de nombres de ámbito de archivo son una nueva posibilidad pequeña, pero interesante y útiles en diferentes casos.

_¿Qué te parece esta nueva funcionalidad?_. Recuerda, puedes usar los comentarios de la entrada para dejar tu feedback.

## Más información

* Documentación Microsoft: [File Scoped Namespaces](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-10.0/file-scoped-namespaces)