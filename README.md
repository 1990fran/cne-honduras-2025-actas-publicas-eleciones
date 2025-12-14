# ACTAS_CNE

Colección de actas escaneadas y datos numéricos extraídos del Visor de Resultados del Consejo Nacional Electoral (CNE) de Honduras para las elecciones generales de 2025. La carpeta agrupa las actas por departamento, municipio, área (urbana/rural), centro de votación y Junta Receptora de Votos (JRV), preservando la jerarquía administrativa oficial para que sea sencillo ubicar cada documento.

## Organización de carpetas

- `ACTAS_<DEPARTAMENTO>` (18 carpetas) → nombre y código del departamento según el CNE.
- `<código_municipio>_<municipio>` → subcarpetas de cada municipio del departamento.
- `01_URBANA` / `02_RURAL` → la zona que reporta el acta.
- `<código_centro>_<centro de votación>` → nombre del centro (escuela, instituto, etc.).
- `<JRV>` → carpeta final que contiene los archivos capturados para esa JRV.

Ejemplo abreviado:

```
ACTAS_CNE/
└── ACTAS_ATLANTIDA/
    └── 001_LA CEIBA/
        └── 01_URBANA/
            └── 001_BO. LA ISLA - CENTRO EVANGELICO BETHEL/
                └── 6973/
                    ├── 6973_acta.png
                    └── 6973_candidatos.json
```

## Archivos por JRV

Cada carpeta de JRV puede contener una o varias de las siguientes piezas:

- `<JRV>_acta.png` / `<JRV>_acta.jpg` / `<JRV>_acta.pdf`: copia exacta del acta publicada por el CNE. Predominan las imágenes PNG; en algunos casos sólo se pudo capturar PDF.
- `<JRV>_candidatos.json`: conteos de votos por candidatura presidencial reportados por el visor en el momento de la descarga. El formato es un diccionario simple, por ejemplo:

```json
{
  "MARIO ENRIQUE RIVERA CALLEJAS": 0,
  "RIXI RAMONA MONCADA GODOY": 0,
  "JORGE NELSON AVILA GUTIERREZ": 0,
  "SALVADOR ALEJANDRO CESAR NASRALLA SALUM": 0,
  "NASRY JUAN ASFURA ZABLAH": 0
}
```

- En algunos centros aún no se ha podido capturar el acta; en esos casos sólo está el JSON de candidatos. Conforme se reintenten las descargas, aparecerá el archivo del acta junto al JSON.

## Estadísticas rápidas

- 18 departamentos (`ACTAS_ATLANTIDA` … `ACTAS_YORO`).
- 19 082 archivos `*_candidatos.json`.
- 17 610 actas en imagen (`*_acta.png`). Algunas JRVs cuentan con PDF o están pendientes de captura.

> **Tip GitHub:** este volumen de archivos pesa varios gigabytes. Si vas a publicar todo en un repositorio público, considera Git LFS o dividir el histórico por departamentos para evitar límites de tamaño.


## Buenas prácticas al compartir

- Incluye esta carpeta tal como está para conservar la trazabilidad de cada acta.
- Añade notas en el README principal del repositorio indicando la fecha de la última descarga y cualquier script modificado.
- Si automatizas nuevas ejecuciones, documenta los parámetros utilizados (p. ej. `--depto-id`, filtros de municipios) para facilitar auditorías.

Con este README tendrás el contexto necesario para que cualquier persona pueda navegar las actas, identificar rápidamente dónde está cada archivo y, si lo desea, reproducir el proceso de descarga.
