# 박재홍 · Backend Engineer

Java와 Spring을 기반으로 업무 규칙을 데이터 구조와 API로 구현하고,
테스트와 배포 절차를 통해 운영을 고려한 서비스로 만듭니다.

📄 **[포트폴리오 보기](https://phj2000.github.io/portfolio/)** · [PDF](https://phj2000.github.io/portfolio/portfolio.pdf)

## Tech Stack

| 분야 | 기술 |
|---|---|
| Backend | Java 21, Spring Boot, Spring MVC, Spring Security, JPA |
| Data | PostgreSQL, PostGIS, Redis, Flyway |
| Delivery | GitHub Actions, Docker, GHCR, AWS EC2, GCP VM |
| Quality | JUnit 5, MockMvc, Testcontainers, JaCoCo |
| Observability | Micrometer Tracing (OpenTelemetry), Tempo, Loki, Alloy, Grafana |

## Projects

### 위굴 Backend · [SaGongSa-404/404_BE](https://github.com/SaGongSa-404/404_BE)
예산, 위시, 구매 결정, 알림, 회고가 하나로 이어지는 소비 의사결정 서비스

📱 **Google Play 출시** · [위굴 다운로드](https://play.google.com/store/apps/details?id=com.sa0sa.wigul)

- 구매 결정(GO/STOP), 예산, 알림 상태를 **단일 트랜잭션**으로 갱신하고 CHECK, partial unique index, trigger로 DB 불변조건 보장
- **Idempotency-Key + partial unique index**로 더블탭과 timeout 재시도에 따른 중복 생성 방지
- **GCP VM standby 배포**: 8081 후보 기동 → Health Check → Caddy 전환 → 8080 복귀, 실패 시 자동 복구
- 쇼핑 링크 가져오기를 비동기 작업 큐로 전환하고 요청 병합, 단기 캐시, 부하 테스트로 검증

### Beach Complex · [Beach-complex/Beach_complex](https://github.com/Beach-complex/Beach_complex)
위치 기반 해수욕장 정보, 혼잡도 수집, 예약과 알림을 제공하는 서비스

- 외부 혼잡도·날씨 데이터를 30분 주기로 수집하고, 관측 이력과 현재 상태를 분리 저장
- 예약 동시 요청 10건 → **201 1건 / 409 9건 / DB row 1건**을 통합 테스트로 검증 (DB UNIQUE + ProblemDetail 오류 계약)
- **AWS EC2 CD**: Docker Buildx → GHCR(commit SHA 태그) → Compose 배포 → Actuator Health 확인
- **분산 추적**: HTTP, 비동기 이메일, SMTP, Scheduler 구간의 Trace 계측과 Loki·Grafana 로그↔Trace 연결

## Open Source

Java 오픈소스 **70개 프로젝트에 95개 PR이 머지**되었습니다. 대부분 엣지 케이스 버그 수정이며, 재현 테스트를 함께 제출했습니다.

| 프로젝트 | ★ | PR |
|---|---:|---|
| [vavr](https://github.com/vavr-io/vavr) | 6.1k | [Preserve priority order in PriorityQueue.distinctBy](https://github.com/vavr-io/vavr/pull/3358) |
| [JavaParser](https://github.com/javaparser/javaparser) | 6.1k | [Preserve unary operator token boundaries in all printers](https://github.com/javaparser/javaparser/pull/5151) |
| [JSqlParser](https://github.com/JSQLParser/JSqlParser) | 5.9k | [Deparse casts to single-field row types](https://github.com/JSQLParser/JSqlParser/pull/2757) |
| [JSON-java](https://github.com/stleary/JSON-java) | 4.7k | [Fix Property enumeration without local entries](https://github.com/stleary/JSON-java/pull/1087) |
| [RoaringBitmap](https://github.com/RoaringBitmap/RoaringBitmap) | 3.9k | [Preserve replacement containers in Roaring64Bitmap.remove](https://github.com/RoaringBitmap/RoaringBitmap/pull/853) |
| [Agrona](https://github.com/aeron-io/agrona) | 3.2k | [Fix IntArrayList operations with different null values](https://github.com/aeron-io/agrona/pull/380) |
| [JGraphT](https://github.com/jgrapht/jgrapht) | 2.7k | [Preserve shortest-path edges in KMB Steiner trees](https://github.com/jgrapht/jgrapht/pull/1391) |
| [ModelMapper](https://github.com/modelmapper/modelmapper) | 2.3k | [Preserve large floating-point values when converting to BigInteger](https://github.com/modelmapper/modelmapper/pull/789) |
| [StreamEx](https://github.com/amaembo/streamex) | 2.2k | [Avoid intermediate overflow when splitting combination streams](https://github.com/amaembo/streamex/pull/288) |
| [JaVers](https://github.com/javers/javers) | 1.5k | [Preserve SQL Timestamp nanoseconds in JSON](https://github.com/javers/javers/pull/1501) |

<details>
<summary>머지된 PR 전체 목록 (34)</summary>

| 머지일 | 저장소 | PR |
|---|---|---|
| 2026-10-12 | [javers/javers](https://github.com/javers/javers) | [Preserve SQL Timestamp nanoseconds in JSON](https://github.com/javers/javers/pull/1501) |
| 2026-10-12 | [jOOQ/jOOR](https://github.com/jOOQ/jOOR) | [Handle null values in Reflect.equals and hashCode](https://github.com/jOOQ/jOOR/pull/131) |
| 2026-10-12 | [networknt/json-schema-validator](https://github.com/networknt/json-schema-validator) | [[2.x] Fix uniqueItems validation for non-array inputs](https://github.com/networknt/json-schema-validator/pull/1298) |
| 2026-10-12 | [networknt/json-schema-validator](https://github.com/networknt/json-schema-validator) | [Fix uniqueItems validation for non-array inputs](https://github.com/networknt/json-schema-validator/pull/1297) |
| 2026-10-11 | [aeron-io/agrona](https://github.com/aeron-io/agrona) | [Fix IntArrayList operations with different null values](https://github.com/aeron-io/agrona/pull/380) |
| 2026-10-11 | [stleary/JSON-java](https://github.com/stleary/JSON-java) | [Fix Property enumeration without local entries](https://github.com/stleary/JSON-java/pull/1087) |
| 2026-10-10 | [vavr-io/vavr](https://github.com/vavr-io/vavr) | [Preserve priority order in PriorityQueue.distinctBy](https://github.com/vavr-io/vavr/pull/3358) |
| 2026-10-09 | [java-diff-utils/java-diff-utils](https://github.com/java-diff-utils/java-diff-utils) | [Track line-count changes when applying fuzzy patches](https://github.com/java-diff-utils/java-diff-utils/pull/238) |
| 2026-10-09 | [jgrapht/jgrapht](https://github.com/jgrapht/jgrapht) | [Preserve shortest-path edges in Kou-Markowsky-Berman Steiner trees](https://github.com/jgrapht/jgrapht/pull/1391) |
| 2026-10-09 | [jhalterman/typetools](https://github.com/jhalterman/typetools) | [Compare reified parameterized types structurally](https://github.com/jhalterman/typetools/pull/88) |
| 2026-10-09 | [JSQLParser/JSqlParser](https://github.com/JSQLParser/JSqlParser) | [fix: deparse casts to single-field row types](https://github.com/JSQLParser/JSqlParser/pull/2757) |
| 2026-10-08 | [FasterXML/java-classmate](https://github.com/FasterXML/java-classmate) | [Include array element types in equality and hashing](https://github.com/FasterXML/java-classmate/pull/126) |
| 2026-10-08 | [knowm/XChart](https://github.com/knowm/XChart) | [Allow tick spacing hints per Y-axis group](https://github.com/knowm/XChart/pull/1035) |
| 2026-10-07 | [javaparser/javaparser](https://github.com/javaparser/javaparser) | [Preserve unary operator token boundaries in all printers](https://github.com/javaparser/javaparser/pull/5151) |
| 2026-10-07 | [knowm/XChart](https://github.com/knowm/XChart) | [Accept null-free immutable lists in box charts](https://github.com/knowm/XChart/pull/1033) |
| 2026-10-07 | [ethlo/itu](https://github.com/ethlo/itu) | [Detect leap seconds across UTC offset date boundaries](https://github.com/ethlo/itu/pull/70) |
| 2026-10-07 | [modelmapper/modelmapper](https://github.com/modelmapper/modelmapper) | [Preserve large floating-point values when converting to BigInteger](https://github.com/modelmapper/modelmapper/pull/789) |
| 2026-10-06 | [albfernandez/juniversalchardet](https://github.com/albfernandez/juniversalchardet) | [Return unsigned values from EncodingDetectorInputStream.read()](https://github.com/albfernandez/juniversalchardet/pull/73) |
| 2026-10-06 | [mangstadt/ez-vcard](https://github.com/mangstadt/ez-vcard) | [Disable grouping separators in vCard floating-point values](https://github.com/mangstadt/ez-vcard/pull/165) |
| 2026-10-06 | [fathzer/javaluator](https://github.com/fathzer/javaluator) | [Preserve large finite values when rounding](https://github.com/fathzer/javaluator/pull/16) |
| 2026-10-06 | [jline/jline3](https://github.com/jline/jline3) | [fix: recompute tab position after truncation](https://github.com/jline/jline3/pull/2305) |
| 2026-10-06 | [semver4j/semver4j](https://github.com/semver4j/semver4j) | [Fix upper bounds for zero-major partial caret ranges](https://github.com/semver4j/semver4j/pull/478) |
| 2026-10-06 | [jdbc-observations/datasource-proxy](https://github.com/jdbc-observations/datasource-proxy) | [Escape remaining control characters in JSON query logs](https://github.com/jdbc-observations/datasource-proxy/pull/135) |
| 2026-10-05 | [haraldk/TwelveMonkeys](https://github.com/haraldk/TwelveMonkeys) | [Fix CompoundReader reset across reader boundaries](https://github.com/haraldk/TwelveMonkeys/pull/1356) |
| 2026-10-05 | [tinylog-org/tinylog](https://github.com/tinylog-org/tinylog) | [Handle a closing escape tick at the end of a message](https://github.com/tinylog-org/tinylog/pull/935) |
| 2026-10-05 | [optimatika/ojAlgo](https://github.com/optimatika/ojAlgo) | [Preserve milliseconds when converting offset and zoned date-times](https://github.com/optimatika/ojAlgo/pull/695) |
| 2026-10-05 | [amaembo/streamex](https://github.com/amaembo/streamex) | [Avoid intermediate overflow when splitting combination streams](https://github.com/amaembo/streamex/pull/288) |
| 2026-10-05 | [vigna/dsiutils](https://github.com/vigna/dsiutils) | [Reject negative skips before changing reader state](https://github.com/vigna/dsiutils/pull/10) |
| 2026-10-05 | [JOML-CI/JOML](https://github.com/JOML-CI/JOML) | [Fix integer overflow in gridDistance](https://github.com/JOML-CI/JOML/pull/428) |
| 2026-10-05 | [lukas-krecan/JsonUnit](https://github.com/lukas-krecan/JsonUnit) | [Preserve shared matches in unordered array comparisons](https://github.com/lukas-krecan/JsonUnit/pull/1206) |
| 2026-10-05 | [RoaringBitmap/RoaringBitmap](https://github.com/RoaringBitmap/RoaringBitmap) | [Preserve replacement containers in Roaring64Bitmap.remove](https://github.com/RoaringBitmap/RoaringBitmap/pull/853) |
| 2026-10-05 | [making/yavi](https://github.com/making/yavi) | [Preserve set membership semantics in containsAll constraints](https://github.com/making/yavi/pull/519) |
| 2026-10-04 | [Sekelenao/Flinkboot](https://github.com/Sekelenao/Flinkboot) | [#237: fix(core): reject exponential backoff multiplier equal to one](https://github.com/Sekelenao/Flinkboot/pull/267) |
| 2026-10-04 | [Sekelenao/Flinkboot](https://github.com/Sekelenao/Flinkboot) | [#243: docs(core): add execution package info](https://github.com/Sekelenao/Flinkboot/pull/266) |

</details>
