Le compte **SA** est un administrateur système sur l’instance SQL Server qui est créée lors de l’installation. Une fois le conteneur SQL Server créé, la variable d’environnement `MSSQL_SA_PASSWORD` que vous avez spécifiée peut être découverte en exécutant `echo $MSSQL_SA_PASSWORD` dans le conteneur. Pour des raisons de sécurité, changez le mot de passe pour SA :

1. Choisissez un mot de passe fort à utiliser pour l’utilisateur SA.

1. Utilisez `docker exec` pour exécuter l’utilitaire **sqlcmd** afin de modifier le mot de passe à l’aide d’une instruction Transact-SQL. Remplacez `<YourStrong!Passw0rd>` et `<YourNewStrong!Passw0rd>` par les valeurs de vos propres mots de passe :

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourStrong!Passw0rd>' \
      -Q 'ALTER LOGIN SA WITH PASSWORD="<YourNewStrong!Passw0rd>"'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourStrong!Passw0rd>" `
      -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
   ```
