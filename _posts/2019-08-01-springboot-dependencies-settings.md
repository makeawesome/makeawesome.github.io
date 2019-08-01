---
title: "스프링부트 프로젝트 의존성 관리, 기본 설정"
date: "2019-08-01 22:00:00 -0400"
categories: springboot web
---

의존성 관리, 기본 설정
-----

Maven 기준으로 다음과 같은 의존성을 가지고 있다.  
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.example</groupId>
	<artifactId>myproject</artifactId>
	<version>0.0.1-SNAPSHOT</version>

	<!-- Inherit defaults from Spring Boot -->
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.0.3.RELEASE</version>
	</parent>

	<!-- Add typical dependencies for a web application -->
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
      <!-- 스프링부트가 관리하는 의존성은 <version>을 <parent>에서 상속 받을 수 있다. -->
		</dependency>
	</dependencies>

	<!-- Package as an executable jar -->
	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>
```

`<parent>`에는 스프링부트가 관리하는 의존성 목록과 인코딩 방식, JDK 버전 등 프로젝트 전반의 기본 설정이 있다.  
스프링부트가 관리하는 의존성은 추가 시 버전을 명시하지 않아도 된다. 버전을 명시하지 않으면 `<parent>`에서 버전을 상속 받는다.

스프링부트가 제공하는 기본 설정의 변경이 필요할 경우, pom.xml에 변경 사항을 입력하면 기본 설정이 Override 된다.

기존 프로젝트에 스프링부트를 도입할 경우 pom.xml에 `<parent>`에 스프링부트를 입력해주면 된다.  
이미 상속 중인 다른 패키지가 있다면 그 패키지의 부모로 스프링부트를 추가하면 스프링부트의 설정을 그대로 사용할 수 있다.

---

스프링부트 프로젝트 생성
-----
https://start.spring.io/ 에서 필요한 언어, 스프링부트 버전, 필요한 의존성을 선택하면  
보일러 플레이트 코드가 담긴 스프링부트 프로젝트를 다운로드 할 수 있다.

---

#### Reference
* [Installation Instructions for the Java Developer](https://docs.spring.io/spring-boot/docs/2.0.3.RELEASE/reference/htmlsingle/#getting-started-installation-instructions-for-java)
* [Developing Your First Spring Boot Application](https://docs.spring.io/spring-boot/docs/2.0.3.RELEASE/reference/htmlsingle/#getting-started-first-application)