Das *Slideshow*-Model definiert eine Serie hin- und herschaltbarer Anzeigen, die dem Anwender schrittweise
einen systematischen Prozess vermitteln sollen.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| title | CharField(max_length=100, unique=True) | Serientitel |
| pages | ForeignKey(SlideshowPage, on_delete=models.CASCADE, related_name="pages") | Anzeigeseiten der Serie |

Das Feld `title` darf nicht leer sein und ein Titel darf nicht mehrmals vergeben werden. Im Feld `pages`
werden die Primärschlüssel der Anzeigeseiten gespeichert, aus denen sich Anzeigeserie zusammensetzt.

Da kein Feld als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung enthält.
