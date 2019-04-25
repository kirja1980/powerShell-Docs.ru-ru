---
title: Параметры свойств | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251427"
---
# <a name="property-parameters"></a>Параметры свойств

Ниже перечислены рекомендуемые имена и функции для параметров свойств.

|Параметр|Функции|
|---|---|
|**число**<br>Тип данных: Int32|Реализуйте этот параметр, благодаря которому пользователь может указать количество объектов для обработки.|
|**Описание**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать описание для ресурса.|
|**От**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать ссылочный объект для получения сведений из.|
|**Id**<br>Тип данных: Зависимых ресурсов|Реализуйте этот параметр, благодаря которому пользователь может указать идентификатор ресурса.|
|**Входные данные**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать входной файл спецификации.|
|**Расположение**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать расположение ресурса.|
|**LogName**<br>Тип данных: Строка|Реализуйте этот параметр, таким образом, пользователь может указать имя файла журнала для обработки или использовать.|
|**Name**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать имя ресурса.|
|**Выходные данные**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать выходной файл.|
|**Владелец**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать имя владельца ресурса.|
|**Свойство**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать имя или имена свойств, которые используются.|
|**Причина**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать, почему этот командлет вызывается.|
|**регулярное выражение**<br>Тип данных: SwitchParameter|Реализуйте этот параметр, чтобы регулярные выражения используются в том случае, если указан параметр. Если этот параметр задан, подстановочные знаки, не разрешаются.|
|**Скорость**<br>Тип данных: Int32|Реализуйте этот параметр, таким образом, пользователь может указать скорость в бодах. Пользователь задает этот параметр для скорости ресурса.|
|**Состояние**<br>Тип данных: Ключевое слово массива|Реализуйте этот параметр, таким образом, пользователь может указать названия штатов, например KEYDOWN.|
|**Значение**<br>Тип данных: Объект|Реализуйте этот параметр, благодаря которому пользователь может указать значение, предоставляемое в командлет.|
|**Версия**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать версию свойства.|

## <a name="see-also"></a>См. также

[Параметры командлета](./cmdlet-parameters.md)

[Запись командлета Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Пакет SDK для Windows PowerShell](../windows-powershell-reference.md)