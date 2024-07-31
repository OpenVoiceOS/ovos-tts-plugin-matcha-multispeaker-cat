# ovos-tts-plugin-matcha-multispeaker-cat

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

`pip install ovos-tts-plugin-matcha-multispeaker-cat`

## Configuration

```json
  "tts": {
    "module": "ovos-tts-plugin-matcha-multispeaker-cat",
    "ovos-tts-plugin-matcha-multispeaker-cat": {
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
from ovos_tts_plugin_matcha_multispeaker_cat import MatchaCatalanTTSPlugin

sent = "Això és una prova de síntesi de veu."
tts = MatchaCatalanTTSPlugin()
tts.get_tts(sent, "test.wav", voice="valencia/gina")
```