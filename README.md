# ED_AD3
Actividad 3: Diagramas UML
1.	Introducción

Este trabajo tiene como objetivo diseñar y desarrollar un sistema de gestión de torneos de eSports, aplicando los principios de la Programación Orientada a Objetos (POO) y utilizando diagramas UML para modelar su funcionalidad y estructura interna. El modelo elegido se basa en una estructura de eliminación directa, en la cual el equipo ganador avanza automáticamente a la siguiente ronda. Este formato es ampliamente utilizado en competiciones reales de eSports por su simplicidad y agilidad, lo que lo convierte en una elección adecuada para una primera versión funcional del sistema.

2.	Análisis del problema y requisitos

Pregunta 1: ¿Quiénes son los actores que interactúan con el sistema?

•	   Administrador del sistema
Es el actor principal del sistema. Se encarga de la gestión completa de los torneos, los equipos y los jugadores. Tiene acceso total a todas las funcionalidades del sistema.
•	Agente de equipo
Representante de uno o varios equipos participantes. Su rol principal es registrar y gestionar equipos, inscribirlos en torneos y administrar los jugadores que forman parte de dichos equipos.
•	Jugador
Puede registrarse en el sistema de forma individual. Sin embargo, su perfil tiene acceso limitado, permitiéndole únicamente consultar información como torneos, partidas, resultados y datos de su equipo.
Pregunta 2: ¿Cuáles son las acciones que cada actor puede realizar?
•	Administrador del sistema
- Registrar equipo: crear una cuenta en el sistema para un equipo determinado
- Registrar jugador: crear una cuenta en el sistema para un jugador determinado
- Consultar lista de equipos y jugadores: visualiza todos los equipos y jugadores registrados en el sistema
- Crear torneo: define nombre, fecha, formato y número máximo de participantes.
- Gestionar inscripción: inscribe o elimina equipos manualmente en un torneo.
- Generar emparejamiento: escoger 2 equipos para que se enfrenten en una partida.
- Registrar resultados: introduce los resultados de enfrentamientos entre jugadores.
- Actualizar Clasificación: actualiza información de la clasificación según los resultados de las partidas 

•	Agente de equipo
-  Registrar equipo: crear una cuenta en el sistema para un equipo determinado, en este caso tiene que ser representado por él
-  Registrar jugador: crear una cuenta en el sistema para un equipo determinado, en este caso tiene que formar parte de un equipo representado por él
-   Gestionar equipo: añadir jugadores a sus equipos representados, eliminar jugadores de sus equipos representados, etc.
-   Inscribir equipo: inscribir un equipo representado por él en un torneo determinado
-  Consultar estadística: accede a estadísticas de los torneos, equipos y jugadores

•	Jugador
-	Registrarse: crea una cuenta personal en el sistema.
-	Consultar torneos: visualiza los detalles de torneos.
-	Consultar equipo: consultar la información de su equipo actual
-	Consultar partidas: consulta las partidas por jugar (por ejemplo, contra qué equipo y cuándo juega).
-	Consultar resultados: revisa los resultados de sus partidas.

Pregunta 3:  ¿Cómo se relacionan entre sí las entidades del sistema?

<img width="870" alt="Screenshot 2025-04-25 at 10 37 52" src="https://github.com/user-attachments/assets/48724992-32f1-4a3d-af30-2ce1e4d621d0" />

3.	Identificación de los casos de uso y elaboración del diagrama
Se ha elaborado un diagrama de casos de uso que representa las funcionalidades principales del sistema en relación con la gestión de equipos y jugadores, en concreto: registrar equipo, añadir jugadores a un equipo y consultar lista de equipos y jugadores.
Los actores involucrados son:
•	Administrador del sistema, con permisos globales.
•	Agente de equipo, con acceso restringido a los equipos que representa.
Los casos de uso incluidos son:
•	Registrar equipo
Ambos actores pueden registrar equipos, pero el agente solo puede registrar los equipos que representa (relación <<extend>>).
•	Registrar jugador
Similar al anterior, el administrador puede registrar cualquier jugador, mientras que el agente solo puede registrar jugadores dentro de sus propios equipos (<<extend>>).
•	Consultar lista de jugadores / equipos
Los dos actores pueden consultar listas, pero el agente solo accede a la información de los equipos y jugadores que representa (<<extend>>).
•	Añadir un jugador a un equipo
Ambos pueden realizar esta acción, pero con limitaciones según el rol. Este caso de uso incluye la verificación previa de que tanto el equipo como el jugador estén registrados (<<include>>).
En resumen, el diagrama muestra cómo el sistema adapta sus funcionalidades según el tipo de usuario, reutilizando acciones generales (como registrar o consultar) y extendiendo sus variantes específicas según el contexto de uso.

![UML_caso-2](https://github.com/user-attachments/assets/9ae23af6-d488-4bab-9c04-dcfbf0a61251)

4.	Identificación de clases y relaciones (basado en punto 2) y creación del diagrama de clases UML
Se ha identificado las clases y relaciones que representan la estructura del sistema de gestión de equipos y jugadores en un torneo de eSports, aplicando los principios de la Programación Orientada a Objetos. A partir de alli, se ha desarrollado un diagrama de clases UML.
El diseño se compone de tres tipos de clases:
•	Clases de entidad (Equipo, Jugador, Agente): representan los elementos principales del sistema. Cada equipo está asociado a un agente y puede tener múltiples jugadores. Las clases incluyen atributos básicos como nombre, email, y métodos que permiten listar, añadir o eliminar jugadores.
•	Clase de control (ControlEquipos): centraliza la lógica del sistema y contiene las listas de entidades (Equipo, Jugador, Agente). Define métodos para registrar equipos y jugadores, gestionar relaciones entre entidades, y consultar información.
•	Clases de interfaz (UIRegistrarEquipo, UIRegistrarJugador, UIAñadirJugador, UIConsultarDatos): son responsables de la interacción con el usuario. Cada una se vincula a ControlEquipos y permite ejecutar acciones como mostrar formularios o consultar datos registrados.
El modelo sigue una estructura modular y escalable, que facilita la separación de responsabilidades y la futura ampliación del sistema. Además, refleja fielmente la lógica de negocio real del dominio de los torneos eSports, con una gestión clara y controlada de los actores y sus relaciones.
<img width="576" alt="Screenshot 2025-04-25 at 10 39 46" src="https://github.com/user-attachments/assets/d924dfff-5a1a-4188-8440-bee12f9d22c4" />

Relaciones entre clases:
•	Asociación:
Jugador — Equipo (muchos a uno)
Equipo — Agente (muchos a uno)
ControlEquipos — Equipo, Agente y Jugador (uno a muchos)
•	Dependencia:
Todas las clases UI dependen de ControEquipos.
![Diagrama_clase](https://github.com/user-attachments/assets/492a68d0-148a-4755-ad88-cef5a2720c0b)

5.	Reflexiones finales
El desarrollo de este sistema de gestión de torneos de eSports ha permitido aplicar de forma práctica los principios de la Programación Orientada a Objetos (POO) y el uso de diagramas UML como herramientas fundamentales para el análisis y diseño de software. A través del modelado de actores, casos de uso y clases, se ha logrado representar con claridad la lógica del sistema, sus funciones principales y las relaciones entre sus componentes.
Uno de los aspectos más valiosos del diseño ha sido la división clara de responsabilidades entre clases de entidad, control e interfaz, lo cual ha facilitado una estructura modular, escalable y fácil de mantener. Además, la incorporación de distintos roles (administrador, agente y jugador) ha permitido reflejar un escenario realista y adaptable a diferentes contextos de uso.
Durante el proceso, se ha reforzado la importancia de una planificación previa al desarrollo, así como el valor de diseñar sistemas pensando tanto en la funcionalidad como en la experiencia del usuario. También ha quedado patente que una buena organización interna del software no solo mejora su comprensión, sino que prepara la base para futuras mejoras o integraciones.
En resumen, el trabajo ha sido una oportunidad enriquecedora para integrar conocimientos técnicos con la capacidad de análisis, y demuestra cómo un diseño bien estructurado puede dar lugar a soluciones robustas y realistas para contextos como el de los eSports.





