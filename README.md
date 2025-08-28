# sdk-engine-siarpicvalini-java



## Sistema Informativo Assistenza Riabilitativa PIC & Valutazione Iniziale



### Descrizione repository:



Il microservizio ha come scopo l'acquisizione dei dati inviati dalle Regioni in merito ai trattamenti riabilitativi erogati, nell'ambito dell'assistenza semiresidenziale e residenziale, a carattere intensivo, estensivo e di mantenimento di cui all'articolo 34 del decreto del Presidente del Consiglio dei ministri del 12 gennaio 2017.



I dati richiesti sono relativi al set di informazioni legate ai trattamenti riabilitativi di cui all'art. 1, previa valutazione multidimensionale dell'assistito, presa in carico e progetto riabilitativo individuale (PRI) ovvero piano individuale di assistenza e riabilitazione. Il tracciato 1 (SIAR_PIC) comprende le informazioni associate all'evento "presa in carico" (dati anagrafici del paziente, Azienda sanitaria di erogazione, struttura erogatrice, ecc.) che include anche i dati della valutazione iniziale dell'assistito.



Il Sistema SIAR viene alimentato con le informazioni relative ai trattamenti riabilitativi erogati a partire dal quarto trimestre 2023



L'invio dei file viene effettuato mediante un tracciato XML.

Per ogni tracciato XML, è fornito il relativo schema XSD di convalida a cui far riferimento



#### Struttura XML:





Campi del nodo di riferimento Trasmissione

-Tipo



Eventi:

- Presa in carico

- Presa in carico (valutazione iniziale)





Nodi di riferimento Presa in carico:

- Dati Anagrafici

- Residenza

- Erogazione

- Presa In Carico





Campi Dati Anagrafici:

- Identificativo univoco CUNI

- Validità del codice Identificativo dell'assistito

- Tipologia del codice Identificativo dell'assistito

- Anno di nascita

- Genere

- Cittadinanza

- Stato civile

- Responsabilità genitoriale



Campi Residenza: 

- Regione di residenza

- Azienda sanitaria di residenza

- Comune di residenza



Campi Erogatore:

- Regione di erogazione (campo chiave)

- Azienda sanitaria di erogazione (campo chiave)

- Struttura erogatrice (campo chiave)



Campi Presa In Carico:

- Data apertura PIC

- ID record

- Soggetto richiedente

- Setting assistenziale di erogazione

- Percentuale a carico del SSN

- Pianificazione condivisa delle cure in cartella/fascicolo



Nodi di riferimento Presa in carico (valutazione iniziale):

- Patologia

- Valutazione

- Operatore



Campi Patologia:

- Patologia principale

- Patologia concomitanteP



Campi Valutazione:

- Data valutazione iniziale

- Livello di Autonomia

- Grado mobilità

- Disturbi cognitivi

- Disturbi comportamentali

- Comunicazione

- Area sensoriale

- Bisogni internistico- assistenziali

- Stabilità clinica

- Presenza di un caregiver

- Supporto sociale

- Utilizzo di dispositivi/protesi/ortesi

- Ambito di intervento previsto dal PRI  1

- Ambito di intervento previsto dal PRI  2

- Ambito di intervento previsto dal PRI  3

- Ambito di intervento previsto dal PRI  4

- Ambito di intervento previsto dal PRI  5

- Ambito di intervento previsto dal PRI  6

- Scala utilizzata per classificazione disabilità 1

- Esito rilevazione della disabilità in ingresso 1

- Scala utilizzata per classificazione disabilità 2

- Esito rilevazione della disabilità in ingresso 2

- Scala utilizzata per classificazione disabilità 3

- Esito rilevazione della disabilità in ingresso 3

- Scala utilizzata per classificazione disabilità 4

- Esito rilevazione della disabilità in ingresso 4

- Scala utilizzata per classificazione disabilità 5

- Esito rilevazione della disabilità in ingresso 5

- Scala utilizzata per classificazione disabilità 6

- Esito rilevazione della disabilità in ingresso 6

- Durata complessiva prevista dal PRI

- Ore di trattamento totali previste dal PRI





Campi Operatore:



- Professionista coinvolto  MMG/PLS

- Professionista coinvolto  Medico specialista

- Professionista coinvolto Infermiere

- Professionista coinvolto  Operatore sociosanitario

- Professionista coinvolto  Fisioterapista

- Professionista coinvolto  Logopedista

- Professionista coinvolto  Terapista della neuro e psicomotricità dell'età evolutiva

- Professionista coinvolto  Terapista occupazionale

- Professionista coinvolto  Psicologo/a

- Professionista coinvolto  Assistente Sociale

- Professionista coinvolto  Educatore professionale

- Professionista coinvolto  Altri professionisti sanitari





## 📚 XSD di riferimento

Il file xsd è disponibile al seguente link [`docs/FLS_SIAR1.xsd`](docs/FLS_SIAR1.xsd).

### Struttura repository



La cartella principale è src/main/java che è organizzata nelle seguenti cartelle:



- it.mds.sdk.engine.config che raccoglie i file di configurazione

- it.mds.sdk.flusso.siar.picvalini che contiene il file necessario all'avvio dell'applicazione

- it.mds.sdk.flusso.siar.picvalini.controller che contiene i file che vengono invocati direttamente dal client

- it.mds.sdk.flusso.siar.picvalini.dto che contiene le classi che rappresentano il modello interno di sdk

- it.mds.sdk.flusso.siar.picvalini.mapper che contiene le classi di conversione



Nella cartella src/main/resources sono presenti le seguenti cartelle:

- META-INF che contiene file di configurazione

- sicof xhe contiene file .moustache

- template contiene un file di regole e file .csv, .xml e .xsd



sono presenti in resources anche file di configurazione:

- application.yaml

- config-flusso.properties

- csvHeaderMapping.properties

- logback-spring.xml

- tmp.xml



è presente il file pom.xml (Project Object Model), è un file XML che contiene le informazioni sul progetto e dettagli sulle configurazioni utilizzate da Maven per eseguire la build del progetto



### Prerequisiti e dipendenze



Il microservizio può girare su qualsiasi sistema operativo per cui è prevista una JVM (Java Virtual Machine) e utilizza la versione 2.7.17 di Spring Boot.



## Istruzioni per l'installazione
Per l'installazione e l'avvio dell'engine seguire la documentazione tecnica dettagliata disponibile all'url [`INSTALL.md`](https://github.com/ministero-salute/sdk-utilities-regole-properties/blob/main/INSTALL.md).



## 📝 Licenza
Questo progetto è rilasciato sotto licenza BSD 3-Clause License così come definita [BSD 3-Clause License](./LICENSE).

## 🤝 Contributi
I contributi sono benvenuti. Si prega di consultare il file [`CONTRIBUTING.md`](CONTRIBUTING.md) per le linee guida su come contribuire al progetto.

## 📞 Contatti
Per ulteriori informazioni, contattare:

- **Service Desk - Ministero della Salute**: servicedesk.mds@medilifegroupspa.com
- **Amministrazione titolare**: [Ministero della Salute](https://www.salute.gov.it)
## mantainer:

 Accenture SpA until January 2026
