# Konzeption, Entwurf und Entwicklung eines Lehrstuhlinformationssystems (Prof. Strecker)

## Ziel: Entwurf und prototypische Implementierung eines Lehrstuhlinformationssystems als Web-Applikation mit Elixir, Phoenix & PostgreSQL

> Ein Lehrstuhlinformationssystem unterstützt die Mitarbeiter eines Lehrstuhls bei der Durchführung ihrer administrativen Aufgaben.
> Die administrativen Aufgaben an einem Lehrstuhl sind vielfältig und umfassen grob die Aufgabenfelder Forschung, Lehre und universitäre Selbstverwaltung.
> Im Bereich der Lehre zählen zu diesen Aufgaben die Planung, Organisation und Durchführung von Klausuren und Seminaren sowie die Planung, Organisation und Betreuung von Abschlussarbeiten (Bachelorarbeit, Masterarbeit, Diplomarbeit).
> Für diese ausgewählten administrativen Aufgaben soll ein Lehrstuhlinformationssystem entworfen und als Web-Applikation mit der Programmiersprache [Elixir](https://elixir-lang.org), dem Web-Framework [Phoenix](https://phoenixframework.org) und dem RDBMS [PostgreSQL](https://postgresql.org) (Version 17+) implementiert werden.
> Dabei soll auf bereits vorliegenden Vorarbeiten aufgebaut werden (u.a. sind Teile des Datenbankschemas bereits entworfen und Teile davon bereits als Web-App implementiert). 

> Hinweis: Der Begriff "Lehrstuhlinformationssystem" ist (bislang) in der Fachsprache der Wirtschaftsinformatik nicht differenziert behandelt und kaum konturiert. Campusmanagementsysteme weisen zu Lehrstuhlinformationssysteme u.U. gewisse Überschneidungen auf. Wir gehen von der Vorstellung aus, dass es sich in einer ersten Näherung um ein typisches Informationssystem zur Verwaltung und Auswertung von Daten handelt, die während der Aufgabendurchführung der genannten Aufgaben benötigt werden. 

## Aufgabenbeschreibung

Ihre Auseinandersetzung beginnt damit, dass Sie sich die Entwurfs- und Implementierungsziele erschließen und daran anschließend beginnen, die fachlichen Anforderungen an das zu entwickelnde Informationssystem zu erheben, zu verstehen und zu konturieren und dabei iterativ diese fachlichen Anforderungen in nicht-funktionalen und funktionalen Anforderungen an die Software-Entwicklung und an den zu entwickelnden Softwareprototyp zu konkretisieren.
Sie diskutieren (mit Betreuer) dazu auch Zielkonflikte und andere Beziehungen zwischen Anforderungen und treffen Entwurfsentscheidungen zwischen Entwurfsalternativen, die Sie zuvor herausgearbeitet haben.
Iterativ reflektieren Sie die Softwarearchitektur und die Struktur der Datenhaltung und entwerfen das Datenbankschema, das Sie der Software-Entwicklung zugrunde legen.   
Iterativ wechseln Sie modellieren, programmieren, dokumentieren, testen und erproben ab - und wählen dabei ein Ihnen sinnvoll erscheinendes Vorgehen, das Sie u.U. an einzelnen (fachlichen) Anforderungen ausrichten (viele agile Vorgehensmodelle schlagen ein solches Vorgehen vor).
Sie zielen darauf, nach jeder Iteration eine lauffähige Funktionalität (prospektiven Anwendern am Lehrstuhl) demonstrieren zu können. 
Wir am Lehrstuhl fungieren als "prospektive Anwender" in der Rolle des "Kunden" (der Begriff passt nicht; hat sich in agilen Vorgehensmodellen jedoch etabliert).


## Anwendungskontext des zu entwickelnden Lehrstuhlinformationssystems  

Das Lehrstuhlinformationssystem soll für den [Lehrstuhl für BWL, insbes. Entwicklung von Informationssystemen (EvIS)](https://fernuni-hagen.de/evis) an der Fakultät für Wirtschaftswissenschaft der FernUniversität in Hagen entwickelt werden.
Die folgende Darstellung des Anwendungskontexts ergänzen Sie in Ihrem Team durch eine sorgfältige Auswertung der Website des Lehrstuhls.
Der Lehrstuhl hat mehrere Mitarbeiter in verschiedenen organisatorischen Rollen (Professor, wissenschaftlicher Mitarbeiter, nicht-wissenschaftlicher Mitarbeiter, ...).
Anwender des Lehrstuhlinformationssystems sind ausschließlich Mitarbeiter des Lehrstuhls.
Bislang wird am Lehrstuhl kein dediziertes Lehrstuhlinformationssystem eingesetzt.
Mit dem Lehrstuhlinformationssystem soll zukünftig das Verwalten und Auswerten von Daten über Klausuren, Seminare und Abschlussarbeiten ermöglicht werden.
Idealerweise sollen Daten aus dem in der Fakultät eingesetzten web-basierten Informationssystem WebRegIS per Datenexport/Datenimport übernommen werden können. Derzeit ist der strukturierte Datenexport aus WebRegIS jedoch noch nicht möglich und daher wird vorläufig die manuelle Datenübernahme aus WebRegIS anvisiert und das bedeutet, für das Seminar gehen wir von einer manuellen Dateneingabe in das Lehrstuhlinformationssystem aus.

Das Lehrstuhlinformationssystem ist als WebApp zu konzipieren, um Zugriff von innerhalb und außerhalb des FernUniversitäts-Rechnernetzes zu ermöglichen und um sowohl mobile als auch stationäre Endgeräte der Mitarbeiter nutzen zu können.
Die Benutzungsschnittstelle des Lehrstuhlinformationssystems soll daher sowohl die Nutzung auf mobilen wie auch auf stationären Endgeräten ermöglichen und sich an das jeweilige Endgerät anpassen. 

Das Lehrstuhlinformationssystem soll das Sicherheitsniveau gängiger WebApps einhalten, die Personen-bezogene Daten verarbeiten. 

## Fachliche Anforderungen

### Fachliche Anforderungen : Seminare

Die Lehrstuhlmitarbeiter betrachten Seminare anders als Studierende zunächst abstrakt, da ein Seminar zu einem bestimmten Thema in verschiedenen Semestern wiederholt (angeboten) werden kann. Ökonomisch ist dies überaus sinnvoll, da die Planung eines Seminars einen nicht unerheblichen Zeitaufwand bedingt. Neben einem Thema ist ein "abstraktes" Seminar durch eine textuelle Beschreibung der (didaktischen) Zielsetzung des Seminars und eine kurze inhaltliche Beschreibung charakterisiert.

Ein konkretes Seminar stellt eine Konkretisierung eines abstrakten Seminars dar. 
Ein konkretes Seminar findet in einem bestimmten Semester statt, hat einen bestimmten Titel, eine bestimmte Aufnahmekapazität und die Präsenzphase des Seminars findet an bestimmten Tagen statt.

An einem konkreten Seminar nehmen mehrere Studenten teil.
Die Teilnahme an einem Seminar drückt sich durch eine Seminarleistung aus, die aus mehreren Teilleistungen besteht.
In den Prüfungsordnungen der Studiengänge der Fakultät sind eine schriftliche und eine mündliche Teilleistung vorgeschrieben.
Die schriftliche Teilleistung wird als "Seminararbeit" bezeichnet. Es soll der Titel der Seminararbeit und das Datum der Einreichung erfasst werden ebenso wie ein Notenvorschlag und eine Teilnote.
Die mündliche Teilleistung wird als Fachvortrag erbracht. Es soll der Titel des Fachvortrags und das Datum des Vortrags erfasst werden. Zudem sollen Beginn und Ende des Fachvortrags erfasst werden - sowie ein Notenvorschlag und eine Teilnote.  
Für die Seminarleistung wird eine Gesamtnote erfasst.

Ein Student mit durch seine Matrikelnummer identifiziert. Es wird der vollständige Namen inklusive aller Vornamen und Nachnamen erfasst sowie das Geburtsdatum des Studenten.

Für ein konkretes Seminar ist ein bestimmter Mitarbeiter verantwortlich zuständig.

In der Regel betreut ein Mitarbeiter mehrere Studenten hinsichtlich eines konkreten Seminars und begutachtet deren Teilleistungen.

Mitarbeiter werden über einen Vornamen und einen Nachnamen und ein Geburtsdatum beschrieben.


Das Lehrstuhlinformationssystem soll den Mitarbeitern des Lehrstuhls _zumindest_ folgende _Auswertungsmöglichkeiten_ bieten:

- Welches Seminar wurde in welchem Semester angeboten?
- Welcher Mitarbeiter war für das Seminar zuständig?
- Welche Studenten haben an welchem Seminar teilgenommen?
- Welche Seminarnote hat ein bestimmter Student in welchem Seminar erzielt?
- Welche Studenten sind von einem Seminar zurückgetreten und aus welchem Grund (kann auch "ohne Angabe von Gründen" sein)?
- ... 


> Hinweis: Sie dürfen in Ihrem Team sehr gerne über weitere Daten diskutieren, die sinnvoll ergänzt werden können, z.B. hat ein konkretes Seminar in aller Regel eine Seminarvorbesprechung an einem bestimmten Termin.

> Hinweis: Seien Sie in Bezug auf die vermeintlichen Beziehungstypen in Ihrem Datenmodell und gleichmaßen in Bezug auf Fremdschlüssel in Ihrem Datenbankschema achtsam und vorsichtig: Nicht alle vermeintlich sinnvollen Beziehungstypen in einem Datenmodell sind für die Architektur des Informationssystems sinnvoll, z.B. ist ein Beziehungstyp "belegt" in "Student - belegt - Seminar" vermutlich nicht zielführend, da die Beziehung zwischen einem Student und einem Seminar über die Seminarleistung des Studenten hergestellt wird (die leider auch als "nicht abgegeben" und damit "nicht bestanden" enden kann). Bevor Sie das finale Schema der Datenbank konzipieren, sollten Sie sich unbedingt mit den in Phoenix und in Ecto vorgesehenen Konventionen vertraut machen und die durch Ecto vorgesehene Umsetzung von One-to-Many- und Many-to-Many-Relationships nachvollziehen. 


### Fachliche Anforderungen : Abschlussarbeiten
Ähnlich wie bei den Seminaren konzipieren Lehrstuhlmitarbeiter die Abschlussarbeiten zunächst abstrakt.
Dazu wird für jede abstrakte Abschlussarbeit ein Thema festgelegt und eine Themenskizze ausgearbeitet, in welcher die Anforderungen an die Abschlussarbeit in einem kurzen Text beschrieben werden.
Diese abstrakten Abschlussarbeiten können an mehrere Studierende vergeben und in mehreren Semestern eingesetzt werden.
Thematisch werden die Arbeiten in der Regel einem der Forschungsprojekte des Lehrstuhls zugeordnet.
Momentan wird an den Projekten TOOL, IMP und SPORT geforscht.

Eine konkrete Abschlussarbeit entsteht durch die Vergabe einer abstrakten Abschlussarbeit an einen Studenten und wird von einem Mitarbeiter des Lehrstuhls betreut.
In Absprache mit dem Betreuer kann der Student Schwerpunkte setzen und das Thema leicht anpassen.
Ergebnis dieser Absprachen ist eine angepasste Themenskizze für die konkrete Abschlussarbeit.
Die konkrete Abschlussarbeit wird zu einem festgelegten Datum beim Prüfungsamt angemeldet und hat ein verbindliches Abgabedatum.

Das Lehrstuhlinformationssystem soll den Mitarbeitern des Lehrstuhls _zumindest_ folgende _Auswertungsmöglichkeiten_ bieten:

- Welche Abschlussarbeiten wurden in einer vorgegebenen Zeitspanne verfasst?
- Welcher Mitarbeiter war für eine konkrete Abschlussarbeit zuständig?
- Welche Abschlussarbeiten wurden zu einem konkreten Projekt geschrieben?
- Welche Note hat ein bestimmter Student zu welcher Abschlussarbeit erzielt?
- Welche Studenten sind von einer Abschlussarbeit zurückgetreten und aus welchem Grund (kann auch "ohne Angabe von Gründen" sein)?
- ... 

Zu Abschlussarbeiten liegt bereits ein Datenbankschema vor, auf dem Sie aufbauen sollen.


### Fachliche Anforderungen : Klausuren
Für jedes vom Lehrstuhl betreute Modul wird in jedem Semester eine Klausur gestellt.
Eine Klausur ist immer einem Modul zugeordnet. Ein Modul ist durch eine fünfstellige Ziffer identifiziert und hat einen textuellen Bezeichner (der auch eindeutig sein sollte).
Jedem Modul ist ein wissenschaftlicher Mitarbeiter als Assistent des verantwortlich Lehrenden zugeordnet. Der verantwortlich Lehrende ist in der Regel der Lehrstuhlinhaber oder ein Postdoctoral Researcher (Postdoc). 
Eine Klausur wird von mehreren Studenten absolviert.
Studierende, die die Klausur geschrieben haben, erhalten ein Ergebnis, das aus der erreichten Gesamtpunktzahl und der Note besteht.


Das Lehrstuhlinformationssystem soll den Mitarbeitern des Lehrstuhls _zumindest_ folgende _Auswertungsmöglichkeiten_ bieten:

- Welche Klausuren hat ein bestimmter Student in welchem Semester geschrieben?
- Welche Noten hat er dabei erzielt?
- Welche Durchschnittsnote wurde für eine bestimmte Klausur vergeben?
- Wie sind die Noten einer Klausur verteilt?
- Wie viele Studierende haben an einer Klausur teilgenommen?
- ... 

## Wichtig!

> Die skizzierten fachlichen Anforderungen sind durch Sie zu reflektieren und um Domänenwissen und Kontextwissen aus der prospektiven Anwendungsdomäne (zu der u.a. die Sphären und Diskurswelten Universität, Fakultät, Lehrstuhl, Professur zählen) zu ergänzen. 

> Antizipieren Sie bei Ihrem Entwurf auch denkbare und möglicherweise erwartbare zukünftige Änderungen! So ist es in einem neuen Studiengang an der Fakultät bereits möglich, zwei Seminare zu belegen und ggf. wird dies in Kürze sogar verpflichtend sein. Überlegen Sie sorgfältig, welche Integritätsbedingungen einzuhalten sind: Offensichtlich ist es nicht zulässig, dass ein Student an einem Seminar, das er bereits erfolgreich absolviert hat, erneut teilnimmt (wie lässt sich dies programmatisch ausschließen?).

> Es bestehen vielfältige Möglichkeiten, die sich aus diesen fachlichen Anforderungen ergebenden funktionalen Anforderungen zu erweitern, z.B. könnten zu einem "abstrakten" Seminar (kritische) Kommentare der Mitarbeiter verwaltet werden, damit auch zu einem späteren Zeitpunkt noch kritische Punkte adressiert werden können (ein Mitarbeiter könnte bspw. anmerken, dass ein "abstraktes" Seminar die Verfügbarkeit von proprietärer Software voraussetzt, die nicht ohne erhebliche Geldmittel verfügbar ist). Nutzen Sie diese Möglichkeiten, um in Ihrem Team das Lehrstuhlinformationssystem weiterzudenken und absehbare zukünftige Anforderungen zu berücksichtigen. Sehen Sie diese fachlichen Anforderungen als einen Ausgangspunkt für Ihre eigenen Überlegungen an.

> Ein Beispiel für eine Weiterentwicklung besteht darin, das Alumni-Management am Lehrstuhl dadurch zu unterstützen, dass (zunächst sehr simple) Auswertungen pro Semester möglich sind, die zeigen, welche und wie viele Studenten in einem Semester an einem Seminar teilgenommen, eine Klausur und/oder eine Abschlussarbeit geschrieben haben. 

Ihre Betreuerin/Ihr Betreuer fungiert als prospektiver Anwender ("Kunden") des Lehrstuhlinformationssystems und beantwortet Ihre Fragen und gibt Feedback.


## Einstieg in die begriffliche, methodische, theoretische und praktische Fundierung

- https://en.wikipedia.org/wiki/Use_case:

> "In 1992 he co-authored the book Object-Oriented Software Engineering - A Use Case Driven Approach,[4] which laid the foundation of the OOSE system engineering method and helped to popularize use cases for capturing functional requirements, especially in software development. [...] Since then, many authors have contributed to the development of the technique, notably: Larry Constantine developed in 1995, in the context of usage-centered design, so called "essential use-cases" that aim to describe user intents rather than sequences of actions or scenarios which might constrain or bias the design of user interface;[8] Alistair Cockburn published in 2000 a goal-oriented use case practice based on text narratives and tabular specifications;[9] Kurt Bittner and Ian Spence developed in 2002 advanced practices for analyzing functional requirements with use cases;[10] Dean Leffingwell and Don Widrig proposed to apply use cases to change management and stakeholder communication activities;[11] Gunnar Overgaard proposed in 2004 to extend the principles of design patterns to use cases" (https://en.wikipedia.org/wiki/Use_case, Zugriff am 14.08.2023)


- https://en.wikipedia.org/wiki/User_story:

> "In software development and product management, a user story is an informal, natural language description of features of a software system. They are written from the perspective of an end user or user of a system, and may be recorded on index cards, Post-it notes, or digitally in project management software.[1] Depending on the project, user stories may be written by different stakeholders like client, user, manager, or development team. User stories are a type of boundary object. They facilitate sensemaking and communication; and may help software teams document their understanding of the system and its context." (https://en.wikipedia.org/wiki/User_story, Zugriff am 14.08.2023)

- https://en.wikipedia.org/wiki/Pair_programming :

> "Remote pair programming, also known as virtual pair programming or distributed pair programming, is pair programming in which the two programmers are in different locations,[12] working via a collaborative real-time editor, shared desktop, or a remote pair programming IDE plugin."


- https://en.wikipedia.org/wiki/Domain-driven_design :

> "Domain-driven design (DDD) is a major software design approach,[1] focusing on modeling software to match a domain according to input from that domain's experts"

> "Command Query Responsibility Segregation (CQRS) is an architectural pattern for separating reading data (a 'query') from writing to data (a 'command'). CQRS derives from Command and Query Separation (CQS), coined by Bertrand Meyer."



- https://en.wikipedia.org/wiki/Test-driven_development :

> "Test-driven development (TDD) is a software development process relying on software requirements being converted to test cases before software is fully developed, and tracking all software development by repeatedly testing the software against all test cases. This is as opposed to software being developed first and test cases created later."


