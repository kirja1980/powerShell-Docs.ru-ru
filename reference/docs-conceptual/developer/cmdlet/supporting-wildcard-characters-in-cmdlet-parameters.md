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
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="85bf7-102">Поддержка подстановочных знаков в параметрах командлета</span><span class="sxs-lookup"><span data-stu-id="85bf7-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="85bf7-103">Часто приходится проектировать командлет, который будет выполняться для группы ресурсов, а не для отдельного ресурса.</span><span class="sxs-lookup"><span data-stu-id="85bf7-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="85bf7-104">Например, командлету может потребоваться поиск всех файлов в хранилище данных с одинаковым именем или расширением.</span><span class="sxs-lookup"><span data-stu-id="85bf7-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="85bf7-105">При проектировании командлета, который будет выполняться для группы ресурсов, необходимо предоставить поддержку подстановочных знаков.</span><span class="sxs-lookup"><span data-stu-id="85bf7-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="85bf7-106">Использование подстановочных знаков иногда называется *глобализации*.</span><span class="sxs-lookup"><span data-stu-id="85bf7-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="85bf7-107">Командлеты Windows PowerShell, использующие подстановочные знаки</span><span class="sxs-lookup"><span data-stu-id="85bf7-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="85bf7-108">Многие командлеты Windows PowerShell поддерживают подстановочные знаки для значений их параметров.</span><span class="sxs-lookup"><span data-stu-id="85bf7-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="85bf7-109">Например, почти каждый командлет с параметром `Name` или `Path` поддерживает подстановочные знаки для этих параметров.</span><span class="sxs-lookup"><span data-stu-id="85bf7-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="85bf7-110">(Хотя большинство командлетов с параметром `Path` также имеют параметр `LiteralPath`, который не поддерживает подстановочные знаки.) Следующая команда показывает, как использовать подстановочный знак для возврата всех командлетов в текущем сеансе, имя которых содержит команду Get.</span><span class="sxs-lookup"><span data-stu-id="85bf7-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="85bf7-111">Поддерживаемые подстановочные знаки</span><span class="sxs-lookup"><span data-stu-id="85bf7-111">Supported Wildcard Characters</span></span>

<span data-ttu-id="85bf7-112">Windows PowerShell поддерживает следующие подстановочные знаки.</span><span class="sxs-lookup"><span data-stu-id="85bf7-112">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="85bf7-113">Использования</span><span class="sxs-lookup"><span data-stu-id="85bf7-113">Wildcard</span></span> |                             <span data-ttu-id="85bf7-114">Описание</span><span class="sxs-lookup"><span data-stu-id="85bf7-114">Description</span></span>                             |  <span data-ttu-id="85bf7-115">Пример</span><span class="sxs-lookup"><span data-stu-id="85bf7-115">Example</span></span>   |     <span data-ttu-id="85bf7-116">Совпадения</span><span class="sxs-lookup"><span data-stu-id="85bf7-116">Matches</span></span>      | <span data-ttu-id="85bf7-117">Не соответствует</span><span class="sxs-lookup"><span data-stu-id="85bf7-117">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="85bf7-118">Соответствует нулю или большему числу символов, начиная с указанной позиции</span><span class="sxs-lookup"><span data-stu-id="85bf7-118">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="85bf7-119">A, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="85bf7-119">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="85bf7-120">?</span><span class="sxs-lookup"><span data-stu-id="85bf7-120">?</span></span>        | <span data-ttu-id="85bf7-121">Соответствует любому символу в указанной позиции</span><span class="sxs-lookup"><span data-stu-id="85bf7-121">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="85bf7-122">Объект, в, на</span><span class="sxs-lookup"><span data-stu-id="85bf7-122">An, in, on</span></span>       | <span data-ttu-id="85bf7-123">обнаружил</span><span class="sxs-lookup"><span data-stu-id="85bf7-123">ran</span></span>            |
| <span data-ttu-id="85bf7-124">[ ]</span><span class="sxs-lookup"><span data-stu-id="85bf7-124">[ ]</span></span>      | <span data-ttu-id="85bf7-125">Соответствует диапазону символов</span><span class="sxs-lookup"><span data-stu-id="85bf7-125">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="85bf7-126">книга, Кука, взгляд</span><span class="sxs-lookup"><span data-stu-id="85bf7-126">book, cook, look</span></span> | <span data-ttu-id="85bf7-127">Нук, занял</span><span class="sxs-lookup"><span data-stu-id="85bf7-127">nook, took</span></span>     |
| <span data-ttu-id="85bf7-128">[ ]</span><span class="sxs-lookup"><span data-stu-id="85bf7-128">[ ]</span></span>      | <span data-ttu-id="85bf7-129">Соответствует указанным символам</span><span class="sxs-lookup"><span data-stu-id="85bf7-129">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="85bf7-130">книга, Нук</span><span class="sxs-lookup"><span data-stu-id="85bf7-130">book, nook</span></span>       | <span data-ttu-id="85bf7-131">Кука, взгляд</span><span class="sxs-lookup"><span data-stu-id="85bf7-131">cook, look</span></span>     |

<span data-ttu-id="85bf7-132">При проектировании командлетов, поддерживающих символы-шаблоны, можно использовать сочетания символов-шаблонов.</span><span class="sxs-lookup"><span data-stu-id="85bf7-132">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="85bf7-133">Например, следующая команда использует командлет `Get-ChildItem` для получения всех TXT-файлов, которые находятся в папке К:\течдокс и начинаются с букв "a" до "l".</span><span class="sxs-lookup"><span data-stu-id="85bf7-133">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="85bf7-134">Предыдущая команда использует `[a-l]` с подстановочным знаком диапазона, чтобы указать, что имя файла должно начинаться с символов "a" до "l" и использовать подстановочный знак `*` в качестве заполнителя для любых символов между первой буквой имени файла и txt-файлом **.** расширение.</span><span class="sxs-lookup"><span data-stu-id="85bf7-134">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="85bf7-135">В следующем примере используется шаблон шаблона диапазона, который исключает букву "d", но включает все остальные буквы из "a" в "f".</span><span class="sxs-lookup"><span data-stu-id="85bf7-135">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="85bf7-136">Обработка литеральных символов в шаблонах с подстановочными знаками</span><span class="sxs-lookup"><span data-stu-id="85bf7-136">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="85bf7-137">Если указанный шаблон шаблона содержит литеральные символы, которые не должны быть интерпреттед в качестве подстановочных знаков, используйте символ обратной кавычки (`` ` ``) в качестве escape-символа.</span><span class="sxs-lookup"><span data-stu-id="85bf7-137">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="85bf7-138">Если вы указываете литеральные символы int API PowerShell, используйте один обратный символ.</span><span class="sxs-lookup"><span data-stu-id="85bf7-138">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="85bf7-139">При указании литеральных символов в командной строке PowerShell используйте два обратных импульса.</span><span class="sxs-lookup"><span data-stu-id="85bf7-139">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="85bf7-140">Например, следующий шаблон содержит две квадратные скобки, которые должны быть выполнены буквально.</span><span class="sxs-lookup"><span data-stu-id="85bf7-140">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="85bf7-141">При использовании в API PowerShell используется:</span><span class="sxs-lookup"><span data-stu-id="85bf7-141">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="85bf7-142">"Джон Смит \` [\* ']"</span><span class="sxs-lookup"><span data-stu-id="85bf7-142">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="85bf7-143">При использовании из командной строки PowerShell:</span><span class="sxs-lookup"><span data-stu-id="85bf7-143">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="85bf7-144">"Джон Смит \` \` [\* \`"] "</span><span class="sxs-lookup"><span data-stu-id="85bf7-144">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="85bf7-145">Этот шаблон соответствует "Джон Смит [Marketing]" или "Джон Смит [разработка]".</span><span class="sxs-lookup"><span data-stu-id="85bf7-145">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="85bf7-146">Пример:</span><span class="sxs-lookup"><span data-stu-id="85bf7-146">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="85bf7-147">Выходные данные командлета и подстановочные знаки</span><span class="sxs-lookup"><span data-stu-id="85bf7-147">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="85bf7-148">Если параметры командлета поддерживают подстановочные знаки, операция обычно создает выходные данные массива.</span><span class="sxs-lookup"><span data-stu-id="85bf7-148">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="85bf7-149">Иногда не имеет смысла поддерживать выходные данные массива, поскольку пользователь может использовать только один элемент.</span><span class="sxs-lookup"><span data-stu-id="85bf7-149">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="85bf7-150">Например, командлет `Set-Location` не поддерживает вывод массива, поскольку пользователь устанавливает только одно расположение.</span><span class="sxs-lookup"><span data-stu-id="85bf7-150">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="85bf7-151">В этом случае командлет по-прежнему поддерживает подстановочные знаки, но обеспечивает разрешение в одном месте.</span><span class="sxs-lookup"><span data-stu-id="85bf7-151">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="85bf7-152">См. также:</span><span class="sxs-lookup"><span data-stu-id="85bf7-152">See Also</span></span>

[<span data-ttu-id="85bf7-153">Запись командлета Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="85bf7-153">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="85bf7-154">Класс Вилдкардпаттерн</span><span class="sxs-lookup"><span data-stu-id="85bf7-154">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)