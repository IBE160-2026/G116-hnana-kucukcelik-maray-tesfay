# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G116 – G116-hnana-kucukcelik-maray-tesfay |
| **Product brief** | `product-brief.md` (commit `00d7701`) |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

Vurdert fil: `product-brief.md` i repoets rot, som er den eneste briefen. Det finnes ennå ikke PRD, arkitektur eller epics.

## Samlet vurdering

- **Godt utgangspunkt med justeringer.** Gruppen kan gå videre og innarbeide punktene under.

**Det som er bra:**

1. Dette er en gjennomarbeidet brief med en tydelig profil: «verified study material», der hver oppsummering, hvert flashcard og hvert spørsmål viser dokument og side. Det løser et reelt problem med generelle chatboter, og det gjør KI-delen kontrollerbar.
2. Suksesskriteriene er konkrete og målbare: under 2 minutter fra opplasting av en 30-siders PDF til første quiz, minst 90 % korrekte spørsmål ved manuell gjennomgang av 50 spørsmål, 95 % riktige sidehenvisninger, og automatiske tester som sikrer at en bruker aldri ser andres materiale. Scope har en tydelig «Explicitly out»-liste (OCR, deling, avansert spaced repetition, Canvas).

**De viktigste endringene:**

1. Prioriter innad i v1. Seks punkter i v1 er mye, og noen er tyngre enn de ser ut: tre detaljnivåer, to språk, KI-tilbakemelding på skriftlige svar, svake punkter, gjentakelse av bommede kort og redigering/regenerering. Merk hva som er kjernen (for eksempel opplasting, flashcards og flervalgsquiz med kildehenvisning), og hva som kommer etterpå (for eksempel KI-vurdering av kortsvar og tre detaljnivåer). Da har dere en sikker versjon å levere.
2. Beskriv hvordan sidehenvisningene lages og kontrolleres. 95 % riktige sider er et godt mål, men forutsetter at teksten fra PDF-en deles opp per side, og at KI-en bare får se de aktuelle sidene eller må oppgi sidetallet. Skriv dette inn som en beslutning, og beskriv hvordan dere sjekker målet (for eksempel 40 tilfeldige elementer mot originalen).
3. Planlegg kjøring uten deres nøkkel. Dere har bestemt skybasert språkmodell, og at nøkkelen aldri skal eksponeres i nettleseren. Bra. Beskriv også hvordan sensor kan prøve appen uten deres nøkkel, for eksempel med en testmodus som bruker ferdig genererte data for ett eksempeldokument.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Middels**

**Sammenlignbart med:** 7) Kurs-FAQ-chatbot (middels) når det gjelder kildeforankrede KI-svar med henvisning, bygget på 1) AI Study Buddy (enkel). Innlogging med privat lagring per bruker og kurs, sidehenvisning på alt og KI-tilbakemelding på kortsvar løfter prosjektet fra enkel til middels.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | Middels | Poengberegning, svake punkter, regler for hvor ofte bommede kort kommer tilbake, og kobling til side. |
| Datamodell – antall entiteter og relasjoner mellom dem | Middels | Bruker, kurs, dokument, side, sammendrag, begrep, flashcard, quizspørsmål, svar og vurdering. |
| Brukere, roller og innlogging | Middels | Registrering og innlogging med strengt privat lagring per bruker. Én rolle. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | Høy | Fire typer innhold med kildehenvisning, tre detaljnivåer, to språk og vurdering av fritekstsvar. Krever gjennomtenkte prompts og strukturert svar. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | Middels | Skybasert språkmodell. Ingen betaling eller Canvas. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | Lav | Ingen deling i v1. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | Middels | Tekstbaserte PDF-er med sidetall. Skannede PDF-er er klokt utelatt. |
| Sikkerhet og personvern | Middels | Privat materiale per bruker, nøkler skjult for nettleseren, og informasjon om at materialet sendes til en ekstern tjeneste. Godt beskrevet. |

**Hva vanskelighetsgraden betyr for dere:**

- _Middels:_ Et godt balansert valg. Pass på at kjerneflyten blir ferdig og stabil før dere legger til mer. Her er kjerneflyten: logg inn, opprett kurs, last opp en PDF, få flashcards og quiz med sidehenvisning, og øv.

### Gjennomførbarhet med BMAD og Claude Code

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | Risiko | Realistisk for fire personer hvis kjernen prioriteres først. Med alle seks punktene fullt ut blir tiden knapp. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | OK | Svært konkret. De åpne beslutningene er tydelig listet og passer å avgjøre i PRD og arkitektur. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | OK | Webapp med innlogging, database, PDF-lesing og API-kall er godt egnet. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | OK | Sidehenvisningene og den manuelle gjennomgangen av 50 spørsmål gjør det mulig å kontrollere svarene. KI-vurdering av kortsvar er vanskeligst å kvalitetssikre. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | OK | Gode måltall og automatiske sikkerhetstester. Bruk mock-svar for KI i de automatiske testene. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | Risiko | Krever språkmodell-nøkkel. Planlegg testmodus eller ferdig generert eksempeldata. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | Risiko | Valg av modell er åpent. Store PDF-er kan gi høye kostnader. Sett en grense for dokumentstørrelse i v1. |

**Konklusjon om gjennomførbarhet:**

- **Gjennomførbart med justert omfang.** Se forslagene under.

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. Del v1 i en kjerne (innlogging, kurs, opplasting, flashcards og flervalgsquiz med sidehenvisning, poengsum) og en utvidelse (sammendrag i tre nivåer, kortsvar med KI-tilbakemelding, svake punkter, regenerering). Bygg og test kjernen ferdig først.
2. Start med ett språk for generert innhold, og legg til det andre når kjernen virker. Sett en øvre grense for PDF-størrelse (for eksempel 50 sider) for å holde kostnad og ventetid nede.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | OK | Svært tydelig: eget pensum blir til verifiserbart øvingsmateriell, lagret per kurs. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | OK | Konkret, med tre dagens alternativer og hva de koster studenten. |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | OK | Beskriver flyten fra innlogging til øving, og hva studenten ser. |
| What Makes This Different – er vurderingen ærlig og realistisk? | OK | Ærlig, inkludert NotebookLM og at det ikke finnes noen teknisk vollgrav. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | OK | Tydelig primærbruker og hva suksess betyr for dem. |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | OK | Målbare og konkrete. Beskriv gjerne også metoden for å sjekke sidehenvisningene. |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | Juster | Tydelig inn/ut, men v1 er stort. Prioriter innad i v1 som foreslått. |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | OK | God trinnvis visjon, tydelig lagt etter v1. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | Juster | Briefen er presis nok. Repoet har bare opplastede filer så langt. Bruk BMAD videre, commit jevnlig fra alle i gruppen, og lagre promptene. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | Juster | Rikelig funksjonalitet. Sørg for at kjernen blir stabil før utvidelsene. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | OK | Svært godt grunnlag for testing, både manuelt og automatisk. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | OK | Flyten kurs → materiale → øving → svake punkter gir et tydelig designgrunnlag. Skisser hvordan kildehenvisningen vises og åpnes. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | OK | Skybasert API og server som skjuler nøkkelen er riktige valg. Begrunn stakken i arkitekturdokumentet. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | Juster | Planlegg testmodus med ferdig generert eksempeldata, og sørg for at innlogging virker lokalt. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Juster | Bestem mappestruktur for planleggingsdokumenter og eksempel-PDF-er (med lov til å dele dem), og hold nøkler i `.env` utenfor Git. |

## 3. Neste steg for gruppen

1. Merk kjerne og utvidelse innad i v1 i Scope.
2. Beskriv hvordan sidehenvisningene lages og kontrolleres, og hvordan sensor kan kjøre appen uten deres nøkkel.
3. Lag PRD og arkitektur med BMAD, og avgjør de åpne beslutningene der.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
