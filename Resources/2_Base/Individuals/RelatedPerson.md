# RelatedPerson

환자의 치료에 관여하지만 의료의 대상이 아니며 진료 과정에서 공식적인 책임이 없는 사람에 대한 정보

### 사용

- 환자의 남편 또는 아내
- 환자의 친척 또는 친구
- 이웃이 환자를 병원으로 데려 오는 경우
- 말의 소유자 또는 조련사
- 환자의 변호사 또는 보호자
- 안내견

### JSON 형식

```json
{
  "resourceType" : "RelatedPerson",
  // fromResource:id,meta,implicitRules, andlanguage
  // fromDomainResource:text,contained,extension, andmodifierExtension
  "identifier" : [{Identifier }], //A human identifier for this person
  "active" : <boolean>, //Whether this related person's record is in active use
  "patient" : {Reference(Patient) }, //R!The patient this person is related to
  "relationship" : [{CodeableConcept }], //The nature of the relationship
  "name" : [{HumanName }], //A name associated with the person
  "telecom" : [{ContactPoint }], //A contact detail for the person
  "gender" : "<code>", //male | female | other | unknown
  "birthDate" : "<date>", //The date on which the related person was born
  "address" : [{Address }], //Address where the related person can be contacted or visited
  "photo" : [{Attachment }], //Image of the person
  "period" : {Period }, //Period of time that this relationship is considered valid
  "communication" : [{ //A language which may be used to communicate with about the patient's health
    "language" : {CodeableConcept }, //R!The language which can be used to communicate with the patient about his or her health
    "preferred" : <boolean> //Language preference indicator
  }]
}
```