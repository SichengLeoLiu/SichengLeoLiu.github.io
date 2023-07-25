# MSMO: Multimodal Summarization with Multimodal Output
*This paper can be accessed form [here](https://aclanthology.org/D18-1448/?source=post_page---------------------------).*

This paper is the first work in Multimodal Summarization with Multimodal Output (MSMO) field. They collected dataset for MSMO research and proposed a model to handle this task.

## Model Structure

### Text Encoder
BiLSTM is used to extract text features.
### Image Encoder
VGG19 is used to extract global and local image features. Here, global features are got from the last layer of VGG19 network and local features are the feature map after last pooling layer (before full connected layer).
#### Visual Attention
Consists of three parts:
- Attention on global features
- Attention on local features
- Hierarchical visual attention on local features

### Multimodal Attention Layer
To fuse the text and visual context information, multimodal attention layer is added.
It calculate attention weight for visual context vector and text context vector respectively. Then weight visual and text context based on attention weights and add them together to get a final fused context information. 
### Decoder
Pointer-Generator Network is used to reduce repetition.

## Contribution
- Present MSMO task
- Propose a multimodal summarization model

## Possible Improvement
- Some models (VGG19, BiLSTM, Pointer-Generator Network) can be replaced with state-of-the-art models.
- It doesn't consider cross-modal information when fusing multimodal information. Cross-modal can be added in multimodal attention layer.