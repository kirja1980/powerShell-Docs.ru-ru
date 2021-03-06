---
title: Элемент Frame для элемента управления Кустомитем для представления (формат) | Документация Майкрософт
ms.date: 09/13/2016
ms.openlocfilehash: 5ade36c183a026cb9001a2abbe91d31638a87108
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773459"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Элемент Frame для элемента CustomItem для элемента Controls для элемента View (формат)

Определяет способ отображения данных, например сдвиг данных влево или вправо. Этот элемент используется при определении элементов управления, которые могут использоваться представлением.

Элемент Configuration (Format) Виевдефинитионс элемент (формат) элемент представления (Format) управляет управляющий элемент (Format) элемент управления для элементов управления представления (Format) ошибка customcontrol для элементов управления элемента Кустоментриес View (формат). для элемента Ошибка customcontrol для представления (Format) Кустоментри для Кустоментриес для элементов управления для представления (Format) Кустомитем элемента для Кустоментри для элементов управления элемента Frame (формат) для Кустомитем для элементов управления представления (формат)

## <a name="syntax"></a>Синтаксис

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы

В следующих разделах описываются атрибуты, дочерние элементы и родительский элемент `Frame` элемента.

### <a name="attributes"></a>Атрибуты

Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|`CustomItem Element`|Обязательный элемент|
|[Элемент Фирстлинехангинг рамки элементов управления представления (формат)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Необязательный элемент.<br /><br /> Указывает, сколько знаков первая строка смещается влево.|
|[Элемент Фирстлинеиндент рамки элементов управления представления (формат)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Необязательный элемент.<br /><br /> Указывает, сколько знаков первая строка смещается вправо.|
|[Элемент Лефтиндент рамки элементов управления представления (формат)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Необязательный элемент.<br /><br /> Указывает, сколько символов перемещает данные из левого поля.|
|[Элемент Ригхтиндент рамки элементов управления представления (формат)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Необязательный элемент.<br /><br /> Указывает, сколько символов перемещает данные с правого края.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CustomItem для элемента CustomEntry для элемента Controls для элемента View (формат)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Определяет, какие данные отображаются элементом управления и как они отображаются.|

## <a name="remarks"></a>Примечания

Нельзя указывать элементы [фирстлинехангинг](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) и [фирстлинеиндент](./firstlineindent-element-for-frame-for-controls-for-view-format.md) в одном и том же `Frame` элементе.

## <a name="see-also"></a>См. также

[Элемент Фирстлинехангинг рамки элементов управления представления (формат)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Элемент Фирстлинеиндент рамки элементов управления представления (формат)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Элемент Лефтиндент рамки элементов управления представления (формат)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Элемент Ригхтиндент рамки элементов управления представления (формат)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Элемент CustomItem для элемента CustomEntry для элемента Controls для элемента View (формат)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Написание файла форматирования PowerShell](./writing-a-powershell-formatting-file.md)
