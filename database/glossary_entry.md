Das *GlossaryEntry*-Model definiert einen Eintrag in das Glossar der App, der neben einem erklärenden Text
auch Links auf weitere Einträge enthalten kann.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| term | CharField(max_length=100) | Begriff |
| text | TextField(verbose_name="text (Markdown)") | Erklärungstext zum Begriff |
| link_children | ManyToManyField("self", blank=True, related_name="link_parents", symmetrical=False, db_Index=False) | Kennungen von anderen Einträgen |

In den Feldern `term` und `text` werden ein Begriff und der dazugehörige Erklärungstext gespeichert, wobei der
Text in Markdown verfasst sein kann. Um sicherzustellen, dass kein inhaltsloser Eintrag erstellt wird, dürfen
beide Felder nicht leer sein.  Das Feld `link_children` speichert die Primärschlüssel von anderen Einträgen,
zu denen aus einem Objekt heraus verwiesen wird. 

Da kein Feld im Model als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung für ein Objekt enthält.
