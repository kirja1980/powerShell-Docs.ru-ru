---
title: Динамические параметры командлета | Документация Майкрософт
ms.date: 09/13/2016
ms.openlocfilehash: f44f71326d4711242c754c332a151dd997721595
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782367"
---
# <a name="cmdlet-dynamic-parameters"></a>Динамические параметры командлета

Командлеты могут определять параметры, доступные пользователю в особых условиях, например, если аргумент другого параметра является определенным значением. Эти параметры добавляются во время выполнения и называются динамическими параметрами, так как они добавляются только при необходимости. Например, можно создать командлет, добавляющий несколько параметров только в том случае, если указан определенный параметр Switch.

> [!NOTE]
> Поставщики и функции PowerShell также могут определять динамические параметры.

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>Динамические параметры в командлетах PowerShell

PowerShell использует динамические параметры в нескольких командлетах поставщика. Например, `Get-Item` `Get-ChildItem` командлеты и добавляют параметр **CodeSigningCert** во время выполнения, когда параметр **path** указывает путь к поставщику **сертификата** . Если параметр **path** задает путь для другого поставщика, параметр **CodeSigningCert** недоступен.

В следующих примерах показано, как параметр **CodeSigningCert** добавляется во время выполнения при `Get-Item` запуске.

В этом примере среда выполнения PowerShell добавила параметр, а командлет — успешно.

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

В этом примере указывается диск **файловой** системы, и возвращается ошибка. Сообщение об ошибке указывает, что не удается найти параметр **CodeSigningCert** .

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Поддержка динамических параметров

Для поддержки динамических параметров в код командлета должны быть добавлены следующие элементы.

### <a name="interface"></a>Интерфейс

[System. Management. Automation. идинамикпараметерс](/dotnet/api/System.Management.Automation.IDynamicParameters).
Этот интерфейс предоставляет метод, который получает динамические параметры.

Пример:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>Метод

[System. Management. Automation. идинамикпараметерс. жетдинамикпараметерс](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).
Этот метод извлекает объект, содержащий определения динамических параметров.

Пример:

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a>Класс

Класс, определяющий динамические параметры, которые необходимо добавить. Этот класс должен включать атрибут **Parameter** для каждого параметра, а также любые дополнительные атрибуты **псевдонима** и **проверки** , необходимые для командлета.

Пример:

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

Полный пример командлета, поддерживающего динамические параметры, см. [в разделе Объявление динамических параметров](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>См. также

[System. Management. Automation. Идинамикпараметерс](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System. Management. Automation. Идинамикпараметерс. Жетдинамикпараметерс](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Как объявить динамические параметры](./how-to-declare-dynamic-parameters.md)

[Запись командлета Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
