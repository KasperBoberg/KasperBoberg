# Kasper Boberg – Power BI Portfolio

Hej! Tack för att du vill titta igenom min portfolio för BI-lösningar med fokus på ekonomi och affärsnytta. Just nu finns ett konkret case där jag analyserat musikstreaming och intäkter med Power BI. Caset nyttjar även self-hosting via Supabase och SQL querying för att lagra, bearbeta och hämta data.

---

## Projekt: Streaming & Earnings Dashboard (Power BI)

### Bakgrund
Syftet är att förstå hur intäkter per stream (eCPM) varierar mellan olika plattformar och territorier över tid. Med hjälp av anonymiserade exportdata från musikdistributiontjänsten DistroKid har en informativ Power BI-rapport skapats. All data har anonymiserats på ett sätt som säkerställer att alla plattformsrelaterade insikter, baserade på jämförande och generaliserande analyser, förblir korrekta, medan den artistspecifika informationen presenteras i en mer anonymiserad form.

Nedan följer en kort sammanfattning över caset. Vänligen navigera till de specifika delarna av repo:n för mer djupgående genomgång av databasbygget, dashboardbygget samt insights och slutsatser.

---

### Data & Modell
- **Datakälla:** Streamingdata från privat musikprojekt via DistroKid
- **Bearbetning:** PostgreSQL, Power Query (datasanering, valutaomräkning, typning)
- **Modellering:** Stjärnschema för tydlig struktur och analys

### Se databasbygget och hanteringen i SQL:
[Databas README](Power-BI-Portfolio/Streaming-Data-Dashboard/Database/README.md)
[Databas Bilder](Power-BI-Portfolio/Streaming-Data-Dashboard/Database/img_readme.md)

### Se dashboard-bilder:
[Dashboard README](Power-BI-Portfolio/Streaming-Data-Dashboard/Power-BI/README.md)
[Dashboard PDF](Power-BI-Portfolio/Streaming-Data-Dashboard/Power-BI/Streaming_Data_Dashboards.pdf)

### Resultat (Dashboard)
- **Översikt:** Total streams, total revenue, eCPM (för 1 000 streams)
- **Plattformsvy:** Top-N plattformar, deras andel av totalt samt eCPM
- **Territorievy:** Intäkter och eCPM per land
- **Trend:** Rullande 12 månader för både intäkter och streams

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
