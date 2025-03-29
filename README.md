# ellina-project-AI
# 🧠 전이 학습을 활용한 아몬드 품종 분류

본 프로젝트는 사전 학습된 딥러닝 모델(VGG16, ResNet50, Inception-v3)을 활용하여 아몬드 품종을 분류하고, 그 성능을 비교하는 것을 목표로 합니다.  
Kaggle의 Almond Varieties 데이터셋을 사용하며, 전이 학습과 데이터 증강을 통해 적은 양의 데이터로도 높은 정확도를 달성했습니다.

---

## 📁 데이터셋

- **출처**: [Kaggle Almond Varieties](https://www.kaggle.com/datasets/mahyeks/almond-varieties)
- **클래스 수**: 4개 (SIRA, NURLU, AK, KAPADOKYA)
- **총 이미지 수**: 1,556장
- **데이터 분할**:
  - 학습(Train): 80%
  - 검증(Validation): 10%
  - 테스트(Test): 10%

---

## 🔧 사용한 모델

| 모델명       | 입력 크기  | 특징 |
|--------------|------------|------|
| VGG16        | 224×224    | 단순하지만 깊은 구조, 파라미터 수 많음 |
| ResNet50     | 224×224    | 잔차 블록으로 깊은 네트워크 안정적 학습 |
| Inception-v3 | 299×299    | 다양한 필터 크기 병렬 적용(Inception 모듈) |

---

## 🎯 적용 기법

- **전이 학습 (Transfer Learning)**: ImageNet 사전 학습 가중치 사용
- **특징 추출 (Feature Extracting)**: FC Layer만 학습
- **데이터 증강 (Data Augmentation)**:
  - 랜덤 좌우 반전, 회전, 어파인 변환, 크롭, 색상 조정 등
- **조기 종료 (Early Stopping)**: 검증 손실 기준
- **학습률 감소 (Learning Rate Scheduler)**: `ReduceLROnPlateau` 적용

---

## 📈 실험 결과

| 모델명       | 테스트 정확도 | 요약 |
|--------------|----------------|------|
| VGG16        | 97.45%         | 안정적인 수렴, Early Stopping 적용 |
| ResNet50     | 99.36%         | 매우 높은 일반화 성능 |
| Inception-v3 | **100.00%**    | 완벽한 분류 성능 달성 |

---

## ⚠️ 한계점

- **데이터셋 규모가 작음** → 과적합 위험 존재
- **촬영 환경이 제한적** (단일 배경, 조명) → 실제 환경 일반화 어려움
- 향후 더 다양한 환경 및 이미지 조건에서의 성능 검증 필요

---

## 📚 참고 문헌

1. Simonyan & Zisserman (2014), *Very Deep Convolutional Networks for Large-Scale Image Recognition*
2. He et al. (2016), *Deep Residual Learning for Image Recognition*
3. Szegedy et al. (2016), *Rethinking the Inception Architecture for Computer Vision*
4. [PyTorch 공식 문서](https://pytorch.org/docs/stable/index.html)
5. [Kaggle Almond Varieties Dataset](https://www.kaggle.com/datasets/mahyeks/almond-varieties)

---

## ▶️ Google Colab 실험 링크

🔗 [Colab 노트북 바로가기](https://colab.research.google.com/drive/1tKxo_KAFyx9igWLM1eNnycfY03WskoiW?usp=sharing)
