# Trust Chain(신뢰 체계)
Trust Chain(신뢰 체계)은 디지털 인증서의 신뢰성을 검증하기 위해 사용되는 일련의 인증서들로 구성된 체계입니다. 이는 최종 사용자 인증서(End-Entity Certificate)에서 시작해 중간 인증 기관(Intermediate CA)의 인증서를 거쳐 루트 인증 기관(Root CA)의 인증서로 이어집니다. 이 과정을 통해 각 인증서가 상위 인증서의 공개 키로 검증되어 신뢰성을 확보합니다. Trust Chain의 구체적인 기록 방식과 작동 원리는 다음과 같습니다:

### 1. 최종 사용자 인증서 (End-Entity Certificate)

**Alice의 웹사이트 인증서**:
- **주체**: Alice의 웹사이트 도메인 (예: www.alice.com)
- **발행자**: Intermediate CA
- **주체의 공개 키**: Alice의 공개 키
- **서명**: Intermediate CA의 개인 키로 서명됨

### 2. 중간 인증서 (Intermediate CA Certificate)

**Intermediate CA의 인증서**:
- **주체**: Intermediate CA의 이름 (예: Intermediate CA Ltd.)
- **발행자**: Root CA
- **주체의 공개 키**: Intermediate CA의 공개 키
- **서명**: Root CA의 개인 키로 서명됨

### 3. 루트 인증서 (Root CA Certificate)

**Root CA의 인증서**:
- **주체**: Root CA의 이름 (예: Root CA Inc.)
- **발행자**: Root CA (자체 서명, self-signed)
- **주체의 공개 키**: Root CA의 공개 키
- **서명**: Root CA의 개인 키로 서명됨

### 신뢰 체계 검증 과정

1. **브라우저 또는 클라이언트**:
   - Alice의 웹사이트에 접속 시, Alice의 웹사이트 인증서를 받습니다.

2. **Alice의 인증서 검증**:
   - **서명 검증**: Intermediate CA의 공개 키를 사용하여 Alice의 인증서 서명을 검증합니다.
   - **인증서 경로**: Alice의 인증서에 포함된 발행자 필드(Issuer) 정보를 통해 Intermediate CA의 인증서를 찾습니다.

3. **Intermediate CA의 인증서 검증**:
   - **서명 검증**: Root CA의 공개 키를 사용하여 Intermediate CA의 인증서 서명을 검증합니다.
   - **인증서 경로**: Intermediate CA의 인증서에 포함된 발행자 필드(Issuer) 정보를 통해 Root CA의 인증서를 찾습니다.

4. **Root CA의 인증서 검증**:
   - **신뢰 확인**: Root CA의 인증서는 브라우저나 운영 체제의 신뢰된 루트 저장소에 사전 설치되어 있습니다. 따라서 추가 검증 없이 신뢰할 수 있는 것으로 간주됩니다.

### Trust Chain 기록 방식

각 인증서는 PEM(Base64로 인코딩된 ASCII 텍스트) 또는 DER(바이너리) 형식으로 저장되며, 다음과 같은 정보를 포함합니다:

- **Version**: X.509 버전
- **Serial Number**: 인증서 고유 번호
- **Signature Algorithm**: 서명에 사용된 알고리즘
- **Issuer**: 발행자 정보 (상위 CA)
- **Validity Period**: 유효 기간 (시작일 및 종료일)
- **Subject**: 주체 정보 (인증서 소유자)
- **Subject Public Key Info**: 주체의 공개 키 및 알고리즘
- **Extensions**: 추가 확장 필드 (예: Key Usage, Basic Constraints)
- **Signature**: 상위 CA의 서명

### 예시

```plaintext
-----BEGIN CERTIFICATE-----
MIIDXTCCAkWgAwIBAgIJALaGzyC9E...
...
-----END CERTIFICATE-----
```

이러한 형식으로 각 인증서가 기록되고, Trust Chain을 통해 상호 검증이 이루어집니다. 각 단계에서 상위 인증서의 공개 키를 사용해 하위 인증서의 서명을 검증함으로써 전체 체인의 신뢰성을 확인합니다.
