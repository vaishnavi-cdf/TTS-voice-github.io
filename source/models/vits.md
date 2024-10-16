# VITS

VITS (Conditional Variational Autoencoder with Adversarial Learning for End-to-End Text-to-Speech
) is an End-to-End (encoder -> vocoder together) TTS model that takes advantage of SOTA DL techniques like GANs, VAE,
Normalizing Flows. It does not require external alignment annotations and learns the text-to-audio alignment
using MAS, as explained in the paper. The model architecture is a combination of GlowTTS encoder and HiFiGAN vocoder.
It is a feed-forward model with x67.12 real-time factor on a GPU.

🐸 YourTTS is a multi-speaker and multi-lingual TTS model that can perform voice conversion and zero-shot speaker adaptation.
It can also learn a new language or voice with a ~ 1 minute long audio clip. This is a big open gate for training
TTS models in low-resources languages. 🐸 YourTTS uses VITS as the backbone architecture coupled with a speaker encoder model.

s
## VitsConfig
```{eval-rst}
.. autoclass:: TTS.tts.configs.vits_config.VitsConfig
    :members:
```

## VitsArgs
```{eval-rst}
.. autoclass:: TTS.tts.models.vits.VitsArgs
    :members:
```

## Vits Model
```{eval-rst}
.. autoclass:: TTS.tts.models.vits.Vits
    :members:
```
