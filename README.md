## Para la evaluación final de Módulo 3: Transformación de datos, he seguido los siguientes pasos:

- Recepción del enunciado y dos archivos csv el 17 de febrero
- Revisión del anunciado para apuntar dudas a alcarar en el soporte técnico el 18 de febrero
- Realización de los ejercicios sobre los dos csv
- Conversar con Rocío para resolver dudas sobre el examen y Yanelis para resolver dudas sobre el bonus
- Creación del repo con un gitignore para no subir los csv (Para poner en práctica esta técnica aprendida)
- Push de varios borradores
- Push del fichero  ya completado trás una última revisión

## Anotaciones sobre Fase 1: Exploración
- Inicialmente, hice la lectura de los csv con index_col =  0 pero como tenía que utliizar "Loyalty Number" en agrupaciones y otras operaciones, no venía bien, por lo que lo acabé quitando.
- Decidí escribir una función para buscar nulos porque era un código que repetí varias veces, y al querer mostrarlos en porcentajes, era más ágil y más limpio no tener que volver a escibir esta línea de código.
- Al descubrir un alto porcetaje de nulos en el df_flight, quise asegurar que toda la fila era duplicada, por lo que elegí un "Loyalty Number" con muchas repeticiones y mostré todas las filas. Observé que de las veces que se repetían esa "Loyalty Number", algunas veces eran datos válidos (no todas las columnas repetidas) y otras veces, eran filas repetidas que había que borrar.
- En el df_loyalty, se observaron 3 columnas con nulos y no había duplicados.
- Hice el merge de las tablas con "Loyalty Number" como llave, y conservando todos los datos de df_flight, la tabla más grande de los dos, y que todos los "Loyalty Number" estaban presentes en el otro fichero.
- Después del merge, continué con la exploración y saqué la información y estadísticas básicas sobre la tabla creada.

- ## Anotaciones sobre Fase 1: Limpieza
- Las tareas de limpieza identificadas durante la fase de exploración eran:
  - Eliminar columnas Cancellation Month y Cancellation year (debido al porcentaje de nulos)
  - Imputar los nulos en la columna 'Salary'
  - Evaluar salarios en negativo
  - Eliminar duplicados
  - Cambiar digitos a nombre de mes en las columnas de 'Month' y 'Enrollment Month' 
- Decidí imputar la columna 'Salary' con Iterative Imputer. Al tener un 25% de nulos, opté por una técnica avanzada, y elegí esa.

## Anotaciones sobre Fase 2: Visualización
1. La complicación fue ordendar el gráfico por mes. Había que utilizar la función en pandas Categorical, que convertía los meses en tipo categorical para que luego se podría especificar orden y ordenar. Se mostró el gráfico con un lineplot porque es buena opción para series temporales.
2. Mostré la correlación en un scatterplot y decidií calcular el coeficiente de correlación para avalar los datos que se observan en el gráfico.
3. Calculé con un groupby de Provincia, y contando el número de "Loyalty Number" que fueron únicos. A posteriori, me dí cuenta que podría haber sido un countplot con las veces que cada provincia aparecía en los datos. Daría el mismo resultado, pero con un código más sencillo.
4. Elegí mostrar los resultados con un barplot, que coge la media.
5. Elegí mostrar los resultados on un pieplot, ideal para calcular y mostarar proporciones. Primero había que agrupar y crear un dataframe intermedio. También había que tener en cuenta que solo contamos "Loyalty Number" que sean únicos, sabiendo que hay repetición de "Loyalty Number" en los datos.
6. Hice un groupby con dos parámetros, y lo mostré en el barplot con hue.  También me pareció interesante crear una tabla de contingencia para mostrar el porcentaje del total de clientes en cada categoria.

## Anotaciones sobre el Bonus
- Primero filtré los datos y los guardé en un dataframe
- Puse una función aggregada para poder calcular las estadísticas descriptivas todas juntas, sobre el dataframe de datos filtrados.
- La prueba estadística tenía más complicación porque me salieron 5 grupos, por tanto, cada prueba había que hacer con un bucle para evitar código repetido. Primero he creado los 5 grupos y los he guardado cada uno en una variable y luego en un diccionario con un nombre identificador.
- Apliqué el test de normalidad con un bucle, salieron todos como ditribución no normal pero con un p_value de 0.0. Mostré las distribuciones en gráfico para comprobar, se ven que no son normales. Hice pruebas con Yanelis pero salía así. He puesto las pruebas en comentarios al final de examen.
- Apliqué el test de Levene de varianza, al tratarse de datos de distribución no normal.
- Independientemente de los resultados del test Levene, apliqué el test Mann Whitney para comprobar si hubiera diferencias significativas entre los grupos. Al tratarse de 5 grupos, el bucle comparaba cada pareja de grupos. Salieron 3 grupos con una diferencia significativa, y los demás que no.
- Anotación adicional: No iba a incluir la tercera pregunta del bonus en el examen, al no sentirme muy segura pero Yanelis me ha animado a hacerlo. 
