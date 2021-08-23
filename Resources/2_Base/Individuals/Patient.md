# FHIR

# 1.2 Resource Index

두개의 리소스가 한번에 전송을 하기위해서는 bundle로 감싸준다.

[https://www.hl7.org/fhir/patient.html](https://www.hl7.org/fhir/patient.html) ( 번역 페이지)

→ Resources → paitent

# 8.1 Resource Patient - Content

## 8.1.1 Scope and Usage

이 리소스는 다음을 포함한 광범위한 건강 관련 활동에 관련된 환자와 동물에 대한 데이터를 다룸

- 치료활동
- 정신과 진료
- 사회서비스
- 임신관리
- 간호 및 보조 생활
- 식이요법
- 개인 건강 및 운동 데이터 추적

리소스 데이터에는 환자에 대한 "누구" 정보가 포함되며, 이 데이터의 속성은 관리, 재무 및 물류 절차를 지원하는 데 필요한 인구 통계 정보에 초점에 맞춰져 있음.

환자 기록은 일반적으로 각 기관이 만들고 유지 관리하며 환자를 돌봄,따라서 여러 기관에서 관리를 받는 환자 또는 동물은 해당 정보를 여러 환자 리소스에 제공할 수 있음.

모든 요소가 기본 리소스에(인종,민족,장기 기증자 상태, 국가 등) 포함이 되는 것은 아니지만 특정 관활권(미국에서 사용프로그램)  또는 표준 확장에 대해 정의 된 개요에서 찾을 수 있다. 이 분야는 국가마다 다양하며, 종종 유사한 개념에 대한 명칭과 값이 다르지만 매핑과 교환이 가능할 정도로 유사하지는 않음

## 8.1.2 Resource Content

XML, JSON이 있음

### JSON Template

```json
{
  "resourceType" : "Patient",
  // fromResource:id,meta,implicitRules, andlanguage
  // fromDomainResource:text,contained,extension, andmodifierExtension
  "identifier" : [{Identifier }], //An identifier for this patient
  "active" : <boolean>, //Whether this patient's record is in active use
  "name" : [{HumanName }], //A name associated with the patient
  "telecom" : [{ContactPoint }], //A contact detail for the individual
  "gender" : "<code>", //male | female | other | unknown
  "birthDate" : "<date>", //The date of birth for the individual// deceased[x]: Indicates if the individual is deceased or not. One of these 2:
  "deceasedBoolean" : <boolean>,
  "deceasedDateTime" : "<dateTime>",
  "address" : [{Address }], //An address for the individual
  "maritalStatus" : {CodeableConcept }, //Marital (civil) status of a patient// multipleBirth[x]: Whether patient is part of a multiple birth. One of these 2:
  "multipleBirthBoolean" : <boolean>,
  "multipleBirthInteger" : <integer>,
  "photo" : [{Attachment }], //Image of the patient
  "contact" : [{ //A contact party (e.g. guardian, partner, friend) for the patient
    "relationship" : [{CodeableConcept }], //The kind of relationship
    "name" : {HumanName }, //A name associated with the contact person
    "telecom" : [{ContactPoint }], //A contact detail for the person
    "address" : {Address }, //Address for the contact person
    "gender" : "<code>", //male | female | other | unknown
    "organization" : {Reference(Organization) }, //C?Organization that is associated with the contact
    "period" : {Period } //The period during which this contact person or organization is valid to be contacted relating to this patient
  }],
  "communication" : [{ //A language which may be used to communicate with the patient about his or her health
    "language" : {CodeableConcept }, //R!The language which can be used to communicate with the patient about his or her health
    "preferred" : <boolean> //Language preference indicator
  }],
  "generalPractitioner" : [{Reference(Organization|Practitioner|
PractitionerRole) }], //Patient's nominated primary care provider
  "managingOrganization" : {Reference(Organization) }, //Organization that is the custodian of the patient record
  "link" : [{ //Link to another patient resource that concerns the same actual person
    "other" : {Reference(Patient|RelatedPerson) }, //R!The other patient or related person resource that the link refers to
    "type" : "<code>" //R!replaced-by | replaces | refer | seealso
  }]
}
```

[각 부분별 설명](https://www.notion.so/6ddcbda00ebf4b3fae86d8077338c036)

## 8.1.13 Resource Patient - Examples

```json
//일반적인 환자 예시 샘플
{
  "resourceType": "Patient",
  "id": "example",
  "text": {
    "status": "generated",
    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">\n\t\t\t<table>\n\t\t\t\t<tbody>\n\t\t\t\t\t<tr>\n\t\t\t\t\t\t<td>Name</td>\n\t\t\t\t\t\t<td>Peter James \n              <b>Chalmers</b> (&quot;Jim&quot;)\n            </td>\n\t\t\t\t\t</tr>\n\t\t\t\t\t<tr>\n\t\t\t\t\t\t<td>Address</td>\n\t\t\t\t\t\t<td>534 Erewhon, Pleasantville, Vic, 3999</td>\n\t\t\t\t\t</tr>\n\t\t\t\t\t<tr>\n\t\t\t\t\t\t<td>Contacts</td>\n\t\t\t\t\t\t<td>Home: unknown. Work: (03) 5555 6473</td>\n\t\t\t\t\t</tr>\n\t\t\t\t\t<tr>\n\t\t\t\t\t\t<td>Id</td>\n\t\t\t\t\t\t<td>MRN: 12345 (Acme Healthcare)</td>\n\t\t\t\t\t</tr>\n\t\t\t\t</tbody>\n\t\t\t</table>\n\t\t</div>"
  },
  "identifier": [
    {
      "use": "usual",
      "type": {
        "coding": [
          {
            "system": "http://terminology.hl7.org/CodeSystem/v2-0203",
            "code": "MR"
          }
        ]
      },
      "system": "urn:oid:1.2.36.146.595.217.0.1",
      "value": "12345",
      "period": {
        "start": "2001-05-06"
      },
      "assigner": {
        "display": "Acme Healthcare"
      }
    }
  ],
  "active": true,
  "name": [
    {
      "use": "official",
      "family": "Chalmers",
      "given": [
        "Peter",
        "James"
      ]
    },
    {
      "use": "usual",
      "given": [
        "Jim"
      ]
    },
    {
      "use": "maiden",
      "family": "Windsor",
      "given": [
        "Peter",
        "James"
      ],
      "period": {
        "end": "2002"
      }
    }
  ],
  "telecom": [
    {
      "use": "home"
    },
    {
      "system": "phone",
      "value": "(03) 5555 6473",
      "use": "work",
      "rank": 1
    },
    {
      "system": "phone",
      "value": "(03) 3410 5613",
      "use": "mobile",
      "rank": 2
    },
    {
      "system": "phone",
      "value": "(03) 5555 8834",
      "use": "old",
      "period": {
        "end": "2014"
      }
    }
  ],
  "gender": "male",
  "birthDate": "1974-12-25",
  "_birthDate": {
    "extension": [
      {
        "url": "http://hl7.org/fhir/StructureDefinition/patient-birthTime",
        "valueDateTime": "1974-12-25T14:35:45-05:00"
      }
    ]
  },
  "deceasedBoolean": false,
  "address": [
    {
      "use": "home",
      "type": "both",
      "text": "534 Erewhon St PeasantVille, Rainbow, Vic  3999",
      "line": [
        "534 Erewhon St"
      ],
      "city": "PleasantVille",
      "district": "Rainbow",
      "state": "Vic",
      "postalCode": "3999",
      "period": {
        "start": "1974-12-25"
      }
    }
  ],
  "contact": [
    {
      "relationship": [
        {
          "coding": [
            {
              "system": "http://terminology.hl7.org/CodeSystem/v2-0131",
              "code": "N"
            }
          ]
        }
      ],
      "name": {
        "family": "du Marché",
        "_family": {
          "extension": [
            {
              "url": "http://hl7.org/fhir/StructureDefinition/humanname-own-prefix",
              "valueString": "VV"
            }
          ]
        },
        "given": [
          "Bénédicte"
        ]
      },
      "telecom": [
        {
          "system": "phone",
          "value": "+33 (237) 998327"
        }
      ],
      "address": {
        "use": "home",
        "type": "both",
        "line": [
          "534 Erewhon St"
        ],
        "city": "PleasantVille",
        "district": "Rainbow",
        "state": "Vic",
        "postalCode": "3999",
        "period": {
          "start": "1974-12-25"
        }
      },
      "gender": "female",
      "period": {
        "start": "2012"
      }
    }
  ],
  "managingOrganization": {
    "reference": "Organization/1"
  }
}
```

```json
// 사망 환자(시간을 사용한 경우)
{
  "resourceType": "Patient",
  "id": "pat3",
  "text": {
    "status": "generated",
    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">\n      \n      <p>Patient Simon Notsowell @ Acme Healthcare, Inc. MR = 123457, DECEASED</p>\n    \n    </div>"
  },
  "identifier": [
    {
      "use": "usual",
      "type": {
        "coding": [
          {
            "system": "http://terminology.hl7.org/CodeSystem/v2-0203",
            "code": "MR"
          }
        ]
      },
      "system": "urn:oid:0.1.2.3.4.5.6.7",
      "value": "123457"
    }
  ],
  "active": true,
  "name": [
    {
      "use": "official",
      "family": "Notsowell",
      "given": [
        "Simon"
      ]
    }
  ],
  "gender": "male",
  "birthDate": "1982-01-23",
  "deceasedDateTime": "2015-02-14T13:42:00+10:00",
  "managingOrganization": {
    "reference": "Organization/1",
    "display": "ACME Healthcare, Inc"
  }
}
```

## 8.1.14 Resource Patient - Detailed Descriptions

### Patient

Element Id : Patient

Definition :  관리, 기타 건강 관련 서비스를 받는 개인 또는 동물에 대한 인구통계 및 기타 관리 정보

Cardinality (표시할 수 있는 값의 범위):  0..*

Type : DomainResource

Requirements(요건) : 환자 추척은 의료 프로세스의 중심

Alternate Names(대체 이름): 진료 의뢰인 

### Patient.identifier

Element Id : Patient.identifier

Definition : 환자의 식별자

Note :  업무적인 식별자이며, 리소스 식별자가 아님

Cardinality : 0..*

Type : Identifier

Requirements : 환자에겐 거의 특정 숫자 식별자가 할당

Summary(개요) : true [http://hl7.org/fhir/search.html#summary](http://hl7.org/fhir/search.html#summary)

### Patient.active

Element Id : Patient.active

Definition : 환자 레코드 활성화 사용 여부. 많은 시스템이 기관의 규칙에 따라 일정기간동안 내원하지 않은 환자 등 이 속성을 활성화 하지 않은 환자로 표시하기 위해 사용.

활성화 되지 않은 환자를 제외하여 환자 목록을 필터링 하는데 자주 사용

사망한 환자도 또한 비활성으로 표시될 수 있지만, 사후 일정 기간동안은 활성 상태일 수도 있음

Cardinality : 0..1

Type : boolean

Is Modifier : true(이유: 이 요소는 레코드가 유요한 것으로  처리되지 않아야 함을 나타낼 수 있는 상태 요소이므로 편집자를 레이블로 지정)

Meaning if Missing :  활성 요소에 값을 제공하지 않는 경우 일반적으로 활성으로 표시

Requirements : 환자 레코드가 잘못 만들어 졌을때 사용할 수 없는 것으로 표시할 수 있어야 함

Summary : true

Comments : 레코드가 비활성화 상태이고 활성 레코드에 연결 된 경우 다른 환자에 대해 향후 환자/레코드 업데이트가 수행

### Patient.name

Element Id : Patient.name

Definition : 개인 이름

Cardinality :  0..*

Type : HumanName 

Requirements : 추적을 위해 환자의 여러 이름이 필요함(예시: 공식이름과 보호자(?)이름)

Summary : true

Comments : 환자의 이름은 여러개일 수 있으며, 용도나 기간이 다를 수 있음

동물의 경우, 사람이 지어주기 때문에 " 사람 이름" 이며 사람 과 같은 패턴을 가지고 있음

### Patient.telecom

Element Id : Patient.telecom

Definition : 개인에게 연락할 수 있는 연락처 세부정보(예: 전화번호 또는 이메일 주소)

Cardinality : 0..*

Type : ContactPoint

Requirements : 전화, 이메일과 같은 방법으로 연락을 취할 수 있음

Summary : true

Comments : 환자는 다양한 용도 또는 기간으로 연락할 수 있는 여러 가지 방법이 있을 수 있음. 긴급히 연락하고 신원을 확인을 도울 수 있는 옵션이 필요할 수 잇음.

주소는 환자를 대리 할 수 있는 다른 사람(예: 집 전화 또는 반려동물 주인) 에게 전달될 수 있음

### Patient.gender

Element Id :  Patient.gender

Definition : 관리 성별 - 환자가 관리 및 기록 보관 목적으로 갖는 것으로 간주

Cardinality : 0..1

Terminology Binding(용어 바인딩) : 

Type :  code

Requirements : 이름, 생년월일과 함께 개인 식별에 필요

Summary : true

Comments : 성별은 유전학이나 개인의 선호 식별에 의해 결정되는 생물학적 성별과 일치 하지 않을 수 있다. 인간, 특히 동물에게 비록 대다수의 시스템과 맥락이 남성과 여성만을 지지하지만, 남성과 여성보다 다른 합법적인 가능성이 있다는 것에 주목.

의사결정 지원을 제공하거나 사업 규칙을 적용하는 시스템은 관심의 특정 성별 또는 성별 측면을 다루는 관찰에 근거하여 이상적으로 이 작업을 수행해야 한다(해부학, 염색체, 사회적 등). 그러나 이러한 관측치는 자주 기록되지 않기 때문에 관리 성별로 기본 설정하는 것이 일반적입니다. 그러한 채무불이행이 발생할 경우 규칙 집행은 행정적 측면과 생물학적 측면, 염색체 및 기타 성별 측면 간의 변화를 허용해야 한다. 예를 들어 남성의 자궁 절제술에 대한 경보는 "하드" 오류가 아니라 경고 또는 재정의 가능한 오류로 처리되어야 합니다. 환자 성별 및 성별 소통에 대한 자세한 내용은 환자 성별 및 성별 섹션을 참조하십시오.

### Patient.birthDate

Element Id : Patient.birthDate

Definition : 개인의 생년월일

Cardinality : 0..1

Type : date

Requirements : 개인의 나이는 많은 임상 과정을 촉진

Summary :  true

Comments : 실제 생일을 알 수 없는 경우 추정 연도를 제공

시간이 필요한 경우(예: 출산, 유아관리 시스템) 표준 연장 " 환자 출생 시간"을 사용할 수 있음

LOINC Code :  21112-8

### Patient.address

Element Id :  Patient.address

Definition :  개인 주소

Cardinality : 0..*

Type :  Address

Requirements : 연락, 청구서 청구 또는 필요한 것을 알리고 식별에 도움이 되는 환자 주소를 추적해야 할 수 있음

Summary : true

Comments : 환자는 용도 또는 기간이 다른 여러 주소를 가질 수 있음

### Patient.maritalStatus

Element Id : Patient.maritalStatus

Definition : 이 필드는 환자의 최근 혼인 상태가 있음.

Cardinality : 0..1

Terminology Binding: 결혼 여부(확장 가능)

Type : CodeableConcept

Requirements : 모든 제도가 캡처하는 것은 아니지만 대부분임

### Patient.photo

Element Id : Patient.photo

Definition : 환자의 사진

Cardinality : 0..*

Type : Attachment

Requirements : 많은 EMR 시스템은 환자의 사진을 캡처 할 수 있는 기능을 가지고 있음.

새로운 소셜 미디어 사용에도 적합

Comments : 가이드라인

- 임상 사진이 아닌 id사진을 이용
- 사이즈를 썸네일로 제한
- 리소스 업데이트를 쉽게 하려면 바이트 수를 낮게 유지

### Patient.contact

Element Id : Patient.contact

Definition : 환자를 위한 연락처 집단( 예: 보호자, 친구)

Cardinality : 0..*

Requirements : 환자에 대해 연락할 수 있는 사람을 추적

Comments : 연락처는 가족, 업무 연락처, 보호자, 간병인 등 모든 종류의 연락처에 적용.

연락을 취할 수 없는 가족을 등록할 수 없음

Invariants :  규칙 : 최소한의 연락처의 세부사항이나 조직에 대한 참조를 포함

### Patient.contact.relationship

Element Id :  Patient.contact.relationship

Definition : 환자와 연락하는자와 관계 특성

Cardinality : 0..*

Terminology Binding: 환자와 연락하는 관계(확장 가능)

Type : CodeableConcept

Requirements : 상황에 따라 어떤 연락 하는 사람이 가장 관련이 있는지 결정하는데 사용

### Patient.contact.name

Element Id : Patient.contact.name

Definition : 연락처 사용자와 관련된 이름

Cardinality : 0..1

Type : HumanName

Requirements : 연락처 담당자를 이름으로 식별해야 하지만, 해당 연락처 담당자에 대한 다른 여러 이름에 대한 세부 정보가 필요한 경우는 흔치 않음

### Patient.contact.telecom

Element Id : Patient.contact.telecom

Definition : 전화 번호 또는 메일 주소와 같은 당사자의 연락처 세부 정보

Cardinality : 0..*

Type : ContactPoint

Requirements : 사람들은 전화, 이메일과 같은 방법으로든 연락을 취할 수 있는 방법들이 있음

Comments : 연락처에는 다양한 

### Patient.contact.address

Element Id : Patient.contact.address

Definition : 연락처 사용자와 관련된 주소

Cardinality : 0..1

Type : Address

Requirements : 우편으로 연락하거나 방문할 수 있는 연락처 위치 추적해야함

### Patient.contact.gender

Element Id : Patient.contact.gender

Definition : 관리 성별 - 연락 담당자가 관리 및 기록 보관 목적으로 갖는 것으로 간주되는 성별

Cardinality : 0..1

Terminology Binding: 괸리 성별(필수)

Type : code

Requirements : 그 사람 주소를 정확하게 하는데 필요 함

### Patient.contact.organization

Element Id : Patient.contact.organization

Definition : 연락이 가능 한 조직

Cardinality : 0..1

Type : Reference(Organization)

Requirements : 보호자 또는 비즈니스관련 연락처의 경우 조직과 관련

Invariants : 규칙 : 최소한 연락처의 세부 사항이나 조직에 대한 정보를 포함해야 함

### Patient.contact.period

Element Id : Patient.contact.period

Definition : 환자 또는 조직에 대해 연락할 수 있는 기간

Cardinality : 0..1

Type : Period

### Patient.communication

Element Id : Patient.communication

Definition : 환자의 건강에 대해 환자와 대화할 때 사용할 수 있는 언어

Cardinality : 0..*

Requirements : 환자가 현지 언어를 구사하지 못하는 경우 통역사가 필요할 수 있으며 환자와 다른 사람 모두를 위해 언어 구사 및 숙련도가 중요한 사항

Comments : 언어가 지정되지 않은 경우 기본 로컬 언어가 사용되고 있음을 의미

여러 언어에 대한 숙련도를 전달해야하는 경우 여러 환자가 필요

통신 연결, 동물에게 언어는 관련 분야가 아니므로 해당 분야에서 빠져야 함

환자가 기본 로컬언어를 사용하지 않는 경우 통역 표준을 사용하여 통역이 필요하다고 명시적으로 선언 할 수 있음

### Patient.communication.language

Element Id : Patient.communication.language

Definition : 언어의 경우 ISO-639-1 alpha 2 코드, 대문자에는 하이픈과 ISO-3166-1 alpha 2 코드(예: 영어의 경우 "en", 미국 영어의 경우 "en-US" 대 영국 영어의 경우 "en-EN" 등)가 뒤따름

Cardinality : 1..1

Terminology Binding : 공용 언어(기본 설정 되지만 모든 언어로 제한)

Type : CodeableConcept

Requirements : 다국어 국가의 대부분의 시스템은 언어를 전달하기를 원함

모든 시스템이 실제로 지역 방언을 필요로 하지는 않음

Comments : 이 정확한 대소문자를 가진 aa-BB 구조는 로케일에서 가장 널리 사용되는 표기법 중 하나입니다. 그러나 모든 시스템이 실제로 이것을 코딩하는 것이 아니라 자유 텍스트로 가지고 있습니다. 따라서 데이터 유형으로 코드 대신 CodeableConcept를 사용합니다.

### Patient.communication.preferred

Element Id : Patient.communication.preferred

Definition : 환자가 특정 레벨에서 마스터하는 다른 언어보다 이 언어를 선호하는지 여부를 나타냄

Cardinality : 0..1

Type : boolean

Requirements : 특정 수준까지 여러 언어를 마스터 하는 사람들은 하나 이상의 언어를 선호할 수 있음. 특정 언어로 의사소통 하는 데 더 자신감을 느낄 수 있음

Comments : 이 언어는 의료 정보 전달을 위해 특별히 식별

### Patient.generalPractitioner

Element Id : Patient.generalPractitioner

Definition : 환자의 부양자

Cardinality : 0..*

Type : Reference(Organization | Practitioner | PractitionerRole)

Alternate Names: careProvider

Comments: 

이는 1차 진료 제공자(GP 맥락에서)일 수도 있고, 커뮤니티/장애 환경에서 환자 지명 진료 관리자일 수도 있고, 심지어 의료 제공자 역할을 수행하도록 사람들을 제공하는 조직일 수도 있다. Care Team을 기록하는 데 사용할 수 없으며, Care Plan 또는 EpisodeOfCare 리소스와 연결될 수 있는 CareTeam 리소스에 있어야 합니다. 학기 중 대학 GP와 함께 집 GP를 등록한 학생이나 현장 GP도 집 GP에 포함시켜 의료 문제를 인지하는 '플라이인/플라이아웃' 근로자 등 다양한 이유로 환자를 상대로 복수의 GP를 기록할 수 있다.

관할구역은 원하는 경우 이를 1개 또는 유형별로 1개로 프로파일링할 수 있다고 결정할 수 있다.

### Patient.managingOrganization

Element Id : Patient.managingOrganization

Definition : 환자의 기록을 관리하는 조직

Cardinality : 0..1

Type : Reference(Organization)

Requirements: 누가 이환자 기록을 인식히고 관리하고 업데이트 하는지 알아야 함

Summary: true

Comments : 특정 환자 기록을 관리하는 조직은 하나뿐. 다른 조직에는 자체 환자 레코드가 있으며 Link속성을 ㅎ사용하여 레코드를 함께 결합할 수 있음(또는 연결에 대한 신뢰 등급을 포함할 수 있는 사용자 리소스)

### Patient.link

Element Id : Patient.link

Definition : 동일한 환자와 관련된 다른 환자 리소스에 연결

Cardinality : 0..*

Is Modifier: true(이유:이 요소는 기본 Patient 리소스가 아닐 수 있으므로 수정자로 레이블이 지정되며 이 Patient 레코드 대신 참조된 환자를 사용해야 함. link.type 값이 '대체 대상'인 경우)

Requirements: 여러 가지 활용 사례가 있음

- 일관되게 사람을 식별하기 어려운 경우 사무적 오류로 인해 환자 기록을 복제
- 여러 서버에 걸쳐 환자 정보를 배폰

Summary: true

Comments : 연결된 환자 기록에 상호 연관성이 있다는 가정은 없음

### Patient.link.other

Element Id : Patient.link.other

Definition :  링크가 참조하는 다른 환자 리소스

Cardinality : 1..1

Type: Reference(Patient | RelatedPerson)

Hierarchy:이 참조는 동일한 인스턴스(순간 포함)를 가리킬 수 있음

Summary: true

Comments : 관련 인물을 참조하면 환자와 관련 인물을 동일한 개인으로 연결하기 위해 사용자 레코드를 사용할 필요가 없음

### Patient.link.type

Element Id : Patient.link.type

Definition : 이 환자의 리소스와 다른 환자 리소스간의 링크 유형

Cardinality : 1..1

Terminology Binding: 링크유형(필수)

Type : code

Summary: true

## 8.1.16 Resource Patient - Extensions & Profiles

### **8.1.16.1 Profiles**

이 리소스에 대한 정의된 프로파일이 존재하지 않음

### 8.1.16.2 Extensions