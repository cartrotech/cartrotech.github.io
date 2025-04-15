---
layout: post
title:  "Qué es Arduino"
date:   2025-04-15 23:26:43 +0200
categories: arduino basico
---

### **1 - ¿Qué es y qué partes tiene Arduino?**  

#### **1.1 - Objetivos**  
- Presentar la placa Arduino.  
- Saber cómo alimentarla.  
- Diferenciar las distintas partes funcionales.  
- Saber cómo funciona Arduino.  

#### **1.2 - ¿Qué es Arduino?**  
Arduino es una plataforma de prototipado electrónico de **código abierto** (*open-source*) basada en una placa sencilla con entradas y salidas, en un entorno de desarrollo que utiliza el lenguaje de programación **Processing**. Es un dispositivo que conecta el **mundo físico con el virtual**, o el **mundo analógico con el digital**. 

<img src="/assets/images/01-01-Arduino-UNO-pines.png" alt="Arduino Uno" width="200">

#### **1.3 - Partes de un Arduino**  
El Arduino, como todo componente, está formado por diferentes partes: **entradas, salidas, alimentación, comunicación y *shields***.  

##### **1.3.1 - Entradas**  
Son los pines de la placa que podemos usar para realizar lecturas. En la placa **Uno**, son los pines digitales (0 al 13) y los analógicos (A0 a A5).  

##### **1.3.2 - Salidas**  
Los pines de salida se utilizan para enviar señales. En este caso, los pines de salida son solo los digitales (0 a 13).  

##### **1.3.3 - Otros pines**  
También hay otros pines como:  
- **GND** (tierra).  
- **5V** (proporciona 5 voltios).  
- **3.3V** (proporciona 3.3 voltios).  
- **REF** (referencia de voltaje).  
- **TX** (transmisión) y **RX** (recepción), usados para comunicación serial.  
- **RESET** (para reiniciar la placa).  
- **Vin** (para alimentar la placa externamente).  
- **ICSP** (comunicación SPI).  

##### **1.3.4 - Alimentación**  
El pin **Vin** sirve para alimentar la placa, pero lo más común es hacerlo mediante el **jack de alimentación** (7-12V). También se puede alimentar por **USB**, aunque en la mayoría de aplicaciones no estará conectado a una computadora. (Ver **Anexo 1** para más información).  

##### **1.3.5 - Comunicación**  
En los tutoriales, nos comunicaremos con Arduino mediante **USB** para cargar programas o enviar/recibir datos. Sin embargo, no es la única forma:  
- Las *shields* usan los pines **ICSP** (comunicación ISP).  
- También se usan los pines **10 a 13** (para SPI).  
- Los pines **TX/RX** o cualquier pin digital configurable como entrada/salida.  

##### **1.3.6 - *Shields***  
Son placas que se insertan sobre Arduino para ampliar sus funciones. Existen infinidad de *shields* en el mercado, como:  
- Ethernet, Wi-Fi, ultrasonidos.  
- Pantallas LCD, relés, matrices LED, GPS.  

**Estructura de Arduino:**  
- Microcontrolador principal: **Atmel AVR (8 bits)**, programable con lenguaje de alto nivel.  

**Características generales de las placas Arduino:**  
- Microprocesador **ATmega328**.  
- Memoria **Flash 32 KB** (2 KB para el *bootloader*).  
- **SRAM 1 KB**, **EEPROM 512 bytes**.  
- **Autónomo**: No necesita estar conectado al PC después de programarse.  
- Velocidad de reloj: **16 MHz**.  
- **13 pines digitales** (entrada/salida programables).  
- **5 pines de entrada analógica**, **6 salidas PWM**.  
- Voltaje de operación: **5V**.  
- Voltaje de entrada recomendado: **7-12V** (límite: 6-20V).  
- Corriente máxima por pin I/O: **40 mA**.  
- Corriente máxima en pin 3.3V: **50 mA**.  

#### **1.4 - ¿Cómo funciona Arduino?**  
Arduino es una placa basada en un **microcontrolador** (generalmente **ATMEL**), que es un circuito integrado programable.  
- Se graban instrucciones mediante un **lenguaje de programación**, permitiendo interactuar con circuitos electrónicos.  
- Tiene **entradas/salidas digitales/analógicas** y soporte para protocolos de comunicación.  
- La placa incluye todos los componentes necesarios para conectar periféricos y comunicarse con una computadora mediante **comunicación serial** (un protocolo antiguamente muy usado en puertos serie).  
