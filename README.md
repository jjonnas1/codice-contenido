# codice-contenido

Contenido remoto de **El Códice: Derecho Colombiano**, la app de Castellanos Abogados ([jonatancastellanosabogado.com](https://jonatancastellanosabogado.com)).

La app descarga `codice-contenido.json` en segundo plano y lo aplica la siguiente vez que se abre. Así llegan preguntas nuevas, casos, paquetes de concursos y correcciones sin publicar una versión nueva en la tienda.

## Reglas

- Cada publicación **sube `version`** (1, 2, 3…). Si el número no sube, la app no descarga nada.
- `esquema` es 1. Una app ignora un archivo con un esquema mayor al que entiende.
- Solo entra contenido **aprobado por el abogado** (decisión "A" en el Word de revisión).
- Si el archivo no existe, está dañado o no hay internet, la app sigue con lo que ya tiene.

## Formato

| Campo | Qué hace |
|---|---|
| `nota` | Texto corto que la app muestra como novedad (opcional) |
| `agregar` | Preguntas nuevas del Tomo I |
| `tomo2` | Preguntas nuevas del Tomo II (con `etapa`) |
| `casos` | Casos simulados nuevos o actualizados |
| `concursos` | Preguntas por paquete: `{ "rama": [...], "procuraduria": [...] }` |
| `corregir` | `{ "id": "...", campos que cambian }` |
| `retirar` | Ids de preguntas que se quitan del juego |
| `terminos` | Términos procesales para el juego «Términos» (desde la versión 1.1.0 de la app): `{ "id", "area", "actuacion", "plazo", "opciones"?, "nota"?, "article", "source", "sourceUrl" }`. El juego aparece con 10 o más. |
| `concursoInfo` | Datos que cambian de cada concurso (desde la 1.1.0): `{ "procuraduria": { "fecha": "AAAA-MM-DD", "estado": "..." } }`. Con `fecha`, la app muestra la cuenta regresiva y programa avisos. Solo fechas oficiales. |
