---
title: '[MLOps] 모델 서빙 형식'
author: SongEun
date: 2022-11-29 12:01:00 +0000
categories: [MLOps]
tags: [Python, MLOPs, Serving]
math: true
mermaid: true
---

최근에 파이썬으로 데몬 만들일이 있었는데 만들면서 삽질한 내용 기록

## **모델 서빙 형식**

### 1. SavedModel

Tensorflow에서 사용, Tensorflow Serving에서 실행가능

### 2. ONNX

Pytorch로 사용해서 학습한 모델에서 사용 가능

### 3. TensorRT

NVIDIA의 TensorRT 기술을 사용해서 GPU 인퍼런스에 최적화
Trition Inference Server 를 사용해서 서빙 가능



## **Code**

### 1. Python Daemon (util.py)


<br>

___

## **Reference**

+ [손쉽게 ML라이프사이클을 다룰 수 있는 MLOps (Naver Deview 2020)](https://deview.kr/data/deview/session/attach/1500_T2_%EC%9C%A0%EC%8A%B9%ED%98%84_%EC%86%90%EC%89%BD%EA%B2%8C%20ML%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4%EC%9D%84%20%EB%8B%A4%EB%A3%B0%20%EC%88%98%20%EC%9E%88%EB%8A%94%20MLOps.pdf)
+ [모델 서빙 최적화를 위한 프레임워크 선정과 서빙 성능 극대화하기 (KakaoPay)](https://tech.kakaopay.com/post/model-serving-framework/)

