Das *Slideshow*-Model definiert eine Serie vor- und zurückschaltbarer Seiten, die dem Anwender schrittweise
einen systematischen Prozess vermitteln sollen.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| title | CharField(max_length=100) | Serientitel |
| img | ImageField(upload_to="slideshow/", null=True, blank=True) | Bild |
| img_alt | CharField(max_length=200, default="", blank=True) | Alternative Textbeschreibung des Bildes |

Das Feld `title` speichert den Serientitel und muss angegeben werden. Optional kann einem Objekt auch ein Bild
zugewiesen werden, das beispielsweise für eine Kachelansicht von mehreren Slideshow-Objekten verwendet werden
kann. Im Feld `img` wird beim Hochladen des Bildes der Verweis auf das Bild in Form eines relativen
Verzeichnispfades mit „slideshow/“ als Unterverzeichnis als String gespeichert. Im Feld `img_alt` muss dann
zusätzlich angegeben werden, was im Bild zum Ausdruck kommt.

Die Seiten, aus denen sich die Serie zusammensetzt, sind im SlideshowPage-Model definiert. Dort ist auch
vorgegeben, dass bevor ein Slideshow-Objekt gelöscht werden kann, erst alle damit in Beziehung stehenden
Seiten gelöscht werden müssen.

Da kein Feld im Model als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung für ein Objekt enthält.
