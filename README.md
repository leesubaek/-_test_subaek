해당 프로젝트 링크: https://github.com/leesubaek/-hacking_test_subaek

1. 사전 협의 
- 모의해킹 실습용 사이트가 중요하게 생각하는게 어떤 것인지?
-> 해당 사이트는 은행사이트이다. 은행 사이트면 고객들의 정보가 중요하다고 생각하기 때문에 보안의 3요소 중 기밀성이 가장 중요하다고 생각한다.

2. 공격 시나리오 설립
- 어떤 기능을 활용하여 공격할지 구상
-> 로그인 화면에서 SQL Injection 공격을 실행한다.
-> XSS 공격을 실행한다.

3. 최종적으로 나올 결과물에 대한 예측/정리
-> 아이디, 비밀번호 없이 로그인 성공
-> 쿠키값을 얻을 수 있다.

4. 서버 모의침투
- 자신이 생각한 서버의 취약점을 공격
  -> 강의에서 배운 파일 업로드 공격을 시도 해보고 싶었지만, 파일 관련된 코드를 발견 못해서 아쉽게 못함.
  -> 다음에 시간 되면 해보기로 결정.

5. 보고서 작성
- 모의 해킹 실습용 사이트 관계자를 만난다면, 이해할 수 있는 취약점 설명 및 보안/보안 방법에 대해서 기술
- > OWASP top 10 에서 정한 취약점 10개에 항상 포함되는 SQL Injection, XSS이 2가지를 실행하였다.
  > SQL Injection은 용 프로그램 보안 상의 허점을 의도적으로 이용해, 악의적인 SQL문을 실행되게 함으로써 데이터베이스를 비정상적으로 조작하는 코드 인젝션 공격이다.
  > 취약 url: https://demo.testfire.net/login.jsp
  > 위험도: 높음
  > 원인: 사용자가 정보를 입력했을 때 sql injection과 관련된 보안을 적용하지 않았다.
  > 해결방법:
  1.입력된 값이 유효한지 검증. -> 'or 1=1;- -	or 1=1-- 등등 해당 문자열을 필터링 하게 한다.
  
  > XSS는 웹 페이지에 스크립트를 삽입하여 악의적인 스크립트를 실행할 수 있는 공격이다.
  > 취약 url: https://demo.testfire.net/search.jsp?query=
  > 위험도: 높음
  > 원인: 검색창에서 xss와 관련된 보안이 적용되지 않았다.
  > 해결방법:
  1. 위험한 문자 삽입에 대한 검증이 필요하다. -> 입력 데이터의 길이 제한가기, 지정된 문자 또는 형식으로 입력되었는지 확인.
  ex) <script>alert('XXS!');</script> 해당 문자열을 필터링 하는 시큐어 코딩 구성해야 함.
