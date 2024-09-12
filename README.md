# OVOS TTS Plugin - matxa-multispeaker-cat

🍵 [Matxa-TTS](https://huggingface.co/projecte-aina/matxa-tts-cat-multiaccent), the multispeaker, multidialectal neural TTS model.  It works together with the vocoder model 🥑 [alVoCat](https://huggingface.co/projecte-aina/alvocat-vocos-22khz), to generate high quality and expressive speech efficiently in four Catalan dialects:

    Balear
    Central
    North-Occidental
    Valencian

## Install

> **NOTE**: you need latest version of espeak-ng for proper [catalan support](https://github.com/espeak-ng/espeak-ng/pull/1681), depending on your distro package versions you might need to compile it from source

the plugin can be installed with pip

`pip install ovos-tts-plugin-matxa-multispeaker-cat`

## Configuration

```json
  "tts": {
    "module": "ovos-tts-plugin-matxa-multispeaker-cat",
    "ovos-tts-plugin-matxa-multispeaker-cat": {
      "voice": "valencia/gina",
    }
  }
```
voices are combinations of `accent/speaker`, valid options are:
- `balear/quim`
- `balear/olga`
- `central/grau`
- `central/elia`
- `nord-occidental/pere`
- `nord-occidental/emma`
- `valencia/lluc`
- `valencia/gina`

if voice is not set it will default to a male voice based on the language code
- `ca-ba` - `balear/quim`
- `ca-va` - `valencia/lluc`
- `ca-nw` - `nord-occidental/pere`
- otherwise - `central/grau`

## Standalone usage

```python
from ovos_tts_plugin_matxa_multispeaker_cat import MatxaCatalanTTSPlugin

sent = "Això és una prova de síntesi de veu."
tts = MatxaCatalanTTSPlugin()
tts.get_tts(sent, "test.wav", voice="valencia/gina")
```


## Credits

Both models are trained with open data; 🍵 Matxa models are free (as in freedom) to use for non-comercial purposes, but for commercial purposes it needs licensing from the voice artist.

![img.png](img.png)
> This plugin was funded by the Ministerio para la Transformación Digital y de la Función Pública and Plan de Recuperación, Transformación y Resiliencia - Funded by EU – NextGenerationEU within the framework of the project ILENIA with reference 2022/TL22/00215337

![img_1.png](img_1.png)
> 🍵 [Matxa-TTS](https://huggingface.co/projecte-aina/matxa-tts-cat-multiaccent) and  🥑 [alVoCat](https://huggingface.co/projecte-aina/alvocat-vocos-22khz) were funded by the Generalitat de Catalunya within the framework of [Projecte AINA](https://politiquesdigitals.gencat.cat/ca/economia/catalonia-ai/aina).
