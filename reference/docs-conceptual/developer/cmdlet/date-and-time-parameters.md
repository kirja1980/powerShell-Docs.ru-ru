---
title: Параметры даты и времени | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369793"
---
# <a name="date-and-time-parameters"></a><span data-ttu-id="0a838-102">Параметры даты и времени</span><span class="sxs-lookup"><span data-stu-id="0a838-102">Date and Time Parameters</span></span>

<span data-ttu-id="0a838-103">В следующей таблице перечислены рекомендуемые имена и функциональные возможности для параметров, обрабатывающих сведения о дате и времени.</span><span class="sxs-lookup"><span data-stu-id="0a838-103">The following table lists recommended names and functionality for parameters that handle date and time information.</span></span> <span data-ttu-id="0a838-104">Параметры даты и времени обычно используются для записи при создании или доступе.</span><span class="sxs-lookup"><span data-stu-id="0a838-104">Date and time parameters are typically used to record when something is created or accessed.</span></span>

|<span data-ttu-id="0a838-105">Параметр</span><span class="sxs-lookup"><span data-stu-id="0a838-105">Parameter</span></span>|<span data-ttu-id="0a838-106">Функция</span><span class="sxs-lookup"><span data-stu-id="0a838-106">Functionality</span></span>|
|---|---|
|<span data-ttu-id="0a838-107">**Обращения**</span><span class="sxs-lookup"><span data-stu-id="0a838-107">**Accessed**</span></span><br><span data-ttu-id="0a838-108">Тип данных: переключатель</span><span class="sxs-lookup"><span data-stu-id="0a838-108">Data type: SwitchParameter</span></span>|<span data-ttu-id="0a838-109">Реализуйте этот параметр, чтобы при указании командлета он работал с ресурсами, к которым осуществлялся доступ в зависимости от даты и времени, указанных в параметрах **Before** и **After** .</span><span class="sxs-lookup"><span data-stu-id="0a838-109">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been accessed based on the date and time specified by the **Before** and **After** parameters.</span></span> <span data-ttu-id="0a838-110">Если этот параметр указан, то **созданные** и **измененные** параметры должны быть не указаны.</span><span class="sxs-lookup"><span data-stu-id="0a838-110">If this parameter is specified, the **Created** and **Modified** parameters must be not be specified.</span></span>|
|<span data-ttu-id="0a838-111">**Запуска**</span><span class="sxs-lookup"><span data-stu-id="0a838-111">**After**</span></span><br><span data-ttu-id="0a838-112">Тип данных: DateTime</span><span class="sxs-lookup"><span data-stu-id="0a838-112">Data type: DateTime</span></span>|<span data-ttu-id="0a838-113">Реализуйте этот параметр, чтобы указать дату и время, после которых был использован командлет.</span><span class="sxs-lookup"><span data-stu-id="0a838-113">Implement this parameter to specify the date and time after which the cmdlet was used.</span></span> <span data-ttu-id="0a838-114">Чтобы параметр **After** работал, командлет также должен иметь **доступный**, **созданный**или **измененный** параметр.</span><span class="sxs-lookup"><span data-stu-id="0a838-114">For the **After** parameter to work, the cmdlet must also have an **Accessed**, **Created**, or **Modified** parameter.</span></span> <span data-ttu-id="0a838-115">И этот параметр должен иметь значение **true** при вызове командлета.</span><span class="sxs-lookup"><span data-stu-id="0a838-115">And, that parameter must be set to **true** when the cmdlet is called.</span></span>|
|<span data-ttu-id="0a838-116">**Для**</span><span class="sxs-lookup"><span data-stu-id="0a838-116">**Before**</span></span><br><span data-ttu-id="0a838-117">Тип данных: DateTime</span><span class="sxs-lookup"><span data-stu-id="0a838-117">Data type: DateTime</span></span>|<span data-ttu-id="0a838-118">Реализуйте этот параметр, чтобы указать дату и время, до которого был использован командлет.</span><span class="sxs-lookup"><span data-stu-id="0a838-118">Implement this parameter to specify the date and time before which the cmdlet was used.</span></span> <span data-ttu-id="0a838-119">Чтобы параметр **Before** работал, командлет также должен иметь **доступный**, **созданный**или **измененный** параметр.</span><span class="sxs-lookup"><span data-stu-id="0a838-119">For the **Before** parameter to work, the cmdlet must also have an **Accessed**, **Created**, or **Modified** parameter.</span></span> <span data-ttu-id="0a838-120">И этот параметр должен иметь значение **true** при вызове командлета.</span><span class="sxs-lookup"><span data-stu-id="0a838-120">And, that parameter must be set to **true** when the cmdlet is called.</span></span>|
|<span data-ttu-id="0a838-121">**Создан**</span><span class="sxs-lookup"><span data-stu-id="0a838-121">**Created**</span></span><br><span data-ttu-id="0a838-122">Тип данных: переключатель</span><span class="sxs-lookup"><span data-stu-id="0a838-122">Data type: SwitchParameter</span></span>|<span data-ttu-id="0a838-123">Реализуйте этот параметр, чтобы при указании командлета он работал с ресурсами, созданными на основе даты и времени, указанных в параметрах **Before** и **After** .</span><span class="sxs-lookup"><span data-stu-id="0a838-123">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been created based on the date and time specified by the **Before** and **After** parameters.</span></span> <span data-ttu-id="0a838-124">Если этот параметр указан, параметры, **Доступные** и **измененные** , не должны быть указаны.</span><span class="sxs-lookup"><span data-stu-id="0a838-124">If this parameter is specified, the **Accessed** and **Modified** parameters must not be specified.</span></span>|
|<span data-ttu-id="0a838-125">**Потребностей**</span><span class="sxs-lookup"><span data-stu-id="0a838-125">**Exact**</span></span><br><span data-ttu-id="0a838-126">Тип данных: переключатель</span><span class="sxs-lookup"><span data-stu-id="0a838-126">Data type: SwitchParameter</span></span>|<span data-ttu-id="0a838-127">Реализуйте этот параметр, чтобы указать, что при указании термин ресурса должен точно совпадать с именем ресурса.</span><span class="sxs-lookup"><span data-stu-id="0a838-127">Implement this parameter so that when it is specified the resource term must match the resource name exactly.</span></span> <span data-ttu-id="0a838-128">Если параметр не указан, термин ресурса и имя не должны точно совпадать.</span><span class="sxs-lookup"><span data-stu-id="0a838-128">When the parameter is not specified the resource term and name do not need to match exactly.</span></span>|
|<span data-ttu-id="0a838-129">**Изменения**</span><span class="sxs-lookup"><span data-stu-id="0a838-129">**Modified**</span></span><br><span data-ttu-id="0a838-130">Тип данных: DateTime</span><span class="sxs-lookup"><span data-stu-id="0a838-130">Data type: DateTime</span></span>|<span data-ttu-id="0a838-131">Реализуйте этот параметр, чтобы при указании командлета он работал с ресурсами, которые были изменены в зависимости от даты и времени, указанных в параметрах **Before** и **After** .</span><span class="sxs-lookup"><span data-stu-id="0a838-131">Implement this parameter so that when it is specified the cmdlet will operate on resources that have been changed based on the date and time specified by the **Before** and **After** parameters.</span></span> <span data-ttu-id="0a838-132">Если этот параметр указан, то **доступ к** параметрам и **созданные** параметры указывать не нужно.</span><span class="sxs-lookup"><span data-stu-id="0a838-132">If this parameter is specified, the **Accessed** and **Created** parameters must not be specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="0a838-133">См. также:</span><span class="sxs-lookup"><span data-stu-id="0a838-133">See Also</span></span>

[<span data-ttu-id="0a838-134">Параметры командлета</span><span class="sxs-lookup"><span data-stu-id="0a838-134">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="0a838-135">Запись командлета Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a838-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="0a838-136">Пакет SDK для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a838-136">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)