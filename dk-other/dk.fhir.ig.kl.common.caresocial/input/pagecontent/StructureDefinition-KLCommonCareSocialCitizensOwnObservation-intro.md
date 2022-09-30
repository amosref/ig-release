### Scope and usage
CommonCareSocialCitizensOwnObservation is used to document, performance level (udførelse) or importance level (betydning) as defined by FSIII. Note that each of the observations require its own instance of this model. The observation only makes sense linked to an already defined Condition or MatterOfInterest. Consequently, the focus-attribute is mandatory.

The code-attribute refers to either performance level or importance level using a required ValueSet, and the result is expressed in valueCodeableConcept, which is also bound to a required FSIII valueSet. Observation and value codes should be correctly matched, so that a performance-result is not used with a importance observation-code.

Note that the profile does not specify explicitely, which role the citizen had in evaluating his or her own performance/importance level. The model just presumes that the citizen (refered in Observation.subject) has been asked about their own evaluation of the matter, and that is has been documented by a municipality practitioner (refered in Observation.performer). However, if further specification of roles in the documentation proces is required for a specific use case, please use [Provenance](https://www.hl7.org/fhir/provenance.html).

The encounter in which the citizen make the observation can be refered to in Observation.encounter. Notice that the status-attribute is mandatory. For normal use, just set to "final". If data is missing or another problem has occured, follow the FHIR guidance to populate the field correctly.

### Conversions between Danish information model and FHIR-profile

Nedenstående tabel oversætter mellem de attributter, der er defineret i den fælleskommunale informationsmodel (FKI), definerer kort den enkelte attribut på dansk og specificerer, hvilke af FHIR-profilens atributter der skal bruges til specifikation af indholdet. 

{:class="grid"}
|   FKI-attribut      | Definition        | FHIR  |
| ------------- |-------------| -----|
|borgervurderingskode|Klasse som udtrykker, at der observeres på borgers evne til at udføre funktion eller aktivitet.|Observation.code.coding|
|borgervurderingsresultat|Klasse, der udtrykker resultatet af borgers vurdering.|Observation.valueCodeableConcept.coding|
|borgervurderingssubjekt|Den borger, som er genstad for vurdering.|Observation.subject|
|borgervurderingskontakt|Den kontakt, hvor vurderingen er foretaget.|Observation.encounter|
|borgervurderingsansvarlig|Den fagperson der er ansvarlig for observationen.|Observation.performer|
|borgervurderingsfokus|Tilstand eller matter of interest, som denne borgervurdering er direkte observation på.|Observation.focus|
|borgervurderingstid|Tidspunkt for borgervurderingen.|Observation.effectiveDateTime|
|borgervurderingsstatus|Klasse der udtrykker, hvor i sin proces, borgervurderingen er.|Observation.status|