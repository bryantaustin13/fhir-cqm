{: #profiles}

## Capability Profiles
{: #capability-profiles}

To define the exchange expectations for measure and library artifacts at different points along the content lifecycle, this implementation guide uses four general categories of profiles, aligned with those established by the Canonical Resource Management Infrastructure (CRMI) implementation guide:

* Shareable - Define the minimum expectations for systems that exchange measure and library artifacts
* Computable - Define elements that are important for the computable representation of a measure (i.e. design-time characteristics and authoring-level concerns)
* Publishable - Define elements that are relevant for publishing and distribution concerns
* Executable - Define elements that are important for the run-time and implementation-level concerns

### Measure Profiles
{: #measure-profiles}

Measure profiles supported in this IG are defined to allow for use independently or in combination with each other to support a wide range of use cases. The diagram depicts these capability profiles and their relationships to the profiles defined in CRMI and the Using CQL With FHIR IGs:

<b>Figure 7-1: Measure Profiles Relationship Diagram</b>

{% include img.html img="profile-diagram.png" %}

| **Capability** | **Profile** | **Description** |
|----|----|----|
| Shareable | [CRMIShareableMeasure]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-shareablemeasure.html)  |  The shareable measure profile defines minimal expectations for exchanging a measure.  | 
| Computable | [CQMComputableMeasure](StructureDefinition-cqm-computablemeasure.html)  |  The computable measure profile defines the elements and constraints that are required to represent the calculation of a measure score, regardless of the specific language used to communicate the criteria expressions   |
| Publishable | [CQMPublishableMeasure](StructureDefinition-cqm-publishablemeasure.html)  |  The publishable measure profile defines the expectations and constraints for metadata associated with formal publication of a measure specification.   | 
| Executable | [CQMExecutableMeasure](StructureDefinition-cqm-executablemeasure.html)  | The executable measure profile defines the elements that are required to support execution of a measure in an implementation environment.    | 
{: .grid }

In addition to conforming to profiles to support appropriate function or representation, measures are required to conform to the appropriate measure profile based on their scoring type:

<table class="grid">
  <tr><th>Scoring Type</th><th>Profile</th></tr>
  <tr><td>Cohort</td><td><a href="StructureDefinition-cqm-cohortmeasure.html">CQMCohortMeasure</a></td></tr>
  <tr><td>Proportion</td><td><a href="StructureDefinition-cqm-proportionmeasure.html">CQMProportionMeasure</a></td></tr>
  <tr><td>Ratio</td><td><a href="StructureDefinition-cqm-ratiomeasure.html">CQMRatioMeasure</a></td></tr>
  <tr><td>Continuous Variable</td><td><a href="StructureDefinition-cqm-cvmeasure.html">CQMContinuousVariableMeasure</a></td></tr>
  <tr><td>Composite</td><td><a href="StructureDefinition-cqm-compositemeasure.html">CQMCompositeMeasure</a></td></tr>
  <tr><td>Attestation</td><td><a href="StructureDefinition-cqm-attestationmeasure.html">CQMAttestationMeasure</a></td></tr>
</table>

As well, the profiles are designed to separate communication of the computable aspects from the specific expression language used to communicate criteria. This implementation guide supports specification of expression criteria using Clinical Quality Language (CQL) and Expression Logical Model (ELM) (i.e. compiled CQL), but other expression languages could be used with this IG if desired:

<table class="grid">
  <tr><th>Language</th><th>Profile</th></tr>
  <tr><td>CQL</td><td><a href="StructureDefinition-cqm-cqlmeasure.html">CQLMeasure</a></td></tr>
  <tr><td>ELM</td><td><a href="StructureDefinition-cqm-elmmeasure.html">ELMMeasure</a></td></tr>
</table>

### Library Profile Usage
{: #library-profile-usage}

This implementation guide makes use of Library resources in two ways:

1. As the container for computable and/or executable representations of expression logic used as criteria in quality measure specifications.
2. As a [_manifest_]({{site.data.fhir.ver.crmi}}/version-manifest.html) for communicating the information required to make use of a set of measure specifications, including dependency and version information.

#### Logic Library Profile Usage
{: #logic-library-profile-usage}

This implementation guide does not introduce any new logic library profiles, but makes use of library profiles defined in the Canonical Resource Management Infrastructure and Using CQL With FHIR implementation guides:

| **Shareable** | **Computable** | **Publishable** | **Executable** |
|----|----|----|----|
| [CRMIShareableLibrary]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-shareablelibrary.html) | [CRMIComputableLibrary]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-computablelibrary.html) | [CRMIPublishableLibrary]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-publishablelibrary.html) | [CRMIExecutableLibrary]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-executablelibrary.html)  |
{: .grid }

For measures that use Clinical Quality Language to represent expression logic, the following profiles are used:
 
| **Shareable** | **Computable** | **Publishable** | **Executable** |
|----|----|----|----|
| N/A | [CQLLibrary]({{site.data.fhir.ver.cql}}/StructureDefinition-cql-library.html) | N/A | [ELM JSON Library]({{site.data.fhir.ver.cql}}/StructureDefinition-elm-json-library.html) <br/> [ELM XML Library]({{site.data.fhir.ver.cql}}/StructureDefinition-elm-xml-library.html)  |
{: .grid }

#### Manifest Library Profile Usage
{: #manifest-library-profile-usage}

| **Shareable** | **Publishable** |
|----|----|
| [CRMIShareableLibrary]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-shareablelibrary.html) | [CRMIPublishableLibrary]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-publishablelibrary.html) <br/>[CRMIManifestLibrary]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-manifestlibrary.html) |
{: .grid }

### Terminology Profile Usage
{: #terminology-profile-usage}

This implementation guide does not introduce any new terminology profiles, but makes use of terminology profiles defined in the Canonical Resource Management Infrastructure implementation guide:

| **Artifact** | **Shareable** | **Computable** | **Publishable** | **Executable** |
|----|----|----|----|----|
| CodeSystem | [CRMIShareableCodeSystem]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-shareablecodesystem.html) | N/A (no requirements) | [CRMIPublishableCodeSytems]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-publishablecodesystem.html) | N/A (no requirements) |
| ValueSet | [CRMIShareableValueSet]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-shareablevalueset.html) | [CRMIComputableValueSet]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-computablevalueset.html) | [CRMIPublishableValueSet]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-publishablevalueset.html) | [CRMIExpandedValueSet]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-expandedvalueset.html) |
{: .grid }

* Note that due to the varying terminology capabilities of target environments, terminology profiles do not necessarily correspond to the capabilities of the measure and library resources. For example, a Computable measure package may include both Computable and Expanded value set resources, depending on the expected capabilities of the target environment with respect to each code system involved. 

### Additional Profiles
{: #additional-profiles}

To support packaging, testing, and distribution of measure and library artifacts, this implementation guide defines the following additional profiles: 

| **Profile** | **Description** | 
|----|----|
| [CRMISoftwareSystemDevice]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-softwaresystemdevice.html) | A software device used in the creation, validation, evaluation, packaging, and/or testing of a library or measure artifact.  |
| [CRMIManifestLibrary]({{site.data.fhir.ver.crmi}}/StructureDefinition-crmi-manifestlibrary.html) |  Used to establish a set of measures together with the version information for code system and value sets referenced by those measures. See the [Manifest](measure-conformance.html#manifest) topic for more information.  |
| [CQMTestCase](StructureDefinition-cqm-testcase.html) | A measure report profile that allows definition and exchange of test cases for a measure.  |
{: .grid }

## Alphabetical Listing

See the [Artifact Index - Structures: Resource Profiles](artifacts.html#structures-resource-profiles) for an alphabetical index of profiles defined in this implementation guide.
