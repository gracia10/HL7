# [Practitioner 3](http://hl7.org/fhir/practitioner.html)

- 의료 서비스에 직간접적으로 관여된 실무자. 책임자
  - 의사 (일반의, 개업의, 치과의사), 약사
  - 간호사, 서기관, 의사조수 , 접수원
  - 조산사,영앙사, 치료사, 검안사, 구급대원
  - 보철 기술자, 방사선 촬영기사
  - 사회복지사, 요양보호사
  - 환자 기록 IT 담당자
  - 서비스 동물 (암 감지견)

```
{
  "resourceType" : "Practitioner",
  "identifier" : [{ Identifier }], 
  "active" : <boolean>, 
  "name" : [{ HumanName }], 
  "telecom" : [{ ContactPoint }],
  "address" : [{ Address }], --------------- 개인주소
  "gender" : "<code>", --------------------- male | female | other | unknown
  "birthDate" : "<date>", 
  "photo" : [{ Attachment }], 
  "qualification" : [{ --------------------- 자격증, 면허, 교육 정보
    "identifier" : [{ Identifier }], 
    "code" : { CodeableConcept }, ---------- 자격증 코드
    "period" : { Period }, ----------------- 자격증 유효 기간
    "issuer" : { Reference(Organization) } - 발급조직
  }],
  "communication" : [{ CodeableConcept }] -- 환자와 소통시 사용 가능 언어
}
```

- qualification 은 역할,조직과 상관없이 취득가능하다
- 자격증이 있어도 해당 업무를 수행을 반드시 의미하지는 않는다
