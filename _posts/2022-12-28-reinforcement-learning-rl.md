---
title: '[RL] 강화학습(Reinforcement Learning, RL)이란?'
author: SongEun
date: 2022-12-28 12:00:00 +0000
categories: [Deep Learning]
tags: [Deep Learning, Reinforcement Learning, RL]
math: true
mermaid: true
img_path: /assets/img/posts/2022-12-28-reinforcement-learning-rl
---


## Reinforcement Learning(RL)이란?
Reinforcement Learning이란 `agent`(AI 모델)가 시행착오와 상호작용을 거치며 작업 수행 방법을 학습하는 방식이며, agent가 `action`을 하고 `environment`로부터 그에 대한 피드백 `reward`를 받아 학습한다.


![RL Process](RL_process.png){: width="1086" height="542"}
_Reinforcement Learning: An Introduction, Richard Sutton and Andrew G. Barto_

<br />

다시 말해, 아래와 같은 과정을 반복한다.

> 1. agent가 environment의 현재 상태 state(t)를 관찰하여, 이를 기반으로 action을 취함
> 2. environment로 부터 state(t+1)가 변화하며 agent는 reward을 받음
> 3. 받은 reward를 기반으로 agent는 더 많은 보상을 얻을 수 있는 방향으로 action을 하도록 학습

<br />

RL의 공식적인 정의는 아래와 같다.
> Reinforcement learning is a framework for solving control tasks (also called decision problems) by building agents that learn from the environment by interacting with it through trial and error and receiving rewards (positive or negative) as unique feedback.

<br />

## RL의 종류

RL 알고리즘은 아래 그림과 같이 분류 될 수 있다.

![Taxonomy of RL](taxonomy_of_rl.svg){: width="1086" height="542"}
_Kinds of RL algorithms, OpenAI_

### Model-Free RL과 Model-Based RL

RL 알고리즘의 가장 큰 분류 기준으로 "agent가 environment 모델에 접근 혹은 학습 할 수 있는가"를 기준으로 볼 수 있다. 이때, environment 모델은 state를 예측하고  reward를 주는 역할을 한다. 이 environment 모델을 사용하는 알고리즘을 `model-Based RL`이라 하고, 사용하지 않는 알고리즘을 `model-free RL`이라 한다.

environment 모델을 가짐으로써 얻는 장단점은 명확하다.

environment 모델은 agent가 가능한 선택지에서 일어날 일을 미리 예측하고 계획을 세울 수 있게하여 sample efficiency에서 큰 향상을 얻을 수 있다.

하지만, 많은 노력을 들여 실제와 비슷한 environment 모델을 만든다고 해도, 이상적인 모델을 얻기란 근본적으로 어렵다. 그렇기 때문에 생성된 모델을 실제 환경에서 사용하였을 때 차이가 발생할 수 있다. 또한, environment 모델의 편향성이 agent에까지 전파될 가능성이 있다는 단점이 있다.

반면에 environment 모델을 갖지 않는 model-free 방식은 environment 모델을 사용함에 있어 오는 sample efficiency을 얻기 어렵지만, 더 쉽게 구현하고 튜닝 할 수 있다는 장점이 있다. 이러한 장점 때문에 model-Based 방식보다 model-free 방식에 대한 연구가 더 많이 진행 되었다.


#### Model-Based RL
+ environment 모델을 가짐
+ agent가 가능한 선택지에서 일어날 일을 미리 예측하고 계획을 세울 수 있음 (sample efficiency)
+ 대표적인 예시로 AlphaZero
+ 실제 환경을 반영한 이상적인 environment 모델을 얻기란 사실상 어려움

#### Model-Free RL
+ environment 모델을 갖지 않음 
+ 구현 및 튜닝이 쉬워 많은 연구가 진행됨
+ agent를 학습하는 두가지 접근 방식이 있음 (다음글에 계속)


<br />

***

## **Reference**

+ [OpenAI Spinning Up](https://spinningup.openai.com/en/latest/spinningup/rl_intro2.html)
+ [What is Reinforcement Learning? - HuggingFace](https://huggingface.co/deep-rl-course/unit1/what-is-rl?fw=pt)
+ [Reinforcement Learning: An Introduction, Richard Sutton and Andrew G. Barto](http://incompleteideas.net/book/RLbook2020.pdf)
