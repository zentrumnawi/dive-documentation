Das *TreeNode*-Model definiert einen Knoten in einer Baumstruktur.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| parent | TreeForeignKey('self', on_delete=models.CASCADE, related_name='leaf_nodes', null=True, blank=True) | Vorknotenkennung |
| is_top_level | BooleanField(default=False) | Wurzel |
| name | CharField(max_length=200, unique=True) | Knotenname |
| info | TextField(default="", blank=True) | Knoteninformation |

Das Feld `parent` speichert die Kennung des übergeordneten Knotens, wobei im Feld `is_top_level` vermerkt wird,
 ob es sich beim Knoten um die Wurzel der Baumstruktur handelt. Einem Knoten muss im Feld `name` ein eindeutiger 
 Name zugewiesen werden. Das Feld `info` ist hingegen optional und kann auch leer gelassen werden.
