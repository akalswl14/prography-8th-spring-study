# spring @repository

- DB에 접근하는 메서드를 사용하기 위한 인터페이스

# spring @Service

- 비지니스 로직을 수행하는 영역
- Client → Controller → Service → Repository → Domain → DB, Controller의 요청 처리 위한 영역

# spring @PersistenceContext

- 영속성 컨텍스트
- 엔티티 영구 저장소(가상의 DB)
- 서비스별 EntityManager Factory 1개, DB 접근때마다 쓰레드별로 EntityManager 생성되고 EntityManager가 영속성 컨텍스트 접근
- 생명주기: 비영속 → 영속 → 준영속 → 삭제
- 특징
    - 1차 Cache 역할
    - 동일성 보장(Identity)
    - 쓰기 지연(Transactional write-behind)
    - 변경 감지(Dirty checking): 엔티티 변경사항 자동 체크
    - 플러시(Flush): 영속성 컨텍스트 변경 내용 DB 반영

# SQL, JPQL 차이점

- SQL: 테이블을 대상으로 쿼리
- Entity 객체를 대상으로 쿼리

# spring @Autowired

- DI(Dependency Injection, 의존성 주입)을 위함
    - 생산성과 보안성을 위해 필요(캡슐화)
    - Bean 생성 → 의존성 주입
- 의존성 주입을 위해 사용, 객체의 타입에 해당하는 Bean을 찾아 주입
- 3가지 사용 방법
    - 필드
        - 필드 수정이 가능하게 된다.
    - setter
        - 필드 수정이 가능하게 된다.
    - 생성자(Best Case)
        - 생성자의 변수 final 가능
        - 테스트에 유용

# 리플렉션

- 

# @RequiredArgsConstructor

- final이나 @NotNull 필드에 자동으로 생성자 생성해주는 롬북 어노테이션
- @Autowired보다 코드가 간결해진다.

# 생성자 주입을 사용해야 하는 이유

- 객체의 불변성 확보(final)
- 테스트 코드 작성 용이
- 스프링 비침투적 코드 작성(@Autowired는 스프링에서 제공하는 어노테이션)
- 순환 참조 에러 방지(필드 주입일 경우)

# spring @Transactional

- 읽기 transaction이 많다면 Class에 @Transactional(readOnly = true)로 두고 쓰기가 필요한 메서드에만 @Transactional로 두기
- ACID(원자성, 일관성, 독립성, 지속성)
