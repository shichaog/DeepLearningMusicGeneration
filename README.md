# DeepLearningMusicGeneration
State of the Art of Music Generation with Deep Learning and AI

The AI generation of text, video, and images has surged since 2023, but the advent of audio generation has been somewhat delayed. This repository tracks the latest advancements in audio generation technology. Both of closed or open sourced achievements will be included!



| model    | Sample Rate    |  Len  | Input   |  Music  |  Example  |  Infer. Time  |  Data  | Model Arch|
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| WaveNet(2016)  | 16kHz@1  | Secs | None  | Piano or speech | Piano | = Audio len. | 260 | |
| Jukebox(2020)  | 44.1kHz@1  | Mins |  Lyrics, author, etc.  | Song with the lyrics | Song | Hours | 70k | |
| RAVE(2021)  | 48kHz@2  | Secs | Latent  | Single-genre Music | Strings | = Audio len. | 100 | |
| AudioLM(2022)  Google | 16kHz@1  | Mins |  text prompt  |  Piano or speech | Piano | Mins | 40k | |

| Musika(2022)  | 22.5kHz@1  | Secs | context vector   | Single-genre Music | Piano | = Audio len. | 1k | |
| Riffusion(2022)  | 44.1kHz@1  | 5s |  Text (genre, author, etc.)  | Music of any genre  | Jazzy clarinet | Mins | - | |
| MusicLM(2023)  Google | 24kHz@2  | up to 5-Mins |  text prompt or image  |  Music | Music | - | 5.5k MusicCaps | Transformer-based multi-stage autoregressive modeling |
| AudioGen(2023) Meta | 16kHz@1  | Secs | Text (a phrase/sentence)   | Daily sounds | Dog barks | Hours | 4k | |
| Moûsai(2023)  | 48kHz@1  | Mins |  Text (genre, author, etc.) | Music of any genre lyrics | African drums | = Audio len. | 2.5k | |


## 2024 
### March 
Suno AI V3 released, v4 is already under development,
* to make full, two-minute songs in seconds
* txt to music generation
* support many styles and genres
* website https://app.suno.ai/


## 2023

### December
musicGen Meta **open sourced** https://github.com/facebookresearch/audiocraft/tree/main
AudioCraft provides the code and models for MusicGen, a simple and controllable model for music generation. MusicGen is a single stage auto-regressive Transformer model trained over a 32kHz EnCodec tokenizer with 4 codebooks sampled at 50 Hz. Unlike existing methods like MusicLM, MusicGen doesn't require a self-supervised semantic representation, and it generates all 4 codebooks in one pass. By introducing a small delay between the codebooks, we show we can predict them in parallel, thus having only 50 auto-regressive steps per second of audio. Check out our sample page or test the available demo!

* 20K hours of licensed music to train MusicGen, internal dataset of 10K high-quality music tracks, and on the ShutterStock and Pond5 music data.
* model have sizes of small(300M), medium(1.5B) and large(3.3B)

  improved from original google musicLM papers, support **Multi Band Diffusion**

SoundStream neural audio codec， SoundStream uses residual vector quantization(RVQ),

 MuLan takes the form of a two-tower, joint audio-text embedding model trained using 44 million music recordings (370K hours) and weakly-associated, free-form text annotations.

more deatils see : https://ai.meta.com/resources/models-and-libraries/audiocraft/

### August
SOUNDRAW's AI
* similar to Suno， also text prompt. https://soundraw.io/

### January

AudioLM https://arxiv.org/pdf/2209.03143.pdf 
MusicLM https://arxiv.org/pdf/2301.11325.pdf dataset 28hours music
from Goolge not open sourced now.
![image](https://github.com/shichaog/DeepLearningMusicGeneration/assets/7869827/d607bcfe-73fa-4b7d-a54e-f8ac1f4e38a8)
audio examples :
https://google-research.github.io/seanet/musiclm/examples/
https://google-research.github.io/seanet/audiolm/examples/



