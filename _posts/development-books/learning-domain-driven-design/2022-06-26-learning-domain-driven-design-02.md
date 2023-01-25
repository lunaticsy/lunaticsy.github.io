---
title: 도메인 주도 설계 첫걸음 - 02장 도메인 지식 찾아내기
author: June
date: 2022-06-26 11:15:00 +0900
categories: [개발 책, 도메인 주도 설계 첫걸음(Done)]
tags: [공부, 책, 도메인 주도 설계 첫걸음, 도메인 주도 설계, domain-driven design, DDD, 도메인, 비즈니스, 아키텍처, 소프트웨어 설계]
toc: true
math: true
mermaid: true
comments: true
---
## 범위

- [Part 1] 전략적 설계 - 02장: 도메인 지식 찾아내기

## 개념 정리

- 멘탈 모델: 도메인 전문가가 문제를 생각하는 방식
- 유비쿼터스 언어: 비즈니스 도메인을 설명하기 위한 단일화된 언어 체계
- 모델: 사물이나 현상에서 의도한 관점만 강조하고 다른 측면은 무시하여 간략히 표현한 것이다. 즉, 특정 용도를 마음에 둔 추상화의 결과다, 실세계의 복제가 아니라 우리가 실제 시스템을 이해하는 데 도움을 주는 인간이 창조물.

## 책에서 기억하고 싶은 내용

### 비즈니스 문제

- 비즈니스 문제는 비즈니스 도메인과 하위 도메인의 모든 수준에서 발생할 수 있다.

### 도메인 지식 찾아내기

- 소프트웨어 솔루션을 설계하려면 기본적으로 비즈니스 도메인 지식이 있어야 한다.
- 이런 지식은 도메인 전문가의 몫이다.
- 도메인 전문가를 이해하고 그들이 쓰는 동일한 비즈니스 용어를 사용하는 것이 중요하다.
- 즉, 멘탈 모델을 모방해야 한다.

### 커뮤니케이션

- 효과적인 커뮤니케이션은 지식 공유와 프로젝트 성공에 필수이다.
- 모든 변환은 정보를 잃게 만든다.
  - 도메인 지식은 소프트웨어 엔지니어에게 전달되는 과정에서 손실된다.
  - 도메인 지식은 종종 왜곡된 상태로 전달 된다.
  - 이러한 정보는 소프트웨어 엔지니어가 잘 못된 솔루션을 구현하게 하거나 솔루션이 올바르다 해도 해결하려는 문제가 잘못된 경우로 이어진다.
  - 어떤 경우든 프로젝트는 실패한다.
- 이 같은 문제를 해결하기 위해 도메인 주도 설계는 도메인 전문가가 소프트웨어 엔지니어에게 지식을 전달하기 위해 더 나은 방법을 제한하는데, 유비쿼터스 언어가 바로 그것이다.
- ![그림 2-1](/posts/development-books/learning-domain-driven-design/pic-2-1.jpg)
- ![그림 2-2](/posts/development-books/learning-domain-driven-design/pic-2-2.jpg)

### 유비쿼터스 언어란 무엇인가?

- 아이디어는 간단하다. 참가자들이 효과적으로 소통하기 위해 변환에 의존하지 말고 같은 언어를 사용하는 것이다.
- 비즈니스 도메인을 설명하기 위한 단일화된 언어 체계를 세우고자 하는데, 이것이 바로 유비쿼터스 언어다.

### 비즈니스 언어

- 유비쿼터스 언어는 비즈니스 언어이다. 그렇기 때문에 기술 용어는 빼고 비즈니스 도메인에 관련된 용어로만 구성해야 한다.

#### 시나리오

#### 일관성

- 유비쿼터스 언어는 반드시 정확하고 일관성이 있어야 한다. 가정할 필요가 없어야 하고, 비즈니스 도메인의 로직을 명료하게 표현해야 한다.
- 모호성이 커뮤니케이션을 방해하기 때문에 유비쿼터스 언어의 용어는 오직 하나의 의미를 가져야 한다.

### 비즈니스 도메인 모델

#### 모델이란 무엇인가?

- 모델이란 사물이나 현상에서 의도한 관점만 강조하고 다른 측면은 무시하여 간략히 표현한 것이다. 즉, 특정 용도를 마음에 둔 추상화의 결과다.
- 모델은 실세계의 복제가 아니라 우리가 실제 시스템을 이해하는 데 도움을 주는 인간이 창조물이다.

#### 효과적인 모델링

- 효과적인 모델은 그 목적을 달성하는데 필요한 세부사항만 포함한다.
- 유용한 모델은 실세계의 복사본이 아니라 문제를 해결하려는 의도가 있으며, 그 목적에 필요한 정보만 제공해야 한다.
- 모델은 본질적으로 추상화의 결과다.

#### 비즈니스 도메인 모델링

- 유비쿼터스 언어를 발전시키는 것은 사실상 비즈니스 도메인 모델을 구축하는 셈이다.

#### 지속적인 노력

- 모든 이해관계자는 모든 프로젝트와 관련된 커뮤니케이션에 유비쿼터스 언어를 지속적으로 사용해서 지식 공유를 확산하고 비즈니스 도메인에 대한 공유된 이해를 강화해야 한다.

#### 도구

#### 도전과제

- 도메인 지식을 수집하는 신뢰할 만한 유일한 방법은 도메인 전문가와 대화를 하는 것이다.
- 대부분의 경우 가장 중요한 지식은 암묵지다.
- 여기에 접근하는 유일한 방법은 질문하는 것이다.
- 조직에서 이미 사용하고 있는 언어를 바꾸는 것은 쉽지 않을 것이다.
- 이 경우 필요한 도구는 바로 인내심이다.
- 문서화나 소스코드와 같이 제어하기 쉬운 부분부터 올바른 언어를 사용하도록 하자.

### 결론

- 도메인 주도 설계의 유비쿼터스 언어는 도메인 전문가와 소프트웨어 엔지니어의 지식 간극을 메워주는 효과적인 도구다.
- 효과적인 커뮤니케이션을 위해서는 유비쿼터스 언어에서 반드시 모호성과 암묵적 가정을 제거해야 한다.
- 언어의 모든 용어는 일관성이 있어야 모호하지 않고 동의어가 없어야 한다.
- 효과적인 유비쿼터스 언어의 전제조건은 언어를 사용해야 한다는 것이다.
- 즉, 유비쿼터스 언어를 모든 프로젝트 관련 커뮤니케이션에서 일관되게 사용해야 한다.

## 요약

- 2장에서는 효과적인 커뮤니케이션과 지식 공유를 위한 도메인 주도 설계 실무인 '유비쿼터스 언어'의 개념을 소개한다.
- 효과적인 커뮤니케이션은 지식 공유와 프로젝트 성공에 필수이다.
- 모든 변환은 정보를 잃게 만든다.
- 비즈니스 도메인을 설명하기 위한 단일화된 언어 체계를 세우고자 하는데, 이것이 바로 유비쿼터스 언어다.
- 도메인 주도 설계의 유비쿼터스 언어는 도메인 전문가와 소프트웨어 엔지니어의 지식 간극을 메워주는 효과적인 도구다.
- 유비쿼터스 언어는 비즈니스 언어이다. 그렇기 때문에 기술 용어는 빼고 비즈니스 도메인에 관련된 용어로만 구성해야 한다.
- 유비쿼터스 언어의 모든 용어는 일관성이 있어야 모호하지 않고 동의어가 없어야 한다.
- 유비쿼터스 언어를 모든 프로젝트 관련 커뮤니케이션에서 일관되게 사용해야 한다.