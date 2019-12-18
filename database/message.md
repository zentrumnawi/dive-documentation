Das *Message* Model definiert eine Nachricht, die dem Anwender beim Benutzen der App angezeigt werden kann. Sie dient beispielsweise dazu, auf neu implementierte Inhalte oder Funktionen aufmerksam zu machen. Neben einem Text ist es auch möglich ein Bild in der Nachricht anzeigen zu lassen.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| id | UUIDField(primary_key=True, default=uuid.uuid4, editable=False, unique=True) | UUID einer Nachricht |
| valid_from | DateField(default=date.today) | Anzeigeanfangsdatum der Nachricht |
| valid_to | DateField(default=date.today) | Anzeigeenddatum der Nachricht |
| title | CharField(max_length=100, blank=True, default="", unique_for_date="valid_from") | Nachrichtentitel |
| mtext | TextField(max_length=500, blank=True, default="") | Nachrichtentext |
| mtype | CharField(max_length=2, choices=MTYPE_CHOICES) | Nachrichtentyp |
| img_url | URLField(blank=True, default="") | URL als Bildquelle |
