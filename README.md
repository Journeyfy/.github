# JOURNEYFY  

## Idea 

**Tema**: guida di viaggio 

**Categorie di mercato**: guide turistiche interattive 

**Problema**: durante l'organizzazione di un viaggio ci si trova spesso a fare ricerche come: “10 cose da fare a ...”, “dove mangiare tipico a …" visionando decine di siti differenti. 

**Soluzione**: Applicazione web che consente ai suoi utilizzatori di ricercare una meta ed ottenere immediatamente una lista delle migliori attività da fare, dei posti da visitare e dei locali, tipici e non, in cui ristorarsi o divertirsi. Tutto centralizzato in una sola applicazione. Il punto di forza dell'applicazione è negli utilizzatori che, se registrati, avranno la possibilità di arricchire mete già esistenti con nuovi suggerimenti che saranno supervisionati da utenti moderatori e/o amministratori. 

 

## Funzionalità pensate 
| Funzionalità                                   | Priorità (1-5) |
|------------------------------------------------|----------------|
|      Ricerca destinazione                      |     5          |
|      Lista luoghi da vedere (con link a Maps)  |     5          |
|      Lista attività (con link a Maps)          |     5          |
|      Lista locali (con link a Maps)            |     5          |
|      Iscrizione all’app                        |     5          |
|      Cronologia mete ricercate                 |     4          |
|      Aggiunta/Modifica/Rimozione contenuti     |     4          |
|      Mete più gettonate                        |     3          |
|      Diario di viaggio (solo se registrati)    |     2          |
|      Blog (solo se registrati)                 |     1          |
|      Aggiunta di foto e video sul diario       |     1          |
|      Stampa album                              |     1          |

 

## Scenari e casi d’uso 
1. Come utente voglio aprire l’app e visualizzare una barra di ricerca che mi chiede dove voglio andare. Mentre digito vengono fuori i vari suggerimenti di destinazioni che corrispondono con quello che sto scrivendo. 

1. Come utente, dopo aver selezionato una meta, voglio visualizzare un ambiente che mi presenta l’immagine di copertina della città selezionata e un menu principale con opzioni che mi rimandano alle cose da vedere, le cose da fare/visitare e i posti in cui mangiare. Cliccando su ciascuna voce di menu vengo rimandato ai rispettivi ambienti in cui visualizzo una lista di attività/luoghi/locali ciascuna con un link che porta a Google Maps.  

1. Come utente voglio avere la possibilità di iscrivermi all’applicazione creando un’utenza locale. 

1. Come utente moderatore o amministratore voglio poter accedere all’applicazione come qualsiasi utente ma con una voce di menu aggiuntiva che mi fa accedere alle richieste di aggiunta/modifica/eliminazione da parte degli utenti. 

## Dettagli tecnici 

### Tecnologie per lo sviluppo 
| Deliverable| Tecnologia         |
|------------|--------------------|
| Frontend   | React              |
| Backend    | NodeJs con Fastify |
| Database   | MySQL              |
 

### Database 

Destination: [idDestination<number>, name<string>, popularity<number>] 

DestinationCoverImage: [idDestination<number>, image<blob>] 

Suggestion: [idSuggestion<number>, idDestination<number>, type<number>, title<string>,mapLink?<string> openAt?<string>, closeAt?<string>] 

User: [idUser<guid>, firstName<string>, lastName<string>, email<string>, password<hash>, idRole<number>, picutre?<string>, registeredOnUtc<datetime>) 

SuggestionRequest: [idRequest<guid>, status<number>, requestType<number>, idSuggestion?<number>, idUser<guid>, idDestination<number>, suggestionType<number>, title<string>, mapLink?<string> openAt?<string>, closeAt?<string>] 

Blog: [idBlog<guid>, title<string>, createdOnUtc<datetime>]

UserHasBlog: [idUser<guid>, idBlog<guid>] 

BlogArticle: [idBlogArticle<number>, idBlog<guid>, article<string>] 

BlogMedia [idBlogMedia<number>, idBlog<guid>, media<blob>] 



### Enumeratori 

SuggestionType: ToSee, ToDo, ToEat 

Role: Administrator, Moderator, User 

TodoRequestType: Add, Update, Delete 
