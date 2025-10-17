# Kasper Boberg – Portfolio Repositories

Hej! Tack för att du vill titta igenom min portfolio. Den gäller i fösta hand BI-lösningar med fokus på ekonomi och affärsnytta. Just nu finns ett konkret case där jag analyserat musikstreaming och intäkter med Power BI. Caset nyttjar även self-hosting via Supabase och SQL querying för att lagra, bearbeta och hämta data. Det finns även ett pågående projekt, repo 2, där Google AI Studio använts för att bygga en webbapp för att omvandla ett vanligt foto till en studiobild med hjälp av Gemini 2.5 Flash Image. Projektet är ett WIP. 

---

## Projekt 1: Streaming & Earnings Dashboard (Power BI)

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

## Projekt 2 - AI CV-Fotogenerator

Detta projekt är en webbapplikation som använder kraften från Google Gemini API för att omvandla dina vardagsfoton till professionella CV-porträtt i studiokvalitet. Användare kan ladda upp ett foto av sig själva, specificera önskad klädstil och anpassa bakgrund och belysning för att generera realistiska och polerade porträtt lämpliga för CV:n, LinkedIn-profiler och professionella webbplatser.

## Huvudfunktioner

- **AI-drivna Porträtt:** Använder gemini-2.5-flash-image-preview-modellen för att generera högkvalitativa, fotorealistiska porträtt samtidigt som användarens identitet bevaras.
- **Flexibla Klädalternativ:** Definiera din outfit genom att antingen ladda upp en referensbild av kläderna eller ge en enkel textbeskrivning (t.ex. "mörkblå blazer och vit skjorta").
- **Studioanpassning:**
  - **Bakgrunder:** Välj från en palett av professionella bakgrundsfärger.
  - **Belysning:** Välj mellan fyra olika belysningsstilar: Auto, Studio, Naturlig och Dramatisk.
- **Avancerat Bildredigeringspaket:**
  - **Integrerad Beskärare:** Beskär dina uppladdade foton precist med flera bildförhållanden (4:5, 2:3, Fyrkant, Fritt) för att säkerställa perfekt komposition.
  - **Justeringar Efter Generering:** Finjustera dina genererade foton i en fullskärms-lightbox med kontroller för Exponering, Kontrast och Tonalitet (Färg/Svartvit).
  - **Ombeskärning av Genererade Bilder:** Beskär den slutliga utmatningen för att få den perfekta inramningen.
- **Dynamiskt Galleri:** Visa, regenerera enskilda bilder och ladda ned dina resultat. Alla redigeringar som görs i förhandsgranskaren tillämpas på den slutliga nedladdade bilden, som även inkluderar en subtil filmkorneffekt för ett mer autentiskt utseende.
- **Intuitiv UI/UX:** Ett rent, responsivt och användarvänligt gränssnitt designat för en sömlös upplevelse från uppladdning till nedladdning, komplett med laddningsindikatorer och tydlig felhantering.

## Så här fungerar det

1. **Ladda upp:** Börja med att ladda upp ett tydligt foto av ditt ansikte.
2. **Stil:** Ladda eventuellt upp ett foto av en outfit eller beskriv kläderna du vill bära.
3. **Anpassa:** Välj önskad bakgrundsfärg och belysningsinställning från kontrollpanelen.
4. **Generera:** Klicka på "Generera Foton" för att skicka input och en detaljerad prompt till Gemini API.
5. **Förfina & Ladda ned:** Applikationen visar de genererade porträtten i ett galleri. Du kan öppna vilken bild som helst i förhandsgranskaren för att göra justeringar, beskära om och ladda ned den slutliga, polerade versionen.

## Teknisk Stack

Denna applikation är byggd med moderna, webbläsarbaserade teknologier för att säkerställa prestanda, tillförlitlighet och en högkvalitativ användarupplevelse.

- **Frontend:**
  - **HTML5:** Tillhandahåller den semantiska strukturen för en välorganiserad och tillgänglig applikation.
  - **CSS3:** Driver hela den visuella upplevelsen, använder moderna funktioner som Grid och Flexbox för responsiva layouter, anpassade egenskaper (:root) för enkel tematisering, och subtila animationer/övergångar för en polerad, interaktiv känsla.
  - **TypeScript:** Lägger till statisk typning till JavaScript, vilket avsevärt förbättrar kodkvalitet, utvecklarupplevelse och underhållbarhet genom att fånga fel tidigt och möjliggöra robust verktygsuppsättning.
- **Kärnteknologi för AI:**
  - **Google Gemini API (@google/genai library):** Applikationens motor. Den utnyttjar de multimodala funktionerna hos gemini-2.5-flash-image-preview-modellen, som utmärker sig på komplexa bildredigeringsuppgifter som att realistiskt komponera en persons ansikte på nya kläder och bakgrunder samtidigt som deras identitet bevaras.
- **Bildmanipulation & Bearbetning:**
  - **Cropper.js:** Ett kraftfullt JavaScript-bibliotek på klientsidan som tillhandahåller ett intuitivt och funktionsrikt gränssnitt för bildbeskärning. Det låter användare exakt rama in sina uppladdade foton, med stöd för flera bildförhållanden för perfekt komposition.
  - **HTML5 Canvas API:** Används för efterbearbetning av de genererade bilderna på klientsidan. Före nedladdning ritas bilden på en canvas där filter (Exponering, Kontrast, Svartvit) och ett subtilt filmkornöverlägg appliceras, vilket säkerställer att alla användarjusteringar bakas in i den slutliga utdatafilen.
- **UI & Tillgångar:**
  - **Font Awesome:** Tillhandahåller en omfattande uppsättning högkvalitativa ikoner som används genom hela gränssnittet för knappar, platshållare och kontroller, vilket förbättrar visuell klarhet och användarvägledning.
- **Utvecklings- & Byggmiljö:**
  - **Vite:** (Som indikerat av package.json) En nästa generations frontend-verktyglösning som erbjuder en extremt snabb utvecklingsserver med Hot Module Replacement (HMR) och optimerade produktionsbyggen.
  - **ES-moduler (via Import Maps):** Projektet använder moderna, webbläsarbaserade ES-moduler för ett rent och effektivt beroendehanteringssystem utan att kräva en komplex bundler-uppsättning för den slutliga koden.

---

## Kontakt
kasperboberg95@gmail.com

> **Notering:** Eftersom datan i sin originalform är hämtad från privata källor innan anonymisering delar jag helst ut varken datakällor eller .pbix-filer. Istället visas datamodell, DAX-kod och skärmdumpar från rapporten.
