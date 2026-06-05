# iATFM-data
You will find on this repository all the data file loaded by iatfm.com.

## **_sectors.json:
List of elementary sector per country. The wildcard ** is for the ICAO 2 letter code for each country. If the 2 letter code is X*, it means it's merge of multiple country.
| Parameter | Description |
|---|---|
| `id` | id of the elementary sector, same for subsector|
| `positionPriority` | position from highest to lowest responsible for the volume |
| `blocks` | list of block for one elementary sector |
| `floorFt` | block lowest altitude |
| `ceilingFt` | block highest altitude |
| `runway` | runway in use (ATIS from position listed) *optional, used when AoR changes depending on RWY config* |
| `polygon` | cordinates in ° |
```json
{
    "id": "LFPOITM",
    "positionPriority": ["LFPO_F_APP","LFPO_APP","LFPG_APP","LFFF_W_CTR","LFFF_CTR"],
    "blocks": [
      {
        "id":"LFPOITMW",
        "floorFt": 2500,
        "ceilingFt": 11000,
        "runway": ["24","25"],
        "polygon": [
          { "lat": 48.4560, "lon": 2.8130 },
          { "lat": 48.5239, "lon": 3.2569 },
          { "lat": 48.6681, "lon": 3.1986 },
          { "lat": 48.8563, "lon": 3.0019 },
          { "lat": 48.8527, "lon": 2.6922 },
          { "lat": 48.7350, "lon": 2.3610 },
          { "lat": 48.7380, "lon": 2.3870 },
          { "lat": 48.7260, "lon": 2.3960 },
          { "lat": 48.5780, "lon": 2.3730 },
          { "lat": 48.4560, "lon": 2.8130 }
        ]
      },
      {
        "id":"LFPOITME",
        "floorFt": 2500,
        "ceilingFt": 11000,
        "runway": ["06","07"],
        "polygon": [
          { "lat": 48.6720, "lon": 2.1040 },
          { "lat": 48.7210, "lon": 2.3210 },
          { "lat": 48.7190, "lon": 2.3590 },
          { "lat": 48.7180, "lon": 2.3770 },
          { "lat": 48.4610, "lon": 2.6390 },
          { "lat": 48.3930, "lon": 1.7260 },
          { "lat": 48.5090, "lon": 1.7290 },
          { "lat": 48.5640, "lon": 1.6790 },
          { "lat": 48.6742, "lon": 1.7668 },
          { "lat": 48.7041, "lon": 1.7907 },
          { "lat": 48.6720, "lon": 2.1040 }
        ]
      }
    ]
  },
```

## **_TV.json:
List of Traffic Volume, this volume are used in the FMP page to monitor expected traffic load.
They can be define by one or more elementary sector, if needed, with exclusion and filter based on the FlowIn/FlowEx, and upstream/downstream flow definition from Eurocontrol.

| Parameter | Type | Format | Description |
|---|---|---|---|
| `id` | text | "***" | volume id, *to work properly we ask you to define them with the 2 letter ICAO code of your country* |
| `label` | text | "***" | volume label, *no use at the current stage* |
| `sectorIds` | list | "***" | list of elementary sectors *optional* |
| `departure` | list | "***" | departure airport |
| `arrival` | list | "***" | arrival airport |
| `FlowEx` | list | "***" | list of flow excluded from the traffic prediction |
| `FlowIn` | list | "***" | list of flow only counted in the traffic prediction |
| `maxEntryPerHour` | interger | "30" | maximum entry per hour, each flight will be counted from their entry time +1H |
| `Sustain` | interger | "12" | maximum sustained capacity, number of aircraft in the sector |
| `Peak` | interger | "16" | maximum peak capacity, this is the redline that should not be crossed, number of aircraft in the sector |

### Format for Flow
| Type | Format |
|---|---|
| Airport group (awlays global) | `AZ*G` |
| Airport (Global) | `AD*G` |
| Airport (Departure) | `AD*D` |
| Airport (Arrival) | `AD*A` |
| Point (FIX/VOR/NDB) | `PT*` |
| Sector | `AS*` |
| Downstream element | `>AZ,AD,PT,AS` |
| Upstream element |  `AZ,AD,PT,AS>`|
| "Via" element | `AZ,AD,PT,AS>AZ,AD,PT,AS` |

```json
      {
        "id": "LFPGPO+",
        "label": "LFPGPO+",
        "arrival": ["LFPG","LFPB","LFPO","LFPV","LFPN","LFPT","LFOB"],
        "departure": ["LFPG","LFPB","LFPO","LFPV","LFPN","LFPT","LFOB"],
        "capacity": {"maxEntryPerHour": 155}
      },
      {
        "id": "LFEERMS",
        "label": "LFEERMS",
        "sectorIds": [
            "LFEEUF",
            "LFEEKF",
            "LFEEUE",
            "LFEEXE",
            "LFEEKE",
            "LFEEHE",
            "LFEEUH",
            "LFEEXH",
            "LFEEKH",
            "LFEEHH",
            "LFEEUB",
            "LFEEKN",
            "LFEEUN",
            "LFEEHN",
            "LFEEKD",
            "LFEEHR",
            "LFEEKR",
            "LFEEUR",
            "LFEEXR",
            "LFEEYB",
            "LFEEYR"
        ],
        "capacity": {
            "maxEntryPerHour": 32,
            "sustain": 14,
            "peak": 16
        }
    },
{
        "id": "LFMLMB",
        "label": "LFMLMB",
        "sectorIds": [
            "LFMLMB"
        ],
        "FlowEx": [
            ">ADLFMLG",
            "ADLFMLG>"
        ],
        "capacity": {"maxEntryPerHour": 6}
    }
```

## LF_aiport_group.json:
List of airport group, can be used in TV Flow parameters and future aXFL files.

| Parameter | Type | Description |
|---|---|---|
| `id` | text | airport group id |
| `label` | text | airport groupe name |
| `airports` | list | list of airport |

# CDM Data

Coming Soon
