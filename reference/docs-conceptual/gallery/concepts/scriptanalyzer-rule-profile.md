---
ms.date: 06/12/2017
contributor: JKeithB
keywords: коллекции,powershell,командлет,psgallery
title: Профиль правила ScriptAnalyzer для коллекции
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328475"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Профиль правила ScriptAnalyzer для коллекции

Для обеспечения качества пакетов, опубликованных в коллекции PowerShell, запускаются правила [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer), чтобы определить наличие нарушений в отправленных скриптах.

Список правил, выполняемых в ScriptAnalyzer, можно найти на [странице GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
По любым вопросам, связанным с применяемыми правилами, обращайтесь к администраторам коллекции PowerShell или создайте запрос в поддержку ScriptAnalyzer.

Результаты работы ScriptAnalyzer будут отображаться на каждой странице отдельного пакета в коллекции в готовящемся выпуске. Владельцам пакетов рекомендуется проверять опубликованные пакеты на наличие серьезных ошибок.
