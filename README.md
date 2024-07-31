# OVOS TTS Plugin - matxa-multispeaker-cat

🍵 Catalan [Matxa-TTS](https://huggingface.co/projecte-aina/matxa-tts-cat-multispeaker) is based on matxa-TTS that is an encoder-decoder architecture designed for fast acoustic modelling in TTS. The encoder part is based on a text encoder and a phoneme duration prediction that together predict averaged acoustic features. And the decoder has essentially a U-Net backbone inspired by Grad-TTS, which is based on the Transformer architecture. In the latter, by replacing 2D CNNs by 1D CNNs, a large reduction in memory consumption and fast synthesis is achieved.

## Install

install espeak with catalan phonemizer support, a binary should be placed at `/usr/local/lib/libespeak-ng.so`

```bash
git clone https://github.com/projecte-aina/espeak-ng
cd ./espeak-ng
./autogen.sh
./configure
make
sudo make install
```

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

![img.png](img.png)
> This work is funded by the Ministerio para la Transformación Digital y de la Función Pública and Plan de Recuperación, Transformación y Resiliencia - Funded by EU – NextGenerationEU within the framework of the project ILENIA with reference 2022/TL22/00215337
