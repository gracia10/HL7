# [Location 3](http://hl7.org/fhir/location.html)


- 서비스가 제공 되는 물리적 장소
  - 건물, 병동, 방, 침대
  - Mobile Clinic (진료차) , 내동고, 인큐베이터
  - 집, 차고, 도로, 주차장, 공원
 

- Organize 의 물리적 구조를 설명하기 위한 리소스
- 관할 영역/구역을 설명하는 리소스 
  - 국가, 도, 사업, 사업 범위, 사업 부문

```
{
  "resourceType" : "Location",
  "identifier" : [{ Identifier }], 
  "status" : "<code>", ------------------- (active | suspended | inactive) 공간 사용 여부
  "operationalStatus" : { Coding }, ------ 침대, 병실/의자 상태 
  "name" : "<string>", 
  "alias" : ["<string>"], ---------------- 장소의 과거/대체 이름
  "description" : "<string>", ------------ 장소를 찾거나 참조하기 위한 설명
  "mode" : "<code>", --------------------- (instance | kind) 해당 리소스가 특정 장소, 관할 의미 여부
  "type" : [{ CodeableConcept }], -------- 장소에서 수행하는 작업 코드
  "telecom" : [{ ContactPoint }], 
  "address" : { Address }, 
  "physicalType" : { CodeableConcept }, -- 물리적 유형 (집, 도로, 자동차)
  "position" : {  ------------------------ WGS84 데이텀을 사용해 표시되는 물리적 위치
    "longitude" : <decimal>, ------------- 경도
    "latitude" : <decimal>, -------------- 위도
    "altitude" : <decimal> --------------- 고도
  },
  "managingOrganization" : { Reference(Organization) }, -- 위치의 프로비저닝 담당 조직
  "partOf" : { Reference(Location) }, -------------------- 물리적으로 상위 장소 (건물-방)
  "hoursOfOperation" : [{ -------------------------------- 장소 오픈 정보
    "daysOfWeek" : ["<code>"], 
    "allDay" : <boolean>, 
    "openingTime" : "<time>", 
    "closingTime" : "<time>" 
  }],
  "availabilityExceptions" : "<string>", --- 장소 이용 추가 예외 정보 (공휴일,단축 시간) 
  "endpoint" : [{ Reference(Endpoint) }]
}
```
- mode는 특정한 장소(instance) or 범위의 장소(kind) 로 나뉜다.
  - A 구급차, 201호 실 vs 구급차, 병실
  - 특정 장소를 참조해야 할 때 "kind" 모드의 리소스를 사용해서는 안된다 
  - kind 모드인 경우 adress가 없을 수 있다  
  - instance 모드인 경우에만 사용하는 element가 있다 (예외 존재. O병원 구급차)
```
Location.identifier
Location.telecom
Location.address
Location.position
Location.status
Location.managingOrganization
```