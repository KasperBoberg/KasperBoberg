# Kasper Boberg – Power BI Portfolio

Hej! Jag heter Kasper och bygger BI-lösningar med fokus på ekonomi och affärsnytta. Här visas ett konkret case där jag analyserat musikstreaming och intäkter med Power BI.

---

## Projekt: Streaming & Earnings Dashboard (Power BI)

### Bakgrund
Syftet var att förstå hur intäkter per stream (eCPM) varierar mellan olika plattformar och territorier över tid. Med hjälp av anonymiserade exportdata från musikdistribution byggdes en informativ Power BI-rapport.

### Data & Modell
- **Faktatabeller:** `Streams`, `Payouts`
- **Dimensioner:** `Date`, `Platform`, `Territory`, `Track`
- **Bearbetning:** Power Query (datasanering, valutaomräkning, typning)
- **Modellering:** Stjärnschema för tydlig struktur och analys

### Se databasbygget och hanteringen i SQL (.md): (Power-BI-Portfolio/Streaming-Data-Dashboard/Database/img_readme.md)

### Nyckelmått (DAX)
```DAX
Total Streams := SUM(FactStreams[streams])
Total Revenue := SUM(FactPayouts[amount_local_converted])
eCPM := DIVIDE([Total Revenue], [Total Streams]) * 1000
Revenue R12 := CALCULATE([Total Revenue], DATESINPERIOD(DimDate[Date], MAX(DimDate[Date]), -12, MONTH))
```

### Resultat (Dashboard)
- **Översikt:** Total streams, total revenue, eCPM (för 1 000 streams)
- **Plattformsvy:** Top-N plattformar och deras andel av totalt
- **Territorievy:** Intäkter och eCPM per land
- **Trend:** Rullande 12 månader för både intäkter och streams

### Se dashboard-bilder (PDF): (Power-BI-Portfolio/Streaming-Data-Dashboard/Power-BI/Streaming_Data_Project.pdf)

### Insikter
- eCPM varierar markant mellan plattformar och territorier
- R12-trenden visar både säsongsvariationer och effekten av nya releaser
- Intäkterna är tydligt koncentrerade till få plattformar

### Reflektion & Nästa steg
Detta projekt är endast en start. Nästa utvecklingssteg skulle kunna bli:
- Cohort-analys per release
- Analyser av churn och outlier-trender i streamingmönster
- Prognosmodell för framtida intäkter baserat på historiska trender

---

## Teknik
**Power BI** (modell, DAX, Power Query) · **SQL** · **Excel**

---

## Kontakt
kasperboberg95@gmail.com

> **Notering:** Av sekretess- och licensskäl delas varken datakällor eller .pbix-filer. Istället visas datamodell, DAX-kod och skärmdumpar från rapporten.
