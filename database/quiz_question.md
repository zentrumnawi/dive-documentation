Das *QuizQuestion* Model definiert eine Frage im Quiz der App zum Selbsttest des Lernerfolgs des Anwenders.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| id | AutoField(primary_key=True, editable=False, unique=True) | Fragekennung |
| type | CharField(max_length=2, choices=QTYPE_CHOICES) | Fragetyp |
| text | TextField() | Fragetext |
| tags | ArrayField(base_field=models.CharField(max_length=200), blank=True, default="", help_text="If you want to add more than one tag, seperate them with commas.") | ??? |
| difficulty | PositiveSmallIntegerField(choices=QDIFFICULTY_CHOICES) | Schwierigkeitsgrad der Frage |

Das Feld `id` enthält eine positive Ganzzahl als eindeutige Fragekennung und im Feld `type` wird der Fragetyp mittels der Auswahlmöglichkeiten von QTYPE_CHOICES bestimmt:
* Single Choice: Nur eine gültige Antwort aus mehreren vorgegebenen Antwortmöglichkeiten
* Multiple Choice: Eine oder mehrere gültige Antworten aus mehreren vorgegebenen Antwortmöglichkeiten
* Drag and Drop: Merkmalszuordung zu vorgegebenen Antworten
* Ranking: Reihenfolgenanordnung von vorgegebenen Antworten
* Hotspot: Markierung der vorgegebenen Antwort in einem Bild

Das Feld `text` darf nicht leer sein, damit keine inhaltslose Frage angezeigt wird und im Feld `difficulty` muss der Frage einer von 5 Schwierigkeitsgraden zugeordnet werden, die mittels den Auswahlmöglichkeiten von `QDIFFICULTY_CHOICES` vorbestimmt sind:
* 1: Neuling
* 2: Einsteiger
* 3: Fortgeschrittener
* 4: Erfahrener
* 5: Experte
