# refresh token

- 로그인을 다시하지 않아도 Access Token을 새로 받을 수 있게 하는 장기 열쇠 같은 것

# refresh token의 필요성

- Access Token은 짧게 쓰는 출입증 역할을 함
  - 유출되었을 때 대응하기 힘들기 때문에 유효시간을 짧게 설정
  - 유효시간이 짧으면 금방 만료되고 로그인이 필요해짐
  - 잦은 로그인은 매우 불편함
- refresh token은 이런 access token을 재발급 받을 수 있게 하는 용도로 쓰임
  - 유효시간은 access token보다 길게 설정
  - 외부에 노출되지 않게 잘 보관해야 함

# access token 재발급 흐름

1. 기본 access token을 활용해서 서버에 요청한다
2. 여기서 access token이 만료되면 401 에러가 발생한다
3. 이 때 refresh token을 활용해 access token을 재발급 받는다
   - 재발급에 성공한 경우
     - 발급받은 access token으로 다시 서버에 요청한다
   - 재발급에 실패한 경우
     - refresh token이 만료되어 다시 로그인 해야 한다
