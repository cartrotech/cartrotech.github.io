---
layout: post
title: "14 - Módulo de zumbador activo"
date: 2025-05-02 12:00:00 +0200
categories: arduino acutadores
excerpt: "Aprender a utilizar el zumbador. Incluir avisos sonoros en nuestros circuitos."
---

## Finalidad

- Aprender a utilizar el zumbador
- Incluir avisos sonoros en nuestros circuitos

## Material

|                               Imagen                               | Descripción                |
| ---------------------------------------------------------------- | ------------------------ |
| ![Arduino](/assets/images/material/mat_unor3.png)  | Arduino Uno o equivalente. |
| ![Cables](/assets/images/material/mat_cables.png) | Cables de conexión        |
| ![Zumbador](/assets/images/material/mat_KY012.png) | Un zumbador activo KY012  |

## Descripción del material

Los zumbadores electrónicos funcionan con corriente continua y están
equipados con un circuito integrado. Se utilizan ampliamente en ordenadores,
impresoras, fotocopiadoras, alarmas, juguetes electrónicos,
dispositivos electrónicos de automoción, teléfonos, temporizadores y otros
productos electrónicos para generar avisos. Los zumbadores se pueden
clasificar como activos y pasivos.

El módulo de zumbador activo KY-012 produce un sonido de un solo tono cuando la
señal es alta. Para producir diferentes tonos se utiliza el módulo de
zumbador pasivo KY-006.

El módulo KY-012 consiste en un zumbador piezoeléctrico activo, que
genera un sonido de aproximadamente 2,5 kHz cuando la señal es alta.

| Característica               | Valor                                 |
| ---------------------------- | ------------------------------------- |
| Voltaje de funcionamiento     | 3,5V ~ 5,5V                           |
| Corriente máxima             | 30mA / 5VDC                           |
| Frecuencia de resonancia     | 2500Hz ± 300Hz                        |
| Salida mínima de sonido      | 85Db @ 10cm                           |
| Temperatura de trabajo       | -20 °C ~ 70 °C [-4 °F ~ 158 °F]   |
| Temperatura de almacenamiento | -30 °C ~ 105 °C [-22 °F ~ 221 °F] |
| Dimensiones                  | 18,5 mm x 15 mm                       |

## Montaje

Conecte la señal (S) al pin 8 del Arduino y el negativo (-) a GND.
Tenga en cuenta que algunos módulos están mal etiquetados. Pruebe
de invertir los cables si no escucha ningún sonido mientras ejecuta el código.

![Montaje](/assets/images/ard/ard_14_01.png)
![Esquema eléctrico](/assets/images/ard/ard_14_02.png)

## Programación

```Arduino

/*
 * CARTROTECH  (https://cartrotech.github.io)
 * 
 * Proyecto nº: ARD_14
 * Descripcion: Aprender a utilizar el zumbador. Incluir avisos sonoros en nuestros circuitos.
 * 
 * Fecha: 2025-05-03
 */

int buzzerPin = 8;

void setup()
{
  pinMode(buzzerPin, OUTPUT);
}

void loop()
{
  digitalWrite(buzzerPin, HIGH);
  delay(500);
  digitalWrite(buzzerPin, LOW);
  delay(500);
}
```

## Conceptos importantes

- La importancia de recibir avisos fuera del alcance de la visión
