Das *SlideshowPage*-Model definiert eine Serienseite für das Slideshow-Model.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| position | PositiveSmallIntegerField() | Seitenposition |
| title | CharField(max_length=100) | Seitentitel |
| text | TextField()| Seitentext |
| images | ForeignKey(SlideshowImage, on_delete=models.CASCADE, related_name="images") | Kennungen der Bilder, die in der Seite angezeigt werden. |

Im Feld `position` muss die Position eingetragen werden, an der die Seite in einer vor- und züruckschaltbaren
Serie des Slideshow-Models angezeigt werden soll. Die Felder `title` und `text` dürfen nicht leer sein, damit
keine inhaltslosen Seiten in der Serie vorkommen. Im Feld `images` werden die Primärschlüssel der Bilder aus
dem SlideshowImage-Model gespeichert, die in der Seite verwendet werden.

Da kein Feld als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung enthält.
