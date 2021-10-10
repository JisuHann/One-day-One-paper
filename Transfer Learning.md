# Transfer Learning

- Pre-trained 사전학습된 모델
- Transfer Learning: Pre-trained된 모델의 weight와 bias를 자신의 데이터로 transfer하여 빠르게 학습하는 방법(Fine-tuning)
    - Fine-tune all the weights based on the new data. 
![](https://www.topbots.com/wp-content/uploads/2019/12/cover_transfer_learning_1600px_web.jpg)
- 대표적인 transfer learning tutorial [link](https://colab.research.google.com/github/pytorch/tutorials/blob/gh-pages/_downloads/62840b1eece760d5e42593187847261f/transfer_learning_tutorial.ipynb#scrollTo=kZ5mBwTMmHUe)
```python
model_ft = models.resnet18(pretrained=True)
num_ftrs = model_ft.fc.in_features
# 여기서 각 출력 샘플의 크기는 2로 설정합니다.
# 또는, nn.Linear(num_ftrs, len (class_names))로 일반화할 수 있습니다.
model_ft.fc = nn.Linear(num_ftrs, 2)

model_ft = model_ft.to(device)

criterion = nn.CrossEntropyLoss()

# 모든 매개변수들이 최적화되었는지 관찰
optimizer_ft = optim.SGD(model_ft.parameters(), lr=0.001, momentum=0.9)

# 7 에폭마다 0.1씩 학습률 감소
exp_lr_scheduler = lr_scheduler.StepLR(optimizer_ft, step_size=7, gamma=0.1)
```
- [reference](https://cs231n.github.io/transfer-learning/)
## Transfer Learning scenarios
1. ConvNet as feature extractor : take a ConvNet pretrained on ImageNet, remove the last fully-connected layer, then treat the rest of the ConvNet as a fixed feature extractor for the new dataset
2. Fine-tuning the ConvNet: Not only replace and retrain the classifier on top of the ConvNet on the new dataset, but to **also fine-tune the weights of the pretrained network by continuing the backpropagation**
3. Pretrained models: people release their final ConvNet checkpoints for the benefit of others who can use the networks for fine-tuning

## When and how to fine-tune?
1. New dataset is small and similar to original dataset: train a linear classifier on the CNN codes.
2. New dataset is large and similar to the original dataset: try to fine-tune through the full network.
3. New dataset is small but very different from the original dataset: it might work better to train the SVM classifier from activations somewhere earlier in the network.
4. New dataset is large and very different from the original dataset: Since the dataset is very large, we may expect that we can afford to train a ConvNet from scratch. However, in practice it is very often still beneficial to initialize with weights from a pretrained model. In this case, we would have enough data and confidence to fine-tune through the entire network.

## Practical advice (skip)
