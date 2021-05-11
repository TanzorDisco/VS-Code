В системе должна присутствовать переменная окружения: ASPNETCORE_ENVIRONMENT=Development

Перед выполнением миграции необходимо сделать Check Out файла Croc.Etp.Domain\Migrations\EtpContextModelSnapshot.cs

Для миграции БД используется тулза [dotnet ef](https://docs.microsoft.com/en-us/ef/core/cli/dotnet) migrations add в папке Croc.Etp.Domain.
Пример: 
```
dotnet ef migrations add Organization_Add_ShortName --startup-project="..\Croc.Etp.Web"
```

Команду выполнять в cmd в папке проекта Croc.Etp.Domain

Команда для получения sql-скрипта миграции dotnet ef migrations script
```
dotnet ef migrations script 20210116085802_Required_Acceptance_For_Directions 
```

Команда обновления БД до определенной миграции (читай чекпоинта)
```
dotnet ef database update 20210426133253_Job_Interviews_Drop_Grade_Meeting_Column
```

Каждую команду заканчивай ссылкой на проект, содержащий конфиг-файл appsettings.json (это для того, чтобы не дублировать этот файл в разных проектах):
```
--startup-project="..\Croc.Etp.Web"
```
