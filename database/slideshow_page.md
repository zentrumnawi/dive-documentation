Das *SlideshowPage*-Model definiert eine Seite für das Slideshow-Model.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| show | ForeignKey(Slideshow, on_delete=models.PROTECT, related_name="pages", related_query_name="page", db_index=False) | Kennung der Slideshow |
| position | PositiveSmallIntegerField(default=1, validators=[validate_position_occupied]) | Seitenposition |
| title | CharField(max_length=100) | Seitentitel |
| text | TextField()| Seitentext |

Das Feld `show` speichert den Primärschlüssel des Slideshow-Objekts, für das die Seite als Teil einer Serie
bestimmt ist. Deren Position innerhalb der Serie wird im Feld `position` eingetragen, wobei geprüft wird, ob
die angegebene Position bereits belegt ist. Der Seiteninhalt wird in den Feldern `title` und `text`
gespeichert, die beide nicht leer sein dürfen. Bilder, die in der Seite angezeigt werden sollen, sind im
SlideshowImage-Model definiert, wo vorgegeben ist, dass beim Löschen eines SlideshowPage-Objekts alle darin
verwendeten Bilder ebenfalls gelöscht werden.

Da kein Feld im Model als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung für ein Objekt enthält.
