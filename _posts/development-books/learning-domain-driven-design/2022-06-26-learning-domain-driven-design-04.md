---
title: 도메인 주도 설계 첫걸음 - 04장 바운디드 컨텍스트 연동
author: June
date: 2022-07-05 15:03:00 +0900
categories: [개발 책, 도메인 주도 설계 첫걸음(Done)]
tags: [공부, 책, 도메인 주도 설계 첫걸음, 도메인 주도 설계, domain-driven design, DDD, 도메인, 비즈니스, 아키텍처, 소프트웨어 설계]
toc: true
math: true
mermaid: true
comments: true
---
## 범위

- [Part 1] 전략적 설계 - 04장: 바운디드 컨텍스트 연동

## 개념 정리

컨트랙트(contract): 바운디드 컨텍스트 사이의 접점

## 책에서 기억하고 싶은 내용

- 바운디스 컨텍스트의 구현은 서로 독립적으로 발전할 수 있지만, 상호작용해야 한다.

### 협력형 패턴 그룹

#### 파트너십 패턴

- 파트너십(partnership) 모델에서 바운디드 컨텍스트 간의 연동은 애드혹(ad-hoc) 방식으로 조정한다.
- 한 팀은 다른 팀에게 API의 변경을 알리고 다른 팀은 충돌 없이 이를 받아들인다.
- 어떤 팀도 컨트랙트를 정의하는 데 ㅆ는 언어를 강요하지 않는다.
- 발생할 수 있는 연동의 문제를 해결하는 데 양 팀 모두 협력한다.
- 공기화나 커뮤니케이션의 어려움 떄문에 지리적으로 떨어져 있는 팀에게는 적합하지 않을 수 있다.
- ![그림 4-1](/posts/development-books/learning-domain-driven-design/pic-4-1.jpg)

#### 공유 커널 패턴

- 공유 커널(shared kernel)과 같은 공유 모델은 모든 바운디드 컨텍스트에 필요에 따라 설계된다.
- 공유 모델은 이를 사용하는 모든 바운디드 컨텍스트에 덜쳐서 일관성을 유지해야 한다.
- 공유 커널은 여러 바운디드 컨텍스트에 속하기 때문에 변경은 지속적으로 통합돼야 한다.
- 고유 커널 패턴의 적용 여부를 결정하는 가장 중요한 기준은 중복 비용과 조율 비용의 비율이다.
- 공유 커널은 동일 팀에서 소유하고 구현한 바운디드 컨텍스트를 연동하는 경우에 잘 맞는다.
- ![그림 4-2](/posts/development-books/learning-domain-driven-design/pic-4-2.jpg)

### 사용자-제공자 패턴 그룹

- 제공자는 사용자에게 서비스를 제공한다.
- 서비스 제공자는 '업스트림(upsteam)'이고, 고객 또는 사용자는 '다운스트림(downstream)'이다.
- ![그림 4-3](/posts/development-books/learning-domain-driven-design/pic-4-3.jpg)

#### 순응주의자 패턴

- 다운스트림 팀이 업스트림 팀의 모델을 받아들이는 바운디드 컨텍스트의 관계
- 제공자의 모델에 따라 정의된 연동 컨트랙트를 제공할 뿐이므로 사용자의 선택지는 이를 받아들이거나 떠나거나 둘 중 하나다.
- ![그림 4-4](/posts/development-books/learning-domain-driven-design/pic-4-4.jpg)

#### 충돌 방지 계층 패턴

- 다운스트림 바운디드 컨텍스트가 이에 순응하지 않는 경우 '충돌 방지 계층(ACL: anticorruption layer)'을 통해 업스트림 바운디드 컨텍스트의 모델을 스스로의 필요에 맞게 가공할 수 있다.
- 충돌 방지 계층 패턴은 다음 사례와 같이 제공자의 모델을 것을 원치 않거나 순응에 필요한 노력이 가치가 없을 경우를 다룬다.
  - 다운스트림 다운디드 컨텍스트가 핵심 하위 도메인을 포함할 경우
  - 업스트림 모델이 사용자의 요건에 비효율적이거나 불편한 경우
  - 제공자가 컨트랙트를 자주 변경하는 경우
- ![그림 4-5](/posts/development-books/learning-domain-driven-design/pic-4-5.jpg)

#### 오픈 호스트 서비스 패턴

- 이 패턴은 힘이 사용자 측에 있을 경우를 처리한다.
- 제공자의 퍼블릭 인터페이스는 자신의 유비쿼텃 언어를 따르는 대신, 연동 지향 언어(integration-oriented language)를 통해 사용자에게 더 편리한 프로토콜을 노출하려고 한다. 이러한 퍼블릭 프로토콜을 공표된 언거(published language)라고 한다.
- 오픈 호스트 서비스(OHS: open-host service) 패턴은 충돌 방지 계층 패턴의 반대다. 사용자 대신 제공자가 내부 모델 번역을 구현한다.
- ![그림 4-6](/posts/development-books/learning-domain-driven-design/pic-4-6.jpg)

### 분리형 노선

- 분리형 노선(separated ways) 패턴에는 팀에 협업 의지가 없거나 협업할 수 없는 경우와 같이 다양한 이유가 있다.

#### 커뮤니케이션 이슈

- 팀이 협업과 합의에 어려움을 격고 있다면 여러 바운디드 컨텍스트 내에서 기능을 중복해서 가져가고 각자의 길을 가는 것이 더 비용 효과적이다.

#### 일반 하위 도메인

- 중복도니 하위 도메인의 특성도 협업 없이 분리된 길을 가야 하는 이유가 될 수 있다.
- 일반 하위 도메인이 일반 솔루션과 연동하는 것이 쉽다면 각 바운디드 컨텍스트 내에서 각자 연동하는 것이 더욱 비용 효과적일 수 있다.

#### 모델의 차이

- 모델이 너무 달라서 순응주의자 관계가 불가능하고 출돌 방지 계층을 구현하는 것도 기능 중복보다 비용이 더 클 수 있다. 이런 경우에는 팀이 각자의 길을 가는 것이 더 비용 효과적이다.

### 컨텍스트 맵

- ![그림 4-8](/posts/development-books/learning-domain-driven-design/pic-4-8.jpg)

#### 유지보수

#### 한계

### 결론

- 바운디드 컨텍스트는 서로 상호작용해야 한다.

## 요약

- 바운디드 컨텍스트는 서로 상호작용해야 한다.
- 바운디드 컨텍스트 간 소통과 통합을 구성하는 다양한 패턴을 탐구한다.
- 파트너십: 바운디드 컨텍스트는 애드훅 방식으로 연동된다.
- 공유 커널: 두 개 이상의 바운디드 컨텍스트가 참여하는 모든 바운디드 컨텍스트가 공유하는 제한적으로 겹치는 모델을 공유해서 연동한다.
- 순응주의자: 사용자는 서비스 제공자의 모델에 순응한다.
- 충돌 방지 계층: 사용자는 서비스 제공자의 모델을 사용자의 요건에 맞게 번역한다.
- 오픈 호스트 서비스: 서비스 제공자는 사용자의 요건에 최적화된 도델인 공표된 언어를 구현한다.
- 분리형 노선: 협력과 연동 보다 특정 기능을 중복으로 두는 것이 더 저렴한 경우다.
