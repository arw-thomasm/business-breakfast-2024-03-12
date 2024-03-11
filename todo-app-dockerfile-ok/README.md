# Todo-App

Todo Applikation, die Daten entweder in einer SQLite oder in einer MySQL Datenbank speichert.

Wenn keine Environment Variablen übergeben werden, dann verwendet die App eine SQLite-DB unter `/etc/todos/todo.db`. Mit der ENV-Varibale `SQLITE_DB_LOCATION` kann der Speicherort der DB angepasst werden.

## MySQL Deployment

Wenn man eine MySQL Datenbank verwenden möchte, dann müssen folgende Environment Variablen übergeben werden:

- MYSQL_HOST
- MYSQL_USER
- MYSQL_PASSWORD
- MYSQL_DB

## Deployment auf OpenShift

### Deployment per Dockerfile

Anpassen des Dockerfiles notwendig, da bei OpenShift die UID standardmäßig dynamisch generiert wird. Die generierte UID ist aber Mitglied der Gruppe `root` (GID 0).
Es muss also sichergestellt werden, dass die GID 0 entsprechende Rechte auf die Dateien hat. Am besten macht man das, indem man die Dateien `COPY --chown=1001:0 . .` zum Image hinzufügt und dann die Dateirechte so setzt, dass die Gruppenrechte den Userrechten entsprechen:
```
RUN chmod -R g=u .
```
