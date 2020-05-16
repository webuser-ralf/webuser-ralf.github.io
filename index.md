---
title: Startseite
---

# Hosting frei Haus
## Websites mit und ohne eigener Domain auf GitHub hosten
**GitHub Pages c't 11/2020 S. 162**


> Man braucht kein dediziertes Webhosting, um eine kleine Homepage zu betreiben. Ein GitHub-Account reicht für den Anfang aus. Eine mit GitHub Pages erstellte Website lässt sich sogar über eine eigene Domain erreichen.
Von Merlin Schumacher

Hosting-Angebote für die eigene Website gibt es wie Sand am Meer. Hat man keine „Berührungsängste“ mit GitHub und weder dynamische noch besonders große Inhalte anzubieten, findet man in GitHub Pages einen flexiblen Webhoster mit 100 GByte Traffic und bis zu 1 GByte Speicherplatz. Und um Dinge wie Updates oder Sicherheitseinstellungen muss man sich auch nicht mehr selbst kümmern. Wer eine eigene Domain verbinden will, kann das mit den passenden DNS-Eintrag erledigen. Dann liefert GitHub die eigene Website nicht nur über beispiel.github.io aus.

Ein paar Haken hat die Sache aber dennoch: Zum einen kann man nur Dateien mit maximal 100 MByte hochladen. Wer also etwa ein größeres Video einbinden will, ist mit YouTube besser bedient. Soll die Website von nicht-technikaffinen Menschen betreut werden, stellt man diese vor eine große Aufgabe, denn GitHub bietet keinen hübschen WYSIWYG-­Editor, sondern nur einen simplen Texteditor mit einer einfachen Vorschaufunktion für Markdown und HTML-Dateien. Immerhin kann man jede noch so verhunzte Änderung durch die Versionskontrolle wieder rückgängig machen. Wer den kostenlosen Tarif von GitHub nutzt, muss sein Repository für die Website öffentlich machen. Das ist nur dann ein Problem, wenn man Inhalte anbieten will, die nicht für die Öffentlichkeit bestimmt sind. Vermutlich ist GitHub dann aber eh die falsche Wahl.

Wenn Sie nur eine bereits bestehende Seite umziehen wollen, können Sie die Dateien auch einfach in ein Repository laden und GitHub als reinen Hoster nutzen. Pages kann jedoch mehr als nur Websites ausliefern.

Die technische Grundlage von GitHub Pages ist Jekyll, ein Generator für statische Websites. Bei jeder Änderung im Repository startet GitHub eine Jekyll-Instanz, die die gesamten Daten verarbeitet und daraus statische Inhalte erzeugt. Dabei verbindet Jekyll verschiedene Dateien zu kompletten HTML-Dateien.

Man schreibt also einfach eine neue Markdown-Datei und Jekyll wandelt deren Inhalt in eine fertige Website. Dafür nimmt es ein festgelegtes Basislayout zur Hand, indem die Positionen verschiedener Elemente und des Seiteninhalts durch Variablen definiert sind. Diese werden dann von Jekyll befüllt und das Ergebnis in eine HTML-Datei gegossen.

### Einrichtung

Jeder, der einen GitHub-Account besitzt, kann sich eine eigene GitHub-Pages-Seite unter meinbenutzername.github.io erstellen. Dafür reicht es, ein neues Repository mit dem Namen meinbenutzername.github.io anzulegen. Für den Anfang erzeugen Sie darin eine Datei namens index.md und befüllen Sie mit einem beliebigen Text, wie etwa „Hallo, Welt!“. Anschließend wechseln Sie über Settings in die Einstellungen des Repositorys. Scrollen Sie dort bis zum Abschnitt „GitHub Pages“. Dort sehen Sie zwei Optionen. Die erste legt fest, aus welchem Zweig des Repositorys GitHub die Seite bauen soll. Wählen Sie hier „master branch“ aus. Sie können auch den Branch „gh-pages“ für die Website anlegen und diesen dann auswählen. Das bietet sich an, wenn Sie im „master“-Branch ein Projekt lagern, dessen Dokumentation Sie unabhängig pflegen wollen. Alternativ können Sie die Website-Dateien auch im Unterverzeichnis /docs des „master“-Zweigs hinterlegen. Dann wählen Sie „master branch /docs folder“ als Quelle.

Darunter bietet GitHub noch die Auswahl eines Themes für die Seiten an. Klicken Sie dazu auf „Change theme“ und wählen Sie ein Design, das Ihnen gefällt. Früher war es so, dass man auf die von GitHub angebotenen Designs festgelegt war. Das ist nicht mehr so. Sie können Ihre Seite mittels CSS völlig frei gestalten. Die Auswahl eines Themes macht aber den ersten Schritt etwas ansehnlicher.

Nach der Auswahl einer Quelle für die Seiten werden zwei weitere Optionen sichtbar: einmal die Option „Custom domain“ und eine Checkbox mit dem Titel „Enforce HTTPS“. Das Feld „Custom domain“ nimmt den Namen entgegen, über den Ihre Seite erreichbar sein soll. Tragen Sie hier den Namen ein und klicken Sie auf Save. Mehr dazu lesen Sie im Abschnitt „Domainnamen“.

Der Haken bei „Enforce HTTPS“ sorgt dafür, dass die Seite immer per HTTPS ausgeliefert wird, unverschlüsselte Anfragen werden auf HTTPS umgeleitet. Der Haken dort ist obligatorisch, denn HTTPS kostet nichts und lässt vor allem die hässlichen Warnsymbole im Browser der Besucher verschwinden. Das Zertifikat für Ihre Adresse bestellt GitHub übrigens bei Let’s Encrypt.

Besuchen Sie nun die Seite mein­benutzername.github.io. Dort sollte Sie das eben eingetippte „Hallo, Welt!“ im eben gewählten Design begrüßen.

Wenn Sie danach einen Blick in das Repository werfen, finden Sie dort eine neue Datei namens _config.yml. Sie ist die Konfigurationsdatei für Jekyll und enthält den Namen des zu verwendenden Themes. Haben Sie bereits eine Domain hinterlegt, finden Sie dort auch die Datei CNAME, die den hinterlegten Domainnamen enthält.

### Domainnamen

Soll Ihre neue Seite auch über eine eigene Domain erreichbar sein, müssen Sie lediglich die DNS-Einträge des Domaineintrags anpassen. Falls Sie keine Domain verbinden wollen, überspringen Sie diesen Abschnitt und lesen Sie bei „Jekyll in Kürze“ weiter.

Die notwendigen DNS-Änderungen können Sie im Konfigurationsbackend Ihres Hosters oder Domainregistrars erledigen. Sollte das nicht möglich sein, müssen Sie die Domain umziehen oder, wenn Sie zumindest eigene DNS-Server für die Domain festlegen können, die DNS-Verwaltung von einem externen DNS-Dienst wie Cloudflare übernehmen lassen.

Als Domains können Sie Subdomains wie `www.beispiel.de` oder Hauptdomains wie beispiel.de eintragen. Bei einer Subdomain müssen Sie lediglich einen ­CNAME-Eintrag anlegen, der auf meinbenutzername.github.io verweist. Alle anderen A- oder CNAME-Einträge für die Subdomain müssen Sie löschen.





