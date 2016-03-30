# Ресурс Archive в DSC

> Область применения: Windows PowerShell 4.0, Windows PowerShell 5.0

Ресурс Archive в DSC Windows PowerShell предоставляет механизм распаковки файлов архивов (ZIP) в указанную папку.

## Синтаксис 
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## Свойства

|  Свойство  |  Описание   | 
|---|---| 
| Destination| Указывает, куда будет извлечено содержимое архива.| 
| путь| Указывает исходный путь для файла архива.| 
| __Контрольная сумма__| Определяет тип проверки пары файлов на идентичность. Если свойство __Checksum__ не задано, для сравнения используется только имя файла или каталога. Допустимые значения: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (по умолчанию). Если свойство __Checksum__ указано без свойства __Validate__, возникает ошибка конфигурации.| 
| Ensure| Указывает необходимость проверки того, существует ли содержимое архива в __папке назначения__. Чтобы убедиться, что содержимое существует, укажите для этого свойства значение __Present__. Чтобы убедиться, что содержимого не существует, укажите для этого свойства значение __Absent__. Значение по умолчанию — __Present__.| 
| DependsOn | Указывает, что перед настройкой этого ресурса необходимо запустить настройку другого ресурса. Например, если идентификатор первого запускаемого блока сценария для конфигурации ресурса — ResourceName, а его тип — __ResourceType__, то синтаксис использования этого свойства таков: `DependsOn = "[ResourceType]ResourceName"`.| 
| Проверить| Проверяет соответствие архива и подписи, используя свойство Checksum. Если свойство Checksum указано без свойства Validate, возникает ошибка конфигурации. Если свойство Validate указано без свойства Checksum, по умолчанию используется контрольная сумма SHA-256.| 
| Force| Определенные операции с файлами (например, перезапись файла или удаление непустого каталога) вызывают ошибку. Свойство Force позволяет переопределять такие ошибки. По умолчанию используется значение False.| 

## Пример

В следующем примере показано, как использовать ресурс Archive, чтобы убедиться, что содержимое архивного файла с именем Test.zip существует и извлекается в указанную папку.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
} 
```
<!--HONumber=Feb16_HO4-->