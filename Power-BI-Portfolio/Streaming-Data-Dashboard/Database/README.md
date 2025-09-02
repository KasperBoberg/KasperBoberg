# Projekt: Databas för Streaming & Earnings Dashboard (PostgreSQL)

### Bakgrund
För att möjliggöra analysen av musikstreaming och intäkter har en databas byggts i **PostgreSQL** och hostats på Supabase. Syftet är att samla, tvätta och optimera rådata från distributionsplattformen DistroKid (export i TSV-format) i en enda **platt tabell**. Tabellen fungerar som källan till Power BI och är strukturerad för att vara både enkel att förstå och snabb att analysera.  

### Data & Modell
- **Plattform:** PostgreSQL (Supabase)  
- **Källor:** DistroKid-exporter (TSV)  
- **Struktur:** En platt tabell med sammanslagen data för streams, intäkter, plattform, territorium, track och datum  
- **Optimering:** Indexering på nyckelkolumner (datum, plattform, territorium) för effektivare frågekörning  
- **Integration:** Direktanslutning till Power BI via DirectQuery  

### Queries & Datatvätt
Exempel på transformationer som gjorts i SQL:  

**1. Rensa null-värden och dubletter**  
```sql
DELETE FROM streaming_data
WHERE ctid IN (
    SELECT ctid
    FROM (
        SELECT ctid,
               ROW_NUMBER() OVER (PARTITION BY stream_id ORDER BY ctid) as rn
        FROM streaming_data
    ) ranked
    WHERE rn > 1
);
```

**2. Byta kolumnnamn till mer beskrivande**
```sql
ALTER TABLE streaming_data
RENAME COLUMN "Earnings (USD)" TO revenue_usd;

ALTER TABLE streaming_data
RENAME COLUMN "Quantity" TO streams;
```

**3. Korrigera datatyper**
```sql
ALTER TABLE streaming_data
ALTER COLUMN revenue_usd TYPE NUMERIC(10,2) USING revenue_usd::NUMERIC(10,2);
```

**4. Skapa kategorier för enklare analys**
```sql
ALTER TABLE streaming_data
ADD COLUMN platform_group TEXT;

UPDATE streaming_data
SET platform_group = CASE
    WHEN platform IN ('Spotify', 'Apple Music', 'YouTube Red') THEN 'Major'
    ELSE 'Other'
END;
```

### Process
1. **Export från DistroKid** i TSV-format  
2. **Uppladdning till Supabase** med importverktyg  
3. **SQL-frågor för datatvätt och modellering**  
   - Cleaning (nulls, dubletter, irrelevanta kolumner)  
   - Renaming av kolumner  
   - Datatypkonvertering (streams, revenue, datum)  
   - Skapande av kategorikolumner  
   - Indexering för bättre prestanda  
4. **Direktkoppling till Power BI**  
   - DirectQuery-anslutning mot databasen  
   - Byggande av dashboard på den platta tabellen  

### Resultat (Databas)
- **Stabil och enkel datakälla** för Power BI-rapporten  
- **Förbättrad prestanda** genom indexering  
- **Flexibel struktur** där SQL queries kan utökas vid behov  

### Insikter
- En välstrukturerad platt tabell räcker långt för analys av streamingdata  
- SQL-tvätt och standardisering gör att datan blir mer användbar och tillförlitlig  
- Processen skapar en tydlig pipeline från rådata → databas → Power BI

### Dataananalys i SQL eller Power BI
- Genom att rensa och strukturera all data, exempelvis genom att grupperingen "Major" bestående av Spotify, Apple Music och YouTube Red är det möjligt att genomföra djupgående numerisk analys likvärdig den som senare genomfördes i Power BI med hjälp av aggregrate functions så som SUM() och DIVIDE().
- Många av de fördelar som kan realiseras med hjälp av Power BI, så som visualisering, klickbart gränssnitt, slicers och on-the-fly filters, är anledningen till att SQL i detta projekt endast användes för initial tvätt och strukturering av data, inte djupgående analys.

---

## Teknik
**PostgreSQL** (datamodellering, SQL, indexering) · **Supabase** (molndatabas) · **Power BI**  

---

## Kontakt
kasperboberg95@gmail.com  

> **Notering:** Eftersom datan i sin originalform är hämtad från privata källor innan anonymisering delas varken datakällor eller råa SQL-dumpfiler. Istället visas utdrag, dokumentation och dashboards.


