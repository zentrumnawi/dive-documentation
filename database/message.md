Das *Message*-Model definiert eine Nachricht, die dem Anwender beim Benutzen der App angezeigt werden kann. Über sie lässt
sich beispielsweise auf neu implementierte Inhalte oder Funktionen aufmerksam machen, wobei der Nachrichteninhalt ein Text,
ein Bild oder beides sein kann. 

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| type | CharField(max_length=2, choices=MTYPE_CHOICES) | Nachrichtentyp |
| title | CharField(max_length=100, unique_for_date="valid_from") | Nachrichtentitel |
| text | TextField(blank=True, default="") | Nachrichtentext |
| img | ImageField(upload_to="messages/, null=True, blank=True) | Verweis auf ein Bild |
| img_alt | CharField(max_length=200, blank=True, default="") | Alternative Textbeschreibung des Bildes |
| valid_from | DateField(default=date.today) | Anfangsdatum, ab wann die Nachricht angezeigt wird. |
| valid_to | DateField(default=date.today) | Enddatum, bis wann die Nachricht angezeigt wird. |

Im Feld `type` wird der Nachrichtentyp mittels der Auswahlmöglichkeiten von `MTYPE_CHOICES` bestimmt:
* A:
* B:

Im Feld `title` muss unbedingt ein Nachrichtentitel angegeben werden, wobei zu einem bestimmten Anzeigeanfangsdatum keine zwei
oder mehr Nachrichten mit demselben Titel erstellt werden können. Von den Feldern `text` und `img` muss mindestens eines einen
nichtleeren Wert enthalten, um sicherzustellen, dass keine inhaltslose Nachricht erstellt wird. Das Feld `img` speichert einen
Verweis auf ein Bild in Form eines relativen Verzeichnispfades als String, das aber auch erlaubt, dass ein Bild hochgeladen
werden kann, das dann im `messages`-Verzeichnis gespeichert wird. Wird dem Feld ein nichtleerer Wert zugewiesen, so darf das
Feld `img_alt` auch nicht leer sein. Für die Felder `valid_from` und `valid_to` gelten noch die weiteren Bedingungen, dass die
Anzeige der Nachricht nicht vor ihrem Erstellungszeitpunkt anfangen und nicht vor ihrem Anzeigeanfangszeitpunkt enden darf.

Da kein Feld als Primärschlüssel ausgewiesen ist, fügt Django automatisch zusätzlich ein Feld hinzu, das einen eindeutigen
Integer als Kennung enthält.
