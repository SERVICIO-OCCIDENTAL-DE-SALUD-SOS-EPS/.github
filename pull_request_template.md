Desarrollador: nombre.apellido@sos.com.co

<!--
Obligatorio: reemplazar por el correo corporativo SOS de quien desarrollo el cambio (varios, separados
por coma). Sin esta linea con un correo real, la revision automatica no revisa el PR.
-->

## Que cambia

<!-- Que hace este PR y por que. Tarjeta o incidencia relacionada, si la hay. -->

## Acceso a datos

<!--
Solo si el PR toca consultas, SP o datasources. Regla vigente:
- Cero SP nuevos. Lo que no reusa un SP del legado va por JDBC en el micro, paginado en la base
  (helper SosJdbcPaginator de com.sos:sos-platform-web-starter 1.1.0 o superior).
- Un espejo _op solo para reusar un SP del legado: indicar aqui que SP reusa y por que no se puede
  pasar a JDBC en el micro.
- Escrituras (insert, update, delete) tambien por JDBC con SQL explicito: transaccion en el caso de
  uso, clave generada con KeyHolder u OUTPUT INSERTED, verificar filas afectadas y batchUpdate para
  lotes. Si el legado escribe con un SP con logica de negocio, se llama ese SP tal cual, sin ALTER.
- Sin JPA en codigo nuevo, ni para leer ni para escribir. Un dato de otro dominio se lee y se
  escribe por HTTP al micro dueno.
-->

## Como se probo

<!-- Tests agregados o ajustados, y verificacion manual si aplica. -->
