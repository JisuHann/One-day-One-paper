# MulT: Multimodal Transformer for Unaligned Multimodal Language Sequences
## Problem
- two major challenges in modeling multimodal human language time-series data
    - inherent data non-alignment ("unaligned" nature of multimodal language sequences)
         - bc variable sampling rates for the sequences from each modality
    - long-range dependencies btw elements across modalities      

## Goal
- generically address the above issues in an end-to-end manner without explicitly aligning the data. 

## In this paper..
![](https://raw.githubusercontent.com/yaohungt/Multimodal-Transformer/master/imgs/architecture.png)
- Crossmodal Transformer
    - extends the standard Transformer network to learn representations directly 
    - repeatedly reinforce a target modality with the low-level features from another source modality by learning the attention across the two modalities' features
- cross modal **attention** module 
    - latently adapt streams from one modality to another(e.g., vision -> language) by repeated reinforcing one modality's features with those from the other modalities 
- built up from multiple stacks of pairwise and bidirectional cross modal attention blocks that directly attend to low-level features

### Overall Architecture
1. Temporal Convolutions
- why? to ensure that each element of the input sequences has sufficient awareness of its neighborhood elements -> to contain the local structure of the sequence
2. Positional Embedding
- why? to enable the sequences to carry temporal information
3. Crossmodal Transformers
- why? 
     - to enable one modality for receiving information from another modality
     - each modality keeps updating its sequence via low-level external information from the multi-head cross modal attention module -> correlate meaningful elements across modalities'
- 6 cross modal transformers (bc 3 modalities, pair forms a crossmodal interaction)
4. Self-Attention Transformers and Prediction
- the last elements of the sequence models are extracted to pass through fully-connected layers to make predictions
