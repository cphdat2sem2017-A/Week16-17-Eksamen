## Fælles feedback
På baggrund af gennemlæsning af jeres rapporter (alle er ikke læst endnu), er der nogle emner, som berører en række af grupperne, som jeg har samlet nedenfor som fælles feedback og inspirationsmateriale til eksamen. Hvis der er noget i teksten, som du ikke forstår, kan det sagtens skyldes at det ikke er relevant for lige netop jeres projektarbejde, jeres rapport og jeres programdesign.

### Domænemodel
Model over entiteter i den virkelige verden. Det er ikke en model over domæneklasser/businesslogik i jeres program.

### Arkitektur 
Når man snakker 3 tier-arkitektur og 3 lag-arkitektur menes ikke nødvendigvis det samme. 

Tier udtrykker typisk noget fysisk (browser, fx Chrome – web server, fx Tomcat – database server, fx MySQL).

3 lagsarkitektur refererer normalt til det logiske softwaredesign, altså hvordan man har opdelt sit program i 3 moduler (dvs. packages) med hvert sit ansvarsområde: præsentationslag (UI), modellag (domæne-/ forretningslogik) og data access lag.

Som designprincip ønskes lav kobling mellem hvert lag og hvert lag skal have høj binding (uk: high cohesion). Det betyder fx, at der ikke må være forretningslogik i UI laget (fx beregning af styklister), ligesom at operationer i databasen (sql) skal ligge i det separate data access lag.

Men i modsætning til den bekymring som Anton og Kasper udtrykte til deres prøveeksamen, må data access laget gerne have kendskab til domæneobjekter. Mapper klasser i dette lag har netop til opgave at transformere et ResultSet til domæneobjekter på baggrund af en databaseforespørgsel. Dette bryder altså ikke med 3 lagsarkitekturen. Domæneobjekterne må også gerne kendes af præsentationslaget, idet data jo skal vises på skærmen. Logisk tilhører domæneobjekterne dog til i det mellemste modellag, og det er vigtigt at objekter i dette lag ikke har kendskab til, hvordan de bruges på jsp siderne, ej heller ved hvordan de skabes på baggrund af ResultSet i data access laget. En måde at sikre sig den lave kobling ml. præsentationslaget og modellaget er at anvende MVC. 

MVC er et pattern, som anvendes i præsentations-laget og er ikke et andet navn for 3 lagsarkitektur. Servlet(ter) fungerer som Controller(e), JSP sider som Views, og det data som Controller giver JSP siderne, er data fra modellaget.

### Test
- Unit test = test af metode i en klasse
- Integrationstest = hvis der under test af metode forbindes til databasen
- Accepttest/Systemtest = test af hel funktionalitet inkl. UI, typisk foretaget af bruger på hjemmesiden/PO.

En test case = test af én ting, fx én unit test af en metode, med et bestemt sæt af parametre.

Man kan/bør både have test cases for gyldige (uk: valid) værdier og test cases for ugyldige (uk: invalid) værdier (gælder for alle tre niveauer af tests), så man også tester robusthed af programmet i forbindelse med fejlindtastninger m.m.

### User stories
I forlængelse af accepttest, kan man sige at en user story skal give mening ud fra et brugersynspunkt. 

Altså hvorfor har man denne user story (WHY). 

Nogle gange ligger begrundelse nogenlunde tydeligt nok i teksten til user story, så man ikke behøver afsluttet teksten med et ”fordi …” (taget fra et af jeres projekter):

”Som Fog medarbejder vil jeg gerne have udskrevet en materialeliste fladt med tag”

Andre gange er det ikke tydeligt, hvorfor man som PO ønsker en user story, og her ville et ”fordi …” have hjulpet (taget fra et af jeres projekter):

”Som fog kunde vil jeg gerne kunne logge ind”

Andre gange er en user story så store at de nærmest er overskrift på hele systemet og er faktisk slet ikke en user story (taget fra et af jeres projekter):

”Som Fog medarbejder vil jeg gerne have en web application”

### Feedback fra PO
Det var tydeligt i forbindelse med demoer for Fog i fredags, at de blev meget begejstret for funktion til 3D tegning. Selvom man som projektgruppe ikke har implementeret dette, kan man godt bruge denne kundeoplevelse i forbindelse med eksamen (hvis man trækker spørgsmål hvor det er relevant at nævne ).

Altså, hvor forretningsværdi først kan (er)kendes i mødet med kunden og den feedback man kan få herfra. Man kan som udvikler gøres sig nogle antagelser om hvad kunde og/eller slutbruger ønsker sig, men reelt vides det først i samspillet med kunden. Derfor har Scrum også indlagt aktiviteter med kontakt ml. team og kunde både i starten og slutningen af hver sprint. 

### Brug af ”fine” begreber
Vi har snakket flere gange om at det er fint at kunne buzz words til eksamen, men at det centrale er at I forstår problematikken og kan beskrive den. 

I forbindelse med følgende tekst (klippet af et af jeres projektet), ville det fx være fint at kunne bruge refaktorering som begreb for den aktivitet, der beskrives her: 

”Vi skal også havde tjekket efter om der er noget kode som ikke længere skulle bruges, eller om der faktisk er noget af det som er duplicate, så det bare skal fjernes.”

### Refleksion
Generelt får man højere karakter, hvis man kan reflektere og ikke bare referere.

Et programmeringseksempel: Hvorfor blev HashMap valgt som datastruktur i en given kode. Fordele (og evt. ulemper) ved det givne valg i den konkrete kontekst. 

Eksempler fra processen:
I stedet for blot at nævne hvem som blev Scrum Master i jeres gruppe, så beskriv hvorfor personen blev valgt. 
Hvilke kvaliteter bør en Scrum Master besidde og hvordan gik det med jeres Scrum Master (husk at bagklogskabens lys altid er det klareste).

Der er grupper som fint har nævnt hvorledes fx burndown chart har hjulpet dem med at se fremdriften (eller mangel på same) i et sprint. 

Der er også grupper, som siger at deres estimater løbende blev bedre, men uden at give forklaring på hvorfor det forholder sig sådan. 

Man skal altså gerne kunne demonstrere at man træffer reflekterede valg og kan se fordele og ulemper herved. Generelt kan man sige at et fravalg også er et valg.

Man kan også tale om at I løbende er begyndt at få jer en ”udvikler toolbox”. Altså en værktøjskasse med en række praktikker som kan anvendes i forbindelse med sprint aktiviteter (listen nedenfor er ikke udtømmende):

-Par programmering
-Code Review
-Code coverage (JaCocoverage)
-Refaktorering
-Design patterns
-Versionsstyring
-…

Hver har de deres særlige formål, men de er alle rettet imod udvikleren til at understøtte kodekvalitet. 


### Ide til demo
Vis det bedste frem som I har. 
Har man fx mail funktion, bør den demo’es til eksamen. Har man responsivt design, fx med Bootstrap for at sikre god mobil kompatibilitet til hjemmesiden bør det også demo’es.

### Forbedringer af kodedokumentation 
Hvis I synes at der er et diagram i jeres afleverede rapport som ikke er fyldestgørende eller lige frem mangler i rapporten, kunne det være en idé at inddrage i gruppens fællespræsentation. 

Der er flere grupper, hvis arkitekturdiagram, designklassediagram og/eller sekvensdiagram godt kunne bruge en revision for at gøre det mere forståeligt og dermed mere brugbart i forbindelse med senere vedligehold af koden. 

Hvis man har et godt klassediagram over sin kode, vil det være et godt redskab til at vurdere koblingen i programmet, både mellem lagene og inden for et enkelt lag.
