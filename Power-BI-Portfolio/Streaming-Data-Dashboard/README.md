# Streaming & Earnings — Power BI

**Varför:** Få helhetsbild av streams och intäkter per plattform/territorium och identifiera vad som driver eCPM och intäkt/stream.

## Data
- Källa: export/sammanställning från DistroKid (anonymiserad).
- Granularitet: dag/land/plattform/track.
- Samplefiler: `data/sample_streams.csv`, `data/sample_payouts.csv`.

## Modell
- Stjärnschema: `FactStreams`, `FactPayouts` + dimensioner `DimDate`, `DimPlatform`, `DimTerritory`, `DimTrack`.
- Valutaomräkning med daglig kurs (exempelserie).

## Nyckel-DAX (urval)
```DAX
Total Streams := SUM(FactStreams[streams])
Total Revenue := SUM(FactPayouts[amount_local_converted])
eCPM := DIVIDE([Total Revenue], [Total Streams]) * 1000
Top Platform Share := 
 VAR TopPlat = CALCULATE([Total Streams], TOPN(1, DimPlatform, [Total Streams], DESC))
 RETURN DIVIDE(TopPlat, [Total Streams])
