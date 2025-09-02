# Kasper Boberg – Power BI Portfolio

Hej! Jag heter Kasper och det här är min portfolio för BI-lösningar med fokus på ekonomi och affärsnytta. Här visas ett konkret case där jag analyserat musikstreaming och intäkter med Power BI. 

---

## Projekt: Streaming & Earnings Dashboard (Power BI)

### Bakgrund
Syftet är att förstå hur intäkter per stream (eCPM) varierar mellan olika plattformar och territorier över tid. Med hjälp av anonymiserade exportdata från musikdistributiontjänsten DistroKid har en informativ Power BI-rapport skapats. All data har anonymiserats på ett sätt som säkerställer att alla plattformsrelaterade insikter, baserade på jämförande och generaliserande analyser, förblir korrekta, medan den artistspecifika informationen presenteras i en mer anonymiserad form. 

### Data & Modell
- **Faktatabeller:** `Streams`, `Payouts`
- **Dimensioner:** `Date`, `Platform`, `Territory`, `Track`
- **Bearbetning:** Power Query (datasanering, valutaomräkning, typning)
- **Modellering:** Stjärnschema för tydlig struktur och analys

### Se databasbygget och hanteringen i SQL (.md): 
[Database](Power-BI-Portfolio/Streaming-Data-Dashboard/Database/img_readme.md)

### Nyckelmått (DAX)
```DAX
Total Streams = SUM('Streaming Data'[Quantity])
Total Revenue = SUM('Streaming Data'[Earnings (USD)])
Revenue per 1000 Streams = DIVIDE([Total Revenue], [Total Streams]) * 1000
```

###  Nyckemått med kontinuerlig datumkolumn (DAX)
```DAX
YoY Revenue Growth = 
VAR CurrentYear = [Total Revenue]
VAR PreviousYear = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('Date Table'[Date]))
RETURN IF(NOT(ISBLANK(PreviousYear)), DIVIDE(CurrentYear - PreviousYear, PreviousYear), BLANK())
```

### Resultat (Dashboard)
- **Översikt:** Total streams, total revenue, eCPM (för 1 000 streams)
- **Plattformsvy:** Top-N plattformar och deras andel av totalt
- **Territorievy:** Intäkter och eCPM per land
- **Trend:** Rullande 12 månader för både intäkter och streams

### Se dashboard-bilder (PDF): 
[Dashboard](Power-BI-Portfolio/Streaming-Data-Dashboard/Power-BI/Streaming_Data_Dashboards.pdf)

### Insikter
- eCPM varierar markant mellan plattformar och territorier
- R12-trenden visar både säsongsvariationer och effekten av nya releaser
- Intäkterna är tydligt koncentrerade till få plattformar

---

## Teknik
**Power BI** (modell, DAX, Power Query) · **SQL** · **Excel**

---

## Kontakt
kasperboberg95@gmail.com

> **Notering:** Eftersom datan i sin originalform är hämtad från privata källor innan anonymisering delar jag helst ut varken datakällor eller .pbix-filer. Istället visas datamodell, DAX-kod och skärmdumpar från rapporten.
