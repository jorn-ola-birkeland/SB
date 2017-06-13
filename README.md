### Komme i gang med skatteberegning 

POST følgende innhold til ```http://skatteberegning.app.skatteetaten.no/2017``` med ```Content-Type=application/json``:

```
{
    "skatteplikt":
    {
        "alder":35,
        "skattekommune":"0301"
    },
    "skattegrunnlag":
    [
        {"fastloenn":{"kr":456000}},
        {"likningsverdiPrimaerbolig":{"kr":1356000}},
        {"likningsverdiFritidsbolig":{"kr":1356000,"kommunenummer":"1403"}},
        {"innskuddBank":{"kr":61456}},
        {"laanBank":{"kr":1890431}},
        {"opptjenteRenter":{"kr":655}},
        {"reiseHjemArbeid":{"km":68,"antall":213}}
    ]
}
```

Følgende er et utdrag av svaret:

```
[
    ...
    {"inntektsskattKommune":[{"kr":13134,"kommunenummer":"0301","grunnlag":{"kr":381000}}}],
    {"inntektsskattFylke":[{"kr":7654,"kommunenummer":"0301","grunnlag":{"kr":381000}}}],
    {"fellesskatt":{"kr":6544}},
    {"trinnskatt":{"kr":1356000}},
    {"formueskattKommune":[{"kr":0,"kommunenummer":"0301","grunnlag":{"kr":0}}}],
    {"reisefradrag",{"kr",4344}},
    ...
]

```

### Oversikt over input

#### Skattegrunnlag

Følgende er de mest brukte skatteobjektene:

| Skatteobjekt        | Eksempel           | Beskrivelse  |
| -------------|---------|----------|
| fastLoenn     | ```{"fastloenn":{"kr":456000}}``` |Årlig, ordinær fastlønnsinntekt utbetalt av arbeidsgiver |
| likningsverdiPrimaerbolig     | ```{"likningsverdiPrimaerbolig":{"kr":1234333}}``` | Likningsverdi av bolig benyttet til opphold  |
| [innskuddBank](innskuddBank.md)     | ```{"innskuddBank":{"kr":61456}}``` | Verdi av innskudd i bank |
| reiseHjemArbeid     | ```{"reiseHjemArbeid":{"km":68,"antall":213}}``` | Lengde på reisevei tur-retur mellom hjem og arbeid i antall km og antall dager |

Se [Alfabetisk liste over alle skatteobjekter](https://www.google.com)

Se [Liste over alle skatteobjekter sortert etter brukshyppighet](https://www.google.com)

Se skatteobjekter gruppert etter tema:

* [Arbeidsinntekter og inntektsfradrag](https://www.google.com)
* [Formue og gjeld](https://www.google.com)
* [Næringsinntekter](https://www.google.com)
* [Fradrag](https://www.google.com)
* [Familie og barn](https://www.google.com)

#### Skatteplikt



|         | Eksempel           | Beskrivelse  |
| -------------|---------|----------|
| alder     | ```"alder":35``` | Alder i inntektsår |
| skattekommune     | ```"skattekommune":"0301"``` | Hjemstestedkommune |
| type     | ```"type":"global"``` | Type skattepliktig tilknytning til Norge; ```Global``` (standard) eller ```Begrenset``` |
| tolvdelerArbeidsoppholdINorge     | ```"tolvdelerArbeidsoppholdINorge":"12"``` | Antall 12-deler arbeidsopphold i Norge (12 er standard) |
| skattemessigeRelasjoner     | ```"skattemessigRelasjoner":[{"ektefelle":"754545645"}]``` | Liste av skattemessigefamiliemedlemmer |
| saerskilteSkatteplikter     | ```"saerskilteSkatteplikter":[{"utenrikstjenestemann":12}]``` | Lengde på reisevei tur-retur mellom hjem og arbeid i antall km og antall dager |

Se [Komplett oversikt over egenskaper i skatteplikten](https://www.google.com)

### Oversikt over beregningsresultatet
