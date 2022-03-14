# HICT CMS REST API 정의서

---

## 0 Client -> Server

## 1. 공통 결과 포멧

- 모든 결과는 JSON 스트링으로 제공됩니다.
- result : 결과 값은 Service VO로 제공됩니다.

## 2. 항목

### 2.1 메인 배너 목록 요청

- URL : /api/banner/{id}

- request parameter

| Type | Key | 설명    | 값(예시) |
| ---- | --- | ------- | -------- |
| text | id  | 배너 id | main     |

```
/api/banner/main
```

- **_일단 main만 존재함_**

- response

| Key      | 설명        |
| -------- | ----------- |
| { }      | JSON        |
| boardSeq | 번호        |
| title    | 제목        |
| thumImg  | 이미지 주소 |

```json
{ "boardSeq": "123", "title": "배너 제목", "thumImg": "배너 이미지 주소" }
```

### 2.2 소개 페이지에 대한 정보 요청

- URL : /api/page/{id}

- request parameter

| Type | Key | 설명      | 값(예시) |
| ---- | --- | --------- | -------- |
| text | id  | 페이지 id | intro    |

```
/api/page/intro
```

- response

| Key     | 설명 |
| ------- | ---- |
| { }     | JSON |
| title   | 제목 |
| content | 내용 |

```json
{ "title": "intro", "content": "<title>행복ICT</title>" }
```

### 2.3 게시판 목록 요청

- URL: /api/board/{id}?search={search}&page={pageNum}

- Request Parameter

| Type | Key     | 설명        | 값(예시) | 기타         |
| ---- | ------- | ----------- | -------- | ------------ |
| text | id      | 게시판 id   | notice   |              |
| text | search  | 검색어      | Happy    | 기본값: null |
| text | pageNum | 페이지 번호 | 123      | 기본값: 1    |

```
/api/board/nocite?search=Happy&page=123
```

- response

| Key      | 설명   |
| -------- | ------ |
| { }      | JSON   |
| boardSeq | 번호   |
| title    | 제목   |
| content  | 내용   |
| regDate  | 등록일 |
| regName  | 등록자 |

```json
{
  "boardSeq": "1",
  "title": "notice",
  "content": "공지사항",
  "regDate": "1993-05-16 01:23:45",
  "regName": "이지은"
}
```

- **_현재 Paging은 구현 되어 있으나 CSS 연동 문제로 추후에 추가 할 예정_**

### 2.4 게시판 내용 요청

- URL : /api/board/{id}/{pageNum}

- request parameter

| Type | Key     | 설명        | 값(예시) | 기타      |
| ---- | ------- | ----------- | -------- | --------- |
| text | id      | 게시판 id   | notice   |           |
| text | pageNum | 페이지 번호 | 100      | 기본값: 1 |

```
/api/board/nocite/100
```

- response

| Key      | 설명   |
| -------- | ------ |
| { }      | JSON   |
| boardSeq | 번호   |
| title    | 제목   |
| regDate  | 등록일 |
| regName  | 등록자 |

```json
{
  "boardSeq": "1",
  "title": "notice",
  "content": "공지사항",
  "regDate": "1994-10-10 01:23:45",
  "regName": "배수지"
}
```

## 3. 개발정보

- 개발환경
  - Spring Boot 2.6.4
  - JDK 1.8
    - **_상위버전(Ex> JDK 17 LTS)에서도 개발 가능_**
  - MariaDB 10.6.x (변경될 수 있음)

### 3.1 SVN

- dev /dev1! 사용하시거나 개인 계정 추가하시면 됩니다.

- Client: [svn://10.10.10.200/happyict_cms/trunk/HCMSClient](svn://10.10.10.200/happyict_cms/trunk/HCMSClient)
- Admin: [svn://10.10.10.200/happyict_cms/trunk/HCMSAdmin](svn://10.10.10.200/happyict_cms/trunk/HCMSAdmin)

### 3.2 개발기

- Client: [http://10.10.10.201:33333](http://10.10.10.201:33333)
- Admin: [http://10.10.10.201:44444](http://10.10.10.201:44444)

### 3.2 계정

- Admin: happyict / happy0113!
