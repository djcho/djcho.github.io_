---
title : "[SpringBoot][Chapter7.2] 테스트 코드 작성하기 - 단위 테스트와 통합 테스트"
categories:
- SpringBoot
tag :
- [SpringBoot, Spring, Java, Intelij]
toc: true
toc_sticky : true
published : true
date : 2022-07-29
last_modified_at : 2022-07-29
---





장정우님이 지음, [스프링부트 핵심가이드 :: 스프링 부트를 활용한 애플리케이션 개발 실무] 책을 읽고 정리한 필기입니다.📢
{: .notice--warning}



## 단위 테스트와 통합 테스트

테스트 방법은 여러 기준으로 분류할 수 있다. 그중 테스트 대상 범위를 기준으로 구분하면 크게 단위 테스트(Unit Test)와 통합 테스트(Integration Test)로 구분된다.

- 단위 테스트 : 애플리케이션의 개별 모듈을 독립적으로 테스트하는 방식이다.
- 통합 테스트 : 애플리케이션을 구성하는 다양한 모듈을 결합해 전체적인 로직이 의도한 대로 동작하는지 테스트하는 방식이다.

<br>

<a href="https://ko.wikipedia.org/wiki/V_%EB%AA%A8%EB%8D%B8" target="_blank">V  모델(V-model)</a>에서의 확인(Validation)단계는 아래와 같다.

![image](https://user-images.githubusercontent.com/13410737/181773861-001da779-f1dc-479e-975b-bf0c27ee19d2.png){: .align-center}

<br>



### 단위 테스트의 특징

단위 테스트는 테스트 대상의 범위를 기준으로 가장 작은 단위의 테스트 방식이다. 일반적으로 메서드 단위로 테스트를 수행하게 되며, 메서드 호출을 통해 의도한 결괏갑싱 나오는지 확인하는 수준으로 테스트를 진행한다. 단위 테스트는 테스트 비용이 적게 들기 때문에 테스트 피드백을 빠르게 받을 수 있다.



### 통합 테스트의 특징

통합 테스트는 모듈을 통합하는 과정에서의 호환성 등을 포함해 애플리케이션이 정상적으로 동작하는지 확인하기 위해 수행하는 테스트 방식이다. 앞에서 언급한 단위 테스트와 비교하자면 단위 테스트는 모듈을 독립적으로 테스트하는 반면 통합 테스트는 여러 모듈을 함께 테스트해서 정상적인 로직 수행이 가능한지를 확인한다. 그리고 단위 테스트는 일반적으로 특정 모듈에 대한 테스트만 진행하기 때문에 데이터베이스나 네트워크 같은 외부 요인들을 제외하고 진행하는 데 비해 통합 테스트는 외부 요인들을 포함하고 테스트를 진행하므로 애플리케이션이 온전히 동작하는지를 테스트하게 된다. 다만 테스트를 수행할 때마다 모든 컴포넌트가 동작해야 하기 때문에 테스트 비용이 커지는 단점이 있다.

<br>

> **💡 Tip. 테스트 비용이란?**
>
> 테스트 비용이란 용어는 소프트웨어 공학에서 많이 사용된다. 여기서 말하는 비용은 금전적인 비용을 포함해서 시간, 인력과 같은 개발에 필요한 것들을 포괄한다. 통계적으로 하나의 서비스를 개발할 때는 개발 과정에서 60%, 테스트 과정에서 40%의 비용이 든다고 알려져 있다.