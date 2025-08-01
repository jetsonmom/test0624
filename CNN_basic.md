# ✏️CNN이란?
## CNN(Convolutional Neural Network, 합성곱 신경망)
- 딥러닝에서 주로 이미지나 영상 데이터를 처리할 때 사용되는 대표적인 신경망 구조입니다.
- CNN은 인간의 시각 피질 구조를 모방해 개발되었으며, 이미지의 공간적, 지역적 정보를 효과적으로 학습할 수 있도록 설계되었습니다.

<img width="705" height="287" alt="image" src="https://github.com/user-attachments/assets/a017bec9-5fcf-4a44-b0a6-a77571c1506e" />


### 등장 배경
- 기존의 인공신경망(특히 다층 퍼셉트론, MLP)은 이미지를 1차원 벡터로 변환해 처리해야 했기 때문에, 이미지의 공간 구조와 지역적 정보가 손실되는 한계가 있었습니다.
- CNN은 이러한 문제를 해결하기 위해 고안되었으며, 이미지의 2차원 구조를 그대로 입력받아 공간 정보를 보존하면서 학습할 수 있습니다.

### 주요 구조와 동작 원리
- **합성곱 계층**(Convolutional Layer): 입력 데이터에 여러 개의 필터(커널)를 적용해 **특징 맵**(feature map)을 생성합니다. 각 필터는 이미지의 특정 패턴(예: 모서리, 색상 변화 등)을 감지하도록 학습됩니다.

![img](https://github.com/user-attachments/assets/e481c078-c53a-4535-a3b9-a49c2095f3e1)


- **활성화 함수**(ReLU 등): 비선형성을 부여해 신경망이 복잡한 패턴을 학습할 수 있도록 합니다. 대표적으로 ReLU(Rectified Linear Unit)가 사용됩니다.

<img width="822" height="362" alt="스크린샷 2025-07-14 09 26 07" src="https://github.com/user-attachments/assets/613ca701-82e5-406a-9d9e-54fef3ca71b9" />


- **풀링 계층**(Pooling Layer): 특징 맵의 크기를 줄이고, 중요한 정보만 추려내어 연산량을 감소시킵니다. 대표적으로 최대 풀링(max pooling)이 사용됩니다.

<img width="1280" height="497" alt="다운로드" src="https://github.com/user-attachments/assets/f72ab12b-ee2a-43dc-8453-e00106c6e7e2" />


- **완전 연결 계층**(Fully Connected Layer): 마지막에 위치하며, 추출된 특징을 바탕으로 최종 분류 작업을 수행합니다.

### CNN의 전체적인 네트워크 구조

<img width="640" height="229" alt="image (1)" src="https://github.com/user-attachments/assets/93a051a6-8655-44d0-a6d4-9ff22e37f067" />


### 특징 및 장점
- 공간 정보 보존: 이미지의 구조적, 지역적 정보를 유지하며 학습합니다.
- 특징 자동 추출: 사람이 직접 특징을 설계하지 않아도, 네트워크가 학습 과정에서 자동으로 특징을 추출합니다.
- 적은 파라미터: 필터(커널)를 공유함으로써 전체 파라미터 수가 줄어들고, 과적합 위험이 낮아집니다.
- 컴퓨터 비전 분야에 최적화: 이미지 분류, 객체 인식, 얼굴 인식, 자율주행 등 다양한 비전 분야에서 뛰어난 성능을 보입니다.


### 활용 예시
- **이미지 분류**: 고양이/강아지 구분, 손글씨 숫자 인식(MNIST 등)
- **객체 탐지 및 인식**: 자율주행차, CCTV 영상 분석
- **의료 영상 분석**: X-ray, MRI 등에서 이상 부위 탐지


### 한계점 및 최근 동향
- **로컬 특징에 강점**: CNN은 인접한 픽셀 간의 상관관계(로컬 특징)는 잘 추출하지만, 전체 이미지를 아우르는 글로벌 특징 추출에는 한계가 있습니다.
- 최근에는 **트랜스포머(Transformer) 구조**와의 결합 등 다양한 하이브리드 모델이 연구되고 있습니다.


## 
# 샤프닝 필터(Sharpening Filter) 완전 가이드 🔍

## 🎯 샤프닝 필터란?

샤프닝 필터(Sharpening Filter)는 **이미지를 선명하게 만드는 필터**입니다!

### 주요 목적
- **흐릿한 이미지를 더 선명하고 뚜렷하게 만들어 줍니다**
- 엣지(경계선)를 강조
- 디테일을 부각
- 윤곽을 더 뚜렷하게

## 🔢 샤프닝 필터의 구조

### 기본 샤프닝 필터
```python
'Sharpen': np.array([[0, -1, 0], 
                     [-1, 5, -1], 
                     [0, -1, 0]])
```

### 작동 원리
- **중심값 (5)**: 현재 픽셀을 강조
- **주변값 (-1)**: 주변 픽셀들을 빼서 차이를 증폭
- **결과**: 경계선이 더 뚜렷해짐

## 🔍 다양한 샤프닝 필터 종류

### 1. 기본 샤프닝
```python
basic_sharpen = np.array([[0, -1, 0], 
                         [-1, 5, -1], 
                         [0, -1, 0]])
```

### 2. 강한 샤프닝
```python
strong_sharpen = np.array([[-1, -1, -1], 
                          [-1, 9, -1], 
                          [-1, -1, -1]])
```

### 3. 부드러운 샤프닝
```python
soft_sharpen = np.array([[0, -0.5, 0], 
                        [-0.5, 3, -0.5], 
                        [0, -0.5, 0]])
```

## 📊 블러 vs 샤프닝 비교

| 특성 | 블러 필터 | 샤프닝 필터 |
|------|-----------|-------------|
| **목적** | 부드럽게, 노이즈 제거 | 선명하게, 디테일 강조 |
| **엣지** | 흐려짐 | 강조됨 |
| **필터값** | 모두 양수 (평균) | 중심 양수, 주변 음수 |
| **합계** | 1.0 | 1.0 |

## 🎨 실제 사용 예시

### 사진 보정 분야
- 초점이 약간 흐린 사진 보정
- 스캔한 문서의 글자 선명화
- 의료 영상의 세부사항 강조

### 컴퓨터 비전 분야
- **엣지 검출 전처리**: 경계선을 더 명확하게
- **특징점 검출**: 코너나 특징을 더 뚜렷하게
- **OCR**: 글자 인식 성능 향상

## ⚠️ 주의사항

### 1. 과도한 사용의 부작용
- 노이즈도 함께 증폭됨
- 이미지가 부자연스러워질 수 있음

### 2. 아티팩트 생성
- 부자연스러운 경계선 생성 가능
- 할로(halo) 효과 발생

### 3. 적절한 강도 조절 필요
- 이미지 특성에 맞는 필터 선택
- 단계적 적용으로 최적 결과 도출

## 🚦 신호등 검출에서의 역할

신호등 검출 시스템에서 샤프닝 필터를 사용하면:

### 장점
- **신호등 경계선**이 더 뚜렷해짐
- **Canny 엣지 검출**이 더 정확해짐
- **원형 윤곽**을 더 잘 찾을 수 있음

### 적용 예시
```python
# 샤프닝 후 엣지 검출
sharpened = cv2.filter2D(image, -1, sharpen_kernel)
edges = cv2.Canny(sharpened, low_threshold, high_threshold)
```

## 💡 핵심 요약

**샤프닝 필터는 "흐린 사진을 선명하게 만드는 마법의 필터"입니다!** ✨📸

- **목적**: 이미지 선명도 향상
- **원리**: 중심 픽셀 강조 + 주변 픽셀 차감
- **효과**: 엣지 강조, 디테일 부각
- **주의**: 과도한 사용 시 부작용 발생

---

*이 가이드는 컴퓨터 비전과 이미지 처리에서 샤프닝 필터의 기본 개념과 실제 활용법을 다룹니다.*
