# Quizfrage Model

Das Model definiert eine Frage im Quiz der Web-App zum Selbsttest des Lernerfolgs des Anwenders.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| qtext | CharField(max_length=500, null=True, verbose_name=_("question text")) | Speichert den Fragetext |
| qtype | CharField(max_length=2, choices=QTYPE_CHOICES, null=True, verbose_name=_("question type")) |  |
| tags | ArrayField(base_field=models.CharField(max_length=200), null=True, help_text="If you want to add more than one tag, seperate them with commas.") |  |
| difficulty | IntegerField(choices=DIFFICULTY_CHOICES, null=True, verbose_name=_("difficulty")) |  |
