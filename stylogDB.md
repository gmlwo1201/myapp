# DB ERD 설명
## 구조 : 회원가입과 회원정보(성별, 피부 톤, 키, 체형, 개인/사업자, 액세서리 유무)를 저장하는 데이터베이스
* 주요 테이블
  - users(회원가입 시 받는 기본 정보)
  - cody(코디에 필요한 회원정보)
  - seller(사업자인지 개인인지)
  - other(액세서리 등 착용 정보)
* 테이블 및 관계
  - users
    - 회원가입으로 기본정보 저장(username, email, password)
    - cody 테이블과 1:1 연결
  - cody
    - 코디에 필요한 회원정보 저장(gender, body, skin, height)
    - 회원정보는 카테고리에 번호를 지정해 저장(ex. gender의 경우 남:1 여:2)
    - 개인/사업자 분류는 isSeller에서 True/False로 값을 받음
    - 기타 액세서리 착용유무를 other 테이블에서 True/False로 받음
    - users - 1:1 / seller, other - 1:n
  - seller
    - 사업자일 경우 (isSeller = True) 회사 이름 등록(sellername)
    - cody 테이블과 1:n 연결
  - other
    - 기타 액세서리를 착용했을 경우(other = true)
    - 안경, 모자, 기타 액세서리 True/False로 저장(glasses, hat, bag)
    - 신발은 이름(ex.워커, 운동화, 단화...)으로 저장(shoes)
  
