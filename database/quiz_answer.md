# Quizantwort Model

Das Model definiert eine Antwort auf eine Frage im Quiz der Web-App.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| atext | CharField(max_length=500, default="", blank=True) |  |
| correct | BooleanField(help_text="Nothing yet.") |  |
| feedback_correct | CharField(max_length=500, default="", blank=True) |  | 
| feedback_incorrect | CharField(max_length=500, default="", blank=True) |  |
| question | ForeignKey(QuizQuestion, default="", blank=True, related_name="answers", on_delete=models.CASCADE) |  | 
