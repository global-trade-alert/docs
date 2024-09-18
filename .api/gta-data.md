# GTA Data endpoint<!-- omit from toc --> 

The Data endpoint allows to extract paginated lists of policies from the GTA database filtered by different criteria. 


## Table of contents<!-- omit from toc --> 

- [Access](#access)
  - [Request body](#request-body)
  - [Accepted filters](#accepted-filters)
- [Output](#output)
- [Pagination](#pagination)

## Access
The data endpoint can be accessed via the following request:
```
POST https://api.globaltradealert.org/api/v1/data/
Content-Type: application/json
Authorization: APIKey [YOUR_API_KEY]
```

Replace `[YOUR_API_KEY]` with your personal API key.

### Request body
The request body can contain the following parameters:
```
{
    "limit": 100,
    "offset": 0,
    "sorting": "-date_announced",
    "request_data": { 
        "affected": [32, 840],
        "implementation_period": ["2023-01-01", ""],
        "in_force_today": true,
        ...
    }
}
```

| Key | Description |
| :--- | :--- |
| `limit` | Set the size of the result set here. Accepted is any number between 0 and 1000 |
| `offset` | Use this parameter to paginate through the output, it accepts any number. |
| `sorting` | Define the parameters you would like to sort the output by, accepted are `date_announced`, `date_implemented`. Combine multiple order clauses together in the same string by separating them via a comma, e.g. `date_announced,date_implemented`. Reverse the order by adding a `-` in front of the order clause you want to reverse, e.g. `-date_announced` |
| `request_data` | This parameter accepts an object containing the key-value pairs used as filters. See accepted filters in the [Accepted filters](#accepted-filters) section. |


### Accepted filters

The Data endpoint accepts a variety of filters to narrow down the output.

| Parameter | Description | Example | Default |
| :--- | :--- | :--- | :--- |
| `gta_evaluation`| Filters by evaluation value, multiple possible. Evaluations determine if an intervention is harmful, liberalising or murky (unclear). [See accepted values here](./gta-value-mappings.md#gta-evaluation) | [1,2,3] | Unfiltered |
| `affected_flow`| Filters by affected flow value, multiple possible. Affected flows determine the trade flow, that an intervention affects. [See accepted values here](./gta-value-mappings.md#affected-flows) | [1,2,3] | Unfiltered |
| `affected`| Filters by affected jurisdictions, accepted values are UN country codes, multiple possible. [See accepted values here](./gta-value-mappings.md#jurisdictions) | [4, 32, 840] | Unfiltered |
| `keep_affected`| Boolean filter defining if chosen commercial flow values should be in- or excluded | True/False | True |
| `implementer`| Filters by implementing jurisdiction, accepted values are UN country codes, multiple possible. [See accepted values here](./gta-value-mappings.md#jurisdictions) | [4, 32, 840] | Unfiltered |
| `keep_implementer`| Boolean filter defining if chosen implementing jurisdiction values should be in- or excluded | True/False | True |
| `intervention_types`| Filters by a list of intervention types directly, multiple possible. [See accepted values here](./gta-value-mappings.md#intervention-types) | [1,2,3] | None |
| `keep_intervention_types`| Boolean filter defining if chosen intervention types should be in- or excluded | True/False | True |
| `mast_chapters`| Filters by a list of mast chapters, multiple possible. [See accepted values here](./gta-value-mappings.md#mast-chapters) | [1,2,3] | None |
| `keep_mast_chapters`| Boolean filter defining if chosen mast chapter values should be in- or excluded | True/False | True |
| `implementation_level`| Filters by a list of implementation levels, multiple possible. [See accepted values here](./gta-value-mappings.md#implementation-level) | [1,2,3] | None |
| `keep_implementation_level`| Boolean filter defining if chosen implementation levels values should be in- or excluded | True/False | True |
| `eligible_firms`| Filters by a list of eligible firm values, multiple possible. [See accepted values here](./gta-value-mappings.md#eligible-firms) | [1,2,3] | None |
| `keep_eligible_firms`| Boolean filter defining if chosen eligible firms values should be in- or excluded | True/False | True |
| `announcement_period`| Daterange filter defining in which range the intervention was announced. None values are treated as unfiltered (=any date into the past or future). | ['2020-01-01', None] | Unfiltered |
| `implementation_period`| Daterange filter defining in which range the intervention was implemented. None values are treated as unfiltered (=any date into the past or future). | ['2020-01-01', None] | Unfiltered |
| `keep_implementation_na`| Boolean filter defining if interventions with no implementation date should be in- or excluded | True/False | True |
| `revocation_period`| Daterange filter defining in which range the intervention was revoked. None values are treated as unfiltered (=any date into the past or future). | ['2020-01-01', None] | Unfiltered |
| `keep_revocation_na`| Boolean filter defining if interventions with no revocation date should be in- or excluded | True/False | True |
| `submission_period`| Daterange filter defining in which range the intervention was published. None values are treated as unfiltered (=any date into the past or future). | ['2020-01-01', None] | Unfiltered |
| `in_force_on_date`| A single datestring value defining a date on which the intervention was in force. | '2020-01-01' | Unfiltered |
| `keep_in_force_on_date`| Boolean filter defining if interventions that were in force on that date should be in- or excluded | True/False | True |
| `affected_sectors`| Filters by a list of CPC sector codes, accepted values are CPC sector codes, multiple possible | [341, 352, 379] | Unfiltered |
| `keep_affected_sectors`| Boolean filter defining if chosen CPC sectors should be in- or excluded | True/False | True |
| `affected_products`| Filters by a list of HS codes, accepted values are HS product codes, multiple possible | [292149, 292229, 292429] | Unfiltered |
| `keep_affected_products`| Boolean filter defining if chosen hs codes should be in- or excluded | True/False | True |
| `intervention_id`| Filters by a list of intervention_ids directly, multiple possible | [123456, 234567, 345678] | Unfiltered |
| `keep_intervention_id`| Boolean filter defining if chosen intervention ids should be in- or excluded | True/False | True |
| `lag_adjustment`| Datestring that filters interventions based on a lag date. Interventions with publishing date after the yearly lag date are excluded. The year component of this datevalue is ignored. | '2023-03-05' | Unfiltered |

## Output
The format of the data being returned looks like this:

```
[
  {
    "intervention_id": 138295,
    "state_act_id": 87754,
    "state_act_title": "EU: Changes to the list of agricultural and industrial products subject to a reduction of import duties (July 2024)",
    "intervention_url": "https://www.globaltradealert.org/intervention/138295",
    "state_act_url": "https://www.globaltradealert.org/state-act/87754",
    "gta_evaluation": "Red",
    "implementing_jurisdictions": [
      {
        "id": 40,
        "name": "Austria",
        "iso": "AUT"
      },
      {
        "id": 56,
        "name": "Belgium",
        "iso": "BEL"
      },
      {
        "id": 100,
        "name": "Bulgaria",
        "iso": "BGR"
      },
      ...
    ],
    "implementing_jurisdiction_groups": [
      {
        "name": "European Union"
      }
    ],
    "affected_jurisdictions": [
      {
        "id": 32,
        "name": "Argentina",
        "iso": "ARG"
      },
      {
        "id": 36,
        "name": "Australia",
        "iso": "AUS"
      },
      {
        "id": 84,
        "name": "Belize",
        "iso": "BLZ"
      },
      ...
    ],
    "implementation_level": "Supranational",
    "eligible_firm": "all",
    "intervention_type": "Import tariff",
    "mast_chapter": "Tariff measures",
    "mast_subchapter": "Tariff measures",
    "affected_sectors": [
      341,
      352,
      379,
      346,
      369,
      469,
      354
    ],
    "affected_products": [
      292149,
      292229,
      292429,
      ...

    ],
    "date_announced": "2024-07-04",
    "date_published": "2024-07-08",
    "date_implemented": "2024-07-01",
    "date_removed": null,
    "is_in_force": 1
  },
  {...},
  {...}
]
```

## Pagination

The Data endpoint allows to return a maximum of 1000 entries per request. Use the `limit` and `offset` parameters to paginate through the output.

I.e. to get the first 1000 entries, set the `limit` to 1000 and the `offset` to 0. To get the next 1000 entries, set the `limit` to 1000 and the `offset` to 1000, and so forth.

No entries are returned if the offset is higher than the total number of entries matching the request filters.

