**

# Progettazione Guidata dal Dominio in Go: Guida Completa

  

## Costruire applicazioni enterprise scalabili con Go, AWS, SvelteKit e CQRS

  

### Versione Estesa - Applicazione "Where Should I Be?" con SvelteKit

---

  

  

## Indice

  

  

- **[Parte I: Fondamenta e Contesto](#parte-i-fondamenta-e-contesto)**
- [[Go Domain Driven Design#Capitolo 1 L'Importanza del Software Aziendale Moderno]]
- [Capitolo 2: L'Applicazione di Esempio: "Where Should I Be?"](#capitolo-2-lapplicazione-di-esempio-where-should-i-be)

  

- [Capitolo 3: Architettura del Backend e Comunicazione tra Servizi](#capitolo-3-architettura-del-backend-e-comunicazione-tra-servizi)

  

- [Capitolo 4: Autenticazione e Sicurezza su AWS](#capitolo-4-autenticazione-e-sicurezza-su-aws)

  

- [Capitolo 5: Scelte Architetturali: Server vs. Serverless](#capitolo-5-scelte-architetturali-server-vs-serverless)

  

  

**[Parte II: Progettazione Tattica con DDD](#parte-ii-progettazione-tattica-con-ddd)**

  

  

- [Capitolo 6: Introduzione al Domain-Driven Design](#capitolo-6-introduzione-al-domain-driven-design)

  

- [Capitolo 7: Ubiquitous Language - Il Linguaggio Condiviso](#capitolo-7-ubiquitous-language---il-linguaggio-condiviso)

  

- [Capitolo 8: Aggregates e Confini di Consistenza](#capitolo-8-aggregates-e-confini-di-consistenza)

  

- [Capitolo 9: Value Objects e Immutabilità](#capitolo-9-value-objects-e-immutabilità)

  

- [Capitolo 10: Entities e Identità nel Ciclo di Vita](#capitolo-10-entities-e-identità-nel-ciclo-di-vita)

  

- [Capitolo 11: Domain Services](#capitolo-11-domain-services)

  

  

**[Parte III: Architettura Pulita e Pattern Avanzati](#parte-iii-architettura-pulita-e-pattern-avanzati)**

  

  

- [Capitolo 12: Clean Architecture e Separazione delle Responsabilità](#capitolo-12-clean-architecture-e-separazione-delle-responsabilità)

  

- [Capitolo 13: Repository Pattern e Astrazione della Persistenza](#capitolo-13-repository-pattern-e-astrazione-della-persistenza)

  

- [Capitolo 14: Dependency Injection Professionale in Go](#capitolo-14-dependency-injection-professionale-in-go)

  

- [Capitolo 15: CQRS e Event Sourcing](#capitolo-15-cqrs-e-event-sourcing)

  

  

**[Parte IV: Progettazione Strategica](#parte-iv-progettazione-strategica)**

  

  

- [Capitolo 16: Bounded Contexts](#capitolo-16-bounded-contexts)

  

- [Capitolo 17: Event Storming: Dalla Specifica al Design](#capitolo-17-event-storming-dalla-specifica-al-design)

  

- [Capitolo 18: Context Mapping](#capitolo-18-context-mapping)

  

  

**[Parte V: Integrazione e API Robuste](#parte-v-integrazione-e-api-robuste)**

  

  

- [Capitolo 19: OpenAPI 3.1: Il Contratto tra Frontend e Backend](#capitolo-19-openapi-31-il-contratto-tra-frontend-e-backend)

  

- [Capitolo 20: Gestione della Concorrenza e delle Sessioni HTTP in Go](#capitolo-20-gestione-della-concorrenza-e-delle-sessioni-http-in-go)

  

- [Capitolo 21: Integrazione Resiliente con OpenAI](#capitolo-21-integrazione-resiliente-con-openai)

  

  

**[Parte VI: Persistenza Scalabile su AWS](#parte-vi-persistenza-scalabile-su-aws)**

  

  

- [Capitolo 22: Disaccoppiare la Persistenza con Lambda e SQS](#capitolo-22-disaccoppiare-la-persistenza-con-lambda-e-sqs)

  

- [Capitolo 23: Scelta del Database su AWS: DynamoDB per Costo ed Efficienza](#capitolo-23-scelta-del-database-su-aws-dynamodb-per-costo-ed-efficienza)

  

- [Capitolo 24: Una Strategia di Testing Completa](#capitolo-24-una-strategia-di-testing-completa)

  

  

**[Parte VII: Sviluppo, Deployment e Operations](#parte-vii-sviluppo-deployment-e-operations)**

  

  

- [Capitolo 25: Frontend Moderno con SvelteKit](#capitolo-25-frontend-moderno-con-sveltekit)

  

- [Capitolo 26: Il Ciclo di Sviluppo Iterativo di Due Settimane](#capitolo-26-il-ciclo-di-sviluppo-iterativo-di-due-settimane)

  

- [Capitolo 27: Infrastructure as Code (IaC) con AWS CDK](#capitolo-27-infrastructure-as-code-iac-con-aws-cdk)

  

- [Capitolo 28: CI/CD, Sicurezza e Deployment Continuo](#capitolo-28-cicd-sicurezza-e-deployment-continuo)

  

- [Capitolo 29: Monitoring e Observability con AWS X-Ray e CloudWatch](#capitolo-29-monitoring-e-observability-con-aws-x-ray-e-cloudwatch)

  

- [Capitolo 30: Conclusioni e Prossimi Passi](#capitolo-30-conclusioni-e-prossimi-passi)

  

  

- Capitolo 25: Frontend Moderno con SvelteKit

  

- Capitolo 26: Il Ciclo di Sviluppo Iterativo di Due Settimane

  

- Capitolo 27: Infrastructure as Code (IaC) con AWS CDK

  

- Capitolo 28: CI/CD, Sicurezza e Deployment Continuo

  

- Capitolo 29: Monitoring e Observability con AWS X-Ray e CloudWatch

  

- Capitolo 30: Conclusioni e Prossimi Passi

  

  

---

  

# **Parte I: Fondamenta e Contesto**

  

  

## Capitolo 1: L'Importanza del Software Aziendale Moderno

  

  

Benvenuti al primo capitolo del nostro viaggio nella costruzione di software enterprise robusto e scalabile. Prima di immergerci nel codice Go, nelle architetture cloud e nei pattern di progettazione, è fondamentale fare un passo indietro e capire il "perché". Perché la progettazione del software è diventata così cruciale? Quali sfide definiscono lo sviluppo di applicazioni moderne e come possiamo attrezzarci per vincerle?

  

  

Questo capitolo esplora il panorama attuale dello sviluppo software, delineando le forze che spingono verso approcci più sofisticati come il Domain-Driven Design (DDD) e le architetture a microservizi.

  

  

### 1.1. Oltre le Applicazioni CRUD

  

  

Per molti anni, gran parte dello sviluppo software aziendale poteva essere riassunto con l'acronimo **CRUD**: Create, Read, Update, Delete. Si trattava di costruire interfacce, spesso per il web, che fungevano da involucro gradevole per un database relazionale. La logica di business era minima e spesso relegata a stored procedure o a semplici validazioni lato server.

  

  

Questo modello non è scomparso, ma rappresenta oggi solo una piccola frazione delle sfide che affrontiamo. Il software moderno deve fare molto di più:

  

  

- **Gestire una Complessità Esponenziale**: I modelli di business sono diventati più complessi. Pensiamo alla nostra applicazione "Where Should I Be?": non si tratta solo di salvare un "viaggio" in un database. Dobbiamo gestire le preferenze degli utenti, integrare l'intelligenza artificiale per i suggerimenti, calcolare itinerari ottimali e forse, in futuro, gestire prenotazioni e pagamenti. Questa non è una complessità tecnica, è una **complessità di dominio**.

  

- **Scalare per un Pubblico Globale**: Grazie al cloud, un'applicazione può raggiungere milioni di utenti dal giorno uno. Questo impone requisiti di performance, resilienza e disponibilità che erano impensabili per le vecchie applicazioni monolitiche on-premise.

  

- **Rispondere Rapidamente al Mercato**: Il business non aspetta. La capacità di rilasciare nuove funzionalità in modo rapido, sicuro e indipendente è un vantaggio competitivo enorme. Un'architettura monolitica, dove ogni piccola modifica richiede il test e il deployment dell'intera applicazione, è un freno all'agilità.

  

- **Essere Resiliente ai Fallimenti**: In un sistema distribuito, il fallimento non è un'opzione, è una certezza. Un servizio esterno potrebbe non rispondere, un database potrebbe avere un picco di latenza, una rete potrebbe essere instabile. Il software moderno deve essere progettato per "degradare con grazia" anziché crollare completamente.

  

  

### 1.2. La Risposta Architetturale

  

  

Per affrontare queste sfide, l'industria si è mossa verso nuovi paradigmi architetturali. In questo libro, ne esploreremo e implementeremo diversi:

  

  

- **Domain-Driven Design (DDD)**: Come vedremo, il DDD è l'approccio principale per domare la complessità del dominio. Ci impone di concentrarci sul cuore del problema di business e di creare un modello software che lo rifletta fedelmente.

  

- **Microservizi**: Invece di un unico, grande monolite, l'applicazione viene scomposta in servizi più piccoli e indipendenti, ognuno responsabile di una specifica area di business (es. servizio Utenti, servizio Viaggi, servizio Suggerimenti). Questo favorisce l'agilità, la scalabilità selettiva e la resilienza.

  

- **Cloud Native e Serverless**: Sfruttare appieno la potenza del cloud (in particolare AWS, nel nostro caso) significa progettare applicazioni che non sono semplicemente "ospitate" nel cloud, ma che ne utilizzano i servizi gestiti (database, code, funzioni serverless) per ridurre il carico operativo e aumentare l'efficienza.

  

- **CQRS (Command Query Responsibility Segregation)**: Un pattern potente che separa le operazioni di scrittura (Comandi) da quelle di lettura (Query). Questo ci permette di ottimizzare in modo indipendente i percorsi di dati, migliorando performance e scalabilità, come vedremo nel dettaglio più avanti.

  

  

### 1.3. Perché Go?

  

  

In questo scenario, il linguaggio di programmazione **Go** (spesso chiamato Golang) si è ritagliato un ruolo da protagonista per lo sviluppo backend. Le sue caratteristiche lo rendono una scelta eccellente per il software enterprise moderno:

  

  

1. **Semplicità e Leggibilità**: Go ha una sintassi minimale e un set di funzionalità ortogonali. Questo riduce il carico cognitivo per gli sviluppatori e rende le codebase più facili da mantenere nel tempo, un fattore critico nei progetti a lungo termine.

  

2. **Prestazioni Eccellenti**: Essendo un linguaggio compilato che produce un singolo binario statico, Go offre performance vicine a quelle di C/C++, ma con la sicurezza della gestione della memoria (garbage collection). È ideale per servizi di rete ad alta intensità.

  

3. **Concorrenza di Prima Classe**: La concorrenza è un requisito fondamentale per i sistemi moderni. Le _goroutine_ e i _canali_ di Go offrono un modello di concorrenza semplice e incredibilmente potente, perfetto per gestire migliaia di richieste simultanee in un server HTTP o per processare messaggi da una coda.

  

4. **Ecosistema Robusto per il Cloud**: Go è il linguaggio con cui sono stati costruiti molti degli strumenti fondamentali del mondo cloud native, come Docker e Kubernetes. La sua toolchain, i test integrati e la facilità di cross-compilazione lo rendono perfetto per la containerizzazione e il deployment in ambienti cloud.

  

  

### 1.4. Obiettivo del Libro

  

  

L'obiettivo di questo libro non è solo insegnarvi a scrivere codice Go. È insegnarvi a pensare come un **architetto di software**. Attraverso la costruzione passo-passo dell'applicazione "Where Should I Be?", uniremo la potenza di Go, la flessibilità di AWS e l'espressività di SvelteKit, tenuti insieme dalla filosofia del Domain-Driven Design.

  

  

Siete pronti a costruire software che non solo funziona, ma che è anche manutenibile, scalabile e allineato ai veri obiettivi di business? Iniziamo.

  

  

---

  

  

## Capitolo 2: L'Applicazione di Esempio: "Where Should I Be?"

  

  

Per imparare a costruire software complesso, non c'è modo migliore che costruirne uno. La teoria è fondamentale, ma è nell'applicazione pratica che i concetti prendono vita. In questo libro, il nostro campo di battaglia e laboratorio sarà un'applicazione reale che chiameremo **"Where Should I Be?"**.

  

  

Questo capitolo introduce il concetto dell'applicazione, i suoi obiettivi di business e le sue funzionalità principali. Comprendere il "cosa" stiamo costruendo è il primo passo indispensabile prima di decidere "come" costruirlo. Questo processo di comprensione del dominio è il cuore pulsante del DDD.

  

  

### 2.1. Il Concetto: Pianificazione di Viaggi Intelligente

  

  

L'idea di base di "Where Should I Be?" è semplice da descrivere, ma complessa da realizzare:

  

  

> "Where Should I Be?" è un'applicazione web che aiuta gli utenti a scoprire nuove destinazioni e a pianificare itinerari di viaggio personalizzati, sfruttando la potenza dell'intelligenza artificiale per fornire suggerimenti unici e pertinenti.

  

  

L'obiettivo è superare le classiche guide di viaggio statiche o i motori di ricerca generici. Vogliamo creare un assistente di viaggio personale che impari a conoscere i gusti dell'utente e lo ispiri con idee che non avrebbe trovato altrove.

  

  

### 2.2. Il Dominio di Business

  

  

Analizziamo il dominio di business per identificare i concetti chiave. Questo è il primo passo informale verso la creazione del nostro _Ubiquitous Language_.

  

  

- **Utente (User)**: Il protagonista dell'applicazione. Un utente si registra, crea un profilo e gestisce i propri viaggi. Dobbiamo conoscere le sue **Preferenze (Preferences)**: ama l'arte? La natura? Il cibo gourmet? Le avventure estreme? Queste preferenze saranno cruciali per la personalizzazione.

  

- **Viaggio (Trip)**: È il contenitore principale della pianificazione. Un Viaggio ha un nome (es. "Weekend a Roma"), un intervallo di date e un insieme di **Tappe (Stops)**. Ogni Tappa rappresenta una visita a una specifica **Località (Location)** in un certo giorno.

  

- **Località (Location)**: Un luogo fisico nel mondo, come il "Colosseo" o la "Torre Eiffel". Ha attributi come nome, descrizione, coordinate geografiche e categoria (es. museo, ristorante, parco).

  

- **Suggerimento (Suggestion)**: Questa è la parte "intelligente" dell'app. Un utente può chiedere un suggerimento, ad esempio: "Suggeriscimi un itinerario di 3 giorni a Lisbona per un amante del cibo e della fotografia". Il sistema, usando un modello di AI (come quelli offerti da OpenAI), genera un potenziale itinerario che l'utente può poi importare e modificare nel suo piano di Viaggio.

  

  

### 2.3. Funzionalità Chiave (User Stories)

  

  

Traduciamo questi concetti in funzionalità concrete dal punto di vista dell'utente:

  

  

1. **Gestione del Profilo Utente**:

  

    - _Come utente_, voglio potermi registrare e accedere in modo sicuro.

  

    - _Come utente_, voglio poter definire e aggiornare le mie preferenze di viaggio (interessi, budget, stile di viaggio).

  

2. **Pianificazione del Viaggio**:

  

    - _Come utente_, voglio poter creare un nuovo Viaggio specificando una destinazione e delle date.

  

    - _Come utente_, voglio poter aggiungere, rimuovere e riordinare le Tappe all'interno del mio Viaggio.

  

    - _Come utente_, voglio poter visualizzare il mio itinerario su una mappa.

  

3. **Generazione di Suggerimenti AI**:

  

    - _Come utente_, voglio poter descrivere il tipo di viaggio che desidero in linguaggio naturale.

  

    - _Come utente_, voglio ricevere un itinerario suggerito basato sulla mia richiesta e sulle mie preferenze salvate.

  

    - _Come utente_, voglio poter importare un Suggerimento (o parti di esso) nel mio piano di Viaggio attivo.

  

4. **Esplorazione**:

  

    - _Come utente_, voglio poter cercare Località specifiche e leggere informazioni su di esse.

  

    - _Come utente_, voglio poter vedere i viaggi e gli itinerari creati da altri utenti (se resi pubblici).

  

  

### 2.4. La Visione a Lungo Termine

  

  

Un buon software è progettato per evolvere. Mentre la nostra implementazione iniziale si concentrerà sulle funzionalità di base, l'architettura che progetteremo deve tenere conto delle possibili evoluzioni future, come:

  

  

- **Collaborazione**: Permettere a più utenti di pianificare un viaggio insieme.

  

- **Booking**: Integrare API di terze parti per prenotare voli, hotel e attività.

  

- **Gamification**: Introdurre badge o punti per gli utenti che completano viaggi o scrivono recensioni.

  

- **Offline Mode**: Permettere l'accesso agli itinerari anche senza connessione a internet.

  

  

Avere questa visione ci aiuta a prendere decisioni architetturali più sagge oggi, evitando di finire in un vicolo cieco domani. Ad esempio, la scelta di usare microservizi (Capitolo 3) ci darà la flessibilità di aggiungere un nuovo servizio "Booking" in futuro senza dover stravolgere l'intera applicazione.

  

  

### 2.5. Conclusione

  

  

Ora abbiamo un'idea chiara di "cosa" stiamo costruendo. "Where Should I Be?" è un'applicazione con una significativa **complessità di dominio**. Non è un semplice CRUD. Le relazioni tra Utenti, Preferenze, Viaggi, Tappe e Suggerimenti AI sono ricche e governate da regole di business precise.

  

  

Questa complessità la rende il candidato ideale per applicare i principi del Domain-Driven Design. Nei prossimi capitoli, inizieremo a definire l'architettura tecnica che darà vita a questa visione.

  

  

---

  

  

## Capitolo 3: Architettura del Backend e Comunicazione tra Servizi

  

  

Dopo aver definito il "perché" (Capitolo 1) e il "cosa" (Capitolo 2), è il momento di affrontare il "come". Come struttureremo il nostro sistema per gestire la complessità del dominio di "Where Should I Be?" in modo scalabile e manutenibile? La risposta risiede in un'**architettura a microservizi**.

  

  

In questo capitolo, delineeremo l'architettura di alto livello del backend, spiegheremo perché i microservizi sono una scelta vincente per il nostro progetto e definiremo come questi servizi comunicheranno tra loro utilizzando tecnologie moderne come gRPC e REST.

  

  

### 3.1. Perché i Microservizi?

  

  

Un'architettura a microservizi scompone un'applicazione complessa in un insieme di servizi più piccoli, coesi e autonomi. Ogni servizio è responsabile di una specifica capacità di business e può essere sviluppato, deployato e scalato in modo indipendente.

  

  

Per "Where Should I Be?", questo approccio offre vantaggi decisivi:

  

  

- **Allineamento con il Dominio (DDD)**: L'idea di scomporre il sistema in servizi si sposa perfettamente con il pattern strategico del DDD dei **Bounded Context** (che vedremo nella Parte IV). Possiamo mappare ogni Bounded Context a un microservizio (o a un insieme di essi). Ad esempio:

  

    - `IdentityService`: Gestisce utenti, autenticazione, profili.

  

    - `PlannerService`: Gestisce la creazione e la modifica di viaggi e tappe.

  

    - `SuggestionService`: Si occupa di interagire con l'AI e generare suggerimenti.

  

- **Scalabilità Selettiva**: Il `SuggestionService` potrebbe richiedere molta CPU quando interroga l'AI, mentre il `PlannerService` potrebbe essere più intensivo in termini di I/O del database. Con i microservizi, possiamo allocare risorse (più CPU, più memoria, più istanze) a ogni servizio in base alle sue esigenze specifiche, ottimizzando i costi.

  

- **Resilienza (Fault Isolation)**: Se il `SuggestionService` dovesse avere un problema e smettere di funzionare, gli utenti potrebbero non essere in grado di generare nuovi itinerari, ma potrebbero comunque accedere e modificare i loro viaggi esistenti gestiti dal `PlannerService`. Il fallimento di un componente non trascina con sé l'intero sistema.

  

- **Libertà Tecnologica**: Sebbene useremo Go per la maggior parte dei servizi, in futuro potremmo decidere che un particolare problema (es. analisi dati) sia risolto meglio con un altro linguaggio, come Python. L'architettura a microservizi ce lo permette, a patto che i servizi comunichino tramite protocolli standard.

  

  

### 3.2. Panoramica dell'Architettura

  

  

La nostra architettura di partenza sarà composta da alcuni servizi chiave, un API Gateway e il frontend SvelteKit.

  

  

```

  

+----------------+      +------------------+      +--------------------+

  

|                |      |                  |      |                    |

  

| Frontend       |----->|   API Gateway    |----->|   IdentityService  | (REST/HTTP)

  

| (SvelteKit)    |      |   (HTTP/REST)    |      |   (Go)             |

  

|                |      |                  |      +--------------------+

  

+----------------+      +--------+---------+

  

                                 |

  

                                 | (gRPC)

  

                                 |

  

           +---------------------+---------------------+

  

           |                                           |

  

+----------v---------+                      +----------v-----------+

  

|                    |                      |                      |

  

|  PlannerService    | (gRPC)               | SuggestionService    |

  

|  (Go)              |<-------------------->| (Go)                 |

  

|                    |                      |                      |

  

+--------------------+                      +----------------------+

  

```

  

  

**Componenti:**

  

  

- **Frontend (SvelteKit)**: L'applicazione single-page con cui l'utente interagisce nel browser.

  

- **API Gateway**: È l'unico punto di ingresso (_entrypoint_) per tutte le richieste provenienti dall'esterno (il nostro frontend). Si occupa di routing, autenticazione, rate limiting e altre _cross-cutting concerns_. Espone un'API **RESTful** (basata su HTTP) sicura e pubblica.

  

- **Servizi Backend (Go)**: Sono i microservizi che implementano la logica di business. **Non sono esposti direttamente a Internet**. Comunicano tra loro e con l'API Gateway tramite un protocollo ad alte prestazioni.

  

  

### 3.3. Comunicazione: REST vs. gRPC

  

  

Una scelta architetturale cruciale è come i servizi parlano tra loro. Adotteremo un approccio ibrido, usando lo strumento giusto per il lavoro giusto.

  

  

#### **REST/HTTP per la Comunicazione Esterna (Frontend ↔ API Gateway)**

  

  

L'API esposta dall'API Gateway al frontend SvelteKit sarà basata su **REST (Representational State Transfer)**.

  

  

- **Perché?**: REST su HTTP è lo standard de facto per le API web pubbliche. È universalmente supportato da browser, librerie client e strumenti di sviluppo. È basato su testo (JSON), il che lo rende facile da debuggare e ispezionare.

  

- **Contratto API**: Definiremo questa API in modo rigoroso utilizzando la specifica **OpenAPI 3.1** (come vedremo nel Capitolo 19). Questo "contratto" garantisce che frontend e backend siano sempre allineati.

  

  

#### **gRPC per la Comunicazione Interna (Servizio ↔ Servizio)**

  

  

Per la comunicazione tra l'API Gateway e i microservizi interni, e tra i microservizi stessi, useremo **gRPC**.

  

  

- **Cos'è gRPC?**: È un framework RPC (Remote Procedure Call) moderno, open source e ad alte prestazioni, inizialmente sviluppato da Google. Permette a un'applicazione di chiamare metodi su un servizio server su un'altra macchina come se fosse un oggetto locale.

  

- **Perché gRPC?**:

  

    1. **Performance**: gRPC utilizza **HTTP/2** per il trasporto e **Protocol Buffers (Protobuf)** come formato di serializzazione. Protobuf è un formato binario molto più compatto e veloce da parsare rispetto a JSON, risultando in una latenza di rete inferiore e un minore utilizzo della CPU.

  

    2. **Contratti Fortemente Tipizzati**: Le API gRPC sono definite in file `.proto` usando il linguaggio di definizione di Protobuf. Da questi file, possiamo generare automaticamente il codice client e server in decine di linguaggi (incluso Go). Questo elimina l'ambiguità e previene interi classi di errori di runtime dovuti a disallineamenti tra client e server.

  

    3. **Streaming**: gRPC supporta nativamente lo streaming bidirezionale, una funzionalità potente per scenari più avanzati che va oltre il semplice ciclo richiesta/risposta di REST.

  

  

> **Analogia**: Pensa a REST come a una lettera scritta in una lingua universale (come l'inglese), comprensibile da chiunque ma un po' verbosa. Pensa a gRPC come a una conversazione telefonica diretta tra due persone che parlano uno slang tecnico e super-efficiente: è molto più veloce, ma richiede che entrambi conoscano esattamente lo stesso slang (il contratto Protobuf).

  

  

### 3.4. Conclusione

  

  

Abbiamo delineato una spina dorsale architetturale moderna e robusta per "Where Should I Be?". L'architettura a microservizi ci fornisce la flessibilità per gestire la complessità e scalare in modo efficiente. La scelta strategica di usare **REST per le API pubbliche** e **gRPC per le comunicazioni interne** ci permette di bilanciare l'interoperabilità universale con le massime prestazioni.

  

  

Nei prossimi capitoli, vedremo come rendere sicura questa architettura e quali modelli di deployment adottare nel cloud AWS. Questa solida base ci permetterà poi di concentrarci sulla modellazione del dominio all'interno di ogni servizio.

  

  

---

  

  

## Capitolo 4: Autenticazione e Sicurezza su AWS

  

  

Un'applicazione senza un solido sistema di sicurezza è come una casa senza serrature. L'autenticazione (chi sei?) e l'autorizzazione (cosa puoi fare?) sono aspetti non negoziabili di qualsiasi sistema enterprise moderno. Gestire manualmente password, sessioni e token è un'impresa complessa e rischiosa, piena di trappole che possono portare a vulnerabilità catastrofiche.

  

  

Fortunatamente, piattaforme cloud come AWS offrono servizi gestiti che ci permettono di implementare soluzioni di sicurezza di livello enterprise delegando gran parte del lavoro pesante. In questo capitolo, progetteremo il nostro sistema di autenticazione per "Where Should I Be?" utilizzando **Amazon Cognito** e definiremo il flusso di interazione tra il frontend, il backend e il servizio di identità.

  

  

### 4.1. Il Problema: Non Reinventare la Ruota della Sicurezza

  

  

Costruire un sistema di autenticazione da zero è notoriamente difficile. Bisogna preoccuparsi di:

  

  

- **Memorizzazione sicura delle password**: Mai salvare password in chiaro! È necessario usare algoritmi di hashing forti e lenti (come bcrypt o Argon2) con salt unici per ogni utente.

  

- **Gestione delle sessioni**: Creare, invalidare e far scadere i token di sessione in modo sicuro.

  

- **Flussi complessi**: Implementare funzionalità come "password dimenticata", verifica dell'email, autenticazione a più fattori (MFA).

  

- **Federazione di Identità**: Permettere agli utenti di accedere con i loro account Google, Facebook o Apple.

  

  

Ognuno di questi punti è un potenziale vettore di attacco se non implementato alla perfezione. La regola d'oro della sicurezza informatica è: **non implementare la tua crittografia o i tuoi protocolli di autenticazione se non sei un esperto di fama mondiale**.

  

  

### 4.2. La Soluzione: Amazon Cognito

  

  

**Amazon Cognito** è un servizio AWS che fornisce soluzioni di identità per applicazioni web e mobili. Si occupa di tutta la complessità della gestione degli utenti, permettendoci di concentrarci sulla logica della nostra applicazione.

  

  

Cognito offre due funzionalità principali che useremo:

  

  

1. **User Pools**: È un-elenco utenti completamente gestito. Si occupa della registrazione, dell'accesso, del recupero password, della MFA e della federazione con provider di identità social (Google, etc.) e enterprise (SAML 2.0).

  

2. **Identity Pools**: Permette di fornire credenziali AWS temporanee agli utenti (autenticati o anonimi) per accedere direttamente ad altri servizi AWS (come caricare un file su S3).

  

  

Per "Where Should I Be?", ci concentreremo principalmente sugli **User Pools**.

  

  

### 4.3. Il Flusso di Autenticazione con JWT

  

  

Il nostro sistema utilizzerà lo standard **JSON Web Tokens (JWT)** per gestire le sessioni autenticate. Un JWT è un token compatto e auto-contenuto che permette di trasmettere in modo sicuro informazioni tra le parti come un oggetto JSON. È "firmato" digitalmente, quindi possiamo fidarci del suo contenuto.

  

  

Ecco il flusso completo, passo dopo passo:

  

  

1. **Registrazione/Accesso (Frontend → Cognito)**: L'utente inserisce le sue credenziali (es. email/password) nel nostro frontend SvelteKit. Il frontend **non invia mai le password al nostro backend Go**. Utilizza invece la libreria AWS Amplify (o una libreria simile) per comunicare direttamente e in modo sicuro con l'endpoint di Amazon Cognito.

  

2. **Cognito Restituisce i Token (Cognito → Frontend)**: Se le credenziali sono valide, Cognito autentica l'utente e restituisce al frontend un set di JWT. I due più importanti sono:

  

    - `id_token`: Contiene le informazioni sull'identità dell'utente (username, email, etc.). Prova che l'utente è stato autenticato.

  

    - `access_token`: Concede i permessi per accedere alle risorse protette (le nostre API).

  

3. Chiamata API Protetta (Frontend → Backend): Quando il frontend deve chiamare un endpoint protetto del nostro backend (es. "ottieni i miei viaggi"), inserisce l'access_token nell'header Authorization della richiesta HTTP, secondo lo standard Bearer.

  

    Authorization: Bearer <ey...jwt...token...>

  

4. **Validazione del Token (Backend Go)**: Il nostro backend (specificamente, l'API Gateway o un middleware nei nostri servizi Go) riceve la richiesta. Prima di eseguire qualsiasi logica di business, deve validare il token JWT. Questo processo avviene **offline**, senza dover richiamare Cognito, ed è per questo che è così veloce ed efficiente. La validazione consiste in diversi controlli:

  

    - **Firma**: Il token è stato firmato dalla User Pool di Cognito corretta? Per verificarlo, il nostro servizio scarica e mette in cache le chiavi pubbliche (JWKS) di Cognito.

  

    - **Scadenza**: Il token non è scaduto?

  

    - **Audience (`aud`) e Issuer (`iss`)**: Il token è stato emesso per la nostra applicazione e dal nostro provider di identità?

  

5. **Accesso Autorizzato**: Se il token è valido, il backend sa con certezza chi è l'utente (grazie ai _claims_ contenuti nel token, come il `sub` o user ID) e che ha il permesso di accedere alla risorsa. La richiesta viene quindi processata. Se il token non è valido, il backend risponde con un errore `401 Unauthorized`.

  

  

### 4.4. Sicurezza tra Servizi con IAM

  

  

Oltre alla sicurezza degli utenti, dobbiamo garantire la sicurezza della comunicazione tra i nostri stessi servizi all'interno di AWS. Non vogliamo che un servizio compromesso possa chiamare indiscriminatamente tutti gli altri.

  

  

Per questo, utilizzeremo **AWS IAM (Identity and Access Management)**.

  

  

- Ogni nostro microservizio (es. `PlannerService` in esecuzione su ECS o Lambda) avrà un **ruolo IAM** associato.

  

- Questo ruolo avrà delle **policy** che specificano esattamente quali altre risorse AWS può invocare. Ad esempio, la policy del `PlannerService` potrebbe consentirgli di leggere e scrivere su una specifica tabella DynamoDB e di invocare il `SuggestionService`, ma nient'altro.

  

  

Questo principio, noto come **Principio del Minimo Privilegio (Principle of Least Privilege)**, è un fondamento della sicurezza nel cloud e limita drasticamente il raggio d'azione di un potenziale attacco.

  

  

### 4.5. Conclusione

  

  

Abbiamo progettato un'architettura di sicurezza robusta e moderna senza dover scrivere codice di autenticazione complesso e fragile.

  

  

- Delegando la gestione degli utenti e l'emissione dei token a **Amazon Cognito**, ci affidiamo a un servizio specializzato e sicuro.

  

- Utilizzando il flusso standard con **JWT**, creiamo un sistema di sessioni stateless, scalabile e interoperabile.

  

- Il nostro backend Go si occupa solo di **validare i token**, un'operazione veloce e sicura.

  

- Utilizzando i **ruoli IAM**, applichiamo il principio del minimo privilegio per la comunicazione interna.

  

  

Con queste fondamenta di sicurezza, possiamo procedere con la fiducia che la nostra applicazione e i dati dei nostri utenti siano protetti secondo le migliori pratiche del settore.

  

  

---

  

  

## Capitolo 5: Scelte Architetturali: Server vs. Serverless

  

  

Una delle decisioni più impattanti nell'architettura di un'applicazione cloud moderna riguarda il **modello computazionale**: dove e come verrà eseguito il nostro codice Go? Le due opzioni principali nel panorama AWS sono l'approccio basato su "server" (utilizzando container) e l'approccio "serverless" (utilizzando funzioni).

  

  

Questa non è una scelta dogmatica. Entrambi i modelli hanno punti di forza e di debolezza. La decisione giusta spesso non è "o l'uno o l'altro", ma "quale modello è più adatto per quale parte del sistema?". In questo capitolo, analizzeremo le differenze, i pro e i contro di entrambi gli approcci nel contesto della nostra applicazione "Where Should I Be?".

  

  

### 5.1. L'Approccio "Server": Container con AWS Fargate

  

  

Quando parliamo di "server" nel cloud moderno, raramente ci riferiamo a macchine virtuali (EC2) gestite manualmente. L'approccio più comune è la **containerizzazione** con Docker. Il nostro codice Go viene pacchettizzato in un'immagine Docker insieme a tutte le sue dipendenze, creando un artefatto portabile e consistente.

  

  

Per eseguire questi container su AWS, una scelta eccellente è **AWS Fargate**. Fargate è un motore di calcolo per container che ci permette di eseguire i nostri container Docker senza dover gestire i server o i cluster sottostanti. È una via di mezzo tra le macchine virtuali tradizionali e il puro serverless.

  

  

**Caratteristiche:**

  

  

- **Sempre Attivo (Always-on)**: Definiamo un "servizio" con un numero desiderato di container in esecuzione (es. 2 istanze del nostro `PlannerService` per l'alta disponibilità). Questi container sono sempre attivi, in attesa di ricevere traffico.

  

- **Controllo e Flessibilità**: Abbiamo pieno controllo sull'ambiente di esecuzione del container, sulle risorse (CPU/memoria) allocate e possiamo eseguire processi di lunga durata.

  

- **Costi Prevedibili**: Paghiamo per le risorse di calcolo che abbiamo allocato, per tutto il tempo in cui sono in esecuzione, indipendentemente dal fatto che stiano servendo traffico o meno.

  

  

Pro per "Where Should I Be?":

  

  

✅ Performance Stabili: Nessun "cold start". I container sono sempre caldi e pronti a rispondere, ideale per le API sincrone rivolte all'utente (come quelle gestite dal nostro API Gateway).

  

  

✅ Task di Lunga Durata: Se avessimo un processo che richiede più di 15 minuti (il limite di AWS Lambda), un container sarebbe l'unica scelta.

  

  

✅ Connessioni Persistenti: Mantenere pool di connessioni al database aperte e ottimizzate è più semplice in un ambiente long-running.

  

  

Contro:

  

  

❌ Costi a Vuoto: Se l'applicazione ha traffico zero durante la notte, stiamo comunque pagando per i container inattivi.

  

  

❌ Gestione della Scalabilità: Dobbiamo configurare noi le regole di auto-scaling (es. "aggiungi un container se la CPU supera il 70%"), il che richiede un minimo di gestione.

  

  

### 5.2. L'Approccio "Serverless": Funzioni con AWS Lambda

  

  

Serverless non significa "senza server", ma piuttosto "senza che tu debba preoccuparti dei server". Con **AWS Lambda**, carichiamo il nostro codice Go (impacchettato in un file .zip o un'immagine container) e AWS si occupa di tutto il resto. Il codice viene eseguito solo quando viene attivato da un evento.

  

  

**Caratteristiche:**

  

  

- **Esecuzione su Evento (Event-driven)**: Una funzione Lambda non è sempre in esecuzione. Si "sveglia" in risposta a un evento: una richiesta HTTP da API Gateway, un nuovo messaggio in una coda SQS, un nuovo file in un bucket S3, etc.

  

- **Gestione Zero**: Non ci sono server da patchare, sistemi operativi da aggiornare o cluster da gestire.

  

- **Scalabilità Automatica e Granulare**: Se arrivano 1000 richieste in contemporanea, AWS avvierà automaticamente 1000 istanze concorrenti della nostra funzione per gestirle. La scalabilità è istantanea e gestita interamente dalla piattaforma.

  

- **Pagamento a Consumo (Pay-per-use)**: Paghiamo solo per il tempo di esecuzione effettivo del nostro codice, misurato in millisecondi, e per il numero di richieste. Se non c'è traffico, il costo è zero.

  

  

Pro per "Where Should I Be?":

  

  

✅ Efficienza dei Costi: Ideale per carichi di lavoro irregolari o "spiky". Il SuggestionService, che potrebbe essere usato intensamente solo a tratti, è un candidato perfetto.

  

  

✅ Velocità di Sviluppo: Riduce drasticamente l'overhead operativo, permettendo al team di concentrarsi sulla scrittura della logica di business.

  

  

✅ Architetture Event-Driven: Si integra nativamente con l'intero ecosistema di servizi AWS, rendendo semplice costruire flussi di lavoro reattivi e disaccoppiati.

  

  

Contro:

  

  

❌ Cold Start: La prima richiesta a una funzione "fredda" (non usata di recente) può subire un ritardo di centinaia di millisecondi o più, il tempo necessario ad AWS per inizializzare l'ambiente di esecuzione. Questo può essere un problema per le API sensibili alla latenza.

  

  

❌ Limiti di Esecuzione: Una singola invocazione di Lambda non può durare più di 15 minuti.

  

  

❌ Complessità nella Composizione: Orchestrare flussi di lavoro complessi che coinvolgono più funzioni può richiedere servizi aggiuntivi come AWS Step Functions.

  

  

### 5.3. La Scelta per il Nostro Progetto: Un Approccio Ibrido e Pragmatico

  

  

Come spesso accade in ingegneria del software, la risposta migliore non è una scelta assoluta, ma un compromesso intelligente. Per "Where Should I Be?", adotteremo un **approccio ibrido**:

  

  

1. **Servizi "Core" su Container (AWS Fargate)**:

  

    - L'**API Gateway** e i servizi sincroni principali come l'**IdentityService** e il **PlannerService** saranno implementati come servizi Go a lunga esecuzione su **AWS Fargate**.

  

    - **Motivazione**: Questi servizi gestiscono il percorso critico delle richieste degli utenti. Abbiamo bisogno di latenza bassa e prevedibile (nessun cold start) e della capacità di gestire pool di connessioni efficienti verso il database.

  

2. **Task Asincroni e "Write Side" su Serverless (AWS Lambda)**:

  

    - Sfrutteremo **AWS Lambda** per task asincroni, event-driven o che beneficiano della scalabilità on-demand.

  

    - **Esempi perfetti nel nostro dominio**:

  

        - Quando il `SuggestionService` riceve una richiesta, potrebbe immediatamente rispondere `202 Accepted` all'utente, e poi avviare un processo Lambda asincrono per interrogare l'API di OpenAI (che può essere lenta) e notificare l'utente quando il risultato è pronto.

  

        - Come vedremo con CQRS (Capitolo 15), potremmo usare Lambda per il "lato scrittura" del nostro sistema. Una richiesta di modifica (Comando) viene inviata a una coda SQS, e una funzione Lambda la preleva, la processa e aggiorna il database. Questo disaccoppia completamente la scrittura dalla lettura ed è incredibilmente resiliente e scalabile.

  

        - Invio di email di benvenuto quando un nuovo utente si registra su Cognito.

  

  

### 5.4. Conclusione

  

  

La scelta tra server e serverless non è una battaglia ideologica, ma una decisione di design strategica. Comprendendo i trade-off di ogni modello, possiamo progettare un sistema che sia allo stesso tempo performante, scalabile ed efficiente in termini di costi.

  

  

L'approccio ibrido che abbiamo scelto per "Where Should I Be?" ci offre il meglio di entrambi i mondi: la stabilità e le performance dei **container Fargate** per il nostro core sincrono, e la flessibilità, scalabilità e efficienza dei costi di **AWS Lambda** per i carichi di lavoro asincroni ed event-driven. Questa architettura flessibile ci posiziona perfettamente per le sfide future e per l'evoluzione della nostra applicazione.

  

  

---

  

# Parte II: Progettazione Tattica con DDD

  

  

La progettazione tattica del Domain-Driven Design ci fornisce gli strumenti pratici per tradurre il nostro modello di dominio in codice pulito, espressivo e manutenibile. Questi "building blocks" sono il vocabolario che useremo per costruire il cuore della nostra applicazione.

  

  

---

  

## Capitolo 6: Introduzione al Domain-Driven Design

  

  

Benvenuti nella Parte II di questo libro. Nelle sezioni precedenti, abbiamo gettato le fondamenta della nostra applicazione, "Where Should I Be?", definendo l'architettura generale, le tecnologie e le strategie di sicurezza. Ora è il momento di entrare nel cuore del software: il **dominio**.

  

  

In questo capitolo, introdurremo il **Domain-Driven Design (DDD)**, un approccio che rivoluzionerà il modo in cui pensate, progettate e scrivete software enterprise. Il DDD non è una tecnologia, un framework o una libreria; è una **filosofia di progettazione** che pone il focus sulla complessità del dominio di business, facilitando la collaborazione tra sviluppatori ed esperti di settore per creare modelli software che risolvono problemi reali in modo efficace e manutenibile.

  

  

Affronteremo il "perché" del DDD, esploreremo i suoi concetti fondamentali e vedremo come si applica direttamente al nostro progetto, preparandoci per i pattern tattici che analizzeremo nei capitoli successivi.

  

  

### 6.1. Il Problema: Complessità e Comunicazione

  

  

Immaginate di iniziare a lavorare su un nuovo progetto software. La richiesta iniziale sembra semplice: "Vogliamo un'app che suggerisca posti da visitare". Il team di sviluppo, desideroso di iniziare, apre l'IDE, crea un database con tabelle come `users`, `trips`, `locations` e inizia a scrivere endpoint CRUD (Create, Read, Update, Delete).

  

  

Nelle prime settimane, tutto procede a gonfie vele. Ma presto, iniziano a sorgere le domande difficili:

  

  

- Cosa succede se un utente vuole aggiungere una "tappa" a un "viaggio"? È solo un'altra riga nella tabella `locations` collegata al `trip`?

  

- Come gestiamo le diverse tipologie di utenti? Un utente "premium" ha limiti diversi rispetto a un utente "free"?

  

- Un "suggerimento" è la stessa cosa di una "destinazione"?

  

- Se un viaggio viene cancellato, cosa succede alle recensioni associate alle sue tappe?

  

  

Senza un approccio strutturato, il team rischia di prendere decisioni tecniche basate su una comprensione superficiale del business. La logica di business viene sparsa in punti diversi dell'applicazione: un po' nel codice dell'API, un po' in stored procedure nel database, un po' addirittura nel frontend. Questo porta a quello che è tristemente noto come **Anemic Domain Model**.

  

  

### Controesempio: L'Anemic Domain Model

  

  

Un Anemic Domain Model è un anti-pattern in cui gli oggetti del dominio contengono solo dati (proprietà con getter e setter) e nessuna logica di business. Tutta la logica viene gestita da classi esterne, spesso chiamate "Services" o "Managers".

  

  

Vediamo un esempio in Go che, purtroppo, è molto comune.

  

  

Go

  

  

```go

  

// anemic/trip.go

  

  

package anemic

  

  

import "github.com/google/uuid"

  

  

// Trip è una semplice struttura dati, un "data bag".

  

// Non ha logica, non protegge i suoi invarianti.

  

type Trip struct {

  

    ID          uuid.UUID

  

    Name        string

  

    Stops       []string // Semplici stringhe, nessuna validazione.

  

    Status      string   // "Planning", "InProgress", "Completed"

  

    MaxStops    int

  

}

  

  

// anemic/trip_service.go

  

  

package anemic

  

  

import "errors"

  

  

// TripService contiene tutta la logica di business.

  

// La logica è separata dai dati su cui opera.

  

type TripService struct {

  

    // ... dipendenze come il repository del database

  

}

  

  

func (s *TripService) AddStop(trip *Trip, newStop string) error {

  

    // 1. La logica di validazione è qui, fuori dall'oggetto Trip.

  

    if trip.Status != "Planning" {

  

        return errors.New("cannot add stops to a trip that is not in planning status")

  

    }

  

  

    // 2. Un'altra regola di business.

  

    if len(trip.Stops) >= trip.MaxStops {

  

        return errors.New("maximum number of stops reached")

  

    }

  

  

    // 3. La modifica dello stato avviene qui.

  

    trip.Stops = append(trip.Stops, newStop)

  

  

    // ... codice per salvare il trip nel database

  

    return nil

  

}

  

```

  

  

**Perché questo approccio è problematico?**

  

  

1. **Modello Povero**: L'oggetto `Trip` non ci dice nulla su cosa può fare o quali sono le sue regole. È solo un contenitore di dati. La vera "essenza" di un viaggio è dispersa altrove.

  

2. **Logica Duplicata**: Se un altro servizio avesse bisogno di aggiungere una tappa, dovrebbe conoscere e probabilmente reimplementare le stesse regole di validazione, portando a inconsistenze.

  

3. **Difficile da Comprendere**: Per capire tutte le regole che governano un `Trip`, un nuovo sviluppatore deve andare a caccia della logica in tutta la codebase, invece di guardare un unico punto coeso.

  

4. **Invarianti non Protetti**: Un invariante è una regola che deve essere sempre vera. Nell'esempio sopra, nulla impedisce a un programmatore di modificare direttamente `trip.Stops` da un'altra parte del codice, bypassando completamente la logica di `TripService`. Lo stato dell'oggetto non è protetto.

  

  

Il Domain-Driven Design nasce per risolvere proprio questi problemi, promuovendo la creazione di **Rich Domain Models**.

  

  

### 6.2. Il Cuore del DDD: Il Modello di Dominio Ricco

  

  

Il DDD ci insegna a invertire il paradigma. Invece di trattare gli oggetti di dominio come semplici sacchi di dati, li trasformiamo nel cuore pulsante dell'applicazione.

  

  

> Un **Modello di Dominio** non è solo un diagramma di classi o uno schema di database. È un sistema di astrazioni interconnesse che descrive aspetti specifici di un dominio. Include non solo gli attributi degli oggetti, ma anche il loro **comportamento** e le **regole** che li governano.

  

  

Riprendiamo l'esempio precedente, ma questa volta applicando i principi del DDD.

  

  

Go

  

  

``` go

  

// rich/trip.go

  

  

package rich

  

  

import (

  

    "errors"

  

    "github.com/google/uuid"

  

)

  

  

// Definiamo tipi specifici per migliorare la leggibilità e la sicurezza.

  

type TripStatus string

  

  

const (

  

    Planning   TripStatus = "Planning"

  

    InProgress TripStatus = "InProgress"

  

    Completed  TripStatus = "Completed"

  

)

  

  

// Trip è ora un oggetto ricco. Contiene dati E comportamento.

  

// Le sue proprietà non sono esportate per proteggere gli invarianti.

  

type Trip struct {

  

    id       uuid.UUID

  

    name     string

  

    stops    []string // In un vero DDD, questo sarebbe un []Stop (Value Object)

  

    status   TripStatus

  

    maxStops int

  

}

  

  

// NewTrip agisce come una "Factory" per garantire che un Trip

  

// venga creato sempre in uno stato valido.

  

func NewTrip(id uuid.UUID, name string, maxStops int) (*Trip, error) {

  

    if name == "" {

  

        return nil, errors.New("trip name cannot be empty")

  

    }

  

    if maxStops <= 0 {

  

        return nil, errors.New("max stops must be a positive number")

  

    }

  

    return &Trip{

  

        id:       id,

  

        name:     name,

  

        stops:    []string{},

  

        status:   Planning, // Lo stato iniziale è un invariante

  

        maxStops: maxStops,

  

    }, nil

  

}

  

  

// AddStop è un metodo dell'oggetto Trip.

  

// La logica di business vive con i dati che governa.

  

func (t *Trip) AddStop(newStop string) error {

  

    // 1. La validazione è co-locata con l'oggetto.

  

    if t.status != Planning {

  

        return errors.New("cannot add stops to a trip that is not in planning status")

  

    }

  

  

    // 2. L'invariante sul numero massimo di tappe è protetto.

  

    if len(t.stops) >= t.maxStops {

  

        return errors.New("maximum number of stops reached")

  

    }

  

    if newStop == "" {

  

        return errors.New("stop name cannot be empty")

  

    }

  

  

    // 3. La modifica dello stato è un comportamento intrinseco del Trip.

  

    t.stops = append(t.stops, newStop)

  

    return nil

  

}

  

  

// Metodi per cambiare stato, anch'essi con la loro logica.

  

func (t *Trip) Start() error {

  

    if t.status != Planning {

  

        return errors.New("trip can only be started from planning status")

  

    }

  

    if len(t.stops) == 0 {

  

        return errors.New("cannot start a trip with no stops")

  

    }

  

    t.status = InProgress

  

    return nil

  

}

  

  

// Getter pubblici per esporre i dati in modo controllato (read-only).

  

func (t *Trip) ID() uuid.UUID {

  

    return t.id

  

}

  

  

func (t *Trip) Status() TripStatus {

  

    return t.status

  

}

  

```

  

  

Confrontando i due esempi, la differenza è abissale. Nel secondo caso:

  

  

- **Coesione**: Dati e logica sono uniti. `Trip` ora descrive _cosa è_ e _cosa fa_.

  

- **Incapsulamento**: Nascondendo i campi (usando lettere minuscole in Go), preveniamo modifiche esterne illegali. L'unico modo per alterare lo stato del `Trip` è attraverso i suoi metodi, che applicano le regole di business.

  

- **Chiarezza**: Le regole del dominio sono esplicite e facili da trovare. L'oggetto si auto-documenta.

  

- **Robustezza**: È molto più difficile mettere l'oggetto in uno stato invalido.

  

  

Questo è l'obiettivo centrale del DDD: creare modelli ricchi ed espressivi che riflettano fedelmente la complessità del dominio di business.

  

  

### 6.3. I Pilastri del DDD: Progettazione Strategica e Tattica

  

  

Il Domain-Driven Design è tradizionalmente suddiviso in due parti principali, che lavorano in sinergia.

  

  

> **Riferimento Chiave:** La fonte definitiva per questi concetti è il libro di Eric Evans, ["Domain-Driven Design: Tackling Complexity in the Heart of Software"](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215). Sebbene denso, è una lettura fondamentale per chiunque voglia padroneggiare il DDD.

  

  

#### 1. Progettazione Strategica (Strategic Design)

  

  

La progettazione strategica si occupa del "quadro generale". È l'insieme di principi per analizzare e decomporre domini complessi in parti più gestibili. Si concentra meno sul codice e più sulla comprensione del business e sulla definizione dei confini. I suoi pattern principali, che esploreremo nella Parte IV, sono:

  

  

- **Ubiquitous Language (Linguaggio Ubiquo)**: È il concetto più importante del DDD. Si tratta di creare un linguaggio rigoroso e condiviso tra sviluppatori, esperti di dominio, product manager e chiunque sia coinvolto nel progetto. Se gli esperti chiamano una funzionalità "Suggerimento di Itinerario", il codice non dovrebbe contenere classi chiamate `TripRecommendation` o `JourneyProposal`. Dovrebbe chiamarsi `SuggerimentoItinerario`. Questo linguaggio viene usato nelle conversazioni, nei diagrammi, nel codice e nei test. Elimina l'ambiguità e la necessità di "traduzione" mentale. (Approfondiremo nel Capitolo 7).

  

- **Bounded Context (Contesto Delimitato)**: Un dominio di business complesso non ha un unico modello unificato. Il significato di un termine può cambiare a seconda del contesto. Ad esempio, nel nostro "Where Should I Be?", il concetto di "Utente" potrebbe essere diverso:

  

    - Nel contesto di **Autenticazione**, un "Utente" è definito da email, password hash e ruoli di sicurezza.

  

    - Nel contesto di **Pianificazione Viaggi**, un "Utente" potrebbe essere definito dal suo livello di abbonamento (che determina il numero massimo di viaggi) e dalle sue preferenze.

  

    - Nel contesto **Social**, un "Utente" potrebbe avere un profilo, una lista di amici e delle foto.

  

    Un Bounded Context è un confine esplicito (logico o fisico, come un microservizio) all'interno del quale un modello di dominio specifico è consistente e valido. Tentare di creare un unico, mega-oggetto "Utente" che serva tutti questi contesti porterebbe a un design fragile e confuso. (Approfondiremo nel Capitolo 16).

  

- **Context Mapping (Mappatura dei Contesti)**: Una volta definiti i Bounded Context, è necessario definire come interagiscono tra loro. Si ignorano? Collaborano strettamente? Uno si conforma al modello dell'altro? La mappatura dei contesti fornisce un catalogo di pattern per gestire queste relazioni inter-servizio. (Approfondiremo nel Capitolo 18).

  

  

#### 2. Progettazione Tattica (Tactical Design)

  

  

La progettazione tattica si occupa dei "dettagli implementativi" all'interno di un singolo Bounded Context. Fornisce un insieme di building block (mattoncini) per costruire un modello di dominio ricco ed espressivo. È qui che scriviamo il codice. Questi pattern, che sono il fulcro della Parte II e III, includono:

  

  

- **Entities (Entità)**: Oggetti che hanno un'identità distintiva che persiste nel tempo. Due entità sono diverse anche se i loro attributi sono identici. Un `Utente` è un'entità; anche se due utenti hanno lo stesso nome, sono persone diverse, distinte dal loro ID univoco. (Capitolo 10).

  

- **Value Objects (Oggetti Valore)**: Oggetti che descrivono una caratteristica di un dominio e sono definiti solo dai loro attributi. Non hanno un'identità concettuale. Due Value Objects con gli stessi attributi sono considerati uguali. Un `Indirizzo` o delle `CoordinateGPS` sono esempi classici. Sono tipicamente immutabili. (Capitolo 9).

  

- **Aggregates (Aggregati)**: Un cluster di oggetti (Entità e Value Objects) che vengono trattati come una singola unità ai fini delle modifiche dei dati. Ogni Aggregato ha una radice (l'**Aggregate Root**), che è l'unica Entità dell'aggregato accessibile dall'esterno. La radice è responsabile di mantenere la consistenza dell'intero aggregato, proteggendo i suoi invarianti. Nel nostro esempio, il `Trip` potrebbe essere l'Aggregate Root che gestisce un insieme di `Stop` (tappe). (Capitolo 8).

  

- **Repositories (Repository)**: Forniscono un'astrazione sopra la persistenza (database, file, API esterne). Dal punto di vista del dominio, un repository è come una "collezione" di aggregati in memoria. Ci permette di recuperare e salvare gli aggregati senza che il modello di dominio debba conoscere i dettagli di SQL, DynamoDB o qualsiasi altra tecnologia di storage. (Capitolo 13).

  

- **Domain Services (Servizi di Dominio)**: A volte, una logica di business importante non appartiene naturalmente a nessuna Entità o Value Object. Spesso coinvolge più aggregati. In questi casi, la logica viene incapsulata in un Domain Service. Ad esempio, un servizio che suggerisce il miglior hotel combinando dati da un `Trip` e dalle `UserPreferences` potrebbe essere un Domain Service. (Capitolo 11).

  

  

> **Approfondimento:** Martin Fowler fornisce eccellenti sintesi di questi pattern sul suo sito. La sua spiegazione degli [Anemic vs. Rich Domain Models](https://martinfowler.com/bliki/AnemicDomainModel.html) è un ottimo punto di partenza per comprendere la motivazione dietro il DDD.

  

  

### 6.4. Perché DDD per "Where Should I Be?"

  

  

Potreste chiedervi se tutto questo sia necessario per la nostra applicazione. La risposta è un sonoro **sì**. La complessità di "Where Should I Be?" non risiede nella tecnologia, ma nel dominio stesso. Abbiamo a che fare con concetti sfumati:

  

  

- **Pianificazione del Viaggio**: Gestire sequenze di tappe, budget, date, trasporti.

  

- **Suggerimenti Intelligenti**: Interagire con modelli di AI (come faremo con OpenAI), interpretarne i risultati e presentarli all'utente in modo coerente.

  

- **Preferenze Utente**: Modellare i gusti di un utente (arte, natura, cibo) e usarli per personalizzare l'esperienza.

  

- **Collaborazione**: In futuro, potremmo permettere a più utenti di pianificare un viaggio insieme, introducendo una complessità notevole.

  

  

Usare il DDD ci offre un percorso strutturato per affrontare questa complessità:

  

  

1. **Progettazione Strategica**: Identificheremo i Bounded Context principali. Potremmo avere:

  

    - `PlanningContext`: Responsabile di tutto ciò che riguarda la creazione e gestione di `Trip` e `Stop`.

  

    - `IdentityAccessContext`: Gestisce `User`, autenticazione e autorizzazione.

  

    - `SuggestionsContext`: Interagisce con servizi esterni (come OpenAI) per generare e gestire i `Suggestion`.

  

    Questa separazione ci permetterà di sviluppare e far evolvere ogni parte in modo indipendente, usando il modello più adatto per ciascuna.

  

2. **Progettazione Tattica**: All'interno di ogni contesto, useremo i pattern tattici per costruire modelli robusti.

  

    - Un `Trip` sarà un **Aggregate Root** nel `PlanningContext`.

  

    - Le `CoordinateGPS` di una `Stop` saranno un **Value Object**.

  

    - Un `User` sarà un'**Entity** nel `IdentityAccessContext`.

  

    - Il processo di salvataggio di un `Trip` avverrà tramite un **Repository**, che nasconderà i dettagli di AWS DynamoDB.

  

  

### 6.5. Quando NON Usare il DDD

  

  

Il DDD è uno strumento potente, ma non è una panacea. Applicarlo a problemi semplici è controproducente, un classico caso di "usare un cannone per uccidere una zanzara". Il DDD introduce un certo overhead cognitivo e di design che si giustifica solo in presenza di una reale complessità di dominio.

  

  

**Non usate il DDD se il vostro progetto è:**

  

  

- **Una semplice applicazione CRUD**: Se state costruendo un'interfaccia di amministrazione per gestire una lista di prodotti con campi semplici, un approccio basato su Anemic Model e servizi transazionali è probabilmente più veloce da implementare e più facile da mantenere.

  

- **Guidato dai dati o dall'integrazione**: Se il compito principale del software è spostare dati da un sistema A a un sistema B, con poche o nessuna trasformazione di business, il cuore del problema non è il dominio, ma l'integrazione.

  

- **Un problema con complessità puramente tecnica**: Se state costruendo un encoder video o un proxy di rete ad alte prestazioni, la sfida è tecnica, non di dominio di business.

  

  

In questi scenari, l'investimento richiesto per implementare Bounded Context, Aggregati e un Linguaggio Ubiquo non porterebbe benefici tangibili.

  

  

### 6.6. Conclusioni e Prossimi Passi

  

  

In questo capitolo, abbiamo scalfito la superficie del Domain-Driven Design. Abbiamo capito che il suo scopo primario è **gestire la complessità** intrinseca del software di business, mettendo il modello di dominio al centro di tutto. Abbiamo distinto tra la visione d'insieme della **Progettazione Strategica** e i mattoncini della **Progettazione Tattica**.

  

  

Soprattutto, abbiamo visto la differenza concreta tra un modello anemico, fragile e difficile da mantenere, e un modello ricco, robusto ed espressivo, che è l'obiettivo a cui tenderemo in questo libro.

  

  

Nei prossimi capitoli, ci tufferemo a capofitto nella Progettazione Tattica. Inizieremo con il concetto più importante di tutti: il **Linguaggio Ubiquo**. Impareremo come costruirlo e come usarlo come strumento principale per colmare il divario tra l'idea di business e il codice che la implementa.

  

  

---

  

  

### Risorse Aggiuntive e Link Utili

  

  

- **Libro (Il "Blue Book")**: [Domain-Driven Design: Tackling Complexity in the Heart of Software](https://www.dddcommunity.org/book/evans_2003/) di Eric Evans. Il testo fondamentale e originario.

  

- **Libro (Il "Red Book")**: [Implementing Domain-Driven Design](https://www.google.com/search?q=https://vaughnvernon.co/%3Fpage_id%3D168) di Vaughn Vernon. Un'eccellente guida pratica che traduce i concetti di Evans in codice e architettura.

  

- **Community**: [DDD Community](https://www.dddcommunity.org/). Un hub per articoli, risorse e gruppi di discussione.

  

- **Articolo di Martin Fowler**: ["Domain-Driven Design"](https://www.google.com/search?q=https://martinfowler.com/tags/domain-driven%2520design.html). Una raccolta dei suoi articoli sull'argomento, sempre chiari e illuminanti.

  

- **Go-DDD Esempio pratico**: [Repository GitHub di "Wild Workouts"](https://github.com/ThreeDotsLabs/wild-workouts-go-ddd-example). Un'applicazione di esempio completa scritta in Go che applica i principi DDD e Clean Architecture, sviluppata da Three Dots Labs. Un'ottima risorsa per vedere questi pattern "in azione".

  

---

  

## Capitolo 7: Ubiquitous Language - Il Linguaggio Condiviso

  

  

Nel capitolo precedente abbiamo introdotto il Domain-Driven Design come filosofia per dominare la complessità. Ora, è il momento di affondare le mani nel suo concetto più critico e fondamentale, la vera pietra angolare su cui poggia l'intero edificio del DDD: l'**Ubiquitous Language** (Linguaggio Ubiquo o Condiviso).

  

  

Sembra un concetto astratto, quasi accademico, ma la sua assenza è la causa principale del fallimento di innumerevoli progetti software. È il collante che tiene insieme il team di sviluppo e gli esperti di dominio. È lo strumento che trasforma le conversazioni in codice funzionante e il codice in una narrazione chiara del business.

  

  

In questo capitolo, esploreremo in profondità perché il Linguaggio Ubiquo è essenziale, come si manifesta nel codice Go e quali tecniche pratiche possiamo usare per scoprirlo, definirlo e farlo evolvere insieme alla nostra applicazione "Where Should I Be?".

  

  

---

  

  

### 7.1. La Torre di Babele del Software: Un Dramma Comune

  

  

Immaginiamo una riunione di avvio per una nuova funzionalità della nostra app "Where Should I Be?". La stanza (reale o virtuale) è piena di persone intelligenti e motivate.

  

  

**La Product Manager**, esperta del settore viaggi, dice:

  

  

> _"Dobbiamo permettere ai nostri clienti di **curare** una **collezione** di **punti d'interesse** per la loro **vacanza**. L'utente deve poter definire un budget e l'intelligenza artificiale deve validare che la selezione sia coerente."_

  

  

Il team di sviluppo annuisce. La riunione finisce e ognuno torna alla propria scrivania. Ecco cosa succede dopo:

  

  

1. **Il Backend Developer (parlando con un collega)**:

  

    > _"Ok, ho capito. Devo modificare il `TripManager` per aggiungere una lista di oggetti `Location` all'entità `Trip`. Implementerò un metodo `validateBudget()` nel servizio."_

  

2. **Il Database Administrator (progettando lo schema)**:

  

    > _"Perfetto. Aggiungo una tabella `POIs` (Points of Interest) con una foreign key `journey_id` che punta alla tabella `Journeys`."_

  

3. **Il Frontend Developer (scrivendo il codice SvelteKit)**:

  

    > _"Bene, creo un nuovo componente `ItineraryBuilder`. Farò una chiamata all'endpoint `/api/destinations` per popolare la lista che l'utente può modificare."_

  

  

Quattro persone, quattro linguaggi diversi per descrivere la stessa identica cosa.

  

  

- **Vacanza** è diventato `Trip`, `Journey` e `Itinerary`.

  

- **Punto d'interesse** è diventato `Location`, `POI` e `Destination`.

  

- L'azione di **curare una collezione** è diventata `aggiungere oggetti a una lista`.

  

  

Questo è un disastro silente. Ogni volta che queste persone comunicano, devono eseguire una **traduzione mentale**.

  

  

- "Ah, quando lei dice 'Vacanza', intende un 'Journey' nel database."

  

- "Ricorda, l'endpoint `destinations` in realtà restituisce le `Location`."

  

  

Questa frizione cognitiva costante è costosa e pericolosa. Genera:

  

  

- **Bug**: La logica implementata nel `TripManager` potrebbe non rispecchiare le sottili regole di business che la Product Manager intendeva con il verbo "curare".

  

- **Rallentamenti**: Ogni conversazione richiede tempo per la traduzione e la chiarificazione. Il nuovo sviluppatore che si unisce al team dovrà imparare questo "dizionario" non scritto, aumentando il suo tempo di onboarding.

  

- **Modello Anemico**: Il codice non riflette il dominio. Diventa un'implementazione tecnica di un problema frainteso, invece di essere un modello vivo del business.

  

  

L'Ubiquitous Language è l'antidoto a questa Torre di Babele.

  

  

---

  

  

### 7.2. Cos'è (e Cosa Non È) il Linguaggio Ubiquo

  

  

> **Definizione:** L'Ubiquitous Language è un linguaggio condiviso, sviluppato in modo collaborativo da sviluppatori, esperti di dominio, e tutte le altre figure coinvolte, per descrivere il dominio del software. Questo linguaggio deve essere usato in modo **rigoroso** in **tutte le forme di comunicazione** del progetto, senza eccezioni: discussioni verbali, diagrammi, documentazione e, soprattutto, nel codice sorgente.

  

  

Analizziamo le caratteristiche chiave:

  

  

- **Condiviso e Collaborativo**: Non è un glossario scritto dagli "uomini di business" e consegnato ai tecnici. Nasce dal dialogo. Gli sviluppatori portano il rigore tecnico, gli esperti portano la conoscenza del dominio. Insieme, negoziano termini precisi.

  

- **Preciso e Ambiguo**: Termini generici come "oggetto", "dato", "manager" sono banditi. Se il business parla di "Utente Premium" e "Utente Standard", non esisterà una singola classe `User` con un flag `is_premium`. Esisteranno probabilmente due tipi distinti o un modello che esprime chiaramente questa differenza.

  

- **Ubiquo (Onnipresente)**: Deve permeare ogni artefatto del progetto. Se si disegna un diagramma alla lavagna usando il termine "**Proposta di Itinerario**", allora nel codice Go deve esistere una `struct` o un'interfaccia chiamata `PropostaDiItinerario`. Non `SuggestedTrip` o `AIPlan`.

  

- **Focalizzato sul Dominio**: Il linguaggio descrive il _problema_ (il dominio), non la _soluzione_ (la tecnologia). Non contiene termini come "tabella del database", "endpoint JSON", "messaggio della coda".

  

  

**Cosa NON è l'Ubiquitous Language:**

  

  

- Non è gergo di business imposto ai programmatori.

  

- Non è gergo tecnico imposto al business.

  

- Non è un documento statico da scrivere una volta e archiviare. È un **modello di linguaggio vivo** che si evolve man mano che la comprensione del team matura.

  

  

---

  

  

### 7.3. Dal Dialogo al Codice Go: L'UL in Azione

  

  

Questa è la parte più importante per noi sviluppatori. Come si traduce questa filosofia in codice Go? Vediamo di costruire un pezzo del nostro linguaggio per "Where Should I Be?" e di modellarlo direttamente.

  

  

Dopo alcune sessioni di dialogo con la nostra Product Manager, emergono i seguenti concetti:

  

  

- Un **`Luogo`** (Place) è una località geografica con un nome e una categoria (es. "Colosseo", "Museo"). È un concetto riutilizzabile e indipendente.

  

- Un **`Viaggio`** (Trip) è l'effettivo piano di un utente. Ha una destinazione principale, date di inizio e fine. Un `Viaggio` deve sempre essere in uno stato consistente.

  

- Un `Viaggio` è composto da **`Tappe`** (Stops). Una `Tappa` è la visita a un `Luogo` specifico in un determinato giorno del `Viaggio`. Non può esistere una `Tappa` senza un `Viaggio`.

  

- L'AI non genera direttamente un `Viaggio`. Genera una **`Proposta di Itinerario`** (Itinerary Proposal). Questa è una bozza, un suggerimento che l'utente può rivedere.

  

- L'utente deve compiere un'azione esplicita per **`Convertire`** una `Proposta di Itinerario` in un `Viaggio` concreto, che a quel punto diventa suo e può essere modificato.

  

  

Ora, tradiamo questo linguaggio in codice Go.

  

  

Go

  

  

``` go

  

//

  

// CONTROESEMPIO: Un codice che IGNORA il linguaggio

  

//

  

  

//

  

// Questo codice è sbagliato perché usa termini generici e tecnici.

  

//

  

  

// models/generic.go

  

package models

  

  

// 'Item' non significa nulla nel nostro dominio.

  

type Item struct {

  

    ID   string

  

    Name string

  

    Data map[string]interface{} // Un sacco generico di dati

  

}

  

  

// services/manager.go

  

package services

  

  

// 'Manager' è un termine vago. Cosa gestisce?

  

type Manager struct { /* ... dipendenze ... */ }

  

  

// Il nome della funzione non riflette l'azione del dominio.

  

// Prende un 'sourceID' e crea un nuovo 'Item'. Non è chiaro cosa stia succedendo.

  

func (m *Manager) ProcessData(sourceID string) (*Item, error) {

  

    // ... logica confusa ...

  

    return nil, nil

  

}

  

```

  

  

---

  

  

Go

  

  

``` go

  

//

  

// ESEMPIO CORRETTO: Un codice che PARLA il linguaggio

  

//

  

  

//

  

// Questo codice è corretto perché ogni nome riflette un concetto del dominio.

  

//

  

  

// planning/place.go - Il concetto di Luogo

  

package planning

  

  

type PlaceID string

  

  

type Place struct {

  

    ID       PlaceID

  

    Name     string

  

    Category string

  

}

  

  

// planning/trip.go - Il Viaggio e la Tappa

  

package planning

  

  

import "time"

  

  

type TripID string

  

  

// Notare come Tappa sia definita all'interno del contesto di un Viaggio.

  

type Stop struct {

  

    Place     Place

  

    DayOfTrip int

  

}

  

  

type Trip struct {

  

    id          TripID

  

    destination string

  

    startDate   time.Time

  

    endDate     time.Time

  

    stops       []Stop

  

}

  

  

// Il metodo riflette l'azione "Aggiungere una Tappa".

  

// La firma del metodo stesso è parte del Linguaggio Ubiquo.

  

func (t *Trip) AddStop(place Place, day int) error {

  

    // ... logica per validare che il giorno sia nel range del viaggio ...

  

    newStop := Stop{Place: place, DayOfTrip: day}

  

    t.stops = append(t.stops, newStop)

  

    return nil

  

}

  

  

// suggestions/proposal.go - La Proposta di Itinerario

  

package suggestions

  

  

// È un tipo distinto perché è un concetto distinto.

  

type ItineraryProposal struct {

  

    ID          string

  

    SuggestedStops []struct{

  

        PlaceName string

  

        Day       int

  

    }

  

}

  

  

// planning/conversion_service.go - Il servizio di dominio per la conversione

  

package planning

  

  

import "where-should-i-be/suggestions"

  

  

// Il nome del servizio è un verbo del nostro linguaggio.

  

// Questo non è un "manager", ha uno scopo specifico e di business.

  

type ProposalConverter struct {

  

    // ... dipendenze, come un repository per trovare i Luoghi (Place) ...

  

}

  

  

// Il nome del metodo è esplicito e non ambiguo.

  

func (c *ProposalConverter) ConvertToTrip(proposal suggestions.ItineraryProposal) (*Trip, error) {

  

    // 1. Crea un nuovo Trip vuoto.

  

    // 2. Per ogni "suggested stop" nella proposta...

  

    // 3. ...cerca il `Place` corrispondente nel nostro sistema.

  

    // 4. ...chiama il metodo `trip.AddStop()`.

  

    // 5. Restituisce il nuovo Trip.

  

    // ...

  

    return nil, nil

  

}

  

```

  

  

La differenza è radicale. Il secondo esempio è **auto-documentante**. Un nuovo sviluppatore può leggere la struttura dei file e i nomi dei tipi e dei metodi per iniziare a capire le regole del business senza dover leggere una singola riga di documentazione esterna. Il codice _è_ il design.

  

  

---

  

  

### 7.4. Tecniche per Scoprire e Coltivare il Linguaggio

  

  

Il Linguaggio Ubiquo non appare per magia. Deve essere attivamente scoperto, negoziato e coltivato. Ecco alcune tecniche pratiche per farlo.

  

  

#### **Event Storming**

  

  

È la tecnica più potente per la scoperta del dominio. L'Event Storming è un workshop collaborativo e flessibile dove sviluppatori ed esperti di dominio esplorano un processo di business complesso. Si usa una grande parete (o una lavagna virtuale) e post-it di colori diversi per mappare i **Domain Events** (eventi di dominio, es. "Viaggio Pianificato", "Tappa Aggiunta").

  

  

> **Approfondimento:** L'Event Storming è stato inventato da Alberto Brandolini. Il suo libro, ["Introducing EventStorming"](https://www.eventstorming.com/book/), è la risorsa definitiva. Preannunciamo che dedicheremo l'intero Capitolo 17 a questa tecnica.

  

  

Il risultato di una sessione di Event Storming non è solo una migliore comprensione del flusso di business, ma anche un vocabolario condiviso di eventi, comandi e attori, che è il seme del nostro Linguaggio Ubiquo.

  

  

#### **Creare un Glossario Condiviso**

  

  

Mantenere un glossario centrale è una buona pratica.

  

  

- **Dove?** In un posto facile da trovare e modificare per tutti. Una pagina Confluence/Notion o, ancora meglio, un file `GLOSSARY.md` direttamente nella root del repository del codice.

  

- **Cosa contiene?** Non solo il termine e la sua definizione, ma anche:

  

    - **Esempi**: "Un _Viaggio_ è 'Weekend a Roma', non 'Volo FR123'".

  

    - **Controesempi / Ambiguità**: "Una _Proposta di Itinerario_ NON è un _Viaggio_. Diventa un Viaggio solo dopo la _Conversione_".

  

    - **Termini Correlati**: Link ad altri termini del glossario.

  

  

Questo glossario non è il linguaggio stesso, ma un suo utile riflesso, un punto di riferimento.

  

  

#### **Il Linguaggio nelle User Stories**

  

  

Scrivete le user stories e i requisiti usando il linguaggio rigoroso.

  

  

- **Male**: "Come utente, voglio aggiungere un posto al mio piano."

  

- **Bene**: "Come _Utente Registrato_, voglio poter **Aggiungere una Tappa** a un _Viaggio_ esistente selezionando un _Luogo_."

  

  

Questo costringe tutti, a partire dai Product Manager, a usare i termini corretti fin dall'inizio del processo.

  

  

#### **Il Linguaggio nelle Code Review**

  

  

Le code review sono un'opportunità fantastica per rafforzare il linguaggio.

  

  

- "Questa variabile `x` non è chiara. Intendevi `tappa` o `luogo`?"

  

- "Il metodo `updateTrip` è troppo generico. L'azione di business qui è `ChangeTripDates` (Cambiare Date Viaggio), quindi il metodo dovrebbe chiamarsi così."

  

  

---

  

  

### 7.5. Un Linguaggio per Ogni Contesto

  

  

Un punto cruciale, che collega la progettazione tattica (come questa) a quella strategica, è che **l'Ubiquitous Language è valido solo all'interno di un Bounded Context (Contesto Delimitato)**.

  

  

Come abbiamo accennato nel Capitolo 6, un Bounded Context è un confine all'interno del quale un modello di dominio è consistente. Questo significa che lo stesso concetto del mondo reale può essere rappresentato da modelli e termini diversi in contesti diversi.

  

  

Consideriamo il concetto di "Viaggio" nella nostra applicazione:

  

  

1. **Nel `PlanningContext` (Contesto di Pianificazione)**:

  

    - Il termine chiave è **`Viaggio`**.

  

    - Il modello è ricco: ha un ID, date, una lista di `Tappe`, regole di validazione complesse (un viaggio non può avere tappe sovrapposte, ecc.). Il suo scopo è la **pianificazione logistica**.

  

2. **Nel `BillingContext` (Contesto di Fatturazione)**:

  

    - Potremmo non avere affatto il concetto di `Viaggio`. Potremmo avere il concetto di **`Prodotto Acquistato`**.

  

    - Il modello `ProdottoAcquistato` potrebbe avere un `trip_id` come riferimento, ma i suoi attributi principali sarebbero `Prezzo`, `DataAcquisto`, `StatoPagamento`. La sua logica riguarderebbe rimborsi e fatture, non l'aggiunta di tappe.

  

3. **Nel `SocialContext` (Contesto Social)**:

  

    - Qui, l'utente non "pianifica" più, ma "condivide". Il termine chiave potrebbe essere **`Diario di Viaggio`**.

  

    - Il modello si concentrerebbe su `Foto`, `Racconti`, `Valutazioni`. La logica riguarderebbe la privacy (chi può vederlo) e i commenti.

  

  

Tentare di creare un'unica, mostruosa classe `Trip` che serva tutti e tre i contesti sarebbe un disastro. Ogni contesto ha il suo **proprio Linguaggio Ubiquo**, ottimizzato per risolvere uno specifico problema di business. L'integrazione tra contesti avviene tramite traduzione esplicita ai confini (come vedremo nel Capitolo 18, "Context Mapping").

  

  

---

  

  

### 7.6. Conclusioni e Prossimi Passi

  

  

L'Ubiquitous Language non è un lusso, ma una necessità per il successo di progetti software complessi. È l'investimento che facciamo per garantire che ciò che costruiamo sia esattamente ciò che il business necessita.

  

  

- **Abbassa la frizione**: Elimina la necessità di traduzione mentale tra business e tecnologia.

  

- **Rende il codice espressivo**: Il codice diventa una narrazione chiara del dominio.

  

- **Guida il design**: La scoperta del linguaggio guida la scoperta dei modelli (Entità, Value Objects, Aggregati).

  

- **È il cuore della collaborazione**: Trasforma lo sviluppo software da un'attività di "raccolta requisiti" a un processo di problem-solving condiviso.

  

  

Nei prossimi capitoli, vedremo come usare questo linguaggio per definire i mattoncini fondamentali del nostro modello di dominio: Aggregati, Entità e Value Objects. Il Linguaggio Ubiquo sarà la nostra guida costante, la nostra stella polare nella progettazione tattica.

  

  

---

  

## Capitolo 8: Aggregates e Confini di Consistenza

  

  

Nei capitoli precedenti, abbiamo stabilito le fondamenta della nostra filosofia di progettazione. Abbiamo capito l'importanza di un modello di dominio ricco (Capitolo 6) e abbiamo imparato a costruirci attorno un Linguaggio Ubiquo (Capitolo 7) per garantire che il nostro codice parli la lingua del business. Ora, dobbiamo affrontare una delle sfide più grandi nella progettazione di software complessi: **gestire le relazioni e garantire la coerenza dei dati**.

  

  

Un modello di dominio non è una collezione di oggetti isolati. È una rete intricata di relazioni: un `Viaggio` ha delle `Tappe`, un `Utente` ha delle `Preferenze`, una `Proposta di Itinerario` è associata a dei `Luoghi`. Se ogni oggetto potesse essere modificato liberamente da qualsiasi punto del sistema, il caos regnerebbe sovrano. Come possiamo garantire che, dopo ogni operazione, il nostro sistema si trovi in uno stato valido e consistente?

  

  

La risposta del Domain-Driven Design a questa domanda è il pattern dell'**Aggregate** (Aggregato). L'aggregato è forse il più cruciale dei pattern tattici. È il guardiano della consistenza, il pilastro che ci permette di costruire modelli robusti e manutenibili. In questo capitolo, ne sveleremo ogni segreto.

  

  

---

  

  

### 8.1. Il Problema: Un Intreccio di Oggetti Ingestibile

  

  

Immaginiamo il nostro modello di dominio per "Where Should I Be?" senza il concetto di Aggregato. Avremmo una serie di oggetti collegati tra loro:

  

  

```

  

+----------+      1..*      +---------+      1..1      +--------+

  

|  Utente  |----------------| Viaggio |----------------| Budget |

  

+----------+                +----+----+                +--------+

  

                                | 1..*

  

                                v

  

                            +-------+      1..1      +-------+

  

                            | Tappa |----------------| Luogo |

  

                            +-------+                +-------+

  

```

  

  

Ora, consideriamo una semplice operazione: "l'utente vuole estendere la sua vacanza di un giorno". Questa azione scatena una cascata di potenziali problemi di consistenza:

  

  

1. **Modifica della Data**: Un programmatore scrive il codice per modificare la data di fine del `Viaggio`.

  

2. **Violazione delle Regole**: Cosa succede se una `Tappa` era pianificata proprio nel giorno che ora è stato eliminato? Quella `Tappa` è ora orfana, invalida. Il nostro modello è in uno stato inconsistente.

  

3. **Violazione del Budget**: Estendere il viaggio potrebbe invalidare il `Budget` associato. Forse il budget era calcolato su base giornaliera.

  

4. **Logica Sparsa**: Dove mettiamo il codice di validazione? Un pezzo nel servizio che modifica il `Viaggio`, un altro nel servizio che gestisce le `Tappe`? Come ci assicuriamo che tutte le regole vengano sempre applicate, in ogni punto del sistema che modifica questi oggetti?

  

  

Senza un confine chiaro, la responsabilità di mantenere la coerenza è distribuita, e quindi, di fatto, non è di nessuno. È incredibilmente facile dimenticare una regola, portando a dati corrotti e bug difficili da diagnosticare.

  

  

---

  

  

### 8.2. La Soluzione: L'Aggregate come Scudo di Consistenza

  

  

L'Aggregate pattern risolve questo problema introducendo un confine formale attorno a un gruppo di oggetti correlati.

  

  

> **Definizione**: Un **Aggregate** è un cluster di oggetti di dominio (Entità e Value Objects) che può essere trattato come una singola unità. Ogni Aggregato ha un'entità principale chiamata **Aggregate Root** (Radice dell'Aggregato), che funge da unico punto di accesso per qualsiasi modifica al suo interno.

  

  

L'Aggregate Root è il guardiano. Il suo compito è far rispettare gli **invarianti**—regole di business che devono essere sempre vere—all'interno del suo confine.

  

  

Pensiamo a un'automobile come analogia:

  

  

- **L'Automobile** è l'Aggregate Root.

  

- Il **Motore**, le **Ruote**, il **Sistema Elettrico** sono oggetti interni all'aggregato.

  

- L'**interfaccia pubblica** dell'auto (volante, pedali, cambio) sono i metodi dell'Aggregate Root.

  

- Quando premiamo l'acceleratore, non stiamo interagendo direttamente con le valvole di iniezione del carburante. Stiamo invocando un metodo sull'Aggregate "Automobile", che si assicura che il motore riceva la giusta quantità di carburante, che la trasmissione sia nella marcia corretta, ecc., mantenendo l'intero sistema in uno stato consistente e funzionante. Non possiamo bypassare l'interfaccia e manipolare direttamente i pistoni mentre l'auto è in marcia.

  

  

L'Aggregate applica lo stesso principio al nostro software. Definiamo un confine attorno a `Viaggio` e alle sue `Tappe`. Il `Viaggio` diventa l'Aggregate Root.

  

  

---

  

  

### 8.3. Le Regole d'Oro per Lavorare con gli Aggregati

  

  

Perché il pattern funzioni, dobbiamo seguire scrupolosamente alcune regole. Queste non sono suggerimenti; sono leggi fondamentali per il successo del design.

  

  

#### **Regola 1: L'Aggregate Root è l'Unico Punto d'Accesso**

  

  

Il codice esterno può avere un riferimento solo all'Aggregate Root. Non deve mai avere un riferimento diretto a un oggetto interno all'aggregato.

  

  

**Come si implementa in Go?** Tramite l'incapsulamento. I campi che contengono gli oggetti interni non vengono esportati (iniziano con lettera minuscola).

  

  

Vediamo come progettare l'aggregato `Viaggio`:

  

  

Go

  

  

``` go

  

//

  

// ESEMPIO CORRETTO: Viaggio come Aggregate Root

  

//

  

  

// planning/trip.go

  

package planning

  

  

import "time"

  

  

// ... altre definizioni come TripID, Place, etc.

  

  

type TripStatus string

  

  

const (

  

    TripStatusPlanning   TripStatus = "Planning"

  

    TripStatusInProgress TripStatus = "InProgress"

  

    TripStatusCompleted  TripStatus = "Completed"

  

)

  

  

// La struct Tappa non è esportata. Può essere usata solo all'interno

  

// del package 'planning'. Meglio ancora, è usata solo dal Viaggio.

  

type stop struct {

  

    place     Place

  

    dayOfTrip int

  

    notes     string

  

}

  

  

// Viaggio è l'Aggregate Root. È l'unico tipo esportato.

  

type Trip struct {

  

    id        TripID

  

    ownerID   UserID // Riferimento a un altro aggregato tramite ID (vedi Regola 2)

  

    status    TripStatus

  

    dateRange DateRange // Value Object

  

    // Il campo 'stops' è privato! Nessuno dall'esterno può manipolare

  

    // direttamente la slice delle tappe.

  

    stops     []stop

  

}

  

  

// L'unico modo per aggiungere una Tappa è attraverso questo metodo

  

// sull'Aggregate Root, che può far rispettare gli invarianti.

  

func (t *Trip) AddStop(place Place, day int, notes string) error {

  

    // INVARIANTE 1: Non si possono aggiungere tappe a un viaggio non in pianificazione.

  

    if t.status != TripStatusPlanning {

  

        return errors.New("cannot add stop to a trip not in planning status")

  

    }

  

    // INVARIANTE 2: La tappa deve essere all'interno delle date del viaggio.

  

    if !t.dateRange.ContainsDay(day) { // Assumendo che DateRange abbia questa logica

  

        return errors.New("stop day is outside the trip's date range")

  

    }

  

  

    // ... altre regole ...

  

  

    t.stops = append(t.stops, stop{place: place, dayOfTrip: day, notes: notes})

  

    return nil

  

}

  

  

// Se il codice esterno ha bisogno di leggere le tappe, forniamo

  

// un metodo che restituisce una COPIA (Value Object) o una versione

  

// read-only, non un puntatore alla slice interna.

  

type StopInfo struct { // Un Data Transfer Object (DTO)

  

    PlaceName string

  

    Day       int

  

    Notes     string

  

}

  

  

func (t *Trip) Stops() []StopInfo {

  

    infos := make([]StopInfo, len(t.stops))

  

    for i, s := range t.stops {

  

        infos[i] = StopInfo{

  

            PlaceName: s.place.Name,

  

            Day:       s.dayOfTrip,

  

            Notes:     s.notes,

  

        }

  

    }

  

    return infos

  

}

  

```

  

  

**Controesempio (COSA NON FARE):**

  

  

Go

  

  

``` go

  

type Trip struct {

  

    // ...

  

    // ESPORTATO! Disastro imminente.

  

    Stops []*Stop

  

}

  

  

// Codice client malvagio

  

trip := repository.FindByID(...)

  

newStop := &Stop{...}

  

// Bypass totale di tutte le regole di business!

  

trip.Stops = append(trip.Stops, newStop) 

  

repository.Save(trip) // Il nostro modello è ora corrotto.

  

```

  

  

#### **Regola 2: Riferirsi ad Altri Aggregati solo tramite ID**

  

  

Questa regola è tanto sottile quanto potente. **Un aggregato non dovrebbe contenere un riferimento diretto in memoria (un puntatore) a un altro aggregato.** Dovrebbe contenere solo l'ID dell'altro aggregato.

  

  

Nel nostro `Trip`, notate: `ownerID UserID`, non `owner *User`.

  

  

**Perché questa regola è così importante?**

  

  

1. **Mantenere i Confini Chiari**: Se `Trip` contenesse un `*User`, sarebbe facile per un programmatore scrivere `trip.owner.ChangeEmail()`, modificando un altro aggregato dall'interno di uno diverso. Questo distrugge il concetto di confine e di responsabilità.

  

2. **Prestazioni e Scalabilità**: Caricare un aggregato dal database deve essere un'operazione rapida. Se `Trip` contenesse un `*User`, che a sua volta contiene una lista di `*Trip`, caricare un singolo viaggio potrebbe potenzialmente caricare l'intero database in memoria. Mantenendo solo gli ID, carichiamo solo ciò che ci serve.

  

3. **Abilitare la Distribuzione**: In un sistema a microservizi, l'aggregato `User` potrebbe vivere in un servizio completamente diverso (`IdentityService`) rispetto all'aggregato `Trip` (`PlannerService`). Un riferimento diretto in memoria è impossibile. Un riferimento tramite ID è l'unico modo per farli comunicare.

  

  

#### **Regola 3: Una Transazione, un Aggregato**

  

  

Il confine di un aggregato definisce il confine di una transazione. Quando eseguiamo un comando su un aggregato, tutte le modifiche a tutti gli oggetti al suo interno devono essere salvate atomicamente (tutto o niente).

  

  

Questo implica che **una singola transazione di business non dovrebbe modificare più di un aggregato**.

  

  

"Ma come faccio a mantenere la coerenza tra aggregati diversi?", potreste chiedere. La risposta è la **consistenza eventuale (eventual consistency)**.

  

  

Se, quando un `Trip` viene creato, dobbiamo aggiornare un contatore nel `User` (es. `numberOfTrips`), non lo facciamo nella stessa transazione. Invece:

  

  

1. Salviamo il nuovo aggregato `Trip`. Questa è la prima transazione, atomica e consistente.

  

2. L'aggregato `Trip`, dopo essere stato salvato, pubblica un **Domain Event** (evento di dominio), come `TripCreated`.

  

3. Un altro pezzo del sistema (un altro servizio o un gestore di eventi) ascolta questo evento e, in una **seconda e separata transazione**, carica l'aggregato `User` e aggiorna il suo contatore.

  

  

Per un breve istante, il `Trip` esiste ma il contatore non è ancora aggiornato. Questo va benissimo per la maggior parte dei casi di business. Il sistema è _eventualmente_ consistente. Questo approccio è la chiave per costruire sistemi scalabili e disaccoppiati.

  

  

---

  

  

### 8.4. Progettare Aggregati Efficaci: L'Arte della Dimensione Giusta

  

  

La domanda più difficile nel design degli aggregati è: "Quanto deve essere grande?". Non c'è una risposta unica, ma ci sono delle euristiche fondamentali.

  

  

> **Approfondimento**: Vaughn Vernon, nel suo libro "Implementing Domain-Driven Design", discute ampiamente queste regole. La sua raccomandazione è chiara: **modellare aggregati piccoli**.

  

  

**Euristiche di Design:**

  

  

1. **Partire dal Piccolo**: La regola predefinita dovrebbe essere: un aggregato contiene solo l'Aggregate Root e, al massimo, qualche Value Object. Includere altre entità solo se strettamente necessario.

  

2. **La Domanda Chiave sulla Consistenza**: Per decidere se un oggetto deve stare dentro o fuori un aggregato, ponetevi questa domanda: "Se modifico l'Aggregate Root, questo oggetto deve essere modificato nella **stessa identica transazione** per mantenere il sistema valido?".

  

    - Se la risposta è **sì**, allora deve stare dentro. _Esempio: quando modifico le date di un `Viaggio`, le `Tappe` devono essere validate immediatamente. `Tappa` sta dentro `Viaggio`._

  

    - Se la risposta è **no**, può essere gestito con consistenza eventuale. _Esempio: quando un `Utente` cambia il suo nome, non è necessario aggiornare istantaneamente il nome dell'autore in tutti i suoi `Viaggi` passati. `Utente` e `Viaggio` sono aggregati separati._

  

3. **Considerare i Casi d'Uso**: Il design degli aggregati è guidato dal comportamento, non solo dai dati. Analizzate i comandi che il vostro sistema deve eseguire. Se molti comandi richiedono di modificare `A` e `B` insieme, potrebbero appartenere allo stesso aggregato. Ma se `B` può cambiare spesso e indipendentemente da `A`, è un forte indicatore che dovrebbero essere separati.

  

  

**L'Aggregato `Viaggio` nella nostra App**

  

  

Applichiamo queste regole a "Where Should I Be?":

  

  

- **Aggregate Root**: `Trip`

  

- **Entità Interne**: `stop` (nota la `s` minuscola)

  

- **Value Objects Interni**: `DateRange`, `Money` (per il budget)

  

- **Riferimenti Esterni (ID)**: `ownerID` (che punta all'aggregato `User`), `originalProposalID` (che punta a un eventuale aggregato `ItineraryProposal`).

  

  

Questo design garantisce che ogni `Trip` sia un'isola di consistenza, facilmente gestibile, persistibile e scalabile.

  

  

---

  

  

### 8.5. Il Ciclo di Vita: Factory e Repository

  

  

Ora che abbiamo i nostri aggregati, come li creiamo e li salviamo? Qui entrano in gioco altri due pattern tattici.

  

  

- **Factory (Fabbrica)**: Se la creazione di un aggregato è complessa (richiede la validazione di molti parametri per creare uno stato iniziale valido), possiamo usare una Factory. Una Factory è un oggetto o una funzione il cui unico scopo è creare altri oggetti. Il nostro `NewTrip(...)` del Capitolo 6 è un semplice esempio di _Factory Method_.

  

- **Repository (Deposito)**: Questo pattern (che esploreremo a fondo nel Capitolo 13) si occupa della persistenza degli aggregati. Dal punto di vista del dominio, un Repository è come una "collezione in memoria" di aggregati. Avremo un `TripRepository`, ma **non** avremo un `StopRepository`. Perché? Perché la **Regola 1** ci impone di accedere alle `Tappe` solo attraverso l'aggregato `Viaggio`. Il Repository carica e salva l'aggregato come un'unica unità.

  

  

Go

  

  

```go

  

// Interfaccia di un potenziale Repository

  

type TripRepository interface {

  

    Save(ctx context.Context, trip *Trip) error

  

    FindByID(ctx context.Context, id TripID) (*Trip, error)

  

}

  

```

  

  

---

  

  

### 8.6. Conclusioni: Ordine dal Caos

  

  

Gli aggregati sono il cuore pulsante del modello tattico di DDD. Sono lo strumento principale con cui trasformiamo un groviglio di oggetti interconnessi in un sistema ordinato, robusto e comprensibile.

  

  

- **Definiscono confini transazionali chiari**.

  

- **Proteggono l'integrità del modello** facendo rispettare gli invarianti.

  

- **Semplificano il design** limitando le relazioni tra oggetti.

  

- **Abilitano la scalabilità** promuovendo la consistenza eventuale tra di essi.

  

  

Padroneggiare l'arte di progettare aggregati efficaci è una delle competenze più preziose per un architetto software. Richiede pratica, un dialogo costante con gli esperti di dominio e la disciplina di seguire le regole d'oro che abbiamo delineato.

  

  

Nel prossimo capitolo, faremo un passo indietro e analizzeremo più in dettaglio i due tipi di oggetti che compongono i nostri aggregati: i **Value Objects** e le **Entities**.

  

  

---

  

## Capitolo 9: Value Objects e Immutabilità

  

  

Nei capitoli precedenti abbiamo esplorato il design di alto livello del nostro modello di dominio, definendo il Linguaggio Ubiquo e i confini di consistenza degli Aggregati. Ora è il momento di zoomare ancora di più, fino ad arrivare ai mattoncini fondamentali con cui questi aggregati sono costruiti: gli oggetti stessi.

  

  

Nel Domain-Driven Design, gli oggetti del nostro modello si dividono in due categorie principali: le **Entità** (Entities) e gli **Oggetti Valore** (Value Objects). Mentre le entità hanno un'identità che persiste nel tempo, i Value Objects descrivono e misurano aspetti del dominio. Sono onnipresenti, eppure spesso vengono trascurati, portando a un design fragile e poco espressivo.

  

  

In questo capitolo, ci dedicheremo interamente ai Value Objects. Scopriremo perché sono molto più di semplici contenitori di dati e come il loro superpotere—l'**immutabilità**—possa drasticamente migliorare la robustezza, la sicurezza e la chiarezza del nostro codice Go.

  

  

---

  

  

### 9.1. La Malattia Silenziosa: L'Ossessione per i Primitivi

  

  

Apriamo il cofano di un'applicazione software tipica e, molto spesso, troveremo una malattia di progettazione tanto comune quanto dannosa: la **Primitive Obsession** (Ossessione per i Tipi Primitivi). Questa si manifesta quando usiamo tipi di base del linguaggio (stringhe, interi, float) per rappresentare concetti di dominio che hanno un significato e delle regole proprie.

  

  

Consideriamo una prima, ingenua implementazione del nostro aggregato `Viaggio` (Trip):

  

  

Go

  

  

```go

  

//

  

// CONTROESEMPIO: Un modello afflitto da Primitive Obsession

  

//

  

package naive

  

  

import "time"

  

  

type Trip struct {

  

    ID                 string

  

    Destination        string

  

    // Problema 1: Date non correlate

  

    StartDate          time.Time

  

    EndDate            time.Time

  

  

    // Problema 2: Denaro come due primitive separate

  

    BudgetAmount       float64

  

    BudgetCurrency     string // "EUR"? "euro"? "E"? Cosa è valido?

  

  

    // Problema 3: Email come semplice stringa

  

    OwnerContactEmail  string

  

}

  

```

  

  

Questo codice sembra innocuo, ma nasconde una miriade di problemi:

  

  

1. **Mancanza di Significato e Unità**: `BudgetAmount` e `BudgetCurrency` sono concetti inseparabili. Un importo senza una valuta non ha senso. Rappresentandoli come due campi distinti, creiamo la possibilità che vengano gestiti separatamente, portando a errori. Lo stesso vale per `StartDate` e `EndDate`, che insieme definiscono un "intervallo di date".

  

2. **Assenza di Validazione**: Cosa impedisce a un programmatore di inserire `"banana"` nel campo `BudgetCurrency`? O un `EndDate` precedente a `StartDate`? O una stringa senza `@` in `OwnerContactEmail`? Nulla. La validazione, se esiste, sarà sparsa in giro per la codebase, invece di essere legata al dato stesso.

  

3. **Logica Dispersa**: Se volessimo confrontare due budget, dovremmo scrivere una funzione esterna che prende quattro parametri (`amount1`, `currency1`, `amount2`, `currency2`), controlla che le valute siano uguali e poi confronta gli importi. Questa logica non appartiene a un servizio generico, ma al concetto stesso di "denaro".

  

  

I **Value Objects** sono la cura per questa malattia. Ci permettono di raggruppare questi attributi in un concetto coeso, dotato di significato, regole e comportamento.

  

  

---

  

  

### 9.2. Cos'è un Value Object?

  

  

> **Definizione**: Un **Value Object** è un oggetto che rappresenta un aspetto descrittivo del dominio. È definito completamente dai valori dei suoi attributi e non possiede un'identità concettuale propria.

  

  

Analizziamo le sue caratteristiche fondamentali:

  

  

- **Descrive, Misura o Quantifica**: Un Value Object non è "la cosa", ma una _descrizione della cosa_. L'indirizzo di una persona non è la persona. Il colore di un'auto non è l'auto. L'importo di una transazione non è la transazione.

  

- **Uguaglianza Strutturale**: Due Value Objects sono considerati uguali se tutti i loro attributi sono identici. Una banconota da 10€ è perfettamente interscambiabile con un'altra banconota da 10€. Non ci interessa il loro numero di serie (la loro identità), ma solo il loro valore. Questo è in netto contrasto con le Entità, dove due oggetti con gli stessi attributi ma ID diversi sono considerati distinti.

  

- **Auto-Validante**: Un Value Object non dovrebbe mai esistere in uno stato non valido. La sua funzione di costruzione (la sua "factory") è responsabile di far rispettare tutti gli invarianti. Se i dati non sono validi, la creazione fallisce.

  

- **Immutabile**: Questa è la caratteristica più importante e potente. Una volta creato, un Value Object non può più essere modificato. Se si desidera un valore diverso, si deve creare una _nuova istanza_ dell'oggetto.

  

  

---

  

  

### 9.3. Immutabilità: Il Superpotere dei Value Objects 

  

  

L'immutabilità non è solo una buona pratica, è un cambiamento di paradigma che porta benefici enormi. Un oggetto immutabile è un oggetto il cui stato interno non può essere alterato dopo la sua creazione.

  

  

**Perché l'immutabilità è così potente?**

  

  

1. **Sicurezza nei Sistemi Concorrenti**: In Go, la concorrenza è una funzionalità di prima classe. Quando più goroutine accedono a dati condivisi e modificabili, abbiamo bisogno di meccanismi di sincronizzazione complessi (come i mutex) per evitare le _data race_. Gli oggetti immutabili, per loro natura, sono **intrinsecamente thread-safe**. Possiamo passarli liberamente tra le goroutine con la certezza assoluta che nessuno li modificherà, eliminando un'intera classe di bug.

  

2. **Prevedibilità e Riduzione del Carico Cognitivo**: Quando riceviamo un oggetto mutabile come parametro di una funzione, non possiamo essere sicuri del suo stato. Qualche altro pezzo del sistema potrebbe averlo modificato. Con un oggetto immutabile, questo problema scompare. Il suo valore è fisso e prevedibile per tutto il suo ciclo di vita. Il nostro ragionamento diventa più semplice e locale.

  

3. **Comportamento Matematico**: Le operazioni sui tipi primitivi come i numeri sono intrinsecamente immutabili. Quando calcoliamo `5 + 3`, non modifichiamo il numero `5`. L'operazione produce un nuovo numero, `8`. I Value Objects dovrebbero comportarsi allo stesso modo. Un'operazione come `budgetIniziale.Aggiungi(spesa)` non modifica `budgetIniziale`, ma restituisce un `nuovoBudget`. Questo rende il codice più robusto e facile da testare.

  

  

Come si ottiene l'immutabilità in Go?

  

  

Poiché Go non ha un costrutto const a livello di struct come altri linguaggi, l'immutabilità si ottiene per convenzione e disciplina:

  

  

- **Campi non esportati**: Tutti i campi della struct devono avere un nome che inizia con lettera minuscola per impedire la modifica diretta dall'esterno del package.

  

- **Nessun "Setter"**: Non fornire alcun metodo che modifichi lo stato interno dell'oggetto (es. `SetAmount(...)`).

  

- **Le Operazioni Restituiscono Nuove Istanze**: Ogni metodo che esegue una logica di trasformazione deve restituire una nuova istanza del Value Object con il nuovo stato.

  

  

---

  

  

### 9.4. Progettare Value Objects in Go: Esempi Pratici

  

  

Rifattorizziamo il nostro modello `Trip` usando Value Objects ben progettati.

  

  

#### **Esempio 1: Il Value Object `Money`** 💰

  

  

Basta con `float64` per il denaro! I float binari sono notoriamente imprecisi per i calcoli finanziari a causa di errori di arrotondamento. Useremo una libreria `decimal` e creeremo un VO `Money`.

  

  

> **Riferimento Chiave**: Una libreria eccellente e ampiamente utilizzata per i decimali in Go è `github.com/shopspring/decimal`. È considerata lo standard de facto.

  

  

Go

  

  

``` go

  

//

  

// ESEMPIO CORRETTO: Il Value Object Money

  

//

  

package domain

  

  

import (

  

    "errors"

  

    "github.com/shopspring/decimal"

  

)

  

  

// Money è un Value Object immutabile e auto-validante.

  

type Money struct {

  

    // Campi non esportati per garantire l'immutabilità.

  

    amount   decimal.Decimal

  

    currency string

  

}

  

  

// NewMoney agisce da Factory e da guardiano degli invarianti.

  

func NewMoney(amount decimal.Decimal, currency string) (Money, error) {

  

    if currency == "" { // Esempio di validazione

  

        return Money{}, errors.New("currency cannot be empty")

  

    }

  

    // In un'app reale, qui si controllerebbe se la valuta è un codice ISO 4217 valido.

  

    return Money{amount: amount, currency: currency}, nil

  

}

  

  

// Metodi per l'accesso in sola lettura.

  

func (m Money) Amount() decimal.Decimal {

  

    return m.amount

  

}

  

  

func (m Money) Currency() string {

  

    return m.currency

  

}

  

  

// Add è un'operazione che restituisce una NUOVA istanza di Money.

  

// L'oggetto originale 'm' non viene mai modificato.

  

func (m Money) Add(other Money) (Money, error) {

  

    if m.currency != other.currency {

  

        return Money{}, errors.New("cannot add money with different currencies")

  

    }

  

    newAmount := m.amount.Add(other.amount)

  

    return Money{amount: newAmount, currency: m.currency}, nil

  

}

  

  

// Equals implementa l'uguaglianza strutturale.

  

func (m Money) Equals(other Money) bool {

  

    return m.amount.Equals(other.amount) && m.currency == other.currency

  

}

  

```

  

  

#### **Esempio 2: Il Value Object `DateRange`** 🗓️

  

  

Un intervallo di date è un concetto singolo, non due date separate.

  

  

Go

  

  

```go

  

package domain

  

  

import (

  

    "errors"

  

    "time"

  

)

  

  

type DateRange struct {

  

    start time.Time

  

    end   time.Time

  

}

  

  

func NewDateRange(start, end time.Time) (DateRange, error) {

  

    if start.After(end) {

  

        return DateRange{}, errors.New("start date cannot be after end date")

  

    }

  

    return DateRange{start: start, end: end}, nil

  

}

  

  

// La logica di business è ora co-locata con i dati.

  

func (dr DateRange) Contains(t time.Time) bool {

  

    return (t.Equal(dr.start) || t.After(dr.start)) && (t.Equal(dr.end) || t.Before(dr.end))

  

}

  

  

func (dr DateRange) DurationInDays() int {

  

    return int(dr.end.Sub(dr.start).Hours() / 24)

  

}

  

  

func (dr DateRange) Equals(other DateRange) bool {

  

    return dr.start.Equal(other.start) && dr.end.Equal(other.end)

  

}

  

```

  

  

Con questi VO, il nostro aggregato `Trip` diventa molto più pulito, robusto ed espressivo:

  

  

Go

  

  

```go

  

// Trip rifattorizzato con Value Objects

  

type Trip struct {

  

    id          TripID

  

    destination string

  

    dateRange   DateRange // Molto meglio di due time.Time!

  

    budget      Money     // Coeso e sicuro!

  

    // ...

  

}

  

```

  

  

---

  

  

### 9.5. Persistenza dei Value Objects

  

  

I database relazionali non hanno un tipo di colonna `Money` o `DateRange`. Come li salviamo?

  

  

La risposta è la **scomposizione**. Il Value Object esiste nel nostro modello di dominio, ma quando dobbiamo persisterlo, lo "appiattiamo" nelle sue parti primitive. Il **Repository** (che vedremo nel Capitolo 13) è responsabile di questa traduzione.

  

  

- **Salvataggio**: Quando il `TripRepository` salva un `Trip`, prenderà il VO `budget` e scriverà i suoi valori in due colonne della tabella `trips`: `budget_amount` (di tipo `NUMERIC`) e `budget_currency` (di tipo `VARCHAR`).

  

- **Caricamento**: Quando il repository legge una riga dalla tabella `trips`, prenderà i valori dalle colonne `budget_amount` e `budget_currency` e userà la factory `NewMoney` per ricostruire il Value Object `Money` prima di idratare l'aggregato `Trip`.

  

  

Questo meccanismo mantiene il nostro modello di dominio puro e completamente agnostico rispetto allo schema di persistenza.

  

  

---

  

  

### 9.6. Value Object vs. Entity: Un Confronto Chiave

  

  

È fondamentale non confondere i Value Objects con le Entità, che esploreremo nel prossimo capitolo. La differenza principale risiede nel concetto di **identità**.

  

  

|Caratteristica|Value Object|Entity (Entità)|

  

|---|---|---|

  

|**Identità**|**Non ha identità**. È definito dai suoi attributi.|**Ha un'identità unica** (ID) che non cambia mai.|

  

|**Uguaglianza**|Uguaglianza strutturale (valori uguali).|Uguaglianza per identità (ID uguali).|

  

|**Ciclo di Vita**|Effimero. Creato quando serve, poi scartato.|Ha una storia. Viene creato, modificato e cancellato.|

  

|**Immutabilità**|**Fortemente raccomandata**.|**Intrinsecamente mutabile** (i suoi attributi cambiano nel tempo).|

  

|**Esempio**|`Money`, `DateRange`, `Indirizzo`|`Utente`, `Viaggio`, `Ordine`|

  

  

**Analogia finale**: Pensa a una **mappa della città** (un Value Object). Se hai due stampe identiche della stessa mappa, sono interscambiabili. Se versi del caffè su una, la butti via e ne usi un'altra. Non "ripari" la mappa. Ora pensa a **te stesso** (un'Entità). Sei unico. Se cambi indirizzo (un attributo), non vieni sostituito con una "nuova persona". La tua identità rimane la stessa, ma il tuo stato cambia.

  

  

---

  

  

### 9.7. Conclusioni e Prossimi Passi

  

  

Abbiamo scoperto che i Value Objects non sono semplici contenitori di dati. Sono un pattern di design fondamentale che porta un'enorme chiarezza e robustezza al nostro modello di dominio.

  

  

- **Combattono la Primitive Obsession** dando un nome e un comportamento ai concetti del dominio.

  

- **Garantiscono la validità** tramite le loro factory.

  

- **Semplificano la concorrenza e il ragionamento** grazie all'immutabilità.

  

- **Rendono il codice più espressivo** e allineato al Linguaggio Ubiquo.

  

  

Adottare una disciplina rigorosa nell'uso dei Value Objects è uno dei passi più efficaci che potete compiere per migliorare la qualità del vostro codice.

  

  

Nel prossimo capitolo, esamineremo l'altra faccia della medaglia: le **Entità**, oggetti definiti non da ciò che sono, ma da _chi_ sono lungo il corso del tempo.

  

  

---

  

## Capitolo 10: Entities e Identità nel Ciclo di Vita

  

  

Nel capitolo precedente, abbiamo esplorato il mondo dei Value Objects: oggetti descrittivi, definiti dai loro attributi e resi potenti dall'immutabilità. Essi rappresentano il "cosa" del nostro dominio. Ora, è il momento di rivolgere la nostra attenzione all'altra faccia della medaglia, al "chi": le **Entità** (Entities).

  

  

Se un Value Object è come il valore "10€", un'entità è come la specifica banconota da 10€ che hai nel portafoglio, con il suo numero di serie univoco. Se un Value Object è come un indirizzo scritto su un pezzo di carta, un'entità è come la persona che vive a quell'indirizzo.

  

  

Le entità sono gli attori principali del nostro dominio. Hanno una storia, un ciclo di vita, e soprattutto, un'**identità** che persiste nonostante i cambiamenti. Comprendere come modellare e gestire questa identità è fondamentale per costruire un dominio che rifletta fedelmente la realtà e che sia in grado di evolvere nel tempo.

  

  

---

  

  

### 10.1. Cos'è un'Entità?

  

  

> **Definizione**: Un'**Entità** è un oggetto del dominio che non è definito dai suoi attributi, ma da un filo di continuità e da un'identità unica. Due istanze di un'entità sono considerate diverse anche se i loro attributi sono identici, a meno che non condividano la stessa identità.

  

  

Un `Utente` nella nostra applicazione "Where Should I Be?" è l'esempio perfetto di un'entità. Consideriamo due utenti:

  

  

1. Mario Rossi, email: `m.rossi@example.com`, ID: `123-abc`

  

2. Mario Rossi, email: `mario.rossi@email.it`, ID: `456-def`

  

  

Anche se condividono lo stesso nome, sono due persone distinte, due entità separate nel nostro sistema. Anni dopo, il primo utente potrebbe cambiare la sua email in `mario.r@newdomain.com`. I suoi attributi sono cambiati, ma la sua identità (`122-abc`) è rimasta la stessa. È sempre lo stesso utente, con una storia continua.

  

  

Le caratteristiche chiave di un'entità sono:

  

  

- **Identità Unica e Stabile**: Questo è il suo tratto distintivo. L'identità viene assegnata alla creazione e non cambia mai per tutto il ciclo di vita dell'entità.

  

- **Ciclo di Vita Definito**: Un'entità viene creata, il suo stato viene modificato attraverso varie operazioni di business e, alla fine, può essere archiviata o rimossa. Ha una storia.

  

- **Intrinsecamente Mutabile**: Lo scopo di un'entità è proprio quello di tracciare i cambiamenti di stato nel tempo. Un `Viaggio` passa dallo stato `Planning` a `Completed`. Un `Ordine` passa da `Pending` a `Shipped`. Questa mutabilità è una caratteristica desiderata e necessaria.

  

- **Uguaglianza basata sull'Identità**: L'unico modo per determinare se due variabili che puntano a un'entità si riferiscono allo stesso concetto di business è confrontare i loro ID. `viaggio1.ID() == viaggio2.ID()`.

  

  

---

  

  

### 10.2. Il Cuore dell'Entità: Gestire l'Identità 🆔

  

  

Poiché l'identità è così centrale, la sua generazione e rappresentazione sono decisioni di design critiche.

  

  

#### **Come Generare gli ID: La Scelta Cruciale**

  

  

Esistono diversi approcci, ma nel contesto del DDD e dei sistemi moderni, la scelta è netta.

  

  

1. ID Generati dal Database (L'Anti-Pattern 👎)

  

  

Un approccio comune, specialmente con i vecchi ORM, è quello di affidarsi al database per generare l'ID (es. colonne AUTO_INCREMENT o SERIAL).

  

  

Perché è una cattiva idea nel DDD?

  

  

- **Accoppiamento Forte**: Il nostro modello di dominio diventa dipendente dal meccanismo di persistenza. Un'entità non è "completa" e non ha una vera identità finché non viene salvata nel database.

  

- **Complessità Implementativa**: Il metodo `Save` di un repository deve avere una logica speciale per capire se sta inserendo un nuovo record (e quindi deve recuperare l'ID generato) o aggiornandone uno esistente.

  

- **Difficoltà nei Sistemi Distribuiti**: Se abbiamo più istanze del nostro servizio che scrivono su database diversi (o in scenari multi-master), gestire sequenze di interi senza conflitti diventa un incubo.

  

- **Testing più Complesso**: I test unitari del dominio non dovrebbero richiedere un database, ma se l'ID viene da lì, diventa più difficile.

  

  

2. ID Generati dall'Applicazione (La Scelta Vincente 👍)

  

  

L'approccio raccomandato è che sia l'applicazione stessa a generare l'ID, prima che l'entità venga passata al livello di persistenza. Il candidato ideale per questo compito è l'UUID (Universally Unique Identifier).

  

  

> **Riferimento Chiave**: La libreria standard de facto per la gestione di UUID in Go è `github.com/google/uuid`.

  

  

**Vantaggi dell'UUID:**

  

  

- **Disaccoppiamento Totale**: L'entità nasce già con la sua identità definitiva, assegnata nel dominio. È completa e valida prima ancora di toccare il database.

  

- **Logica di Persistenza Semplificata**: Il metodo `Save` del repository può diventare un semplice "UPSERT" (UPDATE or INSERT). Se l'ID esiste, aggiorna; altrimenti, inserisce. Non c'è bisogno di logica condizionale.

  

- **Pronto per la Distribuzione**: Gli UUID sono progettati per essere unici anche quando generati da milioni di macchine diverse contemporaneamente, senza bisogno di un'autorità centrale.

  

- **Sicurezza**: Gli ID sequenziali possono esporre informazioni (es. "so che l'ordine #1001 viene dopo il #1000") e rendere più facili attacchi di enumerazione. Gli UUID non hanno questo problema.

  

  

#### **Modellare l'Identità in Go**

  

  

Anche se un UUID è una stringa o un array di byte, non dovremmo usare tipi primitivi. Applichiamo il pattern Value Object all'identità stessa! Creiamo tipi specifici per ogni ID.

  

  

Go

  

  

```go

  

//

  

// ESEMPIO CORRETTO: ID come Tipi specifici

  

//

  

  

// identity/identity.go

  

package identity

  

  

import "github.com/google/uuid"

  

  

// UserID è un tipo distinto. Non è una semplice stringa.

  

type UserID uuid.UUID

  

  

func NewUserID() UserID {

  

    return UserID(uuid.New())

  

}

  

  

func UserIDFromString(s string) (UserID, error) {

  

    id, err := uuid.Parse(s)

  

    return UserID(id), err

  

}

  

  

func (id UserID) String() string {

  

    return uuid.UUID(id).String()

  

}

  

  

// TripID è un altro tipo distinto.

  

type TripID uuid.UUID

  

  

func NewTripID() TripID {

  

    return TripID(uuid.New())

  

}

  

  

func TripIDFromString(s string) (TripID, error) {

  

    id, err := uuid.Parse(s)

  

    return TripID(id), err

  

}

  

  

func (id TripID) String() string {

  

    return uuid.UUID(id).String()

  

}

  

```

  

  

**Perché questo sforzo extra è così importante?**

  

  

- **Type Safety**: Il compilatore Go ora ci impedirà di commettere errori come `trip.ownerID = trip.ID()`. Un `UserID` e un `TripID` sono tipi diversi e incompatibili, anche se la loro rappresentazione sottostante è la stessa. Questo elimina un'intera categoria di bug.

  

- **Esprimere il Linguaggio Ubiquo**: Il codice ora dice `TripID`, non un generico `uuid.UUID`. È più chiaro e allineato al dominio.

  

  

---

  

  

### 10.3. Progettare Entità in Go

  

  

Armati del nostro approccio all'identità, vediamo come modellare le entità chiave della nostra applicazione.

  

  

#### **L'Entità `User`**

  

  

L'utente è un'entità che non è un Aggregate Root (nel nostro design attuale, ma potrebbe diventarlo in un `IdentityContext` separato). È una classica entità che tiene traccia dei dati di un utente.

  

  

Go

  

  

``` go

  

// user/user.go

  

package user

  

  

import (

  

    "where-should-i-be/internal/domain/identity"

  

    "where-should-i-be/internal/domain/common" // Dove definiamo VO come Email

  

)

  

  

type SubscriptionLevel string // Questo potrebbe essere un VO più complesso

  

  

const (

  

    LevelFree    SubscriptionLevel = "Free"

  

    LevelPremium SubscriptionLevel = "Premium"

  

)

  

  

type User struct {

  

    id                identity.UserID

  

    email             common.Email // Un Value Object

  

    name              string

  

    subscriptionLevel SubscriptionLevel

  

    // altri attributi...

  

}

  

  

// NewUser è la nostra Factory per creare un Utente in uno stato valido.

  

func NewUser(name string, email common.Email) (*User, error) {

  

    // ... validazione ...

  

    return &User{

  

        id:                identity.NewUserID(),

  

        email:             email,

  

        name:              name,

  

        subscriptionLevel: LevelFree, // Stato iniziale di default

  

    }, nil

  

}

  

  

// Metodi che modificano lo stato (mutabilità).

  

// Questi metodi contengono la logica di business relativa alla modifica.

  

func (u *User) ChangeEmail(newEmail common.Email) {

  

    // In un'app reale, potremmo voler invalidare la vecchia sessione

  

    // o inviare un'email di notifica. La logica vive qui.

  

    u.email = newEmail

  

}

  

  

func (u *User) UpgradeToPremium() {

  

    if u.subscriptionLevel == LevelPremium {

  

        return // È già premium, non fare nulla

  

    }

  

    u.subscriptionLevel = LevelPremium

  

}

  

  

// Metodi per esporre i dati in modo controllato.

  

func (u *User) ID() identity.UserID {

  

    return u.id

  

}

  

  

func (u *User) Email() common.Email {

  

    return u.email

  

}

  

```

  

  

#### **Entità vs. Aggregate Root: Una Chiarificazione**

  

  

Nel capitolo 8, abbiamo definito `Viaggio` come il nostro Aggregate Root. Ora lo analizziamo come entità.

  

  

- **Tutti gli Aggregate Root sono Entità**: `Viaggio` ha un'identità (`TripID`) e un ciclo di vita, quindi è senza dubbio un'entità. Essere un Aggregate Root è un "ruolo" aggiuntivo che un'entità assume: quello di guardiano della consistenza per un cluster di oggetti.

  

- **Non tutte le Entità sono Aggregate Root**: Potremmo avere entità _interne_ a un aggregato. Per esempio, se una `Tappa` (Stop) dovesse avere una sua identità e un suo ciclo di vita complesso, potremmo modellarla come un'entità interna all'aggregato `Viaggio`. Nel nostro design, abbiamo scelto di mantenerla più semplice (come uno `struct` non esportato), ma in domini più complessi (es. ogni `Tappa` ha le sue recensioni e foto), potrebbe diventare un'entità a tutti gli effetti. La scelta dipende sempre dagli invarianti che dobbiamo proteggere.

  

  

---

  

  

### 10.4. Gestire il Ciclo di Vita di un'Entità

  

  

Un'entità vive un percorso che va dalla creazione alla cancellazione. Il nostro codice deve gestire ogni fase.

  

  

1. Creazione (Nascita 🌱)

  

  

Avviene tramite una Factory (come la funzione NewUser). Il suo scopo è garantire che nessuna entità venga mai creata in uno stato invalido. L'ID viene generato qui.

  

  

2. Recupero e Salvataggio (Vita Quotidiana 🏠)

  

  

Questo è il dominio dei Repository.

  

  

- `userRepo.FindByID(ctx, userID)`: Carica un'entità dalla persistenza, ricostruendola nel suo stato attuale.

  

- `userRepo.Save(ctx, user)`: Persiste lo stato attuale dell'entità. Poiché l'ID è già parte dell'entità, questo metodo non si preoccupa se si tratta di un inserimento o di un aggiornamento.

  

  

3. Modifica (Cambiamento 🎭)

  

  

Lo stato di un'entità viene modificato chiamando i suoi metodi di business (es. user.ChangeEmail(...)). Questi metodi incapsulano la logica e garantiscono che la transizione di stato sia valida. Il codice chiamante (es. un Application Service o un HTTP Handler) orchestra queste chiamate.

  

  

4. Cancellazione (Fine 🏁)

  

  

Raramente si esegue una DELETE fisica dal database (hard delete). Questo comporterebbe la perdita di dati storici importanti. L'approccio preferito è il soft delete.

  

  

- Si aggiunge un campo all'entità, come `deactivatedAt *time.Time` o `status Status`.

  

- Si definisce un metodo `Deactivate()` sull'entità che imposta questo stato.

  

- Il metodo `Delete()` del repository, invece di eseguire una `DELETE`, eseguirà un `UPDATE` per impostare lo stato di disattivazione.

  

- Tutti i metodi di recupero (`Find...`) del repository dovranno poi includere una clausola `WHERE deactivated_at IS NULL` per escludere le entità "cancellate".

  

  

Questo preserva la storia e la coerenza referenziale, un aspetto fondamentale in molti domini di business.

  

  

---

  

  

### 10.5. Conclusioni

  

  

Le Entità sono la spina dorsale del nostro modello di dominio. Rappresentano i concetti che hanno una storia e un'identità che trascende i loro attributi.

  

  

- Abbiamo stabilito che **l'identità è la caratteristica fondamentale** di un'entità e che deve essere gestita con cura.

  

- Abbiamo promosso l'uso di **ID generati dall'applicazione (UUID)** come standard per disaccoppiare il dominio dalla persistenza e abilitare la scalabilità.

  

- Abbiamo visto come **modellare gli ID come tipi specifici** per aumentare la sicurezza e l'espressività del codice.

  

- Abbiamo delineato il **ciclo di vita completo** di un'entità, dalla creazione tramite Factory alla cancellazione tramite soft delete.

  

  

Con una solida comprensione di Value Objects ed Entità, ora possediamo i mattoncini per costruire qualsiasi aggregato. Ma cosa succede quando una logica di business non sembra appartenere a nessun oggetto specifico? Nel prossimo capitolo, affronteremo questo problema introducendo l'ultimo dei building block tattici: i **Domain Services**.

  

  

---

  

## Capitolo 11: Domain Services

  

  

Finora, nel nostro percorso attraverso la progettazione tattica, abbiamo assemblato una potente cassetta degli attrezzi. Abbiamo imparato a definire un **Linguaggio Ubiquo** per comunicare efficacemente (Capitolo 7), a proteggere la consistenza con gli **Aggregati** (Capitolo 8) e a costruire questi aggregati con i mattoncini fondamentali delle **Entità** (Capitolo 10) e dei **Value Objects** (Capitolo 9).

  

  

Un principio cardine che abbiamo promosso è quello di creare **modelli di dominio ricchi**, dove la logica di business risiede all'interno degli oggetti di dominio stessi (Entità e Value Objects). Questo approccio è potente e porta a un design coeso e comprensibile. Tuttavia, a volte ci imbattiamo in un problema: cosa fare quando un'operazione di business significativa non sembra appartenere naturalmente a nessun singolo oggetto?

  

  

Forzare questa logica "senzatetto" in un'entità o in un value object a cui non appartiene ne violerebbe la coesione e ne offuscherebbe le responsabilità. Per queste situazioni, il DDD ci offre l'ultimo dei suoi building block tattici: il **Domain Service** (Servizio di Dominio).

  

  

---

  

  

### 11.1. Il Problema dell'Operazione "Senzatetto"

  

  

Consideriamo alcuni scenari nel nostro dominio "Where Should I Be?":

  

  

1. **Conversione di una Proposta**: La funzionalità principale della nostra app è prendere una `PropostaDiItinerario` generata dall'AI e trasformarla in un `Viaggio` concreto per un `Utente`. Dove dovrebbe risiedere questa logica di conversione?

  

    - Su `Viaggio`? Non proprio, perché un `Viaggio` non dovrebbe sapere come è fatto l'oggetto `PropostaDiItinerario`.

  

    - Su `PropostaDiItinerario`? No, perché una proposta è solo un suggerimento e non dovrebbe avere la responsabilità di creare un'entità complessa come un `Viaggio`.

  

    - Su `Utente`? Assolutamente no. L'utente _innesca_ l'azione, ma la sua entità non dovrebbe contenere la logica complessa di pianificazione dei viaggi.

  

2. **Trasferimento di Proprietà**: Immaginiamo una futura funzionalità che permetta a un utente di trasferire un `Viaggio` a un altro utente. Questa operazione coinvolge due aggregati `Utente` e un aggregato `Viaggio`. Mettere questa logica in una qualsiasi delle tre entità sarebbe una forzatura.

  

  

Questi sono esempi classici di operazioni che coinvolgono più oggetti di dominio, dove la responsabilità è distribuita. Qui entra in gioco il Domain Service.

  

  

---

  

  

### 11.2. Cos'è un Domain Service?

  

  

> **Definizione**: Un **Domain Service** è un tipo specifico di servizio che incapsula un processo o un'operazione di business significativa che non appartiene concettualmente a nessuna entità o value object. I Domain Services rappresentano i "verbi" del dominio.

  

  

Le sue caratteristiche distintive sono cruciali per non abusarne:

  

  

- **Rappresenta un'Azione**: Il nome di un Domain Service dovrebbe riflettere l'operazione che compie. Nomi come `ConvertitoreProposta` (Proposal Converter) o `CalcolatorePrezzi` (Pricing Calculator) sono eccellenti. Se il nome suona come un'entità (es. `GestoreViaggi`), probabilmente state sbagliando strada.

  

- **È Stateless (Senza Stato)**: Questa è la regola più importante. Un Domain Service non deve avere uno stato proprio. Riceve tutto ciò di cui ha bisogno tramite i parametri dei suoi metodi, esegue l'operazione e restituisce un risultato. Qualsiasi istanza di un Domain Service deve essere interscambiabile con qualsiasi altra. Se sentite il bisogno di memorizzare dati nel servizio tra una chiamata e l'altra, quello che vi serve è probabilmente un'entità.

  

- **Opera su Oggetti di Dominio**: Un Domain Service parla il Linguaggio Ubiquo. I suoi parametri e i suoi valori di ritorno sono oggetti del dominio (Aggregati, Entità, Value Objects), non tipi primitivi o DTO.

  

- **Contiene solo Logica di Dominio**: Non deve sapere nulla di database, transazioni, richieste HTTP, logging o qualsiasi altra infrastruttura. È un componente puro del layer di dominio.

  

  

---

  

  

### 11.3. Domain Service vs. Application Service: Una Distinzione Fondamentale ⚠️

  

  

Questo è uno dei punti che genera più confusione, ma è essenziale per una corretta architettura a strati (che vedremo nella Parte III con la Clean Architecture).

  

  

Un **Application Service** non è la stessa cosa di un **Domain Service**.

  

  

- L'**Application Service** è l'orchestratore di un caso d'uso. È il punto di ingresso per il mondo esterno (es. un controller HTTP). Il suo compito è:

  

    1. Iniziare/gestire una transazione.

  

    2. Recuperare gli aggregati necessari usando i **Repository**.

  

    3. Invocare i metodi sugli aggregati o sui **Domain Services** per eseguire il lavoro.

  

    4. Salvare gli aggregati modificati usando i **Repository**.

  

    5. Completare la transazione.

  

    6. Pubblicare eventi per altri sistemi (se necessario).

  

- Il **Domain Service** è un pezzo del puzzle _usato dall'Application Service_. Contiene solo la logica di business pura che non trova posto altrove.

  

  

|Caratteristica|**Application Service** (Il Direttore d'Orchestra 🎼)|**Domain Service** (Il Musicista Virtuoso 🎻)|

  

|---|---|---|

  

|**Scopo**|Orchestrazione di un caso d'uso completo.|Esecuzione di una specifica operazione di dominio.|

  

|**Stato**|Può essere stateful all'interno di una singola richiesta.|**Assolutamente Stateless**.|

  

|**Consapevolezza**|Conosce l'infrastruttura (DB, transazioni, sicurezza).|**Pura logica di dominio**. Ignora l'infrastruttura.|

  

|**Input/Output**|Primitivi (ID, DTO da richieste HTTP), `context.Context`.|**Oggetti di Dominio** (Aggregati, Entità, VO).|

  

|**Chiamato Da**|Mondo esterno (Controller HTTP, Handler gRPC).|**Application Services** o, a volte, altri Domain Services.|

  

  

**Flusso di Esempio:**

  

  

1. Un `HTTP Handler` riceve una richiesta `POST /trips/from-proposal` con un `proposalID` nel body.

  

2. L'handler chiama il metodo `CreateTripFromProposal(ctx, userID, proposalID)` sull'**Application Service**.

  

3. L'Application Service:

  

    a. Recupera l'Utente dal userRepository.

  

    b. Recupera la PropostaDiItinerario dal proposalRepository.

  

    c. Istanzia il nostro Domain Service ProposalConverter.

  

    d. Chiama converter.ConvertToTrip(utente, proposta).

  

    e. Riceve un nuovo aggregato Viaggio (o un errore).

  

    f. Salva il nuovo Viaggio usando il tripRepository.

  

    g. Restituisce l'ID del nuovo viaggio all'handler.

  

4. L'`HTTP Handler` risponde con `201 Created` e l'ID.

  

  

---

  

  

### 11.4. Progettare un Domain Service in Go

  

  

Applichiamo questi concetti per costruire il nostro `ProposalConverter`.

  

  

Go

  

  

```go

  

//

  

// ESEMPIO CORRETTO: Il Domain Service ProposalConverter

  

//

  

package planning

  

  

import (

  

    "errors"

  

    // Importiamo i nostri modelli di dominio da altri package

  

    "where-should-i-be/internal/domain/user"

  

    "where-should-i-be/internal/domain/suggestions"

  

)

  

  

// ProposalConverter è il nostro Domain Service.

  

// È una struct vuota perché è stateless.

  

type ProposalConverter struct {

  

    // Le dipendenze (se ci sono) dovrebbero essere altre astrazioni

  

    // del dominio, non handle di database o client HTTP.

  

}

  

  

// NewProposalConverter è la sua semplice factory.

  

func NewProposalConverter() ProposalConverter {

  

    return ProposalConverter{}

  

}

  

  

// ConvertToTrip è il cuore del servizio. Prende in input oggetti

  

// di dominio puri (User e ItineraryProposal) e restituisce un

  

// oggetto di dominio (Trip) o un errore.

  

func (pc ProposalConverter) ConvertToTrip(

  

    u user.User,

  

    p suggestions.ItineraryProposal,

  

) (*Trip, error) {

  

  

    // 1. Logica di business che coinvolge più oggetti.

  

    // Qui potremmo avere regole complesse basate sul livello di abbonamento dell'utente.

  

    if u.SubscriptionLevel() == user.LevelFree && len(p.Stops()) > 5 {

  

        return nil, errors.New("free users cannot create trips with more than 5 stops")

  

    }

  

  

    // 2. Creazione dell'aggregato tramite la sua factory.

  

    // Il Domain Service non deve conoscere i dettagli interni di NewTrip.

  

    newTrip, err := NewTrip(u.ID(), p.Name()) // NewTrip è la factory del nostro aggregato Trip

  

    if err != nil {

  

        return nil, err

  

    }

  

    // 3. Orchestrazione delle modifiche sull'aggregato.

  

    // Il Domain Service chiama i metodi pubblici dell'aggregato,

  

    // rispettandone i confini e gli invarianti.

  

    for _, suggestedStop := range p.Stops() {

  

        // La logica di validazione di una singola tappa è ancora

  

        // responsabilità del metodo AddStop() sull'aggregato Trip.

  

        err := newTrip.AddStop(suggestedStop.Place(), suggestedStop.Day(), suggestedStop.Notes())

  

        if err != nil {

  

            // Se una tappa non è valida, l'intera operazione fallisce.

  

            return nil, err 

  

        }

  

    }

  

  

    // 4. Restituzione del risultato: un aggregato nuovo e consistente.

  

    return newTrip, nil

  

}

  

```

  

  

Questo design è pulito e manutenibile:

  

  

- La logica di coordinamento è isolata nel `ProposalConverter`.

  

- La logica di consistenza interna del `Viaggio` è ancora protetta dal suo Aggregate Root.

  

- Il servizio è facilmente testabile in isolamento, poiché non ha dipendenze infrastrutturali.

  

  

---

  

  

### 11.5. Quando Usare un Domain Service: Una Checklist ✅

  

  

Abusare dei Domain Services è un errore comune che porta a modelli anemici, dove tutta la logica finisce nei servizi e gli oggetti di dominio diventano semplici contenitori di dati. Prima di crearne uno, chiedetevi sempre:

  

  

- [ ] **L'operazione coinvolge più di un aggregato/entità?** Se la logica opera solo su un singolo aggregato, dovrebbe essere un metodo su quell'aggregato.

  

- [ ] **L'operazione sembra "stonata" su qualsiasi oggetto esistente?** Se tentare di inserire un metodo in un'entità la fa sentire meno coesa, è un buon candidato per un Domain Service.

  

- [ ] **L'operazione è stateless?** Se avete bisogno di stato, non è un Domain Service.

  

- [ ] **L'operazione è un concetto importante nel Linguaggio Ubiquo?** Operazioni come "Calcolare Tasse", "Trasferire Fondi", "Convertire Proposta" sono processi di business fondamentali e candidati ideali.

  

  

Se la risposta a queste domande è "sì", allora procedete con la creazione di un Domain Service.

  

  

---

  

  

### 11.6. Conclusioni: Completare la Cassetta degli Attrezzi Tattica

  

  

Con l'introduzione dei Domain Services, la nostra cassetta degli attrezzi per la progettazione tattica del DDD è finalmente completa. Ora abbiamo uno strumento per ogni tipo di logica di business:

  

  

- **Value Objects**: Per descrivere e misurare, con la garanzia dell'immutabilità.

  

- **Entità**: Per rappresentare oggetti con un'identità e una storia.

  

- **Aggregati**: Per raggruppare entità e value objects in confini di consistenza.

  

- **Domain Services**: Per orchestrare operazioni complesse che attraversano i confini degli oggetti.

  

  

Abbiamo imparato a creare modelli di dominio ricchi, espressivi e robusti. Ora siamo pronti per fare un passo indietro e vedere come inserire questo modello di dominio all'interno di un'architettura software più ampia e pulita.

  

  

Nella **Parte III**, esploreremo la **Clean Architecture**, il **Repository Pattern** e la **Dependency Injection**, imparando a proteggere il nostro prezioso dominio dalle preoccupazioni del mondo esterno e a costruire un'applicazione veramente enterprise.

  

  

---

  

# **Parte III: Architettura Pulita e Pattern Avanzati**

  

  

## Capitolo 12: Clean Architecture e Separazione delle Responsabilità

  

  

Benvenuti nella Parte III del nostro libro. Nelle sezioni precedenti, ci siamo immersi nella progettazione tattica del DDD. Abbiamo forgiato un modello di dominio ricco e significativo, composto da Aggregati, Entità e Value Objects, e abbiamo imparato a comunicare attraverso un Linguaggio Ubiquo. Ora possediamo un cuore pulsante per la nostra applicazione: un _core domain_ che rappresenta la vera essenza del business di "Where Should I Be?".

  

  

Ma questo cuore prezioso non può vivere nel vuoto. Deve essere inserito in un corpo, un'applicazione funzionante che interagisce con il mondo esterno: database, API di terze parti, interfacce utente. Come possiamo strutturare la nostra applicazione in modo che il nostro dominio rimanga protetto, puro e isolato dai dettagli tecnici e mutevoli dell'infrastruttura?

  

  

La risposta è un'architettura a strati che impone una rigorosa **separazione delle responsabilità**. In questo capitolo, esploreremo uno degli schemi architetturali più influenti e potenti per raggiungere questo obiettivo: la **Clean Architecture**.

  

  

---

  

  

### 12.1. Il Problema: Il "Grande Pasticcio di Fango" (Big Ball of Mud)

  

  

Senza una disciplina architetturale, i sistemi software tendono a degenerare in quello che viene chiamato un **Big Ball of Mud**. In questo anti-pattern, i confini tra le responsabilità svaniscono. Il codice che gestisce la logica di business è intrecciato con le query del database, con la gestione delle richieste HTTP e con la formattazione delle risposte JSON.

  

  

Immaginiamo un tipico `http.Handler` in Go scritto senza una chiara architettura:

  

  

Go

  

  

``` go

  

//

  

// CONTROESEMPIO: Un handler che fa tutto (Big Ball of Mud)

  

//

  

func CreateTripHandler(db *sql.DB, openAIClient *openai.Client) http.HandlerFunc {

  

    return func(w http.ResponseWriter, r *http.Request) {

  

        // 1. Logica HTTP: Parsing del body della richiesta

  

        var reqBody struct {

  

            Name      string    `json:"name"`

  

            StartDate time.Time `json:"start_date"`

  

            // ...

  

        }

  

        if err := json.NewDecoder(r.Body).Decode(&reqBody); err != nil {

  

            http.Error(w, "Invalid request body", http.StatusBadRequest)

  

            return

  

        }

  

  

        // 2. Logica di Business: Validazione

  

        if reqBody.Name == "" {

  

            http.Error(w, "Trip name is required", http.StatusBadRequest)

  

            return

  

        }

  

        if reqBody.StartDate.Before(time.Now()) {

  

            http.Error(w, "Start date must be in the future", http.StatusBadRequest)

  

            return

  

        }

  

        // 3. Logica di Persistenza: Scrittura diretta sul DB

  

        tripID := uuid.New().String()

  

        _, err := db.ExecContext(r.Context(),

  

            "INSERT INTO trips (id, name, start_date) VALUES ($1, $2, $3)",

  

            tripID, reqBody.Name, reqBody.StartDate)

  

        if err != nil {

  

            http.Error(w, "Failed to save trip", http.StatusInternalServerError)

  

            return

  

        }

  

        // 4. Interazione con API esterne

  

        // ... codice che chiama direttamente openAIClient ...

  

  

        // 5. Logica HTTP: Scrittura della risposta

  

        w.Header().Set("Content-Type", "application/json")

  

        w.WriteHeader(http.StatusCreated)

  

        json.NewEncoder(w).Encode(map[string]string{"id": tripID})

  

    }

  

}

  

```

  

  

Questo approccio è disastroso per diversi motivi:

  

  

- **Fragilità**: Un cambiamento allo schema del database richiede una modifica all'handler HTTP. Un cambiamento alla libreria OpenAI potrebbe rompere la logica di business.

  

- **Impossibilità di Test**: Come si può testare la logica di validazione del business in isolamento? È necessario avviare un server HTTP e un database reale, rendendo i test lenti, complessi e inaffidabili.

  

- **Non Riutilizzabile**: Se volessimo esporre la stessa funzionalità tramite un'interfaccia gRPC o una CLI, dovremmo duplicare tutta la logica di business e di persistenza.

  

- **Accoppiamento Forte**: Ogni parte del sistema è strettamente accoppiata a tutte le altre.

  

  

La Clean Architecture è una strategia formale per prevenire questo caos.

  

  

---

  

  

### 12.2. Introduzione alla Clean Architecture 🧅

  

  

La Clean Architecture, resa popolare da Robert C. "Uncle Bob" Martin, non è un framework, ma un **modello architetturale** per la progettazione di sistemi software. Propone di strutturare il software in una serie di cerchi concentrici, simili a una cipolla.

  

  

_(Fonte: blog.cleancoder.com)_

  

  

Ogni cerchio rappresenta un diverso livello di software. I livelli esterni sono meccanismi, quelli interni sono policy. La regola fondamentale che governa questa architettura è la **Regola della Dipendenza (The Dependency Rule)**.

  

  

> **La Regola della Dipendenza**: Le dipendenze del codice sorgente possono puntare **solo verso l'interno**. Niente in un cerchio interno può sapere alcunché di un cerchio esterno. In particolare, il nome di qualcosa dichiarato in un cerchio esterno non deve essere menzionato dal codice in un cerchio interno.

  

  

Questo significa che la logica di business (interna) non deve dipendere dai dettagli dell'interfaccia utente o del database (esterni). Al contrario, sono i dettagli esterni che devono dipendere e conformarsi alle policy definite internamente.

  

  

---

  

  

### 12.3. I Livelli della Clean Architecture in Dettaglio

  

  

Analizziamo ogni livello e mappiamolo ai componenti della nostra applicazione Go.

  

  

#### **🟡 Livello 1 (Giallo): Entità (Entities)**

  

  

Questo è il cerchio più interno. Contiene gli **oggetti di dominio** che abbiamo meticolosamente progettato nella Parte II: gli Aggregati, le Entità e i Value Objects.

  

  

- **Cosa c'è qui**: Le struct `Trip`, `User`, `Money`, `DateRange`, ecc.

  

- **Caratteristiche**: Questo strato contiene la logica di business più generale e di alto livello. È il cuore pulsante dell'applicazione.

  

- **Dipendenze**: **Nessuna**. Questo codice è Go puro. Non importa se l'applicazione è web, se usa PostgreSQL o DynamoDB. Queste regole di business sono universalmente valide nel nostro dominio.

  

  

#### **🔴 Livello 2 (Rosso): Casi d'Uso (Use Cases / Application Services)**

  

  

Questo livello contiene la logica di business specifica dell'applicazione. Orchestrami i casi d'uso del sistema. Corrisponde perfettamente a quello che abbiamo chiamato **Application Service** nel capitolo 11.

  

  

- **Cosa c'è qui**: Un `TripApplicationService` con metodi come `CreateTripFromProposal`, `AddStopToTrip`, `GetUserTrips`.

  

- **Caratteristiche**: Ogni metodo orchestra un flusso di lavoro: recupera le entità, invoca i loro metodi (o quelli dei Domain Services) e le salva di nuovo.

  

- **Dipendenze**: Dipende dal livello delle Entità. Conosce e usa gli oggetti di dominio. **Non conosce nulla dei livelli esterni**. Ma come fa a salvare i dati senza conoscere il database? Tramite l'**Inversione delle Dipendenze**.

  

  

#### **🟢 Livello 3 (Verde): Adattatori di Interfaccia (Interface Adapters)**

  

  

Questo livello è un insieme di "traduttori" o "adattatori". Il loro compito è convertire i dati da un formato comodo per un livello esterno (come il web o il DB) a un formato comodo per i livelli interni (Use Cases ed Entità), e viceversa.

  

  

- **Cosa c'è qui**:

  

    - **Adattatori DB**: Le implementazioni concrete dei nostri `Repository` (es. `PostgresTripRepository`).

  

    - **Adattatori Web**: I nostri `http.Handler` o `gRPCHandler`. Questi traducono le richieste HTTP in chiamate ai metodi degli Use Cases.

  

    - **Presenters**: Oggetti che prendono i dati di output dagli Use Cases e li formattano per la UI (es. in JSON).

  

- **Caratteristiche**: È il ponte tra il mondo del dominio e il mondo dell'infrastruttura.

  

  

#### **🔵 Livello 4 (Blu): Framework e Driver (Frameworks and Drivers)**

  

  

Questo è il cerchio più esterno. Contiene tutti i dettagli, tutto ciò che è volatile e specifico di una tecnologia.

  

  

- **Cosa c'è qui**: Il web framework (es. `net/http` di Go), il driver del database (es. `pq` o `pgx`), il client SDK di AWS, il frontend SvelteKit, la libreria di logging.

  

- **Caratteristiche**: È il livello più "instabile". Le tecnologie cambiano. L'obiettivo della Clean Architecture è rendere questo strato un dettaglio implementativo facilmente sostituibile, senza impattare i livelli interni più stabili.

  

  

---

  

  

### 12.4. Implementare la Clean Architecture in Go

  

  

Vediamo come la Regola della Dipendenza prende forma in un progetto Go.

  

  

#### **La Struttura delle Directory**

  

  

Una buona struttura di directory può aiutare a visualizzare e far rispettare i confini architetturali.

  

  

```

  

/where-should-i-be

  

  /internal

  

    /domain

  

      /trip/

  

        trip.go         // Aggregate Root, Entità interne, VO

  

        trip_factory.go // Factory

  

      /user/

  

        user.go

  

      /common/

  

        money.go

  

        email.go

  

    /application

  

      trip_service.go   // TripApplicationService (Use Cases)

  

      ports.go          // Definizioni delle interfacce (es. TripRepository)

  

    /adapters

  

      /persistence/postgres/

  

        postgres_trip_repo.go // Implementazione del Repository

  

      /web/http/

  

        trip_handler.go // Handler HTTP

  

      /gateway/openai/

  

        openai_client.go // Adattatore per l'API di OpenAI

  

  /cmd

  

    /server/

  

      main.go           // Il punto di ingresso dove tutto viene "cablato"

  

```

  

  

#### **Il Principio di Inversione delle Dipendenze (DIP)**

  

  

Il DIP è la magia che fa funzionare la Clean Architecture. Dice che i moduli di alto livello non dovrebbero dipendere da quelli di basso livello, ma entrambi dovrebbero dipendere da astrazioni (interfacce).

  

  

1. **Definiamo l'interfaccia nel livello interno**: Il nostro `Application Service` ha bisogno di un repository. Definiamo l'interfaccia `TripRepository` nel package `application`.

  

    Go

  

    ``` go

  

    // internal/application/ports.go

  

    package application

  

    import (

  

        "context"

  

        "where-should-i-be/internal/domain/trip"

  

    )

  

    // TripRepository è una "porta" che il nostro caso d'uso

  

    // utilizza per parlare con la persistenza.

  

    type TripRepository interface {

  

        Save(ctx context.Context, t *trip.Trip) error

  

        FindByID(ctx context.Context, id trip.ID) (*trip.Trip, error)

  

    }

  

    ```

  

2. **L'Use Case dipende dall'interfaccia**: Il nostro `TripApplicationService` riceve un `TripRepository` come dipendenza.

  

    Go

  

    ``` go

  

    // internal/application/trip_service.go

  

    package application

  

    // ...

  

    type TripApplicationService struct {

  

        repo TripRepository // Dipende dall'interfaccia, non da un'implementazione!

  

    }

  

    func (s *TripApplicationService) CreateNewTrip(...) (*trip.Trip, error) {

  

        // ... logica ...

  

        newTrip := // ...

  

        return newTrip, s.repo.Save(ctx, newTrip) // Usa l'interfaccia

  

    }

  

    ```

  

3. **Implementiamo l'interfaccia nel livello esterno**: L'adattatore per PostgreSQL implementa l'interfaccia definita nel livello applicativo.

  

    Go

  

    ``` go

  

    // internal/adapters/persistence/postgres/postgres_trip_repo.go

  

    package postgres

  

    import (

  

        "database/sql"

  

        // ...

  

    )

  

    // La struct dipende da un dettaglio infrastrutturale: *sql.DB

  

    type PostgresTripRepository struct {

  

        db *sql.DB

  

    }

  

    // Il metodo Save implementa l'interfaccia del livello applicativo.

  

    func (r *PostgresTripRepository) Save(ctx context.Context, t *trip.Trip) error {

  

        // ... logica SQL per salvare il viaggio ...

  

    }

  

    // ...

  

    ```

  

  

Il **flusso di controllo** va dal controller all'use case e poi al repository, ma le **dipendenze del codice sorgente** puntano sempre verso l'interno: `PostgresTripRepository` (esterno) dipende da `application.TripRepository` (interno). Abbiamo invertito la dipendenza!

  

  

---

  

  

### 12.5. I Vantaggi Concreti della Clean Architecture 🏆

  

  

Perché sobbarcarsi tutto questo lavoro di strutturazione? I benefici a lungo termine sono immensi.

  

  

- **Testabilità Superiore**: Possiamo testare i nostri `Application Services` e il nostro `Domain` in totale isolamento, fornendo un'implementazione "mock" del `TripRepository`. I test diventano velocissimi, affidabili e facili da scrivere.

  

- **Indipendenza dal Database**: Domani vogliamo passare da PostgreSQL a DynamoDB per ragioni di costo e scalabilità? Nessun problema. Basta scrivere un nuovo adattatore `DynamoDBTripRepository` che implementi la stessa interfaccia. Nessuna riga di codice nel dominio o nell'applicazione deve essere modificata.

  

- **Indipendenza dall'Interfaccia Utente**: L'applicazione non sa se è guidata da una richiesta HTTP, gRPC o da una riga di comando. Possiamo aggiungere nuove interfacce senza toccare i casi d'uso.

  

- **Manutenibilità e Comprensibilità**: Le responsabilità sono chiare. Un nuovo sviluppatore sa esattamente dove guardare per trovare la logica di business, dove per trovare il codice del database e dove per trovare gli handler HTTP.

  

  

---

  

  

### 12.6. Conclusioni: Proteggere il Nostro Asset più Prezioso

  

  

La Clean Architecture non è solo un modo di organizzare le directory; è una filosofia che ci impone di riconoscere che il **modello di dominio è l'asset più prezioso del nostro software**. L'interfaccia utente, il database, i framework... sono solo dettagli. Dettagli importanti, ma che cambiano nel tempo. Il business, invece, ha una stabilità maggiore.

  

  

Adottando la Clean Architecture e la Regola della Dipendenza, costruiamo un "muro di fuoco" attorno al nostro dominio, proteggendolo dalla volatilità dell'infrastruttura. Creiamo un sistema che non è solo funzionante oggi, ma che è anche testabile, manutenibile e pronto a evolvere per gli anni a venire.

  

  

Nel prossimo capitolo, approfondiremo uno degli adattatori più importanti: il **Repository Pattern**, esplorando nel dettaglio come implementare un'astrazione efficace per la persistenza.

  

  

---

  

## Capitolo 13: Repository Pattern e Astrazione della Persistenza

  

  

Nel capitolo precedente, abbiamo eretto le mura della nostra fortezza con la Clean Architecture, stabilendo una regola ferrea: il nostro prezioso dominio, il cuore del sistema, non deve sapere nulla del mondo esterno, specialmente dei dettagli sordidi e mutevoli della persistenza dei dati. Questa è una grande idea in teoria, ma solleva una domanda fondamentale: se il dominio è isolato, come facciamo a salvare e caricare i nostri oggetti di business? Come fa il nostro aggregato `Viaggio` a passare da un oggetto in memoria a una serie di righe in un database PostgreSQL, e viceversa?

  

  

La risposta è un ponte, un'astrazione attentamente progettata che si trova al confine tra il nostro mondo pulito del dominio e il mondo disordinato dell'infrastruttura. Nel Domain-Driven Design, questo ponte ha un nome specifico: il **Repository Pattern**.

  

  

Il Repository è molto più di un semplice oggetto di accesso ai dati (DAO). È un pattern fondamentale del DDD che fornisce l'illusione di una collezione di oggetti di dominio in memoria, permettendo al resto della nostra applicazione di rimanere beatamente ignorante dei dettagli di SQL, NoSQL o qualsiasi altra tecnologia di storage.

  

  

---

  

  

### 13.1. Cos'è il Repository Pattern?

  

  

> **Definizione**: Il **Repository Pattern** media tra il layer di dominio e il layer di mappatura dei dati, agendo come una collezione di oggetti di dominio in memoria. Incapsula la logica necessaria per ottenere oggetti di dominio e persisterne le modifiche.

  

  

Analizziamo questa definizione. I punti chiave sono:

  

  

1. **L'Illusione di una Collezione in Memoria**: Questo è il concetto più importante. Quando il nostro `Application Service` usa un repository, il codice dovrebbe dare l'impressione di interagire con una semplice collezione, come una slice o una mappa. Dovrebbe poter dire: "Cara collezione di Viaggi, dammi il viaggio con questo ID" o "Cara collezione di Viaggi, salva questo nuovo viaggio". Non dovrebbe mai dire: "Esegui questa query SQL con una `JOIN` sulla tabella delle tappe".

  

2. **Lavora con gli Aggregati**: Un repository è definito per un **aggregato**. Avremo un `TripRepository` per gestire l'aggregato `Viaggio`. **Non** avremo un `StopRepository` separato. Perché? Perché, come stabilito nel Capitolo 8, l'integrità di un aggregato è garantita dalla sua radice (l'Aggregate Root). Non si possono modificare le sue parti interne bypassando la radice. Pertanto, si carica e si salva sempre l'aggregato nella sua interezza.

  

3. **Incapsula la Logica di Persistenza**: Tutto il codice specifico per la tecnologia (query SQL, chiamate all'SDK di DynamoDB, ecc.) è nascosto all'interno dell'implementazione concreta del repository. Il resto dell'applicazione non lo vede mai.

  

4. **Traduce tra Modelli**: Come abbiamo visto nel capitolo sui Value Objects, il nostro dominio usa tipi ricchi come `Money` o `DateRange`. Il database, invece, usa tipi primitivi come `NUMERIC`, `VARCHAR` e `TIMESTAMP`. Il repository è responsabile di questa traduzione (o _mapping_) in entrambe le direzioni.

  

  

---

  

  

### 13.2. Progettare l'Interfaccia del Repository (La "Porta")

  

  

Seguendo i principi della Clean Architecture, il nostro `Application Layer` (dove vivono i casi d'uso) non dipende dall'implementazione concreta del repository, ma da una sua **astrazione**: un'interfaccia Go. Questa interfaccia è la "porta" attraverso cui il dominio parla al mondo esterno.

  

  

**Dove vive l'interfaccia?** Vive nel layer applicativo, perché è quest'ultimo a definirne il contratto di cui ha bisogno.

  

  

Go

  

  

``` go

  

//

  

// ESEMPIO CORRETTO: L'interfaccia del Repository

  

//

  

  

// internal/application/ports.go

  

package application

  

  

import (

  

    "context"

  

    "where-should-i-be/internal/domain/trip"

  

    "where-should-i-be/internal/domain/identity"

  

)

  

  

// TripRepository definisce il contratto che i casi d'uso

  

// si aspettano per interagire con la persistenza dei viaggi.

  

// I nomi dei metodi sono agnostici rispetto alla tecnologia.

  

type TripRepository interface {

  

    // Save gestisce sia la creazione (INSERT) che l'aggiornamento (UPDATE).

  

    // È un'operazione di "upsert".

  

    Save(ctx context.Context, t *trip.Trip) error

  

  

    // FindByID recupera un singolo aggregato tramite la sua identità.

  

    FindByID(ctx context.Context, id identity.TripID) (*trip.Trip, error)

  

  

    // FindByOwnerID è un esempio di un metodo di query più specifico

  

    // richiesto da un caso d'uso.

  

    FindByOwnerID(ctx context.Context, ownerID identity.UserID) ([]*trip.Trip, error)

  

  

    // Delete rimuove un aggregato.

  

    Delete(ctx context.Context, id identity.TripID) error

  

}

  

```

  

  

**Convenzioni di Naming e Progettazione:**

  

  

- Usate verbi che evocano una collezione: `Find`, `Save`, `Delete`, `Add`. Evitate `Insert`, `Update`, `Select`.

  

- I metodi accettano e restituiscono sempre oggetti di dominio (`*trip.Trip`, `identity.TripID`), mai DTO o tipi di database.

  

- Ogni metodo dovrebbe accettare un `context.Context` come primo parametro. Questa è una best practice fondamentale in Go per la gestione di deadline, cancellation e passaggio di dati di richiesta (come i trace ID per l'observability).

  

  

Come gestire query complesse?

  

  

Evitate di riempire l'interfaccia con un metodo per ogni combinazione di filtri. Questo la renderebbe fragile e difficile da mantenere. Le strategie sono:

  

  

1. **Metodi di Query Specifici**: Aggiungete metodi solo per le query che sono chiaramente definite dai casi d'uso, come `FindByOwnerID`.

  

2. **Specification Pattern**: Un pattern più avanzato dove si costruisce un oggetto-query che incapsula i criteri di ricerca e lo si passa a un metodo `Find` generico.

  

3. **Separare le Letture (CQRS)**: Per query complesse e di sola lettura (es. reportistica), spesso è meglio non usare affatto il repository dell'aggregato. Si può creare un "modello di lettura" ottimizzato (una _read model_) interrogato direttamente, bypassando il dominio. Questo è il primo passo verso il CQRS, che affronteremo nel Capitolo 15.

  

  

---

  

  

### 13.3. Implementazione Concreta: `PostgresTripRepository`

  

  

Ora costruiamo l'adattatore per PostgreSQL. Questo codice vive nel layer più esterno (`adapters`).

  

  

**Dove vive l'implementazione?** `internal/adapters/persistence/postgres/`

  

  

Go

  

  

``` go

  

// internal/adapters/persistence/postgres/postgres_trip_repo.go

  

package postgres

  

  

import (

  

    "context"

  

    "database/sql"

  

    "errors"

  

  

    "where-should-i-be/internal/application" // Importa per l'interfaccia

  

    "where-should-i-be/internal/domain/trip"

  

    "where-should-i-be/internal/domain/identity"

  

)

  

  

// PostgresTripRepository è l'implementazione concreta per PostgreSQL.

  

// Dipende da un dettaglio infrastrutturale: *sql.DB.

  

type PostgresTripRepository struct {

  

    db *sql.DB

  

}

  

  

// NewPostgresTripRepository è la sua factory.

  

func NewPostgresTripRepository(db *sql.DB) *PostgresTripRepository {

  

    return &PostgresTripRepository{db: db}

  

}

  

  

// Garanzia a tempo di compilazione che la nostra struct implementa l'interfaccia.

  

var _ application.TripRepository = (*PostgresTripRepository)(nil)

  

```

  

  

#### **Implementazione del Metodo `Save`**

  

  

Il salvataggio di un aggregato è un'operazione transazionale.

  

  

Go

  

  

``` go

  

func (r *PostgresTripRepository) Save(ctx context.Context, t *trip.Trip) error {

  

    tx, err := r.db.BeginTx(ctx, nil)

  

    if err != nil {

  

        return err

  

    }

  

    // Defer a rollback in caso di errore. Se il commit ha successo,

  

    // il rollback non farà nulla.

  

    defer tx.Rollback()

  

  

    // 1. Salva l'Aggregate Root (UPSERT)

  

    // Qui scomponiamo i Value Objects (DateRange, Budget) in colonne primitive.

  

    _, err = tx.ExecContext(ctx, `

  

        INSERT INTO trips (id, owner_id, name, status, start_date, end_date, budget_amount, budget_currency)

  

        VALUES ($1, $2, $3, $4, $5, $6, $7, $8)

  

        ON CONFLICT (id) DO UPDATE SET

  

            name = EXCLUDED.name,

  

            status = EXCLUDED.status,

  

            start_date = EXCLUDED.start_date,

  

            end_date = EXCLUDED.end_date,

  

            budget_amount = EXCLUDED.budget_amount,

  

            budget_currency = EXCLUDED.budget_currency

  

    `, t.ID(), t.OwnerID(), t.Name(), t.Status(), t.DateRange().Start(), t.DateRange().End(), t.Budget().Amount(), t.Budget().Currency())

  

    if err != nil {

  

        return err

  

    }

  

  

    // 2. Sincronizza le entità figlie (le Tappe)

  

    // La strategia più semplice e robusta è "delete-then-insert".

  

    _, err = tx.ExecContext(ctx, "DELETE FROM stops WHERE trip_id = $1", t.ID())

  

    if err != nil {

  

        return err

  

    }

  

  

    for _, s := range t.Stops() { // Assumendo che Trip abbia un getter Stops()

  

        _, err = tx.ExecContext(ctx, `

  

            INSERT INTO stops (id, trip_id, place_id, day, notes)

  

            VALUES ($1, $2, $3, $4, $5)

  

        `, s.ID(), t.ID(), s.PlaceID(), s.Day(), s.Notes())

  

        if err != nil {

  

            return err

  

        }

  

    }

  

  

    // 3. Se tutto è andato bene, conferma la transazione.

  

    return tx.Commit()

  

}

  

```

  

  

#### **Implementazione del Metodo `FindByID`**

  

  

Il caricamento richiede il processo inverso di **idratazione**: da righe di database a un aggregato ricco.

  

  

Go

  

  

``` go

  

func (r *PostgresTripRepository) FindByID(ctx context.Context, id identity.TripID) (*trip.Trip, error) {

  

    // 1. Recupera la riga dell'Aggregate Root

  

    row := r.db.QueryRowContext(ctx, "SELECT ... FROM trips WHERE id = $1", id)

  

  

    // ... variabili per scansionare i dati ...

  

    err := row.Scan(&id, &ownerID, /* ... e tutti gli altri campi ... */)

  

    if err != nil {

  

        if errors.Is(err, sql.ErrNoRows) {

  

            return nil, application.ErrTripNotFound // Un errore definito nel layer applicativo

  

        }

  

        return nil, err

  

    }

  

  

    // 2. Recupera le entità figlie

  

    rows, err := r.db.QueryContext(ctx, "SELECT ... FROM stops WHERE trip_id = $1", id)

  

    if err != nil {

  

        return nil, err

  

    }

  

    defer rows.Close()

  

  

    var stops []trip.Stop // Assumendo che Stop sia un tipo esportato o accessibile

  

    for rows.Next() {

  

        // ... scansiona i dati di una tappa ...

  

        // ... ricostruisci l'oggetto Stop ...

  

        stops = append(stops, rebuiltStop)

  

    }

  

  

    // 3. Idrata l'Aggregato

  

    // Usiamo una Factory per ricostruire l'aggregato, assicurandoci che sia valido.

  

    return trip.Hydrate(id, ownerID, /* ... tutti gli altri parametri e le tappe ... */), nil

  

}

  

```

  

  

_Nota: `trip.Hydrate` sarebbe una factory speciale, non pubblica, usata solo dal repository per assemblare un aggregato da dati già esistenti, potenzialmente bypassando alcune validazioni che si applicano solo alla creazione ex-novo._

  

  

---

  

  

### 13.4. Repository vs. DAO (Data Access Object)

  

  

È facile confondere questi due pattern, ma la loro intenzione è molto diversa.

  

  

|Caratteristica|**Repository** (Pattern di DDD)|**DAO** (Pattern di Accesso ai Dati)|

  

|---|---|---|

  

|**Lavora con**|**Aggregati** di dominio.|Singole tabelle del database.|

  

|**Restituisce**|Oggetti di dominio ricchi e consistenti.|DTO (Data Transfer Objects) o dati grezzi.|

  

|**Granularità**|Grossolana. Es. `TripRepository`.|Fine. Es. `TripDAO`, `StopDAO`.|

  

|**Scopo**|Astrazione del comportamento di una collezione.|Astrazione di una singola fonte di dati.|

  

  

Un Repository _potrebbe_ usare internamente diversi DAO per comporre un aggregato, ma il layer applicativo non deve saperlo.

  

  

---

  

  

### 13.5. Test e Mocking: La Ricompensa dell'Astrazione

  

  

Il più grande vantaggio di questa architettura è la testabilità. Poiché i nostri `Application Services` dipendono da un'interfaccia, possiamo facilmente sostituirla nei test con un'implementazione fittizia (_mock_).

  

  

Go

  

  

```go

  

// Esempio di test per un Application Service

  

func TestCreateNewTrip_Success(t *testing.T) {

  

    // 1. Setup: Crea il mock del repository

  

    mockRepo := new(mocks.TripRepository) // Usando una libreria come testify/mock

  

    tripToSave := // ... costruisci l'oggetto trip che ti aspetti venga salvato ...

  

  

    // 2. Expectation: Dì al mock cosa aspettarsi

  

    // Ci aspettiamo che il metodo Save venga chiamato una volta con il nostro oggetto.

  

    mockRepo.On("Save", mock.Anything, tripToSave).Return(nil)

  

  

    // 3. Execution: Crea il servizio con il mock e chiamalo

  

    appService := application.NewTripApplicationService(mockRepo)

  

    result, err := appService.CreateNewTrip(...)

  

  

    // 4. Assertion: Verifica i risultati

  

    assert.NoError(t, err)

  

    assert.NotNil(t, result)

  

    mockRepo.AssertExpectations(t) // Verifica che Save sia stato chiamato come previsto.

  

}

  

```

  

  

Questo test viene eseguito in millisecondi, senza richiedere un database, permettendoci di verificare la logica del nostro caso d'uso in completo isolamento.

  

  

---

  

  

### 13.6. Conclusioni: L'Astrazione che Libera il Dominio

  

  

Il Repository Pattern è molto più di un meccanismo per accedere ai dati. È un'astrazione strategica che:

  

  

- **Disaccoppia il dominio dalla persistenza**, realizzando la promessa della Clean Architecture.

  

- **Semplifica il layer applicativo**, fornendo una semplice metafora di una collezione.

  

- **Centralizza la logica di accesso ai dati e di mapping**, rendendola più facile da gestire e ottimizzare.

  

- **Aumenta esponenzialmente la testabilità** del nostro sistema.

  

  

Padroneggiare il Repository Pattern significa costruire un ponte robusto e flessibile tra il cuore del nostro software e il mondo esterno. Con questo ponte in posizione, siamo ora pronti a esplorare come "iniettare" queste dipendenze in modo pulito e come evolvere i nostri pattern di dati con CQRS.

  

  

---

  

## Capitolo 14: Dependency Injection Professionale in Go

  

  

Nei capitoli precedenti di questa sezione, abbiamo compiuto un lavoro monumentale. Abbiamo progettato un'architettura pulita che protegge il nostro dominio (Capitolo 12) e abbiamo definito un ponte robusto verso il mondo della persistenza tramite il Repository Pattern (Capitolo 13). Ora abbiamo una serie di componenti ben definiti e disaccoppiati:

  

  

- Un `HTTP Handler` che dipende da un `Application Service`.

  

- Un `Application Service` che dipende da un'interfaccia `Repository`.

  

- Un'implementazione `PostgresRepository` che dipende da una connessione al database `*sql.DB`.

  

  

Questi componenti sono come dei mattoncini LEGO® di alta qualità, ognuno con le sue porte e i suoi connettori ben definiti. Ma ora sorge la domanda fondamentale: **chi assembla i mattoncini?** Chi crea tutte queste istanze e le "passa" (le inietta) alle altre che ne hanno bisogno?

  

  

Questa fase, spesso trascurata, è critica. Un assemblaggio disordinato può vanificare tutti i benefici di un'architettura pulita. In questo capitolo, affronteremo il "problema del cablaggio" e impareremo a gestirlo in modo professionale in Go utilizzando il pattern della **Dependency Injection (DI)** e strumenti moderni come **Google Wire**.

  

  

---

  

  

### 14.1. Il Problema: Il Cablaggio nel Caos

  

  

Quando un'applicazione è piccola, è facile assemblare i componenti manualmente nella funzione `main`.

  

  

Go

  

  

```go

  

//

  

// CONTROESEMPIO: Cablaggio manuale e disordinato

  

//

  

func main() {

  

    // Configurazione sparsa

  

    dbUser := os.Getenv("DB_USER")

  

    dbPass := os.Getenv("DB_PASS")

  

    connStr := fmt.Sprintf("user=%s password=%s ...", dbUser, dbPass)

  

  

    // Creazione delle dipendenze

  

    db, err := sql.Open("postgres", connStr)

  

    if err != nil {

  

        log.Fatalf("failed to open db connection: %v", err)

  

    }

  

    defer db.Close()

  

  

    // Cablaggio manuale

  

    tripRepo := postgres.NewPostgresTripRepository(db)

  

    userRepo := postgres.NewPostgresUserRepository(db)

  

    // ... altri 10 repository ...

  

  

    tripService := application.NewTripApplicationService(tripRepo)

  

    userService := application.NewUserApplicationService(userRepo)

  

    // ... altri 10 servizi applicativi ...

  

    authService := // ... creazione del servizio di autenticazione ...

  

  

    // Creazione degli handler, un incubo di parametri

  

    tripHandler := web.NewTripHandler(tripService, authService)

  

    userHandler := web.NewUserHandler(userService, authService)

  

  

    http.HandleFunc("/trips", tripHandler.HandleCreateTrip)

  

    // ...

  

    log.Fatal(http.ListenAndServe(":8080", nil))

  

}

  

```

  

  

Questo approccio non scala. Man mano che l'applicazione cresce, la funzione `main` diventa un "mostro":

  

  

- **Fragile**: L'ordine di inizializzazione è critico e facile da sbagliare.

  

- **Difficile da Leggere**: Comprendere il grafo delle dipendenze dell'applicazione richiede di analizzare un'enorme e complessa funzione.

  

- **Violazione del DRY (Don't Repeat Yourself)**: Le stesse dipendenze (come `authService`) vengono passate a più costruttori.

  

- **Difficile da Testare**: Testare il processo di avvio stesso diventa quasi impossibile.

  

  

Abbiamo bisogno di un approccio sistematico. Abbiamo bisogno della Dependency Injection.

  

  

---

  

  

### 14.2. Cos'è la Dependency Injection (DI)?

  

  

La Dependency Injection è un concetto sorprendentemente semplice, che abbiamo già applicato istintivamente.

  

  

> **Definizione**: La **Dependency Injection** è un design pattern in cui un oggetto o una funzione riceve le dipendenze di cui ha bisogno da una fonte esterna, invece di crearle da solo. È l'applicazione pratica del **Principio di Inversione delle Dipendenze**.

  

  

Invece di questo (Service Locator, un anti-pattern):

  

  

Go

  

  

```go

  

func NewTripApplicationService() *TripApplicationService {

  

    // Il servizio crea la sua dipendenza. MALE!

  

    repo := postgres.NewPostgresTripRepository(globalDB) 

  

    return &TripApplicationService{repo: repo}

  

}

  

```

  

  

Facciamo questo (Dependency Injection):

  

  

Go

  

  

```go

  

func NewTripApplicationService(repo TripRepository) *TripApplicationService {

  

    // Il servizio riceve la sua dipendenza. BENE!

  

    return &TripApplicationService{repo: repo}

  

}

  

```

  

  

La DI non è un framework, è un principio di progettazione. La vera sfida non è _usare_ la DI, ma _gestire l'assemblaggio_ di un intero grafo di dipendenze in modo pulito. È qui che entrano in gioco i **contenitori DI**.

  

  

---

  

  

### 14.3. Il Contenitore DI: L'Assemblatore Intelligente 🤖

  

  

Immagina un contenitore DI come un capocantiere esperto in una fabbrica di automobili. Invece di assemblare l'auto pezzo per pezzo manualmente, tu gli fornisci le "istruzioni di montaggio" per ogni componente (il motore, il telaio, le ruote) e gli dici: "Costruiscimi un'auto". Il capocantiere legge le istruzioni, capisce che per montare le ruote serve il telaio, e che per montare il telaio serve il motore, quindi assembla tutto nell'ordine corretto e ti consegna l'auto finita.

  

  

Un contenitore DI fa esattamente questo per il nostro software. Le sue responsabilità sono:

  

  

1. **Registrazione**: Gli insegnamo come costruire ogni componente. Questi "insegnamenti" sono le nostre funzioni `New...`, chiamate _provider_ o _costruttori_.

  

2. **Risoluzione del Grafo**: Analizza le dipendenze. Vede che `Handler` richiede `Service`, che richiede `Repository`, che richiede `DB`, e costruisce un piano per assemblarli.

  

3. **Iniezione**: Chiama i nostri costruttori, passando le dipendenze richieste che ha già costruito.

  

4. **Gestione del Ciclo di Vita**: Decide se un oggetto deve essere un **singleton** (creato una sola volta per tutta la durata dell'applicazione, come una connessione al DB) o **transient** (creato nuovo ogni volta che serve).

  

  

---

  

  

### 14.4. Approcci alla DI in Go: Una Scelta di Campo

  

  

La community di Go ha opinioni forti sulla DI. Esistono tre approcci principali:

  

  

1. Cablaggio Manuale Strutturato (Pure Go)

  

  

Questo approccio prevede di scrivere il codice di cablaggio a mano, ma in modo pulito e strutturato, spesso in una funzione Build o in un package wire. È trasparente, non ha "magia", ma può diventare verboso.

  

  

2. DI basata su Reflection (Da Evitare)

  

  

Librerie come facebookgo/inject usano la reflection (reflect package) per iniettare le dipendenze automaticamente in campi struct taggati.

  

  

Perché evitarle? Spostano il controllo dal programmatore alla libreria. Gli errori di dipendenza si verificano a runtime invece che a compile-time. Il codice è più difficile da seguire e le performance possono risentirne. In generale, la community Go le considera un anti-pattern.

  

  

3. DI basata su Generazione di Codice (La Scelta Professionale ✅)

  

  

Questo è il punto d'incontro ideale per Go. Uno strumento a riga di comando analizza il codice e genera un file .go che contiene il cablaggio manuale e pulito. Otteniamo i benefici dell'automazione senza sacrificare nessuno dei vantaggi di Go.

  

  

- **Nessuna Magia, Nessuna Reflection**: Il codice generato è Go standard, leggibile e debuggabile.

  

- **Sicurezza a Compile-Time**: Se una dipendenza non può essere soddisfatta, il generatore di codice fallisce, non la tua applicazione in produzione.

  

- **Performance Massime**: Il codice generato è efficiente come se lo avessi scritto a mano.

  

  

Lo strumento di riferimento in questa categoria è **Google Wire**.

  

  

---

  

  

### 14.5. Guida Pratica a Google Wire

  

  

Wire è diventato lo standard de facto per la DI in Go. Vediamo come usarlo nel nostro progetto.

  

  

#### **Passo 1: Installare Wire**

  

  

Bash

  

  

```

  

go install github.com/google/wire/cmd/wire@latest

  

```

  

  

#### **Passo 2: Scrivere i Costruttori (Providers)**

  

  

La buona notizia è che, seguendo i principi della Clean Architecture, abbiamo già scritto la maggior parte dei nostri provider! Sono le nostre funzioni `New...`.

  

  

Go

  

  

```go

  

// internal/adapters/persistence/postgres/postgres_trip_repo.go

  

func NewPostgresTripRepository(db *sql.DB) *PostgresTripRepository { ... }

  

  

// internal/application/trip_service.go

  

func NewTripApplicationService(repo TripRepository) *TripApplicationService { ... }

  

  

// internal/adapters/web/http/trip_handler.go

  

func NewTripHandler(service *application.TripApplicationService) *TripHandler { ... }

  

```

  

  

#### **Passo 3: Creare il Set di Provider e l'Injector**

  

  

Ora dobbiamo dire a Wire come usare questi costruttori. Lo facciamo in un file `wire.go` (che per convenzione viene ignorato dalla compilazione Go grazie a un _build tag_).

  

  

Go

  

  

```go

  

// cmd/server/wire.go

  

  

//go:build wireinject

  

// +build wireinject

  

  

package main

  

  

import (

  

    "database/sql"

  

    "github.com/google/wire"

  

  

    // importiamo tutti i nostri package

  

    "where-should-i-be/internal/application"

  

    "where-should-i-be/internal/adapters/persistence/postgres"

  

    "where-should-i-be/internal/adapters/web/http"

  

)

  

  

// Definiamo un "Provider Set" per raggruppare i provider correlati.

  

// Questo è utile per la riusabilità.

  

var tripSet = wire.NewSet(

  

    // Diciamo a Wire che quando serve un'interfaccia application.TripRepository,

  

    // deve usare l'implementazione *postgres.PostgresTripRepository.

  

    wire.Bind(new(application.TripRepository), new(*postgres.PostgresTripRepository)),

  

    postgres.NewPostgresTripRepository,

  

    application.NewTripApplicationService,

  

    http.NewTripHandler,

  

)

  

  

// L'Injector è una funzione che dice a Wire quale oggetto finale vogliamo costruire.

  

// Il corpo di questa funzione verrà generato da Wire.

  

func initializeApp(db *sql.DB) (*http.TripHandler, error) {

  

    // La chiamata a wire.Build istruisce il generatore.

  

    // L'errore `panic` è un segnaposto che non verrà mai eseguito.

  

    wire.Build(tripSet)

  

    return nil, nil

  

}

  

```

  

  

#### **Passo 4: Eseguire Wire e Analizzare il Risultato**

  

  

Dalla directory `cmd/server/`, eseguiamo il comando:

  

  

Bash

  

  

```

  

wire

  

```

  

  

Wire creerà un nuovo file chiamato `wire_gen.go`. Diamo un'occhiata!

  

  

Go

  

  

```go

  

// cmd/server/wire_gen.go

  

  

// Code generated by Wire. DO NOT EDIT.

  

  

//go:generate go run -mod=mod github.com/google/wire/cmd/wire

  

//go:build !wireinject

  

// +build !wireinject

  

  

package main

  

  

// ... import ...

  

  

func initializeApp(db *sql.DB) (*http.TripHandler, error) {

  

    // Questo è codice Go pulito e leggibile, generato per noi!

  

    postgresTripRepository := postgres.NewPostgresTripRepository(db)

  

    tripApplicationService := application.NewTripApplicationService(postgresTripRepository)

  

    tripHandler := http.NewTripHandler(tripApplicationService)

  

    return tripHandler, nil

  

}

  

```

  

  

**Nessuna magia!** Wire ha semplicemente scritto il codice di cablaggio manuale che avremmo scritto noi, ma in modo automatico e senza errori.

  

  

#### **Passo 5: Usare l'Injector in `main.go`**

  

  

La nostra funzione `main` diventa ora incredibilmente semplice e pulita.

  

  

Go

  

  

```go

  

// cmd/server/main.go

  

package main

  

  

func main() {

  

    db := // ... codice per connettersi al db ...

  

    // Chiamiamo la funzione generata da Wire per assemblare l'applicazione.

  

    tripHandler, err := initializeApp(db)

  

    if err != nil {

  

        log.Fatalf("failed to initialize app: %v", err)

  

    }

  

  

    // Ora usiamo l'handler

  

    http.HandleFunc("/trips", tripHandler.HandleCreateTrip)

  

    // ...

  

}

  

```

  

  

---

  

  

### 14.6. Gestione della Configurazione e del Cleanup

  

  

Le applicazioni reali hanno bisogno di configurazioni e di rilasciare le risorse in modo pulito.

  

  

**Configurazione**: Possiamo passare un oggetto `Config` alla nostra funzione `initializeApp`. Wire lo userà per configurare i componenti.

  

  

**Cleanup**: Wire ha un supporto eccellente per il cleanup. Se un provider crea una risorsa (come `*sql.DB`), può restituire anche una funzione di cleanup. Wire si assicurerà che tutte le funzioni di cleanup vengano chiamate nell'ordine inverso di creazione quando l'applicazione termina.

  

  

Go

  

  

```go

  

// Esempio di provider con cleanup

  

func ProvideDatabaseConnection(cfg Config) (*sql.DB, func(), error) {

  

    db, err := sql.Open("postgres", cfg.DatabaseURL)

  

    if err != nil {

  

        return nil, nil, err

  

    }

  

    cleanup := func() {

  

        db.Close()

  

        log.Println("Database connection closed.")

  

    }

  

  

    return db, cleanup, nil

  

}

  

  

// In wire.go, initializeApp restituirà anche la funzione di cleanup

  

func initializeApp(...) (*App, func(), error) { ... }

  

  

// In main.go

  

func main() {

  

    app, cleanup, err := initializeApp(...)

  

    if err != nil { ... }

  

    defer cleanup() // Chiusura pulita garantita!

  

  

    // ... avvia l'app ...

  

}

  

```

  

  

---

  

  

### 14.7. Conclusioni: Ordine e Professionalità nel Cablaggio

  

  

La Dependency Injection non è un optional in un'architettura software seria, è il meccanismo che le permette di funzionare. Mentre il cablaggio manuale può essere sufficiente per progetti piccoli, l'uso di un generatore di codice come **Google Wire** porta il nostro approccio a un livello professionale.

  

  

- **Automatizza** il processo di cablaggio, riducendo il boilerplate e gli errori.

  

- **Garantisce la sicurezza dei tipi** e la risoluzione delle dipendenze a tempo di compilazione.

  

- **Produce codice Go idiomatico**, trasparente e performante, senza ricorrere a "magie" basate sulla reflection.

  

- **Gestisce elegantemente** il ciclo di vita delle risorse, inclusa la loro chiusura.

  

  

Con un sistema di DI robusto, abbiamo completato l'assemblaggio della nostra architettura. Ora siamo pronti per esplorare pattern ancora più avanzati, come il **CQRS**, che ci permetteranno di ottimizzare e scalare ulteriormente la nostra applicazione.

  

  

---

  

## Capitolo 15: CQRS e Event Sourcing

  

  

Siamo giunti al capitolo finale della nostra esplorazione dell'architettura e dei pattern avanzati. Finora, abbiamo costruito un sistema robusto basato su DDD e Clean Architecture, con un modello di dominio ricco e un repository che lo astrae dalla persistenza. Questo è un modello potente e sufficiente per un'ampia gamma di applicazioni.

  

  

Tuttavia, man mano che i sistemi crescono in complessità, a volte emergono delle tensioni. Le necessità di chi _scrive_ i dati (ottimizzazione per la consistenza, regole di business complesse) e di chi li _legge_ (ottimizzazione per la velocità, viste aggregate per le UI) iniziano a divergere drasticamente. Tentare di servire entrambi con un unico modello può portare a compromessi, query inefficienti e complessità.

  

  

In questo capitolo, esploreremo due pattern avanzati, spesso usati in sinergia, che affrontano questa tensione di petto: **CQRS (Command Query Responsibility Segregation)** e **Event Sourcing**. Questi non sono strumenti da usare alla leggera, ma per i problemi giusti, offrono un livello di scalabilità, flessibilità e resilienza ineguagliabile.

  

  

---

  

  

### 15.1. Il Problema: Un Modello, Due Padroni

  

  

Il nostro aggregato `Viaggio`, con le sue entità e i suoi value objects, è ottimizzato per un compito: far rispettare gli invarianti di business e garantire la consistenza transazionale. È un modello perfetto per le **operazioni di scrittura**.

  

  

Ma cosa succede quando il nostro frontend SvelteKit ha bisogno di visualizzare una dashboard con una lista di tutti i viaggi dell'utente, mostrando per ognuno il nome, lo stato e il numero totale di tappe?

  

  

Con il nostro modello attuale, l'Application Service dovrebbe:

  

  

1. Chiamare `tripRepository.FindByOwnerID(...)` per caricare una lista di aggregati `Viaggio`.

  

2. Per ogni `Viaggio` caricato, l'intero aggregato, con tutte le sue `Tappe` e altri oggetti, viene idratato in memoria.

  

3. L'applicazione dovrebbe poi ciclare su questa lista e, per ogni `Viaggio`, contare le `Tappe` per ottenere il numero totale.

  

4. Infine, dovrebbe mappare questi dati in un DTO (Data Transfer Object) da inviare al frontend.

  

  

Questo approccio, sebbene funzionante, è inefficiente. Carichiamo una mole di dati (tutti i dettagli delle tappe) solo per calcolare un conteggio. Su larga scala, questo porta a un consumo eccessivo di memoria e a query lente. Il nostro modello, ottimizzato per la scrittura, non è ottimizzato per questa specifica lettura.

  

  

---

  

  

### 15.2. CQRS: Segregare Comandi e Query

  

  

Il **Command Query Responsibility Segregation (CQRS)** è un pattern architetturale che risolve questo problema introducendo una separazione netta tra il modello usato per modificare lo stato e quello usato per leggerlo.

  

  

> **Definizione**: **CQRS** è un principio che separa le operazioni che modificano i dati (**Comandi**) da quelle che li leggono (**Query**). Questo porta alla creazione di due modelli distinti: un **Write Model** ottimizzato per la logica di business e la consistenza, e uno o più **Read Models** ottimizzati per le interrogazioni della UI.

  

  

#### **Lo Stack dei Comandi (Write Side)**

  

  

- **Scopo**: Eseguire comandi, far rispettare le regole di business, garantire la consistenza.

  

- **Componenti**: Questo è il lato che abbiamo costruito finora! Contiene:

  

    - **Comandi**: Oggetti che rappresentano l'intenzione di modificare lo stato (es. `CreateTripCommand`, `AddStopCommand`).

  

    - **Command Handlers**: Simili ai nostri Application Services, ricevono un comando e orchestrano il caso d'uso.

  

    - **Modello di Dominio**: I nostri Aggregati, Entità e Value Objects ricchi.

  

    - **Repository**: Per persistere gli aggregati.

  

  

#### **Lo Stack delle Query (Read Side)**

  

  

- **Scopo**: Rispondere alle query in modo rapido ed efficiente.

  

- **Componenti**:

  

    - **Query**: Oggetti che rappresentano una richiesta di dati.

  

    - **Query Handlers**: Ricevono una query, interrogano il Read Model e restituiscono un DTO.

  

    - **Read Models**: Questo è il cuore del Read Side. Sono modelli di dati semplici, spesso "appiattiti" e **denormalizzati**, progettati su misura per una specifica vista della UI. Non contengono logica di business. Potrebbero essere semplici `struct` Go.

  

    - **Meccanismo di Persistenza**: Il Read Model può vivere in un database completamente separato e usare una tecnologia diversa (es. una tabella PostgreSQL, un documento Elasticsearch, una cache Redis).

  

  

#### **Sincronizzare i Modelli: Il Ruolo degli Eventi**

  

  

Quando un comando modifica il Write Model, come fa il Read Model a essere aggiornato? La risposta è la **comunicazione asincrona tramite eventi**.

  

  

1. Il Command Handler processa un comando e salva l'aggregato.

  

2. Subito dopo, pubblica un **Domain Event** (es. `TripCreated`, `StopAddedToTrip`) su un bus di eventi.

  

3. Un **Event Handler** (o _proiettore_) sottoscritto a quell'evento lo riceve.

  

4. L'Event Handler esegue una semplice operazione di aggiornamento sul Read Model (es. inserisce una nuova riga nella tabella dei riepiloghi dei viaggi, o incrementa un contatore).

  

  

Questo significa che il Read Model è **eventualmente consistente**. Per un breve istante, potrebbe non essere aggiornato, ma si sincronizzerà poco dopo. Per la stragrande maggioranza delle interfacce utente, questo è un compromesso perfettamente accettabile in cambio di enormi guadagni in performance e scalabilità.

  

  

---

  

  

### 15.3. Event Sourcing: La Storia come Unica Fonte di Verità

  

  

L'Event Sourcing (ES) è un pattern più radicale e potente, che si sposa magnificamente con CQRS.

  

  

> **Definizione**: L'**Event Sourcing** è un approccio alla persistenza in cui non si salva lo stato _attuale_ di un'entità, ma si persiste la **sequenza cronologica e immutabile di eventi** che hanno portato a quello stato. Lo stato attuale è un effetto collaterale, un calcolo derivato da questa storia.

  

  

Pensa al tuo estratto conto bancario. La banca non memorizza solo il tuo saldo finale. Memorizza ogni singola transazione: `+50€`, `+100€`, `-20€`. Il tuo saldo attuale è semplicemente la somma di tutte queste transazioni. Quelle transazioni sono gli eventi.

  

  

**Concetti Chiave:**

  

  

- **Event Store**: È il database specializzato (o una semplice tabella) che memorizza gli eventi. È una struttura _append-only_ (si può solo aggiungere, mai modificare o cancellare). Gli eventi sono fatti, e i fatti non si cambiano.

  

- **Ricostruzione dello Stato**: Per ottenere lo stato corrente di un aggregato, il repository legge l'intera sequenza di eventi per quell'ID dal'Event Store e li "riproduce" su un'istanza vuota dell'aggregato.

  

- **Eventi come Fonte di Verità**: L'Event Store diventa la fonte di verità assoluta e auditabile del sistema.

  

  

#### **Come Cambia il Nostro Aggregato `Viaggio`**

  

  

Per implementare l'Event Sourcing, il nostro aggregato deve cambiare leggermente.

  

  

1. **I metodi di comando non modificano lo stato, ma producono eventi.**

  

    Go

  

    ```go

  

    // Metodo di comando in un aggregato event-sourced

  

    func (t *Trip) AddStop(place Place, day int, notes string) (*StopAdded, error) {

  

        // 1. Validazione delle regole di business

  

        if t.status != TripStatusPlanning {

  

            return nil, errors.New("cannot add stop to a trip not in planning status")

  

        }

  

        // ... altre validazioni ...

  

        // 2. Se la validazione ha successo, crea un evento. NON modificare t.stops qui!

  

        event := &StopAdded{

  

            EventID: uuid.New(),

  

            TripID:  t.id,

  

            Place:   place,

  

            Day:     day,

  

            Notes:   notes,

  

        }

  

        return event, nil

  

    }

  

    ```

  

2. Si introduce un metodo Apply per modificare lo stato.

  

    Questo metodo viene usato internamente per applicare gli eventi (sia quelli nuovi che quelli storici durante la ricostruzione).

  

    Go

  

    ```go

  

    // Metodo Apply che effettivamente muta lo stato

  

    func (t *Trip) Apply(event Event) {

  

        switch e := event.(type) {

  

        case *TripCreated:

  

            t.id = e.TripID

  

            t.ownerID = e.OwnerID

  

            t.status = TripStatusPlanning

  

            // ...

  

        case *StopAdded:

  

            newStop := stop{

  

                place: e.Place,

  

                dayOfTrip: e.Day,

  

                notes: e.Notes,

  

            }

  

            t.stops = append(t.stops, newStop)

  

        }

  

    }

  

    ```

  

  

Il `Repository` ora non salva più lo stato, ma si limita ad accodare i nuovi eventi generati dall'aggregato nell'Event Store.

  

  

---

  

  

### 15.4. La Sinergia Perfetta: CQRS + Event Sourcing

  

  

Quando usati insieme, questi due pattern creano un'architettura incredibilmente potente e disaccoppiata.

  

  

- L'**Event Store** diventa il cuore del sistema.

  

- Il **Write Side** è il nostro aggregato event-sourced che produce eventi e li scrive nell'Event Store.

  

- Il **Read Side** è composto da uno o più _proiettori_ (event handler) che sono sottoscritti al flusso di eventi dell'Event Store. Ogni volta che un nuovo evento viene salvato, i proiettori lo ricevono e aggiornano le loro specifiche tabelle di lettura denormalizzate.

  

  

Questo significa che il Read Side è completamente disaccoppiato dal Write Side. Possiamo aggiungere nuove viste (nuovi Read Models) in qualsiasi momento, semplicemente creando un nuovo proiettore e facendogli processare la storia degli eventi dall'inizio. Non c'è bisogno di complesse migrazioni di dati.

  

  

---

  

  

### 15.5. Pro e Contro: Un Martello per Quali Chiodi?

  

  

Questi pattern sono il "martello pneumatico" della progettazione software. Potentissimi, ma non adatti per appendere un quadretto.

  

  

**CQRS:**

  

  

- 👍 **Pro**: Performance di lettura eccellenti, scalabilità indipendente, modelli più semplici e focalizzati.

  

- 👎 **Contro**: Complessità architetturale (due modelli, un bus di eventi), la consistenza eventuale richiede un cambio di mentalità e una gestione attenta.

  

- **Quando usarlo?** Quando i modelli di lettura e scrittura sono molto diversi, o quando le esigenze di scalabilità delle query sono elevate. **È un pattern che si può applicare anche solo a parti del sistema (es. solo per l'aggregato `Viaggio`), non deve essere per forza tutto o niente.**

  

  

**Event Sourcing:**

  

  

- 👍 **Pro**: Audit trail completo e immutabile (chi ha fatto cosa e quando?), capacità di debug eccezionali ("viaggiare nel tempo" per vedere lo stato in qualsiasi momento), flessibilità nel creare nuove proiezioni future.

  

- 👎 **Contro**: Complessità significativa (gestione dello store, riproduzione degli eventi, versioning degli schemi degli eventi, snapshot per le performance). È un cambiamento di paradigma radicale.

  

- **Quando usarlo?** Per i domini di business _core_ dove la storia e l'audit sono requisiti non funzionali critici (es. finanza, sanità, logistica).

  

  

Raccomandazione per "Where Should I Be?":

  

  

Per il nostro progetto, un approccio pragmatico è il migliore.

  

  

1. **Iniziare con un'architettura DDD/Clean standard.**

  

2. **Introdurre CQRS selettivamente**: Creare un Read Model `TripSummary` per la dashboard dei viaggi è un'ottima prima applicazione di CQRS, che porta benefici immediati senza stravolgere l'intero sistema.

  

3. **Valutare Event Sourcing con cautela**: Potrebbe essere overkill all'inizio. Ma se in futuro volessimo aggiungere funzionalità come "Annulla l'ultima modifica al viaggio" o "Mostra la cronologia completa delle modifiche di un itinerario", l'Event Sourcing diventerebbe la soluzione ideale.

  

  

---

  

  

### 15.6. Conclusioni: Un Nuovo Orizzonte di Possibilità

  

  

CQRS e Event Sourcing rappresentano un passo evolutivo oltre le tradizionali architetture CRUD. Ci costringono a pensare ai dati non solo come uno stato da sovrascrivere, ma come un flusso di eventi e intenzioni.

  

  

- **CQRS** ci permette di ottimizzare e scalare il nostro sistema in modi che un modello unificato non consente.

  

- **Event Sourcing** ci fornisce una fedeltà storica perfetta, trasformando la nostra applicazione in un sistema di registrazione a prova di manomissione.

  

  

Questi pattern chiudono la nostra esplorazione della progettazione tattica e architetturale. Con questi strumenti, siamo equipaggiati per affrontare domini di una complessità enorme. Nella **Parte IV**, alzeremo lo sguardo dal codice e dall'architettura di un singolo servizio per affrontare la **progettazione strategica**: come scomporre un grande problema di business in contesti gestibili e farli collaborare efficacemente.

  

  

---

  

# **Parte IV: Progettazione Strategica**

  

  

## Capitolo 16: Bounded Contexts

  

  

Benvenuti nella Parte IV del nostro viaggio. Finora ci siamo concentrati sulla **progettazione tattica**: abbiamo imparato a costruire modelli di dominio ricchi ed espressivi, con Aggregati, Entità e Value Objects, e a inserirli in un'architettura pulita. Abbiamo imparato a fare lo "zoom-in", a curare i dettagli del nostro codice per renderlo robusto e significativo.

  

  

Ora è il momento di fare "zoom-out". È il momento di alzare lo sguardo dal singolo modello e affrontare la sfida più grande nello sviluppo di software enterprise: **la gestione della complessità su larga scala**. I sistemi reali non sono composti da un unico, perfetto modello di dominio. Sono ecosistemi vasti, con aree di business diverse, team diversi e, soprattutto, linguaggi diversi.

  

  

In questa sezione, entreremo nel mondo della **progettazione strategica** del DDD. E il suo pattern fondamentale, il concetto che permette di dominare la complessità su larga scala, è il **Bounded Context** (Contesto Delimitato). Capire e applicare questo pattern è ciò che distingue un'architettura software ordinaria da una veramente strategica e resiliente.

  

  

---

  

  

### 16.1. Il Problema: L'Illusione di un Unico Modello Globale

  

  

Quando un'azienda cresce, la sua complessità cresce con essa. Consideriamo una grande piattaforma di e-commerce e pensiamo a un concetto apparentemente semplice come "Cliente" (Customer).

  

  

- Per il **Team Vendite**, un "Cliente" è definito dal suo storico ordini, dalle sue informazioni di spedizione e dai dettagli di fatturazione. La loro preoccupazione è processare un acquisto.

  

- Per il **Team Marketing**, un "Cliente" è un profilo con dati demografici, interessi, segmenti di appartenenza e una cronologia delle interazioni con le campagne pubblicitarie. La loro preoccupazione è la conversione e la fidelizzazione.

  

- Per il **Team Assistenza**, un "Cliente" è un utente con una cronologia di ticket di supporto, reclami e contatti telefonici. La loro preoccupazione è la risoluzione dei problemi.

  

- Per il **Team Spedizioni**, un "Cliente" è semplicemente un nome e un `Indirizzo` (un Value Object) a cui consegnare un pacco.

  

  

L'errore più comune e disastroso è tentare di creare un unico, monolitico modello `Cliente` che soddisfi le esigenze di tutti. Il risultato sarebbe un "mostro": una `struct` o una classe con decine e decine di campi, la maggior parte dei quali `nullable` o irrilevanti per la maggior parte dei casi d'uso. Questo "Mega-Cliente" diventa:

  

  

- **Incoerente**: Le regole che lo governano sono un miscuglio di logiche contraddittorie.

  

- **Fragile**: Una modifica richiesta dal team Marketing rischia di rompere una funzionalità critica del team Vendite.

  

- **Di Nessuno**: Nessun team ne ha la piena proprietà. Tutti hanno paura di toccarlo.

  

  

Il problema di fondo è che **un singolo modello unificato è un'illusione**. Il significato delle parole dipende dal contesto in cui vengono usate.

  

  

---

  

  

### 16.2. La Soluzione: Definire i Bounded Context

  

  

Il DDD risolve questo problema in modo radicale, introducendo il concetto di Bounded Context.

  

  

> **Definizione**: Un **Bounded Context** è un confine esplicito (linguistico e applicativo) all'interno del quale un particolare modello di dominio è coerente e ha un significato univoco. All'interno di questo confine, il **Linguaggio Ubiquo** è valido e non ambiguo.

  

  

Pensa a un Bounded Context come a una nazione. All'interno dei confini dell'Italia, la parola "Costituzione" si riferisce a un documento specifico con un significato preciso. Al di là del confine, in Francia, la stessa parola ("Constitution") si riferisce a un altro documento, con una storia e regole diverse. Il confine geografico delimita il contesto di validità del termine.

  

  

**Caratteristiche chiave di un Bounded Context:**

  

  

- **Confine Linguistico**: È il luogo dove un Linguaggio Ubiquo vive. Anzi, possiamo dire che esiste una **relazione 1:1 tra un Bounded Context e un Linguaggio Ubiquo**. Questo affina la nostra comprensione dal Capitolo 7: un linguaggio non è "ubiquo" in tutta l'azienda, ma è "ubiquo" _all'interno del suo contesto_.

  

- **Confine del Modello**: All'interno del contesto, il modello di dominio (con i suoi Aggregati, Entità, ecc.) è ottimizzato per risolvere uno specifico sotto-problema di business.

  

- **Confine di Consistenza**: Le regole di consistenza forte (invarianti degli aggregati) sono applicate rigorosamente all'interno del contesto. La consistenza tra contesti diversi è tipicamente gestita in modo più lasco (consistenza eventuale).

  

- **Confine del Team (spesso)**: Idealmente, un Bounded Context è di proprietà di un singolo team, che ha la piena autonomia di svilupparlo e farlo evolvere.

  

  

---

  

  

### 16.3. Identificare i Bounded Context in "Where Should I Be?"

  

  

Applichiamo questi principi per scomporre la nostra applicazione. Invece di pensare a un unico grande sistema, identifichiamo le sue capacità di business distinte.

  

  

#### **Contesto 1: `Identity & Access Context` (Identità e Accesso)** 👤

  

  

- **Responsabilità**: Gestire chi sono gli utenti e cosa possono fare. Si occupa di registrazione, login, gestione dei profili, ruoli e permessi.

  

- **Linguaggio e Modello**:

  

    - **`Utente`**: È l'entità centrale. Qui, è un modello ricco con attributi come `Email`, `HashedPassword`, `StatoVerifica`, `Ruoli`.

  

    - **`Profilo`**: Potrebbe contenere nome, cognome, avatar.

  

- **Obiettivo**: Sicurezza e gestione dell'identità.

  

  

#### **Contesto 2: `Trip Planning Context` (Pianificazione Viaggi)** 🗺️

  

  

- **Responsabilità**: È il cuore della nostra applicazione. Permette agli utenti di creare, modificare e gestire i loro itinerari di viaggio.

  

- **Linguaggio e Modello**:

  

    - **`Viaggio`**: È l'aggregato principale che abbiamo progettato nella Parte II.

  

    - **`Tappa`**, **`Luogo`**: Concetti centrali per la pianificazione.

  

    - **`Utente`**: Qui, il concetto di "Utente" è molto più semplice. Non ci interessano la sua password o la data di registrazione. Ci interessa solo il suo **`UserID`** (per collegarlo ai suoi viaggi) e forse il suo **`LivelloAbbonamento`** (un Value Object) per applicare regole come "un utente Free non può avere più di 3 viaggi attivi".

  

  

#### **Contesto 3: `Suggestions Context` (Suggerimenti)** ✨

  

  

- **Responsabilità**: Interagire con servizi di Intelligenza Artificiale (come OpenAI) per generare proposte di itinerari basate sulle richieste degli utenti.

  

- **Linguaggio e Modello**:

  

    - **`RichiestaSuggerimento`**: Un oggetto che cattura l'input dell'utente ("3 giorni a Parigi per amanti dell'arte").

  

    - **`PropostaDiItinerario`**: L'output strutturato dell'AI.

  

    - **`Viaggio`**: In questo contesto, il concetto di "Viaggio" non è un aggregato complesso, ma probabilmente solo un insieme di vincoli (destinazione, durata, interessi) da inviare all'AI.

  

  

#### **Contesto 4: `Billing Context` (Fatturazione) - Futuro** 💳

  

  

- **Responsabilità**: Gestire gli abbonamenti a pagamento, processare i pagamenti, generare fatture.

  

- **Linguaggio e Modello**:

  

    - **`Cliente`**: Qui l'utente diventa un "Cliente", un'entità con un `MetodoDiPagamento`, uno `StatoAbbonamento` e una cronologia di `Transazioni`.

  

    - **`Prodotto`**: Un'entità che rappresenta i piani tariffari ("Piano Premium Mensile").

  

    - Il concetto di `Viaggio` qui potrebbe non esistere affatto, o essere solo una stringa descrittiva su una fattura.

  

  

---

  

  

### 16.4. Bounded Context e Microservizi: Un Abbinamento Perfetto 

  

  

La progettazione strategica con i Bounded Context ci fornisce la mappa perfetta per una corretta scomposizione in microservizi.

  

  

> **La Regola d'Oro della Decomposizione**: Un microservizio dovrebbe essere l'implementazione di **un singolo Bounded Context**.

  

  

- **NON dividere un Bounded Context su più microservizi**: Se lo facessi, la comunicazione tra le parti del tuo modello di dominio, che dovrebbe essere in-process e fortemente consistente, diventerebbe una chiamata di rete, lenta e inaffidabile. Questo porta a problemi come le transazioni distribuite, un campo minato da evitare a tutti i costi.

  

- **NON mettere più Bounded Context in un unico microservizio**: Se lo facessi, ricreeresti un "mini-monolite". I modelli e i linguaggi diversi si mescolerebbero, le logiche si intreccerebbero e perderesti i vantaggi dell'autonomia e della manutenibilità.

  

  

La nostra architettura fisica, quindi, rifletterà direttamente il nostro design strategico:

  

  

- `identity-access-service` (implementa l'Identity & Access Context)

  

- `trip-planning-service` (implementa il Trip Planning Context)

  

- `suggestions-service` (implementa il Suggestions Context)

  

  

Questo approccio ci dà una **giustificazione di business** per i nostri confini architetturali. Non stiamo creando microservizi "perché sono di moda", ma perché il nostro dominio di business si scompone naturalmente in queste aree di responsabilità.

  

  

---

  

  

### 16.5. I Vantaggi di un Design Orientato ai Contesti

  

  

Progettare esplicitamente attorno ai Bounded Context sblocca benefici enormi:

  

  

- **Autonomia dei Team**: Il team "Planning" può scegliere le tecnologie e le strategie di deployment migliori per il suo servizio, senza dover coordinarsi costantemente con il team "Identity".

  

- **Chiarezza del Modello**: Ogni modello di dominio è più piccolo, più semplice e focalizzato su un unico scopo. Gli sviluppatori possono tenerlo interamente in testa.

  

- **Evoluzione Indipendente**: Possiamo sostituire completamente l'implementazione del `suggestions-service` (magari passando da OpenAI a un altro provider) senza che nessun altro servizio se ne accorga.

  

- **Confini Espliciti**: Ci costringe a pensare attentamente a come i diversi contesti comunicano tra loro, portando a contratti (API) più puliti e intenzionali.

  

  

---

  

  

### 16.6. Conclusioni: Dalla Tattica alla Strategia

  

  

Il Bounded Context è il mattone fondamentale della progettazione strategica. È lo strumento che ci permette di applicare tutti i pattern tattici che abbiamo imparato (Aggregati, Entità, ecc.) su una scala più ampia, evitando di creare un unico, ingestibile "Grande Pasticcio di Fango".

  

  

Comprendere e identificare i contesti delimitati significa passare da semplice programmatore ad **architetto del software**. Significa imparare a vedere il sistema non come un'unica massa informe, ma come una federazione di modelli specialistici e collaborativi.

  

  

Ora che sappiamo _cosa_ sono i Bounded Context e _perché_ sono importanti, i prossimi capitoli risponderanno a due domande cruciali:

  

  

1. **Come possiamo scoprire questi confini in modo collaborativo ed efficace?** La risposta è l'**Event Storming** (Capitolo 17).

  

2. **Come facciamo a far comunicare tra loro questi contesti una volta che li abbiamo definiti?** La risposta è il **Context Mapping** (Capitolo 18).

  

  

---

  

## Capitolo 17: Event Storming: Dalla Specifica al Design

  

  

Nel capitolo precedente, abbiamo introdotto il Bounded Context come il pilastro della progettazione strategica, lo strumento che ci permette di scomporre un dominio complesso in parti gestibili. Questo solleva una domanda da un milione di dollari: **come troviamo questi confini?** Come facciamo a sapere dove finisce un contesto e ne inizia un altro? Basarsi sull'intuito o su una comprensione superficiale del business è una ricetta per il disastro.

  

  

La risposta non si trova in un documento di 100 pagine o in una serie infinita di riunioni. Si trova in un workshop dinamico, visivo e intensamente collaborativo chiamato **Event Storming**.

  

  

L'Event Storming è una tecnica, inventata da Alberto Brandolini, che sta rivoluzionando il modo in cui i team esplorano i domini di business complessi. Non è una riunione, è un processo di scoperta collettiva. È il modo più efficace che conosciamo per colmare il divario tra gli esperti di dominio e gli sviluppatori, trasformando la conoscenza del business direttamente in un progetto software. In questo capitolo, impareremo a condurre un workshop di Event Storming per mappare il dominio della nostra applicazione "Where Should I Be?".

  

  

---

  

  

### 17.1. Il Problema: La Conoscenza Chiusa nei Silos

  

  

Il modo tradizionale di raccogliere i requisiti è spesso rotto. Gli analisti di business parlano con gli stakeholder, scrivono lunghe specifiche e le passano agli sviluppatori. Gli sviluppatori le leggono, le interpretano (spesso in modo errato), fanno domande e il ciclo si ripete. La conoscenza rimane intrappolata in "silos": la testa degli esperti, i documenti Word, i ticket di Jira.

  

  

Questo processo è lento, inefficiente e pieno di rischi di fraintendimento. L'Event Storming rompe questi silos. Mette tutte le persone chiave nella stessa stanza (fisica o virtuale) con un obiettivo comune: creare una narrazione visibile e condivisa di come funziona il business.

  

  

**I Principi Chiave:**

  

  

- **La Collaborazione è Essenziale**: Riunisce persone con prospettive diverse: sviluppatori, esperti di dominio (le persone più importanti nella stanza), product manager, designer UX, tester.

  

- **La Visualizzazione è Potere**: Si usa una superficie di modellazione illimitata (un lungo rotolo di carta su un muro o una lavagna virtuale infinita come Miro) e post-it colorati. L'atto fisico di scrivere e spostare i post-it è parte integrante del processo.

  

- **Focus sugli Eventi di Dominio**: Il punto di partenza non sono i dati o le funzionalità, ma gli **eventi**: le cose che accadono nel business e che sono importanti per gli esperti di dominio.

  

  

---

  

  

### 17.2. La Leggenda dei Post-it: Il Linguaggio dell'Event Storming 🎨

  

  

L'Event Storming ha un suo linguaggio visivo ben definito. Ogni colore di post-it ha un significato preciso. Imparare questa "leggenda" è il primo passo.

  

  

**🟧 Evento di Dominio (Arancione)**

  

  

- **Cos'è**: Il protagonista assoluto. Un fatto accaduto nel passato che è di interesse per il business.

  

- **Grammatica**: Sempre al **tempo passato**, in forma di participio passato. Es. "**Viaggio Creato**", "**Pagamento Ricevuto**", "**Utente Registrato**".

  

- **Perché**: Costringe a pensare a fatti concreti e immutabili, non a desideri o processi.

  

  

**🟦 Comando (Azzurro)**

  

  

- **Cos'è**: L'intenzione di un utente o di un altro sistema che scatena un evento. È la causa.

  

- **Grammatica**: Un **verbo all'imperativo** o all'infinito. Es. "**Crea Viaggio**", "**Aggiungi Tappa**".

  

  

**🟨 Aggregato (Giallo)**

  

  

- **Cos'è**: Il "sostantivo" del nostro dominio. L'oggetto di business che riceve un comando, applica le regole e, se tutto va bene, emette uno o più eventi. Questi sono i nostri candidati **Aggregati** del DDD.

  

- **Grammatica**: Un **nome**. Es. "**Viaggio**", "**Utente**".

  

  

**🟩 Read Model / Vista (Verde)**

  

  

- **Cos'è**: L'informazione che viene presentata a un utente per aiutarlo a prendere una decisione (e quindi a lanciare un comando). È la nostra UI.

  

- **Grammatica**: Una descrizione della vista. Es. "**Dashboard dei Viaggi**", "**Modulo di Registrazione**".

  

  

**🟪 Sistema Esterno (Viola)**

  

  

- **Cos'è**: Qualsiasi dipendenza esterna al nostro sistema: un servizio di terze parti, un'altra API aziendale, un sistema legacy.

  

- **Grammatica**: Il nome del sistema. Es. "**Gateway di Pagamento Stripe**", "**API di OpenAI**".

  

  

**🟥 Policy / Reazione (Rosa/Magenta)**

  

  

- **Cos'è**: La "colla" che lega i processi. È la logica del tipo "Ogni volta che... Allora...". Una policy ascolta un evento e scatena un nuovo comando.

  

- **Grammatica**: `Ogni volta che [Evento], allora [Comando]`. Es. "`Ogni volta che Utente Registrato, allora Invia Email di Benvenuto`".

  

  

---

  

  

### 17.3. Le Fasi di un Workshop di Event Storming: Mappiamo "Where Should I Be?"

  

  

L'Event Storming non è una sessione caotica, ma un processo strutturato in fasi, ognuna con un obiettivo specifico. Simuliamo un workshop per la nostra applicazione.

  

  

#### **Fase 1: Big Picture - La Tempesta di Eventi (Solo Post-it Arancioni)**

  

  

- **Obiettivo**: Generare una comprensione di alto livello del dominio, senza preoccuparsi dei dettagli.

  

- **Processo**:

  

    1. Il facilitatore riunisce tutti davanti alla superficie di modellazione vuota.

  

    2. La regola è semplice: "Per i prossimi 15 minuti, chiunque può scrivere su un post-it arancione qualsiasi **evento di dominio** che gli viene in mente relativo alla nostra applicazione e attaccarlo al muro".

  

    3. Inizia la "tempesta". I partecipanti scrivono e attaccano post-it senza un ordine preciso: `Utente Registrato`, `Viaggio Creato`, `Suggerimento Generato dall'AI`, `Tappa Aggiunta al Viaggio`, `Abbonamento Premium Acquistato`, `Password Reimpostata`, `Recensione Pubblicata`, `Viaggio Condiviso`.

  

    4. Il facilitatore fa rispettare la regola del **tempo passato**. Se qualcuno scrive "Pianificare Viaggio", viene corretto in "**Viaggio Pianificato**".

  

    5. Dopo la tempesta iniziale, il gruppo collabora per rimuovere i duplicati e tentare di ordinare gli eventi su una linea temporale approssimativa da sinistra a destra.

  

  

Il risultato è una prima, grezza narrazione del flusso di business, vista attraverso gli occhi degli esperti.

  

  

#### **Fase 2: Enforce the Process - Aggiungere le Cause (Comandi e Attori)**

  

  

- **Obiettivo**: Capire cosa scatena ogni evento.

  

- **Processo**: Il facilitatore si sposta lungo la timeline e, per ogni evento arancione, chiede al gruppo: "**Cosa ha causato questo evento?**".

  

    - Per l'evento `Viaggio Creato` (arancione), la causa è il comando `Crea Viaggio` (blu).

  

    - **Chi** ha eseguito questo comando? Un `Utente` (un piccolo post-it giallo per l'attore).

  

    - **Quale informazione** ha visto l'utente per poter eseguire questo comando? La `Dashboard dei Viaggi` (verde).

  

    - Si procede così per tutti gli eventi, aggiungendo post-it blu e verdi, e iniziando a vedere le interazioni utente-sistema.

  

  

#### **Fase 3: Identificare gli Aggregati - Trovare i Sostantivi (Post-it Gialli)**

  

  

- **Obiettivo**: Scoprire i nostri aggregati di dominio.

  

- **Processo**: Ora che abbiamo delle catene `Comando -> Evento`, chiediamo: "**Chi è responsabile di eseguire questo comando e generare questo evento?**".

  

    - I comandi `Crea Viaggio`, `Aggiungi Tappa`, `Completa Viaggio` vengono naturalmente raggruppati attorno a un post-it giallo più grande: **Viaggio**.

  

    - I comandi `Registra Utente`, `Aggiorna Profilo` si raggruppano attorno a **Utente**.

  

    - I comandi `Genera Suggerimento` si raggruppano attorno a **Motore di Suggerimenti**.

  

  

**Questo è il momento "Aha!" del workshop.** I cluster che si formano spontaneamente sulla parete rappresentano i nostri candidati **Aggregati**. Lo spazio vuoto tra un cluster e l'altro è un forte indicatore di un confine.

  

  

#### **Fase 4: Identificare i Bounded Context - Disegnare i Confini**

  

  

- **Obiettivo**: Formalizzare i confini strategici del nostro sistema.

  

- **Processo**:

  

    1. Facciamo un passo indietro e osserviamo l'intera parete.

  

    2. Cerchiamo le "fratture" naturali nel modello. Dove cambia il linguaggio? Dove i cluster di aggregati sembrano parlare di cose diverse?

  

    3. Noteremo che il gruppo di post-it relativi a `Utente`, `Password`, `Registrazione` è un mondo a sé.

  

    4. Il gruppo relativo a `Viaggio`, `Tappa`, `Luogo` è un altro mondo, il nostro core domain.

  

    5. Il gruppo relativo a `Suggerimento`, `Prompt AI` e l'interazione con il sistema esterno `API OpenAI` (viola) è un terzo mondo.

  

    6. Con un pennarello, **disegniamo fisicamente delle linee sulla parete** per separare questi gruppi.

  

    7. Diamo un nome a ogni area delimitata, usando il Linguaggio Ubiquo che è emerso: **Identity & Access Context**, **Trip Planning Context**, **Suggestions Context**.

  

  

Abbiamo appena scoperto i nostri Bounded Context, non basandoci sulla tecnologia, ma direttamente dalla narrazione del business.

  

  

---

  

  

### 17.4. Dal Workshop al Codice: Tradurre la Mappa

  

  

L'output di un Event Storming non è solo una parete colorata, è un vero e proprio **blueprint per il nostro design software**:

  

  

- I **Bounded Context** (le aree disegnate) diventano i nostri **microservizi** o i moduli di alto livello della nostra applicazione.

  

- Gli **Aggregati** (i post-it gialli) diventano le nostre `struct` Aggregate Root nel codice Go.

  

- I **Comandi** (blu) diventano i metodi pubblici sui nostri aggregati e sui nostri Application Services.

  

- Gli **Eventi di Dominio** (arancioni) diventano le `struct` che pubblicheremo, ideali per un'architettura CQRS o event-driven.

  

- Le **Policy** (rosa) diventano i nostri Event Handler asincroni.

  

- I **Read Models** (verdi) diventano i DTO e le viste che i nostri endpoint API restituiranno al frontend.

  

- Il **Linguaggio Ubiquo** è letteralmente scritto sui post-it. Abbiamo creato un primo glossario condiviso e validato da tutto il team.

  

  

---

  

  

### 17.5. Consigli Pratici e Errori da Evitare

  

  

- ✅ **Ottenere le persone giuste**: Un Event Storming senza esperti di dominio è inutile. La loro conoscenza è il carburante del workshop.

  

- ✅ **Usare uno spazio illimitato**: La creatività ha bisogno di spazio. Un muro lungo o una lavagna virtuale infinita sono essenziali.

  

- ✅ **Il facilitatore è cruciale**: Deve guidare il processo, fare le domande giuste e mantenere la conversazione focalizzata sul business, non sulla tecnologia.

  

- ❌ **Non discutere di tecnologia**: "Useremo PostgreSQL o DynamoDB?" è la domanda sbagliata in questa fase. L'Event Storming è agnostico rispetto alla tecnologia.

  

- ❌ **Non cercare la perfezione subito**: L'inizio è caotico per design. Abbracciate il caos iniziale; l'ordine emergerà.

  

- ❌ **Non avere fretta**: Un buon Event Storming può richiedere da mezza giornata a più giorni, a seconda della complessità del dominio. È un investimento, non un costo.

  

  

---

  

  

### 17.6. Conclusioni: Imparare Insieme, Progettare Meglio

  

  

L'Event Storming è una delle pratiche più trasformative che un team possa adottare. Non è solo un modo per raccogliere requisiti, ma una piattaforma per l'**apprendimento collaborativo**. Costringe sviluppatori ed esperti di business a costruire un linguaggio e una comprensione condivisi, mattone dopo mattone (o post-it dopo post-it).

  

  

Fornisce un percorso chiaro e visuale per passare da un'idea di business astratta a una mappa concreta della nostra architettura software, basata sui confini naturali del dominio stesso.

  

  

Ora che abbiamo scoperto i nostri Bounded Context, siamo pronti per l'ultimo passo della progettazione strategica: definire come questi contesti interagiranno tra loro. Questo è l'argomento del prossimo capitolo, il **Context Mapping**.

  

  

---

  

## Capitolo 18: Context Mapping

  

  

Nei capitoli precedenti, abbiamo compiuto il passo fondamentale dello "zoom-out". Abbiamo imparato a scomporre il nostro complesso dominio in **Bounded Context** (Capitolo 16) e abbiamo scoperto una tecnica potente come l'**Event Storming** (Capitolo 17) per identificare questi confini in modo collaborativo.

  

  

Il risultato è un'architettura che non è più un monolite informe, ma un arcipelago di "isole", ognuna con il proprio modello, il proprio linguaggio e la propria autonomia. Questa separazione è un'enorme vittoria. Ma nessuna applicazione reale è un insieme di isole disconnesse. Per fornire valore di business, questi contesti devono comunicare. Il `Trip Planning Context` deve sapere chi è l'utente dall'`Identity & Access Context`. Il `Suggestions Context` deve ricevere input dall'utente per generare proposte.

  

  

Senza una guida, le integrazioni tra questi contesti possono diventare un groviglio caotico di dipendenze, un "Grande Pasticcio di Fango Distribuito". Per evitare questo, il DDD ci offre un ultimo, potente strumento strategico: il **Context Mapping** (Mappatura dei Contesti).

  

  

---

  

  

### 18.1. Cos'è una Context Map? 🗺️

  

  

> **Definizione**: Una **Context Map** è un documento o un diagramma che visualizza le relazioni e i modelli di integrazione tra i diversi Bounded Context di un sistema. È la "mappa politica" del nostro panorama software.

  

  

Se i Bounded Context sono le nazioni del nostro mondo software, la Context Map è l'atlante che mostra:

  

  

- I **confini** tra le nazioni.

  

- Le **rotte commerciali** (le API e i flussi di eventi).

  

- I **trattati diplomatici** (i contratti e le responsabilità tra i team).

  

- Le **relazioni di potere** (chi dipende da chi).

  

  

L'obiettivo di una Context Map non è solo documentare le integrazioni esistenti, ma **progettarle intenzionalmente**. Ci costringe a porci domande strategiche: "Qual è il modo migliore per far parlare il Contesto A con il Contesto B? Quali sono i costi e i benefici di un'integrazione stretta rispetto a una lasca?".

  

  

Per la nostra applicazione "Where Should I Be?", una prima bozza di mappa potrebbe assomigliare a questa:

  

  

**Da cambiare con una foto**

  

```

  

                                      +--------------------------+

  

  [Frontend SvelteKit] --(REST/API)--> |   API Gateway            |

  

                                      +-----------+--------------+

  

                                                  |

  

         +----------------------------------------+------------------------------------------+

  

         | (gRPC)                                 | (gRPC)                                   |

  

         v                                        v                                          v

  

+----------------------+           +-------------------------+                      +---------------------+

  

| Identity & Access    | --(OHS)-->|   Trip Planning         | --(ACL, Conformist)--> | Suggestions         |

  

| Context              |           |   Context               |                      | Context             |

  

| (Team A - Supplier)  |           |   (Team B - Customer)   |                      | (Team B)            |

  

+----------------------+           +-------------------------+                      +----------+----------+

  

                                                                                                |

  

                                                                                                | (ACL, Conformist)

  

                                                                                                v

  

                                                                                    +---------------------+

  

                                                                                    |    OpenAI API       |

  

                                                                                    | (External System)   |

  

                                                                                    +---------------------+

  

```

  

  

Questa mappa, anche se semplice, è ricca di informazioni strategiche. Usa termini come `OHS`, `ACL`, `Conformist` che rappresentano specifici **pattern di integrazione**. Esploriamoli in dettaglio. 

  

  

---

  

  

### 18.2. I Pattern di Mappatura dei Contesti

  

  

Eric Evans, nel suo libro, ha definito un catalogo di pattern per descrivere le relazioni tra contesti. Li possiamo raggruppare in categorie logiche.

  

  

#### **A. Pattern di Collaborazione Stretta**

  

  

Questi pattern si usano quando due contesti sono legati a doppio filo dal successo del business.

  

  

**🤝 Partnership**

  

  

- **Descrizione**: Due team, che gestiscono due contesti diversi, devono collaborare intensamente per realizzare una funzionalità. Il successo di uno dipende strettamente dal successo dell'altro. Non c'è una chiara relazione upstream/downstream; sono partner alla pari.

  

- **Quando usarlo**: Quando la logica di business attraversa intrinsecamente i confini dei due contesti e richiede un coordinamento continuo.

  

- **Esempio in "Where Should I Be?"**: Immaginiamo di aggiungere un `Booking Context` per le prenotazioni. Il `Trip Planning Context` e il `Booking Context` sarebbero in una relazione di **Partnership**. È inutile pianificare un viaggio se non si possono prenotare le attività, ed è impossibile prenotare senza un piano. I due team dovrebbero definire le API di integrazione insieme, con riunioni frequenti e test di integrazione condivisi.

  

- **Costo**: Alta frizione comunicativa, richiede un grande sforzo di coordinamento.

  

  

** Shared Kernel (Nucleo Condiviso)**

  

  

- **Descrizione**: È il pattern di integrazione più forte e pericoloso. I due team si accordano per condividere un piccolo sottoinsieme del modello di dominio (codice, librerie, talvolta anche tabelle del database).

  

- **Quando usarlo**: **Con estrema cautela!** Da usare solo per parti del dominio molto stabili e veramente generiche.

  

- **Esempio in "Where Should I Be?"**: Potremmo decidere di creare una libreria Go condivisa, `internal/kernel`, che contiene solo le definizioni dei nostri ID tipizzati (`identity.TripID`, `identity.UserID`) e magari qualche Value Object fondamentale. Poiché questi tipi sono stabili e usati da più contesti, condividerli potrebbe ridurre la duplicazione.

  

- **Costo**: Altissimo accoppiamento. Qualsiasi modifica allo Shared Kernel richiede il coordinamento e il re-deployment di tutti i contesti che lo utilizzano. Va contro il principio di autonomia dei microservizi. **Usatelo con parsimonia, se non mai.**

  

  

---

  

  

#### **B. Pattern Upstream/Downstream**

  

  

Questi sono i pattern più comuni e descrivono una relazione di dipendenza, dove un contesto **downstream** (a valle) consuma le funzionalità di un contesto **upstream** (a monte).

  

  

**👑 Customer-Supplier (Cliente-Fornitore)**

  

  

- **Descrizione**: Una relazione di potere bilanciata. Il team downstream è un "Cliente" che ha esigenze specifiche. Il team upstream è il "Fornitore" che cerca di soddisfare queste esigenze. Il cliente può influenzare la roadmap del fornitore.

  

- **Quando usarlo**: È la relazione ideale tra team interni a una stessa organizzazione.

  

- **Esempio in "Where Should I Be?"**: La relazione tra `Trip Planning` (Cliente) e `Identity & Access` (Fornitore) è di tipo Customer-Supplier. Il team di Planning ha bisogno di sapere il livello di abbonamento di un utente. Può quindi "commissionare" al team Identity un endpoint API specifico che fornisca questa informazione in un formato comodo. Il team Identity darà priorità a questa richiesta per sbloccare il team a valle.

  

  

** Conformist (Conformista)**

  

  

- **Descrizione**: Una relazione di potere sbilanciata. Il team downstream si adatta completamente e senza discutere al modello del team upstream. Non ha alcun potere per influenzarne le decisioni.

  

- **Quando usarlo**: Quando si integra con un sistema esterno o legacy su cui non si ha alcun controllo, o quando è più conveniente adattarsi che negoziare.

  

- **Esempio in "Where Should I Be?"**: Il nostro `Suggestions Context` è un **Conformista** nei confronti dell'**API di OpenAI**. Non possiamo chiedere a OpenAI di cambiare il formato della loro risposta per farci un favore. Dobbiamo accettare il loro modello così com'è e adattare il nostro codice.

  

  

**🛡️ Anti-Corruption Layer (ACL - Strato Anti-Corruzione)**

  

  

- **Descrizione**: Questo non è un pattern di relazione, ma un pattern di implementazione sul lato **downstream**. È un meccanismo di difesa. L'ACL è un componente software (un adattatore, un facade) che traduce il modello del contesto upstream in un modello più appropriato per il proprio dominio, proteggendolo da influenze esterne "corrotte" o scomode.

  

- **Quando usarlo**: **Quasi sempre in una relazione Conformist!** È essenziale per mantenere l'integrità del proprio modello di dominio.

  

- **Esempio in "Where Should I Be?"**: Quando il `Suggestions Context` riceve una risposta complessa e magari disordinata dall'API di OpenAI, non permette a quella struttura dati di "inquinare" il suo dominio. Ha un adattatore, l'**ACL**, il cui unico compito è prendere quella risposta grezza e tradurla nel nostro pulito oggetto di dominio `PropostaDiItinerario`.

  

    Go

  

    ```go

  

    // internal/adapters/gateway/openai/translator.go

  

    package openai

  

    // La risposta grezza dell'API esterna

  

    type OpenAIChatCompletion struct { /* ... campi complessi ... */ }

  

    // Il nostro pulito oggetto di dominio

  

    import "where-should-i-be/internal/domain/suggestions"

  

    // L'ACL è questo traduttore.

  

    type Translator struct {}

  

    func (t *Translator) ToItineraryProposal(rawResponse OpenAIChatCompletion) (*suggestions.ItineraryProposal, error) {

  

        // Logica di parsing e traduzione per mappare

  

        // la risposta grezza al nostro modello di dominio.

  

        // ...

  

        return &proposal, nil

  

    }

  

    ```

  

  

**🏛️ Open Host Service (OHS - Servizio Pubblico Aperto)**

  

  

- **Descrizione**: Il contesto upstream progetta e pubblica un'API pensata per essere un "servizio pubblico" per l'intera organizzazione. L'API è ben documentata, stabile, e cerca di essere il più generica possibile per servire un'ampia gamma di consumatori.

  

- **Quando usarlo**: Per contesti che forniscono funzionalità fondamentali e trasversali.

  

- **Esempio in "Where Should I Be?"**: L'`Identity & Access Context` dovrebbe esporre un **Open Host Service**. Qualsiasi nuovo servizio che aggiungeremo in futuro avrà probabilmente bisogno di autenticare un utente o di recuperarne l'ID. L'API di questo contesto (che sia REST o gRPC) deve essere trattata come un prodotto pubblico e stabile.

  

  

---

  

  

#### **C. Pattern di Separazione**

  

  

**🚧 Separate Ways (Vie Separate)**

  

  

- **Descrizione**: Il pattern più semplice: i due contesti non comunicano affatto. Non c'è integrazione.

  

- **Quando usarlo**: Quando non c'è alcuna ragione di business per cui due contesti debbano interagire.

  

- **Esempio in "Where Should I Be?"**: Se avessimo un contesto per la gestione del blog aziendale (`ContentContext`), questo vivrebbe probabilmente in **Separate Ways** rispetto al `Trip Planning Context`. L'integrazione tra loro non è necessaria e aggiungerebbe solo complessità.

  

- **Costo**: Zero costi di integrazione. A volte, la migliore integrazione è nessuna integrazione.

  

  

---

  

  

### 18.3. Creare e Mantenere una Context Map

  

  

Una Context Map non è un artefatto da creare una volta e poi dimenticare. È un documento vivo che guida le decisioni architetturali.

  

  

- **Creazione**: Il primo draft di una Context Map è un output naturale di un workshop di **Event Storming**. Le linee che disegniamo sulla parete per separare i contesti sono i confini sulla nostra mappa.

  

- **Formato**: Può essere un semplice diagramma su una pagina wiki, un file nella documentazione del progetto, o un diagramma creato con strumenti come C4 Model. L'importante è che sia **visibile e accessibile a tutti i team**.

  

- **Manutenzione**: La mappa dovrebbe essere rivista periodicamente (es. ogni trimestre) o ogni volta che si propone una nuova integrazione tra servizi. Chiedersi "Quale pattern di mapping useremo qui?" dovrebbe diventare una prassi standard.

  

  

---

  

  

### 18.4. Conclusioni: La Mappa per il Successo Strategico

  

  

Se i Bounded Context ci aiutano a dividere per regnare (_divide et impera_), il Context Mapping ci insegna come governare i regni che abbiamo creato. È il passo finale e cruciale della progettazione strategica.

  

  

Senza una mappa esplicita, le integrazioni tendono a diventare un groviglio di dipendenze accidentali. Con una mappa, ogni connessione è **intenzionale**, ogni relazione è definita e ogni team conosce le proprie responsabilità. Questo ci permette di:

  

  

- **Scegliere la giusta strategia di integrazione** per ogni situazione.

  

- **Gestire le dipendenze politiche e organizzative** tra i team.

  

- **Prevenire l'accoppiamento indesiderato** e proteggere l'autonomia dei nostri servizi.

  

- **Costruire un ecosistema software** che non è solo un insieme di parti, ma un tutto coerente e collaborativo.

  

  

Con questo capitolo, si conclude la nostra immersione nella progettazione strategica. Abbiamo imparato a vedere il "quadro generale". Nelle prossime parti del libro, torneremo a fare zoom-in, armati di questa nuova visione, per implementare i dettagli tecnici, come le API e la persistenza, in modo ancora più robusto e consapevole.

  

  

---

  

# **Parte V: Integrazione e API Robuste**

  

  

## Capitolo 19: OpenAPI 3.1: Il Contratto tra Frontend e Backend

  

  

Nelle parti precedenti, abbiamo dedicato un'enorme quantità di energia a progettare e costruire il nostro backend. Abbiamo un dominio ricco e protetto da una Clean Architecture, con confini chiari tra i Bounded Context. Il nostro sistema interno è un'opera di ingegneria di cui essere fieri. Ma ora, dobbiamo esporlo al mondo. Dobbiamo creare un'interfaccia, un'API, che permetta al nostro frontend SvelteKit di interagire con tutta la potenza che abbiamo costruito.

  

  

Come gestiamo questa interfaccia critica? In molti progetti, la risposta è: "in modo caotico". Un developer backend crea un endpoint, ne comunica i dettagli su Slack o a voce, e il developer frontend prova a usarlo. Quando qualcosa cambia, tutto si rompe. Questo approccio informale è una delle maggiori fonti di frizione, bug e ritardi nello sviluppo software.

  

  

In questo capitolo, introdurremo un approccio professionale e disciplinato: il **design API-first**. Impareremo a usare la **Specifica OpenAPI (OAS)** non solo come strumento di documentazione, ma come un vero e proprio **contratto legalmente vincolante** tra il frontend e il backend. È la singola fonte di verità che guiderà lo sviluppo, abiliterà l'automazione e garantirà una collaborazione fluida.

  

  

---

  

  

### 19.1. Il Problema: Deriva delle API e Accordi Verbali

  

  

Senza un contratto formale, il confine tra frontend e backend è governato da accordi verbali e documentazione sparsa che diventa inevitabilmente obsoleta. Questo porta a problemi noti come **API Drift** (deriva dell'API), dove l'implementazione effettiva dell'API si allontana nel tempo da quella che era la sua specifica originale.

  

  

Consideriamo un dialogo tipico:

  

  

- **Backend Dev**: "Ho creato l'endpoint `POST /trips`. Manda un JSON con `name`, `startDate` e `endDate`."

  

- **Frontend Dev**: (Implementa la chiamata).

  

- _(Due settimane dopo)_ **Backend Dev**: (Per coerenza con il database) "Ho rinominato `startDate` in `start_date`." (Dimentica di comunicarlo).

  

- **Frontend Dev**: "L'applicazione è rotta! La creazione dei viaggi non funziona più."

  

  

Questa scenetta comica è la triste realtà di molti team. Il problema non è tecnico, ma di processo e comunicazione. La soluzione è smettere di parlare di API in modo informale e iniziare a usare un linguaggio formale, preciso e leggibile sia dagli esseri umani che dalle macchine: la Specifica OpenAPI.

  

  

---

  

  

### 19.2. Cos'è la Specifica OpenAPI (OAS)? 📜

  

  

> **Definizione**: La **Specifica OpenAPI** (precedentemente nota come Swagger) è uno standard aperto, agnostico rispetto al linguaggio, per descrivere, documentare e consumare API RESTful. Definisce un formato (YAML o JSON) che permette a macchine e umani di comprendere le capacità di un servizio senza accedere al codice sorgente.

  

  

Un file OpenAPI è il **contratto**. Descrive ogni singolo aspetto della nostra API:

  

  

- **Endpoint disponibili**: I percorsi (es. `/users/{userId}/trips`) e i metodi HTTP (GET, POST, DELETE, etc.).

  

- **Parametri**: I parametri di percorso (`{userId}`), di query, di header.

  

- **Body delle Richieste**: La struttura esatta dei dati inviati con le richieste POST o PUT.

  

- **Risposte**: Tutte le possibili risposte che un endpoint può restituire, inclusi i codici di stato (200, 201, 404, 500) e la struttura dei dati di risposta.

  

- **Schemi di Sicurezza**: Come l'API è protetta (es. JWT Bearer Token, OAuth2), un punto che si lega direttamente al nostro Capitolo 4 su AWS Cognito.

  

- **Schemi dei Dati (Schemas)**: La definizione riutilizzabile di tutti gli oggetti dati scambiati (es. `Trip`, `User`, `ErrorResponse`).

  

  

---

  

  

### 19.3. Progettare il Contratto per "Where Should I Be?"

  

  

Adottiamo un approccio **API-first**: progettiamo il contratto in un file `api.yaml` _prima_ di scrivere una singola riga di codice di implementazione. Questo costringe i team a concordare il "cosa" prima di perdersi nel "come".

  

  

Creiamo una porzione della nostra specifica per l'endpoint `GET /trips/{tripId}`.

  

  

YAML

  

  

```yaml

  

# api.yaml

  

openapi: 3.1.0 # Specifichiamo la versione dello standard

  

info:

  

  title: "Where Should I Be? API"

  

  version: "1.0.0"

  

  description: API per la pianificazione di viaggi intelligenti.

  

  

servers:

  

  - url: https://api.whereshouldibe.com/v1

  

    description: Production Server

  

  - url: http://localhost:8080/v1

  

    description: Local Development Server

  

  

paths:

  

  /trips/{tripId}:

  

    get:

  

      summary: "Recupera i dettagli di un viaggio specifico"

  

      tags:

  

        - Trips

  

      security:

  

        - bearerAuth: [] # Applichiamo lo schema di sicurezza definito sotto

  

      parameters:

  

        - name: tripId

  

          in: path

  

          required: true

  

          description: "L'ID del viaggio da recuperare"

  

          schema:

  

            type: string

  

            format: uuid

  

      responses:

  

        '200':

  

          description: "Dettagli del viaggio recuperati con successo."

  

          content:

  

            application/json:

  

              schema:

  

                $ref: '#/components/schemas/TripDetail' # Riferimento a uno schema riutilizzabile

  

        '401':

  

          description: "Non autorizzato. Il token JWT è mancante o non valido."

  

          content:

  

            application/json:

  

              schema:

  

                $ref: '#/components/schemas/Error'

  

        '404':

  

          description: "Viaggio non trovato."

  

          content:

  

            application/json:

  

              schema:

  

                $ref: '#/components/schemas/Error'

  

  

components:

  

  schemas:

  

    TripDetail:

  

      type: object

  

      properties:

  

        id:

  

          type: string

  

          format: uuid

  

        name:

  

          type: string

  

          example: "Weekend a Roma"

  

        status:

  

          type: string

  

          enum: ["Planning", "InProgress", "Completed"]

  

        startDate:

  

          type: string

  

          format: date

  

        endDate:

  

          type: string

  

          format: date

  

        stops:

  

          type: array

  

          items:

  

            $ref: '#/components/schemas/Stop'

  

    Stop:

  

      type: object

  

      properties:

  

        placeName:

  

          type: string

  

          example: "Colosseo"

  

        day:

  

          type: integer

  

    Error:

  

      type: object

  

      properties:

  

        message:

  

          type: string

  

        code:

  

          type: string

  

  securitySchemes:

  

    bearerAuth:

  

      type: http

  

      scheme: bearer

  

      bearerFormat: JWT

  

      description: "Autenticazione tramite JWT token ottenuto da Cognito."

  

  

```

  

  

Questo file YAML è ora la nostra fonte di verità. È chiaro, leggibile e, soprattutto, utilizzabile da strumenti automatici.

  

  

---

  

  

### 19.4. La Superpotenza dell'Ecosistema OpenAPI 🚀

  

  

Un file YAML di per sé non è magico. La sua vera potenza risiede nell'enorme ecosistema di strumenti che lo possono consumare.

  

  

#### **1. Documentazione Interattiva Automatica**

  

  

Dimenticate le pagine Confluence scritte a mano e destinate a diventare obsolete. Con strumenti come **Swagger UI** o **Redoc**, possiamo generare automaticamente una documentazione API interattiva e bellissima. Gli sviluppatori (sia frontend che backend) possono esplorare gli endpoint, vedere gli schemi dei dati e persino **provare le API direttamente dal browser**.

  

  

#### **2. Generazione di Codice (Codegen): La Chiave dell'Automazione**

  

  

Questo è il vantaggio più grande. Dal nostro singolo file `api.yaml`, possiamo generare codice boilerplate per _entrambi_ i lati della comunicazione, garantendo che siano sempre perfettamente sincronizzati.

  

  

Per il Backend (Go):

  

  

Useremo una libreria come oapi-codegen. Eseguendo un comando, possiamo generare:

  

  

- **Tipi Go**: `struct` Go per `TripDetail`, `Stop`, `Error`, ecc. Non dovremo più scriverle a mano, rischiando errori di battitura o disallineamenti.

  

- **Boilerplate del Server**: `oapi-codegen` può generare un'interfaccia Go che i nostri `http.Handler` devono implementare. Questo ci forza a implementare ogni singolo endpoint definito nella specifica, con la firma corretta. Il contratto è ora applicato a tempo di compilazione!

  

  

Per il Frontend (SvelteKit con TypeScript):

  

  

Useremo una libreria come openapi-typescript-codegen. Eseguendo un comando, questo strumento legge lo stesso file api.yaml e genera:

  

  

- **Interfacce TypeScript**: `interface TripDetail { ... }`.

  

- **Un Client API Completamente Tipizzato**: Funzioni come `getTripById(tripId: string): Promise<TripDetail>` che incapsulano la logica `fetch`, la gestione degli header e la serializzazione/deserializzazione dei dati. Il developer frontend ottiene **sicurezza dei tipi** e **autocompletamento** per tutte le chiamate API, eliminando un'intera classe di bug.

  

  

#### **3. Testing e Mocking**

  

  

La specifica può essere usata per:

  

  

- **Generare server mock**: Il team frontend può lavorare contro un server fittizio che rispetta il contratto, anche se il backend non è ancora pronto.

  

- **Contract Testing**: Eseguire test automatici che verificano che l'implementazione del backend sia conforme al contratto definito nel file OpenAPI.

  

  

---

  

  

### 19.5. Il Flusso di Lavoro API-First in Pratica

  

  

Il nostro ciclo di sviluppo per nuove funzionalità cambia radicalmente:

  

  

1. **Progettazione del Contratto**: Backend e frontend dev discutono una nuova feature e la prima cosa che fanno è modificare e concordare il file `api.yaml`. La Pull Request contiene le modifiche al contratto, che diventa oggetto di revisione.

  

2. **Generazione del Codice**: Una volta che il contratto è approvato e unito al ramo principale, una pipeline CI (o uno script locale) esegue gli strumenti di `codegen` per aggiornare il codice boilerplate sia in Go che in TypeScript.

  

3. **Sviluppo in Parallelo**: A questo punto, i due team possono lavorare in parallelo con la certezza che le interfacce non cambieranno inaspettatamente.

  

    - Il backend developer deve "solo" implementare la logica di business dietro le interfacce generate.

  

    - Il frontend developer usa il client tipizzato per costruire la UI.

  

4. **Integrazione Semplificata**: Quando entrambi hanno finito, la fase di integrazione è molto più fluida, perché hanno costruito le loro parti contro lo stesso identico stampo.

  

  

---

  

  

### 19.6. Conclusioni: Il Contratto come Pilastro della Collaborazione

  

  

La Specifica OpenAPI, quando usata in un processo API-first, cessa di essere un semplice strumento di "documentazione" e diventa il pilastro su cui si fonda la collaborazione tra team e servizi.

  

  

- **Crea una Singola Fonte di Verità**: Elimina ambiguità e fraintendimenti.

  

- **Abilita l'Automazione**: Genera tipi, client e server, riducendo il codice boilerplate e gli errori manuali.

  

- **Facilita lo Sviluppo in Parallelo**: Disaccoppia i cicli di vita dello sviluppo frontend e backend.

  

- **Applica il Contratto**: Garantisce, a tempo di compilazione, che l'implementazione sia conforme al design.

  

  

In un'architettura moderna e distribuita, dove i confini tra i servizi sono le API stesse, gestirle con questo livello di disciplina non è un lusso, ma una necessità per costruire sistemi scalabili, robusti e manutenibili.

  

  

---

  

## Capitolo 20: Gestione della Concorrenza e delle Sessioni HTTP in Go

  

  

Nei capitoli precedenti, abbiamo definito il contratto della nostra API con OpenAPI. Ora siamo pronti per implementare il server HTTP che darà vita a questo contratto. Un server web moderno, per definizione, è un sistema concorrente: deve gestire centinaia, se non migliaia, di richieste simultanee in modo efficiente e sicuro.

  

  

Fortunatamente, il linguaggio Go è stato progettato con la concorrenza come una cittadina di prima classe. Il suo modello basato su **goroutine** e **canali** ci fornisce strumenti incredibilmente potenti per costruire server ad alte prestazioni. Tuttavia, con grande potere deriva una grande responsabilità. Una gestione incauta della concorrenza può portare a bug sottili e devastanti, come le _race condition_.

  

  

In questo capitolo, esploreremo in profondità il modello di concorrenza del server `net/http` di Go. Impareremo a scrivere handler sicuri, a gestire il ciclo di vita di una richiesta con `context.Context`, e implementeremo un sistema di gestione delle sessioni moderno e stateless, basato sui JWT che abbiamo introdotto nel capitolo sulla sicurezza.

  

  

---

  

  

### 20.1. La Magia del Server `net/http`: Una Goroutine per Richiesta

  

  

Quando si avvia un server web in Go con una semplice chiamata a `http.ListenAndServe`, accade qualcosa di meraviglioso e potente sotto il cofano. Per ogni singola richiesta HTTP in arrivo, il pacchetto `net/http` avvia automaticamente una **nuova goroutine** dedicata a servire quella richiesta.

  

  

Una **goroutine** è un "thread" estremamente leggero, gestito dal runtime di Go e non direttamente dal sistema operativo. Avviare una goroutine è un'operazione rapidissima e a basso consumo di memoria (pochi kilobyte), il che rende possibile per un server Go gestire decine di migliaia di connessioni concorrenti sulla stessa macchina.

  

  

Questo modello ha un'implicazione profonda per noi sviluppatori: **il nostro codice degli handler HTTP sarà sempre eseguito in un contesto concorrente**. Non dobbiamo gestire manualmente un pool di thread, ma dobbiamo essere estremamente consapevoli dei rischi che questa concorrenza comporta, in particolare il rischio di **race condition**.

  

  

#### **Il Pericolo Nascosto: Race Conditions**

  

  

Una race condition si verifica quando più goroutine accedono a una risorsa condivisa e modificabile (una variabile, una mappa, una slice, una struct) contemporaneamente, e almeno una di queste scritture può portare a uno stato corrotto o imprevedibile.

  

  

Controesempio: Un Contatore Globale (NON FARE QUESTO)

  

  

Immaginiamo di voler tenere un semplice contatore in memoria per il numero totale di richieste ricevute.

  

  

Go

  

  

```go

  

package main

  

  

import (

  

    "fmt"

  

    "net/http"

  

)

  

  

var counter int // Stato condiviso e modificabile

  

  

func CounterHandler(w http.ResponseWriter, r *http.Request) {

  

    counter++ // Accesso concorrente da più goroutine! DATA RACE!

  

    fmt.Fprintf(w, "Questa è la richiesta numero %d", counter)

  

}

  

  

func main() {

  

    http.HandleFunc("/", CounterHandler)

  

    http.ListenAndServe(":8080", nil)

  

}

  

```

  

  

Se si esegue questo codice e lo si testa con uno strumento di benchmark che invia richieste concorrenti (come `ab` o `hey`), i risultati saranno imprevedibili. Alcuni incrementi potrebbero andare persi. Se si esegue il programma con il **Race Detector** integrato in Go (`go run -race .`), il runtime rileverà e segnalerà immediatamente la data race.

  

  

---

  

  

### 20.2. Pattern per la Sicurezza nella Concorrenza

  

  

Come possiamo scrivere codice concorrente in modo sicuro? Go ci offre diversi strumenti.

  

  

#### **Pattern 1: Mutua Esclusione con `sync.Mutex`**

  

  

Il modo più classico per proteggere una risorsa condivisa è usare un **mutex** (mutual exclusion lock). Un mutex garantisce che solo una goroutine alla volta possa entrare in una "sezione critica" di codice.

  

  

Go

  

  

```go

  

import (

  

    "fmt"

  

    "net/http"

  

    "sync" // Importiamo il pacchetto sync

  

)

  

  

var (

  

    counter int

  

    mu      sync.Mutex // Il nostro mutex

  

)

  

  

func SafeCounterHandler(w http.ResponseWriter, r *http.Request) {

  

    mu.Lock()   // Acquisiamo il lock. Tutte le altre goroutine si bloccano qui.

  

    counter++

  

    currentCount := counter

  

    mu.Unlock() // Rilasciamo il lock, permettendo ad altre goroutine di procedere.

  

  

    fmt.Fprintf(w, "Questa è la richiesta numero %d", currentCount)

  

}

  

```

  

  

Questo codice è ora sicuro. Tuttavia, l'uso eccessivo di mutex può diventare un collo di bottiglia per le performance, poiché serializza l'accesso alla risorsa.

  

  

#### **Pattern 2: La Via Idiomatica di Go - Condividere Dati Comunicando**

  

  

Una filosofia centrale in Go è: _"Non comunicare condividendo la memoria; condividi la memoria comunicando"_. Questo si traduce nell'uso dei **canali** (channels) per orchestrare l'accesso a risorse condivise. Invece di avere più goroutine che competono per un lock, si può avere una singola goroutine che "possiede" la risorsa e le altre comunicano con essa tramite canali per richiedere operazioni. Questo pattern è più complesso e solitamente riservato a scenari specifici.

  

  

#### **Pattern 3: La Soluzione Migliore - Progettare Servizi Stateless**

  

  

La soluzione più efficace e robusta per evitare problemi di concorrenza è, ove possibile, **eliminare del tutto lo stato condiviso e modificabile** a livello di applicazione.

  

  

Questo è esattamente ciò che la nostra **Clean Architecture** ci incoraggia a fare!

  

  

- I nostri **Application Services** e **Repository** vengono istanziati una sola volta all'avvio dell'applicazione.

  

- Essi stessi sono **stateless**: non mantengono uno stato che cambia tra una richiesta e l'altra. Le loro dipendenze (come `*sql.DB`) sono progettate per essere usate in modo concorrente.

  

- Ogni richiesta, nella sua goroutine, riceve i dati di cui ha bisogno (es. dal body della richiesta o dal database), chiama i metodi stateless dei servizi e lavora su una "copia" dei dati specifica per quella transazione.

  

  

Grazie a questo design, la maggior parte del nostro codice è naturalmente al sicuro dalle race condition, perché non c'è memoria condivisa da proteggere.

  

  

---

  

  

### 20.3. `context.Context`: Il Sistema Nervoso di una Richiesta

  

  

Ogni richiesta HTTP in Go ha un ciclo di vita. Potrebbe completarsi con successo, andare in timeout, o essere annullata perché l'utente ha chiuso il browser. Il pacchetto `context` è lo strumento standard e indispensabile per gestire questo ciclo di vita.

  

  

> Un `context.Context` è un oggetto che trasporta deadline, segnali di cancellazione e altri valori legati a una richiesta attraverso i confini delle API e dei processi.

  

  

Il server `net/http` crea un `Context` per ogni richiesta e lo rende disponibile tramite `r.Context()`. Dobbiamo passarlo esplicitamente attraverso tutti i livelli della nostra applicazione.

  

  

**Casi d'Uso Chiave:**

  

  

1. **Cancellazione (Cancellation)**: Se un utente chiude la connessione mentre stiamo eseguendo una query database molto lunga, il context verrà "annullato". Il nostro `database/sql` driver, se scritto correttamente, rileverà questo segnale (`ctx.Done()`) e interromperà la query, rilasciando preziose risorse del database.

  

2. **Timeout**: Possiamo usare `context.WithTimeout` per imporre una deadline a un'intera operazione. Se un caso d'uso non si completa entro, diciamo, 5 secondi, tutte le operazioni a valle (chiamate al DB, a servizi esterni) verranno annullate.

  

3. **Valori Scoped-Request**: Il context è il posto giusto per memorizzare dati che sono validi solo per la durata di una singola richiesta, come un ID di tracciamento per il logging, o l'ID dell'utente autenticato.

  

  

Go

  

  

```go

  

// Esempio di middleware che aggiunge un valore al context

  

func AuthMiddleware(next http.Handler) http.Handler {

  

    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {

  

        // ... logica per validare un token JWT ...

  

        userID := // ... estrae l'ID utente dal token ...

  

  

        // Crea un nuovo context con l'ID utente e lo mette nella richiesta

  

        ctx := context.WithValue(r.Context(), "userIDKey", userID)

  

        next.ServeHTTP(w, r.WithContext(ctx))

  

    })

  

}

  

  

// L'Application Service può poi recuperare il valore

  

func (s *TripApplicationService) FindTripsForCurrentUser(ctx context.Context) ([]*Trip, error) {

  

    userID, ok := ctx.Value("userIDKey").(identity.UserID)

  

    if !ok {

  

        return nil, errors.New("unauthorized")

  

    }

  

    // ... usa userID per chiamare il repository ...

  

}

  

```

  

  

---

  

  

### 20.4. Gestione delle Sessioni: JWT Stateless

  

  

Come abbiamo anticipato, un'architettura a microservizi scalabile trae enormi benefici da un approccio **stateless**, dove il server non ha bisogno di memorizzare lo stato della sessione di un utente tra una richiesta e l'altra.

  

  

L'approccio tradizionale con cookie di sessione e uno store lato server (in memoria o su DB/Redis) crea un collo di bottiglia e complica lo scaling orizzontale.

  

  

La soluzione moderna, che abbiamo adottato nel nostro design, è usare i **JSON Web Tokens (JWT)**.

  

  

1. L'utente si autentica (nel nostro caso, con AWS Cognito).

  

2. Il servizio di identità restituisce un JWT firmato digitalmente. Il JWT è un token che **contiene** le informazioni sull'utente (i _claims_).

  

3. Il nostro frontend SvelteKit memorizza questo token e lo invia con ogni richiesta nell'header `Authorization: Bearer <token>`.

  

4. Il nostro backend Go, ad ogni richiesta, verifica il token **senza dover contattare nessun servizio esterno**.

  

  

La "sessione" è il token stesso. Il server rimane stateless.

  

  

#### **Implementazione di un Middleware di Validazione JWT**

  

  

Ecco come potrebbe apparire un middleware che protegge i nostri endpoint.

  

  

Go

  

  

```go

  

// Middleware per validare un JWT di Cognito

  

func JWTAuthMiddleware(next http.Handler) http.Handler {

  

    // All'avvio, dovremmo recuperare e mettere in cache le chiavi pubbliche (JWKS) da Cognito.

  

    // jwks_url := "https://cognito-idp.{region}.amazonaws.com/{userPoolId}/.well-known/jwks.json"

  

    // ... codice per recuperare le chiavi ...

  

  

    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {

  

        authHeader := r.Header.Get("Authorization")

  

        if authHeader == "" {

  

            http.Error(w, "Authorization header required", http.StatusUnauthorized)

  

            return

  

        }

  

  

        tokenString := strings.TrimPrefix(authHeader, "Bearer ")

  

        if tokenString == authHeader {

  

            http.Error(w, "Invalid Authorization header format", http.StatusUnauthorized)

  

            return

  

        }

  

  

        // Usa una libreria come 'github.com/golang-jwt/jwt/v5'

  

        token, err := jwt.Parse(tokenString, func(token *jwt.Token) (interface{}, error) {

  

            // Qui si recupera la chiave pubblica corretta dal set (JWKS)

  

            // in base all'ID della chiave ('kid') presente nell'header del token.

  

            // ... logica di lookup della chiave ...

  

            return publicKey, nil

  

        })

  

  

        if err != nil || !token.Valid {

  

            http.Error(w, "Invalid token", http.StatusUnauthorized)

  

            return

  

        }

  

  

        claims, ok := token.Claims.(jwt.MapClaims)

  

        if !ok {

  

            http.Error(w, "Invalid token claims", http.StatusUnauthorized)

  

            return

  

        }

  

  

        // Estrai l'ID utente (claim 'sub') e mettilo nel context

  

        userID := claims["sub"].(string)

  

        ctx := context.WithValue(r.Context(), "userIDKey", userID)

  

        next.ServeHTTP(w, r.WithContext(ctx))

  

    })

  

}

  

```

  

  

---

  

  

### 20.5. Conclusioni: Costruire Server Robusti e Scalabili

  

  

La gestione della concorrenza e delle sessioni è dove "la gomma incontra la strada" nello sviluppo di backend.

  

  

- Go ci offre un modello di **concorrenza di default** che è incredibilmente performante, ma che richiede disciplina per evitare le race condition. La migliore strategia è **progettare servizi stateless**, come promosso dalla Clean Architecture.

  

- Il `context.Context` è lo strumento essenziale per gestire il ciclo di vita delle richieste, garantendo **resilienza e un corretto uso delle risorse**.

  

- Le **sessioni stateless basate su JWT** sono l'approccio standard per le API moderne e distribuite, eliminando i colli di bottiglia e abilitando uno scaling orizzontale senza sforzo.

  

  

Padroneggiare questi concetti ci permette di tradurre il nostro design architetturale di alto livello in un'implementazione server-side che non è solo corretta, ma anche sicura, performante e pronta per la produzione.

  

  

---

  

## Capitolo 21: Integrazione Resiliente con OpenAI

  

  

Nel vasto ecosistema del software moderno, nessuna applicazione è un'isola. La nostra capacità di creare valore è spesso amplificata esponenzialmente dalla nostra capacità di integrarci con servizi esterni specializzati. Per la nostra applicazione "Where Should I Be?", l'integrazione con i Large Language Models (LLM) di OpenAI è la chiave per la nostra funzionalità più innovativa: la generazione di suggerimenti di viaggio intelligenti.

  

  

Tuttavia, questa integrazione è un'arma a doppio taglio. Mentre ci dà accesso a capacità straordinarie, ci espone anche a un mondo di incertezza. La rete è inaffidabile. I servizi esterni possono essere lenti, possono fallire, possono cambiare le loro API o restituire dati inaspettati. Siamo alla mercé di un sistema che è completamente fuori dal nostro controllo.

  

  

Un'implementazione ingenua di questa integrazione creerebbe un sistema fragile, pronto a crollare al primo segno di difficoltà. In questo capitolo, impareremo a costruire un ponte **resiliente** verso OpenAI. Progetteremo e implementeremo un **Anti-Corruption Layer (ACL)** robusto, utilizzando pattern collaudati come Timeouts, Retries e Circuit Breakers per garantire che la nostra applicazione rimanga stabile, reattiva e affidabile, indipendentemente dal comportamento del servizio esterno.

  

  

---

  

  

### 21.1. Il Problema: La Fragilità delle Chiamate Dirette

  

  

Immaginiamo un approccio naive. Il nostro `SuggestionService`, all'interno di un handler HTTP, riceve una richiesta dall'utente e chiama direttamente il client Go di OpenAI.

  

  

Go

  

  

```go

  

//

  

// CONTROESEMPIO: Un'integrazione fragile e diretta

  

//

  

func (h *Handler) HandleGenerateSuggestion(w http.ResponseWriter, r *http.Request) {

  

    // ... parsing della richiesta ...

  

  

    // Chiamata diretta e sincrona al client OpenAI

  

    resp, err := h.openAIClient.CreateChatCompletion(r.Context(), openai.ChatCompletionRequest{

  

        Model: openai.GPT4o,

  

        Messages: []openai.ChatCompletionMessage{

  

            // ... messaggi del prompt ...

  

        },

  

    })

  

  

    if err != nil {

  

        // Se OpenAI fallisce, il nostro server risponde con un errore 500 generico.

  

        http.Error(w, "Failed to generate suggestion", http.StatusInternalServerError)

  

        return

  

    }

  

  

    // ... parsing della risposta e invio al client ...

  

}

  

```

  

  

Questo codice è una bomba a orologeria. Cosa succede se:

  

  

- **L'API di OpenAI è lenta?** La nostra richiesta HTTP rimane appesa, bloccando una goroutine sul nostro server e facendo attendere l'utente per decine di secondi, fino a un probabile timeout del nostro load balancer.

  

- **La rete ha un problema transitorio?** La chiamata fallisce. L'utente riceve un errore e deve riprovare manualmente, frustrato.

  

- **L'API di OpenAI è completamente offline?** Ogni richiesta al nostro endpoint fallirà, potenzialmente saturando il nostro sistema di errori e log inutili.

  

- **La nostra richiesta supera i limiti di rateo di OpenAI?** Riceveremo un errore `429 Too Many Requests` che non stiamo gestendo in modo intelligente.

  

  

Per costruire un sistema di livello enterprise, dobbiamo anticipare questi fallimenti e gestirli con grazia. La soluzione inizia con un design architetturale pulito: l'Anti-Corruption Layer.

  

  

---

  

  

### 21.2. L'Anti-Corruption Layer (ACL) in Pratica

  

  

Come introdotto nel Capitolo 18, un ACL è il nostro scudo difensivo. È un componente specifico il cui unico scopo è mediare la comunicazione tra il nostro dominio e un sistema esterno, traducendo i dati e assorbendo gli shock.

  

  

Il nostro ACL per OpenAI sarà composto da:

  

  

1. **Una Porta (Interface)**: Definiamo un'interfaccia nel nostro layer applicativo che descrive il contratto di cui il nostro dominio ha bisogno, in termini del nostro Linguaggio Ubiquo.

  

2. **Un Adattatore (Adapter)**: L'implementazione concreta della porta. Questo è il nostro ACL. Contiene tutta la logica "sporca" di comunicazione e resilienza.

  

  

Go

  

  

```go

  

// internal/application/ports.go

  

package application

  

  

import (

  

    "context"

  

    "where-should-i-be/internal/domain/suggestions"

  

)

  

  

// SuggestionProvider è la nostra porta. Il dominio dipende da questa astrazione.

  

type SuggestionProvider interface {

  

    GenerateItinerary(ctx context.Context, request suggestions.SuggestionRequest) (*suggestions.ItineraryProposal, error)

  

}

  

```

  

  

Go

  

  

```go

  

// internal/adapters/gateway/openai/acl.go

  

package openai

  

  

import (

  

    "context"

  

    "where-should-i-be/internal/application"

  

    "where-should-i-be/internal/domain/suggestions"

  

    // ...

  

)

  

  

// OpenAIAdapter è il nostro ACL, l'implementazione concreta.

  

type OpenAIAdapter struct {

  

    client *openai.Client

  

    // ... altre dipendenze per la resilienza ...

  

}

  

  

// NewOpenAIAdapter è la sua factory.

  

func NewOpenAIAdapter(...) *OpenAIAdapter { ... }

  

  

var _ application.SuggestionProvider = (*OpenAIAdapter)(nil)

  

  

func (a *OpenAIAdapter) GenerateItinerary(ctx context.Context, request suggestions.SuggestionRequest) (*suggestions.ItineraryProposal, error) {

  

    // Qui dentro implementeremo i pattern di resilienza!

  

    // ...

  

}

  

```

  

  

---

  

  

### 21.3. Pattern di Resilienza per Chiamate di Rete

  

  

All'interno del nostro `OpenAIAdapter`, implementeremo una serie di pattern per renderlo robusto.

  

  

#### **Pattern 1: Timeouts (Sempre e Comunque)**

  

  

Nessuna chiamata di rete dovrebbe mai essere fatta senza un timeout. In Go, il `context` è lo strumento perfetto per questo.

  

  

Go

  

  

```go

  

func (a *OpenAIAdapter) makeRequestWithTimeout(ctx context.Context, prompt string) (string, error) {

  

    // Creiamo un nuovo context con un timeout di, ad esempio, 15 secondi.

  

    // La chiamata a OpenAI verrà annullata se dura più a lungo.

  

    reqCtx, cancel := context.WithTimeout(ctx, 15*time.Second)

  

    defer cancel() // È fondamentale chiamare cancel per rilasciare le risorse.

  

  

    // ... corpo della richiesta ...

  

    resp, err := a.client.CreateChatCompletion(reqCtx, req)

  

    if err != nil {

  

        // Se l'errore è dovuto alla scadenza del timeout, possiamo loggarlo specificamente.

  

        if errors.Is(err, context.DeadlineExceeded) {

  

            log.Println("OpenAI request timed out")

  

        }

  

        return "", err

  

    }

  

    // ...

  

}

  

```

  

  

#### **Pattern 2: Retries con Exponential Backoff e Jitter**

  

  

Per errori transitori (es. un `502 Bad Gateway` o un momentaneo problema di rete), non ha senso fallire subito. È meglio riprovare. Ma riprovare immediatamente può peggiorare le cose.

  

  

- **Exponential Backoff**: La strategia di attesa tra un tentativo e l'altro aumenta esponenzialmente (es. 1s, 2s, 4s, 8s). Questo dà tempo al sistema esterno di riprendersi.

  

- **Jitter**: Si aggiunge un piccolo ritardo casuale all'attesa per evitare che più istanze del nostro servizio, in caso di fallimento di massa, riprovino tutte nello stesso identico istante (problema della "Thundering Herd").

  

  

Invece di reinventare la ruota, usiamo una libreria standard del settore come `cenkalti/backoff`.

  

  

> **Riferimento Chiave**: La libreria `github.com/cenkalti/backoff/v4` è una scelta eccellente e robusta per implementare strategie di retry in Go.

  

  

Go

  

  

```go

  

import "github.com/cenkalti/backoff/v4"

  

  

func (a *OpenAIAdapter) GenerateItinerary(...) (*suggestions.ItineraryProposal, error) {

  

    var rawResponse string

  

    // Definiamo la nostra operazione di chiamata all'API

  

    operation := func() error {

  

        // La nostra funzione con timeout

  

        resp, err := a.makeRequestWithTimeout(ctx, "...") 

  

        if err != nil {

  

            // Se l'errore è un 429 (Too Many Requests) o un 5xx,

  

            // vogliamo riprovare. Altri errori (es. 400 Bad Request)

  

            // sono permanenti e non ha senso riprovare.

  

            if shouldRetry(err) {

  

                return err // L'errore indica a backoff di riprovare

  

            }

  

            return backoff.Permanent(err) // Errore permanente, non riprovare

  

        }

  

        rawResponse = resp

  

        return nil // Successo

  

    }

  

  

    // Creiamo una policy di backoff esponenziale

  

    expBackoff := backoff.NewExponentialBackOff()

  

    expBackoff.MaxElapsedTime = 30 * time.Second // Non riprovare per più di 30s in totale

  

  

    // Eseguiamo l'operazione con la policy di retry

  

    err := backoff.Retry(operation, expBackoff)

  

    if err != nil {

  

        return nil, fmt.Errorf("failed to call OpenAI after multiple retries: %w", err)

  

    }

  

  

    // ... ora tradiamo rawResponse nel nostro ItineraryProposal ...

  

}

  

```

  

  

#### **Pattern 3: Circuit Breaker (Interruttore di Circuito)**

  

  

Se l'API di OpenAI è completamente down, continuare a martellarla di richieste è dannoso per noi (sprechiamo risorse) e per loro. Il pattern Circuit Breaker previene questo.

  

  

- **Stati**: **Chiuso** (tutto ok), **Aperto** (fallisce subito), **Semi-Aperto** (prova una richiesta per vedere se il servizio è tornato online).

  

  

Una libreria popolare in Go per questo è `sony/gobreaker`.

  

  

Go

  

  

```go

  

// In NewOpenAIAdapter:

  

var st gobreaker.Settings

  

st.Name = "OpenAI"

  

st.OnStateChange = func(name string, from, to gobreaker.State) {

  

    log.Printf("Circuit Breaker %s changed from %s to %s", name, from, to)

  

}

  

cb := gobreaker.NewCircuitBreaker(st)

  

  

// Dentro GenerateItinerary, prima della logica di retry:

  

func (a *OpenAIAdapter) GenerateItinerary(...) (*suggestions.ItineraryProposal, error) {

  

    var proposal *suggestions.ItineraryProposal

  

  

    _, err := a.circuitBreaker.Execute(func() (interface{}, error) {

  

        // Tutta la nostra logica con i retry va qui dentro.

  

        // ... codice con backoff.Retry ...

  

        return result, err

  

    })

  

  

    if err != nil {

  

        // Se l'errore è gobreaker.ErrOpenState, sappiamo che il circuito è aperto.

  

        return nil, fmt.Errorf("circuit breaker is open: %w", err)

  

    }

  

  

    return proposal, nil

  

}

  

```

  

  

---

  

  

### 21.4. Disaccoppiamento Asincrono: Non Far Aspettare l'Utente

  

  

Anche con tutti questi pattern, una chiamata a un LLM può richiedere svariati secondi. Far attendere un utente davanti a uno spinner per 10 secondi è una pessima esperienza utente. La soluzione è rendere l'interazione **asincrona**.

  

  

1. L'endpoint API del nostro `suggestions-service` (`POST /suggestions`) non chiama più l'ACL di OpenAI direttamente.

  

2. Invece, convalida la richiesta, crea un comando `GenerateSuggestionCommand` e lo pubblica su una **coda di messaggi** (come **AWS SQS**, che vedremo nel Capitolo 22).

  

3. Risponde **immediatamente** al client con `202 Accepted` e un ID per tracciare lo stato del lavoro.

  

4. Un **worker in background** (una **AWS Lambda**, vedi Capitolo 22) è sottoscritto alla coda SQS.

  

5. Quando arriva un nuovo messaggio, la Lambda si attiva ed è lei a eseguire il nostro `OpenAIAdapter` con tutta la sua logica di resilienza.

  

6. Una volta ottenuto il risultato, lo salva nel database.

  

7. Il frontend può interrogare un endpoint di stato o ricevere una notifica (tramite WebSocket o Server-Sent Events) che il suggerimento è pronto.

  

  

Questo design trasforma l'esperienza utente da sincrona e bloccante ad asincrona e reattiva, e isola completamente i fallimenti del servizio esterno in un processo in background.

  

  

---

  

  

### 21.5. Prompt Engineering e Validazione delle Risposte

  

  

La resilienza non è solo a livello di rete, ma anche di dati.

  

  

- **Prompt Engineering**: La qualità del nostro prompt è tutto. Dobbiamo istruire esplicitamente l'LLM a fornirci una risposta strutturata. Le API più recenti di OpenAI hanno una "JSON mode" che aiuta in questo. Un buon prompt include esempi (few-shot prompting) e una descrizione chiara dello schema JSON desiderato.

  

- **Validazione Difensiva**: **Mai fidarsi ciecamente dell'output di un LLM**. Anche in JSON mode, la struttura potrebbe non essere perfetta o i dati potrebbero essere senza senso. L'ultima fase del nostro ACL (il "Translator") deve:

  

    1. Validare che il JSON sia sintatticamente corretto.

  

    2. Validare che la struttura corrisponda a quella attesa.

  

    3. Validare che i dati abbiano un senso per il nostro dominio (es. le date sono coerenti, i nomi dei luoghi non sono vuoti) prima di creare l'oggetto `ItineraryProposal`.

  

  

---

  

  

### 21.6. Conclusioni: Costruire Ponti Robusti

  

  

L'integrazione con servizi esterni come OpenAI è un superpotere per le applicazioni moderne. Ma per evitare che questo superpotere diventi il nostro tallone d'Achille, dobbiamo approcciare l'integrazione con una mentalità difensiva e orientata alla resilienza.

  

  

In questo capitolo, abbiamo trasformato una semplice chiamata API in un robusto Anti-Corruption Layer, combinando:

  

  

- **Pattern di resilienza di rete**: Timeouts, Retries e Circuit Breakers.

  

- **Pattern architetturali**: Disaccoppiamento asincrono tramite code di messaggi.

  

- **Pattern di resilienza dei dati**: Prompt engineering e validazione difensiva.

  

  

Questo approccio non solo rende la nostra applicazione più stabile e affidabile, ma migliora anche drasticamente l'esperienza dei nostri utenti. Ora siamo pronti ad affrontare le sfide della persistenza su larga scala nel cloud AWS.

  

  

---

  

# **Parte VI: Persistenza Scalabile su AWS**

  

  

## Capitolo 22: Disaccoppiare la Persistenza con Lambda e SQS

  

  

Nelle parti precedenti, abbiamo progettato un'architettura software pulita e un modello di dominio ricco. Abbiamo discusso di pattern avanzati come il CQRS, che separa le responsabilità di scrittura (Comandi) da quelle di lettura (Query). Ma finora, quando abbiamo parlato di salvare dati, abbiamo implicitamente assunto che l'operazione `repository.Save()` avvenisse in modo **sincrono**, all'interno dello stesso ciclo di richiesta-risposta dell'utente.

  

  

Questo approccio sincrono è semplice da capire, ma nasconde un'enorme fragilità. Cosa succede se il nostro database è lento o momentaneamente non disponibile? La richiesta dell'utente rimane bloccata, lo spinner sul suo browser gira all'infinito e, nel peggiore dei casi, un rallentamento del database può esaurire il pool di connessioni del nostro server API, causando un'interruzione totale del servizio.

  

  

In questo capitolo, introdurremo un'architettura molto più robusta e scalabile. Impareremo a **disaccoppiare il processo di scrittura** dalla richiesta principale dell'utente, trasformando la persistenza da un'operazione bloccante a un flusso di lavoro asincrono. Useremo due dei servizi più potenti dell'ecosistema AWS per raggiungere questo obiettivo: **Amazon SQS (Simple Queue Service)** e **AWS Lambda**.

  

  

---

  

  

### 22.1. Il Problema: La Tirannia delle Scritture Sincrone

  

  

Consideriamo il flusso di lavoro del nostro `TripPlanningService` quando un utente aggiunge una tappa a un viaggio. In un modello sincrono:

  

  

1. L'API riceve la richiesta `POST /trips/{id}/stops`.

  

2. L'Application Service carica l'aggregato `Viaggio`.

  

3. Chiama il metodo `viaggio.AddStop(...)`, che valida gli invarianti.

  

4. Chiama `tripRepository.Save(viaggio)`.

  

5. Il repository inizia una transazione, esegue `UPDATE` e `INSERT` sul database. **L'API attende.**

  

6. Il database conferma il commit. **L'API attende.**

  

7. Solo ora, l'API risponde `200 OK` all'utente.

  

  

L'intero processo è legato alla performance del database. Se il passo 5 richiede 3 secondi, l'utente attenderà 3 secondi. Questo non è solo una cattiva esperienza utente; è un rischio per la stabilità dell'intero sistema.

  

  

---

  

  

### 22.2. L'Architettura Asincrona: La Coda come Buffer

  

  

La soluzione è introdurre un "cuscinetto" tra la nostra API e il database: una coda di messaggi.

  

  

> **Definizione**: Una **coda di messaggi** è un servizio che agisce come una casella di posta intermediaria. I produttori inviano messaggi alla coda, dove vengono memorizzati in modo duraturo. I consumatori leggono i messaggi dalla coda e li processano quando sono pronti.

  

  

Nel nostro caso, i componenti chiave saranno:

  

  

- **Amazon SQS (Simple Queue Service)**: Il nostro servizio di coda gestito. È altamente disponibile, scalabile e duraturo. Funzionerà come il buffer per le nostre operazioni di scrittura.

  

- **AWS Lambda**: Il nostro servizio di calcolo serverless. Scriveremo una funzione Go che verrà eseguita automaticamente ogni volta che un nuovo messaggio arriva sulla nostra coda SQS.

  

  

Il nuovo flusso di lavoro (il lato **Comando** del nostro CQRS) diventa:

  

  

1. L'API riceve la richiesta `POST /trips/{id}/stops`.

  

2. L'Application Service esegue **solo la validazione sincrona essenziale**. Carica l'aggregato per controllare le regole di business.

  

3. Se la validazione ha successo, invece di chiamare il repository, crea un evento (es. `StopAddedToTripEvent`) e lo invia come **messaggio alla nostra coda SQS**.

  

4. L'API risponde **immediatamente** all'utente con `202 Accepted`, che significa: "Ho ricevuto la tua richiesta e la elaborerò. Non devi più aspettare". L'esperienza utente è istantanea.

  

5. **Nel frattempo, in background...**

  

6. La coda SQS, ricevendo un nuovo messaggio, **attiva automaticamente la nostra funzione AWS Lambda**.

  

7. La funzione Lambda riceve l'evento, istanzia il nostro `TripRepository` e finalmente esegue l'operazione di scrittura sul database.

  

  

---

  

  

### 22.3. SQS in Dettaglio: La Nostra Cassetta Postale Affidabile

  

  

SQS è un servizio semplice ma con alcune caratteristiche cruciali per un design robusto.

  

  

#### **Tipi di Code: Standard vs. FIFO**

  

  

- **Standard Queue**: È la scelta di default. Offre un throughput quasi illimitato e garantisce una consegna _at-least-once_ (almeno una volta). L'ordine dei messaggi non è strettamente garantito. È la scelta perfetta per la maggior parte dei casi d'uso in cui le operazioni sono **idempotenti** (eseguire la stessa operazione più volte ha lo stesso risultato che eseguirla una volta sola).

  

- **FIFO (First-In, First-Out) Queue**: Garantisce l'ordine esatto dei messaggi e una consegna _exactly-once_. Questo ha un costo in termini di performance (throughput inferiore). Da usare solo se l'ordine delle operazioni è un invariante critico del business.

  

  

Per la nostra applicazione, useremo una **Coda Standard** per la sua scalabilità, e progetteremo i nostri consumatori (le Lambda) perché siano idempotenti.

  

  

#### **Dead-Letter Queue (DLQ): La Rete di Sicurezza**

  

  

Cosa succede se la nostra funzione Lambda fallisce ripetutamente nel processare un messaggio a causa di un bug o di dati corrotti (un "poison pill")? Senza una DLQ, la Lambda tenterebbe all'infinito, bloccando la coda.

  

  

Una **Dead-Letter Queue** è una seconda coda SQS che funge da "cestino" per i messaggi falliti. Configuriamo la coda principale dicendo: "Dopo N tentativi di elaborazione falliti, sposta questo messaggio nella DLQ". Questo sblocca la coda principale e ci permette di ispezionare, analizzare e potenzialmente riprocessare i messaggi falliti in un secondo momento, senza interrompere il servizio. **Una coda di produzione senza una DLQ configurata è un sistema incompleto.**

  

  

---

  

  

### 22.4. Scrivere una Funzione Lambda in Go per Processare i Messaggi SQS

  

  

Vediamo come appare il codice del nostro consumatore serverless.

  

  

**Prerequisiti**:

  

  

- SDK di AWS per Go V2: `aws.Config`, client SQS.

  

- Libreria per eventi Lambda: `github.com/aws/aws-lambda-go/events`.

  

- Libreria Lambda per Go: `github.com/aws/aws-lambda-go/lambda`.

  

  

Go

  

  

```go

  

// cmd/trip-persistence-worker/main.go

  

package main

  

  

import (

  

    "context"

  

    "encoding/json"

  

    "log"

  

  

    "github.com/aws/aws-lambda-go/events"

  

    "github.com/aws/aws-lambda-go/lambda"

  

    // I nostri package interni

  

    "where-should-i-be/internal/application"

  

    "where-should-i-be/internal/adapters/persistence/postgres"

  

    "where-should-i-be/internal/domain/events" // Dove definiamo i nostri eventi

  

)

  

  

// Definiamo il nostro gestore, che contiene le dipendenze.

  

// Le dipendenze vengono inizializzate una volta per ogni istanza "calda" della Lambda.

  

type SQSHandler struct {

  

    tripRepo application.TripRepository

  

}

  

  

// L'inizializzazione avviene nella funzione init() o globalmente.

  

// Questo sfrutta la "cold start" per preparare le connessioni.

  

var handler SQSHandler

  

func init() {

  

    // In un'app reale, la configurazione verrebbe da variabili d'ambiente.

  

    db, err := postgres.Connect(...) 

  

    if err != nil {

  

        log.Fatalf("failed to connect to db: %v", err)

  

    }

  

    handler = SQSHandler{

  

        tripRepo: postgres.NewPostgresTripRepository(db),

  

    }

  

}

  

  

// HandleRequest è la funzione che viene invocata da AWS Lambda.

  

func (h *SQSHandler) HandleRequest(ctx context.Context, sqsEvent events.SQSEvent) error {

  

    // Lambda può inviare i messaggi in batch.

  

    for _, message := range sqsEvent.Records {

  

        log.Printf("Processing message ID: %s", message.MessageId)

  

  

        // Qui, dovremmo avere una logica per distinguere i tipi di evento,

  

        // ad esempio usando un campo "EventType" nel JSON.

  

        var event events.StopAddedToTrip

  

        if err := json.Unmarshal([]byte(message.Body), &event); err != nil {

  

            // Messaggio malformato. Non ha senso riprovare.

  

            // Logghiamo l'errore e non restituiamo 'err', così SQS

  

            // considera il messaggio processato (e lo rimuove dalla coda).

  

            log.Printf("ERROR: failed to unmarshal message body: %v", err)

  

            continue

  

        }

  

  

        // Ora che abbiamo l'evento di dominio, eseguiamo la logica di persistenza.

  

        err := h.tripRepo.ApplyStopAddedEvent(ctx, event)

  

        if err != nil {

  

            // Errore durante l'elaborazione (es. DB non disponibile).

  

            // Restituiamo l'errore. Questo farà sì che SQS

  

            // renda di nuovo visibile il messaggio per un altro tentativo.

  

            // Dopo N tentativi, finirà nella DLQ.

  

            log.Printf("ERROR: failed to process event for trip %s: %v", event.TripID, err)

  

            return err

  

        }

  

  

        log.Printf("Successfully processed event for trip %s", event.TripID)

  

    }

  

  

    // Se tutte le elaborazioni vanno a buon fine, restituiamo nil.

  

    return nil

  

}

  

  

func main() {

  

    // Avviamo il listener di Lambda, passando il nostro metodo handler.

  

    lambda.Start(handler.HandleRequest)

  

}

  

```

  

  

Questo codice viene compilato in un eseguibile Go, impacchettato in un file .zip e caricato su AWS Lambda.

  

  

---

  

  

### 22.5. Vantaggi e Complessità del Modello Asincrono

  

  

Adottare questo pattern porta a un'architettura più complessa, ma con benefici enormi.

  

  

Vantaggi:

  

  

✅ Resilienza: Un'interruzione del database non impatta la capacità della nostra API di accettare nuove scritture. I messaggi si accumulano pazientemente in SQS.

  

  

✅ Scalabilità: SQS e Lambda scalano in modo indipendente e automatico. Possiamo assorbire picchi di traffico di scrittura senza dover scalare i nostri server API.

  

  

✅ Esperienza Utente: La risposta API è quasi istantanea, migliorando drasticamente la reattività percepita dal frontend.

  

  

✅ Disaccoppiamento: L'API server è completamente disaccoppiato dalla logica di persistenza. Potremmo cambiare il database o la logica del worker senza toccare l'API.

  

  

Complessità da Gestire:

  

  

⚠️ Consistenza Eventuale: Questo è il compromesso principale. Dopo che l'utente ha aggiunto una tappa, se ricarica la pagina istantaneamente, potrebbe non vedere ancora la modifica. Il sistema è eventualmente consistente. La nostra UI deve essere progettata per gestire questo (es. con aggiornamenti "ottimistici" o polling).

  

  

⚠️ Monitoring: Abbiamo ora un sistema distribuito. Il monitoraggio diventa cruciale. Dobbiamo avere allarmi sulla dimensione della coda SQS (se cresce troppo, c'è un problema nel consumatore) e sugli errori di esecuzione della Lambda. (Vedi Capitolo 29).

  

  

⚠️ Idempotenza: Poiché le code standard SQS garantiscono una consegna at-least-once, la nostra Lambda deve essere idempotente. Se riceve lo stesso messaggio StopAddedToTrip due volte, il risultato finale deve essere lo stesso. Questo può essere gestito con controlli sulla versione dell'aggregato o ID di evento univoci.

  

  

---

  

  

### 22.6. Conclusioni: La Persistenza come Flusso, non come Muro

  

  

Introducendo una coda di messaggi tra la nostra API e il database, abbiamo trasformato la persistenza da un "muro" sincrono e bloccante a un "fiume" asincrono, resiliente e scalabile. Questo pattern è un pilastro delle moderne applicazioni cloud-native e realizza pienamente il potenziale disaccoppiante del nostro design CQRS.

  

  

Sebbene introduca la complessità della consistenza eventuale, i guadagni in termini di robustezza, scalabilità ed esperienza utente sono un investimento che ripaga ampiamente in qualsiasi sistema non banale. Con questa base, siamo ora pronti a discutere della scelta del database stesso, esplorando perché DynamoDB potrebbe essere una scelta ancora più adatta a questo modello serverless ed event-driven.

  

  

---

  

## Capitolo 23: Scelta del Database su AWS: DynamoDB per Costo ed Efficienza

  

  

Nel capitolo precedente, abbiamo fatto un passo da gigante verso un'architettura più resiliente, disaccoppiando le nostre operazioni di scrittura tramite code SQS e funzioni Lambda. Abbiamo costruito un sistema in cui la nostra API può accettare richieste istantaneamente, delegando il lavoro "sporco" della persistenza a un processo in background.

  

  

Questo design, tuttavia, mette in luce una potenziale frizione. Abbiamo parlato di usare un database relazionale come PostgreSQL, ma questo tipo di database è stato progettato in un'era diversa, l'era dei server "always-on". Un database relazionale tradizionale si aspetta di avere un numero limitato di client con connessioni persistenti e di lunga durata. Il nostro nuovo mondo, fatto di centinaia di esecuzioni Lambda concorrenti e di breve durata, può mettere a dura prova questo modello, portando a problemi di esaurimento delle connessioni, colli di bottiglia e costi non ottimali.

  

  

È il momento di mettere in discussione le nostre supposizioni e chiederci: se stiamo costruendo un'applicazione cloud-native e serverless, non dovremmo usare un database nato per questo mondo? In questo capitolo, esploreremo perché **Amazon DynamoDB**, un database NoSQL completamente gestito, non è solo una scelta praticabile, ma spesso la scelta **superiore** per costo, scalabilità ed efficienza in un'architettura come la nostra.

  

  

---

  

  

### 23.1. Il Paradigma Relazionale e i Suoi Limiti nel Mondo Serverless

  

  

Per decenni, il database relazionale (SQL) è stato la scelta di default, quasi istintiva, per la persistenza. Offre un modello di dati strutturato, un linguaggio di query potente e le garanzie transazionali di ACID (Atomicità, Consistenza, Isolamento, Durabilità). Per molti sistemi, è ancora la scelta giusta.

  

  

Tuttavia, quando lo si accoppia con un'architettura basata su AWS Lambda, emergono delle sfide significative:

  

  

1. **Gestione delle Connessioni**: Ogni esecuzione di una funzione Lambda è un ambiente effimero. Se ogni funzione aprisse una nuova connessione a PostgreSQL, esauriremmo rapidamente il numero massimo di connessioni del database. Le soluzioni, come l'uso di **RDS Proxy** per gestire un pool di connessioni, sono efficaci ma aggiungono un altro livello di complessità e un costo aggiuntivo.

  

2. **Scalabilità**: I database relazionali scalano verticalmente (aumentando la potenza della singola macchina) molto bene, ma scalare orizzontalmente (aggiungendo più macchine) è complesso. La gestione di cluster, read replicas e failover richiede un'esperienza operativa non banale.

  

3. **Costi**: Con un database come Amazon RDS (il servizio gestito di AWS per i database relazionali), si paga per l'istanza del server, 24 ore su 24, 7 giorni su 7, indipendentemente dal fatto che stia servendo traffico o meno. Questo va contro il modello "pay-per-use" del paradigma serverless.

  

4. **Rigidità dello Schema**: L'evoluzione di uno schema relazionale richiede migrazioni formali (`ALTER TABLE`), che possono essere operazioni delicate e complesse in un ambiente di deployment continuo.

  

  

Queste sfide non sono insormontabili, ma ci costringono a chiederci se stiamo usando il martello giusto per il chiodo giusto.

  

  

---

  

  

### 23.2. Introduzione a DynamoDB: Un Database Nato per il Cloud ☁️

  

  

DynamoDB è un database NoSQL chiave-valore e di documenti, completamente gestito da AWS. È stato progettato da zero per offrire performance di latenza di millisecondi a singola cifra, a qualsiasi scala.

  

  

Il suo modello mentale è radicalmente diverso da quello di un database SQL.

  

  

**Componenti Fondamentali:**

  

  

- **Tabelle**: Simili alle tabelle SQL, ma non hanno uno schema fisso, se non per la chiave primaria.

  

- **Item**: Simili alle righe. Sono collezioni di attributi.

  

- **Attributi**: Simili alle colonne. Ogni item può avere un set di attributi diverso.

  

- **Chiave Primaria (Primary Key)**: Questo è il concetto più importante. È l'unico elemento richiesto per ogni item e determina in modo univoco la sua posizione. Esistono due tipi di chiavi primarie:

  

    1. **Chiave Semplice (Partition Key)**: Composta da un singolo attributo, chiamato _partition key_ (o PK). DynamoDB usa il valore della PK per partizionare i dati su più server. Tutte le operazioni di lettura/scrittura basate sulla PK sono estremamente veloci.

  

    2. **Chiave Composita (Partition Key + Sort Key)**: Composta da due attributi, la _partition key_ (PK) e la _sort key_ (SK). Tutti gli item con la stessa PK sono memorizzati insieme, ordinati fisicamente in base al valore della SK. Questo permette di eseguire query molto efficienti, come "recupera tutti gli ordini (SK) per un cliente specifico (PK)".

  

  

**Modello di Costo e Throughput:**

  

  

- **On-Demand (A Consumo)**: La scelta ideale per iniziare e per carichi di lavoro imprevedibili. Si paga per ogni singola operazione di lettura e scrittura eseguita. Se non c'è traffico, il costo è zero. Si allinea perfettamente con la filosofia serverless.

  

- **Provisioned (Provisionato)**: Per carichi di lavoro prevedibili, si può "prenotare" una certa capacità di lettura/scrittura (RCU/WCU) a un costo orario inferiore.

  

  

Questo modello elimina completamente i problemi di gestione delle connessioni e di pagamento per risorse inutilizzate. Le nostre funzioni Lambda possono comunicare con DynamoDB tramite semplici chiamate API HTTP, un'interazione stateless che scala all'infinito.

  

  

---

  

  

### 23.3. Progettare il Modello di Dati: L'Arte del Single-Table Design

  

  

Il più grande errore che si possa fare con DynamoDB è provare a usarlo come un database SQL. Il mantra della modellazione relazionale è **normalizzare** (dividere i dati in più tabelle per evitare ridondanze). Il mantra della modellazione DynamoDB è **denormalizzare** e progettare lo schema in base ai **pattern di accesso** (access patterns) della nostra applicazione.

  

  

Una delle tecniche più potenti e controintuitive per chi proviene dal mondo SQL è il **Single-Table Design**.

  

  

> **Definizione**: Nel **Single-Table Design**, si memorizzano diversi tipi di entità (es. `Viaggio`, `Tappa`, `Utente`) all'interno della **stessa tabella DynamoDB**, usando i valori della Partition Key (PK) e della Sort Key (SK) in modo generico per creare relazioni gerarchiche.

  

  

Perché questo approccio è così potente?

  

  

Permette di recuperare collezioni di item eterogenei (es. un aggregato Viaggio con tutte le sue Tappe) con una singola e iper-efficiente chiamata API Query, invece di eseguire costose JOIN come in SQL.

  

  

#### **Applichiamolo a "Where Should I Be?"**

  

  

Definiamo la nostra tabella `whereshouldibe_table`:

  

  

- **Partition Key (PK)**: `TRIP#{tripId}` o `USER#{userId}`

  

- **Sort Key (SK)**: `TRIP_METADATA`, `STOP#{stopId}`, `USER_PROFILE`

  

  

Vediamo come appaiono i nostri dati:

  

  

|PK (string)|SK (string)|`name` (string)|`status` (string)|`placeName` (string)|`email` (string)|...|

  

|---|---|---|---|---|---|---|

  

|`TRIP#uuid-1`|`TRIP_METADATA`|Weekend a Roma|Planning|-|-||

  

|`TRIP#uuid-1`|`STOP#uuid-a`|-|-|Colosseo|-||

  

|`TRIP#uuid-1`|`STOP#uuid-b`|-|-|Fontana di Trevi|-||

  

|`TRIP#uuid-2`|`TRIP_METADATA`|Viaggio in Giappone|Completed|-|-||

  

|`USER#uuid-x`|`USER_PROFILE`|Mario Rossi|-|-|mario.r@ex.com||

  

  

Con questo schema, possiamo soddisfare i nostri pattern di accesso principali:

  

  

1. **Recuperare un intero aggregato `Viaggio` (il viaggio + tutte le sue tappe):**

  

    - `Query` sulla tabella dove `PK = "TRIP#uuid-1"`

  

    - Questa singola chiamata ci restituisce una collezione di item: la riga con SK `TRIP_METADATA` (i dati dell'aggregato root) e tutte le righe con SK che inizia per `STOP#` (le entità figlie). È l'equivalente di una `JOIN` ma con una performance di gran lunga superiore.

  

2. **Recuperare il profilo di un utente:**

  

    - `GetItem` sulla tabella dove `PK = "USER#uuid-x"` e `SK = "USER_PROFILE"`

  

  

#### **Gestire Accessi Secondari con i GSI (Global Secondary Indexes)**

  

  

Cosa succede se abbiamo bisogno di un nuovo pattern di accesso, come "trova tutti i viaggi di un utente"? La nostra chiave primaria non può soddisfarlo. Qui entrano in gioco i **Global Secondary Indexes (GSI)**.

  

  

Un GSI è essenzialmente una "copia" della nostra tabella con una chiave primaria diversa. Possiamo creare un GSI con:

  

  

- **GSI1 PK**: `ownerId` (un attributo che aggiungeremo all'item `TRIP_METADATA`)

  

- **GSI1 SK**: `status` o `creationDate`

  

  

Interrogando questo GSI, possiamo soddisfare query come:

  

  

- `Query` sul GSI1 dove `GSI1_PK = "USER#uuid-x"` -> Otteniamo tutti i viaggi di quell'utente.

  

- `Query` sul GSI1 dove `GSI1_PK = "USER#uuid-x"` e `GSI1_SK` inizia per `Planning` -> Otteniamo tutti i viaggi in pianificazione per quell'utente.

  

  

> **Riferimento Chiave**: Per approfondire il Single-Table Design, le risorse di Alex DeBrie, in particolare il suo libro "The DynamoDB Book", sono considerate il gold standard assoluto.

  

  

---

  

  

### 23.4. Implementare il Repository Go per DynamoDB

  

  

Il nostro `Repository` farà da ponte, nascondendo questa complessità di modellazione.

  

  

Go

  

  

```go

  

// internal/adapters/persistence/dynamodb/dynamo_trip_repo.go

  

package dynamodb

  

  

import (

  

    "github.com/aws/aws-sdk-go-v2/service/dynamodb"

  

    "github.com/aws/aws-sdk-go-v2/feature/dynamodb/attributevalue"

  

    // ...

  

)

  

  

type DynamoDBTripRepository struct {

  

    client    *dynamodb.Client

  

    tableName string

  

}

  

  

func (r *DynamoDBTripRepository) Save(ctx context.Context, t *trip.Trip) error {

  

    // 1. Marshallare l'aggregato in una lista di item DynamoDB

  

    items, err := r.marshalTrip(t)

  

    if err != nil {

  

        return err

  

    }

  

    // 2. Creare una richiesta transazionale di scrittura

  

    // DynamoDB supporta transazioni fino a 100 item.

  

    var writeOps []types.TransactWriteItem

  

    for _, item := range items {

  

        writeOps = append(writeOps, types.TransactWriteItem{

  

            Put: &types.Put{

  

                TableName: &r.tableName,

  

                Item:      item,

  

            },

  

        })

  

    }

  

  

    _, err = r.client.TransactWriteItems(ctx, &dynamodb.TransactWriteItemsInput{

  

        TransactItems: writeOps,

  

    })

  

    return err

  

}

  

  

func (r *DynamoDBTripRepository) marshalTrip(t *trip.Trip) ([]map[string]types.AttributeValue, error) {

  

    // Logica per trasformare l'aggregato Trip in una lista di "righe"

  

    // una per i metadati e una per ogni tappa, con le PK e SK corrette.

  

    // ...

  

}

  

```

  

  

---

  

  

### 23.5. DynamoDB Streams: L'Abbinamento Perfetto per l'Architettura Event-Driven

  

  

**DynamoDB Streams** è una delle funzionalità più potenti e sinergiche con il nostro design. È un flusso ordinato nel tempo di tutte le modifiche (creazioni, aggiornamenti, cancellazioni) che avvengono sugli item di una tabella.

  

  

Possiamo configurare un "trigger" che invochi una **funzione Lambda** ogni volta che si verifica una modifica. Questo sblocca pattern potentissimi:

  

  

- **Replica dei Dati**: Quando un `Viaggio` viene salvato su DynamoDB, lo stream può attivare una Lambda che aggiorna un nostro Read Model su un altro servizio (es. un cluster Elasticsearch per ricerche full-text).

  

- **Notifiche**: Quando lo `status` di un viaggio cambia in `Completed`, una Lambda può essere attivata per inviare un'email di notifica all'utente.

  

- **Aggregazioni**: Una Lambda può ascoltare gli stream per calcolare e aggiornare statistiche in tempo reale.

  

  

Questo completa perfettamente il nostro modello di persistenza asincrona: la Lambda del Capitolo 22 scrive su DynamoDB, e lo stream di DynamoDB può a sua volta innescare altre Lambda per compiti successivi, creando una catena di elaborazione reattiva, serverless e completamente disaccoppiata.

  

  

---

  

  

### 23.6. Conclusioni: Scegliere lo Strumento Giusto per il Lavoro Giusto

  

  

La scelta del database non è una decisione religiosa, ma una scelta ingegneristica basata su trade-off. Mentre un database relazionale è uno strumento familiare e potente, **DynamoDB** offre una serie di vantaggi quasi imbattibili per l'architettura specifica che stiamo costruendo in questo libro:

  

  

- **Scalabilità Infinita e Gestita**: Elimina completamente le preoccupazioni operative.

  

- **Performance Prevedibili**: Latenze a millisecondi a singola cifra, indipendentemente dalla scala.

  

- **Modello di Costo Serverless**: Il modello On-Demand si allinea perfettamente con Lambda, permettendoci di pagare solo per ciò che usiamo.

  

- **Integrazione Nativia con l'Ecosistema AWS**: L'accoppiata con Lambda tramite trigger diretti o DynamoDB Streams è un superpotere per le architetture event-driven.

  

  

Il prezzo da pagare è un cambio di paradigma. Richiede di abbandonare l'abitudine alla normalizzazione e di abbracciare la modellazione basata sui pattern di accesso. Ma per un'applicazione cloud-native, scalabile ed efficiente, è un investimento che ripaga esponenzialmente. Con DynamoDB come base della nostra persistenza, siamo pronti a costruire un sistema veramente enterprise.

  

  

---

  

## Capitolo 24: Una Strategia di Testing Completa

  

  

Finora, in questa parte del libro, abbiamo progettato un'architettura di persistenza potente e scalabile, basata su servizi cloud-native come SQS, Lambda e DynamoDB. Abbiamo costruito un sistema distribuito, asincrono e resiliente. Ma con questa potenza arriva una nuova sfida: **come possiamo essere sicuri che tutto funzioni?** Come possiamo avere la fiducia di modificare, estendere e deployare il nostro codice sapendo di non aver rotto nulla?

  

  

La risposta non risiede in un singolo tipo di test, ma in una **strategia di testing multi-livello**. In questo capitolo, abbandoneremo l'idea del testing come un'attività manuale e noiosa da fare alla fine del ciclo di sviluppo. Invece, la tratteremo come una disciplina ingegneristica fondamentale, uno strumento di design che ci permette di costruire software di alta qualità, manutenibile e robusto.

  

  

Esploreremo la "Piramide del Testing" e vedremo come applicarla concretamente alla nostra architettura basata su Go, DDD e AWS, scrivendo test unitari, di integrazione e end-to-end per garantire la correttezza del nostro sistema "Where Should I Be?".

  

  

---

  

  

### 24.1. La Piramide del Testing: Un Modello per la Qualità pyramids

  

  

La Piramide del Testing è un modello concettuale che ci aiuta a pensare e a bilanciare i nostri sforzi di testing. Suggerisce che dovremmo avere diversi tipi di test e che il loro numero dovrebbe essere inversamente proporzionale al loro costo e alla loro lentezza.

  

  

_(Fonte: Martin Fowler)_

  

  

1. **Test Unitari (Unit Tests)** - La Base della Piramide:

  

    - **Scopo**: Verificare una piccola unità di codice (una funzione, un metodo) in completo isolamento.

  

    - **Caratteristiche**: Sono numerosissimi, estremamente veloci da eseguire (millisecondi), economici da scrivere e mantenere. Costituiscono il fondamento della nostra rete di sicurezza.

  

2. **Test di Integrazione (Integration Tests)** - Il Centro della Piramide:

  

    - **Scopo**: Verificare che diverse unità di codice (o componenti) collaborino correttamente. Ad esempio, testare che il nostro repository possa effettivamente parlare con un database.

  

    - **Caratteristiche**: Sono meno numerosi dei test unitari, più lenti (da secondi a minuti) e più costosi da scrivere e mantenere, perché richiedono un ambiente più complesso.

  

3. **Test End-to-End (E2E)** - La Cima della Piramide:

  

    - **Scopo**: Verificare un intero flusso utente attraverso tutti i livelli dell'applicazione, dal frontend al backend fino al database, in un ambiente che simula la produzione.

  

    - **Caratteristiche**: Sono pochissimi, molto lenti (minuti) ed estremamente fragili e costosi. Vanno riservati solo per i percorsi critici dell'applicazione.

  

  

La regola d'oro della piramide è: **scrivere test al livello più basso possibile**. Se una logica può essere verificata da un test unitario, è lì che dovrebbe essere testata.

  

  

---

  

  

### 24.2. Livello 1: Test Unitari - Il Nostro Fondamento 🔬

  

  

I test unitari sono il nostro pane quotidiano. Grazie alla **Clean Architecture** che abbiamo adottato, scrivere test unitari per la maggior parte del nostro codice è incredibilmente semplice.

  

  

#### **Testare il Dominio**

  

  

Il nostro layer di dominio (Aggregati, Entità, Value Objects) non ha dipendenze infrastrutturali. È Go puro. Questo lo rende perfettamente testabile in isolamento.

  

  

Esempio: Testare l'Aggregato Viaggio

  

  

Vogliamo verificare che la regola di business "non si possono aggiungere tappe a un viaggio completato" sia rispettata.

  

  

Go

  

  

```go

  

// internal/domain/trip/trip_test.go

  

package trip_test

  

  

import (

  

    "testing"

  

    "github.com/stretchr/testify/assert" // Una libreria di asserzioni molto popolare

  

    // ... import dei nostri package di dominio ...

  

)

  

  

func TestTrip_AddStop_FailsIfTripIsCompleted(t *testing.T) {

  

    // Arrange: prepariamo lo stato iniziale

  

    // Creiamo un viaggio e lo portiamo allo stato "Completed"

  

    trip, _ := trip.New(...) // Usiamo la nostra factory

  

    trip.Start()

  

    trip.Complete() // Metodo che cambia lo stato

  

  

    // Act: eseguiamo l'azione da testare

  

    err := trip.AddStop(...) // Proviamo ad aggiungere una tappa

  

  

    // Assert: verifichiamo il risultato

  

    assert.Error(t, err) // Ci aspettiamo un errore

  

    assert.Equal(t, "cannot add stop to a completed trip", err.Error())

  

}

  

```

  

  

Questo test è auto-contenuto, non richiede database o server, e viene eseguito in una frazione di secondo.

  

  

#### **Testare i Servizi Applicativi (Use Cases)**

  

  

I nostri `Application Services` dipendono da interfacce (le "porte"), come `TripRepository`. Per testarli in isolamento, usiamo i **mock**. Un mock è un'implementazione fittizia di un'interfaccia, usata per simulare il comportamento di una dipendenza e verificare le interazioni.

  

  

> **Riferimento Chiave**: La libreria `github.com/stretchr/testify` offre un eccellente package `mock` che semplifica la creazione di oggetti mock in Go.

  

  

**Esempio: Testare `TripApplicationService`**

  

  

Go

  

  

```go

  

// internal/application/trip_service_test.go

  

package application_test

  

  

import (

  

    "testing"

  

    "context"

  

    "github.com/stretchr/testify/mock"

  

    // ...

  

)

  

  

// 1. Creiamo la struct del mock

  

type MockTripRepository struct {

  

    mock.Mock

  

}

  

  

// 2. Implementiamo l'interfaccia TripRepository per il mock

  

func (m *MockTripRepository) Save(ctx context.Context, t *trip.Trip) error {

  

    args := m.Called(ctx, t)

  

    return args.Error(0)

  

}

  

// ... implementiamo anche gli altri metodi dell'interfaccia ...

  

  

func TestTripApplicationService_CreateNewTrip(t *testing.T) {

  

    // Arrange

  

    mockRepo := new(MockTripRepository)

  

    appService := application.NewTripApplicationService(mockRepo)

  

    // Definiamo l'aspettativa: ci aspettiamo che il metodo Save

  

    // venga chiamato esattamente una volta con qualsiasi context e qualsiasi

  

    // puntatore a un trip. Se chiamato, deve restituire 'nil' (nessun errore).

  

    mockRepo.On("Save", mock.Anything, mock.AnythingOfType("*trip.Trip")).Return(nil)

  

  

    // Act

  

    _, err := appService.CreateNewTrip(context.Background(), "Mio Viaggio", ...)

  

  

    // Assert

  

    assert.NoError(t, err)

  

    // Verifichiamo che tutte le aspettative definite sul mock siano state soddisfatte.

  

    mockRepo.AssertExpectations(t)

  

}

  

```

  

  

---

  

  

### 24.3. Livello 2: Test di Integrazione - Verificare le Collaborazioni 🔗

  

  

I test di integrazione verificano che i nostri "adattatori" (come i repository) funzionino correttamente con i servizi esterni reali (come un database).

  

  

#### **Testare i Repository con `testcontainers-go`**

  

  

Come possiamo testare il nostro `DynamoDBTripRepository` contro un vero DynamoDB senza doverne gestire un'installazione manuale? La risposta è **Testcontainers**.

  

  

> **Riferimento Chiave**: `testcontainers-go` è una libreria Go che permette di avviare e gestire istanze di servizi (database, code, ecc.) all'interno di container Docker, direttamente dal nostro codice di test.

  

  

Questo ci permette di avere un ambiente pulito e isolato per ogni esecuzione dei test di integrazione.

  

  

**Esempio: Testare `DynamoDBTripRepository`**

  

  

Go

  

  

```go

  

// internal/adapters/persistence/dynamodb/dynamo_repo_integration_test.go

  

  

//go:build integration // Un build tag per separare questi test lenti

  

  

package dynamodb_test

  

  

import (

  

    "testing"

  

    "context"

  

    "github.com/testcontainers/testcontainers-go"

  

    "github.com/testcontainers/testcontainers-go/modules/dynamodb"

  

    // ...

  

)

  

  

func TestDynamoDBTripRepository_SaveAndFind(t *testing.T) {

  

    ctx := context.Background()

  

  

    // Arrange: Avviamo un container Docker con DynamoDB Local

  

    dynamoContainer, err := dynamodb.RunContainer(ctx,

  

        testcontainers.WithImage("amazon/dynamodb-local:latest"),

  

    )

  

    assert.NoError(t, err)

  

    // Assicuriamoci che il container venga terminato alla fine del test

  

    defer dynamoContainer.Terminate(ctx)

  

  

    // Creiamo il client DynamoDB che punta al container

  

    client, err := dynamoContainer.GetClient(ctx)

  

    assert.NoError(t, err)

  

  

    // Creiamo la tabella per il nostro test

  

    // ... codice per creare la tabella `whereshouldibe_table` ...

  

  

    // Creiamo l'istanza del repository da testare

  

    repo := dynamodb.NewDynamoDBTripRepository(client, "whereshouldibe_table")

  

  

    // Act

  

    newTrip := trip.New(...)

  

    err = repo.Save(ctx, newTrip)

  

    assert.NoError(t, err)

  

  

    foundTrip, err := repo.FindByID(ctx, newTrip.ID())

  

    // Assert

  

    assert.NoError(t, err)

  

    assert.NotNil(t, foundTrip)

  

    assert.Equal(t, newTrip.ID(), foundTrip.ID())

  

    assert.Equal(t, newTrip.Name(), foundTrip.Name())

  

}

  

```

  

  

Questo test ci dà la massima fiducia che il nostro codice di mappatura e le query verso DynamoDB siano corretti.

  

  

---

  

  

### 24.4. Livello 3: Test End-to-End (E2E) - Simulare il Mondo Reale 🌐

  

  

I test E2E sono la cima della piramide. Verificano un intero flusso di business dal punto di vista dell'utente. Sono pochi e preziosi.

  

  

**Scopo**: Simulare un utente reale che interagisce con il nostro frontend SvelteKit, che a sua volta chiama le API del nostro backend, che interagisce con i servizi AWS.

  

  

**Strumenti**: Useremo un framework di browser automation come **Cypress** o **Playwright**.

  

  

**Flusso di Test E2E per "Crea un Viaggio":**

  

  

1. **Setup**: Lo script di test si assicura che l'applicazione sia deployata in un ambiente di test dedicato su AWS.

  

2. **Azione (UI)**: Lo script, tramite Cypress, apre un browser, naviga alla nostra app SvelteKit, si registra e/o effettua il login.

  

3. **Azione (UI)**: Naviga alla pagina di creazione viaggio, compila il form con "Viaggio a Tokyo" e clicca "Salva".

  

4. **Asserzione (UI)**: Lo script verifica che nella dashboard dei viaggi appaia una card con "Viaggio a Tokyo".

  

5. **Asserzione (API/DB)**: (Opzionale ma potente) Lo script può fare una chiamata diretta all'API di backend o interrogare il database per verificare che i dati siano stati persistiti correttamente.

  

6. **Cleanup**: Lo script cancella il viaggio e l'utente creati per mantenere l'ambiente pulito.

  

  

Questi test sono lenti e possono essere instabili ("flaky"), ma sono insostituibili per verificare che tutti i pezzi del nostro sistema distribuito comunichino correttamente.

  

  

---

  

  

### 24.5. Testare le Architetture Serverless (Lambda e SQS)

  

  

Testare le nostre Lambda asincrone presenta sfide uniche.

  

  

- **Test Unitari**: La logica interna della nostra funzione Lambda (`HandleRequest`) è solo una funzione Go. Possiamo testarla unitariamente chiamandola direttamente nel nostro test e passandole un oggetto `events.SQSEvent` fittizio.

  

- **Test di Integrazione Locali**: Strumenti come **AWS SAM (Serverless Application Model) CLI** permettono di invocare le nostre funzioni Lambda localmente in un ambiente Docker che simula l'ambiente di esecuzione di AWS. Questo è utile per testare la funzione in un contesto più realistico senza deployare.

  

- **Test di Integrazione nel Cloud**: L'approccio con la massima fedeltà. La nostra pipeline di CI/CD deploya l'intera architettura (SQS, Lambda, DynamoDB) su un ambiente AWS di `staging` o `testing`. A questo punto, i nostri test di integrazione inviano un messaggio reale alla coda SQS e verificano (magari interrogando il DynamoDB) che la Lambda lo abbia processato correttamente.

  

  

---

  

  

### 24.6. Conclusioni: La Qualità come Disciplina

  

  

Una strategia di testing completa non è un'opzione, ma un requisito fondamentale per costruire software enterprise di alta qualità. Non è un'attività da relegare alla fine, ma una disciplina che permea l'intero ciclo di vita dello sviluppo.

  

  

Adottando la Piramide del Testing, abbiamo imparato a:

  

  

- **Verificare la logica di business** in isolamento con test unitari veloci e affidabili, resi possibili dalla nostra Clean Architecture.

  

- **Garantire la corretta collaborazione** tra i nostri componenti e i servizi esterni con test di integrazione robusti, usando strumenti moderni come Testcontainers.

  

- **Convalidare i flussi utente critici** attraverso l'intero sistema con un piccolo numero di test E2E mirati.

  

  

Questa rete di sicurezza ci dà la fiducia necessaria per innovare, refattorizzare e deployare il nostro codice frequentemente, sapendo che la qualità del nostro lavoro è costantemente protetta.

  

  

---

  

# **Parte VII: Sviluppo, Deployment e Operations**

  

  

## Capitolo 25: Frontend Moderno con SvelteKit

  

  

Benvenuti nella parte finale del nostro viaggio. Abbiamo dedicato la maggior parte di questo libro a progettare e costruire un backend eccezionalmente robusto, scalabile e manutenibile. Abbiamo esplorato i meandri del Domain-Driven Design, della Clean Architecture e della persistenza su AWS. Abbiamo un motore potente, ma un motore senza un telaio, delle ruote e un volante è un'opera d'arte incompleta e inutilizzabile.

  

  

L'interfaccia utente è il punto di contatto finale con i nostri utenti. È dove tutta la complessità e la potenza che abbiamo costruito vengono finalmente tradotte in valore tangibile. La scelta della tecnologia frontend non è quindi un dettaglio secondario, ma una decisione architetturale critica che impatta la performance, la manutenibilità e, soprattutto, l'esperienza utente.

  

  

In un mondo frontend dominato da framework complessi e da una grande quantità di boilerplate, abbiamo scelto un approccio diverso, più snello e performante: **SvelteKit**. In questo capitolo, esploreremo perché SvelteKit è il partner perfetto per il nostro backend Go e come ci permette di costruire interfacce utente moderne in modo più semplice, veloce ed efficiente.

  

  

---

  

  

### 25.1. Perché Svelte? Il Framework che Scompare

  

  

Per capire SvelteKit, dobbiamo prima capire **Svelte**. Svelte si autodefinisce "il framework che scompare" e questa non è solo una trovata di marketing, ma la sua filosofia fondamentale. A differenza di framework come React o Vue, che spediscono una pesante libreria runtime al browser dell'utente per gestire un **Virtual DOM (VDOM)**, Svelte adotta un approccio radicalmente diverso.

  

  

> **Svelte non è una libreria, è un compilatore.**

  

  

Invece di fare il lavoro pesante nel browser, Svelte lo fa durante la fase di **compilazione**. Prende i nostri file `.svelte` (che assomigliano a semplice HTML, CSS e JavaScript) e li compila in codice JavaScript vanilla, piccolo, efficiente e altamente ottimizzato, che manipola direttamente il DOM. Quando la nostra applicazione viene eseguita, il "framework" è già scomparso.

  

  

Questo approccio porta a benefici enormi:

  

  

1. **Meno Codice, Meno Complessità**: La sintassi di Svelte è estremamente concisa e intuitiva. Non c'è bisogno di `useState`, `useEffect` o di imparare una sintassi di template complessa.

  

    **Controesempio: Un contatore in React vs. Svelte**

  

    JavaScript

  

    ```javascript

  

    // React

  

    import { useState } from 'react';

  

    function Counter() {

  

      const [count, setCount] = useState(0);

  

      return <button onClick={() => setCount(count + 1)}>Clicks: {count}</button>;

  

    }

  

    ```

  

    HTML

  

    ```html

  

    <script>

  

      let count = 0;

  

    </script>

  

    <button on:click={() => count += 1}>Clicks: {count}</button>

  

    ```

  

2. **Reattività Chirurgica**: La reattività in Svelte è "gratuita". Basta assegnare un nuovo valore a una variabile e il compilatore Svelte si occupa di generare il codice minimo indispensabile per aggiornare il DOM. È un approccio chirurgico, non c'è bisogno di un intero VDOM che calcoli le differenze.

  

3. **Performance Eccezionali**: Poiché non c'è un runtime pesante da caricare e nessun VDOM da calcolare nel browser, le applicazioni Svelte sono più piccole, si avviano più velocemente e hanno performance migliori, specialmente su dispositivi a basse prestazioni.

  

  

---

  

  

### 25.2. SvelteKit: Il Framework Applicativo Full-Stack

  

  

Se Svelte è il motore per costruire componenti UI, **SvelteKit** è l'automobile completa. È un framework applicativo full-stack, costruito sopra Svelte, che fornisce tutto il necessario per creare applicazioni web complesse e robuste. È per Svelte ciò che Next.js è per React.

  

  

Le caratteristiche principali di SvelteKit che lo rendono perfetto per il nostro progetto sono:

  

  

#### **Routing basato su File System**

  

  

La struttura delle URL della nostra applicazione è definita direttamente dalla struttura delle directory in `src/routes`.

  

  

- `src/routes/+page.svelte` -> La nostra homepage (`/`)

  

- `src/routes/trips/+page.svelte` -> La pagina della dashboard dei viaggi (`/trips`)

  

- `src/routes/trips/[tripId]/+page.svelte` -> La pagina di dettaglio per un viaggio specifico (`/trips/123-abc`). Il parametro `tripId` è dinamicamente disponibile.

  

  

Questo approccio è intuitivo e rende l'organizzazione del progetto immediatamente comprensibile.

  

  

#### **Data Loading Universale**

  

  

Questa è la funzionalità più potente di SvelteKit per la nostra architettura. Per ogni pagina, possiamo definire una funzione `load` che si occupa di caricare i dati necessari prima che la pagina venga renderizzata.

  

  

- `+page.server.ts`: Questo file esporta una funzione `load` che viene eseguita **esclusivamente sul server**. È il luogo perfetto e sicuro per fare chiamate al nostro backend Go, usare chiavi API segrete o accedere direttamente a un database. I dati caricati qui vengono poi passati in modo sicuro al componente della pagina.

  

- `+page.ts`: Esporta una funzione `load` che viene eseguita sul server durante la prima visita e poi sul client durante le navigazioni successive. Utile per chiamare API pubbliche.

  

  

Per "Where Should I Be?", useremo quasi esclusivamente i file `+page.server.ts` per comunicare in modo sicuro con i nostri microservizi backend.

  

  

#### **Form Actions e Progressive Enhancement**

  

  

SvelteKit ha un sistema integrato per la gestione dei form, chiamato **Actions**. Permette di definire funzioni lato server che gestiscono l'invio di un form. L'aspetto migliore è che funziona anche se JavaScript è disabilitato (progressive enhancement), ma quando JavaScript è attivo, SvelteKit gestisce il tutto in modo asincrono senza un ricaricamento completo della pagina, offrendo un'esperienza utente moderna.

  

  

---

  

  

### 25.3. Costruire la Pagina di Dettaglio di un Viaggio

  

  

Vediamo come tutti questi pezzi si uniscono per costruire la pagina `/trips/[tripId]`.

  

  

#### **Passo 1: Caricare i Dati sul Server (`+page.server.ts`)**

  

  

Creiamo un file per definire la nostra funzione `load` lato server. Questa funzione utilizzerà il **client API tipizzato che abbiamo generato con OpenAPI** nel Capitolo 19.

  

  

TypeScript

  

  

```TypeScript

  

// src/routes/trips/[tripId]/+page.server.ts

  

import { error } from '@sveltejs/kit';

  

import type { PageServerLoad } from './$types';

  

import { api } from '$lib/server/api'; // Il nostro client API generato

  

  

export const load: PageServerLoad = async ({ params, fetch }) => {

  

    console.log(`Caricamento dati per il viaggio: ${params.tripId}`);

  

  

    try {

  

        // Usiamo il client API generato per chiamare il nostro backend Go.

  

        // La chiamata è sicura, avviene server-to-server.

  

        // `fetch` viene passato da SvelteKit per poter fare chiamate autenticate.

  

        const tripDetail = await api.getTripById(params.tripId, {

  

            fetch: fetch, // Passiamo il fetch di SvelteKit per inoltrare i cookie/header

  

        });

  

  

        if (!tripDetail) {

  

            throw error(404, 'Viaggio non trovato');

  

        }

  

  

        return {

  

            trip: tripDetail, // Passiamo i dati al componente della pagina

  

        };

  

    } catch (e) {

  

        // Gestione degli errori

  

        console.error('Errore nel caricamento del viaggio:', e);

  

        throw error(500, 'Impossibile caricare i dati del viaggio');

  

    }

  

};

  

```

  

  

#### **Passo 2: Renderizzare il Componente UI (`+page.svelte`)**

  

  

Ora creiamo il componente Svelte che riceverà e visualizzerà i dati.

  

  

HTML

  

  

```html

  

<script lang="ts">

  

  import type { PageData } from './$types';

  

  

  // SvelteKit passa automaticamente i dati dalla funzione 'load'

  

  // a questa prop 'data'. È tutto tipizzato!

  

  export let data: PageData;

  

  

  // Assegnamo i dati a una variabile più comoda

  

  const { trip } = data;

  

</script>

  

  

<div class="container mx-auto p-4">

  

  <h1 class="text-3xl font-bold mb-2">{trip.name}</h1>

  

  <span class="badge badge-primary">{trip.status}</span>

  

  

  <div class="my-4">

  

    <p>Dal: {new Date(trip.startDate).toLocaleDateString()}</p>

  

    <p>Al: {new Date(trip.endDate).toLocaleDateString()}</p>

  

  </div>

  

  

  <h2 class="text-2xl font-semibold mt-6 mb-3">Tappe del Viaggio</h2>

  

  {#if trip.stops && trip.stops.length > 0}

  

    <ul class="list-disc pl-5">

  

      {#each trip.stops as stop}

  

        <li>

  

          <span class="font-medium">{stop.placeName}</span> (Giorno {stop.day})

  

        </li>

  

      {/each}

  

    </ul>

  

  {:else}

  

    <p>Nessuna tappa ancora aggiunta a questo viaggio.</p>

  

  {/if}

  

</div>

  

  

```

  

  

Questo codice è pulito, leggibile e potente. La logica di caricamento dei dati è nettamente separata dalla logica di presentazione, e l'integrazione con il nostro backend è sicura e tipizzata.

  

  

---

  

  

### 25.4. Gestione dello Stato Globale con gli Stores

  

  

Per lo stato che deve essere condiviso tra diversi componenti (come le informazioni sull'utente autenticato), Svelte offre un meccanismo semplice e potente: gli **Stores**. Uno store è semplicemente un oggetto con un metodo `subscribe` a cui i componenti possono "abbonarsi" per ricevere notifiche sui cambiamenti.

  

  

Svelte fornisce delle implementazioni già pronte:

  

  

- `writable`: Uno store il cui valore può essere impostato e aggiornato dall'esterno.

  

- `readable`: Uno store il cui valore può essere impostato solo dall'interno (es. per dati che arrivano da un WebSocket).

  

- `derived`: Uno store il cui valore è derivato da uno o più altri stores.

  

  

Per "Where Should I Be?", potremmo creare un `userStore` per tenere traccia dello stato di autenticazione dell'utente, accessibile da qualsiasi punto della nostra UI.

  

  

---

  

  

### 25.5. Riepilogo dell'Integrazione con il Backend

  

  

Vediamo come il nostro stack completo collabora:

  

  

1. **Il Contratto**: Il file `api.yaml` (OpenAPI) è la fonte di verità che definisce l'API tra SvelteKit e il backend Go.

  

2. **Il Codice Generato**: `oapi-codegen` (per Go) e `openapi-typescript-codegen` (per SvelteKit) generano il codice boilerplate, garantendo la coerenza.

  

3. **L'Autenticazione**: L'app SvelteKit gestisce il flusso di login con Cognito (Capitolo 4). Memorizza il JWT ricevuto e lo passa al client API.

  

4. **Il Caricamento dei Dati**: Le funzioni `load` in `+page.server.ts` usano il client API tipizzato per chiamare in modo sicuro gli endpoint del nostro backend Go.

  

5. **CORS**: Il nostro server Go deve essere configurato con una policy CORS (Cross-Origin Resource Sharing) per accettare le richieste provenienti dal dominio della nostra app SvelteKit.

  

  

---

  

  

### 25.6. Conclusioni: Un Frontend Degno di un Backend Robusto

  

  

La scelta di SvelteKit per il nostro progetto non è casuale. La sua filosofia di semplicità, performance e una superba esperienza di sviluppo si sposa perfettamente con l'etica di Go.

  

  

- **Elimina la complessità inutile**, permettendoci di concentrarci sulla costruzione di interfacce utente efficaci.

  

- Il suo **modello di data loading server-side** fornisce un meccanismo naturale e sicuro per interagire con i nostri microservizi backend.

  

- La combinazione di un backend Go ben architettato, un frontend SvelteKit moderno e un contratto OpenAPI che li unisce, rappresenta un'architettura **full-stack professionale, performante e piacevole da sviluppare**.

  

  

Con la nostra interfaccia utente in costruzione, siamo ora pronti ad affrontare gli ultimi capitoli, dedicati al processo di sviluppo, al deployment continuo e al monitoraggio della nostra applicazione in produzione.

  

  

---

  

## Capitolo 26: Il Ciclo di Sviluppo Iterativo di Due Settimane

  

  

Abbiamo percorso un lungo cammino. Abbiamo un'architettura robusta basata sui principi del Domain-Driven Design e della Clean Architecture. Abbiamo scelto le nostre tecnologie, dal backend in Go al frontend in SvelteKit, passando per i servizi cloud di AWS. Abbiamo definito come testare il nostro sistema per garantirne la qualità. Ora, ci troviamo di fronte a una domanda fondamentale: **come tradiamo tutto questo design in software funzionante, consegnato agli utenti?**

  

  

Un grande design è inutile se il processo per realizzarlo è caotico o inefficiente. L'approccio "Waterfall", dove si progetta tutto per mesi per poi costruire per altri mesi, è troppo rigido per il mondo moderno, dove i requisiti cambiano e l'apprendimento è continuo. D'altra parte, un approccio senza alcuna struttura porta al caos, al debito tecnico e a scadenze mancate.

  

  

La soluzione risiede nell'adottare un processo di sviluppo **iterativo e incrementale**. In questo capitolo, definiremo il nostro "battito cardiaco" operativo: un ciclo di sviluppo di **due settimane**, spesso chiamato **Sprint**. Questo ritmo ci fornirà la struttura per pianificare, costruire e adattarci, permettendoci di navigare la complessità dello sviluppo e di fornire valore ai nostri utenti in modo prevedibile e sostenibile.

  

  

---

  

  

### 26.1. Perché Due Settimane? Il Ritmo dello Sviluppo (The Rhythm of Development)

  

  

La scelta della durata di un ciclo di sviluppo (o Sprint) è strategica. Un ciclo di due settimane offre un equilibrio quasi perfetto per la maggior parte dei team e dei progetti, inclusa la nostra applicazione "Where Should I Be?".

  

  

- **È abbastanza lungo per costruire qualcosa di significativo**: In due settimane, un team di sviluppo può completare una o più funzionalità verticali (dall'interfaccia utente al database), producendo un incremento di valore tangibile che può essere mostrato e discusso.

  

- **È abbastanza corto per un feedback rapido**: Il vantaggio più grande dell'agilità è la capacità di adattarsi. Se, alla fine di due settimane, ci accorgiamo che una funzionalità non è quella che gli utenti vogliono o che stiamo seguendo un percorso tecnico sbagliato, abbiamo perso al massimo due settimane di lavoro. Questo riduce drasticamente il rischio rispetto a cicli di sviluppo di mesi.

  

- **Crea una cadenza prevedibile**: Il ripetersi di un ciclo di due settimane (pianificazione, sviluppo, revisione, retrospettiva) crea un ritmo costante e prevedibile. Questa cadenza è rassicurante per il team, che sa cosa aspettarsi, e utile per il business, che può avere una visibilità più chiara sui progressi e sulle previsioni di rilascio.

  

  

Un ciclo più lungo (es. un mese) rischia di trasformarsi in un mini-waterfall, mentre un ciclo più corto (es. una settimana) può essere stressante e l'overhead delle "cerimonie" (riunioni di pianificazione, ecc.) può diventare sproporzionato rispetto al tempo di sviluppo effettivo.

  

  

---

  

  

### 26.2. Gli Attori del Processo: Ruoli e Responsabilità

  

  

Perché il nostro processo funzioni, abbiamo bisogno di ruoli chiari. Ispirandoci al framework **Scrum**, definiamo tre ruoli principali:

  

  

#### **Il Product Owner (o Product Manager)**

  

  

È la **voce del business e dell'utente**. La sua responsabilità principale è massimizzare il valore del prodotto risultante dal lavoro del team.

  

  

- **Gestisce il Product Backlog**: Una lista ordinata di tutto ciò che è desiderato nel prodotto.

  

- **Prioritizza**: Decide l'ordine degli elementi nel backlog per focalizzare il team sulle cose più importanti.

  

- **Definisce il "Cosa" e il "Perché"**: Comunica chiaramente la visione e gli obiettivi di ogni funzionalità.

  

  

#### **Il Team di Sviluppo (The Development Team)**

  

  

È il cuore pulsante del processo. Un gruppo cross-funzionale di professionisti che possiedono le competenze per trasformare gli elementi del backlog in un incremento di software funzionante.

  

  

- **Composizione**: Nel nostro caso, include sviluppatori Go, sviluppatori SvelteKit, esperti di AWS e tester.

  

- **Auto-organizzazione**: Il team decide _come_ trasformare il lavoro richiesto in software funzionante. Nessuno, nemmeno il Product Owner o lo Scrum Master, dice al team come eseguire il proprio lavoro tecnico.

  

- **Responsabilità**: Creare un incremento di alta qualità che rispetti la "Definition of Done" (definizione di "fatto").

  

  

#### **Lo Scrum Master (o Team Lead / Agile Coach)**

  

  

È il **facilitatore e il custode del processo**. È un _servant-leader_ per il team.

  

  

- **Rimuove gli Ostacoli (Impediments)**: Qualsiasi cosa che rallenti o blocchi il team di sviluppo è un problema che lo Scrum Master deve aiutare a risolvere.

  

- **Protegge il Team**: Difende il team da interferenze esterne e distrazioni durante lo sprint.

  

- **Insegna e Guida**: Si assicura che il team comprenda e segua i principi e le pratiche agili, facilitando le cerimonie e promuovendo il miglioramento continuo.

  

  

---

  

  

### 26.3. Gli Artefatti del Lavoro: Rendere Tutto Visibile

  

  

Il processo si basa su alcuni "artefatti" chiave che rendono il lavoro e il progresso trasparenti a tutti.

  

  

- **Product Backlog**: La lista completa e ordinata di tutte le funzionalità, requisiti, miglioramenti e fix desiderati per il prodotto. È un documento vivo, che viene costantemente perfezionato (un processo chiamato _refinement_ o _grooming_).

  

- **Sprint Backlog**: Il sottoinsieme di elementi del Product Backlog che il Team di Sviluppo seleziona per uno Sprint. Include anche il piano per consegnare questi elementi. Una volta definito all'inizio dello Sprint, solo il Team di Sviluppo può modificarlo.

  

- **Incremento (Increment)**: La somma di tutti gli elementi del backlog completati durante uno Sprint, integrata con il lavoro di tutti gli Sprint precedenti. Al termine di uno Sprint, il nuovo Incremento deve essere "potenzialmente rilasciabile", il che significa che deve essere testato, integrato e funzionante.

  

  

---

  

  

### 26.4. Le Cerimonie: Il Ciclo di Vita di Due Settimane 🗓️

  

  

Il nostro ciclo di due settimane è scandito da una serie di riunioni (o "cerimonie"), ognuna con uno scopo preciso.

  

  

#### **Giorno 1: Sprint Planning (Pianificazione - max 4 ore)**

  

  

- **Scopo**: Definire il lavoro da svolgere nello Sprint.

  

- **Come funziona**:

  

    1. Il Product Owner propone l'obiettivo dello Sprint e presenta gli elementi più importanti del Product Backlog.

  

    2. Il Team di Sviluppo fa domande per capire a fondo ogni elemento (qui il nostro **Linguaggio Ubiquo** è fondamentale!).

  

    3. Il team seleziona gli elementi che ritiene di poter completare nello Sprint, creando lo **Sprint Backlog**.

  

    4. Il team definisce uno **Sprint Goal**: una singola frase che descrive l'obiettivo principale dello Sprint, fornendo uno scopo comune.

  

- **Esempio di Sprint Goal**: "Un utente può registrarsi, accedere e visualizzare una dashboard vuota dei suoi viaggi."

  

  

#### **Ogni Giorno: Daily Stand-up (15 minuti)**

  

  

- **Scopo**: Sincronizzare il team e identificare ostacoli. Non è una riunione di reporting.

  

- **Come funziona**: Ogni membro del team risponde brevemente a tre domande:

  

    1. _Cosa ho fatto ieri per aiutare il team a raggiungere lo Sprint Goal?_

  

    2. _Cosa farò oggi per aiutare il team a raggiungere lo Sprint Goal?_

  

    3. _Vedo qualche ostacolo che impedisce a me o al team di raggiungere lo Sprint Goal?_

  

  

#### **Ultimo Giorno: Sprint Review (Revisione - max 2 ore)**

  

  

- **Scopo**: Ispezionare l'Incremento e ottenere feedback dagli stakeholder.

  

- **Come funziona**:

  

    - È una sessione informale, non una presentazione formale.

  

    - Il Team di Sviluppo fa una **demo dal vivo** del software funzionante che ha costruito.

  

    - Il Product Owner e gli altri stakeholder forniscono feedback, fanno domande e discutono su cosa fare dopo.

  

    - Il Product Backlog può essere aggiornato sulla base di questo feedback.

  

  

#### **Ultimo Giorno: Sprint Retrospective (Retrospettiva - max 1.5 ore)**

  

  

- **Scopo**: Ispezionare e migliorare il **processo** di lavoro del team. È la cerimonia più importante per il miglioramento continuo.

  

- **Come funziona**:

  

    - Partecipano solo il Team di Sviluppo e lo Scrum Master. È uno spazio sicuro.

  

    - Il team discute apertamente su: **Cosa è andato bene? Cosa potrebbe essere migliorato? Quali azioni concrete intraprenderemo nel prossimo Sprint per migliorare?**

  

    - Esempi di azioni: "Miglioriamo la definizione delle nostre user story", "Automatizziamo quel test manuale che ci rallenta", "Dedichiamo del tempo per ridurre il debito tecnico nel modulo X".

  

  

---

  

  

### 26.5. Mettere Tutto Insieme: Uno Sprint Esempio per "Where Should I Be?"

  

  

Immaginiamo di essere all'inizio del nostro progetto.

  

  

- **Sprint Goal**: "L'utente può creare un nuovo viaggio e vederlo nella sua dashboard."

  

- **Sprint Backlog (User Stories)**:

  

    1. _Come utente registrato, voglio vedere un pulsante "Nuovo Viaggio" sulla mia dashboard per poter iniziare la pianificazione._

  

    2. _Come utente, quando clicco "Nuovo Viaggio", voglio vedere un form dove posso inserire il nome del viaggio, una data di inizio e una data di fine._

  

    3. _Come utente, quando invio il form, il nuovo viaggio deve essere salvato e voglio essere reindirizzato alla mia dashboard._

  

    4. _Come utente, voglio vedere il viaggio appena creato apparire come una "card" nella mia dashboard._

  

- **Lavoro del Team durante lo Sprint**:

  

    - Il team scompone queste storie in task tecnici:

  

        - _Backend_: Creare l'endpoint `POST /trips` nell'API Gateway.

  

        - _Backend_: Implementare il caso d'uso `CreateTrip` nell'Application Service del `Trip Planning Context`.

  

        - _Backend_: Implementare l'endpoint `GET /trips` per la dashboard.

  

        - _Frontend_: Creare la pagina della dashboard in SvelteKit.

  

        - _Frontend_: Creare il componente del form per il nuovo viaggio.

  

        - _Frontend_: Integrare le chiamate API usando il nostro client generato.

  

        - _Testing_: Scrivere test unitari e di integrazione per il nuovo codice.

  

- **Sprint Review**: Il team mostra dal vivo l'intero flusso: l'utente clicca il pulsante, compila il form, preme invio e la card del nuovo viaggio appare magicamente sulla dashboard.

  

- **Sprint Retrospective**: Il team potrebbe scoprire che: "La comunicazione tra il dev frontend e il dev backend sulla struttura esatta del form è stata difficile. Per il prossimo Sprint, faremo una breve sessione di pair programming per definire insieme i tipi TypeScript e il contratto OpenAPI prima di iniziare a scrivere il codice."

  

  

---

  

  

### 26.6. Conclusioni: Agilità è Disciplina, non Caos

  

  

Un ciclo di sviluppo iterativo non è un invito a "fare le cose a caso". Al contrario, è un **framework disciplinato** che sostituisce la rigidità di un piano a lungo termine con la flessibilità di un ciclo di feedback breve e costante.

  

  

Questo ritmo di due settimane ci fornisce:

  

  

- **Trasparenza**: Tutti sanno su cosa sta lavorando il team e quali sono i progressi.

  

- **Prevedibilità**: Dopo alcuni sprint, il team sviluppa una comprensione della propria velocità, rendendo le stime future più accurate.

  

- **Adattabilità**: La capacità di cambiare rotta ogni due settimane è il nostro più grande vantaggio competitivo.

  

- **Miglioramento Continuo**: La retrospettiva garantisce che il team non solo costruisca il prodotto, ma costruisca anche un processo di lavoro migliore.

  

  

Questo processo agile è il motore che alimenta la nostra macchina ingegneristica. Con questo motore acceso, siamo pronti a costruire l'infrastruttura di automazione (IaC e CI/CD) che supporterà e accelererà questo ciclo di consegna continua.

  

  

---

  

## Capitolo 27: Infrastructure as Code (IaC) con AWS CDK

  

  

Abbiamo progettato la nostra architettura, scritto il nostro codice e definito i nostri processi di sviluppo. Ora dobbiamo affrontare una domanda critica: **dove verrà eseguita questa applicazione?** La nostra architettura si basa su un ricco ecosistema di servizi AWS: Lambda, SQS, DynamoDB, API Gateway, Cognito. Come creiamo, configuriamo e gestiamo queste risorse in modo affidabile e ripetibile?

  

  

L'approccio tradizionale, e più pericoloso, è quello di affidarsi alla console di gestione di AWS. Un ingegnere si collega, clicca su una serie di pulsanti, compila form, imposta permessi e, se tutto va bene, l'infrastruttura è pronta. Questo metodo, ironicamente soprannominato **"ClickOps"**, è una ricetta per il disastro in qualsiasi progetto serio. È manuale, lento, prono a errori umani, non documentato e impossibile da replicare con coerenza.

  

  

Per costruire sistemi di livello enterprise, dobbiamo trattare la nostra infrastruttura con lo stesso rigore con cui trattiamo il nostro codice applicativo. Dobbiamo adottare il paradigma dell'**Infrastructure as Code (IaC)**. In questo capitolo, esploreremo come definire l'intera nostra infrastruttura AWS utilizzando un moderno linguaggio di programmazione e uno strumento potente come l'**AWS Cloud Development Kit (CDK)**.

  

  

---

  

  

### 27.1. Il Problema: La Fragilità del "ClickOps"

  

  

Gestire l'infrastruttura manualmente tramite un'interfaccia grafica è insostenibile per diverse ragioni:

  

  

- **Non è Ripetibile**: Se devi creare un nuovo ambiente per lo staging o per un test, come puoi essere sicuro che sia _esattamente_ identico all'ambiente di produzione? La probabilità di dimenticare una configurazione o un permesso è altissima.

  

- **Non è Versionabile**: Se un'impostazione dell'infrastruttura viene modificata, come si tiene traccia di chi ha fatto la modifica, quando e perché? Come si può tornare alla versione precedente se la modifica causa un problema? Con il ClickOps, non si può. La cronologia è persa.

  

- **È Lento e Non Scala**: Creare manualmente decine di risorse interconnesse è un processo lungo e noioso. Automatizzare il deployment diventa impossibile.

  

- **È Pieno di Rischi**: Una modifica manuale errata in produzione, fatta magari sotto pressione, può causare un'interruzione del servizio. Non c'è un processo di revisione (code review) o di validazione.

  

  

L'**Infrastructure as Code (IaC)** risolve tutti questi problemi applicando le pratiche consolidate dello sviluppo software alla gestione dell'infrastruttura. L'intera configurazione del nostro ambiente cloud viene definita in file di codice, che possono essere versionati, revisionati, testati e automatizzati.

  

  

---

  

  

### 27.2. Il Panorama dell'IaC su AWS e la Scelta del CDK

  

  

Esistono diversi strumenti per implementare l'IaC su AWS.

  

  

- **AWS CloudFormation**: È il servizio IaC nativo di AWS. Si definisce l'infrastruttura in file **YAML** o **JSON**. È potente e affidabile, ma anche estremamente verboso. Definire un'architettura complessa può richiedere migliaia di righe di configurazione, con molte ripetizioni.

  

- **Terraform**: È lo strumento open-source più popolare, sviluppato da HashiCorp. Usa un suo linguaggio dichiarativo (HCL), che è più conciso di CloudFormation. È cloud-agnostico, ma per questo capitolo ci concentriamo su strumenti nativi di AWS.

  

- **AWS CDK (Cloud Development Kit)**: È l'approccio più moderno e "developer-friendly" di AWS. Il CDK ci permette di definire la nostra infrastruttura cloud usando linguaggi di programmazione familiari come **TypeScript** (il più supportato), Python, Go, Java o C#.

  

  

Per questo libro, abbiamo scelto l'**AWS CDK con TypeScript**. Perché?

  

  

1. **La Potenza di un Vero Linguaggio di Programmazione**: Possiamo usare cicli, condizioni, funzioni, classi e astrazioni per definire la nostra infrastruttura in modo conciso e riutilizzabile (DRY - Don't Repeat Yourself).

  

2. **Astrazioni di Alto Livello (Constructs)**: Il CDK fornisce una libreria di "costrutti" che rappresentano le risorse AWS. Oltre ai costrutti di basso livello (L1) che mappano 1:1 con CloudFormation, esistono costrutti di alto livello (L2/L3) che incapsulano le best practice. Ad esempio, creare una VPC (Virtual Private Cloud) sicura e con sottoreti pubbliche e private richiede poche righe di codice, contro centinaia di righe in CloudFormation.

  

3. **Sicurezza dei Tipi e Autocompletamento**: Usando TypeScript, il nostro IDE ci aiuterà con il completamento automatico, il controllo dei tipi e la documentazione inline, riducendo drasticamente gli errori di configurazione prima ancora del deployment.

  

4. **Sintetizza in CloudFormation**: Il CDK non sostituisce CloudFormation, ma lo migliora. Il nostro codice TypeScript viene "sintetizzato" in un template CloudFormation standard. Otteniamo così il meglio di due mondi: un'esperienza di sviluppo moderna e la potenza del motore di deployment transazionale e affidabile di CloudFormation.

  

5. **Allineamento con lo Stack**: Poiché il nostro frontend SvelteKit è già basato su TypeScript, l'uso di TypeScript anche per l'IaC crea una coerenza tecnologica e abbassa la barriera d'ingresso per gli sviluppatori del team.

  

  

---

  

  

### 27.3. Costruire lo Stack per il Nostro Worker Asincrono

  

  

Mettiamoci al lavoro. Useremo il CDK per definire l'infrastruttura del nostro worker asincrono, descritto nel Capitolo 22, composto da una coda SQS, una tabella DynamoDB e una funzione Lambda in Go.

  

  

#### **Primi Passi e Struttura del Progetto**

  

  

Dopo aver installato gli strumenti necessari (AWS CLI, Node.js, AWS CDK), inizializziamo il nostro progetto:

  

  

Bash

  

  

```bash

  

mkdir infrastructure

  

cd infrastructure

  

cdk init app --language typescript

  

```

  

  

Questo crea una struttura di base. Il file più importante per noi sarà `lib/infrastructure-stack.ts`, dove definiremo le nostre risorse.

  

  

#### **Implementazione dello Stack CDK**

  

  

Modifichiamo il file `lib/infrastructure-stack.ts` per definire i nostri componenti.

  

  

TypeScript

  

  

```TypeScript

  

// lib/infrastructure-stack.ts

  

import * as cdk from 'aws-cdk-lib';

  

import { Construct } from 'constructs';

  

import * as sqs from 'aws-cdk-lib/aws-sqs';

  

import * as dynamodb from 'aws-cdk-lib/aws-dynamodb';

  

import * as lambda from 'aws-cdk-lib/aws-lambda';

  

import * as iam from 'aws-cdk-lib/aws-iam';

  

import { SqsEventSource } from 'aws-cdk-lib/aws-lambda-event-sources';

  

import * as path from 'path';

  

  

export class WhereShouldIBeStack extends cdk.Stack {

  

  constructor(scope: Construct, id: string, props?: cdk.StackProps) {

  

    super(scope, id, props);

  

  

    // === 1. Tabella DynamoDB ===

  

    // Definiamo la nostra tabella con Single-Table Design.

  

    const table = new dynamodb.Table(this, 'AppTable', {

  

      tableName: 'where-should-i-be-table',

  

      partitionKey: { name: 'PK', type: dynamodb.AttributeType.STRING },

  

      sortKey: { name: 'SK', type: dynamodb.AttributeType.STRING },

  

      billingMode: dynamodb.BillingMode.PAY_PER_REQUEST, // Modello On-Demand, perfetto per serverless

  

      removalPolicy: cdk.RemovalPolicy.DESTROY, // Per questo esempio, distruggi la tabella se lo stack viene eliminato. In produzione, usare RETAIN.

  

    });

  

  

    // === 2. Coda SQS con Dead-Letter Queue (DLQ) ===

  

    // Creiamo prima la DLQ per i messaggi falliti.

  

    const deadLetterQueue = new sqs.Queue(this, 'PersistenceWorkerDLQ');

  

  

    // Creiamo la coda principale, configurata per usare la DLQ.

  

    const queue = new sqs.Queue(this, 'PersistenceWorkerQueue', {

  

      visibilityTimeout: cdk.Duration.seconds(30),

  

      deadLetterQueue: {

  

        maxReceiveCount: 3, // Dopo 3 tentativi falliti, il messaggio va nella DLQ.

  

        queue: deadLetterQueue,

  

      },

  

    });

  

  

    // === 3. Ruolo IAM per la Funzione Lambda ===

  

    // Creiamo un ruolo con i permessi minimi indispensabili (Principle of Least Privilege).

  

    const lambdaRole = new iam.Role(this, 'PersistenceWorkerRole', {

  

      assumedBy: new iam.ServicePrincipal('lambda.amazonaws.com'),

  

      managedPolicies: [

  

        // Policy gestita da AWS per i log di base su CloudWatch.

  

        iam.ManagedPolicy.fromAwsManagedPolicyName('service-role/AWSLambdaBasicExecutionRole'),

  

      ],

  

    });

  

  

    // === 4. Funzione Lambda in Go ===

  

    const goWorkerLambda = new lambda.Function(this, 'PersistenceWorker', {

  

      runtime: lambda.Runtime.GO_1_X,

  

      // Il codice Go deve essere compilato per Linux amd64.

  

      // `path.join` costruisce il percorso relativo al nostro codice Go compilato.

  

      code: lambda.Code.fromAsset(path.join(__dirname, '..', '..', 'services', 'trip-persistence-worker', 'dist')),

  

      handler: 'main', // Il nome del nostro eseguibile Go.

  

      role: lambdaRole, // Assegniamo il ruolo IAM.

  

      timeout: cdk.Duration.seconds(15),

  

      environment: {

  

        TABLE_NAME: table.tableName, // Passiamo il nome della tabella come variabile d'ambiente.

  

      },

  

    });

  

  

    // === 5. Concessione dei Permessi e Collegamento dei Servizi ===

  

    // Concediamo esplicitamente alla Lambda i permessi di cui ha bisogno.

  

    queue.grantConsumeMessages(goWorkerLambda); // Permesso di leggere dalla coda SQS.

  

    table.grantReadWriteData(goWorkerLambda);   // Permesso di leggere/scrivere sulla tabella DynamoDB.

  

  

    // Impostiamo la coda SQS come trigger per la nostra Lambda.

  

    goWorkerLambda.addEventSource(new SqsEventSource(queue, {

  

      batchSize: 5, // Processa fino a 5 messaggi per volta.

  

    }));

  

    // === 6. Output (Opzionale ma utile) ===

  

    // Esponiamo l'URL della coda come output dello stack per un facile riferimento.

  

    new cdk.CfnOutput(this, 'QueueURL', { value: queue.queueUrl });

  

  }

  

}

  

```

  

  

Questo codice TypeScript definisce in modo chiaro, leggibile e riutilizzabile l'intera nostra infrastruttura serverless.

  

  

---

  

  

### 27.4. Il Ciclo di Vita del Deployment con CDK

  

  

Una volta definito lo stack, il nostro flusso di lavoro diventa semplice e potente.

  

  

1. `cdk synth`: Questo comando compila il nostro codice TypeScript e lo "sintetizza" in un template AWS CloudFormation. È un ottimo modo per vedere cosa verrà creato.

  

    Bash

  

    ```bash

  

    cdk synth

  

    ```

  

2. `cdk diff`: Questo comando confronta il template appena sintetizzato con lo stato attuale dell'infrastruttura deployata su AWS e ci mostra una `diff` simile a quella di `git`. Ci dice esattamente cosa sta per essere creato, modificato o cancellato. È la nostra rete di sicurezza finale prima di un deployment.

  

    Bash

  

    ```bash

  

    cdk diff

  

    ```

  

3. `cdk deploy`: Questo comando prende il template CloudFormation e lo applica al nostro account AWS, eseguendo il provisioning o l'aggiornamento di tutte le risorse. Il CDK gestirà il caricamento del codice Lambda e tutte le configurazioni.

  

    Bash

  

    ```bash

  

    cdk deploy

  

    ```

  

4. `cdk destroy`: Quando abbiamo finito (ad esempio, con un ambiente di test), questo comando distrugge in modo pulito tutte le risorse create dallo stack.

  

    Bash

  

    ```bash

  

    cdk destroy

  

    ```

  

  

---

  

  

### 27.5. Conclusioni: L'Infrastruttura è Software

  

  

L'Infrastructure as Code non è più un'opzione, ma un requisito fondamentale per la gestione di applicazioni cloud moderne. Ci permette di portare nel mondo dell'infrastruttura tutta la disciplina e l'automazione che già applichiamo al codice applicativo.

  

  

Scegliendo l'AWS CDK, abbiamo potenziato questo paradigma, usando un linguaggio di programmazione completo per:

  

  

- **Definire infrastrutture complesse** in modo conciso e leggibile.

  

- **Sfruttare astrazioni di alto livello** che incorporano le best practice.

  

- **Ottenere sicurezza dei tipi e supporto dall'IDE**, riducendo gli errori.

  

- **Integrare la gestione dell'infrastruttura** direttamente nel nostro processo di sviluppo e di controllo di versione.

  

  

La nostra infrastruttura non è più un'entità fragile e opaca gestita manualmente, ma è diventata una parte integrante e versionata della nostra codebase. Questa solida base di automazione è il prerequisito indispensabile per costruire le pipeline di CI/CD che esploreremo nel prossimo capitolo, consentendoci di rilasciare valore ai nostri utenti in modo rapido, sicuro e continuo.

  

  

Certamente. Proseguiamo con il capitolo che trasforma tutto il nostro lavoro di progettazione e sviluppo in un processo automatizzato, affidabile e veloce. Questo capitolo è il cuore pulsante delle pratiche DevOps moderne e un requisito essenziale per qualsiasi team che voglia rilasciare software di qualità in modo continuo.

  

  

---

  

## Capitolo 28: CI/CD, Sicurezza e Deployment Continuo

  

  

Nei capitoli precedenti, abbiamo definito un processo di sviluppo iterativo (Capitolo 26) e abbiamo imparato a definire la nostra intera infrastruttura come codice (Capitolo 27). Abbiamo tutti i pezzi del puzzle: codice sorgente versionato, una suite di test automatizzati e un'infrastruttura ripetibile. Manca l'ultimo, fondamentale anello della catena: **come colleghiamo tutto insieme per portare le modifiche dal computer di uno sviluppatore alla produzione in modo rapido, sicuro e automatico?**

  

  

La risposta risiede nell'adozione di una pipeline di **CI/CD (Continuous Integration / Continuous Deployment)**. L'era dei deployment manuali, fatti a tarda notte con dita incrociate e una lunga checklist, è finita. Un processo di deployment manuale è lento, prono a errori e incredibilmente stressante. Per competere nel mercato odierno, dobbiamo automatizzare.

  

  

In questo capitolo, progetteremo e implementeremo una pipeline di CI/CD professionale per la nostra applicazione "Where Should I Be?". Integreremo test, build, analisi di sicurezza (un approccio noto come **DevSecOps**) e strategie di deployment avanzate per creare una vera e propria "linea di assemblaggio" per il nostro software, capace di consegnare valore ai nostri utenti in modo continuo e con la massima fiducia.

  

  

---

  

  

### 28.1. Demistificare CI/CD: Oltre gli Acronimi

  

  

I termini CI e CD vengono spesso usati in modo intercambiabile, ma rappresentano concetti distinti che si costruiscono l'uno sull'altro.

  

  

#### **Continuous Integration (CI) - Integrazione Continua**

  

  

- **Cos'è**: È la pratica con cui gli sviluppatori integrano il loro lavoro nel ramo principale del repository di codice (es. `main` o `develop`) molto frequentemente, idealmente più volte al giorno. Ogni integrazione scatena un'**esecuzione automatica della build e dei test unitari**.

  

- **Obiettivo**: Rilevare i problemi di integrazione il prima possibile. Se una modifica di uno sviluppatore rompe la build o fallisce un test, il team lo sa immediatamente, non dopo settimane di sviluppo in isolamento. Il mantra è: "fallisci presto, fallisci a basso costo".

  

- **Analogia**: È come un'officina meccanica dove, ogni volta che un meccanico produce un nuovo pezzo, lo prova subito sul motore principale per assicurarsi che sia compatibile, invece di aspettare di aver costruito tutti i pezzi per poi scoprire che non si incastrano.

  

  

#### **Continuous Delivery (CD) - Consegna Continua**

  

  

- **Cos'è**: È il passo successivo alla CI. Se la fase di build e test della CI ha successo, il software viene automaticamente **pacchettizzato e preparato per il rilascio**. L'artefatto (es. un'immagine Docker, un file .zip per Lambda) viene deployato in un ambiente di staging o pre-produzione.

  

- **Obiettivo**: Avere sempre un artefatto **pronto per il rilascio in produzione**. Il deployment effettivo in produzione rimane un'azione manuale, spesso un "one-click button" che può essere premuto dal Product Owner o dal team lead quando il business lo decide.

  

  

#### **Continuous Deployment (CD) - Deployment Continuo**

  

  

- **Cos'è**: È l'automazione completa del processo. Se tutte le fasi precedenti (CI, test di integrazione, test E2E nell'ambiente di staging) hanno successo, la nuova versione del software viene **deployata automaticamente in produzione senza alcun intervento umano**.

  

- **Obiettivo**: Massimizzare la velocità di rilascio e ridurre al minimo il "lead time" (il tempo che intercorre tra un'idea e la sua consegna agli utenti). Questo richiede un'altissima fiducia nella propria pipeline di test e monitoraggio.

  

  

Per il nostro progetto, punteremo a implementare una pipeline di **Continuous Delivery**, con la possibilità di evolvere verso il Continuous Deployment man mano che la nostra fiducia nel sistema cresce.

  

  

---

  

  

### 28.2. Progettare la Nostra Pipeline CI/CD ⚙️

  

  

Useremo **GitHub Actions** come strumento di CI/CD, data la sua eccellente integrazione con il nostro repository di codice e il suo vasto ecosistema di azioni riutilizzabili.

  

  

Progettiamo la pipeline per uno dei nostri microservizi Go, ad esempio il nostro worker serverless `trip-persistence-worker`.

  

  

**Trigger**: La pipeline si attiverà su ogni `push` al ramo `main` e su ogni apertura/aggiornamento di una `Pull Request` verso `main`.

  

  

**Fasi della Pipeline:**

  

  

1. **Checkout Code**: Scarica l'ultima versione del codice dal repository.

  

2. **Setup dell'Ambiente**: Installa la versione corretta di Go e le dipendenze necessarie.

  

3. **Linting & Static Analysis**: Esegue `golangci-lint` per verificare la qualità e lo stile del codice.

  

4. **Test Unitari**: Esegue `go test -race ./...` per lanciare tutti i test unitari e il race detector. Un fallimento qui blocca immediatamente la pipeline.

  

5. **Scansione di Sicurezza (DevSecOps)**:

  

    - **SAST (Static Application Security Testing)**: Usa `gosec` per analizzare il codice alla ricerca di vulnerabilità comuni.

  

    - **SCA (Software Composition Analysis)**: Usa `Trivy` per scansionare il file `go.mod` alla ricerca di vulnerabilità note nelle nostre dipendenze.

  

6. **Build dell'Artefatto**: Compila il nostro codice Go per l'ambiente di destinazione di Lambda (`GOOS=linux GOARCH=amd64`) e crea il pacchetto di deployment (un file .zip).

  

7. **Deployment (solo sul ramo `main`)**:

  

    - **Autenticazione su AWS**: Si autentica su AWS in modo sicuro usando OIDC (OpenID Connect), senza bisogno di salvare chiavi segrete a lunga durata su GitHub.

  

    - **Deploy con CDK**: Esegue `cdk deploy` per applicare le modifiche all'infrastruttura e deployare il nuovo pacchetto Lambda.

  

  

---

  

  

### 28.3. Implementazione con GitHub Actions

  

  

Ecco come potrebbe apparire il file di workflow `ci.yml` per il nostro servizio.

  

  

YAML

  

  

```yaml

  

# .github/workflows/ci.yml

  

name: Go Backend CI/CD

  

  

on:

  

  push:

  

    branches: [ "main" ]

  

  pull_request:

  

    branches: [ "main" ]

  

  

# Permessi necessari per l'autenticazione OIDC con AWS

  

permissions:

  

  id-token: write

  

  contents: read

  

  

jobs:

  

  build-and-test:

  

    name: Build, Test and Security Scan

  

    runs-on: ubuntu-latest

  

  

    steps:

  

      - name: Checkout code

  

        uses: actions/checkout@v4

  

  

      - name: Set up Go

  

        uses: actions/setup-go@v5

  

        with:

  

          go-version: '1.2x' # Usa la versione di Go del tuo progetto

  

  

      - name: Run golangci-lint

  

        uses: golangci/golangci-lint-action@v6

  

        with:

  

          version: v1.59

  

      - name: Run Unit Tests

  

        run: go test -v -race ./...

  

  

      - name: Run GoSec Security Scanner (SAST)

  

        run: |

  

          go install github.com/securego/gosec/v2/cmd/gosec@latest

  

          gosec ./...

  

  

      - name: Run Trivy Vulnerability Scanner (SCA)

  

        uses: aquasecurity/trivy-action@master

  

        with:

  

          scan-type: 'fs'

  

          scan-ref: '.'

  

          exit-code: '1' # Fa fallire la build se trova vulnerabilità critiche

  

          format: 'table'

  

      - name: Build Go Binary for Lambda

  

        if: github.ref == 'refs/heads/main' # Esegui solo sul ramo main

  

        run: |

  

          cd services/trip-persistence-worker 

  

          GOOS=linux GOARCH=amd64 go build -o dist/main

  

          cd dist && zip ../../../worker-deployment-package.zip main

  

  

      - name: Upload Lambda Artifact

  

        if: github.ref == 'refs/heads/main'

  

        uses: actions/upload-artifact@v4

  

        with:

  

          name: worker-deployment-package

  

          path: ./worker-deployment-package.zip

  

  

  deploy:

  

    name: Deploy to AWS

  

    needs: build-and-test # Questo job parte solo se 'build-and-test' ha successo

  

    if: github.ref == 'refs/heads/main' # Esegui solo sul ramo main

  

    runs-on: ubuntu-latest

  

  

    steps:

  

      - name: Checkout code

  

        uses: actions/checkout@v4

  

  

      - name: Download Lambda Artifact

  

        uses: actions/download-artifact@v4

  

        with:

  

          name: worker-deployment-package

  

      - name: Configure AWS Credentials via OIDC

  

        uses: aws-actions/configure-aws-credentials@v4

  

        with:

  

          role-to-assume: arn:aws:iam::${{ secrets.AWS_ACCOUNT_ID }}:role/GitHubActionsDeployRole # Ruolo IAM configurato su AWS

  

          aws-region: ${{ secrets.AWS_REGION }}

  

  

      - name: Setup Node.js (for AWS CDK)

  

        uses: actions/setup-node@v4

  

        with:

  

          node-version: '20'

  

  

      - name: Deploy with AWS CDK

  

        working-directory: ./infrastructure # Naviga nella directory del CDK

  

        run: |

  

          npm install

  

          npm install -g aws-cdk

  

          # Il flag --require-approval never è per l'automazione

  

          cdk deploy --all --require-approval never 

  

```

  

  

---

  

  

### 28.4. DevSecOps: La Sicurezza come Responsabilità Condivisa

  

  

Il termine **DevSecOps** rappresenta un cambiamento culturale: la sicurezza non è più un controllo fatto da un team separato alla fine del processo, ma una responsabilità condivisa, integrata in ogni fase del ciclo di vita del software. La nostra pipeline CI/CD è il luogo perfetto per automatizzare questi controlli.

  

  

- **SAST (Static Application Security Testing)**: Strumenti come `gosec` analizzano il nostro codice sorgente alla ricerca di pattern di codice insicuri, come credenziali hard-coded, query SQL non sicure o uso di pacchetti crittografici deboli.

  

- **SCA (Software Composition Analysis)**: Strumenti come `Trivy` o il Dependabot di GitHub analizzano le nostre dipendenze (`go.mod`) e ci avvisano se stiamo usando una libreria con una vulnerabilità nota (CVE). Questo è fondamentale, perché il nostro codice è sicuro solo quanto è sicura la dipendenza più debole.

  

- **Scansione dei Container**: Se usassimo Docker, la pipeline includerebbe anche uno step per scansionare l'immagine Docker finale con `Trivy`, per trovare vulnerabilità nel sistema operativo di base o nei pacchetti installati.

  

  

Integrando questi controlli nella pipeline, otteniamo un feedback sulla sicurezza immediato, proprio come per i test unitari.

  

  

---

  

  

### 28.5. Strategie di Deployment per Ridurre il Rischio

  

  

Fare "deploy" non significa semplicemente sovrascrivere la vecchia versione con la nuova. Esistono strategie sofisticate per rilasciare il software in produzione minimizzando il rischio di downtime o di impatto negativo per gli utenti.

  

  

- **Rolling Update**: La strategia più comune. Le nuove istanze dell'applicazione vengono avviate gradualmente, mentre le vecchie vengono spente, assicurando che ci sia sempre capacità disponibile per servire il traffico.

  

- **Blue/Green Deployment**: Si mantengono due ambienti di produzione identici: "Blue" (la versione attuale) e "Green" (la nuova versione). Tutto il traffico va a Blue. Si deploya la nuova versione su Green e la si testa. Quando si è pronti, si sposta il router del traffico da Blue a Green. Il vantaggio è un rollback istantaneo: se qualcosa va storto, basta rispostare il traffico su Blue.

  

- **Canary Release**: La strategia più avanzata e a basso rischio. Si rilascia la nuova versione solo a un piccolo sottoinsieme di utenti (es. l'1%). Si monitorano attentamente le metriche di errore e di performance. Se tutto va bene, si aumenta gradualmente la percentuale di traffico verso la nuova versione (10%, 50%, 100%) fino a completare il rollout. AWS Lambda e API Gateway hanno un supporto nativo eccellente per le implementazioni canary.

  

  

Per la nostra applicazione, un approccio **Canary** per le nostre Lambda esposte via API Gateway sarebbe la scelta ideale per massimizzare la sicurezza dei rilasci.

  

  

---

  

  

### 28.6. Conclusioni: L'Automazione come Motore di Velocità e Qualità

  

  

Una pipeline di CI/CD ben costruita è la spina dorsale di un team di sviluppo moderno e performante. È più di un semplice strumento di automazione; è una manifestazione della nostra cultura ingegneristica.

  

  

- **Automatizza i compiti ripetitivi e rischiosi**, liberando gli sviluppatori di potersi concentrare sulla creazione di valore.

  

- **Crea un ciclo di feedback rapido**, permettendoci di trovare e correggere bug e vulnerabilità in poche ore, non settimane.

  

- **Aumenta la fiducia nei rilasci**, trasformando il deployment da un evento temuto a un'attività di routine.

  

- **Incarna i principi di DevSecOps**, rendendo la qualità e la sicurezza una responsabilità continua e condivisa.

  

  

Questa pipeline è il motore che alimenta il nostro ciclo iterativo. Con essa, siamo pronti ad affrontare l'ultimo aspetto fondamentale delle operations: capire cosa sta succedendo nella nostra applicazione una volta che è in produzione, attraverso il **monitoring e l'observability**.

  

  

---

  

## Capitolo 29: Monitoring e Observability con AWS X-Ray e CloudWatch

  

  

Abbiamo progettato, costruito, testato e, con il capitolo precedente, finalmente deployato la nostra applicazione "Where Should I Be?" nel cloud AWS. La nostra pipeline di CI/CD ha funzionato, il deployment è andato a buon fine. Il lavoro è finito, giusto?

  

  

Assolutamente no. Il lavoro è appena iniziato.

  

  

Un'applicazione in produzione è un sistema vivo, complesso e soggetto a forze imprevedibili: picchi di traffico, fallimenti di rete, bug nascosti, lentezza dei servizi da cui dipendiamo. Come facciamo a sapere se la nostra applicazione sta funzionando correttamente in questo momento? E quando un utente segnala "non riesco a salvare il mio viaggio", come possiamo diagnosticare il problema in un'architettura distribuita dove la richiesta attraversa API Gateway, Lambda, SQS e DynamoDB?

  

  

Rispondere a queste domande è il dominio del **Monitoring** e dell'**Observability**. In questo capitolo, impareremo a trasformare la nostra applicazione da una "scatola nera" a un sistema trasparente. Strumenteremo il nostro codice Go e useremo la potenza dei servizi AWS nativi come **Amazon CloudWatch** e **AWS X-Ray** per ottenere una visibilità profonda sulla salute e sul comportamento del nostro sistema in tempo reale.

  

  

---

  

  

### 29.1. Monitoring vs. Observability: Una Distinzione Cruciale

  

  

Sebbene spesso usati come sinonimi, questi due concetti rappresentano due approcci complementari alla comprensione di un sistema.

  

  

#### **Monitoring (Monitoraggio) 📈**

  

  

- **Cos'è**: Il monitoraggio è la pratica di raccogliere, aggregare e analizzare dati su un sistema per osservare il suo comportamento nel tempo e **verificare condizioni predefinite**. Si tratta di porre al sistema **domande che già conosciamo**.

  

- **Analogia**: Il cruscotto della tua automobile. Mostra un set predefinito di metriche: velocità, livello del carburante, temperatura del motore. Ti avvisa se una di queste metriche supera una soglia critica (es. la spia dell'olio si accende). Il monitoraggio ti dice _che_ qualcosa è rotto.

  

- **Esempi**:

  

    - "Avvisami se la CPU della mia istanza supera l'80% per 5 minuti."

  

    - "Avvisami se la latenza p99 della mia API supera i 500ms."

  

    - "Avvisami se ci sono più di 10 messaggi nella Dead-Letter Queue."

  

  

#### **Observability (Osservabilità) 🔍**

  

  

- **Cos'è**: L'osservabilità è la capacità di dedurre lo stato interno di un sistema complesso esaminando i suoi output esterni. Si tratta di avere dati sufficientemente ricchi da poter porre **domande che non sapevamo di dover fare**.

  

- **Analogia**: Se il monitoraggio è il cruscotto, l'osservabilità è la porta diagnostica a cui il meccanico collega il suo computer. Mentre il cruscotto ti ha detto _che_ il motore è surriscaldato, la diagnostica permette al meccanico di esplorare i dati di decine di sensori per capire _perché_ è surriscaldato.

  

- **I Tre Pilastri dell'Observability**:

  

    1. **Logs (Registri)**: Record immutabili e con timestamp di eventi discreti. Ci dicono cosa è successo in un punto specifico del codice.

  

    2. **Metrics (Metriche)**: Dati numerici aggregati nel tempo. Sono ideali per il monitoraggio e per individuare trend.

  

    3. **Traces (Tracciamenti)**: Rappresentano l'intero percorso di una singola richiesta attraverso tutti i servizi del nostro sistema distribuito. Sono lo strumento principe per il debug di problemi di latenza e di errori in architetture a microservizi.

  

  

Per la nostra applicazione, useremo **Amazon CloudWatch** per il Monitoring (Logs e Metrics) e **AWS X-Ray** per l'Observability (Traces).

  

  

---

  

  

### 29.2. Logging Strutturato in Go: Le Fondamenta dell'Analisi

  

  

Dei `log.Printf("errore")` sparsi nel codice non sono sufficienti. Per essere analizzabili, i log devono essere **strutturati**, preferibilmente in formato JSON.

  

  

> **Definizione**: Il **Logging Strutturato** è la pratica di scrivere i log non come stringhe di testo informali, ma come oggetti dati (es. JSON) con coppie chiave-valore ben definite. Questo li rende facilmente interrogabili, filtrabili e analizzabili da strumenti automatici.

  

  

Fortunatamente, a partire dalla versione 1.21, Go ha un eccellente pacchetto nella libreria standard per questo scopo: `log/slog`.

  

  

**Esempio di implementazione con `slog`:**

  

  

Go

  

  

```go

  

// Logger di base per una funzione Lambda

  

var logger *slog.Logger

  

  

func init() {

  

    // Creiamo un logger che produce JSON sull'output standard.

  

    // CloudWatch Logs catturerà automaticamente questo output.

  

    logger = slog.New(slog.NewJSONHandler(os.Stdout, nil))

  

}

  

  

func HandleRequest(ctx context.Context, ...) error {

  

    // ...

  

    tripID := "..."

  

    userID := "..."

  

  

    // Logghiamo informazioni utili con contesto strutturato.

  

    logger.Info(

  

        "Processing new trip creation",

  

        slog.String("tripId", tripID),

  

        slog.String("userId", userID),

  

    )

  

  

    if err != nil {

  

        // Logghiamo errori con attributi aggiuntivi.

  

        logger.Error(

  

            "Failed to save trip to database",

  

            slog.String("error", err.Error()),

  

            slog.String("tripId", tripID),

  

        )

  

        return err

  

    }

  

    // ...

  

}

  

```

  

  

Scrivendo i log in questo modo, possiamo poi usare **CloudWatch Logs Insights** per eseguire query complesse, come: "mostrami tutti i log di errore per `userId=123` negli ultimi 30 minuti".

  

  

---

  

  

### 29.3. Monitoring Attivo con CloudWatch Metrics e Alarms

  

  

CloudWatch raccoglie automaticamente una vasta gamma di metriche da tutti i servizi AWS che usiamo. Per la nostra architettura, le più importanti sono:

  

  

- **AWS Lambda**: `Invocations`, `Errors`, `Duration`, `ConcurrentExecutions`.

  

- **Amazon SQS**: `ApproximateNumberOfMessagesVisible`, `ApproximateAgeOfOldestMessage`.

  

- **Amazon DynamoDB**: `ConsumedReadCapacityUnits`, `ConsumedWriteCapacityUnits`, `ThrottledRequests`.

  

- **API Gateway**: `Count`, `Latency`, `4xxError`, `5xxError`.

  

  

Il nostro compito è definire degli **allarmi** su queste metriche per essere notificati proattivamente quando qualcosa va storto. Useremo il nostro stack **AWS CDK** (Capitolo 27) per definire questi allarmi come codice.

  

  

Esempio: Creare un allarme per la Dead-Letter Queue (DLQ)

  

  

Questo è uno degli allarmi più importanti. Se un messaggio finisce nella DLQ del nostro worker di persistenza, significa che un'operazione di scrittura sta fallendo ripetutamente e richiede un intervento umano.

  

  

TypeScript

  

  

```TypeScript

  

// Aggiunta a lib/infrastructure-stack.ts

  

  

import * as cloudwatch from 'aws-cdk-lib/aws-cloudwatch';

  

import * as cw_actions from 'aws-cdk-lib/aws-cloudwatch-actions';

  

import * as sns from 'aws-cdk-lib/aws-sns';

  

  

// ... dentro la classe WhereShouldIBeStack, dopo aver definito la DLQ ...

  

  

// 1. Creiamo un topic SNS a cui inviare la notifica di allarme.

  

const alarmTopic = new sns.Topic(this, 'AlarmTopic');

  

// In un progetto reale, qui si aggiungerebbero sottoscrizioni (es. email, PagerDuty).

  

  

// 2. Creiamo l'allarme sulla metrica della dimensione della DLQ.

  

const dlqAlarm = new cloudwatch.Alarm(this, 'PersistenceWorkerDLQAlarm', {

  

  alarmName: 'PersistenceWorker-DLQ-HasMessages',

  

  metric: deadLetterQueue.metricApproximateNumberOfMessagesVisible({

  

    period: cdk.Duration.minutes(1),

  

    statistic: 'Sum',

  

  }),

  

  threshold: 0,

  

  evaluationPeriods: 1, // Scatta se la metrica è > 0 per 1 periodo di 1 minuto.

  

  comparisonOperator: cloudwatch.ComparisonOperator.GREATER_THAN_THRESHOLD,

  

  treatMissingData: cloudwatch.TreatMissingData.NOT_BREACHING,

  

});

  

  

// 3. Colleghiamo l'allarme all'azione di notifica sul topic SNS.

  

dlqAlarm.addAlarmAction(new cw_actions.SnsAction(alarmTopic));

  

```

  

  

---

  

  

### 29.4. Tracciamento Distribuito con AWS X-Ray

  

  

Mentre il monitoring ci dice _che_ c'è un errore (es. un `5xx` su API Gateway), il tracciamento distribuito ci dice _dove_ e _perché_. **AWS X-Ray** è il servizio di AWS progettato per questo.

  

  

**Come funziona?**

  

  

1. Quando una richiesta entra nel nostro sistema, X-Ray le assegna un **Trace ID** univoco.

  

2. Questo ID viene propagato in un header (`X-Amzn-Trace-Id`) attraverso tutte le chiamate successive: da API Gateway a Lambda, da Lambda a SQS, da SQS a un'altra Lambda, da Lambda a DynamoDB.

  

3. Ogni servizio registra un **segmento** di lavoro, annotando quando ha iniziato e finito la sua parte.

  

4. X-Ray raccoglie tutti questi segmenti e li unisce in un'unica **traccia** (trace), fornendoci una visione completa e cronologica dell'intero percorso della richiesta.

  

  

#### **Abilitare X-Ray**

  

  

La bellezza di X-Ray è che per i servizi gestiti di AWS, l'abilitazione è quasi banale, specialmente con il CDK.

  

  

TypeScript

  

  

```

  

// In lib/infrastructure-stack.ts

  

  

// Per API Gateway e Lambda, basta una singola riga di configurazione.

  

const api = new apigateway.LambdaRestApi(this, 'ApiEndpoint', {

  

  handler: apiLambda,

  

  proxy: false,

  

  deployOptions: {

  

    tracingEnabled: true, // Abilita X-Ray per l'API Gateway

  

  },

  

});

  

  

const goWorkerLambda = new lambda.Function(this, 'PersistenceWorker', {

  

  // ... altre configurazioni ...

  

  tracing: lambda.Tracing.ACTIVE, // Abilita X-Ray per la Lambda

  

});

  

```

  

  

#### **Strumentazione Manuale del Codice Go**

  

  

Per le chiamate che il nostro codice fa esplicitamente (es. a un'API esterna come OpenAI), dobbiamo instrumentare il codice noi stessi usando l'SDK di X-Ray per Go.

  

  

> **Riferimento Chiave**: `github.com/aws/aws-xray-sdk-go`

  

  

Go

  

  

```go

  

// Esempio di come instrumentare un client HTTP

  

import "github.com/aws/aws-xray-sdk-go/xray"

  

  

// Quando creiamo il nostro http.Client, lo "wrappiamo" con X-Ray

  

httpClient := xray.Client(&http.Client{Timeout: 5 * time.Second})

  

  

// Ora, quando usiamo questo client, X-Ray creerà automaticamente un sottosegmento per la chiamata.

  

req, _ := http.NewRequestWithContext(ctx, "GET", "https://api.openai.com/...", nil)

  

resp, err := httpClient.Do(req)

  

  

// Possiamo anche creare sottosegmenti manuali per misurare parti specifiche del nostro codice.

  

err = xray.Capture(ctx, "saveToDatabase", func(ctx1 context.Context) error {

  

    // ... logica del repository che parla con DynamoDB ...

  

    // Se c'è un errore, X-Ray lo registrerà nel trace.

  

    return repo.saveInternal(ctx1, data)

  

})

  

```

  

  

#### **Il Risultato: La Mappa del Servizio**

  

  

Una volta che i dati di tracciamento sono stati raccolti, X-Ray ci fornisce due viste potentissime:

  

  

- **La Mappa del Servizio (Service Map)**: Un diagramma generato automaticamente che mostra tutti i nostri servizi (API Gateway, Lambda, SQS, DynamoDB) e le connessioni tra di loro. I nodi cambiano colore per indicare la loro salute (verde per OK, giallo per errori, rosso per fault), permettendoci di vedere a colpo d'occhio dove si trova un problema.

  

- **La Vista della Traccia (Trace View)**: Un diagramma a cascata (waterfall) che mostra la cronologia di una singola richiesta. Vediamo esattamente quanto tempo ha impiegato ogni servizio, dove si sono verificati gli errori e quali log e metadati sono associati a ogni passo. È lo strumento di debug definitivo per un'architettura a microservizi.

  

  

---

  

  

### 29.5. Conclusioni: Da Reattivi a Proattivi

  

  

Senza una solida strategia di monitoring e observability, gestire un'applicazione in produzione è come guidare un'auto di notte, a fari spenti e con i finestrini oscurati. Si è destinati a schiantarsi.

  

  

In questo capitolo, abbiamo imparato a "illuminare" il nostro sistema:

  

  

- Il **Monitoring** con **CloudWatch** ci funge da cruscotto, avvisandoci proattivamente quando le metriche chiave deviano dalla norma.

  

- L'**Observability**, ottenuta tramite **logging strutturato** e il tracciamento distribuito con **AWS X-Ray**, ci fornisce gli strumenti diagnostici per capire il "perché" dietro ogni problema.

  

  

Adottando questi strumenti e pratiche, trasformiamo il nostro rapporto con la produzione. Non siamo più in uno stato reattivo, in attesa che gli utenti segnalino i problemi, ma diventiamo proattivi, capaci di comprendere, diagnosticare e risolvere i problemi prima che abbiano un impatto significativo. Questa è la vera essenza delle moderne Operations.

  

  

---

  

## Capitolo 30: Conclusioni e Prossimi Passi

  

  

Siamo giunti alla fine del nostro lungo e intenso viaggio. Insieme, abbiamo attraversato un panorama vasto e complesso, partendo dai concetti filosofici del software enterprise moderno fino ad arrivare ai dettagli implementativi di un'applicazione full-stack, scalabile e resiliente. Se siete arrivati fin qui, avete dimostrato una dedizione e una curiosità che sono il marchio dei veri professionisti del software.

  

  

Questo libro non è stato concepito come una semplice raccolta di tutorial, ma come un percorso guidato attraverso un approccio olistico alla costruzione di software. Abbiamo visto come ogni scelta, dalla definizione di un `Value Object` nel nostro dominio Go fino alla configurazione di una pipeline di CI/CD, sia interconnessa e contribuisca a un obiettivo più grande: creare sistemi che non solo funzionano, ma che sono anche comprensibili, manutenibili e capaci di evolvere nel tempo.

  

  

In questo capitolo finale, faremo un passo indietro per ammirare il quadro completo. Riepilogheremo ciò che abbiamo costruito e, soprattutto, _perché_ lo abbiamo costruito in questo modo. Distilleremo i principi fondamentali che spero porterete con voi in ogni progetto futuro e tracceremo una mappa per i vostri prossimi passi nel continuo viaggio dell'apprendimento.

  

  

---

  

  

### 30.1. Riepilogo del Nostro Viaggio: Cosa Abbiamo Costruito e Perché

  

  

Ripercorriamo le tappe principali della nostra avventura, consolidando la narrazione che ha legato insieme ogni capitolo.

  

  

#### **Parte I: Le Fondamenta e il Contesto**

  

  

Abbiamo iniziato stabilendo il **"perché"**. Abbiamo compreso che il software moderno deve affrontare sfide di complessità, scala e agilità che richiedono un approccio più sofisticato del semplice CRUD. Abbiamo quindi dato un volto a queste sfide, introducendo la nostra applicazione di esempio, **"Where Should I Be?"**, e delineando un'architettura di alto livello basata su microservizi, Go, AWS e SvelteKit. Abbiamo affrontato fin da subito temi cruciali come la sicurezza con AWS Cognito e le scelte strategiche tra modelli server e serverless.

  

  

#### **Parte II: La Progettazione Tattica con DDD**

  

  

Questa è stata la nostra immersione nel **cuore del software**. Armati del Domain-Driven Design, abbiamo imparato a modellare il dominio di business. Abbiamo scoperto l'importanza del **Linguaggio Ubiquo** come ponte tra business e tecnologia. Abbiamo poi imparato a usare i mattoncini del DDD:

  

  

- **Aggregati** per definire confini di consistenza transazionale.

  

- **Value Objects** per catturare concetti descrittivi in modo robusto e immutabile.

  

- **Entità** per modellare oggetti con un'identità e un ciclo di vita.

  

- Domain Services per incapsulare la logica di business che non appartiene a un singolo oggetto.

  

    Abbiamo trasformato la logica di business da un groviglio di codice procedurale a un modello ricco, espressivo e auto-documentante.

  

  

#### **Parte III & IV: Architettura e Progettazione Strategica**

  

  

Con un solido modello di dominio, abbiamo fatto "zoom-out". Abbiamo inserito il nostro dominio all'interno di una Clean Architecture, proteggendolo con il Repository Pattern e assemblando il tutto con la Dependency Injection. Abbiamo esplorato pattern avanzati come CQRS per ottimizzare le nostre letture e scritture.

  

  

Subito dopo, abbiamo abbracciato la progettazione strategica, imparando a gestire la complessità su larga scala. Con i Bounded Context, abbiamo imparato a scomporre un grande problema in sistemi più piccoli e autonomi. Con l'Event Storming, abbiamo scoperto una tecnica collaborativa per mappare il dominio, e con il Context Mapping, abbiamo imparato a definire le relazioni tra i nostri contesti in modo intenzionale.

  

  

#### **Parte V, VI & VII: Integrazione, Persistenza e Operations**

  

  

Nelle parti finali, abbiamo reso reale la nostra architettura. Abbiamo definito **contratti API** robusti con OpenAPI, gestito la **concorrenza** e l'**integrazione resiliente** con servizi esterni. Abbiamo scelto **DynamoDB** come database cloud-native, disaccoppiando le scritture con **SQS e Lambda** per massimizzare la resilienza e la scalabilità. Abbiamo costruito un'interfaccia utente moderna con **SvelteKit**, definito un processo di sviluppo **agile**, automatizzato la nostra infrastruttura con l'**AWS CDK** e il nostro ciclo di vita con **pipeline di CI/CD sicure**. Infine, abbiamo imparato ad "ascoltare" la nostra applicazione in produzione con **CloudWatch e X-Ray**.

  

  

Abbiamo completato il cerchio, dall'idea al codice, dall'architettura alle operations.

  

  

---

  

  

### 30.2. I Principi Fondamentali da Portare con Voi

  

  

Al di là delle singole tecnologie, che sono destinate a cambiare, questo libro ha cercato di trasmettere un insieme di principi senza tempo. Se doveste ricordare solo cinque cose, spero siano queste:

  

  

#### **1. Il Dominio Prima di Tutto (Domain-First)**

  

  

La tecnologia è un mezzo, non il fine. Il software di successo risolve problemi di business reali. Iniziate sempre con una profonda comprensione del dominio. Immergetevi nel suo linguaggio, nelle sue regole e nelle sue complessità. Il **Linguaggio Ubiquo** non è un gergo, è il vostro strumento più potente per colmare il divario tra l'intenzione e l'implementazione.

  

  

#### **2. Progettare per il Disaccoppiamento (Design for Decoupling)**

  

  

Bounded Context, Clean Architecture, Repository Pattern, comunicazione asincrona tramite eventi. Tutti questi pattern servono un unico, grande obiettivo: **ridurre l'accoppiamento**. Un software disaccoppiato è più facile da testare, da mantenere, da scalare e da far evolvere. Ogni volta che prendete una decisione di design, chiedetevi: "Questa scelta sta aumentando o diminuendo l'accoppiamento nel mio sistema?".

  

  

#### **3. L'Automazione è Libertà (Automation is Freedom)**

  

  

Infrastructure as Code (IaC) e Continuous Integration/Continuous Deployment (CI/CD) non sono "extra" o "nice-to-have". Sono pratiche fondamentali che trasformano lo sviluppo da un'attività artigianale e rischiosa a un processo ingegneristico, prevedibile e ad alta velocità. L'automazione riduce gli errori umani, elimina i compiti noiosi e libera gli sviluppatori di potersi concentrare sulla risoluzione di problemi creativi, che è dove creiamo il vero valore.

  

  

#### **4. La Semplicità come Prerequisito per la Complessità**

  

  

Sia Go che Svelte sono stati scelti per la loro semplicità filosofica. Abbiamo visto come, usando strumenti semplici e concetti chiari a ogni livello (un Value Object, una funzione Lambda, un componente Svelte), possiamo gestire la complessità che emerge dall'interazione di queste parti. I sistemi complessi che funzionano sono quasi sempre evoluzioni di sistemi semplici che funzionavano. Non cercate la complessità; gestitela con astrazioni semplici e chiare.

  

  

#### **5. Trattare l'Infrastruttura (e le Operations) come Codice**

  

  

L'era in cui gli sviluppatori "passavano il codice" a un altro team per il deployment è finita. In un modello DevOps e cloud-native, la responsabilità si estende a tutto il ciclo di vita. Trattare l'infrastruttura (IaC), il testing, il deployment (CI/CD) e l'observability come discipline ingegneristiche a tutti gli effetti è il segno di un team moderno e performante.

  

  

---

  

  

### 30.3. Oltre il Libro: I Vostri Prossimi Passi 🚀

  

  

Questo libro è una base solida, ma il mondo dell'ingegneria del software è in continua evoluzione. Ecco alcune aree in cui potete approfondire le vostre conoscenze per continuare a crescere.

  

  

**Approfondimenti Tecnici:**

  

  

- **Event Sourcing in Pratica**: Abbiamo introdotto il concetto, ma implementare un Event Store robusto, gestire lo snapshotting per le performance e il versioning degli eventi sono argomenti che meritano un libro a parte.

  

- **Data Mesh**: Man mano che un'organizzazione cresce, come si gestisce la "proprietà" dei dati tra decine o centinaia di Bounded Context? Il Data Mesh è un paradigma socio-tecnico emergente per affrontare questo problema su scala aziendale.

  

- **Advanced Cloud Networking & Security**: Approfondite le VPC di AWS, le security groups, le NACL, e pattern di sicurezza come il "zero trust".

  

- **WebAssembly (Wasm)**: Una tecnologia emergente che potrebbe rivoluzionare il modo in cui eseguiamo codice portabile e sicuro, sia sul frontend che sul backend (es. come runtime per funzioni serverless).

  

  

**Risorse Consigliate per lo Studio Continuo:**

  

  

- **Libri Classici**: Rileggete periodicamente "Domain-Driven Design" di Eric Evans e "Implementing Domain-Driven Design" di Vaughn Vernon. Aggiungete alla vostra libreria "Clean Architecture" di Robert C. Martin e "Building Microservices" di Sam Newman.

  

- **Blog e Autori**: Seguite figure chiave come Martin Fowler, Gregor Hohpe, e le pubblicazioni tecniche di aziende all'avanguardia come Netflix, Uber e Amazon.

  

- **Community**: Partecipate a conferenze (come DDD Europe, GOTO, QCon) e a meetup locali. La discussione e il confronto con altri professionisti sono fonti di apprendimento inestimabili.

  

  

---

  

  

### 30.4. L'Applicazione "Where Should I Be?": Possibili Evoluzioni

  

  

Il modo migliore per imparare è fare. Il nostro progetto di esempio è un'ottima base di partenza per sperimentare. Ecco alcune idee su come potreste estenderlo:

  

  

- **Implementare un `SocialContext`**: Permettete agli utenti di rendere pubblici i loro viaggi, di seguirsi a vicenda e di lasciare commenti. Questo vi costringerà a progettare nuove integrazioni tra contesti.

  

- **Implementare un `BookingContext`**: Integrate API reali (es. di hotel o compagnie aeree) per aggiungere funzionalità di prenotazione. Sarà un'ottima occasione per implementare un Anti-Corruption Layer robusto.

  

- **Rifattorizzare in Event Sourcing**: Provate a modificare il `TripPlanningContext` per renderlo completamente event-sourced. Implementate una funzione "Annulla Ultima Modifica" per vedere la potenza di questo pattern.

  

- **Migliorare il Frontend**: Aggiungete mappe interattive (usando librerie come Mapbox o Leaflet.js), funzionalità offline con i Service Worker, o animazioni più ricche.

  

  

---

  

  

### 30.5. Conclusione Finale: Costruire con Intenzione

  

  

Siamo giunti al termine. Spero che questo libro vi abbia lasciato non solo con una serie di competenze tecniche, ma con un nuovo modo di pensare al software.

  

  

Costruire software di qualità, specialmente su larga scala, non è mai un caso. Non è il risultato dell'uso dell'ultimo framework di moda o di una scrittura di codice febbrile. È il risultato di un **design intenzionale**. È il prodotto di decisioni deliberate, di compromessi ponderati e di una continua ricerca di chiarezza e semplicità.

  

  

I pattern e le pratiche che abbiamo discusso—dal DDD alla Clean Architecture, dall'IaC all'Observability—non sono dogmi da seguire ciecamente. Sono una bussola e una mappa. Sono un linguaggio condiviso per ragionare sulla complessità, per comunicare le nostre decisioni e per costruire sistemi che non solo risolvano i problemi di oggi, ma che siano anche pronti ad affrontare le sfide di domani.

  

  

Il vostro viaggio come architetti, designer e ingegneri del software è appena iniziato. Spero che questo libro vi sia stato una guida utile. Ora, andate e costruite qualcosa di straordinario.

  

**

**