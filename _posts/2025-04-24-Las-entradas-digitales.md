---
layout: post
title: "Las entradas digitales"
date: 2025-04-24 16:00:00 +0200
categories: arduino basic
excerpt: "La finalidad de esta lección es conocer las entradas digitales y aprovecharemos para leer un pulsador. Presentaremos los valores booleanos y un operador: Negación."
---

[img1]: /assets/images/ard/ard_03_01.jpg "Esquema eléctrico"
[img2]: /assets/images/ard/ard_03_02.jpg "Montaje"

## Objetivos

La finalidad de esta lección es conocer las entradas digitales y aprovecharemos para leer un pulsador. Presentaremos los valores booleanos y un operador: Negación.

## Material requerido

| Elemento | Descripción |
|----------|-------------|
| ![Arduino Uno](/assets/images/material/mat_unor3.png) | Arduino Uno o compatible |
| ![Protoboard](/assets/images/material/mat_protoboard.png) | Una protoboard |
| ![Cables](/assets/images/material/mat_cables.png) | Cables de connexión |
| ![LED](/assets/images/material/mat_led.png) | Un diodo led |
| ![Resistencia](/assets/images/material/mat_resis330.png) | Dos resistencias 330 Ohms |
| ![Pulsador](/assets/images/material/mat_polsador.png) | Un pulsador              |

## Entradas digitales

Frecuentemente en electrónica necesitamos saber si una luz está encendida o apagada, si alguien ha pulsado un botón o si una puerta ha quedado abierta o cerrada.

A este tipo de señales se les llama digitales, y podemos manejarlas con los pines de 0 al 13 de Arduino y por eso hablamos de pines digitales.

Muchos de los sensores y actuadores que vemos en el mundo real son digitales:

- _Como actuadores digitales, tenemos luces, alarmas, sirenas, desbloqueo de puertas, etc._
- _Como sensores digitales podemos mencionar botones y pulsadores, Finales de carrera, desbordamiento de nivel, sensores de llamas, humo o gases tóxicos._

Hemos visto que Arduino puede usar los **pines digitales** como salidas todo o nada para encender un LED. De la misma manera podemos leer valores, todo o nada, del mundo exterior.

En esta lección veremos que los **pines digitales** de Arduino pueden ser usados tanto de entrada como de salida. Leeremos un botón o pulsador externo y encenderemos o apagaremos un LED en función de que el botón se presione o no.

## Esquema electrónico del circuito

Montaremos un circuito con un diodo LED y resistencia conectado al pin digital 10 de Arduino, tal como vimos en las lecciones previas y además un segundo circuito con un pulsador S1 conectado al pin 6 con una resistencia como se muestra en el diagrama siguiente.

!["Esquema eléctrico"][img1]

Obsérvese que mientras no presionamos S1 el pin 6 de Arduino está conectado a 5V a través de la resistencia R3 forzando una lectura de tensión alta (HIGH). En cambio cuando presionamos S1 cerraremos el circuito del pin 6 a negativo con lo que leerá tensión baja, LOW. En ambos casos tenemos un valor de tensión definido.

Si no pusiéramos la resistencia R3, al presionar S1 leeríamos correctamente LOW en el pin 6. Pero al dejar de presionar S1 el pin 6 estaría en un estado flotante, que es ni HIGH ni LOW sino indeterminado. Como esto es inaceptable en circuitos digitales forzamos una lectura alta con R3.

- _A esta resistencia que fuerza el valor alto en vacío se le conoce como **pullup.** Si la conectáramos a masa para forzar una lectura a negativo se diría **pulldown.**_
- _Esta resistencia es clave para que las lecturas del pulsador sean consistentes. El circuito, simplemente, no funcionará bien si se omite (volveremos sobre esto)._

Y aquí tenemos el esquema para protoboard del circuito.

![Montaje][img2]

- _En este esquema hemos seguido la práctica habitual de usar cables negros para conectar a masa y cables rojos para conectar a tensión (5V)._
- _Obsérvese que el pulsador S1 tiene cuatro pines (el que está sobre la resistencia horizontal). Esto es porque cada entrada del interruptor tiene dos pines conectados. En nuestro circuito simplemente ignoramos los pines secundarios._

## Leyendo los pulsadores

Empecemos haciendo un programa que haga que el LED se encienda cuando presionamos el botón y se apague cuando lo soltamos. Para esto pediremos a Arduino que configure el pin digital 10 (D10) como salida para manejar el LED, y el pin digital 6 (D6) como entrada para leer el botón.

Normalmente en programas sencillos basta con poner el número de pin en las instrucciones. Pero a medida que el programa se complica esto tiende a provocar errores difíciles de detectar.

Por eso es costumbre definir **variables** con los números de pin que usamos, de manera que podamos modificarlos tocando en un solo lugar (y no teniendo que buscar a lo largo del programa). Escribiremos esto un poco más elegantemente:

```Arduino
int LED = 10;
int boton = 6;

void setup()
{
pinMode(LED, OUTPUT); // LED como salida
pinMode(boton, INPUT); // botón como entrada
}
```

- _Atención: C++ diferencia entre mayúsculas y minúsculas y por tanto LED, Led y led no son lo mismo en absoluto. De la misma manera, pinMode es correcto y en cambio pinmode generará un error de compilador fulminante._
- _He usado la variable boton sin acento porque no es recomendable usarlos ni la ñ en los nombres de variables, porque pueden pasar cosas extrañas._

Vimos que para encender el LED bastaba usar `digitalWrite(LED, HIGH)`. Para leer un botón se puede hacer algo similar: `digitalRead(boton)`. Veamos cómo podría ser nuestro **loop**:

```Arduino
void loop()
{
int valor = digitalRead(boton); // leemos el valor de boton en valor
digitalWrite(LED, valor);
}
```

¿Fácil no? Aunque el LED está encendido hasta que presionamos el botón y se apaga al presionar.

¿Cómo podríamos hacer lo contrario, que el LED se encienda al presionar y se apague si no? Bastaría con escribir en LED lo contrario de lo que leemos en el botón.

Existe un operador que hace esto exactamente, el operador **negación** **" ! "** . Si un valor dado **x** es HIGH, entonces **!x** es LOW y viceversa.

- _Un operador es un símbolo que relaciona varios valores entre sí, o que modifica el valor de una variable de una manera previsible._
- _Ejemplos de operadores en C++ son los matemáticos como +,-,* , / ; y hay otros como la negación ! o el cambio de signo de una variable : -- x. Iremos viendo más._

De hecho este tipo de operaciones son tan frecuentes que C++ incorpora un tipo llamado **bool** o **booleano** que solo acepta dos valores TRUE (verdadero) y FALSE (falso) y son completamente equivalentes al 1/0, y al HIGH/LOW.

Este nuevo programa sería algo así:

```Arduino
void loop()
{
bool valor = digitalRead(boton); // leemos el valor de boton en valor
digitalWrite(LED, !valor); // Escribimos valor contrario en LED
}
```

Hemos definido valor como bool, porque podemos usar el valor de tensión alta como TRUE y el valor bajo como FALSE. Si el botón no está presionado el D6 leerá TRUE y por tanto pondrá LED a FALSE. En caso contrario encenderá el LED.

```Arduino
void loop()
{
bool valor = digitalRead(LED);
digitalWrite(LED, !valor);
delay(1000);
}
```

De hecho podríamos escribir una variante curiosa del blinking LED usando el operador negación, en solo dos líneas:

- _Podemos leer la situación actual de un pin (nos retorna su estado actual), aunque lo hayamos definido como salida. En cambio no podemos escribir en un pin definido como entrada._

```Arduino
void loop()
{
digitalWrite(LED, !digitalRead(LED));
delay(1000);
}
```

- La primera línea lee la situación del LED y la invierte, después escribe eso en LED.
- _Las instrucciones dentro de los paréntesis se ejecutan antes que las que están fuera de ellos. Por eso el digitalRead se ejecuta antes que el digitalWrite._

## Resumen de la lección

- Hemos visto una manera de leer señales digitales en Arduino del mundo exterior además de poder enviarlas:
  - digitalRead(pin)
  - digitalWrite(pin, valor)
- Hemos conocido un nuevo componente: el pulsador.
- Conocemos un nuevo tipo en C++, el booleano y un nuevo operador de negación.
