## Curso SQL Y Mysql
### como hacer una base de datos
- 1.-Se mira el problema a solucionar
- 2.-Encontramos entidades ejemplo:carro = rectangulos
- 2.1 atributos ejempl:color = redondeadod
- 2.2 relaciones = rombo
- 2.3 sub atributos = redondeados pequeños
- 2.4 identificamod ID Y FK = subrayamos
- 3. cardinalidades 1 a 1 1 a * o * a **
- 4.- Normalizamos 5FN
- 5..-Diagrama relacional
<p align="center"><img src="https://i.ibb.co/93jMYBv/img041.jpg" width="700" height="400"></p>
<p align="center"><img src="https://i.ibb.co/JrSFQbL/img042.jpg" width="400" height="700"></p>
<p align="center"  ><img src="https://i.ibb.co/4sK67Nw/img043.jpg" width="400" height="700" ></p>
<p align="center"  ><img src="https://i.ibb.co/gM3BrZ5/img044.jpg" width="400" height="700" ></p>

a normalización en las bases de datos relacionales es uno de esos temas que, por un lado es sumamente importante y por el otro suena algo esotérico. Vamos a tratar de entender las formas normales (FN) de una manera simple para que puedas aplicarlas en tus proyectos profesionales.

Primera Forma Normal (1FN)
Esta FN nos ayuda a eliminar los valores repetidos y no atómicos dentro de una base de datos.

Formalmente, una tabla está en primera forma normal si:

Todos los atributos son atómicos. Un atributo es atómico si los elementos del dominio son simples e indivisibles.
No debe existir variación en el número de columnas.
Los campos no clave deben identificarse por la clave (dependencia funcional).
Debe existir una independencia del orden tanto de las filas como de las columnas; es decir, si los datos cambian de orden no deben cambiar sus significados.
Se traduce básicamente a que si tenemos campos compuestos como por ejemplo “nombre_completo” que en realidad contiene varios datos distintos, en este caso podría ser “nombre”, “apellido_paterno”, “apellido_materno”, etc.

También debemos asegurarnos que las columnas son las mismas para todos los registros, que no haya registros con columnas de más o de menos.

Todos los campos que no se consideran clave deben depender de manera única por el o los campos que si son clave.

Los campos deben ser tales que si reordenamos los registros o reordenamos las columnas, cada dato no pierda el significado.

Segunda Forma Normal (2FN)
Esta FN nos ayuda a diferenciar los datos en diversas entidades.

Formalmente, una tabla está en segunda forma normal si:

Está en 1FN
Sí los atributos que no forman parte de ninguna clave dependen de forma completa de la clave principal. Es decir, que no existen dependencias parciales.
Todos los atributos que no son clave principal deben depender únicamente de la clave principal.
Lo anterior quiere decir que sí tenemos datos que pertenecen a diversas entidades, cada entidad debe tener un campo clave separado. Por ejemplo:
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.30.27-e38ed9bb-5d10-4f2b-acdc-fa2fa45433d3.jpg" width="700" height="300"></p>
En la tabla anterior tenemos por lo menos dos entidades que debemos separar para que cada uno dependa de manera única de su campo llave o ID. En este caso las entidades son alumnos por un lado y materias por el otro. En el ejemplo anterior, quedaría de la siguiente manera:
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.26.28-2a12f9b9-2f11-4a1d-9cb0-23c2595cc260.jpg" width="700" height="300"></p>
Tercera Forma Normal (3FN)
Esta FN nos ayuda a separar conceptualmente las entidades que no son dependientes.

Formalmente, una tabla está en tercera forma normal si:

Se encuentra en 2FN
No existe ninguna dependencia funcional transitiva en los atributos que no son clave

Esta FN se traduce en que aquellos datos que no pertenecen a la entidad deben tener una independencia de las demás y debe tener un campo clave propio. Continuando con el ejemplo anterior, al aplicar la 3FN separamos la tabla alumnos ya que contiene datos de los cursos en ella quedando de la siguiente manera.
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.27.43-92a1523a-c6fc-42e6-85fb-86dd87ee20af.jpg" width="700" height="300"></p>
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.27.52-cb96ff88-e8f4-4957-8bbb-ded1cc6cf599.jpg" width="700" height="300"></p>
Cuarta Forma Normal (4FN)
Esta FN nos trata de atomizar los datos multivaluados de manera que no tengamos datos repetidos entre rows.

Formalmente, una tabla está en cuarta forma normal si:

Se encuentra en 3FN
Los campos multivaluados se identifican por una clave única
Esta FN trata de eliminar registros duplicados en una entidad, es decir que cada registro tenga un contenido único y de necesitar repetir la data en los resultados se realiza a través de claves foráneas.

Aplicado al ejemplo anterior la tabla materia se independiza y se relaciona con el alumno a través de una tabla transitiva o pivote, de tal manera que si cambiamos el nombre de la materia solamente hay que cambiarla una vez y se propagara a cualquier referencia que haya de ella.
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.29.00-ba58de30-a08d-472a-82f9-ea478bf6fcee.jpg" width="700" height="300"></p>
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.29.29-149d96f3-78e4-4a26-8c4a-0f002c81cc2f.jpg" width="700" height="300"></p>
De esta manera, aunque parezca que la información se multiplicó, en realidad la descompusimos o normalizamos de manera que a un sistema le sea fácil de reconocer y mantener la consistencia de los datos.

Algunos autores precisan una 5FN que hace referencia a que después de realizar esta normalización a través de uniones (JOIN) permita regresar a la data original de la cual partió.
<p align="center"><img src="https://i.ibb.co/6DyPVqk/img045.jpg" width="400" height="700"></p>
<p align="center"><img src="https://i.ibb.co/VHZZnLT/img046.jpg" width="400" height="700"></p>
<p align="center"><img src="https://i.ibb.co/Zf8cmgf/img047.jpg" width="400" height="700"></p>

##Rastrear cambios en una base de datos
https://www.sqlshack.com/es/como-rastrear-el-historial-de-cambios-de-datos-usando-tablas-temporales-con-versiones-del-sistema-en-sql-server-2016/
