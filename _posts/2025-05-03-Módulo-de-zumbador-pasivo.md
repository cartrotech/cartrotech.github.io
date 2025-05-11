---
layout: post
title: "Módulo de zumbador pasivo"
date: 2025-05-03 10:00:00 +0200
categories: arduino actuadores
excerpt: "Aprender a utilizar el zumbador. Incluir avisos sonoros en nuestros circuitos."
---

## Finalidad

- Aprender a utilizar el zumbador
- Incluir avisos sonoros en nuestros circuitos

## Material

| Imagen | Descripción  |
| ------ | ------------ |
| ![Arduino Uno](/assets/images/material/mat_unor3.png) | Arduino Uno o equivalente.  |
| ![Cables](/assets/images/material/mat_cables.png)     | Cables de conexión          |
| ![Zumbador](/assets/images/material/mat_KY006.png)    | Un zumbador pasivo KY-006   |

## Descripción

### ¿Qué es?

Un zumbador es un transductor electroacústico que produce un sonido continuo
o intermitente de un mismo tono, generalmente agudo. El zumbador transforma
la señal eléctrica que recibe en una vibración, que genera un ruido. Cuanto
más alta es la señal que recibe, más intensa es la vibración y más fuerte es
el sonido.

### Especificaciones

El módulo de zumbador pasivo (KY-006) puede generar tonos entre 1.5 a 2.5
kHz al encenderlo y apagarlo en diferentes frecuencias usando retrasos o
PWM.

| Característica            | Valor           |
| ------------------------- | --------------- |
| Voltaje de funcionamiento  | 1,5 ~ 15 V CC   |
| Rango de generación de tonos | 1,5 ~ 2,5 kHz   |
| Dimensiones                | 18,5 mm x 15 mm |

### ¿Cómo funciona?

El funcionamiento se basa en el efecto piezoeléctrico de los materiales.
Este efecto funciona de tal manera que cuando aplicamos un voltaje, el
volumen del material cambia ligeramente. Los zumbadores están construidos
con dos pequeñas placas, una metálica y una cerámica, las cuales
aprovechan este efecto pero solo generan un clic ya que los materiales
cambian de forma pero no vuelven a su estado natural hasta que se les
quita el voltaje.

![Efecto piezoeléctrico](/assets/images/ard/ard_15_01.png)

Para que se pueda emitir un sonido continuo, las placas necesitan vibrar
constantemente. Para esto se necesita un oscilador que hace que los
materiales cambien de estado una vez y otra, y así puedan cambiar
miles de veces para poder conseguir un audio perceptible.

En este caso lo conseguiremos cambiando el estado de una salida digital de
la placa Arduino. Recordemos que el sonido es audible desde 20 Hz hasta 20
kHz, por tanto, el número de veces que la salida debe cambiar (llamado
frecuencia) estará entre 20 y 20000 veces por segundo.

![Montaje del zumbador](/assets/images/ard/ard_15_02.png)
![Esquema eléctrico](/assets/images/ard/ard_15_03.png)

El montaje lo haremos directamente con cables tipo Dupont M-F, conectando
la salida 8 con la S (señal) del zumbador y por otra parte el pin GND
de la placa con el pin « -- « del módulo.

![Montaje final](/assets/images/ard/ard_15_04.png)

## Programación

Código: ARD_15

```Arduino

/*
CARTROTECH  (https://cartrotech.github.io)

Proyecto nº: ARD_15
Descripcion: Aprender a utilizar el zumbador. Incluir avisos sonoros en nuestros circuitos.

Fecha: 2025-05-04
 */

int buzzer = 8; // establece el pin digital de control del zumbador

void setup()
{
  pinMode(buzzer, OUTPUT); // configura el pin 8 como salida
}

void loop()
{
  for (int i = 0; i < 80; i++) // crea un sonido de 500 Hz
  {
    digitalWrite(buzzer, HIGH); // envía señal alta al zumbador
    delay(1); // delay 1ms
    digitalWrite(buzzer, LOW); // envía señal baja al zumbador
    delay(1);
  }
  delay(50);

  for (int j = 0; j < 100; j++)  //crea un sonido de 250 Hz
  {
    digitalWrite(buzzer, HIGH);
    delay(2); // delay 2ms
    digitalWrite(buzzer, LOW);
    delay(2);
  }
delay(100);
}
```

## Conceptos importantes

- Efectos de los activadores acústicos
- Entender qué es la frecuencia
