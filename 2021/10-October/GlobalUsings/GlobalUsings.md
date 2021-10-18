# [.NET 6] Global Usings

Una de las novedades más sonadas quizás por ser un cambio del que estoy seguro tendrá desarrolladores a favor y otros en contra. En este artículo, vamos a hablar de la llegada de **Global Usings**.

## Declarar usings hasta ahora

En la parte superior de todas las clases C# hay una colección de instrucciones using que especifican los espacios de nombres que la clase necesita para compilar:

```
using System;

namespace GlobalUsingsSample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Global Usings!");
        }
    }
}
```

Cuando en el mismo proyecto tenemos diferentes clases haciendo uso de las mismas APIs, aparecen **duplicadas** en instrucciones using.

Es cierto que Visual Studio puede colapsar los usings, pero, ¿y si se pueden gestionar de otra forma?.

## Global Usings

C # 10 permite hacer uso de la palabra **global** para poder identificar namespaces que deberían aplicarse a toda nuestra aplicación:

```
global using System;

// The previous using statements will be included in every class in this project.
```

Estas declaraciones pueden colocarse en un archivo en cualquier lugar del proyecto, y el compilador de C# sabrá que tiene que aplicar estos namespaces a nivel de aplicación.

De esta forma:

```
namespace GlobalUsingsSample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Global Usings!");
        }
    }
}
```

No hay namespaces a nivel de la clase!. Pero..._¿y si añades un namespace a nivel de clase que ya se encuentra a nivel global?_. Visual Studio avisará de este caso con un warning.

## Más información

* .NET Documentation: [Global Using Directive](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-10.0/globalusingdirective)