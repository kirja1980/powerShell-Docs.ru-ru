---
title: Как создать XML-файл HelpInfo | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853270"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Как создать XML-файл HelpInfo

В этом разделе, в этом разделе объясняется, как создать и заполнить файл сведений о справке, известную как «HelpInfo XML файла» для функцию обновляемой справки Windows PowerShell.

## <a name="helpinfo-xml-file-overview"></a>Общие сведения о файле HelpInfo XML

XML-файл HelpInfo является основным источником информации об обновляемой справке для модуля. Он включает расположение файлов справки для модулей, поддерживаемых языков и региональных параметров пользовательского интерфейса и номера версий, обновляемую справку для определения, имеет ли пользователь новейшие файлы справки.

Каждый модуль имеет только один XML-файл HelpInfo, даже если модуль содержит несколько файлов справки для нескольких языков и региональных параметров пользовательского интерфейса. Создает XML-файл HelpInfo автора модуля и помещает ее в расположения в Интернете, задаваемый **HelpInfoUri** ключа в манифесте модуля. Если файлы справки для модуля обновления, чтобы загружены, автора модуля обновляет файл HelpInfo XML и заменяет исходный файл HelpInfo XML с новой версией.

Крайне важно, что XML-файл HelpInfo тщательно сохранится. Если загрузить новые файлы, но забыть номера версий, обновляемой справки не будет загружать новые файлы на компьютеры пользователей. При добавлении файлы справки для нового пользовательского языка и региональных параметров, но не обновить файл HelpInfo XML или поместить его в нужное место, обновляемую справку, не скачивают новые файлы.

## <a name="in-this-section"></a>Содержание раздела

Этот раздел содержит следующие темы.

- [HelpInfo XML-схемы](./helpinfo-xml-schema.md)

- [Пример файла HelpInfo XML](./helpinfo-xml-sample-file.md)

- [Принципы присвоения имен XML-файл HelpInfo](./how-to-name-a-helpinfo-xml-file.md)

- [Как задать номера версий HelpInfo XML](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>См. также

[Поддержка обновляемой справки](./supporting-updatable-help.md)