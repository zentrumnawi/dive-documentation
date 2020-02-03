Das *Slideshow*-Model definiert eine Serie vor- und zurückschaltbarer Seiten, die dem Anwender schrittweise
einen systematischen Prozess vermitteln sollen.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| title | CharField(max_length=100, primary_key=True) | Serientitel |

Das einzige Feld `title`, das den Serientitel speichert, ist als Primärschlüssel ausgewiesen und muss deshalb
angegeben werden und einzigartig sein. Die Seiten, aus denen sich die Serie zusammensetzt, sind im
SlideshowPage-Model definiert. Dort ist auch vorgegeben, dass bevor ein Slideshow-Objekt gelöscht werden kann,
erst alle damit in Beziehung stehenden Seiten gelöscht werden müssen.
