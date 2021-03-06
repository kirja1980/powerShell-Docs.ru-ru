---
ms.date: 06/12/2017
contributor: JKeithB
keywords: коллекции,powershell,командлет,psgallery
title: Синтаксис поиска по коллекции
ms.openlocfilehash: 9eaabc22090655076dabe177f04130738e081179
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90847006"
---
# <a name="gallery-search-syntax"></a>Синтаксис поиска по коллекции

Выполнять поиск в коллекции PowerShell на [веб-сайте коллекции PowerShell](https://www.powershellgallery.com/). На веб-сайте коллекции PowerShell есть текстовое окно поиска, где можно использовать слова, фразы и выражения с ключевыми словами, чтобы сузить результаты поиска.

## <a name="search-by-keywords"></a>Поиск по ключевым словам

```Syntax
dsc azure sql
```

Поисковая система пытается показать соответствующие документы, содержащие все три ключевые слова.

## <a name="search-using-phrases-and-keywords"></a>Поиск с использованием ключевых слов и фраз

```Syntax
"azure sql" deployment
```

При вводе фразы, заключенной в кавычки (""), выполняется поиск конкретной фразы, а не отдельных ключевых слов. Соответствующие документы обычно содержат точную фразу azure sql, включая варианты (с другим регистром букв, например Azure SQL), а также обычно содержат слово "развертывание".

## <a name="filtering-on-fields"></a>Фильтрация по полям

Вы можете выполнять поиск конкретного идентификатора пакета (ID, Id или id) или других полей, указывая перед условиями поиска имя поля.

В настоящее время для поиска доступны следующие поля: Id, Version, Tags, Author, Owner, Functions, Cmdlets, DscResources и PowerShellVersion.

- Идентификатор — это имя, используемое в консоли.
- Заголовок — это то, что отображается в верхней части страницы пакета в результатах поиска.

## <a name="examples"></a>Примеры

```Syntax
ID:PSReadline
```

Находит пакеты с идентификатором, содержащим PSReadline.

```Syntax
Id:"AzureRM.Profile"
```

— еще один способ поиска пакетов с текстом AzureRM.Profile в поле ID.

Фильтр Id — это сопоставление вложенных строк, поэтому при следующем поиске:

```Syntax
Id:"azure"
```

Этот фильтр выводит результаты, содержащие AzureRM.Profile и Azure.Storage.

можно также выполнить поиск с несколькими ключевыми словами в одном поле;

```Syntax
id:azure tags:intellisense
```

Можно выполнять поиск фраз с использованием двойных кавычек.

```Syntax
id:"azure.storage"
```

Чтобы найти все пакеты с тегом DSC:

```Syntax
Tags:DSC
```

Чтобы найти все пакеты с указанной функцией:

```Syntax
Functions:Get-TreeSize
```

Чтобы найти все пакеты с указанным командлетом:

```Syntax
Cmdlets:Get-AzureRmEnvironment
```

Чтобы найти все пакеты с указанным именем ресурса DSC:

```Syntax
DscResources:xArchive
```

Чтобы найти все пакеты с указанной версией PowerShellVersion:

```Syntax
PowerShellVersion:2.0
```

Наконец, если вы используете поле, которое не поддерживается, например commands, мы просто проигнорируем его и выполним поиск по всем полям. Поэтому следующий запрос

```Syntax
commands:blobs storage
```

интерпретируется точно так же, как этот запрос:

```Syntax
blobs storage
```
