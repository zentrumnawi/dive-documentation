# Quizfrage Model

Das Model definiert eine Frage im Quiz der Web-App zum Selbsttest des Lernerfolgs des Anwenders.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| qtext | TextField(max_length=500) | Speichert den Fragetext |
| qtype | CharField(max_length=2, choices=QTYPE_CHOICES) |  |
| tags | ArrayField(base_field=models.CharField(max_length=200), blank=True, default="",help_text="If you want to add more than one tag, seperate them with commas.") |  |
| difficulty | IntegerField(choices=DIFFICULTY_CHOICES) |  |



# Anmerkungen

Die Auswahlmöglichkeiten `QTYPE_CHOICES` sind:

* Single Choice - Eine der zugeordneten Antworten ist korrekt.
* Multiple Choice - Mehrere der zugeordneten Antorten ist korrekt.
* Drag and Drop - Die zugeordneten Antworten müssen bestimmten Eigenschaften zu geordnet werden.
* Ranking - Die zugeordneten Antowrten müssen in eine gewisse Reihenfolge gebracht werden.
* Hotspot - Die zugeordnete Antwort muss auf einem Bild markiert werden.

Die Auswahlmöglichkeiten `DIFFICULTY_CHOICES`sind:

* 1 - Neuling-Frage
* 2 - Einsteiger-Frage
* 3 - Fortgeschrittenen-Frage
* 4 - Erfahrenen-Frage
* 5 - Experten-Frage
