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
