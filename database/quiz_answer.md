Das *QuizAnswer*-Model definiert eine Antwortmöglichkeit bezogen auf eine Frage des QuizQuesiton-Models.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| question | ForeignKey(QuizQuestion, on_delete=models.CASCADE, related_name="answers", related_query_name="answer") | Kennung der Frage | 
| text | CharField(max_length=200) | Antworttext |
| correct | BooleanField() | Antwortgültigkeit |
| feedback_correct | CharField(max_length=400, default="", blank=True) | Rückmeldung für eine richtige Antwortauswahl | 
| feedback_incorrect | CharField(max_length=400, default="", blank=True) | Rückmeldung für eine falsche Antwortauswahl |

Das Feld `question` speichert den Primärschlüssel des QuizQuestion-Objekts, auf das sich die Antwort beziehen
soll, wobei vorgegeben ist, dass beim Löschen des Objekts auch alle darauf bezogenen Antwortmöglichkeiten
gelöscht werden. Im Feld `text` wird der Antworttext hinterlegt, der nicht leer sein darf und im Feld
`correct` muss vermerkt werden, ob es ich um eine richtige oder falsche Antwort handelt. Als Rückmeldung
können in den Feldern `feedback_correct` und `feedback_incorrect` Kommentare hinterlegt werden, die in zwei
unterschiedlichen Fällen angezeigt werden. Im Feld `feedback_correct` wird ein Kommentar für den Fall
eingetragen, dass eine richtige Antwort ausgewählt wurde oder eine falsche Antwort nicht ausgewählt wurde und
im Feld `feedback_incorrect` für den Fall, dass eine richtige Antwort nicht ausgewählt wurde oder eine falsche
Antwort ausgewählt wurde.

Da kein Feld im Model als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung für ein Objekt enthält.
