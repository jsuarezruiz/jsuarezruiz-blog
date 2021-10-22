# Bordes personalizados en .NET MAUI

Aplicar bordes personalizados es una necesidad bastante común utilizada en el diseño de aplicaciones para crear estructuras visuales concretas, resaltar elementos o poder personalizar ciertos controles específicos.

En Xamarin.Forms el control **Frame** ha sido ampliamente utilizado con este fin. Sin embargo, el control Frame contaba con ciertas limitaciones:
- No poder personalizar cada esquina del borde.
- No poder personalizar el ancho del borde.
- No poder utilizar brushes en el propio borde.
- Etc.

Con la Preview 9 de .NET MAUI llega un nuevo control, Border, con bastantes más posibilidades y con el objetivo de resolver todas las limitaciones que teníamos hasta ahora. _¿Lo revisamos en este artículo?_.

## Nuevo control Border

El nuevo control Border, similar en concepto al Frame, es un control que permite un único elemento como contenido pero que puede ser cualquier cosa. Es decir, podremos aplicar un Border desde a un sencillo Label a un Grid con un layout complejo.

![.NET MAUI Border](maui-border.gif)

_¿Qué te parece esta novedad en .NET MAUI?_. Recuerda, puedes usar los comentarios de la entrada para dejar tu feedback.

## Más información

* .NET Blog: [Announcing .NET MAUI Preview 9](https://devblogs.microsoft.com/dotnet/announcing-net-maui-preview-9/)