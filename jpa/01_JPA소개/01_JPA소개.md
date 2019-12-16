#1.JPA 소개
* 애플리케이션은 대부분 관계형 데이터베이스를 데이터 저장소로 사용한다.

### 1.1.1 반복, 반복 그리고 반복
* SQL 을 직접 다룰 때의 문제점을 알아보기 위해 자바와 관계형 데이터 베이스를 사용해서 회원관리 기능을 개발해보자.
* 회원 테이블은 이미 만들어져 있다고 가정하고 회원을 CRUD(등록, 수정, 삭제, 조회) 하는 기능을 개발해보자
* 먼저 예제 1.1과 같이 자바에서 사용할 회원(Member) 객체를 만들자.

```
Public class Member {
    private String memberId;
    private String name;
    …
}
```
* DAO를 만들자

```
Public class MemberDAO {
    Public Member find(String memberId){…}
}
```

* 이제 MemberDAO의 find() 메소드를 완성해서 회원을 조회하는 기능을 개발해보자.

1. 회원 조회용 SQL을 작성한다.
SELECT MEMBER_ID, NAME FROM MEMBER M WHERE MEMBER_ID = ?

2. JDBC API를 사용해서 SQL을 실행한다.
ResultSet rs = stmt.executeQuery(sql);

3. 조회 결과를 Member 객체로 매핑한다.

```
String memberId = re.getString(“MEMBER_ID”);
String name = rs.getString(“NAME”);

Member member = new Member();
member.setMemberId(memberId);
Member.setName(name);
…
```

* 이제 회원 조회 기능을 완성 했다. 다음으로 예제 1.3과 같이 회원 등록 기능을 만들어 보자.

```
Public class MemberDAO {
    Public Member find(String memberId){…}
    Public void save(Member member){…} // 추가
}
```

1. 회원 등록용 SQL을 작성한다.
INSERT INFO MEMBER(MEMBER_ID, NAME) VALUES(?,?)

2. 회원 객체의 값을 꺼내서 등록 SQL에 전달한다.
pstmt.setString(1, member.getMemberId())
Pstmt.setString(2, member.getName())

3. JDBC API를 사용해서 SQL을 실행한다.
pstmt.executeUpdate(sql)


* 회원을 조회하는 기능과 등록하는 기능을 만들었다. 
* 다음으로 회원을 수정하고 삭제하는 기능도 추가해보자. 
* 아마도 SQL을 작성하고 JDBC API를 사용하는 비슷한 일을 반복해야 할 것이다.
* 회원 객체를 데이터 베이스가 아닌 자바 컬렉션에 보관한다면 어떨까? 컬렉션은 다음 한 줄로 객체를 저장할 수 있다.
list.add(member)

* 하지만 데이터 베이스는 객체 구조와는 다른 데이터 중심의 구조를 가지므로 객체를 데이터 베이스에 직접 저장하거나 조회할 수는 없다.
* 따라서 개발자가 SQL과 JDBC API를 사용해서 변환 작업을 직접 해주어야 한다.
* 개발하려는 애플리케이션에서 사용하는 데이터베이스 테이블이 100개라면 무수히 많은 SQL을 작성해야 하고 이런 비슷한 일을 100번은 더 반복해야 한다.
* 이렇듯 지루함과 반복의 연속이다.

### 1.1.2 SQL 의존적인 개발
컬럼 하나만 추가해도 CRUD 모두 수정해야한다.

### 1.1.3 JPA 문제 해결


## 1.2.패러다임 불일치
### 1.2.1 상속
### 1.2.2 연관관계
### 1.2.3 객체 그래프 탐색
### 1.2.4 비교
### 1.2.5 정리

## 1.3 JPA란 무엇인가?
### 1.3.1 JPA 소개
### 1.3.2 왜 JPA를 사용해야 하는가?

## 1.4 정리
Q&A ORM에 대한 궁금증과 오해

