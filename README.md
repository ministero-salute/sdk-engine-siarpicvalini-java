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


XSD:
```
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://flussi.mds.it/FLS_SIAR1" xmlns:fls="http://flussi.mds.it/FLS_SIAR1" xmlns:xs="http://www.w3.org/2001/XMLSchema">
	<xs:simpleType name="tipoTrasmissione">
		<xs:restriction base="xs:string">
			<xs:pattern value="[IVC]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="Id_Rec">
		<xs:restriction base="xs:string">
			<xs:length value="88"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="CUNI">
		<xs:restriction base="xs:string">
			<xs:length value="88"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="validitaCI">
		<xs:restriction base="xs:integer">
			<xs:pattern value="[0-1]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="tipologiaCI">
		<xs:restriction base="xs:integer">
			<xs:enumeration value="0"/>
			<xs:enumeration value="1"/>
			<xs:enumeration value="2"/>
			<xs:enumeration value="3"/>
			<xs:enumeration value="4"/>
			<xs:enumeration value="97"/>
			<xs:enumeration value="98"/>
			<xs:enumeration value="99"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="anno">
		<xs:restriction base="xs:string">
			<xs:pattern value="(1899|19[0-9]{2}|20[0-9]{2}|2099)|9999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="genere">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="cittadinanza">
		<xs:restriction base="xs:string">
			<xs:pattern value="[A-Z]{2}"/>
			<xs:pattern value="99"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="statoCivile">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-9]{1}|[10][99]{2}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="responsabilitaGenitoriale">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-6]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="titoloStudio">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-7]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="condizioneProfessionale">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-7]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="regioneResidenza">
		<xs:restriction base="xs:string">
			<xs:pattern value="010"/>
			<xs:pattern value="020"/>
			<xs:pattern value="030"/>
			<xs:pattern value="041"/>
			<xs:pattern value="042"/>
			<xs:pattern value="050"/>
			<xs:pattern value="060"/>
			<xs:pattern value="070"/>
			<xs:pattern value="080"/>
			<xs:pattern value="090"/>
			<xs:pattern value="100"/>
			<xs:pattern value="110"/>
			<xs:pattern value="120"/>
			<xs:pattern value="130"/>
			<xs:pattern value="140"/>
			<xs:pattern value="150"/>
			<xs:pattern value="160"/>
			<xs:pattern value="170"/>
			<xs:pattern value="180"/>
			<xs:pattern value="190"/>
			<xs:pattern value="200"/>
			<xs:pattern value="999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="comuneResidenza">
		<xs:restriction base="xs:string">
			<xs:pattern value="[a-zA-Z0-9]{6}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="regioneErogazione">
		<xs:restriction base="xs:string">
			<xs:pattern value="010"/>
			<xs:pattern value="020"/>
			<xs:pattern value="030"/>
			<xs:pattern value="041"/>
			<xs:pattern value="042"/>
			<xs:pattern value="050"/>
			<xs:pattern value="060"/>
			<xs:pattern value="070"/>
			<xs:pattern value="080"/>
			<xs:pattern value="090"/>
			<xs:pattern value="100"/>
			<xs:pattern value="110"/>
			<xs:pattern value="120"/>
			<xs:pattern value="130"/>
			<xs:pattern value="140"/>
			<xs:pattern value="150"/>
			<xs:pattern value="160"/>
			<xs:pattern value="170"/>
			<xs:pattern value="180"/>
			<xs:pattern value="190"/>
			<xs:pattern value="200"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="codASL">
		<xs:restriction base="xs:string">
			<xs:length value="3"/>
			<xs:pattern value="[0-9]{3}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="strutturaErogatrice">
		<xs:restriction base="xs:string">
			<xs:maxLength value="6"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="soggettoRichiedente">
		<xs:restriction base="xs:string">
			<xs:pattern value="[0-7]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="assistenzaErogazione">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-5]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="percentualeSSN">
		<xs:restriction base="xs:decimal">
			<xs:minInclusive value="0"/>
			<xs:maxInclusive value="100"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="pianificazioneCondivisa">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-2]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="autonomia">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="gradoMobilita">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-5]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="disturbo">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="areaSensoriale">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="bisognoAssistenziale">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-8]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="ambito">
		<xs:restriction base="xs:string">
			<xs:length value="2"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="esito">
		<xs:restriction base="xs:string">
			<xs:maxLength value="5"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="durataPri">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-9]{1}|[10-99]{2}|[100-365]{3}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="orePri">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-9]{1}|[10-99]{2}|[100-999]{3}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="professionista">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-2]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="patologia">
		<xs:restriction base="xs:string">
			<xs:length value="5"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="bisogno">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-2]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="stabilita">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-6]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="supporto">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="scalaDis1">
		<xs:restriction base="xs:string">
			<xs:pattern value="[0-9]{1}|1[0-9]{1}|2[0-2]{1}|99"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="scalaDis2">
		<xs:restriction base="xs:string">
			<xs:pattern value="[0-9]{1}|1[0-9]{1}|2[0-2]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:element name="Trasmissione">
		<xs:complexType>
			<xs:attribute name="tipo" type="fls:tipoTrasmissione" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Assistito">
		<xs:complexType>
			<xs:sequence>
				<xs:element ref="fls:DatiAnagrafici"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="DatiAnagrafici">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="CUNI" type="fls:CUNI"/>
				<xs:element ref="fls:Residenza"/>
				<xs:element name="validitaCI" type="fls:validitaCI"/>
				<xs:element name="tipologiaCI" type="fls:tipologiaCI"/>
				<xs:element name="AnnoNascita" type="fls:anno"/>
				<xs:element name="Genere" type="fls:genere"/>
				<xs:element name="Cittadinanza" type="fls:cittadinanza"/>
				<xs:element name="StatoCivile" type="fls:statoCivile"/>
				<xs:element minOccurs="0" name="ResponsabilitaGenitoriale" type="fls:responsabilitaGenitoriale"/>
				<xs:element name="TitoloStudio" type="fls:titoloStudio"/>
				<xs:element name="CondizioneProfessionale" type="fls:condizioneProfessionale"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Residenza">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="Regione" type="fls:regioneResidenza"/>
				<xs:element name="ASL" type="fls:codASL"/>
				<xs:element name="Comune" type="fls:comuneResidenza"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Erogatore">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="CodiceRegione" type="fls:regioneErogazione"/>
				<xs:element name="CodiceASL" type="fls:codASL"/>
				<xs:element name="StrutturaErogatrice" type="fls:strutturaErogatrice"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="PresaInCarico">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="Id_Rec" type="fls:Id_Rec"/>
				<xs:element minOccurs="0" name="PercentualeSSN" type="fls:percentualeSSN"/>
				<xs:element minOccurs="0" name="PianificazioneCondivisa" type="fls:pianificazioneCondivisa"/>
				<xs:element minOccurs="0" name="SettingAssistenziale" type="fls:assistenzaErogazione"/>
			</xs:sequence>
			<xs:attribute name="Data" type="xs:date" use="required"/>
			<xs:attribute name="SoggettoRichiedente" type="fls:soggettoRichiedente" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Patologia">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="Principale" type="fls:patologia"/>
				<xs:element minOccurs="0" name="Concomitante" type="fls:patologia"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Valutazione">
		<xs:complexType>
			<xs:sequence>
				<xs:element ref="fls:Patologia"/>
				<xs:element name="Autonomia" type="fls:autonomia"/>
				<xs:element name="GradoMobilita" type="fls:gradoMobilita"/>
				<xs:element ref="fls:Disturbi"/>
				<xs:element name="AreaSensoriale" type="fls:areaSensoriale"/>
				<xs:element name="BisognoInternistico" type="fls:bisognoAssistenziale"/>
				<xs:element name="StabilitaClinica" type="fls:stabilita"/>
				<xs:element minOccurs="0" name="PresenzaCaregiver" type="fls:bisogno"/>
				<xs:element name="SupportoSociale" type="fls:supporto"/>
				<xs:element minOccurs="0" name="UtilizzoDisProtesiOrtesi" type="fls:bisogno"/>
				<xs:element name="AmbitoInterventoPRI1" type="fls:ambito"/>
				<xs:element minOccurs="0" name="AmbitoInterventoPRI2" type="fls:ambito"/>
				<xs:element minOccurs="0" name="AmbitoInterventoPRI3" type="fls:ambito"/>
				<xs:element minOccurs="0" name="AmbitoInterventoPRI4" type="fls:ambito"/>
				<xs:element minOccurs="0" name="AmbitoInterventoPRI5" type="fls:ambito"/>
				<xs:element minOccurs="0" name="AmbitoInterventoPRI6" type="fls:ambito"/>
				<xs:element name="ScalaClassDis1" type="fls:scalaDis1"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis1" type="fls:esito"/>
				<xs:element name="ScalaClassDis2" type="fls:scalaDis1"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis2" type="fls:esito"/>
				<xs:element name="ScalaClassDis3" type="fls:scalaDis1"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis3" type="fls:esito"/>
				<xs:element minOccurs="0" name="ScalaClassDis4" type="fls:scalaDis2"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis4" type="fls:esito"/>
				<xs:element minOccurs="0" name="ScalaClassDis5" type="fls:scalaDis2"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis5" type="fls:esito"/>
				<xs:element minOccurs="0" name="ScalaClassDis6" type="fls:scalaDis2"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis6" type="fls:esito"/>
				<xs:element name="DurataComplessivaPRI" type="fls:durataPri"/>
				<xs:element name="OreTrattTotPRI" type="fls:orePri"/>
				<xs:element ref="fls:Operatore"/>
			</xs:sequence>
			<xs:attribute name="Data" type="xs:date" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Disturbi">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="Cognitivi" type="fls:disturbo"/>
				<xs:element name="Comportamentali" type="fls:disturbo"/>
				<xs:element name="Comunicazione" type="fls:disturbo"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Operatore">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="ProfCoinMMGPLS" type="fls:professionista"/>
				<xs:element name="ProfCoinMedicoSpec" type="fls:professionista"/>
				<xs:element name="ProfCoinInfermiere" type="fls:professionista"/>
				<xs:element name="ProfCoinOSS" type="fls:professionista"/>
				<xs:element name="ProfCoinFisio" type="fls:professionista"/>
				<xs:element name="ProfCoinLogopedista" type="fls:professionista"/>
				<xs:element name="ProfCoinTerPsico" type="fls:professionista"/>
				<xs:element name="ProfCoinTerOccup" type="fls:professionista"/>
				<xs:element name="ProfCoinPsicologo" type="fls:professionista"/>
				<xs:element name="ProfCoinAssSociale" type="fls:professionista"/>
				<xs:element name="ProfCoinEduProf" type="fls:professionista"/>
				<xs:element name="ProfCoinAltriProfSan" type="fls:professionista"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="FlsSiar_1">
		<xs:complexType>
			<xs:sequence>
				<xs:element maxOccurs="unbounded" ref="fls:Assistenza"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Assistenza">
		<xs:complexType>
			<xs:sequence>
				<xs:element ref="fls:Trasmissione"/>
				<xs:element ref="fls:Assistito"/>
				<xs:element ref="fls:Erogatore"/>
				<xs:element ref="fls:Eventi"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Eventi">
		<xs:complexType>
			<xs:sequence>
				<xs:element ref="fls:PresaInCarico"/>
				<xs:element maxOccurs="unbounded" ref="fls:Valutazione"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
</xs:schema>
```

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

### Istruzioni per l'installazione

Per poter eseguire la build: 
build system maven,
comando mvn clean package

Per eseguire l'installazione è necessario prendere il jar generato dal build system e copiarlo in una cartella, successivamente all'interno della root folder ( / su Linux mentre C:\ su Windows) creare la cartella sdk e tutte le sottocartelle e i file necessari:
```
 /
 +- sdk
   +- db - la directory in cui viene genrato il db sqllite per la storicizzazione dele anagrafiche
   +- dir - la directory in cui inserire i csv da validare e inviare
   +- esiti - la directory in cui verranno depositati i file con gli esiti delle esecuzioni dell'sdk
   +- log - la directory in cui verranno scritti i log delll'applicativo
   +- progressivo - la directory in cui l'applicativo mantiene un file dat per la generazione degli id di esecuzione
   +- properties - la directory contenente i file di configurazione dell'sdk
      +- config-flusso.properties - file di configurazione principale (da referenziare in fase di avvio)  
      \- configurazioni-anagrafiche.properties - file per la configurazione del recupero delle anagrafiche 
   +- regole - la directory contenente le regole da applicare ai csv
   +- run - la cartella contenente i file di run per ogni singola esecuzione
   +- xmloutput - la directory contenente gli xml di output
   \- sent - la directory in cui vengono spostati gli xml inviati al ministero
``` 
- #### config-flusso.properties
```
nome.flusso=<nome del flusso lato ministero>
flusso.categoria=<categoria del flusso lato ministero>
flusso.codifica=<codice identificativo del flusso lato ministero>
regole.percorso=<path completo al file xml delle regole: /sdk/regole/regole.xml>

xmloutput.percorso=<path completo della folder in cui scrivere l'output>/SDK_{{periodoRiferimento}}_{{idRun}}.xml (/sdk/xmloutput/SDK_{{periodoRiferimento}}_{{idRun}}.xml)

sent.percorso=<path completo della directory in cui spostare gli xml inviati al ministero: /sdk/sent/>
flusso.percorso=<path completo della directory in cui verranno depositati i file csv: /sdk/dir/>
soglia.invio.mds=<numero intero indicante quanti la soglia di record validi per file affinché possa essere inviato l'xml di output: 100>
separatore=<carattere di separazione dei valori nel csv: ~>

run.percorso=<path completo della directory in storicizzare i file di run: /sdk/run>
esito.percorso=<path completo della directory in cui depositare i file di esito: /sdk/esiti>
progressivo.percorso=<path completo della directory in cui generare il file dat dei progressivi: /sdk/progressivo>

url.rest.gaf=<url per l'invio degli xml: https://api.salute.gov.it/api/gaf/upldfunc>
gaf.sender.authorizer.token-issuer.url=<url per l'autenticazione dell'invio: https://nsis-ids.sanita.it/nidp/oauth/nam/token>
gaf.sender.authorizer.token-issuer.grant_type=<flow di autenticazione: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.username=<username: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.password=<password: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.client_id=<client id: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.client_secret=<client secret: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.scope=<scopes a cui deve appartenere l'utente: verranno forniti dal ministero>
gaf.sender.authorizer.type=<tipo di token di autenticazione: JWT>
gaf.sender.type=REST
gaf.sender.fileType=<categoria del flusso: valorizzare come flusso.categoria>
```

- #### configurazioni-anagrafiche.properties
```
sqlite.database.file.path=<path completo in cui creare il db sqllite: /sdk/db/anagrafica.db>
resilienza.ore=<time to live delle anagrafiche nel DB in ore: 2>

client.rest.headers.x-pplication-id: APP_ID_REGISTRYDOWNLOADER_CLIENT
client.type=REST
client.host=<url del gestore anagrafi: https://api.salute.gov.it/api/gestanag/v1>

rest.authorizer.type=<tipo del token di autorizzazione/autenticazione: JWT>
rest.authorizer.token-issuer.url=<url per la generazione di un token di autenticazione: https://nsis-ids.sanita.it/nidp/oauth/nam/token>
rest.authorizer.token-issuer.grant_type=<tipo di flow da utilizzare per l'autenticazione: client_credentials>
rest.authorizer.token-issuer.username=<username: verrà fornita dal ministero>
rest.authorizer.token-issuer.password=<password: verrà fornita dal ministero>
rest.authorizer.token-issuer.client_id=<client id: verrà fornita dal ministero>
rest.authorizer.token-issuer.client_secret=<client secret: verrà fornita dal ministero>
rest.authorizer.token-issuer.scope=<scopes a cui deve appartenere l'utenza: verrà fornita dal ministero>
```

### Istruzioni di avvio

Per avviare l'applicativo eseguire il seguente comando
```
java -jar <path completo del jar> --config=<path completo al file di configurazione principale>
```
Il comando farà partire il software che rimarrà in attesa di richieste sulla porta 8080

#### Avvio validazione di un csv
```
curl --location --request POST 'http://localhost:8080/v1/flusso/SIAR_PICVALINI' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--data-raw '{
    "nomeFile": "test.csv",
    "idClient": "1663" ,
    "modalitaOperativa":"P",
    "annoRiferimento": "2022",
    "periodoRiferimento": "13",
    "codiceRegione": "120"
}'
```

#### Recupero dell'esito di un'elaborazione
```
curl --location --request GET 'http://localhost:8080/v1/flusso/SIAR_PICVALINI/info?idRun=34' --header 'Accept: */*'
```

### Detentori di copyright

### Incaricati del mantenimento del progetto open source

### Contatti per segnalazioni

## mantainer:
 Accenture SpA until January 2026



