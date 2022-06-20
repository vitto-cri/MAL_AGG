# Malaria - System Design Document { #mal-agg-200-design}

Version 2.0.0

## Background and Purpose

The Malaria Core Aggregate System Design document provides an overview of the design principles and guidance used to develop the digital data package for routine aggregate malaria reporting in countries’ HMIS. This document is intended for use by DHIS2 implementers at country and regional level to be able to support implementation and localisation of the package. The Malaria metadata package can be adapted to local needs and national guidelines. In particular, local work flows and national guidelines should be considered in the localization and adoption of the programs included in this package.

The data sets have all been based either on WHO recommendations and best-practice examples or published reporting frameworks [Disease surveillance for malaria control](https://apps.who.int/iris/bitstream/handle/10665/44851/9789241503341_eng.pdf;jsessionid=7D2258370F31444A72815B5CFB2E1FE8?ua=1?sequence=1).

These data sets will in many instances have to be adjusted to fit with national reporting systems, to varying degrees. On the one hand, there might be additional variables that are important in a national context which must be added. On the other hand, there might be information that is simply not available for reporting, for example if the data is not captured in the case-based registers at the clinical level.

## System Design Overview

### Version update

The version of the malaria package described in this design guide is an improved and more comprehensive adaptation of the package with version 1.2.1. Please refer to the downloadable [Diff File](resources/mal_agg_diff_1.2.1_2.0.0.xlsx) in order to have an overview of the differences between teh two versions.

### Package Structure

The malaria program consists of 3 different data sets that can be used at any given time based on the needs of the program:

| Dataset                  | Description     |
|---------|--------|
| **Malaria annual data**      | The malaria annual data set is recommended in all settings. It contains the key info on the target/catchment population.<br>As the name indicates, this information is to only be collected once a year.<br>This data set contains a mostly flat structure.<br>It is suggested to assign the dataset at district level, though the assignment can change at local level depending on the availability of population data. |
| **Malaria burden reduction** | This is a monthly data set that is meant for areas in which malaria burden reduction is the priority. <br>The dataset is designed to report data at the lowest administrative level present in the organizational unit hierarchy.    |
| **Malaria elimination**      | This is a monthly data set intended for areas where malaria elimination is the priority. <br>The dataset is designed to report data at the lowest administrative level present in the organizational unit hierarchy.     |

>**NOTE**:
>
>The malaria elimination and malaria burden reduction data sets can be used either separately or in conjunction with one-another depending on the type of public health responses being implemented within a particular geographical area (ie. in one district the burden reduction data set may be used, while in another the malaria elimination data set may be used).

### Data Elements

The full list of data elements belonging to the different datasets can be found in the [Malaria Metadata Reference File](resources/metadata.xlsx).

Please note that there are a number of additional data elements that could potentially be used within the Malaria Burden Reduction and Malaria Elimination data sets, however are not currently assigned to either of the datasets. These data elements can be found within the Malaria unassigned data element group.

| Dataset                  | Unassigned DEs       |
|--------------------------|----|
| Malaria Burden Reduction | Migrant and mobile population (MMP) positive<br>Malaria cases tested at community level<br>Malaria confirmed cases (Mic + RDT)<br>Plasmodium falciparum (Mic + RDT)<br>Malaria cases positive at community level<br>Migrant and mobile population (MMP) tested<br>Migrant and mobile population (MMP) followed up for 14 days<br>Mixed malaria species (Mic + RDT)<br>Plasmodium vivax (Mic + RDT)<br>Malaria tested cases (Mic + RDT)<br>Malaria cases treated at community level<br>Mixed/Other malaria species (Mic + RDT) |
| Malaria Elimination      | Malaria tested from cross-borders<br>Malaria cases notified within (N1) timeframe of the guideline (24hrs)<br>Malaria cases investigated within (N2)* timeframe of the guideline<br>Malaria positive from cross-borders followed for 14 days<br>Malaria positive from cross-borders<br>Other malaria species (microscopy)      |

### Intended users

- **Health facility users**: capture and report key data on malaria activities
- **Program managers**: managers at national and sub-national level may be responsible for supporting data entry and analysis.
- **National and local health authorities**: to monitor and analyze the surveillance of data through dashboards and analytics tools, to conduct risk assessments and plan response measures; to generate reports for regional and global reporting

### Data Set - Malaria Annual Data

#### Population at risk

![Population at risk](resources/images/MAL_POP_001.png)

This disaggregation of the population was set as a category combination, as it is more efficient to disaggregate this population data element by the three age category options rather than create three data elements separately.

#### Interventions

![Interventions](resources/images/MAL_POP_002.png)

The section has a flat structure and focuses on the preventive interventions carried out in the target area and within the groups most at risk of infection. Contrary to the annual demographic data, this information is rather meant to be compiled at the end of a LLINs distribution intervention.

### Data Set - Malaria Burden Reduction

The Malaria Burden Reduction dataset is split in seven sections. Two of these sections are identical both in this dataset and in the Malaria Elimination dataset: Laboratory, Treatment.

#### Patients Volume

![Volume of patients](resources/images/MAL_MBR_020.png)

The age category combination (0-4, 5-14, 15+ years) drastically reduces the number of data elements. The totals for all of these data elements can also be used for analysis purposes.

#### Laboratory

![Lab](resources/images/MAL_MBR_002.png)

The age/sex category combination {Age (0-4, 5-14, 15+ years)/Sex (Male, Female)} drastically reduces the number of data elements. The totals for all of these data elements can also be used for analysis purposes; allowing you to pivot both the age and sex dimensions and place them where required.

#### Treatment

![Treatment of Malaria](resources/images/MAL_MBR_003.png)

Several of the data elements in this section are subsets of one another. Making totals from these would not be meaningful. Though this increases the data element count, it makes interpreting the output easier.

#### Intermittent Preventive Treatment in pregnancy (IPTp)

![IPTp](resources/images/MAL_MBR_005.png)

While it could potentially be argued that a category combination could potentially be used here in order to output the total number of doses administered, understanding the breakdown of the number of doses by their schedule takes precedence in the analysis. For this reason, no category combination is used.

#### Pregnant Women

![Pregnant women](resources/images/MAL_MBR_006.png)

All of the data elements in this section have different definitions. No disaggregations required.

### Data Set - Malaria Elimination

The Malaria Elimination dataset is split in seven sections. Two of these sections are identical both in this dataset and in the Malaria Burden Reduction dataset: Laboratory, Treatment.

#### All-cause inpatients and outpatients

![IPD and deaths](resources/images/MAL_ME_001.png)

The age category combination (0-4, 5-14, 15+ years) reduces the number of data elements. The totals for the two data elements can also be used for analysis purposes.

#### Case Investigation

![Case investigation](resources/images/MAL_ME_003.png)

The age/sex category combination {Age (0-4, 5-14, 15+ years)/Sex (Male, Female)} drastically reduces the number of data elements. The totals for all of these data elements can also be used for analysis purposes.

#### Laboratory

![Lab](resources/images/MAL_ME_002.png)

The age/sex category combination {Age (0-4, 5-14, 15+ years)/Sex (Male, Female)} drastically reduces the number of data elements. The totals for all of these data elements can also be used for analysis purposes; allowing you to pivot both the age and sex dimensions and place them where required.

#### Active Case Detection

![Treatment of Malaria](resources/images/MAL_ME_008.png)

All of the data elements in this section have different definitions. No disaggregations required.
Case Investigation

![Malaria case investigation](resources/images/MAL_ME_004.png)

The age/sex category combination {Age (0-4, 5-14, 15+ years)/Sex (Male, Female)} drastically reduces the number of data elements. The totals for all of these data elements can also be used for analysis purposes; allowing you to pivot both the age and sex dimensions and place them where required.

#### Treatment

![Treatment](resources/images/MAL_ME_009.png)

Several of the data elements in this section are subsets of one another. Making totals from these would not be meaningful. Though this increases the data element count, it makes interpreting the output easier.

#### Foci Investigation

![Malaria foci investigation](resources/images/MAL_ME_005.png)

Several of the data elements in this section are subsets of one another. Making totals from these would not be meaningful. Though this increases the data element count, it makes interpreting the output easier.

#### Foci Classification and Response

![Malaria foci classification and response](resources/images/MAL_ME_006.png)

The foci classification category combination (Active, Residual, Cleared-up) allows for simplified classification of the data elements based on the three foci category options. The total of this category combination when applied to the data elements is useful for analysis as well.

#### Stock-out

![Stock management](resources/images/MAL_ME_007.png)

These data elements are all of yes/no type. No disaggregations required.
This section can be removed should the implementation require the uptake of the [MAL - Malaria stock dataset](https://docs.dhis2.org/en/topics/metadata/malaria/malaria-logistics/malaria-logistics-design.html) within the Malaria Package.

## Analytics and Indicators

The full list of indicators and indicator groups is available in the [Malaria Metadata Reference File](resources/metadata.xlsx).

Please refer to the section “Special Considerations: Malaria by health sector” of this design guide for further guidance on how to obtain further information on the cases of malaria detected in the different health sectors (private, public, and community).

## Validation Rules

The validation rules for malaria are divided across three groups:

- **Malaria: burden reduction**
- **Malaria: elimination**
- **Malaria: other**

The full list of validation rules that have been set-up to ensure the quality of data are available in the [Malaria Metadata Reference File](resources/metadata.xlsx).

## Dashboards

The Malaria package includes nine predefined dashboards, each focusing on different aspects of the preventive, curative, and reactive sides of the health programmes against malaria:

- MAL - 1.Malaria Burden Reduction;
- MAL - 2.Testing and diagnosis;
- MAL - 3.Malaria Maps;
- MAL - 4.Treatment;
- MAL - 5.Intervention Coverage;
- MAL - 6.Malaria Quality Control;
- MAL - 7.Malaria Data Quality;
- MAL - 8.Malaria Elimination;
- MAL - 9. Malaria Stock

The full list of items (graphs and tables) available in each dashboard is available in the [Malaria Metadata Reference File](resources/metadata.xlsx).

The table below lists only the dashboards in which there are notes of interest for the implementation of the package and the set-up of the dashboards

| Dashboard                        | Comment   |
|--------------|-----|
| MAL - 1.Malaria Burden Reduction | In the graph and table entitled “Reported malaria cases “ , the DE MAL- Confirmed malaria cases (reported), depending on the local implementation and guidelines, could be used instead of the DE “confirmed malaria cases (micr + RDT)”<br>The graph entitled “Epidemic detection” uses in its default configuration the DE MAL - Malaria confirmed MEAN+2 STD (threshold). Countries should choose either the mean+2SD OR the MEDIAN (threshold), but not both. The latter is suggested for elimination settings. The DEs are in the burden reduction data elements group. |
| MAL - 4.Treatment                | The graphs entitled “Treatment of P.vivax” and “G6PD testing and treatment of P.vivax” are optional and only relevant depending on the context.   |

## User groups

As part of the package configuration, user groups have been created to be used to manage sharing settings in the metadata for all the modules. Core metadata that use these sharing settings include mainly the dataSets, dashboard, indicators and data Elements.
The three user groups created include:

| User group       | Dashboard         | Program Metadata  | Program data         |
|------------------|-------------------|-------------------|----------------------|
| MAL - Admin        | Can edit and view | Can edit and view | Can view only        |
| MAL - Access       | Can view only     | Can view only     | Can view only        |
| MAL - Data capture | No access         | Can view only     | Can capture and view |

Whereas it is important to maintain these userGroups while installing this package, feel free to review them in line with any existing userGroups setup or policy in the host instance.

## Special Considerations: Malaria by health sector

As mentioned in the section on Analytics and Indicators of this design guide, this section is set to provide some suggestions and considerations on the analysis and visualization of the detected cases of malaria according to the type of facility ownership (public or private), and the cases detected in the community.

The WHO requirements for the CORE malaria aggregate  data reporting included the following indicators:

- “MAL - Malaria cases detected in the public sector (%)”
- “MAL - Malaria cases detected in the private sector (%)”
- “MAL - Malaria cases detected in the community (%)”

Given the wide range of set-ups and configurations of the hierarchy and organizational units (OUs), this section will advise the users and implementers a few solutions and propositions.

### Malaria cases detected in the public and private sector

As of the latest DHIS2 version release (2.37) the number of facilities can still only be obtained by setting up a **predictor**.

In order to ease the technical configuration of the package, a solution to this could be the use of a DE or an indicator (e.g. MAL - Confirmed malaria cases (micr + RDT) or MAL - Malaria cases detected) and filter the analysis by the groupSet assigned to the OUs (private or public).

In the screenshot below, an example of the Private and Public OU Groups and below the facilities selected to belong to the Public group.

![Organization Unit Group for facilities](resources/images/MAL_SDG_001.png)

![Organization Units assigned to the Public OU group](resources/images/MAL_SDG_002.png)

Once the OUs are arranged by OU groups, the Public and Private groups can be further categorized in an “Ownership” OU Group Set and it should be of type data dimension for it to be used as analytic filter or dimension.

![OU Group Set for Public and private OU groups](resources/images/MAL_SDG_002.png)

Once the data is entered in the datasets in all the required OUs, the user can analyze the data in the system by health sector. Depending on the final purpose of this specific analysis, the data can be visualized using the wide range of DHIS2 core analytics, though it could be recommended to analyze these in one or more maps filtered by the different ownership OU groups.

### Malaria cases detected in the community

Depending on the local implementation and context, the community level of the health activities and interventions can either be set-up aside, or can be already fully integrated among the health facilities and various admin levels of the OUs.

There are two options that can be used in order to analyze the data coming from the community:
Use the same approach as outlined in the previous section and create an OU group for the communities in the hierarchy. The procedure and analysis of the data will then follow the same method as the public and private OU groups.
Download and update the relevant metadata from the [Community Health Information System (CHIS) package](#chis-system-design), map the relevant metadata, and triangulate the information with the ones obtained from the malaria package(s).
In particular there are two monthly datasets that can be useful for this specific purpose within the CHIS package: The [CH - Malaria](#ch-mal-aggregate-design) dataset and the [CH - Community-based Surveillance](#ch-cbs-aggregate-design) dataset. Some relevant DEs for the data triangulation of malaria information can also be obtained from the [CH - Integrated Community Case Management](#ch-iccm-aggregate-design) monthly dataset in the CHIS package.

## References

World Health Organization (2012). Disease Surveillance for Malaria Control. An operational manual. Printed by the WHO Document Production Services, Geneva, Switzerland. ISBN 978 92 4 150334 1. URL: [https://apps.who.int/iris/bitstream/handle/10665/44851/9789241503341_eng.pdf;jsessionid=7D2258370F31444A72815B5CFB2E1FE8?ua=1?sequence=1](https://apps.who.int/iris/bitstream/handle/10665/44851/9789241503341_eng.pdf;jsessionid=7D2258370F31444A72815B5CFB2E1FE8?ua=1?sequence=1)
