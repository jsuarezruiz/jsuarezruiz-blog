# [.NET 6] DateOnly y TimeOnly

Estamos muy cerca del lanzamiento de .NET, el próximo 9 de Noviembre. Así que, es un momento ideal para comenzar una nueva seria de artículos donde hablar de novedades.
En este artículo, vamos a hablar de **DateOnly** y **TimeOnly**.

![Clock](clock.jpg)

## Trabajando con fechas

Hasta ahora, para trabajar con fechas usábamos la clase DateTime. 

```
var date = new DateTime(1985, 7, 23);
var onlyDate = DateTime.Now.Date;
```
Con bastantes constructores y métodos, podíamos crear fechas de diferentes formas pero siempre trabajando con el tipo DateTime que incluye el tiempo aunque no lo necesitásemos.

De igual forma, no tenemos una forma de representar una hora del día sin incluir información de la fecha. Tenemos a nuestra disposición la clase TimesSpan que pueden representar tiempo transcurrido (2 horas, 20 minutos y 5 segundos) pero para representar una hora del día necesitamos DateTime.

## Nuevas posibilidades

Con la llegada de .NET 6 se introducen nuevas estructuras, DateOnly y TimeOnly que permiten representar fechas sin una hora del día y una hora del día sin fecha respectivamente.

```
// DateOnly is a new struct in .NET 6 that represents just a date.
DateOnly july23th = new DateOnly(1985, 7, 23);

// TimeOnly is a new type in .NET 6. Stores a time without a date.
TimeOnly tenThirtyPM = new TimeOnly(22, 30); // 22:30, or 10:30 PM
```     

## DateOnly

La nueva struct cuenta con los mismo métodos que ya existían en DateTime para modificar la fecha: **AddDays**, **AddMonths** y **AddYears**.

```
// Like with DateTime, we can add days, months, and years.
var dateOnlyFromDateTime = dateOnlyFromDateTime.AddYears(1).AddMonths(2).AddDays(15); // Apr 29th, 2001
```

DateOnly almacena los valores como un entero, donde el valor 0 corresponde al 0 de Enero, 0001. De esta forma, es posible convertir un entero a un DateOnly usando el método **FromDayNumber**.

```
DateOnly dateOnlyInteger = new(1985, 7, 23); // Jul 23th 1985
int dayNumber = dateOnlyInteger.DayNumber;
DateOnly resultFromDayNumber = DateOnly.FromDayNumber(dayNumber);
```
También es posible creat una instancia de DateOnly desde una cadena usando el método **TryParse**.

```
// We can parse like uusing DateTime with the TryParse method.
DateOnly.TryParse("01/21/2020", out DateOnly result);
```

## TimeOnly

La struct TimeOnly almacena la información usando un long que representa el número de ticks desde medianoche.

```
TimeOnly elevenTen = new TimeOnly(11, 10);
long ticks = elevenTen.Ticks;
TimeOnly timeOnlyTicks = new TimeOnly(ticks);
```

Podemos crear una instancia TimeOnly desde un DateTime usando el método FromDateTime.

```
DateTime dateTime = new DateTime(2020, 12, 12, 8, 00, 00);
TimeOnly timeOnlyFromDateTime = TimeOnly.FromDateTime(dateTime);
``` 

Podemos realizar **operaciones matemáticas** entre instancias de TimeOnly que nos devolverá como resultado un TimeSpan.

```
var afternoon = new TimeOnly(17, 00); // 5:00 PM
var morning = new TimeOnly(8, 00); // 8:00 AN
TimeSpan difference = afternoon - morning; // 9 hours
```

En general, nuevas structs que en mi opinión se integrarán facilmente con el resto de posibilidades de .NET y sobretodo será útil en tareas donde haya operaciones de serialización o bases de datos.

_¿Qué te parecen estas novedades?_. Recuerda, puedes usar los comentarios de la entrada para dejar tu opinión.

## Más Información

.NET Blog: [Date, Time, and Time Zone Enhancements in .NET 6](https://devblogs.microsoft.com/dotnet/date-time-and-time-zone-enhancements-in-net-6/)
