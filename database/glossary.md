# Glossar Model

Das Model definiert einen Glossar, der in der Web-App angezeigt wird.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| id | CharField(max_length=100, primary_key=True) |  |
| header | CharField(max_length=200, default="", blank=True) |  |
| description | TextField(default="", blank=True) |  |
