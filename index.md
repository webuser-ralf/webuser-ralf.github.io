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

Sollten Sie statt einer Subdomain eine Hauptdomain verwenden wollen, müssen Sie dazu vier A-Einträge anlegen, die auf folgende IP-Adressen zeigen:
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
Anschließend erreichen Sie Ihre Seite auf beispiel.de. Eventuell dauert es ein paar Minuten, bis die Änderung auf Ihrem Rechner sichtbar wird. Je nachdem, wie lange er oder Ihr Router den DNS-Eintrag zwischenspeichert.

Haben Sie für Ihre Domain einen Eintrag für die DNS Certification Authority Authorization hinterlegt, der ausweist, welche Anbieter für Ihre Domains TLS-­Zertifikate ausstellen dürfen, müssen Sie diesen anpassen. Hier muss, falls das nicht schon der Fall ist, Let’s Encrypt als erlaubter Anbieter eingetragen sein. Ein Beispiel für einen passenden Eintrag mit der Kontaktadresse `mail@beispiel.de` sieht wie folgt aus:
```
beispiel.de. IN CAA 0 issue "letsencrypt.org"
beispiel.de. IN CAA 0 iodef "mailto:mail@beispiel.de"
```
### Jekyll in Kürze

Natürlich soll die Seite mehr als nur ein schnödes „Hallo Welt!“ in einem der Standarddesigns von GitHub sein. Ein kleiner Crashkurs im Aufbau einer Jekyll-Seite befähigt Sie, im Handumdrehen schicke Websites zu erzeugen. Ein Beispielrepository, das Sie als Basis für Ihre eigene Seite verwenden können, finden Sie über `ct.de/y2u3`. Dort finden Sie auch weiterführende Informationen zu Jekyll und GitHub-Pages.

In dem Repository finden Sie vier Ordner. In _includes landen HTML-Dateien, deren Inhalt Sie an beliebigen Stellen im Layout einbinden wollen. Das ist bei Seiten- oder Navigationsleisten sinnvoll, wie die Leiste in der Datei _nav.html illustriert. So kann man Elemente an einer zentralen Stelle bearbeiten und sie werden im gesamten Layout geändert.

Im Ordner _sass finden Sie zwei Sass-­Dateien. Auch Dateien dieser Stylesheet-­Sprache kann Jekyll verarbeiten, zusammenfügen und in eine CSS-Datei konvertieren. Damit deren Einbindung aber stattfindet, liegt in assets/css/ die Datei styles.scss. Sie enthält zwei @import-Zeilen, die die beiden Stylesheets aus dem Ordner _sass einbinden.

Nun braucht es aber einen Trick, damit Jekyll die Datei korrekt interpretiert. Am Anfang der Datei stehen zweimal drei Minuszeichen mit einer Leerzeile dazwischen. Das ist ein sogenannter Front-Matter-Block, in dem Metadaten und Variablen im YAML-Format für die Seite hinterlegt sind. Dateien mit einem solchen Abschnitt jagt Jekyll in jedem Fall durch seine interne Verarbeitung. Nur so lässt er sich überreden, die SASS-Style­sheets zusammenzufassen. Die Summe der SASS-Anweisungen als CSS ist nach der Verarbeitung über den Pfad /assets/css/styles.css zu erreichen. Man beachte die geänderte Endung. So steht sie auch in der Datei default.html als Style­sheet-Verweis.

Der Ordner _layouts enthält ein oder mehrere HTML-Dateien mit Basislayouts. Darin finden Sie den HTML-Rahmen der Seite wieder. Das Beispiel enthält lediglich das Standdardlayout default.html. Darin finden Sie eine einfache HTML5-Seite mit drei Schlüsselwörtern. Diese weisen Jekyll an, bestimmte Werte oder Inhalte einzufügen. Innerhalb des <title>-Tags liegt die Zeile {{ page.title | default: site.title }}. Sie ist der Platzhalter entweder für den Titel einer einzelnen Seite (page.title) oder der gesamten Website (site.title) . Diese Variablen werden teils automatisch bestimmt oder lassen sich im Front-Matter-Block befüllen – dazu gleich mehr. Ist kein Seitentitel gesetzt, fällt Jekyll auf die erste Überschrift im Text zurück. Die Navigationsleiste aus dem _includes-Ordner bindet {% include nav.html %} ein. Das Schlüsselwort {{ content }} etwas weiter unten bestimmt, wo die Inhalte der Markdown-Dateien im Hauptverzeichnis des Repos landen.

Neben den bereits erwähnten Dateien, CNAME und _config.yml liegen noch zwei Markdown-Dateien im Hauptverzeichnis. Die Datei index.md bestimmt den Inhalt der Startseite. Die Datei image.md zeigt die Einbindung eines Bildes. Beide Seiten sind nach der Umwandlung über index.html beziehungsweise image.html erreichbar. Dort aber eben mit dem Rahmenlayout aus der default.html.

In der index.md finden Sie nur einen einfachen Beispieltext. Ein Blick in die image.md offenbart einen Front-Matter-Block, in dem ein Titel und das Layout hinterlegt ist. Das Layout steht auf default, was redundant ist und nur als Beispiel dient, denn der Wert ist ohnehin die Vorgabe. Die Variable title bestimmt den Wert von page.title, der im <title>-Tag der Seite erscheint.

Wenn Sie eine neue Markdown-Datei erstellen, ist diese kurz darauf unter `meinbenutzername.github.io/neuedatei.html` sichtbar.

Die Datei _config.yml enthält im Beispiel keine Theme-Definition, dafür aber Optionen für den Ort und die Verarbeitung der SASS-Dateien sowie einen globalen Seitentitel. Fehlt dieser, nimmt GitHub den Namen des Repositorys.

### Mehr machen

Jekyll und damit GitHub Pages können wahnsinnig viele Dinge, weit mehr, als dieser Artikel auflisten könnte. Jekyll ist sogar so flexibel, dass man damit auch ein kleines Blog betreiben kann. Für einen tieferen Einstieg bietet sich nicht nur ein Blick in die Jekyll-Doku an, sondern auch in andere Jekyll-Projekte. Übrigens brauchen Sie keine weiteren Accounts anlegen, wenn Sie mehrere Seiten hosten möchten. Weitere GitHub-Pages-Repos erscheinen automatisch unter `meinbenutzername.github.io/namedesrepo`. Sie können diese ebenfalls so einrichten, dass sie über eigene Domains erreichbar sind.

**Beispiel und Dokumentation:** [ct.de/y2u3][1]


[1]:  https://www.heise.de/select/ct/2020/11/softlinks/y2u3?wt_mc=pred.red.ct.ct112020.162.softlink.softlink








