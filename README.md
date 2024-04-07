# DeepLearningMusicGeneration
State of the Art of Music Generation with Deep Learning and AI， mainly focus on text to music generation.

# why need AIGC music

1. Personalized Music Composition: Music generation models may become increasingly adept at creating personalized music based on a user’s emotions and preferences.
2. Music Accompaniment Applications: With the demand from industries such as gaming, film, and advertising, music generation models can provide real-time, automated background scores for these media.
3. Music Education and Compositional Aid: Music generation technology can help musicians and composers come up with new musical ideas, or be used in music education to demonstrate compositional techniques.
4. Interactive Performance: Using music generation models in live performances to interact with the audience and create a unique performance experience.
5. Music Analysis and Reconstruction: Utilizing models to analyze the style of musical works and reconstruct or generate new pieces based on that analysis.

Chinese of above
1. 个性化音乐创作：音乐生成模型可能会越来越擅长根据用户的情绪和喜好创作个性化的音乐。
2. 音乐伴随应用：随着游戏、电影、广告等行业的需求，音乐生成模型可以为这些媒介提供实时、自动化的配乐。
3. 音乐教育和辅助作曲：音乐生成技术可以帮助音乐家和作曲家提出新的音乐想法，或者用于音乐教育来展示作曲技巧。
4. 交互式表演：在现场表演中使用音乐生成模型，实现与观众的互动，创造独一无二的表演体验。
5. 音乐分析和重构：利用模型分析音乐作品的风格，并基于分析重构或生成新的作品。

The AI generation of text, video, and images has surged since 2023, but the advent of audio generation has been somewhat delayed. This repository tracks the latest advancements in audio generation technology. Both of closed or open sourced achievements will be included!



| model    | Sample Rate    |  Len  | Input   |  Music  |  Example  |  Infer. Time  |  Data  | Model Arch|
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| WaveNet(2016)  | 16kHz@1  | Secs | None  | Piano or speech | Piano | = Audio len. | 260 | |
| Jukebox(2020)  | 44.1kHz@1  | Mins |  Lyrics, author, etc.  | Song with the lyrics | Song | Hours | 70k | |
| RAVE(2021)  | 48kHz@2  | Secs | Latent  | Single-genre Music | Strings | = Audio len. | 100 | |
| AudioLM(2022)  Google | 16kHz@1  | Mins |  text prompt  |  Piano or speech | Piano | Mins | 40k | |
| Musika(2022)  | 22.5kHz@1  | Secs | context vector   | Single-genre Music | Piano | = Audio len. | 1k | |
| Riffusion(2022)  | 44.1kHz@1  | 5s |  Text (genre, author, etc.)  | Music of any genre  | Jazzy clarinet | Mins | - | |
| **MusicLM(2023)** Google | 24kHz@2  | up to 5-Mins |  text prompt or image  |  Music | Music | - | 5.5k MusicCaps | Transformer-based multi-stage autoregressive modeling |
| **AudioGen(2023)** Meta | 16kHz@1  | Secs | Text (a phrase/sentence)   | Daily sounds | Dog barks | Hours | 4k | |
| Moûsai(2023)  | 48kHz@1  | Mins |  Text (genre, author, etc.) | Music of any genre lyrics | African drums | = Audio len. | 2.5k | |
| JEN-1(2023.8)  | 48kHz@2  | Mins | text prompt   | piano instruments | piano | - | private 5k hours |  autoencoder and autoregressive and non-autoregressive diffusion + transformer |
| JEN-1 Composer(2023.11)  | 48kHz@4  | Mins | text prompt   | music | music | - | - |  autoencoder and autoregressive and non-autoregressive diffusion + transformer |

# 模型技术路线图思考
基于Transformer的大语言模型（Autoregressive模型）生成方法先是用Embedding的方式将词/符号转为Token，然后通过Attention结构Decoder获取上下文和长上下文的关联，而基于Diffusion模型（Non-autoregressive模型）的图像生成方法是一次可以生成一幅图，而不是一个一个像素生存，这两种结构上的差异在于Transformer是Token by Token生成的，效率上并不够高，而Diffusion是整张图生成的，如何将二者结合起来，获得**高效、高质量**的模型就至关重要了。

从OpenAI的Sora模型可以看到，未来音频（音乐、人声）生成采用类似的结构也许会取得突破性进展，类似于OpenAI的visual patches，会由audio pathes的结构（这种结构是音频的表示单元，类似语言模型中的词，在时间长度并不是等长的），通过类似图中的videencoder将视频转到latent space，audioEncoder也是将其转到latent space patches（并非是RVQ，而是人类建模物理信号层面上目前是不可解释的，但可以采用RVQ代替），然后这些将Spacetime latent patches作为大语言模型中的Token，但是将大语言模型中的Transformer换成diffusion transformer，

![image](https://github.com/shichaog/DeepLearningMusicGeneration/assets/7869827/beb24861-3171-485e-b3a4-42f82c30d4c7)




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

JEN-1
Can works for Generation, painting and Continuation.

![image](https://github.com/shichaog/DeepLearningMusicGeneration/assets/7869827/d3707238-34de-42d5-b496-71eb3eb14350)

entails the amalgamation of both the auto-regressive(from LLM) and non-autoregressive modes(from image generation, stable diffusion) into a cohesive omnidirectional diffusion model.


### January

AudioLM https://arxiv.org/pdf/2209.03143.pdf 
MusicLM https://arxiv.org/pdf/2301.11325.pdf dataset 28hours music
from Goolge not open sourced now.
![image](https://github.com/shichaog/DeepLearningMusicGeneration/assets/7869827/d607bcfe-73fa-4b7d-a54e-f8ac1f4e38a8)
audio examples :
https://google-research.github.io/seanet/musiclm/examples/
https://google-research.github.io/seanet/audiolm/examples/



