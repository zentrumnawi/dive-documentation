Das *SlideshowImage*-Model definiert ein Bild, das in einer Serienseite des SlideshowPage-Models verwendet
werden kann.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| position | PositiveSmallIntegerField() | Bildposition |
| title | CharField(max_length=100) | Bildtitel |
| img | ImageField(upload_to="slideshow/images/") | Bild |
| img_alt | CharField(max_length=200) | Alternative Textbeschreibung des Bildes |
| caption | TextField(blank=True, default="") | Text zum Bild |
