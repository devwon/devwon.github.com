---
layout: post
title:  "How to use postman easily"
date:   2020-01-04 17:20:00
last_modified_at:  2020-01-04 17:20:00
excerpt: "lalala"
categories: history
tags:  Postman, django, python, collection
image:
  feature: postman-logo.png
  topPosition: 0px
bgContrast: dark
bgGradientOpacity: darker
syntaxHighlighter: no
---


### [Postman 편하게 쓰기]

회사내 기존 api들을 테스트하기 위해서 postman으로 직접 request 날려보면서 하면 더 이해가 쉽게 된다. swagger를 보면서 날려보기에는 한계가 있어서 모듈별로 collection을 만들어서 사용해보았다.

참고 사이트 - [[Automatically Set CSRF Token in Postman — Django Tips]](https://hackernoon.com/automatically-set-csrf-token-in-postman-django-tips-c9ec8eb9eb5b)

*(잘못된 내용이 있으면 언제든지 고쳐주시고 댓글로 알려주시면 감사하겠습니다!)*

## [테스트 방법]

####  1.  Postman API collection 파일을 준비한다.
	🧞‍♂️: 각자 만들어 놓은 collection으로!(난 내가 만들었음..)

#### 2.  import collections

![1_import_collection](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F92d76edd-be69-4c31-9f53-9e7ce3feafa7%2F1_import_collection.png?table=block&id=9d82d480-e742-4219-892a-dd38c1d0fc03&width=4000&cache=v2){: width="100%" height="100%"}

postman 접속해서 다운 받은 파일을 압축해제 후 **import**한다.

#### 3.  회원가입, 유저 로그인

'**hakdokman_party**' collection에서 회원 가입, 유저 로그인을 진행한다.

#### 4.  token 발행 확인

유저 로그인 후 Response 부분에서 두 곳을 봐야한다.

1.  Body : 발행된 key
2.  Cookies : 발행된 csrftoken


#### 5. environment 추가

		🧞‍♂️: environment를 사용하면 매번 cookie와 token을 입력할 필요가 없이 변수에 담아놓고 사용할 수 있어 굉장히 엄청나게 대박 편리하다!

![5-1-add-env](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fbc0c7607-2913-4eea-903d-ba4926d1dc30%2F5-add-env.png?table=block&id=82197f43-f5d5-4257-9eb6-34bf092e054b&width=4000&cache=v2){: width="100%" height="100%"}

우측 상단에 톱니바퀴 버튼을 누르면 environment 관리 화면이 나오는데, 여기서 Add 버튼 눌러서 환경을 추가한다.

![5-2-add-var](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fbc0c7607-2913-4eea-903d-ba4926d1dc30%2F5-add-env.png?table=block&id=82197f43-f5d5-4257-9eb6-34bf092e054b&width=4000&cache=v2){: width="100%" height="100%"}

환경의 이름을 추가하고, 'token', 'csrftoken'의 이름으로 2개의 변수를 추가한다.

먼저 token이라는 변수에는 위에 로그인 후 발행된 key(uuid)를 넣고, csrftoken이라는 변수에는 로그인 후 발행된 csrftoken을 넣는다.

	🧞‍♂️: 추후에 새로운 정보로 재로그인시 두 VALUE 를 바꿔준다.

#### 6.  environment 적용

![6-1-adjust-env](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F27d5790c-9a08-402c-ac4e-4fc36d31abb1%2F6-adjust-env.png?table=block&id=5887b46b-4cff-4368-bfe8-0ada52327da2&width=3350&cache=v2){: width="100%" height="100%"}

우측 상단에서 위에서 추가한 환경을 선택하여 적용시킨다.

> Request Headers부분에 {{csrftoken}}이 들어가있는데, 이건 환경에서 추가한 변수이다.

![6-2-token](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F5476d0d2-fb66-491b-8f94-10ea89723cb6%2F3.png?table=block&id=a865413f-9465-45f2-83d4-77d1e47c78d2&width=2790&cache=v2){: width="100%" height="100%"}

Request Authorization부분에 Bearer Token 타입으로 {{token}}이 들어가있는데, 이것도 환경에서 추가한 변수이다.

---
> #### 🧞‍♂️: 권한 문제! 
>![7-issue1](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F051d5acb-71ae-4e58-a0ac-2d37ecf262b8%2FUntitled.png?table=block&id=b2e36f9a-fa3c-4a78-b75e-5699aea897e4&width=1340&cache=v2)
>로그인한 계정으로는 권한이 충분치 않은 request를 날리면 위와 같이 뜬다. 이때 권한을 바꾸고 싶으면, DB자체 혹은 관련 API로 수정한다.



