Das *Message* Model definiert eine Nachricht, die dem Anwender beim Benutzen der App angezeigt werden kann. Über sie lässt sich beispielsweise auf neu implementierte Inhalte oder Funktionen aufmerksam machen, wobei der Nachrichteninhalt ein Text, ein Bild oder beides sein kann. 

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| id | UUIDField(primary_key=True, default=uuid.uuid4, editable=False, unique=True) | UUID einer Nachricht |
| type | CharField(max_length=2, choices=MTYPE_CHOICES) | Nachrichtentyp |
| title | CharField(max_length=100, blank=True, default="", unique_for_date="valid_from") | Nachrichtentitel |
| text | TextField(blank=True, default="") | Nachrichtentext |
| img_url | URLField(blank=True, default="") | URL, unter der ein Bild abgerufen wird. |
| img_alt | CharField(max_length=200, blank=True, default="") | Alternative Textbeschreibung des Bildes |
| valid_from | DateTimeField(default=timezone.now) | Anfangszeitpunkt, ab wann die Nachricht angezeigt wird. |
| valid_to | DateTimeField(default=timezone.now) | Endzeitpunkt, bis wann die Nachricht angezeigt wird. |

Das Feld `id` enthält eine eindeutige Nachrichtenkennung und im Feld `type` wird der Nachrichtentyp mittels der Auswahlmöglichkeiten von `MTYPE_CHOICES` bestimmt:
* A:
* B:

Ein Nachrichtentitel muss nicht unbedingt angegeben werden, weswegen `title` auch leer sein darf. Hingegen muss mindestens eines der Felder `text` und `img_url` einen nichtleeren Wert enthalten, um sicherzustellen, dass keine inhaltslose Nachricht erstellt wird. Wird dem Feld `img_url` ein nichtleerer Wert zugewiesen, so darf das Feld `img_alt` auch nicht leer sein. Für die Felder `valid_from` und `valid_to` gelten noch die weiteren Bedingungen, dass die Anzeige der Nachricht nicht vor ihrem Erstellungszeitpunkt anfangen und nicht vor ihrem Anzeigeanfangszeitpunkt enden darf.
