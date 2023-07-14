# TLDW: Extreme Multimodal Summarisation of News Videos
*This paper can be accessed form [here](https://arxiv.org/abs/2210.08481).*

This paper mainly focus on Extreme Multimodal summarisation (XMSMO) task which is summering a vedio and a paragraph into one picture and one sentence. I'm going briefly introduce the content and my understanding of this paper.
## Model Structure
The model is consist of three parts: Encoder, Fusion and Decoder.
### Encoder
Encoder is used to convert inputs to vectors (can be viewed as feature extraction). It consist of two parts including visual encoder and text encoder since the model will receive two kinds of inputs (vedio and text).
#### Visual Encoder
CLIP model is used to do multimodal embedding. It is used to convert each frame to pre-trained feature $x^{frame}_i$. Then a pooling method is used to get scene representation.

#### Text Encoder


### Fusion
### Decoder
## Contribution
## Possible Improvement