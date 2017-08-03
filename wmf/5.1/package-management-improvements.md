---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,установка"
contributor: jianyunt, quoctruong
title: "Усовершенствования в управлении пакетами в WMF 5.1"
ms.openlocfilehash: b55a1742530b7cd48d60d79b7d4866ebee80a3b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-package-management-in-wmf-51"></a><span data-ttu-id="cf778-103">Усовершенствования в управлении пакетами в WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="cf778-103">Improvements to Package Management in WMF 5.1#</span></span>

## <a name="improvements-in-packagemanagement"></a><span data-ttu-id="cf778-104">Усовершенствования в управлении пакетами</span><span class="sxs-lookup"><span data-stu-id="cf778-104">Improvements in PackageManagement</span></span> ##
<span data-ttu-id="cf778-105">Ниже перечислены исправления, внесенные в WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="cf778-105">The following are the fixes made in the WMF 5.1:</span></span> 

### <a name="version-alias"></a><span data-ttu-id="cf778-106">Псевдоним версии</span><span class="sxs-lookup"><span data-stu-id="cf778-106">Version Alias</span></span>

<span data-ttu-id="cf778-107">**Ситуация**. Если в системе установлены версии 1.0 и 2.0 пакета P1 и вы хотите удалить версию 1.0, вы выполняете команду `Uninstall-Package -Name P1 -Version 1.0`. При этом вы ожидаете, что после выполнения командлета будет удалена версия 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf778-107">**Scenario**: If you have version 1.0 and 2.0 of a package, P1, installed on your system, and you want to uninstall version 1.0, you would run `Uninstall-Package -Name P1 -Version 1.0` and expect version 1.0 to be uninstalled after running the cmdlet.</span></span> <span data-ttu-id="cf778-108">Но в результате удаляется версия 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf778-108">However the result is that version 2.0 gets uninstalled.</span></span>  
    
<span data-ttu-id="cf778-109">Это происходит потому, что параметр `-Version` является псевдонимом параметра `-MinimumVersion`.</span><span class="sxs-lookup"><span data-stu-id="cf778-109">This occurs because the `-Version` parameter is an alias of the `-MinimumVersion` parameter.</span></span> <span data-ttu-id="cf778-110">Когда модуль PackageManagement ищет подходящий пакет с минимальной версией 1.0, он возвращает последнюю версию.</span><span class="sxs-lookup"><span data-stu-id="cf778-110">When PackageManagement is looking for a qualified package with the minimum version of 1.0, it returns the latest version.</span></span> <span data-ttu-id="cf778-111">Такое поведение является нормальным в большинстве случаев, так как обычно требуется найти именно последнюю версию.</span><span class="sxs-lookup"><span data-stu-id="cf778-111">This behavior is expected in normal cases because finding the latest version is usually the desired result.</span></span> <span data-ttu-id="cf778-112">Но в случае с `Uninstall-Package` ситуация иная.</span><span class="sxs-lookup"><span data-stu-id="cf778-112">However, it should not apply to the `Uninstall-Package` case.</span></span>
    
<span data-ttu-id="cf778-113">**Решение**. Полностью удалить псевдоним `-Version` в PackageManagement (так называемом</span><span class="sxs-lookup"><span data-stu-id="cf778-113">**Solution**:removed `-Version` alias entirely in PackageManagement (a.k.a.</span></span> <span data-ttu-id="cf778-114">OneGet) и PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="cf778-114">OneGet) and PowerShellGet.</span></span> 

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a><span data-ttu-id="cf778-115">Несколько запросов на начальную загрузку поставщика NuGet</span><span class="sxs-lookup"><span data-stu-id="cf778-115">Multiple prompts for bootstrapping the NuGet provider</span></span>

<span data-ttu-id="cf778-116">**Ситуация**. При первом выполнении командлета `Find-Module`, `Install-Module` или других командлетов PackageManagement на компьютере модуль PackageManagement пытается выполнить начальную загрузку поставщика NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf778-116">**Scenario**: When you run `Find-Module` or `Install-Module` or other PackageManagement cmdlets on your computer for the first time, PackageManagement tries to bootstrap the NuGet provider.</span></span> <span data-ttu-id="cf778-117">Связано это с тем, что поставщик PowershellGet также использует поставщик NuGet для скачивания модулей PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf778-117">It does this because the PowerShellGet provider also uses the NuGet provider to download PowerShell modules.</span></span> <span data-ttu-id="cf778-118">Затем модуль PackageManagement запрашивает у пользователя разрешение на установку поставщика NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf778-118">PackageManagement then prompts the user for permission to install the NuGet provider.</span></span> <span data-ttu-id="cf778-119">После того как пользователь разрешает начальную загрузку, устанавливается последняя версия поставщика NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf778-119">After the user selects "yes" for the bootstrapping, the latest version of the NuGet provider will be installed.</span></span> 
    
<span data-ttu-id="cf778-120">Но если на компьютере установлена старая версия поставщика NuGet, она иногда может загружаться первой в сеанс PowerShell (и в PackageManagement возникает состояние гонки).</span><span class="sxs-lookup"><span data-stu-id="cf778-120">However, in some cases, when you have an old version of NuGet provider installed on your computer, the older version of NuGet sometimes gets loaded first into the PowerShell session (that's the race condition in PackageManagement).</span></span> <span data-ttu-id="cf778-121">Но модуль PowerShellGet требует, чтобы работала последняя версия поставщика NuGet, поэтому он еще раз запрашивает начальную загрузку поставщика NuGet у модуля PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="cf778-121">However PowerShellGet requires the later version of the NuGet provider to work, so PowerShellGet asks PackageManagement to bootstrap the NuGet provider again.</span></span> <span data-ttu-id="cf778-122">Это приводит к выводу нескольких запросов на начальную загрузку поставщика NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf778-122">This results in multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="cf778-123">**Решение**. В WMF 5.1 модуль PackageManagement теперь загружает последнюю версию поставщика NuGet во избежание вывода нескольких запросов на начальную загрузку поставщика NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf778-123">**Solution**: In WMF5.1, PackageManagement loads the latest version of the NuGet provider to avoid multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="cf778-124">Также имеется обходной путь: вы можете вручную удалить старую версию поставщика NuGet (NuGet-Anycpu.exe), если она существует, из папок $env:ProgramFiles\PackageManagement\ProviderAssemblies и $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span><span class="sxs-lookup"><span data-stu-id="cf778-124">You could also work around this issue by manually deleting the old version of the NuGet provider (NuGet-Anycpu.exe) if exists from $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span></span>


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a><span data-ttu-id="cf778-125">Поддержка PackageManagement на компьютерах с доступом только к интрасети</span><span class="sxs-lookup"><span data-stu-id="cf778-125">Support for PackageManagement on computers with Intranet access only</span></span>

<span data-ttu-id="cf778-126">**Ситуация**. В средах предприятий у пользователей может быть доступ только к интрасети, но не к Интернету.</span><span class="sxs-lookup"><span data-stu-id="cf778-126">**Scenario**: For the enterprise scenario, people are working under an environment where there is no Internet access but Intranet only.</span></span> <span data-ttu-id="cf778-127">Модуль PackageManagement не поддерживал такую ситуацию в WMF 5.0.</span><span class="sxs-lookup"><span data-stu-id="cf778-127">PackageManagement did not support this case in WMF 5.0.</span></span>

<span data-ttu-id="cf778-128">**Ситуация**. В WMF 5.0 модуль PackageManagement не поддерживался на компьютерах с доступом только к интрасети (но не к Интернету).</span><span class="sxs-lookup"><span data-stu-id="cf778-128">**Scenario**: In WMF 5.0, PackageManagement did not support computers that have only Intranet (but not Internet) access.</span></span>

<span data-ttu-id="cf778-129">**Решение**. Чтобы обеспечить использование PackageManagement на компьютерах в интрасети, в WMF 5.1 можно выполнить указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="cf778-129">**Solution**: In WMF 5.1, you can follow these steps to allow Intranet computers to use PackageManagement:</span></span>

1. <span data-ttu-id="cf778-130">Скачайте поставщик NuGet с другого компьютера, имеющего подключение к Интернету, выполнив команду `Install-PackageProvider -Name NuGet`.</span><span class="sxs-lookup"><span data-stu-id="cf778-130">Download the NuGet provider using another computer that has an Internet connection by using `Install-PackageProvider -Name NuGet`.</span></span>

2. <span data-ttu-id="cf778-131">Поставщик NuGet находится в `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` или `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span><span class="sxs-lookup"><span data-stu-id="cf778-131">Find the NuGet provider under either `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget`  or  `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span></span>

3. <span data-ttu-id="cf778-132">Скопируйте двоичные файлы в папку или сетевую папку, к которой есть доступ у компьютера в интрасети, и установите поставщик NuGet, выполнив команду `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span><span class="sxs-lookup"><span data-stu-id="cf778-132">Copy the binaries to a folder or network share location that the Intranet computer can access, and then install the NuGet provider with `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span></span>


### <a name="event-logging-improvements"></a><span data-ttu-id="cf778-133">Усовершенствования, касающиеся ведения журнала событий</span><span class="sxs-lookup"><span data-stu-id="cf778-133">Event logging improvements</span></span>

<span data-ttu-id="cf778-134">При установке пакетов состояние компьютера меняется.</span><span class="sxs-lookup"><span data-stu-id="cf778-134">When you install packages, you are changing the state of the computer.</span></span> <span data-ttu-id="cf778-135">В WMF 5.1 модуль PackageManagement записывает события в журнал событий Windows для действий `Install-Package`, `Uninstall-Package` и `Save-Package`.</span><span class="sxs-lookup"><span data-stu-id="cf778-135">In WMF 5.1, PackageManagement now logs events to the Windows event log for `Install-Package`, `Uninstall-Package`, and `Save-Package` activities.</span></span> <span data-ttu-id="cf778-136">Журнал событий совпадает с журналом событий для PowerShell, т. е. `Microsoft-Windows-PowerShell, Operational`.</span><span class="sxs-lookup"><span data-stu-id="cf778-136">The Event log  is the same as for PowerShell, that is, `Microsoft-Windows-PowerShell, Operational`.</span></span>

### <a name="support-for-basic-authentication"></a><span data-ttu-id="cf778-137">Поддержка обычной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="cf778-137">Support for basic authentication</span></span>

<span data-ttu-id="cf778-138">В WMF 5.1 модуль PackageManagement поддерживает поиск и установку пакетов из репозитория, требующего обычной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="cf778-138">In WMF 5.1, PackageManagement supports finding and installing packages from a repository that requires basic authentication.</span></span> <span data-ttu-id="cf778-139">Можно указать учетные данные в командлетах `Find-Package` и `Install-Package`.</span><span class="sxs-lookup"><span data-stu-id="cf778-139">You can supply your credentials to the `Find-Package` and `Install-Package` cmdlets.</span></span> <span data-ttu-id="cf778-140">Например:</span><span class="sxs-lookup"><span data-stu-id="cf778-140">For example:</span></span>

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a><span data-ttu-id="cf778-141">Поддержка использования PackageManagement через прокси-сервер</span><span class="sxs-lookup"><span data-stu-id="cf778-141">Support for using PackageManagement behind a proxy</span></span>

<span data-ttu-id="cf778-142">В WMF 5.1 модуль PackageManagement принимает новые параметры прокси-сервера, `-ProxyCredential` и `-Proxy`.</span><span class="sxs-lookup"><span data-stu-id="cf778-142">In WMF 5.1, PackageManagement now takes new proxy parameters `-ProxyCredential` and `-Proxy`.</span></span> <span data-ttu-id="cf778-143">В этих параметрах можно указать URL-адрес и учетные данные прокси-сервера для командлетов PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="cf778-143">Using these parameters, you can specify the proxy URL and credentials to PackageManagement cmdlets.</span></span> <span data-ttu-id="cf778-144">По умолчанию используются системные настройки прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="cf778-144">By default, system proxy settings are used.</span></span> <span data-ttu-id="cf778-145">Например:</span><span class="sxs-lookup"><span data-stu-id="cf778-145">For example:</span></span>

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
