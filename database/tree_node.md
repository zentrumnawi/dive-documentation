# Baumkoten Model

Das Model definiert einen Knoten ein einer Baumstruktur.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| node_name | CharField(max_length=200, verbose_name=_("node name"), unique=True) |  |
| parent | TreeForeignKey('self', on_delete=models.CASCADE, null=True, blank=True, related_name='leaf_nodes') |  |
| info_text | TextField(max_length=500, blank=True) |  |
| is_top_level | BooleanField(default=False) |  |
