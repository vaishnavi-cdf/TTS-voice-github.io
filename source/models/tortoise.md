# 🐢 Tortoise
Tortoise is a very expressive TTS system with impressive voice cloning capabilities. It is based on an GPT like autogressive acoustic model that converts input
text to discritized acoustic tokens, a diffusion model that converts these tokens to melspectrogram frames and a Univnet vocoder to convert the spectrograms to
the final audio signal. The important downside is that Tortoise is very slow compared to the parallel TTS models like VITS.

Big thanks to 👑 who helped us implement Tortoise in 🐸TTS.

Example use:

```python
from TTS.tts.configs.tortoise_config import TortoiseConfig
from TTS.tts.models.tortoise import Tortoise

config = TortoiseConfig()
model = Tortoise.init_from_config(config)
model.load_checkpoint(config, checkpoint_dir="paths/to/models_dir/", eval=True)

# with random speaker
output_dict = model.synthesize(text, config, speaker_id="random", extra_voice_dirs=None, **kwargs)

# cloning a speaker
output_dict = model.synthesize(text, config, speaker_id="speaker_n", extra_voice_dirs="path/to/speaker_n/", **kwargs)
```

Using 🐸TTS API:

```python
from TTS.api import TTS
tts = TTS("tts_models/en/multi-dataset/tortoise-v2")

# cloning `lj` voice from `TTS/tts/utils/assets/tortoise/voices/lj`
# with custom inference settings overriding defaults.
tts.tts_to_file(text="Hello, my name is Manmay , how are you?",
                file_path="output.wav",
                voice_dir="path/to/tortoise/voices/dir/",
                speaker="lj",
                num_autoregressive_samples=1,
                diffusion_iterations=10)

# Using presets with the same voice
tts.tts_to_file(text="Hello, my name is Manmay , how are you?",
                file_path="output.wav",
                voice_dir="path/to/tortoise/voices/dir/",
                speaker="lj",
                preset="ultra_fast")

# Random voice generation
tts.tts_to_file(text="Hello, my name is Manmay , how are you?",
                file_path="output.wav")
```

Using 🐸TTS Command line:

```console
# cloning the `lj` voice
tts --model_name  tts_models/en/multi-dataset/tortoise-v2 \
--text "This is an example." \
--out_path "output.wav" \
--voice_dir path/to/tortoise/voices/dir/ \
--speaker_idx "lj" \
--progress_bar True

# Random voice generation
tts --model_name  tts_models/en/multi-dataset/tortoise-v2 \
--text "This is an example." \
--out_path "output.wav" \
--progress_bar True
```


## Important resources & papers
- Original Repo: https://
- Faster implementation: 
- Univnet: 
- Latent Diffusion:
- DALL-E: 
## TortoiseConfig
```{eval-rst}
.. autoclass:: TTS.tts.configs.tortoise_config.TortoiseConfig
    :members:
```

## TortoiseArgs
```{eval-rst}
.. autoclass:: TTS.tts.models.tortoise.TortoiseArgs
    :members:
```

## Tortoise Model
```{eval-rst}
.. autoclass:: TTS.tts.models.tortoise.Tortoise
    :members:
```
