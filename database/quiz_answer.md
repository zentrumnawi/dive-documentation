# Quizantwort Model

Das Model definiert eine Antwort auf eine Frage im Quiz der Web-App.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| atext | CharField(max_length=500, null=True, verbose_name=_("answer text")) |  |
| correct | BooleanField(verbose_name=_("correct"), help_text="Nothing yet.") |  |
| feedback_correct | CharField(max_length=500, default="", blank=True, verbose_name=_("feedback if answered correctly")) |  | 
| feedback_incorrect | CharField(max_length=500, default="", blank=True, verbose_name=_("feedback if answered incorrectly")) |  |
| question | ForeignKey(QuizQuestion, null=True, verbose_name=_("question"), related_name="answers", on_delete=models.CASCADE) |  | 
