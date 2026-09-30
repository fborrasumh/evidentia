# EvidentIA

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21519654.svg)](https://doi.org/10.5281/zenodo.21519654)

**Aplicación:** https://fborrasumh.github.io/evidentia/

De la **pregunta clínica** a una **búsqueda bibliográfica reproducible** en PubMed. El estudiante formula la pregunta, la estructura en PICO, PICOS, PECO o SPIDER y elige los términos. Cada descriptor MeSH se verifica en vivo contra PubMed antes de entrar en la ecuación. Después filtra, ve cuánto aporta cada elemento, compara en otras fuentes, criba los resultados y exporta un anexo metodológico alineado con la rúbrica de la asignatura *Documentación Científica Avanzada y Elaboración Práctica de un Proyecto de Investigación*. Aplicación de un solo fichero (`index.html`), sin servidor.

## Novedades de la versión 6.0

**Correcciones que afectan a los resultados**

- **Filtros bien combinados.** En la v5 todos se unían con OR: marcar «Ensayo clínico aleatorizado» y «Solo humanos» producía `(RCT[pt] OR Humans[Mesh])`. Ahora los diseños de estudio se combinan con OR entre sí, igual que las edades, y el resto de límites con AND.
- **La ecuación entregada es la ejecutada.** La fecha y el idioma forman parte de la ecuación, del embudo y del anexo, que además registra la fecha de la búsqueda.
- **Compatibilidad.** Las sesiones de la v5 se abren y su ecuación se reconstruye, con aviso para repetir la búsqueda. El historial se conserva y ahora se ordena por fecha.

**Mejoras**

- Recorrido guiado con el estilo de Forja, con comprobación en vivo de la forma interrogativa que exige la rúbrica.
- **Recuento en PubMed de cada término y de cada bloque**; un cero se marca como posible errata.
- **Opciones MeSH** [Majr] y sin explosión, y truncamiento en texto libre.
- **17 filtros** en tres grupos: diseño (incluye cualitativa y precisión diagnóstica), edad y otros límites.
- **Embudo** con el nombre de cada elemento y aviso de bloques demasiado restrictivos. La edición manual se valida: paréntesis, OR sueltos, [All Fields] y operadores en minúscula.
- **Otras fuentes**: la ecuación traducida a Scopus, Web of Science y Cochrane, y el recuento real en Europe PMC.
- **Cribado del estudiante**, con sugerencias opcionales de la IA; recuento tipo PRISMA; orden por relevancia o fecha; «cargar más»; exportación **RIS** y CSV.
- **Anexo**: rúbrica siempre visible, párrafo de métodos con fecha y cribado, y protección para que la IA no altere la ecuación al mejorar la redacción. Exportación a Word, PDF y JSON.
- **Cuatro ejemplos resueltos**, uno por marco (PICO, PICOS, PECO y SPIDER), verificados en vivo contra PubMed.

## Verificación MeSH

Ningún descriptor entra por la palabra de la IA. Cada candidato se comprueba contra el campo `[MeSH Terms]` de PubMed:

- **coincidencia exacta**: se añade;
- **interpretado como otro descriptor** (p. ej., *effectiveness* → *Treatment Outcome*): se muestra su definición oficial de la NLM y el estudiante decide;
- **inexistente**: pasa a texto libre con una nota.

## Privacidad

Todo se guarda en el navegador (IndexedDB y `localStorage`). La clave de OpenAI es opcional (modo manual sin IA) y es la compartida del catálogo (`ia_openai_key`). Las consultas van a PubMed (NCBI) y Europe PMC.

## Cómo citar

Borrás Rocher, F. (2026). *EvidentIA* (versión 6.0.0) [Software]. Universidad Miguel Hernández de Elche. https://doi.org/10.5281/zenodo.21519654

El DOI es el de concepto: apunta siempre a la última versión. GitHub ofrece la cita en APA y BibTeX con el botón *Cite this repository*, a partir de `CITATION.cff`.

Forma parte del catálogo [Herramientas IA para la academia](https://fborrasumh.github.io/ia/).

## Licencia

MIT © 2026 Fernando Borrás Rocher · Universidad Miguel Hernández de Elche.
