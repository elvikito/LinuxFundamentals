# Interfaces de Usuario

Existe 2 tipos de interfaces de usuario. 

Por un lado tenemos a la interfaz de línea de comandos o CLI, y por otro lado tenemos a la interfaz gráfica o GUI.

## Es posible usar utilizar GNU/Linux sin entorno gráfico?

El entorno gráfico en su conjunto es lo que podemos decir que es lo que determina la experiencia visual de usuario. La experiencia gráfica de la que disponemos en cualquier distribución Linux es el resultado de un complejo entramado de protocolos, servicios y herramientas interdependientes, empezando por el servidor gráfico, en la capa mas baja, pasando por los gestores de ventanas, y acabando en los entornos de escritorio.

## El Servidor Gráfico

El servidor gráfico es la primera capa de software, a nivel gráfico, que interactúa con el hardware del dispositivo. Generalmente proporciona las herramientas necesarias para permitir disponer de una interfaz gráfica en Linux, pero luego debe acompañarse de otros elementos clave, como el gestor de ventanas, o el entrono de escritorio propiamente dicho.

### X Window System

X Window System es el sistema de ventanas con el que, aún a día de hoy, se basan muchas de las distribuciones GNU/Linux.

### Wayland

Wayland presenta un enfoque más limpio y eficiente que X Windows Sytem, prometiendo a la vez una mayor sencillez tanto en el desarrollo como en el mantenimiento.

## Entorno de Escritorio

Un entorno de escritorio (en inglés desktop environment) es un conjunto de software creado para ofrecer al usuario una interacción amigable y cómoda con su equipo.


### GNOME

Gnome (GNU Network Object Model Environment), este entorno de escritorio es uno de los más conocidos que no solo está presente en Linux. También se puede encontrar en otros sistemas Unix como BSD y Solaris. Tuvo su origen en los mejicanos Miguel de Icaza y Federico Mena en 1999 El objetivo de este entorno es crear un sistema de escritorio para el usuario final que sea completo, libre y fácil de usar. Usa las bibliotecas gráficas GTK y está bajo licencia GPL. Una de sus características más importantes es el poder usar varios espacios de trabajo, cada uno con un escritorio independiente de los demás.


### KDE 

KDE (KDesktop Environment) se trata de un entorno de escritorio creado en 1996 por Mathias Ettrich, se basa en el la biblioteca gráfica Qt. Este es un escritorio diseñado además para ser bonito y eso conlleva que tenga mayor consumo de recursos que GNOME. También es cierto que el mayor consumo de recursos no es exagerado, aunque si sensiblemente superior siendo más pronunciado en la carga del escritorio. Donde más evidente se nota esta diferencia es en equipos con los recursos más ajustados. Este entorno se basa en la personalización.


### Unity

Unity Es un entorno de escritorio desarrollado en Junio de 2010 por Canonical para Ubuntu.
Su primer lanzamiento se pudo ver en la versión 10.10 de Ubuntu Notebook Remix, con el objetivo de optimizar el espacio de las pantallas de los notebooks. Después de esto, en octubre de ese mismo año, se anunció que Unity se utilizaría en la versión de escritorio de Ubuntu. 

Unity técnicamente no es un entorno de escritorio, es una shell gráfica desarrollada por Canonical para Ubuntu. Unity corre por encima de un entorno de escritorio Gnome.


### XFCE

Este es un entorno de escritorio muy ligero para sistemas Unix. Según palabras de su creador Olivier Fourdan, XFCE (XForms Common Environment) está “diseñado para la productividad, las aplicaciones se cargan y se ejecutan rápidamente, mientras se conserva recursos del sistema“. Está basado en la biblioteca GTK y utiliza el gestor de ventanas Xfwm. XFCE es un entorno muy ligero, y resulta ideal para equipos como menos recursos ya que el no ser un entorno visualmente tan potente como pueden ser los anteriores, hace que no consuma tantos recursos.


### BUDGIE

Es un entorno de escritorio basado en gnome 3 con algunas instrucciones de gnome 2, lo que lo hace un entorno muy liviano pero con un look moderno, actualmente se encuentra en su versión 10.2.7 y es mantenido a través de Git-hub por el desarrollador de solus- ikeydoherty4.

