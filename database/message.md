Das *Message* Model definiert eine Nachricht, die dem Anwender beim Benutzen der App angezeigt werden kann. Über sie lässt sich beispielsweise auf neu implementierte Inhalte oder Funktionen aufmerksam machen, wobei der Nachrichteninhalt ein Text, ein Bild oder beides sein kann. 

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| id | UUIDField(primary_key=True, default=uuid.uuid4, editable=False, unique=True) | UUID einer Nachricht |
| mtype | CharField(max_length=2, choices=MTYPE_CHOICES) | Nachrichtentyp |
| mtitle | CharField(max_length=100, blank=True, default="", unique_for_date="valid_from") | Nachrichtentitel |
| mtext | TextField(blank=True, default="") | Nachrichtentext |
| img_url | URLField(blank=True, default="") | URL, unter der ein Bild abgerufen wird. |
| valid_from | DateField(default=date.today) | Anfangsdatum, ab wann die Nachricht angezeigt wird. |
| valid_to | DateField(default=date.today) | Enddatum, bis wann die Nachricht angezeigt wird. |

Das Feld `id` enthält eine eindeutige Nachrichtenkennung und im Feld `mtype` wird der Nachrichtentyp mittels der Auswahlmöglichkeiten von `MTYPE_CHOICES` bestimmt:
* A:
* B:

Ein Nachrichtentitel muss nicht unbedingt angegeben werden, weswegen `mtitle` auch leer sein darf. Hingegen muss mindestens eines der Felder `mtext` und `img_url` einen nichtleeren Wert enthalten, um sicherzustellen, dass keine inhaltslose Nachricht erstellt wird. Für die Felder `valid_from` und `valid_to` gelten noch die weiteren Bedingungen, dass die Anzeige der Nachricht nicht vor ihrem Erstellungsdatum anfangen und nicht vor ihrem Anzeigeanfangsdatum enden darf.
