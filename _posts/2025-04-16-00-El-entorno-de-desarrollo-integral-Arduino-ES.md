---
layout: post
title: "El entorno de desarrollo integrado Arduino (IDE)"
date: 2025-04-16 23:12:43 +0200
categories: arduino basic
excerpt: "Vamos a presentar el entorno de desarrollo integrado de Arduino (IDE, nombre generado por sus siglas en inglés). Es el software que nos permite programar las placas Arduino y es necesario conocerlo para sacar todo el provecho de su potencia y características."
---

# El entorno de desarrollo integrado Arduino (IDE)

[img01]: /assets/images/ard-00-01.png "IDE Arduino"  
[img02]: /assets/images/ard-00-02.png "Barra de herramientas"  
[img03]: /assets/images/ard-00-03.png "Barra de menú"

Vamos a presentar el entorno de desarrollo integrado de Arduino (IDE, nombre generado por sus siglas en inglés). Es el software que nos permite programar las placas Arduino y es necesario conocerlo para sacar todo el provecho de su potencia y características.

El entorno de desarrollo integrado Arduino (IDE) contiene:

1. un editor de texto para escribir código,  
2. un área de mensajes,  
3. una consola de texto,  
4. una barra de herramientas con botones para funciones habituales  
5. una serie de menús.

Se conecta a las placas Arduino para cargar programas y comunicarse con ellas.

![IDE Arduino][img01]

## Escribir bocetos (sketches)

Los programas escritos con el software Arduino (IDE) se llaman bocetos o *sketches*. Estos bocetos se escriben en el editor de texto y se guardan con la extensión de archivo **.ino**. El editor tiene funciones para copiar / pegar y para buscar / reemplazar texto.

El área de mensajes proporciona comentarios mientras se guarda y exporta y también muestra errores. La consola muestra la salida de texto del software Arduino (IDE), incluidos mensajes de error completos y otra información.

En la esquina inferior derecha de la ventana se muestra la placa configurada y el puerto serie.

Los botones de la barra de herramientas te permiten verificar y subir programas, crear, abrir y guardar bocetos y abrir el monitor serie.

### Los botones de la barra de herramientas

![Barra de herramientas][img02]

- **Verificar**. Comprueba el código en busca de errores antes de compilarlo.  
- **Subir**. Compila el código y lo sube a la placa configurada.  
- **Nuevo**. Crea un nuevo boceto.  
- **Abrir**. Muestra un menú con todos los bocetos del *sketchbook*. Al hacer clic en uno, se abrirá en una nueva ventana.  
- **Guardar**. Guarda tu boceto.  
- **Monitor serie**. Abre el monitor serie.

Hay órdenes adicionales en cinco menús: **Archivo, Editar, Boceto, Herramientas, Ayuda**. Los menús son contextuales, lo que significa que solo están disponibles los elementos relevantes para el trabajo que se está realizando en ese momento.

![Barra de menú][img03]

### Archivo

- **Nuevo.** Abre una nueva ventana del editor con la estructura mínima de un boceto ya instalada.  
- **Abrir.** Permite cargar un archivo de boceto navegando por las unidades y carpetas del ordenador.  
- **Abrir reciente.** Ofrece una lista breve de los bocetos más recientes, listos para abrir.  
- **Sketchbook.** Muestra los bocetos actuales dentro de la estructura del *Sketchbook*; al hacer clic en cualquiera se abrirá en una nueva ventana del editor.  
- **Ejemplos.** Cualquier ejemplo proporcionado por el software Arduino (IDE) o por una biblioteca aparece en este elemento del menú. Todos los ejemplos están organizados en un árbol para facilitar el acceso por tema o biblioteca.  
- **Cerrar.** Cierra la ventana del software Arduino desde la que se hace clic.  
- **Guardar.** Guarda el boceto con el nombre actual. Si el archivo no tiene nombre, se proporcionará uno en la ventana "Guardar como...".  
- **Guardar como...** Permite guardar el boceto actual con un nombre diferente.  
- **Configuración de página.** Muestra la ventana de configuración de página para impresión.  
- **Imprimir.** Envía el boceto actual a la impresora según los parámetros definidos en Configuración de página.  
- **Preferencias.** Abre la ventana de preferencias, donde se pueden personalizar algunos parámetros del IDE, como el idioma de la interfaz.  
- **Salir.** Cierra todas las ventanas del IDE. Los mismos bocetos abiertos cuando se eligió *Salir* se volverán a abrir automáticamente la próxima vez que inicies el IDE.

### Editar

- **Deshacer / Rehacer.** Retrocede uno o más pasos que se hayan hecho mientras se editaba; también permite rehacer lo deshecho.  
- **Cortar.** Elimina el texto seleccionado del editor y lo coloca en el portapapeles.  
- **Copiar.** Duplica el texto seleccionado y lo coloca en el portapapeles.  
- **Copiar para el foro.** Copia el código del boceto en formato adecuado para publicarlo en el foro, con colores de sintaxis.  
- **Copiar como HTML.** Copia el código como HTML, adecuado para insertarlo en páginas web.  
- **Pegar.** Pega el contenido del portapapeles en la posición del cursor en el editor.  
- **Seleccionar todo.** Selecciona y resalta todo el contenido del editor.  
- **Ir a la línea...** Solicita e indica el cursor en una línea concreta.  
- **Comentar o descomentar.** Añade o quita los caracteres `//` al inicio de cada línea seleccionada.  
- **Aumentar / Disminuir sangría.** Añade o elimina un espacio al inicio de cada línea seleccionada.  
- **Aumentar / Disminuir tamaño de fuente.** Cambia el tamaño de la fuente del boceto.  
- **Buscar.** Abre la ventana de *Buscar y reemplazar* para buscar texto en el boceto.  
- **Buscar siguiente.** Resalta la siguiente ocurrencia del texto buscado.  
- **Buscar anterior.** Resalta la ocurrencia anterior del texto buscado.

### Boceto

- **Verificar / Compilar.** Comprueba si hay errores al compilar el boceto e informa del uso de memoria en la consola.  
- **Subir.** Compila y carga el archivo binario a la placa seleccionada.  
- **Subir usando programador.** Esto sobrescribe el *bootloader* de la placa. Tendrás que volver a grabarlo desde el menú *Herramientas > Grabar el bootloader*.  
- **Exportar binario compilado.** Guarda un archivo **.hex** que se puede conservar o cargar en la placa con otras herramientas.  
- **Mostrar carpeta del sketch.** Abre la carpeta donde se guarda el boceto actual.  
- **Incluir biblioteca.** Añade una biblioteca al boceto insertando una instrucción `#include` al principio del código. Desde este menú también se accede al gestor de bibliotecas.  
- **Añadir archivo...** Añade un archivo fuente al boceto (se copiará a la carpeta del proyecto). Aparecerá en una nueva pestaña.

### Herramientas

- **Formato automático.** Organiza bien el código: sangrías, alineación de llaves, etc.  
- **Archivar proyecto.** Guarda una copia del boceto en formato **.zip**.  
- **Corregir codificación y recargar.** Arregla discrepancias de codificación de caracteres.  
- **Monitor serie.** Abre el monitor serie e inicia el intercambio de datos con la placa conectada.  
- **Gráfica serie.** Aplicación que permite visualizar datos en forma de gráfico.  
- **Placa.** Selecciona la placa que estás usando.  
- **Puerto.** Muestra los dispositivos serie disponibles. Se actualiza automáticamente.  
- **Información de la placa.** Muestra información sobre la placa conectada.  
- **Programador.** Selecciona un programador cuando no se usa la conexión USB serie.  
- **Grabar el bootloader.** Graba un *bootloader* en el microcontrolador. Útil para microcontroladores nuevos que no lo tengan.

### Ayuda

Aquí encontrarás acceso a diversos documentos incluidos con el software Arduino (IDE). Puedes acceder a la Introducción, la Referencia, una guía del IDE y otros documentos localmente, sin conexión a Internet. Los documentos son copias locales de los documentos en línea y pueden enlazar al sitio web oficial.

**Buscar en la referencia.** Es la única función interactiva del menú Ayuda: selecciona la página correspondiente de la copia local de la referencia para la función u orden bajo el cursor.
