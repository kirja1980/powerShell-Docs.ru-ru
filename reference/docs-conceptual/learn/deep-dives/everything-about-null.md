---
title: Все, что нужно знать о $null
description: В PowerShell состояние $null часто кажется простым, но оно имеет много нюансов. Давайте подробно рассмотрим $null и выясним, что означает неожиданное получение значения NULL.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149477"
---
# <a name="everything-you-wanted-to-know-about-null"></a>Все, что нужно знать о $null

В PowerShell состояние `$null` часто кажется простым, но оно имеет много нюансов. Давайте подробно рассмотрим `$null` и выясним, что означает неожиданное получение значения `$null`.

> [!NOTE]
> [Оригинал статьи][] этой статьи впервые был опубликован в блоге автора [@KevinMarquette][]. Команда разработчиков PowerShell благодарит Кевина за то, что он поделился с нами этим материалом. Читайте его блог — [PowerShellExplained.com][].

## <a name="what-is-null"></a>Что означает NULL

Значение NULL можно считать неизвестным или пустым значением. Переменная имеет значение NULL, пока ей не присвоено значение или объект. Это важный момент, так как некоторые команды требуют значения и возвращают ошибку, если значением является NULL.

### <a name="powershell-null"></a>$null в PowerShell

`$null` — это автоматическая переменная в PowerShell, используемая для представления значения NULL. Ее можно назначать переменным и использовать в сравнениях, а также в качестве заполнителя для значения NULL в коллекции.

В PowerShell `$null` считается объектом со значением NULL, что отличается от трактовки этого понятия в других языках.

## <a name="examples-of-null"></a>Примеры использования $null

Всякий раз, когда вы пытаетесь использовать переменную, которая не была инициализирована, ее значением будет `$null`. Это одна из самых распространенных причин, по которой значения `$null` появляются в коде.

```powershell
PS> $null -eq $undefinedVariable
True
```

Если вы неправильно указали имя переменной, PowerShell не распознает ее и присвоит ей значение `$null`.

Значения `$null` также появляются при выполнении команд, которые не выдают результатов.

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a>Интерпретация $null

Значения `$null` обрабатываются в коде по-разному, в зависимости от того, где они находятся.

### <a name="in-strings"></a>В строках

Если в строке используется `$null`, то это пустое значение (или пустая строка).

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

Это одна из причин, по которой я предпочитаю заключать переменные в скобки при их использовании в сообщениях журнала. Если значение находится в конце строки, это также помогает обнаружить границы значений переменных.

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

Так можно легко обнаружить пустые строки и значения `$null`.

### <a name="in-numeric-equation"></a>В числовом уравнении

Когда значение `$null` используется в числовом уравнении, результаты будут недействительными, если не будет возвращена ошибка. Иногда `$null` значит `0`, но в других случаях полученный результат будет приравнен к `$null`.
Ниже приведен пример с умножением, результатом которого может быть как 0, так и `$null` в зависимости от порядка значений.

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a>Вместо коллекции

Коллекция позволяет использовать индекс для доступа к значениям. При попытке индексировать в коллекцию, которая фактически является `null`, вы получите ошибку `Cannot index into a null array`.

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

Если у вас есть коллекция, но вы пытаетесь получить доступ к элементу, который отсутствует в коллекции, вы получите результат `$null`.

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a>Вместо объекта

При попытке доступа к свойству или подсвойству объекта, у которого нет указанного свойства, вы получите значение `$null`, как и в случае доступа к неопределенной переменной. При этом не имеет значения, является ли переменная `$null` или фактическим объектом.

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a>Метод в выражении со значением NULL

Вызов метода для объекта `$null` вызывает исключение `RuntimeException`.

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

Когда я получаю сообщение `You cannot call a method on a null-valued expression`, первое, что я ищу, — это места, где я вызываю метод для переменной без предварительной проверки на соответствие `$null`.

## <a name="checking-for-null"></a>Проверка на соответствие $null

Вы могли заметить, что при проверке на `$null` я всегда указываю `$null` слева в своих примерах. Это сделано специально, как и рекомендуется в PowerShell. Возможны ситуации, когда размещение $null справа не дает ожидаемого результата.

Взгляните на следующий пример и постарайтесь предсказать результаты:

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

Если я не определяю `$value`, результатом первого условия будет `$true`, а мы получим сообщение `The array is $null`. Ловушка заключается в том, что можно создать `$value`, допускающее, чтобы оба условия были `$false`.

```powershell
$value = @( $null )
```

В данном случае `$value` является массивом, содержащим `$null`. `-eq` проверяет каждое значение в массиве и возвращает совпадающее значение `$null`. Результатом этого будет `$false`. `-ne` возвращает все, что не соответствует `$null`, и в этом случае не имеет результата (результатом также будет `$false`). Ни одно из условий не является `$true`, тогда как кажется, что одно из них должно быть таким.

Мы можем не только создать значение, допускающее, чтобы оба условия были `$false`, но и такое, когда оба из них станут `$true`. Матиас Йессен (Mathias Jessen, @IISResetMe) опубликовал [Хорошая статья][] на эту тему.

### <a name="psscriptanalyzer-and-vscode"></a>PSScriptAnalyzer и VSCode

Модуль [PSScriptAnalyzer][] имеет правило для проверки таких коллизий, называющееся `PSPossibleIncorrectComparisonWithNull`.

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

Поскольку VS Code также использует правила PSScriptAnalyser, в редакторе такие фрагменты кода выделяются и считаются проблемой.

### <a name="simple-if-check"></a>Простая проверка if

Проверку на несоответствие значению $null обычно выполняют с помощью простой инструкции `if()` без сравнения.

```powershell
if ( $value )
{
    Do-Something
}
```

Если значение равно `$null`, то результатом будет `$false`. Это выглядит просто, но только на первый взгляд. Я понимаю эту строку кода как:

> Если `$value` имеет значение.

Но это еще не все. На самом деле строка значит следующее:

> Если `$value` не имеет значение `$null`, `0`, `$false` или `empty string`.

Ниже приведен более полный пример этой инструкции.

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

Вполне допустимо использовать базовую проверку `if`, помня не только о значении переменной, но и о том, что другие значения считаются `$false`.

Несколько дней назад я столкнулся с этой проблемой при рефакторинге кода. В нем присутствовала базовая проверка такого типа.

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

Мне было нужно присвоить значение свойству объекта только в том случае, если он существует. В большинстве случаев первоначальному объекту было присвоено значение, для которого возвращался результат `$true` при выполнении `if`. Но я столкнулся с проблемой, когда значение иногда не устанавливалось. Я начал отладку и обнаружил, что у объекта есть свойство, но это пустое строковое значение. Это вообще не позволяло ему обновляться в соответствии с предыдущей логикой. Поэтому я добавил необходимую проверку на соответствие `$null`, и все заработало.

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

Такие мелкие ошибки трудно обнаружить, что научило меня специально проверять значения на соответствие `$null`.

## <a name="nullcount"></a>$null.Count

Если вы попытаетесь получить доступ к свойству по значению `$null`, это свойство также будет `$null`. Свойство `count` является исключением из этого правила.

```powershell
PS> $value = $null
PS> $value.count
0
```

Если у вас есть значение `$null`, то `count` равняется `0`. Это специальное свойство добавляется PowerShell.

### <a name="pscustomobject-count"></a>[PSCustomObject] Count

Почти у всех объектов в PowerShell есть свойство Count. Одним из примечательных исключений является `[PSCustomObject]` в Windows PowerShell 5.1 (что было исправлено в PowerShell 6.0). У него нет свойства Count, поэтому при попытке его использования вы получаете значение `$null`. Я вспомнил это к тому, чтобы вы не пытались использовать `.Count` вместо проверки `$null`.

Выполнение этого примера в Windows PowerShell 5.1 и PowerShell 6.0 дает разные результаты.

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a>Пустое значение NULL

Существует один особый тип `$null`, который отличается от остальных. Я буду называть его пустым значением `$null`, тогда как фактически это [System.Management.Automation.Internal.AutomationNull][]. Такое пустое значение `$null` вы получаете в результате выполнения функции или блока скрипта, которые не возвращают ничего (возвращают void).

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

Если сравнить его с `$null`, вы получите значение `$null`. При использовании в вычислении, где требуется значение, его значение всегда будет `$null`. Но если поместить его в массив, он будет считаться пустым массивом.

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

Можно создать массив с одним значением `$null`, при этом его свойство `count` будет равно `1`. Но если поместить пустой результат в массив, он не будет считаться элементом, а Count будет иметь значение `0`.

Если пустое значение `$null` вы обрабатываете как коллекцию, она будет считаться пустой.

### <a name="pipeline"></a>Pipeline

Различия особенно заметны при работе с конвейером. Вы можете передать в него значение `$null`, но не пустое значение `$null`.

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

В зависимости от кода следует учитывать `$null` в логике.

В любом случае сначала выполните проверку на соответствие `$null`:

- В конвейере отфильтруйте значение NULL(`... | Where {$null -ne $_} | ...`).
- Задайте его обработку с помощью функции конвейера.

## <a name="foreach"></a>foreach

Одна из моих любимых возможностей метода `foreach` — это то, что он не выполняет перечисление по коллекции `$null`.

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

Это избавляет от необходимости проверять коллекцию на соответствие `$null` перед ее перечислением. Если у вас есть коллекция со значениями `$null`, объект `$node` также может иметь значение `$null`.

Оператор foreach начал так работать с версии PowerShell 3.0. Если у вас предыдущая версия, такой режим работы в ней не поддерживается. Это одно из важных отличий, которое необходимо учитывать при обратном портировании кода для совместимости с версией 2.0.

## <a name="value-types"></a>Типы значений

Технически только ссылочные типы могут принимать значение `$null`. Но благодаря стараниям разработчиков PowerShell мы можем указывать любой тип для переменных. Если вы решили строго типизировать значения, задать `$null` не получится.
PowerShell преобразует `$null` в значение по умолчанию для многих типов.

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

У некоторых типов не предусмотрено значение для преобразования из `$null`. Такие типы при обработке вызывают ошибку `Cannot convert null to type`.

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a>Параметры функции

Общепринято использовать строго типизированные значения в параметрах функций. Обычно мы стараемся определять типы параметров, даже если не собираемся определять типы других переменных в скриптах. Возможно, вы сами строго типизировали переменные в функциях, даже не осознавая этого.

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

Как только вы задаете тип параметра `string`, его значение не может быть `$null`. Обычно принято выполнять проверку на соответствие `$null`, чтобы выяснить, предоставил ли пользователь значение.

```powershell
if ( $null -ne $Value ){...}
```

Если значение не указано, `$Value` является пустой строкой `''`. Вместо этого используйте автоматическую переменную `$PSBoundParameters.Value`.

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

`$PSBoundParameters` содержит только параметры, указанные при вызове функции.
Для проверки свойства можно также использовать метод `ContainsKey`.

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a>IsNotNullOrEmpty

Если значение является строкой, можно использовать статическую строковую функцию для проверки того, является ли значение `$null` или пустой строкой одновременно.

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

Я часто так делаю, когда знаю, что тип значения должен быть строкой.

## <a name="when-i-null-check"></a>Когда я выполняю проверку на соответствие $null

Когда я пишу код, то стараюсь предусмотреть все варианты. Вызывая функцию и присваивая ее переменной, я проверяю ее на соответствие `$null`.

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

Я предпочитаю использовать `if` или `foreach`, а не `try/catch`. Не поймите мене неправильно, я часто пользуюсь `try/catch`. Но если я могу задать проверку на состояния ошибки или пустой набор результатов, я могу обеспечить обработку реальных исключений.

Я стараюсь проверять на соответствие `$null` перед индексацией в значение или вызовом методов для объекта. Оба этих действия не срабатывают для объектов `$null`, поэтому сначала нужно их проверить. Эти сценарии уже рассматривались ранее в этой статье.

### <a name="no-results-scenario"></a>Сценарий без результатов

Важно помнить, что разные функции и команды по-разному обрабатывают сценарий без результатов. Многие команды PowerShell возвращают пустое значение `$null` и ошибку в потоке ошибок, тогда как другие вызывают исключения или предоставляют объект состояния. Вам нужно выяснить, как используемые вами команды работают со сценариями без результатов и сценариями ошибок.

## <a name="initializing-to-null"></a>Инициализация значения $null

У меня выработалась привычка инициализировать все переменные перед их использованием. В других языках это обязательно. В начале функции или цикла foreach я определяю все используемые значения.

Вот сценарий, который я советую вам внимательно изучить. Это пример ошибки, которую я однажды выявлял.

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

Здесь предполагается, что `Get-Something` возвращает либо результат, либо пустое значение `$null`. Если возникает ошибка, она регистрируется в журнале. Перед ее обработкой мы проводим проверку, чтобы убедиться в том, что получен допустимый результат.

Ошибка в этом коде возникает, когда `Get-Something` создает исключение и не присваивает `$result` значение. Выполнение кода завершается ошибкой до назначения, поэтому переменной `$result` даже не присваивается значение `$null`. Переменная `$result` сохраняет допустимое значение `$result` из предыдущих итераций.
В этом примере `Update-Something` выполняется несколько раз с одним и тем же объектом.

Устранить проблему мне удалось после того, как я задал `$null` для `$result` прямо в цикле foreach.

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a>Проблемы с областью действия

Это также помогает устранить проблемы, связанные с областью действия функции. В следующем примере мы будем последовательно задавать значения `$result` в цикле. Поскольку PowerShell позволяет значениям переменных, находящимся за пределами функции, попадать в область действия текущей функции, их инициализация в функции снижает вероятность ошибок, которые могут возникать в таких ситуациях.

Неинициализированная переменная в функции не имеет значения `$null`, если ей присвоено значение в родительской области.
Родительской областью может быть другая функция, которая вызывает эту функцию и использует такие же имена переменных.

Если взять тот же пример `Do-something` и удалить из него цикл, то код будет таким:

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

Если вызов `Get-Something` возвращает исключение, тогда проверка на соответствие `$null` найдет `$result` в `Invoke-Something`. Инициализация значения внутри функции устраняет эту ошибку.

Именовать переменные сложно, и разработчики часто используют одинаковые имена переменных в разных функциях. Например, я постоянно использую `$node`,`$result` и `$data`. Из-за этого значения из других областей могут легко появиться в тех местах, где их не должно быть.

## <a name="redirect-output-to-null"></a>Перенаправление вывода в $null

Все вышесказанное касалось значений `$null`, но тема не будет раскрыта, если не объяснить, как перенаправлять выходные данные в `$null`. Бывают команды, выходные данные или объекты которых нужно опустить. Это можно сделать, перенаправив выходные данные в `$null`.

### <a name="out-null"></a>Out-Null

Команда Out-Null — это встроенный способ перенаправления данных конвейера в `$null`.

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a>Назначение в $null

Результатам команды можно назначить значение `$null`, что будет аналогично использованию `Out-Null`.

```powershell
$null = New-Item -Type Directory -Path $path
```

Поскольку `$null` является постоянным значением, перезаписать его нельзя. Мне не нравится такая реализация в коде, но этот способ часто работает быстрее, чем `Out-Null`.

### <a name="redirect-to-null"></a>Перенаправление в $null

Можно также использовать оператор перенаправления для отправки выходных данных в `$null`.

```powershell
New-Item -Type Directory -Path $path > $null
```

Если вы работаете с исполняемыми файлами командной строки, которые выводят данные в различные потоки, вы можете перенаправить все выходные потоки в `$null` следующим образом:

```powershell
git status *> $null
```

## <a name="summary"></a>Сводка

Здесь я много рассказал о $null, но статья получилась несколько отрывочной. Все потому, что значения `$null` могут встречаться повсюду в PowerShell, и их трактовка будет обусловлена конкретным местом. Надеюсь, теперь вы лучше разобрались с `$null` и непонятными ситуациями, где это состояние может повстречаться.

<!-- link references -->
[Оригинал статьи]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Хорошая статья]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
