---
title: Элемент ScriptBlock для Селектионкондитион для Ентриселектедби для Таблеконтрол (Format) | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368583"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="e4bf4-102">Элемент ScriptBlock для элемента SelectionCondition для элемента EntrySelectedBy для элемента TableControl (формат)</span><span class="sxs-lookup"><span data-stu-id="e4bf4-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="e4bf4-103">Указывает блок скрипта, который запускает условие.</span><span class="sxs-lookup"><span data-stu-id="e4bf4-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="e4bf4-104">При вычислении этого скрипта в `true` условие выполняется, и используется запись таблицы.</span><span class="sxs-lookup"><span data-stu-id="e4bf4-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="e4bf4-105">Элемент конфигурации (Format) Виевдефинитионс элемент (формат) элемент представления (Format) Таблеконтрол элемент (Format) Таблеровентриес элемент (Format) Таблеровентри элемент (Format) Ентриселектедби для Таблеровентри (Format) Элемент Селектионкондитион для Ентриселектедби для элемента ScriptBlock Таблеровентри (Format) для Селектионкондитион для ентриселектедби в TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e4bf4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4bf4-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e4bf4-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4bf4-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e4bf4-107">Attributes and Elements</span></span>

<span data-ttu-id="e4bf4-108">В следующих разделах описываются атрибуты, дочерние элементы и родительский элемент элемента `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="e4bf4-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4bf4-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e4bf4-109">Attributes</span></span>

<span data-ttu-id="e4bf4-110">Нет.</span><span class="sxs-lookup"><span data-stu-id="e4bf4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4bf4-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e4bf4-111">Child Elements</span></span>

<span data-ttu-id="e4bf4-112">Нет.</span><span class="sxs-lookup"><span data-stu-id="e4bf4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e4bf4-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e4bf4-113">Parent Elements</span></span>

|<span data-ttu-id="e4bf4-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="e4bf4-114">Element</span></span>|<span data-ttu-id="e4bf4-115">Описание</span><span class="sxs-lookup"><span data-stu-id="e4bf4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4bf4-116">Элемент Селектионкондитион для Ентриселектедби для Таблеровентри (Format)</span><span class="sxs-lookup"><span data-stu-id="e4bf4-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e4bf4-117">Определяет условие, которое должно существовать для использования этой записи таблицы.</span><span class="sxs-lookup"><span data-stu-id="e4bf4-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e4bf4-118">Текстовое значение</span><span class="sxs-lookup"><span data-stu-id="e4bf4-118">Text Value</span></span>

<span data-ttu-id="e4bf4-119">Укажите оцениваемый скрипт.</span><span class="sxs-lookup"><span data-stu-id="e4bf4-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4bf4-120">Замечания</span><span class="sxs-lookup"><span data-stu-id="e4bf4-120">Remarks</span></span>

<span data-ttu-id="e4bf4-121">Условие выбора должно указывать по крайней мере один блок скрипта или имя свойства, но не может одновременно указывать оба значения.</span><span class="sxs-lookup"><span data-stu-id="e4bf4-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="e4bf4-122">Дополнительные сведения об использовании условий выбора см. в разделе [Определение условий для, когда используется запись или элемент представления](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e4bf4-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e4bf4-123">Дополнительные сведения о компонентах табличного представления см. в разделе [Создание табличного представления](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e4bf4-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e4bf4-124">См. также:</span><span class="sxs-lookup"><span data-stu-id="e4bf4-124">See Also</span></span>

[<span data-ttu-id="e4bf4-125">Создание табличного представления</span><span class="sxs-lookup"><span data-stu-id="e4bf4-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e4bf4-126">Определение условий для отображения данных</span><span class="sxs-lookup"><span data-stu-id="e4bf4-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e4bf4-127">Элемент PropertyName для Селектионкондитион для Ентриселектедби для Таблеровентри (Format)</span><span class="sxs-lookup"><span data-stu-id="e4bf4-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="e4bf4-128">Элемент Селектионкондитион для Ентриселектедби для Таблеровентри (Format)</span><span class="sxs-lookup"><span data-stu-id="e4bf4-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e4bf4-129">Написание файла форматирования PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4bf4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)