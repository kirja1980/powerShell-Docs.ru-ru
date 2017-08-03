---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,установка"
ms.openlocfilehash: d23cfc2aaa680c247aaab91d8875c64c9d62187e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2017
---
# <a name="archive-cmdlets"></a><span data-ttu-id="bf328-102">Командлеты Archive</span><span class="sxs-lookup"><span data-stu-id="bf328-102">Archive cmdlets</span></span>

<span data-ttu-id="bf328-103">Два новых командлета **Compress-Archive** и **Expand-Archive** позволяют сжимать и распаковывать ZIP-файлы.</span><span class="sxs-lookup"><span data-stu-id="bf328-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="bf328-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="bf328-104">Compress-Archive</span></span>
<span data-ttu-id="bf328-105">Командлет **Compress-Archive** создает новый файл архива из указанных файлов.</span><span class="sxs-lookup"><span data-stu-id="bf328-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="bf328-106">Файл архива позволяет упаковать и при необходимости сжать несколько файлов в один для упрощения обработки и хранения.</span><span class="sxs-lookup"><span data-stu-id="bf328-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="bf328-107">Файл архива можно сжать с помощью алгоритма, указанного в параметре **-CompressionLevel**.</span><span class="sxs-lookup"><span data-stu-id="bf328-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```PowerShell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="bf328-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="bf328-108">Expand-Archive</span></span>
<span data-ttu-id="bf328-109">Командлет **Expand-Archive** извлекает файлы из указанного файла архива.</span><span class="sxs-lookup"><span data-stu-id="bf328-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="bf328-110">Файл архива позволяет упаковать и при необходимости сжать несколько файлов в один для упрощения обработки и хранения.</span><span class="sxs-lookup"><span data-stu-id="bf328-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```PowerShell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
