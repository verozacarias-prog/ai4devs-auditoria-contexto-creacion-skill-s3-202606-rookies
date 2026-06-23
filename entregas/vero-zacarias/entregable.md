# Entregable · Sesión 3 — Copilotos IA

- **Nombre / usuario:** Veronica Zacarias
- **Fecha de entrega:** 23/06/2026
- **Repo auditado en la Parte A** Proyecto personal, backend. Sistema de biblioteca implementado como dos microservicios independientes.  TypeScript / Node 20 y Go 1.21. Antiguedad: 2 semanas
---

## 1. Hallazgos de la auditoría (Parte A)

> 3-5 cosas que el agente **no pudo inferir** del código y que tendrías que decirle explícitamente.
-NO DETECTO COMO INICIAR EL PROYECTO SIN BORRAR LA BASE DE DATOS, PARA MANTENER LOS DATOS
-NO ESPECIFICA QUE TIPO DE USUARIOS SE PUEDEN CREAR Y QUE FUNCIONALIDAD PUEDE ACCEDER CADA TIPO DE USUARIO
-NO DETECTO LOS SCRIPTS DE CARGA INICIAL DE INFORMACION EN LAS BASES DE DATOS Y SCRIPTS DE PRUEBA DE LOS ENDPOINTS
-NO MENCIONA COMO VER LA DOCUMENTACION SWAGGER
-NO MENCIONA CI para git
-NO DETECTO QUE JWT_SECRET nunca se debe commitear
> Redáctalas para que otra persona las entienda sin contexto adicional. **Sin código propietario ni secretos.**

1. El proyecto se inicializa con docker compose, lo cual crea las bases de datos vacias. Para no tener que estar insertando informacion entre cada prueba, se configuro docker compose para tener la opcion de no eleminar y recrear la base de datos entre pruebas locales.
2. El sistema maneja dos tipos de usuario, admin, que puede realizar todas las operaciones, crud de libros y crud de prestamos. Y usuario normal, "user", que solo puede ver los libros que hay y sus propios prestamos
3. El repositorio tiene archivos de tipo scripts, que inicializa las base de datos con informacion mock, y otro que hace llamadas a todas las apis indicando el status code esperado, probando todos flujos de disponibles.
4. El repositorio tiene configurado el CI minimo para hacer commits en git.
5. Nunca se debe commitear JWT_SECRET

---

## 2. SKILL.md de la skill creada (Parte B)

> Pega aquí el contenido completo de tu `.claude/skills/endpoints-documentation/SKILL.md`
> (o enlaza al archivo en tu repositorio sandbox).

```markdown
---
description: Documentar endpoints expuestos y listas endpoint documentados. Usar cuando el usuario pida documentar los endpoints.
---

## Instructions

Documentar con swagger todos los endpoints expuestos del sistema. Solo los que son accesibles desde un cliente del sistema. No los endpoints de uso interno. Agregar la documentacion a todos los endpoint que no lo tengan. Revisar los que si ya tengan la documentacion, que sea coherente con el codigo. Y al finalizar, listar los endpoinst que fueron documentados y/o actualizados.

---

## 3. Diario de decisiones

*Skill creada:* endpoints-documentation: documentar endpoint con swagger

*Decisiones de diseño tomadas:*
- Decisión 1: qué use swagger, porque es la documentacion mas usada
- Decisión 2: que documente solo los expuestos, no funciones internas.
- Decisión 3: que ademas de documentar nuevos, revise coherencia de los ya documentados.

*Qué me resultó fácil:*
-el nombre de la skill y el prompt a utilizar

*Qué me resultó ambiguo o difícil de decidir:*
- tuve problemas con la ubicacion de la skill, porque queria que sea para todos los proyectos, no me la reconocia. Tuve que poner el archivo fuera del scope de git. En este escenario la skill no podria ser subida en un repo general de skills si quisiera que sea compartida en un entorno de trabajo. A diferencia de las skills a nivel proyecto que esas pueden ser subidas en el mismo repo del proyecto.

*Tiempo real invertido:*
- total: 1 hora con 30 min aprox, 
-lectura previa: 1 hora
-diseño: 15 min 
-escritura: 5 min

*Qué probarías si tuvieras más tiempo:*
-La estructura mas definida, deshabilitar la opcion para que solo se pueda usar invocandola, y a que recursos tendria acceso. Tambien mejorarla con IA

*¿Usaste IA para crear la skill?* No, no use IA. Me base en experiencia real de cuando tuve que crear la documentacion del proyecto.
-

### Resultado de la prueba (Paso 8)

- ¿Se activó cuando lo esperabas?
Si, se activo cuando pedi documentar el proyecto, no lo llame con "/endpoints-documentation"
- ¿El resultado fue el que querías?
Si, documento y tambien detecto diferencias en lo que ya habia documentado.
- Si no, ¿qué crees que falló? (no la "arregles" — documenta el primer intento)
