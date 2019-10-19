---
title: Элемент Ентриселектедби для Видинтри (Format) | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363333"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="9488c-102">Элемент EntrySelectedBy для элемента WideEntry (формат)</span><span class="sxs-lookup"><span data-stu-id="9488c-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="9488c-103">Определяет типы .NET, которые используют это определение расширенного представления или условие, которое должно существовать, чтобы использовать это определение.</span><span class="sxs-lookup"><span data-stu-id="9488c-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="9488c-104">Элемент конфигурации (Format) Виевдефинитионс элемент (формат) элемент представления (Format) Видеконтрол элемент (Format) Видинтриес элемент (Format) Видинтри элемент (Format) Ентриселектедби для Видинтри (Format)</span><span class="sxs-lookup"><span data-stu-id="9488c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9488c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9488c-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9488c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9488c-106">Attributes and Elements</span></span>

<span data-ttu-id="9488c-107">В следующих разделах описываются атрибуты, дочерние элементы и родительский элемент элемента `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="9488c-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9488c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9488c-108">Attributes</span></span>

<span data-ttu-id="9488c-109">Нет.</span><span class="sxs-lookup"><span data-stu-id="9488c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9488c-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9488c-110">Child Elements</span></span>

|<span data-ttu-id="9488c-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="9488c-111">Element</span></span>|<span data-ttu-id="9488c-112">Описание</span><span class="sxs-lookup"><span data-stu-id="9488c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9488c-113">Элемент Селектионкондитион для Ентриселектедби для Видинтри (Format)</span><span class="sxs-lookup"><span data-stu-id="9488c-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9488c-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="9488c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="9488c-115">Определяет условие, которое должно существовать для использования в этом расширенном определении представления.</span><span class="sxs-lookup"><span data-stu-id="9488c-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="9488c-116">Элемент Селектионсетнаме для Ентриселектедби для Видинтри (Format)</span><span class="sxs-lookup"><span data-stu-id="9488c-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9488c-117">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="9488c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9488c-118">Указывает набор типов .NET, использующих это определение в масштабах представления.</span><span class="sxs-lookup"><span data-stu-id="9488c-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="9488c-119">Элемент TypeName для Ентриселектедби для Видинтри (Format)</span><span class="sxs-lookup"><span data-stu-id="9488c-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="9488c-120">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="9488c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9488c-121">Указывает тип .NET, использующий это определение в масштабе представления.</span><span class="sxs-lookup"><span data-stu-id="9488c-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9488c-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9488c-122">Parent Elements</span></span>

|<span data-ttu-id="9488c-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="9488c-123">Element</span></span>|<span data-ttu-id="9488c-124">Описание</span><span class="sxs-lookup"><span data-stu-id="9488c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9488c-125">Элемент Видинтри (Format)</span><span class="sxs-lookup"><span data-stu-id="9488c-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="9488c-126">Предоставляет определение расширенного представления.</span><span class="sxs-lookup"><span data-stu-id="9488c-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9488c-127">Замечания</span><span class="sxs-lookup"><span data-stu-id="9488c-127">Remarks</span></span>

<span data-ttu-id="9488c-128">Необходимо указать по крайней мере один тип, набор выбора или условие выбора для расширенного определения представления.</span><span class="sxs-lookup"><span data-stu-id="9488c-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="9488c-129">Максимальное количество дочерних элементов, которое можно использовать, не ограничено.</span><span class="sxs-lookup"><span data-stu-id="9488c-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="9488c-130">Условия выбора используются для определения условия, которое должно существовать для использования определения, например, если объект имеет определенное свойство или значение конкретного свойства или значения скрипта, равное `true`.</span><span class="sxs-lookup"><span data-stu-id="9488c-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="9488c-131">Дополнительные сведения об условиях выбора см. в разделе [Определение условий для отображения данных](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9488c-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9488c-132">Дополнительные сведения о других компонентах расширенного представления см. [в разделе Создание расширенного представления](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9488c-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9488c-133">См. также:</span><span class="sxs-lookup"><span data-stu-id="9488c-133">See Also</span></span>

[<span data-ttu-id="9488c-134">Элемент Видинтри (Format)</span><span class="sxs-lookup"><span data-stu-id="9488c-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="9488c-135">Элемент Селектионкондитион для Ентриселектедби для Видинтри (Format)</span><span class="sxs-lookup"><span data-stu-id="9488c-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9488c-136">Элемент Селектионсетнаме для Ентриселектедби для Видинтри (Format)</span><span class="sxs-lookup"><span data-stu-id="9488c-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9488c-137">Элемент TypeName для Ентриселектедби для Видинтри (Format)</span><span class="sxs-lookup"><span data-stu-id="9488c-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="9488c-138">Создание расширенного представления</span><span class="sxs-lookup"><span data-stu-id="9488c-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9488c-139">Определение условий для отображения данных</span><span class="sxs-lookup"><span data-stu-id="9488c-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9488c-140">Написание файла форматирования PowerShell</span><span class="sxs-lookup"><span data-stu-id="9488c-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)