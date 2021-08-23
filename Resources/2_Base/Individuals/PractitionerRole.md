# [PractitionerRole 2](http://hl7.org/fhir/practitionerrole.html)

- 일정기간 동안, Practitioner 가 Organization 에서, 수행하는 장소/서비스 기록
- 


```
{
  "resourceType" : "PractitionerRole",
  "identifier" : [{ Identifier }], 
  "active" : <boolean>, 
  "period" : { Period }, 
  "practitioner" : { Reference(Practitioner) }, -------------- 조직을 위하여 정의된 서비스를 수행하는 실무자
  "organization" : { Reference(Organization) }, -------------- 역할이 있는 조직
  "code" : [{ CodeableConcept }], ---------------------------- 실무자가 수행해야하는 역할 코드
  "specialty" : [{ CodeableConcept }], ----------------------- 조직의 전공/전문 분야 코드
  "location" : [{ Reference(Location) }], -------------------- 실무자가 진료하는 장소
  "healthcareService" : [{ Reference(HealthcareService) }], -- 역할을 위해 수행하는 헬스케어서비스들
  "telecom" : [{ ContactPoint }], ---------------------------- 역할, 장소, 서비스에 관련 별도 연락처 (전용회선)
  "availableTime" : [{ --------------------------------------- 실무자가 서비스를 수행할 수 있는 시간
    "daysOfWeek" : ["<code>"],  ------------------------------ (mon | tue | wed | thu | fri | sat | sun)
    "allDay" : <boolean>, 
    "availableStartTime" : "<time>", 
    "availableEndTime" : "<time>" 
  }],
  "notAvailable" : [{ ---------------------------------------- 특정 사유로 업무 수행, 서비스 제공할 수 없는 기간
    "description" : "<string>", ------------------------------ 사유 
    "during" : { Period } 
  }],
  "availabilityExceptions" : "<string>", --------------------- availableTime 대 예외인 경우 사유 (공휴일)
  "endpoint" : [{ Reference(Endpoint) }]
}
```
- allDay 플러그가 true인 경우 availableStartTime, availableEndTime 은 무시됨
