# EvidentIA

De la pregunta clínica a una búsqueda bibliográfica reproducible en PubMed y en otras fuentes. Aplicación web de un solo fichero, pensada para la asignatura «Documentación Científica Avanzada y Elaboración Práctica de un Proyecto de Investigación» (Universidad Miguel Hernández de Elche).

**Usar la app:** https://fborrasumh.github.io/evidentia/

**Idiomas:** español (por defecto), inglés y portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21519654.svg)](https://doi.org/10.5281/zenodo.21519654)

## Qué hace

1. **Pregunta y marco.** Comprueba que la pregunta está en forma interrogativa y la estructura en PICO, PICOS, PECO o SPIDER, a mano o con propuesta de la IA.
2. **Términos verificados.** Cada candidato a MeSH se comprueba en vivo contra PubMed (E-utilities): los exactos entran directamente; los que PubMed interpreta como otro descriptor se muestran con su definición oficial y la persona decide. Cada término y bloque muestra su recuento de artículos.
3. **Filtros y límites.** Diseños de estudio y edades (OR dentro de cada grupo); humanos y las tres opciones de disponibilidad del texto de PubMed —Resumen (`hasabstract`), Texto completo gratuito (`"free full text"[sb]`) y Texto completo (`"full text"[sb]`)—, cada una con AND; fecha e idioma. Todo forma parte de la ecuación.
4. **Ecuación y embudo.** La ecuación que se ejecuta es la que se entrega. Embudo con recuentos reales al añadir cada bloque. Refinado opcional con IA, que el código rechaza si añade `[All Fields]`, une conceptos con OR fuera de paréntesis o rompe la sintaxis, y avisa si desaparecen términos.
5. **Otras fuentes.** La ecuación se reescribe para la búsqueda avanzada de:
   - **Cochrane Library** (Search manager): `[mh "…"]`, `[mh ^"…"]` sin explosión, `:ti,ab,kw`, y frases truncadas con `NEXT` (Cochrane ignora el asterisco dentro de comillas).
   - **Scopus** (Advanced document search): `TITLE-ABS-KEY(…)`, `PUBYEAR >`, `LANGUAGE(…)`.
   - **Web of Science Core Collection** (Advanced search): `TS=(…)`, `PY=(…)`, `LA=(…)`.
   - **Europe PMC**: `MESH:`, `TITLE`/`ABSTRACT`, `PUB_YEAR`, `LANG`, `HAS_ABSTRACT`, `HAS_FREE_FULLTEXT`, con recuento en vivo.
   - Una versión genérica para cualquier otra base.

   El código comprueba en cada una paréntesis, comillas, operadores y que no queden etiquetas de PubMed, y lista los límites que no tienen equivalente en esa base (con cómo aplicarlos).
6. **Carga e integración de resultados.** Cada fuente tiene su botón para cargar los resultados exportados (CSV; también el TXT delimitado por tabuladores de Web of Science, Excel y RIS). Europe PMC permite traerlos directamente por su API (hasta 2.000). En el paso 6 todos los registros se integran en una sola lista, se eliminan duplicados por DOI, PMID o título con el mismo año, y cada registro indica en qué fuentes apareció. Recuento tipo PRISMA (identificados, duplicados eliminados, únicos cribados, incluidos, excluidos) y tabla por fuente.
7. **Cribado.** Incluir, excluir o dudoso, decidido por la persona. La IA (opcional) sugiere por título y resumen; el código descarta respuestas con identificadores inexistentes o valores no válidos.
8. **Anexo metodológico.** Word y PDF con la pregunta, el marco, los términos, las ecuaciones de cada fuente, la fecha, los límites, la integración, los artículos, la respuesta y la autoevaluación de la rúbrica (apartados A a D). Párrafo de métodos generado; el pulido con IA se rechaza si cambia la ecuación o introduce cifras nuevas. Exportación RIS y CSV de todas las fuentes y sesión en JSON.

Las sesiones y el historial de las versiones 5 y 6 se abren en esta versión (las decisiones de cribado se conservan).

## Cómo se usa la IA

Es opcional: sin clave se trabaja en modo manual y los ejemplos funcionan sin ella. Con la propia clave de OpenAI, Google Gemini o Anthropic Claude, guardada solo en el navegador. No hace falta servidor.

## Privacidad

La búsqueda, el historial, las claves y los archivos que se cargan se guardan y procesan solo en el navegador. A PubMed (NCBI) y Europe PMC salen los términos y las ecuaciones. Al proveedor de IA, solo si se usa, salen la pregunta, los términos y, para sugerir el cribado, títulos y resúmenes publicados; antes del primer envío se muestra una muestra de lo que sale. Los archivos cargados no salen del navegador.

## Límites

- Las ecuaciones de Cochrane, Scopus y Web of Science se generan y se comprueban por sintaxis, pero la app no puede ejecutarlas en bases de suscripción: hay que revisar el número de resultados en cada una.
- Los filtros de diseño, edad, humanos y disponibilidad del texto son propios de PubMed y no siempre tienen equivalente: la app lo indica y hay que aplicarlos con los filtros de cada base o en el cribado.
- Las ecuaciones de las otras fuentes se construyen desde los términos, filtros y límites, no desde una edición manual de la ecuación de PubMed.
- La deduplicación no detecta dos versiones de un mismo trabajo con títulos distintos y sin DOI ni PMID comunes; compara solo los registros de PubMed que se hayan traído.
- La lectura de CSV reconoce las cabeceras habituales de Scopus, Web of Science, Cochrane, PubMed y Europe PMC; si una exportación usa otras, la app indica qué columnas encontró.
- La IA puede equivocarse: propone, el código comprueba lo que puede comprobar y la decisión es de la persona.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche) y Enrique Perdiguero Gil (Universidad Miguel Hernández de Elche).

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · Enrique Perdiguero Gil [0000-0003-0870-3512](https://orcid.org/0000-0003-0870-3512)

## Cómo citar

Borrás Rocher, F. y Perdiguero Gil, E. (2026). *EvidentIA* (v7.0.0) [Software]. Zenodo. https://doi.org/10.5281/zenodo.21519654

## Licencia

MIT. Véase [LICENSE](LICENSE).
