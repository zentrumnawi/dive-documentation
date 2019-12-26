Das *QuizAnswer*-Model definiert eine Antwortmöglichkeit bezogen auf eine Frage im Quiz der App.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| id | AutoField(primary_key=True, editable=False, unique=True) | Antwortkennung |
| question | ForeignKey(QuizQuestion, on_delete=models.CASCADE, related_name="answers", related_query_name="answer", db_Index=False) | Fragekennung, auf die sich die Antwort bezieht. | 
| text | CharField(max_length=200) | Antworttext |
| correct | BooleanField() | Antwortgültigkeit |
| feedback_correct | CharField(max_length=400, default="", blank=True) | Rückmeldung für eine ausgewählte richtige Antwort | 
| feedback_incorrect | CharField(max_length=400, default="", blank=True) | Rückmeldung für eine ausgewählte falsche Antwort |

Das Feld `id` enthält einen eindeutigen Integer als Antwortkennung und das Feld `question` speichert die dazugehörige Fragekennung aus dem QuizQuestion-Model von der Frage, auf die sich die Antwort bezieht. Das Feld `text` darf nicht leer sein, damit keine inhaltslose Antwort erstellt werden kann und im Feld `correct` muss vermerkt werden, ob es sich um eine richtige oder falsche Antwort handelt. Die Felder `feedback_correct` und `feedback_incorrect` sind optional und können einzeln für sich leer sein.
