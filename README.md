# :fire: FHIR

## :pushpin: FHIR 리소스 정리

### 1.2 Resource Index

#### :cherries:Foundation 

| Conformance                                                  | Terminology                                                  | Security                                      | Documents                                                    | Other                                                        |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------------------------------------- | :----------------------------------------------------------- | ------------------------------------------------------------ |
| • CapabilityStatement <br/>• StructureDefinition <br/>• ImplementationGuide <br/>• SearchParameter <br/>• MessageDefinition<br/>• OperationDefinition<br/>• CompartmentDefinition <br/>• StructureMap <br/>• GraphDefinition <br/>• ExampleScenario | • CodeSystem <br/>• ValueSet <br/>• ConceptMap <br/>• NamingSystem <br/>•TerminologyCapabilities | •Provenance <br/>• AuditEvent <br />• Consent | • Composition <br/>• DocumentManifest •DocumentReference <br/>• CatalogEntry | • Basic <br/>• Binary <br/>• Bundle <br/>• Linkage <br/>• MessageHeader <br/>•OperationOutcome • Parameters <br/>• Subscription |

#### :strawberry: Base


| Individuals                                                  | Entities #1                                                  | Entities #2                                                  | Workflow                                                     | Management                                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| • Patient <br/>• Practitioner <br/>• PractitionerRole <br/>• RelatedPerson <br/>• Person <br/>• Group | • Organization<br/>• OrganizationAffiliation <br/>• HealthcareService <br/>• Endpoint <br/>• Location | • Substance <br/>• BiologicallyDerivedProduct <br/>• Device <br/>• DeviceMetric | • Task <br/>• Appointment <br/>• AppointmentResponse <br/>• Schedule <br/>• Slot <br/>• VerificationResult | • Encounter <br/>•EpisodeOfCare<br/> • Flag <br/>• List<br/> • Library |

#### :apple:Clinical

| Summary                                                      | Diagnostics                                                  | Medications                                                  | Care Provision                                               | Request & Response                                           |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| • AllergyIntolerance <br/>• AdverseEvent <br/>• Condition (Problem) <br/>• Procedure <br/>•FamilyMemberHistory <br/>•ClinicalImpression<br/>•DetectedIssue | • Observation <br/>• Media <br/>• DiagnosticReport <br/>• Specimen <br/>• BodyStructure<br/>•ImagingStudy <br/>•QuestionnaireResponse • MolecularSequence | • MedicationRequest <br/>• MedicationAdministration <br/>• MedicationDispense <br/>• MedicationStatement <br/>• Medication <br/>• MedicationKnowledge <br/>• Immunization <br/>• ImmunizationEvaluation <br/>•ImmunizationRecommendation | • CarePlan <br/>• CareTeam <br/>• Goal <br/>• ServiceRequest <br/>• NutritionOrder <br/>•VisionPrescription • RiskAssessment <br/>• RequestGroup | • Communication <br/>•CommunicationRequest • DeviceRequest <br/>• DeviceUseStatement <br/>• GuidanceResponse <br/>• SupplyRequest <br/>• SupplyDelivery |

#### :watermelon: Financial

| Support | Billing | Payment | General |
| ------- | ------- | ------- | ------- |
|         |         |         |         |

#### :tomato:Specialized

| Public Health & Research | Definitional Artifacts | Evidence-Based Medicine | Quality Reporting & Testing | Medication Definition |
| ------------------------ | ---------------------- | ----------------------- | --------------------------- | --------------------- |
|                          |                        |                         |                             |                       |

