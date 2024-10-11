# DPA Data endpoint<!-- omit from toc --> 

The Data endpoint allows to extract paginated lists of policies from the GTA database filtered by different criteria. 


## Table of contents<!-- omit from toc --> 

- [Access](#access)
  - [Request payload](#request-payload)
  - [Accepted filters](#accepted-filters)
  - [Value id mappings](#value-id-mappings)
- [Output](#output)
- [Pagination](#pagination)

## Access
The data endpoint can be accessed via the following request:
```
POST https://api.globaltradealert.org/api/v1/dpa/events/
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
    "request_data": { 
        "jurisdiction": [32, 840],
        "period": ["2023-01-01", "2024-01-01"],
        ...
    }
}
```

| Key | Description |
| :--- | :--- |
| `limit` | Set the size of the result set here. Accepted is any number between 0 and 1000 |
| `offset` | Use this parameter to paginate through the output, it accepts any number. |
| `sorting` | This parameter is coming soon. |
| `request_data` | This parameter accepts an object containing the key-value pairs used as filters. See accepted filters in the [Accepted filters](#accepted-filters) section. |


### Accepted filters

The Data endpoint accepts a variety of filters to narrow down the output.

| Parameter | Description | Example | Default |
| :--- | :--- | :--- | :--- |
| `implementing_jurisdiction`| Filters by implementing jurisdictions. Accepted is a list of UN country codes (see value id mappings below). | [1,2,3] | Unfiltered |
| `economic_activity`| Filters by economic activity, accepted are economic activity ids (see value id mappings below). | [1,2,3] | Unfiltered |
| `government_branch`| Filters by government branch, accepted are government branch ids (see value id mappings below). | [1,2,3] | Unfiltered |
| `event_type`| Filters by event type, accepted are event type ids (see value id mappings below). | [1,2,3] | Unfiltered |
| `policy_area`| Filters by policy areas, accepted are policy area ids (see value id mappings below). | [1,2,3] | Unfiltered |
| `implementation_level`| Filters by implementation levels, accepted are implementation level ids (see value id mappings below). | [1,2,3] | Unfiltered |
| `event_period`| Daterange filter defining in which range the latest event occurs. | ['2020-01-01', '2023-01-01'] | Unfiltered |


### Value id mappings

In this section you can find id values for the different filters accepted by the endpoint.

**Value id mappings for jurisdictions**:
| Value | ID |
| :--- | :--- |
| Afghanistan | 4 |
| Albania | 8 |
| Algeria | 12 |
| American Samoa | 16 |
| Andorra | 20 |
| Angola | 24 |
| Antigua & Barbuda | 28 |
| Azerbaijan | 31 |
| Argentina | 32 |
| Australia | 36 |
| Austria | 40 |
| Bahamas | 44 |
| Bahrain | 48 |
| Bangladesh | 50 |
| Armenia | 51 |
| Barbados | 52 |
| Belgium | 56 |
| Bermuda | 60 |
| Bhutan | 64 |
| Bolivia | 68 |
| Bosnia & Herzegovina | 70 |
| Botswana | 72 |
| Brazil | 76 |
| Belize | 84 |
| Solomon Islands | 90 |
| British Virgin Islands | 92 |
| Brunei Darussalam | 96 |
| Bulgaria | 100 |
| Myanmar | 104 |
| Burundi | 108 |
| Belarus | 112 |
| Cambodia | 116 |
| Cameroon | 120 |
| Canada | 124 |
| Cape Verde | 132 |
| Cayman Islands | 136 |
| Central African Republic | 140 |
| Sri Lanka | 144 |
| Chad | 148 |
| Chile | 152 |
| China | 156 |
| Chinese Taipei | 158 |
| Colombia | 170 |
| Comoros | 174 |
| Mayotte | 175 |
| Congo | 178 |
| DR Congo | 180 |
| Cook Islands | 184 |
| Costa Rica | 188 |
| Croatia | 191 |
| Cuba | 192 |
| Cyprus | 196 |
| Czechia | 203 |
| Benin | 204 |
| Denmark | 208 |
| Dominica | 212 |
| Dominican Republic | 214 |
| Ecuador | 218 |
| El Salvador | 222 |
| Equatorial Guinea | 226 |
| Ethiopia | 231 |
| Eritrea | 232 |
| Estonia | 233 |
| Faeroe Islands | 234 |
| Falkland Islands | 238 |
| Fiji | 242 |
| Finland | 246 |
| France | 251 |
| French Guiana | 254 |
| French Polynesia | 258 |
| Djibouti | 262 |
| Gabon | 266 |
| Georgia | 268 |
| Gambia | 270 |
| State of Palestine | 275 |
| Germany | 276 |
| Ghana | 288 |
| Kiribati | 296 |
| Greece | 300 |
| Greenland | 304 |
| Grenada | 308 |
| Guadeloupe | 312 |
| Guam | 316 |
| Guatemala | 320 |
| Guinea | 324 |
| Guyana | 328 |
| Haiti | 332 |
| Vatican | 336 |
| Honduras | 340 |
| Hong Kong | 344 |
| Hungary | 348 |
| Iceland | 352 |
| Indonesia | 360 |
| Iran | 364 |
| Iraq | 368 |
| Ireland | 372 |
| Israel | 376 |
| Italy | 381 |
| Ivory Coast | 384 |
| Jamaica | 388 |
| Japan | 392 |
| Kazakhstan | 398 |
| Jordan | 400 |
| Kenya | 404 |
| DPR Korea | 408 |
| Republic of Korea | 410 |
| Kuwait | 414 |
| Kyrgyzstan | 417 |
| Lao | 418 |
| Lebanon | 422 |
| Lesotho | 426 |
| Latvia | 428 |
| Liberia | 430 |
| Libya | 434 |
| Liechtenstein | 438 |
| Lithuania | 440 |
| Luxembourg | 442 |
| Macao | 446 |
| Madagascar | 450 |
| Malawi | 454 |
| Malaysia | 458 |
| Maldives | 462 |
| Mali | 466 |
| Malta | 470 |
| Martinique | 474 |
| Mauritania | 478 |
| Mauritius | 480 |
| Mexico | 484 |
| Monaco | 492 |
| Mongolia | 496 |
| Republic of Moldova | 498 |
| Montenegro | 499 |
| Montserrat | 500 |
| Morocco | 504 |
| Mozambique | 508 |
| Oman | 512 |
| Namibia | 516 |
| Nauru | 520 |
| Nepal | 524 |
| Netherlands | 528 |
| Netherlands Antilles | 532 |
| Aruba | 533 |
| New Caledonia | 540 |
| Vanuatu | 548 |
| New Zealand | 554 |
| Nicaragua | 558 |
| Niger | 562 |
| Nigeria | 566 |
| Niue | 570 |
| Norfolk Island | 574 |
| Norway | 578 |
| Northern Mariana Islands | 580 |
| Micronesia | 583 |
| Marshall Islands | 584 |
| Palau | 585 |
| Pakistan | 586 |
| Panama | 591 |
| Papua New Guinea | 598 |
| Paraguay | 600 |
| Peru | 604 |
| Philippines | 608 |
| Pitcairn | 612 |
| Poland | 616 |
| Portugal | 620 |
| Guinea-Bissau | 624 |
| Timor-Leste | 626 |
| Puerto Rico | 630 |
| Qatar | 634 |
| Réunion | 638 |
| Romania | 642 |
| Russia | 643 |
| Rwanda | 646 |
| Saint-Barthélemy | 652 |
| Saint Helena | 654 |
| Saint Kitts & Nevis | 659 |
| Anguilla | 660 |
| Saint Lucia | 662 |
| Saint-Martin | 663 |
| Saint Pierre & Miquelon | 666 |
| Saint Vincent & the Grenadines | 670 |
| San Marino | 674 |
| Sao Tome & Principe | 678 |
| Saudi Arabia | 682 |
| Senegal | 686 |
| Serbia | 688 |
| Seychelles | 690 |
| Sierra Leone | 694 |
| India | 699 |
| Singapore | 702 |
| Slovakia | 703 |
| Vietnam | 704 |
| Slovenia | 705 |
| Somalia | 706 |
| South Africa | 710 |
| Zimbabwe | 716 |
| Spain | 724 |
| South Sudan | 728 |
| Republic of the Sudan | 729 |
| Western Sahara | 732 |
| Suriname | 740 |
| Svalbard & Jan Mayen Islands | 744 |
| Eswatini | 748 |
| Sweden | 752 |
| Switzerland | 756 |
| Syria | 760 |
| Tajikistan | 762 |
| Thailand | 764 |
| Togo | 768 |
| Tokelau | 772 |
| Tonga | 776 |
| Trinidad & Tobago | 780 |
| United Arab Emirates | 784 |
| Tunisia | 788 |
| Turkiye | 792 |
| Turkmenistan | 795 |
| Turks & Caicos Islands | 796 |
| Tuvalu | 798 |
| Uganda | 800 |
| Ukraine | 804 |
| Macedonia | 807 |
| Egypt | 818 |
| United Kingdom | 826 |
| Tanzania | 834 |
| United States of America | 840 |
| US Virgin Islands | 850 |
| Burkina Faso | 854 |
| Uruguay | 858 |
| Uzbekistan | 860 |
| Venezuela | 862 |
| Wallis & Futuna Islands | 876 |
| Samoa | 882 |
| Yemen | 887 |
| Zambia | 894 |
| Republic of Kosovo | 999 |

**Value id mappings for economic activities**:
| Value | ID |
| :--- | :--- |
| cross-cutting | 1 |
| infrastructure provider: internet and telecom services | 2 |
| online advertising provider | 4 |
| digital payment provider (incl. cryptocurrencies) | 5 |
| platform intermediary: user-generated content | 6 |
| streaming service provider | 7 |
| platform intermediary: e-commerce | 8 |
| ML and AI development | 9 |
| other service provider | 10 |
| unspecified | 11 |
| technological consumer goods | 12 |
| semiconductors | 13 |
| software provider: app stores | 14 |
| DLT development | 15 |
| search service provider | 16 |
| software provider: other software | 17 |
| messaging service provider | 18 |
| platform intermediary: other | 19 |
| infrastructure provider: cloud computing, storage and databases | 20 |
| infrastructure provider: network hardware and equipment | 21 |
| infrastructure provider: other | 22 |

**Value id mappings for government branches**:
| Value | ID |
| :--- | :--- |
| legislature | 1 |
| executive | 2 |
| judiciary | 3 |

**Value id mappings for event types**:
| Value | ID |
| :--- | :--- |
| order | 1 |
| outline | 2 |
| inquiry | 3 |
| decision | 4 |
| law | 5 |
| treaty | 6 |
| public lawsuit | 8 |
| investigation | 9 |
| declaration | 10 |
| civil lawsuit | 11 |

**Value id mappings for policy areas**:
| Value | ID |
| :--- | :--- |
| International trade | 1 | 
| Competition | 2 | 
| Content moderation | 3 | 
| Data governance | 4 | 
| Subsidies and industrial policy | 5 | 
| Instrument unspecified | 6 | 
| Other operating conditions | 8 | 
| Public procurement | 9 | 
| Authorisation, registration and licensing | 10 | 
| Taxation | 11 | 
| Foreign direct investment | 12 | 
| Labour law | 13 | 
| Intellectual property | 14 | 
| Consumer protection | 15 | 
| Design and testing standards | 16 | 
| Regulatory Compliance and Transparency | 17 | 

**Value id mappings for implementation levels**:
| Value | ID |
| :--- | :--- |
| national | 1 |
| supranational | 2 |
| subnational | 3 |
| bi- or plurilateral agreement | 4 |
| multilateral agreement | 5 |
| other | 6 |


## Output
The format of the data being returned looks like this:

```
[
 {
    "id": 20442,
    "title": "Adopted Second Edition Model AI Governance Framework",
    "url": "https://digitalpolicyalert.org/event/20442-adopted-model-ai-governance-framework-for-generative-ai",
    "description": "On 21 January 2020, the Infocomm Media Development Authority (IMDA) of Singapore, together with the Personal Data Privacy Commission (PDPC) and in collaboration with the World Economic Forum (WEF), adopted the Second Edition Model AI Governance Framework. The Governance Framework updates the First Edition Model AI Governance Framework, adopted in 2019, [...]",
    "date": "2020-01-21",
    "status": "adopted",
    "event_type": "outline",
    "action_type": "adoption",
    "implementers": [
      {
        "name": "Singapore",
        "id": 702
      }
    ],
    "implementer_groups": [],
    "policy_area": "Design and testing standards",
    "policy_instrument": "Artificial Intelligence authority governance",
    "economic_activities": [
      {
        "name": "ML and AI development",
        "id": 9
      }
    ],
    "implementation_level": "national"
  },
  {...},
  {...}
]
```

## Pagination

The Data endpoint allows to return a maximum of 1000 entries per request. Use the `limit` and `offset` parameters to paginate through the output.

I.e. to get the first 1000 entries, set the limit to 1000 and the offset to 0. To get the next 1000 entries, set the limit to 1000 and the offset to 1000, and so forth.

No entries are returned if the offset is higher than the total number of entries matching the request filters.

