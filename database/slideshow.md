Das *Slideshow*-Model definiert eine Serie vor- und zurückschaltbarer Seiten, die dem Anwender schrittweise
einen systematischen Prozess vermitteln sollen.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| title | CharField(max_length=100, unique=True) | Serientitel |
| pages | ForeignKey(SlideshowPage, on_delete=models.CASCADE, related_name="pages") | Kennungen der Serienseiten |

Das Feld `title` darf nicht leer sein und ein Serientitel darf nicht mehrmals vergeben werden. Im Feld `pages`
werden die Primärschlüssel der Seiten aus dem SlideshowPages-Model gespeichert, aus denen sich die Serie
zusammensetzt.

Da kein Feld als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung enthält.
