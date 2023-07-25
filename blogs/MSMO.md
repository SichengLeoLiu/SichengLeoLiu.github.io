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
- Attention on loca features
- Hierachical visual attention on local features


### Multimodal Attention Layer
To fuse the text and visual context information, multimodal attention layer is added.
### Text Decoder & Summary Decoder
#### Pointer-Generator Network

## Contribution
## Possible Improvement
- The models used as encoder can be replaced with state-of-the-art models.