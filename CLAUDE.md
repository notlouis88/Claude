# Instrucciones del proyecto

## OpenMontage + Higgsfield

`OpenMontage/` es un submódulo (https://github.com/calesthio/OpenMontage). Para producir
videos, sigue su `OpenMontage/AGENT_GUIDE.md` y usa **Higgsfield** como proveedor de
generación por defecto (imagen, video y voz). Úsalo por una de estas dos vías:

1. **Conector MCP de Higgsfield (preferida).** Herramientas `mcp__Higgsfield__*`; no
   necesita claves en el entorno.
   - Antes de generar, llama a `balance` y muestra al usuario modelo, cantidad de piezas y
     costo estimado en créditos. Genera solo con su aprobación.
   - Elige el modelo con `models_explore` (`recommend`). Para video: `seedance_2_0` o
     `kling3_0`. Para imágenes: `nano_banana_2` o `soul_2`. Para voz: `text2speech_v2`.
   - Usa `generate_*_batch` + `jobs_wait` cuando haya varias escenas.
   - Descarga cada resultado al workspace de OpenMontage:
     `OpenMontage/projects/<project-id>/assets/{video,images,audio}/` (nombres en orden de
     escena: `scene-01.mp4`, …) y regístralo en el asset manifest y en el decision log
     del proyecto (categoría `provider_selection`, subject por tipo de asset,
     proveedor `higgsfield (mcp)`).
   - El montaje, los subtítulos, la música libre y el render final los hacen las
     herramientas locales de OpenMontage (`video_compose`, `subtitle_gen`, `pixabay_music`,
     Remotion/HyperFrames).
2. **Herramienta nativa `higgsfield_video` de OpenMontage.** Se activa sola si existen
   `HIGGSFIELD_API_KEY` + `HIGGSFIELD_API_SECRET` (o `HIGGSFIELD_KEY=key:secret`) en el
   entorno. Son claves de Higgsfield Cloud (cloud.higgsfield.ai/api-keys), distintas de la
   cuenta del conector. Si están, puede usarse en lugar de la vía 1.

Si Higgsfield no tiene créditos, dilo y ofrece las alternativas gratuitas de OpenMontage
(clips de stock, imágenes generadas por código, Piper TTS) en vez de cambiar de proveedor
de pago sin preguntar. Nunca pidas ni escribas claves de API en el chat ni en archivos
versionados.

## Puesta en marcha en una sesión nueva

El contenedor es efímero. Si `OpenMontage/.venv` no existe:

```bash
git submodule update --init --depth 1 OpenMontage
cd OpenMontage && make setup
```
