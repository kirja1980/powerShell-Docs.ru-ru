---
title: Элемент ScriptBlock для GroupBy (формат) | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856210"
---
# <a name="scriptblock-element-for-groupby-format"></a>Элемент ScriptBlock для элемента GroupBy (формат)

Указывает сценарий, который запускает новую группу, при каждом изменении его значения.

Элемент (формат) элемент ViewDefinitions (формат) представление элемента (формат) GroupBy элемента конфигурации для элемента представления (формат) ScriptBlock для GroupBy (формат)

## <a name="syntax"></a>Синтаксис

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы

Ниже описаны атрибуты, дочерние элементы и родительский элемент `ScriptBlock` элемент.

### <a name="attributes"></a>Атрибуты

Нет.

### <a name="child-elements"></a>Дочерние элементы

Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[GroupBy-элемент для представления (формат)](./groupby-element-for-view-format.md)|Определяет порядок отображения группы объектов .NET.|

## <a name="text-value"></a>Текстовое значение

Укажите сценарий, который вычисляется.

## <a name="remarks"></a>Замечания

Windows PowerShell запускает новую группу, при каждом изменении значения этого сценария.

Если этот элемент указан, нельзя указать [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) элемент, чтобы начать новую группу.

## <a name="see-also"></a>См. также

[Элемент PropertyName для GroupBy (формат)](./propertyname-element-for-groupby-format.md)

[GroupBy-элемент для представления (формат)](./groupby-element-for-view-format.md)

[Запись файла форматирования PowerShell](./writing-a-powershell-formatting-file.md)