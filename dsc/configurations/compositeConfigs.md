---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Вложение конфигураций
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402280"
---
# <a name="nesting-dsc-configurations"></a>Вложение конфигураций DSC

Вложенная конфигурация (также называемая составной конфигурацией) — это конфигурация, которая вызывается в составе другой конфигурации подобно ресурсу.
Обе конфигурации должны быть определены в одном файле.

Давайте рассмотрим простой пример:

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }

}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

В этом примере `FileConfig` принимает два обязательных параметра — **CopyFrom** и **CopyTo**, — которые используются как значения для свойств **SourcePath** и **DestinationPath** в блоке ресурсов `File`.
Конфигурация `NestedConfig` вызывает конфигурацию `FileConfig`, как будто это ресурс.
Свойства в блоке ресурсов `NestedConfig` (**CopyFrom** и **CopyTo**) — параметры конфигурации `FileConfig`.

## <a name="see-also"></a>См. также

- [Составные ресурсы: использование DSC как ресурса](../resources/authoringResourceComposite.md)