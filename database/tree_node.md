Das *TreeNode*-Model definiert einen Knoten in einer Baumstruktur.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| is_root | BooleanField(default=False) | Wurzelmarkierung |
| parent | ForeignKey("self", on_delete=models.CASCADE, null=True, blank=True, related_name="children", related_query_name="child", validators=[validate_node_is_not_root]) | Kennung des übergeordneten Knotens |
| name | CharField(max_length=100, unique=True) | Knotenname |
| info | TextField(default="", blank=True) | Knoteninformation |

Im Feld `is_root` wird festgelegt, ob ein Knoten die Wurzel eines Baums bildet. Falls nicht, wird im Feld
`parent` der Primärschlüssel des übergeordneten Knotens gespeichert, das nur für die Wurzel leer sein darf.
Dem Knoten muss im Feld `name` ein eindeutiger Name zugewiesen werden und im Feld `info` lassen sich den
Knoten beschreibende Informationen hinterlegen.

Da kein Feld im Model als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung für ein Objekt enthält.
