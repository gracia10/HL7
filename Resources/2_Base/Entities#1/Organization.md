# [Organization 3](http://hl7.org/fhir/organization.html)

- 회사, 기업, 부서, 병동, 지불자/보험자 등 공동목적의 집단 
- 조직의 연락처 및 기타정보 공유 및 식별을 위해 사용

```
{
  "resourceType" : "Organization",
  "identifier" : [{ Identifier }],
  "active" : <boolean>,  ------------------- *true. 해당 리소스 활성 여부 
  "type" : [{ CodeableConcept }], ---------- 조직 유형 (병원,기관..) 
  "name" : "<string>",
  "alias" : ["<string>"], ------------------ 조직의 이전이름, 대체이름
  "telecom" : [{ ContactPoint }], ---------- 조직의 공공 조직 연락 창구
  "address" : [{ Address }], 
  "partOf" : { Reference(Organization) }, -- 현재 조직의 상위 조직
  "contact" : [{ --------------------------- 특정 목적을 위한 조직의 연락처 (Admin..)
    "purpose" : { CodeableConcept }, ------- 당사자에게 연락하는 목적
    "name" : { HumanName }, 
    "telecom" : [{ ContactPoint }], 
    "address" : { Address } 
  }],
  "endpoint" : [{ Reference(Endpoint) }] --- 조직에 대한 서비스 접근을 제공하는 end point 
}
```
- name or identifier 중 하나는 존재해야 한다.
- adress , telecom 의 use 를 'home' 으로 지정할 수 없다.
 
** Resource를 상송받음 - id, meta, implicitRules, language
** Domain Resource 상속받음 - text, contained, extension, modifierExtension 