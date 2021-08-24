# Person

# Scope and Usage

여러 역할에 걸쳐 개인(인간 또는 동물)애 대한 공통 인구 통계의 참조 집합을 제공할 수 있는 연결 리소스 역할을 함

이 연결은 같거나 서로 다른 FHIR시스템,애플리케이션에 있는 역할별 FHIR 리소스 (환자, 실무자 및 관련 담당자)로 직접 연결 되거나 비즈니스 식별자를 통해 간접적으로 연결 할 수 있음.

### 리소스 사용

- 의사, 환자 및 관련 인력 간에 이러한 비규격화된 정보의 유지관리를 저정하는데 사용할 수 있는 인구통계 집합(예: 시스템 내에서 서로 다른 유형의 알려진 리소스를 함께 연결)
- 네트워크 기반 마스터 사용자 색인(예: 국가 식별자 색인 또는 네트워크 구성원, 가입자 목록)
- 여러 서버의 환자 리소스를 연결하여 모두 동일한 개인에게 해당하는 중앙 레지스터(예: 많은 시스템을 갖춘 대규모 조직 내에서, 외부 링크와 소스 정보를 수정할 필요 없이 다양한 레코드를 연결 할 수 있음)
- 의사, 환자 및 관련자의 기록이 동일한 사람에 해당함을 주장할 수 있는 액세스 모니터링 소프트웨어 지원

### JSON형태

```json
{
  "resourceType" : "Person",
  // fromResource:id,meta,implicitRules, andlanguage
  // fromDomainResource:text,contained,extension, andmodifierExtension
  "identifier" : [{Identifier }], //A human identifier for this person
  "name" : [{HumanName }], //A name associated with the person
  "telecom" : [{ContactPoint }], //A contact detail for the person
  "gender" : "<code>", //male | female | other | unknown
  "birthDate" : "<date>", //The date on which the person was born
  "address" : [{Address }], //One or more addresses for the person
  "photo" : {Attachment }, //Image of the person
  "managingOrganization" : {Reference(Organization) }, //The organization that is the custodian of the person record
  "active" : <boolean>, //This person's record is in active use
  "link" : [{ //Link to a resource that concerns the same actual person
    "target" : {Reference(Patient|Practitioner|RelatedPerson|Person) }, //R!The resource to which this actual person is associated
    "assurance" : "<code>" //level1 | level2 | level3 | level4
  }]
}
```