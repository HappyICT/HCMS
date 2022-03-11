# HICT CMS REST API 정의서

---

## 1. 공통 결과 포멧

- 모든 결과는 JSON 스트링으로 제공됩니다.
- result : 결과 값은 Service VO로 제공됩니다.

## 2. 항목

### 2.1 메인 배너 목록 요청

- URL :

  - 프로토콜 :

- request parameter

| Type | Key            | 설명             | 값(예시) |
| ---- | -------------- | ---------------- | -------- |
| text | main_banner_id | 컨텐츠 배너 id   | 100      |
| text | limit          | 가져올 컨텐츠 수 | 20       |

- response

| Key  | 설명           |
| ---- | -------------- |
| {}   | array          |
| seq  | 컨텐츠 배너 id |
| seq1 | 배너 vo 내용   |

### 2.2 소개 페이지에 대한 정보 요청

<!-- 클라이언트에서 서버로 api 요청 시 -->
<!-- Json 형식으로 단일 페이지 내용 가져오기 -->

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

<!-- 클라이언트에서 서버로 api 요청 시 -->
<!-- Json 배열로 게시판 목록 가져오기 -->

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

| Key     | 설명 |
| ------- | ---- |
| { }     | JSON |
| title   | 제목 |
| content | 내용 |

```json
{ "title": "notice", "content": "공지사항" }
```

### 2.4 게시판 내용 요청

<!-- 클라이언트에서 서버로 api 요청 시 -->
<!-- Json 형식으로 게시판 내용 가져오기 -->

- URL : /api/board/id/{pageNum}

- request parameter

| Type | Key     | 설명        | 값(예시) | 기타      |
| ---- | ------- | ----------- | -------- | --------- |
| text | id      | 게시판 id   | notice   |           |
| text | pageNum | 페이지 번호 | 100      | 기본값: 1 |

```
/api/board/nocite/100
```

- response

| Key     | 설명 |
| ------- | ---- |
| { }     | JSON |
| title   | 제목 |
| content | 내용 |

```json
{ "title": "notice", "content": "<p><img class="image_resized" style="width:28.18%;" src="/liveFile/notice-edit/happyFileView.do?fileName=20220307000000ABCD.jpg"></p><p>&nbsp;</p>" }
```

## 3. 개발정보

- 개발환경
  - Spring Boot 2.6.4
  - JDK 1.8

### 3.1 SVN

- Client: [svn://10.10.10.200/happyict_cms/trunk/HCMSClient](svn://10.10.10.200/happyict_cms/trunk/HCMSClient)
- Admin: [svn://10.10.10.200/happyict_cms/trunk/HCMSAdmin](svn://10.10.10.200/happyict_cms/trunk/HCMSAdmin)

### 3.2 개발기

- Client: [http://10.10.10.201:33333](http://10.10.10.201:33333)
- Admin: [http://10.10.10.201:44444](http://10.10.10.201:44444)

### 3.2 계정

- Admin: happyict / happy0113!
