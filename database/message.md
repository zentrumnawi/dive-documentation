Das *Message*-Model definiert eine Nachricht, die dem Anwender beim Benutzen der App angezeigt werden kann.
Über sie lässt sich beispielsweise auf neu implementierte Inhalte oder Funktionen aufmerksam machen, wobei der Nachrichteninhalt ein Text, ein Bild oder beides sein kann. 

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| type | CharField(max_length=2, choices=MTYPE_CHOICES) | Nachrichtentyp |
| title | CharField(max_length=100) | Nachrichtentitel |
| text | TextField(default="", blank=True) | Nachrichtentext |
| img | ImageField(upload_to="message/", null=True, blank=True) | Bild |
| img_alt | CharField(max_length=200, default="", blank=True, validators=[validate_img_is_not_empty]) | Alternative Textbeschreibung des Bildes |
| valid_from | DateField(default=date.today, validators=[validate_date_is_not_past]) | Anzeigeanfangsdatum |
| valid_to | DateField(default=date.today, validators=[validate_date_is_not_before_valid_from_date]) | Anzeigeenddatum |

Im Feld `type` wird der Nachrichtentyp mittels der Auswahlmöglichkeiten von `MTYPE_CHOICES` festgelegt:
* _Changelog_: Hinweis auf eine neue App-Version und/oder Funktionalität
* _Series_: Folge von regelmäßigen, gleichlang angezeigten Nachrichten
* _Notice_: Allgemeiner Hinweis

Im Feld `title` muss ein Nachrichtentitel angegeben werden. Ein Nachrichtentext wird im Feld `text`
gespeichert und wenn ein Bild verwendet werden soll, so wird im Feld `img` beim Hochladen des Bildes der
Verweis auf das Bild in Form eines relativen Verzeichnispfades mit „messages/“ als Unterverzeichnis als String
gespeichert. Falls ein Bild verwendet wird, muss zusätzlich im Feld `img_alt` angegeben werden, was im Bild
zum Ausdruck kommt. In den Feldern `valid_from` und `valid_to` werden das Anfangs- und Enddatum der
Anzeigedauer der Nachricht gespeichert. Dabei wird geprüft, dass die Anzeigedauer nicht vor dem
Erstellungsdatum anfängt und nicht vor dem Anfangsdatum endet.  

Da kein Feld im Model als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung für ein Objekt enthält.
