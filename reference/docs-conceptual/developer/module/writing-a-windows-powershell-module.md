---
title: Создание модуля Windows PowerShell | Документация Майкрософт
ms.date: 09/13/2016
ms.openlocfilehash: d2398a8111a9832af2465d045be0bdefc3cf927a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779154"
---
# <a name="writing-a-windows-powershell-module"></a>Написание модуля Windows PowerShell

Этот документ предназначен для администраторов, разработчиков скриптов и разработчиков командлетов, которым необходимо упаковать и распространить свои командлеты Windows PowerShell. С помощью модулей Windows PowerShell можно упаковывать и распространять решения Windows PowerShell без использования скомпилированного языка.

Модули Windows PowerShell позволяют секционировать, упорядочивать и систематизировать код Windows PowerShell в автономных, многократно используемых единицах. С помощью этих многократно используемых модулей можно легко предоставить доступ к модулям напрямую другим пользователям. Если вы являетесь разработчиком скриптов, вы также можете повторно упаковать сторонние модули для создания пользовательских приложений на основе сценариев. Модули, аналогичные модулям в других языках сценариев, таких как Perl и Python, обеспечивают готовые к работе решения сценариев, использующие многократно используемые, распространяемые компоненты с дополнительным преимуществом, позволяющим переупаковать и составить абстрактные компоненты, чтобы создать пользовательские решения.

В большинстве случаев Windows PowerShell будет обрабатывать любой допустимый код сценария Windows PowerShell, сохраненный в файле. PSM1 в качестве модуля. PowerShell также будет автоматически обрабатывать любую сборку двоичных командлетов как модуль. Однако можно также использовать модуль (или более конкретно, манифест модуля) для объединения всего решения. В следующих сценариях описываются типичные варианты использования модулей Windows PowerShell.

### <a name="libraries"></a>Библиотеки

Модули можно использовать для упаковки и распространения согласованных библиотек функций, выполняющих стандартные задачи. Как правило, имена этих функций имеют одно или несколько существительных, отражающих общую задачу, для которой они используются. Эти функции также могут быть похожи на .NET Framework классы в том, что они могут иметь открытые и закрытые члены. Например, Библиотека может содержать набор функций для передачи файлов. В этом случае существительное, отражающее общую задачу, может быть «File».

### <a name="configuration"></a>Конфигурация

Модули можно использовать для настройки среды путем добавления конкретных командлетов, поставщиков, функций и переменных.

### <a name="compiled-code-development-and-distribution"></a>Разработка и распространение скомпилированного кода

Разработчики командлетов и поставщиков могут использовать модули для тестирования и распространения скомпилированного кода без необходимости создавать оснастки. Они могут импортировать сборку, содержащую скомпилированный код, в виде модуля (двоичный модуль) без необходимости создавать и регистрировать оснастки.

## <a name="see-also"></a>См. также:

[Общие сведения о модулях Windows PowerShell](./understanding-a-windows-powershell-module.md)

[Как написать модуль сценария PowerShell](./how-to-write-a-powershell-script-module.md)

[Как написать бинарный модуль PowerShell](./how-to-write-a-powershell-binary-module.md)

[Как написать манифест модуля PowerShell](how-to-write-a-powershell-module-manifest.md)

[Изменение пути установки PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Импорт модуля PowerShell](./importing-a-powershell-module.md)

[Установка модуля PowerShell](./installing-a-powershell-module.md)
