---
title: Как переопределить методы обработки ввода | Документация Майкрософт
ms.date: 09/13/2016
ms.openlocfilehash: b245dc56b78ce9b7f1dea80b5d4988057c2f125f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784118"
---
# <a name="how-to-override-input-processing-methods"></a>Как переопределить методы обработки входных данных

В этих примерах показано, как перезаписать методы обработки ввода в командлете. Эти методы используются для выполнения следующих операций:

- Метод [System. Management. Automation. командлет. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) используется для выполнения одноразовых операций запуска, допустимых для всех объектов, обрабатываемых командлетом. Среда выполнения Windows PowerShell вызывает этот метод только один раз.

- Метод [System. Management. Automation. командлет. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) используется для обработки объектов, передаваемых в командлет. Среда выполнения Windows PowerShell вызывает этот метод для каждого объекта, передаваемого в командлет.

- Метод [System. Management. Automation. командлет. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) используется для выполнения операций однократной завершающей обработки. Среда выполнения Windows PowerShell вызывает этот метод только один раз.

## <a name="to-override-the-beginprocessing-method"></a>Переопределение метода BeginProcessing

- Объявите защищенное переопределение метода [System. Management. Automation. командлета. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

Следующий класс выводит образец сообщения. Чтобы использовать этот класс, измените глагол и существительное в атрибуте командлета, измените имя класса, чтобы отразить новую глагол и существительное, а затем добавьте функциональные возможности, необходимые для переопределения метода [System. Management. Automation. командлет. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>Переопределение метода ProcessRecord

- Объявите защищенное переопределение метода [System. Management. Automation. командлета. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

Следующий класс выводит образец сообщения. Чтобы использовать этот класс, измените глагол и существительное в атрибуте командлета, измените имя класса, чтобы отразить новую глагол и существительное, а затем добавьте функциональные возможности, необходимые для переопределения метода [System. Management. Automation. командлет. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>Переопределение метода EndProcessing

- Объявите защищенное переопределение метода [System. Management. Automation. командлет. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .

Следующий класс выводит пример. Чтобы использовать этот класс, измените глагол и существительное в атрибуте командлета, измените имя класса, чтобы отразить новую глагол и существительное, а затем добавьте функциональные возможности, необходимые для переопределения метода [System. Management. Automation. командлет. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>См. также

[System. Management. Automation. командлет. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. командлет. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. командлет. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Запись командлета Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
