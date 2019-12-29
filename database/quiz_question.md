Das *QuizQuestion*-Model definiert eine Frage im Quiz der App zum Selbsttest des Lernerfolgs des Anwenders.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| type | CharField(max_length=2, choices=QTYPE_CHOICES) | Fragetyp |
| text | TextField() | Fragetext |
| tags | ArrayField(base_field=models.CharField(max_length=200), blank=True, default="", help_text="If you want to add more than one tag, seperate them with commas.") | ??? |
| difficulty | PositiveSmallIntegerField(choices=QDIFFICULTY_CHOICES) | Schwierigkeitsgrad der Frage |

Im Feld `type` wird der Fragetyp mittels der Auswahlmöglichkeiten von `QTYPE_CHOICES` bestimmt:
* _Single Choice_: Nur eine gültige Antwort aus mehreren vorgegebenen Antwortmöglichkeiten
* _Multiple Choice_: Eine oder mehrere gültige Antworten aus mehreren vorgegebenen Antwortmöglichkeiten
* _Drag and Drop_: Merkmalszuordung zu vorgegebenen Antworten
* _Ranking_: Reihenfolgenanordnung von vorgegebenen Antworten
* _Hotspot_: Markierung der vorgegebenen Antwort in einem Bild

Das Feld `text` darf nicht leer sein, damit keine inhaltslose Frage angezeigt wird und im Feld `difficulty` muss der 
Frage einer von 5 Schwierigkeitsgraden zugeordnet werden, die mittels den Auswahlmöglichkeiten von 
`QDIFFICULTY_CHOICES` vorbestimmt sind:
* _1_: Neuling
* _2_: Einsteiger
* _3_: Fortgeschrittener
* _4_: Erfahrener
* _5_: Experte
