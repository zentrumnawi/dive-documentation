Das *SlideshowImage*-Model definiert ein Bild, das in einer Seite des SlideshowPage-Models verwendet werden
kann.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| page | ForeignKey(SlideshowPage, on_delete=models.CASCADE, related_name="images", related_query_name="image", db_index=False) | Kennung der Seite |
| position | PositiveSmallIntegerField(default=1, validators=[validate_position_occupied]) | Bildposition |
| title | CharField(max_length=100) | Bildtitel |
| img | ImageField(upload_to="slideshow/") | Bild |
| img_alt | CharField(max_length=200) | Alternative Textbeschreibung des Bildes |
| caption | TextField(default="", blank=True) | Text zum Bild |

Das Feld `page` speichert den Primärschlüssel des SlideshowPage-Objekts, in dem das Bild angezeigt werden
soll. Hinsichtlich der Verwendung mehrerer Bilder, wird die Position des Bildes im Feld `position`
eingetragen, wobei als Standardwert „1“ voreingestellt ist und geprüft wird, ob die angegebene Position
bereits belegt ist. Im Feld `img` wird beim Hochladen des Bildes der Verweis auf das Bild in Form eines
relativen Verzeichnispfades mit „slideshow/“ als Unterverzeichnis als String gespeichert. Im Feld `img_alt`
muss zusätzlich angegeben werden, was im Bild zum Ausdruck kommt und das Feld `caption` dient für einen
ergänzenden Text zum Bild. 

Da kein Feld im Model als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung für ein Objekt enthält.
