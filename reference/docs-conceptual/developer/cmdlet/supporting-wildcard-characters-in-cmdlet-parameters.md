---
title: Поддержка подстановочных знаков в параметрах командлета
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365313"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Поддержка подстановочных знаков в параметрах командлета

Часто приходится проектировать командлет, который будет выполняться для группы ресурсов, а не для отдельного ресурса. Например, командлету может потребоваться поиск всех файлов в хранилище данных с одинаковым именем или расширением. При проектировании командлета, который будет выполняться для группы ресурсов, необходимо предоставить поддержку подстановочных знаков.

> [!NOTE]
> Использование подстановочных знаков иногда называется *глобализации*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Командлеты Windows PowerShell, использующие подстановочные знаки

 Многие командлеты Windows PowerShell поддерживают подстановочные знаки для значений их параметров. Например, почти каждый командлет с параметром `Name` или `Path` поддерживает подстановочные знаки для этих параметров. (Хотя большинство командлетов с параметром `Path` также имеют параметр `LiteralPath`, который не поддерживает подстановочные знаки.) Следующая команда показывает, как использовать подстановочный знак для возврата всех командлетов в текущем сеансе, имя которых содержит команду Get.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>Поддерживаемые подстановочные знаки

Windows PowerShell поддерживает следующие подстановочные знаки.

| Использования |                             Описание                             |  Пример   |     Совпадения      | Не соответствует |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | Соответствует нулю или большему числу символов, начиная с указанной позиции | `a*`       | A, AG, Apple     |                |
| ?        | Соответствует любому символу в указанной позиции                     | `?n`       | Объект, в, на       | обнаружил            |
| [ ]      | Соответствует диапазону символов                                       | `[a-l]ook` | книга, Кука, взгляд | Нук, занял     |
| [ ]      | Соответствует указанным символам                                    | `[bn]ook`  | книга, Нук       | Кука, взгляд     |

При проектировании командлетов, поддерживающих символы-шаблоны, можно использовать сочетания символов-шаблонов. Например, следующая команда использует командлет `Get-ChildItem` для получения всех TXT-файлов, которые находятся в папке К:\течдокс и начинаются с букв "a" до "l".

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

Предыдущая команда использует `[a-l]` с подстановочным знаком диапазона, чтобы указать, что имя файла должно начинаться с символов "a" до "l" и использовать подстановочный знак `*` в качестве заполнителя для любых символов между первой буквой имени файла и txt-файлом **.** расширение.

В следующем примере используется шаблон шаблона диапазона, который исключает букву "d", но включает все остальные буквы из "a" в "f".

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Обработка литеральных символов в шаблонах с подстановочными знаками

Если указанный шаблон шаблона содержит литеральные символы, которые не должны быть интерпреттед в качестве подстановочных знаков, используйте символ обратной кавычки (`` ` ``) в качестве escape-символа. Если вы указываете литеральные символы int API PowerShell, используйте один обратный символ. При указании литеральных символов в командной строке PowerShell используйте два обратных импульса.

Например, следующий шаблон содержит две квадратные скобки, которые должны быть выполнены буквально.

При использовании в API PowerShell используется:

- "Джон Смит \` [* ']"

При использовании из командной строки PowerShell:

- "Джон Смит \` \` [* \`"] "

Этот шаблон соответствует "Джон Смит [Marketing]" или "Джон Смит [разработка]". Пример:

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Выходные данные командлета и подстановочные знаки

Если параметры командлета поддерживают подстановочные знаки, операция обычно создает выходные данные массива.
Иногда не имеет смысла поддерживать выходные данные массива, поскольку пользователь может использовать только один элемент. Например, командлет `Set-Location` не поддерживает вывод массива, поскольку пользователь устанавливает только одно расположение. В этом случае командлет по-прежнему поддерживает подстановочные знаки, но обеспечивает разрешение в одном месте.

## <a name="see-also"></a>См. также:

[Запись командлета Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Класс Вилдкардпаттерн](/dotnet/api/system.management.automation.wildcardpattern)