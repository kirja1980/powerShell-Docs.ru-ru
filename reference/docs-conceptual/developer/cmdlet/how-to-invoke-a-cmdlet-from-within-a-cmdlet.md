---
title: Вызов командлета из командлета | Документация Майкрософт
ms.date: 09/13/2016
ms.openlocfilehash: 2d5b0788d3310d0dd7b311f86c497afe8eec9d11
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784152"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Как вызвать командлет из другого командлета

В этом примере показано, как вызвать командлет из другого командлета, который позволяет добавлять функциональные возможности вызванного командлета в разрабатываемый командлет. В этом примере `Get-Process` вызывается командлет для получения процессов, выполняемых на локальном компьютере. Вызов `Get-Process` командлета эквивалентен следующей команде. Эта команда извлекает все процессы, имена которых начинаются с символов "a" и т. д.

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Можно вызывать только те командлеты, которые являются производными непосредственно от класса [System. Management. Automation. командлет](/dotnet/api/System.Management.Automation.Cmdlet) . Нельзя вызвать командлет, производный от класса [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Вызов командлета из командлета

1. Убедитесь, что указана сборка, определяющая вызываемый командлет, и что `using` добавляется соответствующая инструкция. В этом примере добавляются следующие пространства имен.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. В методе обработки входных данных командлета создайте новый экземпляр вызываемого командлета. В этом примере создается объект типа [Microsoft. PowerShell. Commands. жетпроцесскомманд](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) вместе со строкой, содержащей аргументы, используемые при вызове командлета.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Вызовите метод [System. Management. Automation. командлет. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) , чтобы вызвать `Get-Process` командлет.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Пример

В этом примере `Get-Process` командлет вызывается из метода [System. Management. Automation. командлет. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) командлета.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>См. также

[Запись командлета Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
