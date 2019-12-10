# Glossar Model

Das Model definiert einen Glossar, der in der Web-App angezeigt wird.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| id | CharField(max_length=100, verbose_name=_("id"), primary_key=True) |  |
| header | CharField(max_length=200, verbose_name=_("header"), null=True) |  |
| description | TextField(verbose_name=_("description"), null=True) |  |
