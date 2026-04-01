# 🐾 Dogs vs Cats Classification Web App

Streamlit과 PyTorch를 이용해 만든 **개 / 고양이 이미지 이진 분류 웹 애플리케이션**입니다.  
사용자가 이미지를 업로드하면, 학습된 ResNet18 모델이 해당 이미지가 **개인지 고양이인지 분류**하고, 예측 결과와 확신도를 함께 보여줍니다.

---

## 1. 프로젝트 개요

이 프로젝트는 이미지 분류 모델을 직접 학습한 뒤,  
이를 Streamlit 웹 애플리케이션으로 연결하여 **사용자가 직접 이미지를 업로드하고 결과를 확인할 수 있도록 구현한 서비스**입니다.

모델은 PyTorch 기반으로 구성되어 있으며,  
웹에서는 업로드 이미지에 대해 실시간 추론을 수행합니다.

---

## 2. 주요 기능

- 이미지 업로드 (`jpg`, `jpeg`, `png`)
- 개 / 고양이 이진 분류
- 예측 결과 출력
- 확신도 표시
- 클래스별 확률 시각화

---

## 3. 사용 기술

- **Python**
- **Streamlit**
- **PyTorch**
- **Torchvision**
- **Pillow**
- **gdown**

---

## 4. 모델 설명

이 프로젝트는 `ResNet18` 기반 CNN 모델을 사용합니다.

### 모델 구조
- Backbone: `ResNet18`
- 최종 출력층: `Linear(..., 1)`
- 문제 유형: **이진 분류(Binary Classification)**

출력이 1개이므로, 예측 시 `sigmoid`를 적용하여  
해당 이미지가 Dog일 확률을 계산합니다.

```python
prob = torch.sigmoid(logit).item()
