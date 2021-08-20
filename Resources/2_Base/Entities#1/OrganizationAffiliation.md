# [OrganizationAffiliation 0](http://hl7.org/fhir/organizationaffiliation.html)

- 일정 기간동안 유지되는 두 조직 간의 제휴/협회/관계 정의
- 비계층적 조직 관계를 정의
  - 한조직이 다른 조직에 서비스를 제공 (케이터링, 에이전시 서비스)
  - 파트너십, 합작 투자 구성
  - 협회의 회원이나 협회를 소유하지 않는 경우

```
{
  "resourceType" : "OrganizationAffiliation",
  "identifier" : [{ Identifier }], 
  "active" : <boolean>, --------------------------------------- *true. 해당 리소스 활성 여부
  "period" : { Period }, -------------------------------------- 관계가 유지되는 기간
  "organization" : { Reference(Organization) }, --------------- 역할이 존재하는 조직. 멤버장 조직 
  "participatingOrganization" : { Reference(Organization) }, -- 역할을 수행/제공하는 조직. 멤버 조직
  "network" : [{ Reference(Organization) }], ------------------ Health insurance provider network
  "code" : [{ CodeableConcept }], ----------------------------- 참여 조직이 수행하는 역할 정의
  "specialty" : [{ CodeableConcept }], ------------------------ 역할 내 참여 조직의 전문/전공 분야 코드
  "location" : [{ Reference(Location) }], --------------------- 역할이 수행되는 장소
  "healthcareService" : [{ Reference(HealthcareService) }], --- 제공되는 헬스케어 서비스
  "telecom" : [{ ContactPoint }], ----------------------------- 참여 조직의 연락처
  "endpoint" : [{ Reference(Endpoint) }] 
}
```
- Health insurance provider network : 건강보험 회사와 계약을 체결한 의료 제공자 그룹
- network 는 참여 조직이 지정된 location에서, 지정한 healthcareService를 제공하는 경우 기재 


** Resource를 상송받음 - id, meta, implicitRules, language
** Domain Resource 상속받음 - text, contained, extension, modifierExtension 
