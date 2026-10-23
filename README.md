# Acta de inicio de práctica — FCA UdeA
https://josefernandoguarin.github.io/FormatoActaInicio/

Aplicativo web de un solo archivo (`acta_inicio_practica.html`) para que profesores y coordinadores de práctica de la Facultad de Ciencias Agrarias de la Universidad de Antioquia diligencien el **Acta de inicio de práctica académica** y la descarguen en PDF, lista para imprimir y firmar.

---

## Requisitos

- Un navegador actualizado: Chrome, Edge, Firefox o Safari.
- Conexión a internet al abrir el archivo. El aplicativo carga desde CDN las librerías para leer Excel ([SheetJS](https://sheetjs.com/)) y generar el PDF ([jsPDF](https://github.com/parallax/jsPDF) y [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable)).
- No requiere instalación, servidor ni cuenta.

## Cómo empezar

1. Descargue `acta_inicio_practica.html`.
2. Ábralo con doble clic; se abre en el navegador predeterminado.
3. Diligencie las secciones y pulse **Descargar PDF**.

---

## Uso paso a paso

### 1. Información general
Complete la unidad académica, la dependencia, el nombre de la práctica, las fechas y los demás campos. Debajo de cada campo aparecen **en rojo** las instrucciones del formato institucional.

Algunos campos se completan solos o tienen ayudas:

- **Número de estudiantes (1.4):** se calcula automáticamente con la lista del numeral 2.1.
- **Fechas:** al ingresarlas, el aplicativo muestra cuántos días y semanas hay entre ellas, y avisa si la fecha de terminación es anterior a la de inicio.
- **Créditos, modalidad y duración:** son opcionales; si se dejan vacíos, no aparecen en el PDF.

### 2. Lista de estudiantes (2.1)

**Importar desde Excel o CSV.** Pulse **Importar Excel / CSV** o arrastre el archivo sobre la sección. Se aceptan los formatos `.xlsx`, `.xls`, `.csv` y `.ods`, y se lee la primera hoja del archivo.

El aplicativo reconoce automáticamente estos encabezados:

| Dato | Encabezados reconocidos (ejemplos) |
|---|---|
| Nombre | `Nombre completo`, `Nombres y apellidos`, `Estudiante`, o `Nombres` + `Apellidos` en columnas separadas |
| Cédula | `Cédula`, `Documento`, `Identificación`, `CC`, `ID` |
| Nivel | `Semestre`, `Nivel` |
| Horario | `Horario` |

- Si el archivo no tiene encabezados reconocibles, se asume este orden de columnas: A = nombre, B = cédula, C = nivel, D = horario.
- Los nombres en MAYÚSCULAS (como los exporta MARES) se convierten a formato de título.
- Las cédulas se limpian de puntos y espacios.
- Si ya hay estudiantes en la lista, el aplicativo pregunta si desea **reemplazarlos** o **agregar** los nuevos al final.
- Con **Descargar plantilla Excel** obtiene un archivo con las columnas esperadas.

**Editar la lista.** Todos los campos de la tabla son editables y cada fila se puede eliminar con **×**. Las **cédulas repetidas** se resaltan en amarillo.

**Valores comunes.** Escriba el *nivel de práctica* y el *horario* una sola vez y pulse **Aplicar nivel y horario a todos los estudiantes**.

### 3. Docentes, escenario y cooperador (2.2 – 2.4)
- **Docentes asesores (2.2):** agregue tantos como necesite. El campo **Rol** es el texto que aparece bajo la firma de cada docente, por ejemplo *Docente asesor/a — Pastos y forrajes*.
- **Escenario (2.3) y cooperador (2.4):** registre los datos de la finca o institución y de la persona que recibe a los estudiantes.

### 4. Propuesta de práctica (3.1 – 3.4)
Los campos de texto admiten un formato sencillo:

| Escriba al inicio de la línea | Resultado en el PDF |
|---|---|
| `## Eje 1. Diagnóstico` | Subtítulo en verde |
| `**Fase 1 — Evaluación inicial**` (la línea completa) | Línea en negrita |
| `- texto` | Viñeta |
| `1. texto` | Lista numerada |
| (texto normal) | Párrafo justificado |

**Evaluación (3.4).** Agregue los ítems con su porcentaje; el aplicativo muestra el total y avisa si no suma 100 %. El botón **Usar esquema práctica profesional** carga el esquema 30-30-30-10. Si la evaluación es cualitativa, deje la tabla vacía y descríbala en el texto.

### 5. Secciones opcionales y compromisos
- **Horarios y lugares (4):** solo aparece en el PDF si se diligencia.
- **Compromisos:** viene precargado con el texto institucional y se puede editar. Separe los párrafos con una línea en blanco. El botón **Restaurar texto institucional** recupera el original.

### 6. Firmas y anexo
- Escriba los nombres de los responsables: coordinador/a, representante del escenario y cooperador. Los docentes se toman del numeral 2.2.
- En el PDF, **las líneas de firma quedan en blanco** para firmar a mano.
- El **anexo de consentimiento informado** se genera en una página aparte. Incluye la lista de estudiantes con nombre y cédula, y una columna de firma vacía. Puede ajustar la ciudad y la fecha del anexo.

### 7. Descargar
- **Vista previa:** abre el PDF en una pestaña nueva. Si no se abre, permita las ventanas emergentes para el archivo.
- **Descargar PDF:** antes de generar el archivo, revisa los campos clave y avisa si falta alguno. El archivo se nombra así: `Acta_inicio_practica_<escenario>_<fecha>.pdf`.

---

## Escudo institucional

Con **Subir escudo para el encabezado** puede cargar una imagen PNG o JPG del escudo de la Universidad. La imagen queda guardada en el navegador y se incluye en todas las páginas del PDF. Si no se sube, el encabezado muestra solo el texto *UNIVERSIDAD DE ANTIOQUIA* en verde.

## Borradores y guardado

- **Autoguardado:** todo lo diligenciado se guarda automáticamente en el navegador. Si cierra y vuelve a abrir el archivo **en el mismo navegador y equipo**, encontrará su información.
- **Guardar borrador:** descarga un archivo `.json` con toda el acta. Úselo para cambiar de equipo, compartir el acta con otro docente o reutilizarla como base para otra práctica.
- **Abrir borrador:** carga un `.json` guardado previamente.
- **Limpiar:** borra el formulario y conserva el escudo.

> El autoguardado depende del navegador. En modo incógnito, o si se borran los datos de navegación, la información se pierde. Para trabajo importante, use **Guardar borrador**.

---

## Privacidad

Toda la información se procesa **localmente en el navegador**. Ni los datos ni los archivos de Excel se envían a ningún servidor; desde internet solo se descargan las librerías. Aun así, el acta contiene datos personales de estudiantes (nombres y cédulas), por lo que se recomienda no dejar borradores en equipos compartidos.

## Solución de problemas

| Problema | Solución |
|---|---|
| «No se pudo cargar el lector de Excel / generador de PDF» | Verifique la conexión a internet y recargue la página. |
| La importación no reconoce las columnas | Revise que la primera hoja tenga una fila de encabezados, o use la plantilla Excel. |
| La vista previa no abre | Permita las ventanas emergentes en el navegador, o use **Descargar PDF**. |
| Aparece «?» en el PDF | El texto contiene un símbolo no compatible con la fuente del PDF. Reemplácelo; los signos ≥ y ≤ se convierten automáticamente a >= y <=. |
| Perdí la información | Si no guardó un borrador `.json`, la información solo existe en el navegador donde la diligenció. |

## Estructura técnica

- Un único archivo HTML con CSS y JavaScript integrados, sin dependencias locales.
- Librerías cargadas desde cdnjs: `xlsx 0.18.5`, `jspdf 2.5.1` y `jspdf-autotable 3.8.2`.
- El PDF se genera en tamaño carta con texto real, no como imagen, así que es liviano y se puede buscar.
- La función que genera el PDF (`buildPDF`) está delimitada entre los comentarios `// ==PDF-START==` y `// ==PDF-END==` para facilitar su mantenimiento.

---

Facultad de Ciencias Agrarias · Universidad de Antioquia · Coordinación de Prácticas
