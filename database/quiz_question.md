Das *QuizQuestion*-Model definiert eine Frage im Quiz der App zum Selbsttest des Lernerfolgs des Anwenders,
die auch ein Bild beziehungsweise eine Grafik enthalten kann.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| type | CharField(max_length=2, choices=QTYPE_CHOICES) | Fragetyp |
| difficulty | PositiveSmallIntegerField(choices=QDIFFICULTY_CHOICES) | Schwierigkeitsgrad |
| text | TextField() | Fragetext |
| img | ImageField(upload_to="quiz/", null=True, blank=True) | Bild |
| img_alt | CharField(max_length=200, default="", blank=True, validators=[validate_img_is_not_empty]) | Alternative Textbeschreibung des Bildes |
| tags | ArrayField(base_field=models.CharField(max_length=100), default=list, blank=True, help_text="If you want to add more than one tag, seperate them with commas.") | Schlagwörter |

Im Feld `type` muss der Fragetyp mittels der Auswahlmöglichkeiten von `QTYPE_CHOICES` festgelegt werden:
* _Single Choice_: Nur eine gültige Antwort aus mehreren vorgegebenen Antwortmöglichkeiten
* _Multiple Choice_: Eine oder mehrere gültige Antworten aus mehreren vorgegebenen Antwortmöglichkeiten
* _Drag and Drop_: Merkmalszuordung zu vorgegebenen Antworten
* _Ranking_: Reihenfolgenanordnung von vorgegebenen Antworten
* _Hotspot_: Markierung der vorgegebenen Antwort in einem Bild

und im Feld `difficulty` muss der Frage mittels den Auswahlmöglichkeiten von `QDIFFICULTY_CHOICES` einer von 5
Schwierigkeitsgraden zugeordnet werden:
* _1_: Neuling
* _2_: Einsteiger
* _3_: Fortgeschrittener
* _4_: Erfahrener
* _5_: Experte

Der Fragetext wird im Feld `text` hinterlegt und darf nicht leer sein. Soll die Frage ein Bild enthalten, so
wird im Feld `img` beim Hochladen des Bildes der Verweis auf das Bild in Form eines relativen
Verzeichnispfades mit „quiz/“ als Unterverzeichnis als String gespeichert. Falls ein Bild verwendet wird, muss
zusätzlich im Feld `img_alt` angegeben werden, was im Bild zum Ausdruck kommt. Im Feld `tags` kann eine Liste
von Schlagwörtern gespeichert werden, die es ermöglichen, die Frage bestimmten Kategorien zuzuschreiben.

Da kein Feld im Model als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung für ein Objekt enthält.
