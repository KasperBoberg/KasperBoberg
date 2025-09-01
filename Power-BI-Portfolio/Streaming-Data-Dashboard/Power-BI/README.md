# Musikstreaming Analytics - Power BI Dashboard

## Projektöversikt

Detta projekt analyserar verklig musikstreaming-data från mina egna musikreleaser och visar hur Power BI kan användas för att generera affärsinsikter inom musikbranschen.

**Syfte**: Optimera intäkter genom att identifiera bäst presterande plattformar och marknader.

## Data och struktur

**Datakälla**: DistroKid streaming-export  
**Omfång**: 26 613 streaming-transaktioner från globala plattformar  
**Tidsperiod**: [01-22 till 02-25]

### Huvudkolumner
- Reporting Date, Sale Month - Tidsdimensioner
- Store - Streaming-plattform (Spotify, Apple Music, etc.)
- Title, Artist, ISRC - Spårinformation  
- Country of Sale - Geografisk marknad
- Quantity - Antal streams
- Earnings (USD) - Intäkter

## Databearbetning

**Power Query-transformationer**:
- Korrigerade datatyper och datum
- Skapade date table för time intelligence
- Validerade datakvalitet och hanterade tomma värden
- Standardiserade geografiska namn

**Datakvalitet**: 99,8% kompletta poster efter rensning.

## Nyckeltal och mått

### Grundläggande mått
```dax
Total Streams = SUM('Streaming Data'[Quantity])
Total Revenue = SUM('Streaming Data'[Earnings (USD)])
Revenue per 1000 Streams = DIVIDE([Total Revenue], [Total Streams]) * 1000
```

### Avancerade analyser
```dax
Streams Required for $1000 = DIVIDE(1000, [Average Revenue per Stream])

YoY Revenue Growth = 
VAR CurrentYear = [Total Revenue]
VAR PreviousYear = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('Date Table'[Date]))
RETURN IF(NOT(ISBLANK(PreviousYear)), DIVIDE(CurrentYear - PreviousYear, PreviousYear), BLANK())
```

## Dashboards

### Dashboard 1: Artistspecifik översikt
Visar totala intäkter, streams och trender över tid. Artistspecifik data som jämför geografisk fördelning över tid.

### Dashboard 2: Plattformsanalys  
Fokuserar på streams-per-dollar-effektivitet, plattformsspecifik utveckling och marknadsranking. Antalet streams för att generera $1000 används som mått på plattformsprestanda i kombination med eCPM för läsbarhetens skull. 

## Viktiga insikter

**Plattformsprestanda**: Spotify genererar 88.5 % av totala intäkter med en eCPM på $1.64 och 613K streams för generera $1000.
Tillsammans med YouTube Red (6.2 %) och Apple Music (2.3 %) genererar de tre största plattformarna 97.1 % av alla intäkter.

**Geografisk analys**: Sverige, USA och Storbritannien står för 66.2 % av intäkterna. Jämfört med snitt-eCPM ($1.07) genererar de främsta tre länderna Bermuda ($7.92), Puerto Rico ($5.28) och Island ($4.17) respektive.

**Effektivitet**: I snitt krävs för närvarande 930K streams för att generera $1000. Qobuz är den streamingtjänst som genererar bäst eCPM ($12.33), jämfört med Spotify ($1.63), YouTube Red ($6.42) och Apple Music ($5.29).

## Teknisk implementation

**Verktyg**: Power BI Desktop, Power Query, DAX  
**Arkitektur**: Import-läge med optimerade relationer  
**Funktioner**: Time intelligence, interaktiva filter, mobil-optimering

## Affärsnytta

**Rekommendationer**:
- Fokusera marknadsföring på plattformar med högst eCPM
- Utöka satsning i högpresterande geografiska marknader
- Optimera release-timing baserat på säsongsmönster

**Mätbar påverkan**: Förbättrad streams-till-intäkt-effektivitet och riktad marknadsstrategi.

## Tekniska färdigheter demonstrerade

- Avancerad DAX för time intelligence och affärsberäkningar
- Datamodellering med stjärnschema-principer
- Power Query för ETL och datakvalitet
- Visualiseringsdesign för tydlig kommunikation
- Mobilresponsiv rapportdesign

## Framtida förbättringar

- Prediktiv analys för intäktsprognoser
- Automatisk datauppdatering från plattforms-APIs
- Jämförande branschanalys

---

**Utvecklare**: Kasper Boberg  
**GitHub**: [KasperBoberg](https://github.com/KasperBoberg)  
**Teknologier**: Power BI, DAX, Power Query, SQL
