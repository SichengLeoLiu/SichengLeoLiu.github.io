# TLDW: Extreme Multimodal Summarisation of News Videos
*2023.07.20*

*This paper can be accessed form [here](https://arxiv.org/abs/2210.08481).*

This paper mainly focus on Extreme Multimodal summarisation (XMSMO) task which is summarizing a video and a paragraph into one picture and one sentence. I'm going briefly introduce the content and my understanding of this paper.
## Model Structure
The model is consist of three parts: Encoder, Fusion and Decoder.
### Encoder
Encoder is used to convert inputs to vectors (can be viewed as feature extraction). It consist of two parts including visual encoder and text encoder since the model will receive two kinds of inputs (video and text).
#### Visual Encoder
In order to get hierarchical information, frames, scenes and videos' feature should be calculate. CLIP model is used to do multimodal embedding. Firstly, it is used to convert each frame to pre-trained feature $x^{frame}_i$. Then a pooling method is used to get scene representation. **A scene is a group of frames which have similar semantic.** Finally, generalize pooling operator (GPO) is used to summarise scenes' information to get the video feature.

#### Text Encoder
Similar to visual encoder, text encoder is used to calculate hierarchical information for words, sentences and documents. It also use CLIP model to get words' representation. Then, a pooling method is used to summarise words' information to calculate representations for sentences. Finally, GPO is used to get document's representation by summarizing sentences' features.

### Fusion
Graph-based attention is used to fuse information from different modals. The whole fusion process can be divided into two steps. The first is local fusion and the second is global fusion.

In local fusion, scene A's fusion features are calculated by  combining A's features with all sentences' features, through the graph-based attention. Then an average pooling is applied to summarise the results. Similarly, sentence fusion features are calculated by combining each sentence feature with all scenes' features.

In global fusion, the representation of whole input is calculated by combining video feature and document feature with same method.


### Decoder
Decoder is also divided into visual decoder and textual decoder.

#### Visual Decoder
Visual decoder consists of three stages. Bi-GRU is used in every stages:
- scene-guided frame decoding - This stage consider frame level information and scene information containing multimodal information.

- video-guided frame decoding - This stage consider frame level information and video information.

- cross-modality-guided frame decoding - This stage consider frame and video level information and global multimdal information.

Finally, one frame with highest score is picked.

#### Textual Decoder
Textual decoder also consists of three stages.
- sentenced-guided word decoding - This stage consider word level information and sentence information containing multimodal information.

- document-guided word decoding - This stage consider word level information and document information.

- cross-modality-guided word decoding - This stage consider document and word level information and global multimodal information.

Finally, *k* words with highest score are picked.

### Coverage Calculation
This paper considers four kinds of coverages which can also be regarded as loss calculation methods. They are list below.
- Document Coverage - Compute the Wasserstein distance between document and the selected sentence.
- Video Coverage - Compute the Wasserstein distance between selected cover frame and the mean of video frames.
- Textual Fluency - Using pre-trained model evaluate the fluency of the textual summary.
- Cross-modal Consistency - Measuring the cos distance between cover frame and summary sentence.

Finally, four coverages are summed to get a final coverage.
## Contribution
- Put forward a new problem - XMSMO
- First put forward a unsupervised method for XMSMO problem.

## Possible Improvement
Not found yet.