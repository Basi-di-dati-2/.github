# 🎮 PLAYWISE 🎮
PlayWise è una piattaforma per la scoperta e la valutazione di videogiochi, arricchita da un sistema di raccomandazione personalizzata basato su tecniche di Machine Learning. Il progetto è stato sviluppato come caso di studio accademico per esplorare l'integrazione di Database NoSQL, AI, MLOps e SE4AI in un contesto applicativo reale.



## 🚀 Overview del Progetto 🚀 
**PlayWise** è una piattaforma web pensata per aiutare gli utenti a esplorare, valutare e condividere opinioni su migliaia di videogiochi. Ispirata a servizi come Metacritic, PlayWise offre un'esperienza interattiva basata su recensioni della community e un ampio catalogo di titoli, arricchito da metadati e contenuti multimediali.

La piattaforma adotta un’**architettura a microservizi** per garantire scalabilità, modularità e facilità di manutenzione. Ogni funzionalità core (gestione utenti, giochi, recensioni, raccomandazioni) è incapsulata in un microservizio indipendente, orchestrato tramite un API Gateway e Service Discovery.


### 👥 Cosa può fare un utente su PlayWise?

- 🔍 **Esplorare il catalogo**: cercare videogiochi filtrando per genere, piattaforma, anno di uscita, e altro.
- 📄 **Visualizzare dettagli approfonditi**: accedere a informazioni complete per ogni gioco, incluse descrizioni, trama, immagini e valutazioni.
- ✍️ **Lasciare recensioni**: esprimere la propria opinione assegnando un punteggio da 0 a 100 e scrivendo una recensione testuale.
- 🎯 **Ricevere raccomandazioni personalizzate**: ottenere suggerimenti basati sulle proprie preferenze e valutazioni, grazie a un sistema di raccomandazione intelligente.


### 🧰 Tecnologie utilizzate
- **Linguaggi**: Java, Python
- **Backend & API**: FastAPI, Spring Boot, REST
- **Frontend**: HTML, CSS, Javascript, React
- **Database**: MongoDB
- **Machine Learning**: SVD con [Surprise](http://surpriselib.com)
- **MLOps**: DVC, MLflow, DAGsHub
- **DevOps/CI-CD**: Ruff, Docker, GitHub Actions
- **Monitoring**: Prometheus, Grafana
- **Service Discovery & Routing**: Eureka, API Gateway

### 🧩 Microservizi

| Microservizio | Linguaggio | Descrizione | Link Repository |
|---------------|------------|-------------|-----------------|
| **API Gateway** | Java | Punto di ingresso per tutte le richieste. Smista il traffico verso i microservizi registrati al Discovery Server. | [🔗 gateway-service](https://github.com/Basi-di-dati-2/api-gateway) |
| **Service Discovery** | Java | Implementato con Eureka. Permette la registrazione dinamica dei microservizi e il bilanciamento interno. | [🔗 discovery-service](https://github.com/Basi-di-dati-2/discovery_server) |
| **User Service** | Java | Gestione degli utenti e autenticazione. | [🔗 user-service](https://github.com/Basi-di-dati-2/user_project) |
| **Game Service** | Java | Gestione del catalogo videogiochi: metadati, piattaforme, media score. | [🔗 game-service](https://github.com/Basi-di-dati-2/Basi-di-dati-2-Pinto-Torino) |
| **Review Service** | Java | Gestione delle recensioni e dei punteggi utente. | [🔗 review-service](https://github.com/Basi-di-dati-2/review_project) |
| **Admin Service** | Java | Gestione e Visualizzazione di Statistiche della piattaforma. | [🔗 admin-service](https://github.com/Basi-di-dati-2/admin-project) |
| **Recommendation Service** | Python | Sistema di raccomandazione AI. Espone API REST per suggerimenti personalizzati e raccoglie feedback. | [🔗 recommendation-service](https://dagshub.com/FrancescoPinto02/SE4AI-Pinto-Torino) |




## 🔧 Installazione 🔧
### ✅ Requisiti
Per eseguire PlayWise in locale è necessario avere installati i seguenti strumenti:

- [Java JDK 17](https://adoptium.net/en-GB/temurin/releases/?version=17) – richiesto per i microservizi Spring Boot
- [Apache Maven](https://maven.apache.org/download.cgi) – per la build dei servizi Java
- [Git](https://git-scm.com/downloads) – per clonare i repository
- [Docker](https://www.docker.com/products/docker-desktop) – per eseguire i container e i servizi dipendenti

### 📥 Clonare le Repository 
Creare una cartella, posizionarsi al suo interno e clonare tutte le repository presenti all'interno dell'[organizzazione](https://github.com/Basi-di-dati-2). Per clonare una repository è possibile utilizzare il seguente comando:
```bash
git clone https://github.com/Basi-di-dati-2/nomeRepository.git
```
> ⚠️ Assicurati di sostituire nomeRepository con il nome reale di ciascuna repository.

### 🧱 Build dei microservizi Java
Utilizzare Maven per effettuare la build dei microservizi Java. Per ogni microservizio java, posizionarsi all`interno della root (cartella che contiene pom.xml) ed utilizzare il seguente comando:
```bash
mvn clean install
```

### 🐳 Avvio dei Container
Scaricare ed inserire il file docker-compose all`interno della cartella principale ed utilizzare il seguente comando:
```bash
docker-compose up --build
```
> ⚠️ Assicurati di aver avviato Docker prima di utilizzare il comando.


### 🎉 Enjoy!
Una volta che tutti i container docker saranno avviati, accedere alla home di PlayWise tramite il seguente link:
```bash
http://localhost:5173 
```

### 🔍 Configurazione Grafana (OPZIONALE)
Per utilizzare Grafana è necessario configurare la dashboard. Per fare ciò, accedere al seguente link:
```bash
http://localhost:3000 
```
Accedere utilizzando le credenziali di default:
```bash
utente: admin
password: admin
```
Impostare credenziali personalizzate (opzionale), navigare su **Settings** e poi su **Data Source**. Fare Click su **Add Data Source** e nel campo **URL** aggiungere Prometheus:
```bash
http://prometheus:9090
```
Una volta salvate le impostazione e testato il collegamento, andare in **dashboard** ed importare il file JSON con la configurazione: [grafana_dashboard.json](https://github.com/FrancescoPinto02/SE4AI-Pinto-Torino/blob/main/monitoring/grafana_dashboard.json) 

> ⚠️ Nel caso in cui i pannelli della dashboard mostrassero un errore, provare ad editarli e salvare il tutto.
