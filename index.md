# Hosting frei Haus
## Websites mit und ohne eigener Domain auf GitHub hosten

> Man braucht kein dediziertes Webhosting, um eine kleine Homepage zu betreiben. Ein GitHub-Account reicht für den Anfang aus. Eine mit GitHub Pages erstellte Website lässt sich sogar über eine eigene Domain erreichen.

 Hosting-Angebote für die eigene Website gibt es wie Sand am Meer. Hat man keine „Berührungsängste“ mit GitHub und weder dynamische noch besonders große Inhalte anzubieten, findet man in GitHub Pages einen flexiblen Webhoster mit 100 GByte Traffic und bis zu 1 GByte Speicherplatz. Und um Dinge wie Updates oder Sicherheitseinstellungen muss man sich auch nicht mehr selbst kümmern. Wer eine eigene Domain verbinden will, kann das mit den passenden DNS-Eintrag erledigen. Dann liefert GitHub die eigene Website nicht nur über beispiel.github.io aus.

Ein paar Haken hat die Sache aber dennoch: Zum einen kann man nur Dateien mit maximal 100 MByte hochladen. Wer also etwa ein größeres Video einbinden will, ist mit YouTube besser bedient. Soll die Website von nicht-technikaffinen Menschen betreut werden, stellt man diese vor eine große Aufgabe, denn GitHub bietet keinen hübschen WYSIWYG-­Editor, sondern nur einen simplen Texteditor mit einer einfachen Vorschaufunktion für Markdown und HTML-Dateien. Immerhin kann man jede noch so verhunzte Änderung durch die Versionskontrolle wieder rückgängig machen. Wer den kostenlosen Tarif von GitHub nutzt, muss sein Repository für die Website öffentlich machen. Das ist nur dann ein Problem, wenn man Inhalte anbieten will, die nicht für die Öffentlichkeit bestimmt sind. Vermutlich ist GitHub dann aber eh die falsche Wahl.

Wenn Sie nur eine bereits bestehende Seite umziehen wollen, können Sie die Dateien auch einfach in ein Repository laden und GitHub als reinen Hoster nutzen. Pages kann jedoch mehr als nur Websites ausliefern.

Die technische Grundlage von GitHub Pages ist Jekyll, ein Generator für statische Websites. Bei jeder Änderung im Repository startet GitHub eine Jekyll-Instanz, die die gesamten Daten verarbeitet und daraus statische Inhalte erzeugt. Dabei verbindet Jekyll verschiedene Dateien zu kompletten HTML-Dateien. 


