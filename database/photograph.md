Das *Photograph*-Model definiert eine Lichtbildaufnahme.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| img | JPEGField(upload_to="photograph/", width_field="img_original_width", height_field="img_original_height", variations={"large": (1200, 800), "medium": (900, 600), "small": (600, 400), "thumbnail": (100, 100, True),}, db_index=True, delete_orphans=True,) | Lichtbild mit Bildgrößenvariationen |
| img_original_width | PositiveSmallIntegerField(editable=False) | Bildbreite in Pixel |
| img_original_height | PositiveSmallIntegerField(editable=False) | Bildhöhe in Pixel |
| img_original_scale | FloatField(verbose_name="scale", null=True, blank=True, help_text="Längenwert (in Meter) pro Pixel",) | Maßstab |
| img_alt | CharField(max_length=200) | Alternative Textbeschreibung des Bildes |
| description | TextField(default="", blank=True, verbose_name="description (Markdown)") | Beschreibungstext zum Bild |
| date | DateField(null=True, blank=True, help_text="Datum der Lichtbildaufnahme") | Datum der Lichtbildaufnahme |
| author | CharField(max_length=100, default="", blank=True) | Fotograf |
| license | CharField(max_length=100, default="", blank=True) | Lizenz |
