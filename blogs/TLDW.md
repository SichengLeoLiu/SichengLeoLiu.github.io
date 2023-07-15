# TLDW: Extreme Multimodal Summarisation of News Videos
*This paper can be accessed form [here](https://arxiv.org/abs/2210.08481).*

This paper mainly focus on Extreme Multimodal summarisation (XMSMO) task which is summarizing a vedio and a paragraph into one picture and one sentence. I'm going briefly introduce the content and my understanding of this paper.
## Model Structure
The model is consist of three parts: Encoder, Fusion and Decoder.
### Encoder
Encoder is used to convert inputs to vectors (can be viewed as feature extraction). It consist of two parts including visual encoder and text encoder since the model will receive two kinds of inputs (vedio and text).
#### Visual Encoder
In order to get herachical information, frames, scenes and vedios' feature should be calculate. CLIP model is used to do multimodal embedding. Firstly, it is used to convert each frame to pre-trained feature $x^{frame}_i$. Then a pooling method is used to get scene representation. **A scene is a group of frames which have similar semantic.** Finally, generalize pooling operator (GPO) is used to summarise scenes' information to get the vedio feature.

#### Text Encoder
Similar to visual encoder, text encoder is used to calculate herachical information for words, sentences and documents. It also use CLIP model to get words' representation. Then, a pooling method is used to summarise words' information to calculate representations for sentences. Finally, GPO is used to get document's representation by summarizing sentences' features.

### Fusion
Graph-based attention is used to fuse information from different modals. The whole fusion process can be divided into two steps. The first is local fusion and the second is global fusion.

In local fusion, scene A's fusion features are calculated by  combining A's features with all sentences' features, through the graph-based attention. Then an average pooling is applied to summarise the results. Similarly, sentence fusion features are calculated by combining each sentence feature with all scenes' features.

In global fusion, the representation of whole input is calculated by combining vedio feature and document feature with same method.


### Decoder
## Contribution
## Possible Improvement