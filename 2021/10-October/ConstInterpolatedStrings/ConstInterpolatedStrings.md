# [C# 10] Const Interpolated Strings

Continuamos hablando de novedades de C# 10. En esta ocasión hablaremos de **cadenas interpoladas constantes**, nueva funcionalidad que llega para hacer que nuestro código sea más legible y más conciso.

## Concatenar cadenas constantes hasta ahora

Cuando usamos cadenas constantes en C# 9.0 y versiones anteriores, solo podíamos concatenarlas usando el **operador +**: 

```
const string Scheme = "https"; 
const string Home = "home";

const string Environment = Scheme + "://localhost:5002";const string HomeUri = Environment + "/" + Home;
```

## Nuevas posibilidades

Con la llegada de C# 10, ahora podemos usar el **operador de cadena interpolada $** para combinar cadenas constantes:

```
const string Scheme = "https"; 
const string Home = "home";

const string Environment = $"{Scheme}://localhost:5002";
const string HomeUri = $"{Environment}/{Home}";
```

**NOTA:** Es importante tener en cuenta acerca de esta función es que solo funciona si todas las cadenas utilizadas en la cadena interpolada están marcadas const.

_¿Qué te parece este añadido?_. Recuerda que puedes usar los comentarios de la entrada para dejar tu feedback.

## Más información

* Documentación .NET: [Constant Interpolated Strings](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-10.0/constant_interpolated_strings)