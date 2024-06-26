# 공인 인증서
인터넷 공인 인증서는 온라인 상에서 사용자의 신원을 확인하고 안전한 통신을 보장하기 위해 사용하는 디지털 문서입니다. 이러한 인증서는 공개 키 기반 구조(PKI, Public Key Infrastructure) 시스템에서 발행되며, 비대칭 암호화 알고리즘을 사용하여 보안을 강화합니다. 아래에 공인 인증서의 기본 개념과 포함된 내용 구조를 설명합니다.

### 공인 인증서 기본 개념

1. **비대칭 암호화**: 
   - **공개 키와 개인 키**: 비대칭 암호화는 두 개의 키 쌍을 사용합니다. 공개 키는 누구에게나 공개되며, 개인 키는 소유자만이 보관합니다. 공개 키로 암호화된 데이터는 해당 개인 키로만 복호화할 수 있습니다.
   - **보안**: 비대칭 암호화를 통해 데이터의 기밀성과 무결성을 보장합니다. 이를 통해 인증서가 유효하고 신뢰할 수 있음을 확인할 수 있습니다.

2. **인증 기관(CA, Certificate Authority)**:
   - 인증 기관은 인증서를 발급하고 관리하는 신뢰할 수 있는 제3자입니다. CA는 인증서 신청자의 신원을 확인하고, 인증서에 디지털 서명을 추가하여 발급합니다.
   - 사용자는 CA가 발행한 인증서를 신뢰함으로써 상대방의 신원을 확인할 수 있습니다.

### 공인 인증서에 포함된 내용

공인 인증서는 다양한 필드와 정보를 포함하고 있습니다. 주요 내용은 다음과 같습니다:

1. **버전(Version)**: 인증서의 버전을 나타냅니다. 현재 가장 널리 사용되는 버전은 X.509 버전 3입니다.

2. **일련 번호(Serial Number)**: 각 인증서에 고유하게 부여되는 번호로, 인증서를 식별하는 데 사용됩니다.

3. **서명 알고리즘(Signature Algorithm)**: 인증서에 서명할 때 사용된 알고리즘을 나타냅니다. 예를 들어, SHA-256과 RSA를 사용한 서명은 "SHA256withRSA"로 표시됩니다.

4. **발행자(Issuer)**: 인증서를 발급한 인증 기관의 정보가 포함됩니다. 이는 인증 기관의 이름, 국가, 조직 등을 포함합니다.

5. **유효 기간(Validity)**:
   - **유효 시작일(Not Before)**: 인증서의 유효 기간 시작 날짜.
   - **유효 종료일(Not After)**: 인증서의 유효 기간 종료 날짜.

6. **주체(Subject)**: 인증서의 소유자에 대한 정보입니다. 주로 사용자의 이름, 조직, 국가 등의 정보가 포함됩니다.

7. **주체 공개 키 정보(Subject Public Key Info)**:
   - **공개 키 알고리즘(Public Key Algorithm)**: 공개 키를 생성하는 데 사용된 알고리즘을 나타냅니다.
   - **공개 키(Public Key)**: 인증서 소유자의 공개 키입니다.

8. **확장 필드(Extensions)**:
   - **기본 제약사항(Basic Constraints)**: 인증서의 용도와 발급자의 권한을 나타냅니다.
   - **키 사용(Key Usage)**: 인증서의 키가 사용될 수 있는 용도를 지정합니다(예: 디지털 서명, 키 인출).
   - **주체 대체 이름(Subject Alternative Name)**: 주체의 추가적인 이름이나 도메인 이름을 포함할 수 있습니다.

9. **서명(Signature)**: 인증 기관이 인증서의 무결성을 보장하기 위해 인증서에 디지털 서명을 추가합니다. 서명은 인증서의 내용을 해시한 후 CA의 개인 키로 암호화하여 생성됩니다.

이러한 구조를 통해 공인 인증서는 사용자의 신원을 확인하고, 안전한 통신을 보장하는 중요한 역할을 합니다. 공인 인증서를 통해 웹사이트나 전자 메일 등의 통신이 안전하게 이루어질 수 있습니다.
