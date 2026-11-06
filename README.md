# La Rioja: law history in git

Part of [lexifina/global-law](https://github.com/lexifina/global-law), one git history for every country's law: this is the law of La Rioja, Argentina, which global-law reads at `argentina/la-rioja/acts/`.

The law of the Province of La Rioja (Provincia de La Rioja, Argentina) as a git history: one file per article, one commit per norm on the day it took effect. `git log` lists the changes to an article; checking out a date gives the text the record holds for that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law), which places it at `ar-f/`. Argentina's national law is in [lexifina/argentina-law](https://github.com/lexifina/argentina-law).

The text is in Spanish, exactly as the source prints it.

## What this repository holds

1 norm so far: the constitution first, then the codes, then laws, newest first, added in parts. 1 of them are shown as enacted; the rest are their current consolidated text only (see Dates).

| Folder | Norm | History |
| --- | --- | --- |
| `constitucion/` | Constitución de la Provincia de La Rioja (reforma 2024) | as enacted, in force 19 July 2024 |

## Source

Legislatura de la Provincia de La Rioja (legislaturalarioja.gob.ar), <https://legislaturalarioja.gob.ar/consulta-de-leyes/>. The Legislatura publishes the Constitución de la Provincia de La Rioja as reformed by the Convención Constituyente 2023/2024 (sanctioned 11 July 2024) as a PDF edition with a text layer, followed by Ley 10.609 (2022), which declared the need for the reform. Its law pages give each law's sanción date and a PDF, without the publication date. The site states no terms of use for the texts.

## Dates

- Each commit is dated at **noon, America/Argentina/La_Rioja, on the day the norm took effect**: the day its own vigencia clause names, or otherwise the ninth day after its publication in the Boletín Oficial de la Provincia de La Rioja (Código Civil y Comercial de la Nación, arts. 5 and 6).
- The source publishes only today's consolidated text of each norm. A norm that no later norm is recorded as related to, and whose text carries no amendment notes, is shown as enacted. Every other norm is its current text only, the **oldest version available**, dated by the day the source last updated its record; its earlier wording is not shown.
- Versions that take effect after the retrieval day are on the `futuro` branch, never merged into `main`.

## Files

`<norm>/art-005.md` is Artículo 5, `art-005-bis.md` Artículo 5 bis; `encabezado.md` holds the number, the enacting formula and anything printed before Artículo 1. Section headings, signatures and the source's amendment notes stay in the file of the article they follow. One paragraph per line.

## How it is checked

- Every version of every norm is read back from git on the day it took effect and on the day before (`tools/check_repo.py`); both must match `corpus.json`.
- The letters and digits of every version equal those of the source document it was read from (read again with an independent HTML reader), so no word is lost or added.
- Health checks: no merge commits, commit dates never go backwards, nothing dated in the future, and every commit's trailers parse.

## Limits

This is not an official publication. The binding text is the one published in the Boletín Oficial de la Provincia de La Rioja. Only the norms listed above are included, and most show only their current text.
