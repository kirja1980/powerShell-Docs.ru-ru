---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Ресурс DSC WindowsOptionalFeatureSet
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047612"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Ресурс DSC WindowsOptionalFeatureSet

> Область применения. Windows PowerShell 5.0

Ресурс **WindowsOptionalFeatureSet** в DSC Windows PowerShell предоставляет механизм включения дополнительных компонентов на целевом узле.
Он является [составным ресурсом](../../../resources/authoringResourceComposite.md), который вызывает [ресурс WindowsOptionalFeature](windowsOptionalFeatureResource.md) для каждого компонента, указанного в свойстве `Name`.

Используйте этот ресурс, если нужно настроить одинаковое состояние для нескольких дополнительных компонентов Windows.

## <a name="syntax"></a>Синтаксис

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Свойства

|  Свойство  |  Описание   |
|---|---|
| Name| Указывает имена компонентов, которые необходимо включить или отключить.|
| Ensure| Указывает, включены ли компоненты. Чтобы включить компоненты, установите для этого свойства значение "Включить", чтобы отключить — значение "Отключить".|
| Источник| Не реализовано.|
| NoWindowsUpdateCheck| Указывает, обращается ли система DISM к Центру обновления Windows при поиске исходных файлов для включения компонентов. Если задано значение $true, система DISM не обращается к Центру обновления Windows.|
| RemoveFilesOnDisable| Задайте значение **$true**, чтобы удалить все файлы, связанные с компонентами, при их отключении (то есть когда свойству **Ensure** присваивается значение Absent).|
| Уровень журнала| Максимальный уровень результатов, показываемый в журналах. Допустимыми являются значения: «ErrorsOnly» (записываются только ошибки), «ErrorsAndWarning» (ошибки и предупреждения записываются) и «ErrorsAndWarningAndInformation» (регистрируются ошибки, предупреждения и отладочной информации).|
| LogPath| Путь к файлу журнала, в котором поставщик ресурсов должен вести журнал работы.|
| DependsOn| Указывает, что перед настройкой этого ресурса необходимо запустить настройку другого ресурса. Например, если идентификатор первого запускаемого блока сценария для конфигурации ресурса — __ResourceName__, а его тип — __ResourceType__, то синтаксис использования этого свойства таков: `DependsOn = "[ResourceType]ResourceName"`.|