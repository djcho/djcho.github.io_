---
title : "[SpringBoot][Chapter13.1] 서비스의 인증과 권한 부여 - 보안 용어 이해"
categories:
- SpringBoot
tag :
- [SpringBoot, Spring, Java, Intelij, SpringSecurity]
toc: true
toc_sticky : true
published : true
date : 2022-08-13
last_modified_at : 2022-08-13
---





장정우님이 지음, [스프링부트 핵심가이드 :: 스프링 부트를 활용한 애플리케이션 개발 실무] 책을 읽고 정리한 필기입니다.📢
{: .notice--warning}





애플리케이션을 개발하다 보면 인증과 인가 등의 보안 기능을 추가해야 할 때가 있다. 이번 장에서는 보안과 관련된 용어와 개념을 알아보고 스프링에 보안을 적용할 때 사용하는 스프링 시큐리티(Spring Security)에 대해 알아보겠다.

지금까지 실습한 애플리케이션은 화면이 없는 무상태 REST 애플리케이션이기 때문에 이번 장에서는 로그인을 통한 일반적인 인증과 인가 방식이 아닌 매 요청마다 토큰값을 활용하는 보안 기법을 알아보겠다.



## 보안 용어 이해

스프링 시큐리티를 화용하려면 먼저 보안과 관련된 용어를 알아두는 것이 중요하다. 그러므로 스프링 시큐리티를 배우기에 앞어 보안과 관련된 용어를 간단하게 설명한다.



### 인증

인증(authentication)은 사용자가 누구인지 확인하는 단계를 의미한다. 인증의 대표적인 예로 '로그인'이 있다. 로그인은 데이터베이스에 등록된 아이디와 패스워드를 사용자가 입력한 아이디와 비밀번호와 비교해서 일치 여부를 확인하는 과정이다. 로그인에 성공하면 애플리케이션 서버는 응답으로 사용자에게 토큰(token)을 전달한다. 로그인에 실패한 사용자는 토큰을 전달받지 못해 원하는 리소스에 접근할 수 없게 된다.



### 인가

인가(authorization)는 앞에서 설명한 인증을 통해 검증된 사용자가 애플리케이션 내부의 리소스에 접근할 때 사용자가 해당 리소스에 접근할 권리가 있는지를 확인하는 과정을 의미한다. 예를 들어, 로그인한 사용자가 특정 게시판에 접근해서 글을 보려고 하는 경우 게시판 접근 등급을 확인해 접근을 허가 하거나 거부하는 것이 대표적인 인가의 사례이다.

일반적인 사용자가 인증 단계에서 발급받은 토큰은 인가 내용을 포함하고 있으며, 사용자가 리소스에 접근하면서 토큰을 함께 전달하면 애플리케이션 서버는 토큰을 통해 권한 유무 등을 확인해 인가를 수행한다.



### 접근 주체

접근 주체(principal)는 말 그대로 애플리케이션의 기능을 사용하는 주체를 의미한다. 접근 주체는 사용자가 될 수도 있고, 디바이스, 시스템 등이 될 수도 있다. 애플리케이션은 앞서 소개한 인증 과정을 통해 접근 주체가 신뢰할 수 있는지 확인하고, 인가 과정을 통해 접근 주체에게 부여된 권한을 확인하는 과정 등을 거친다.
