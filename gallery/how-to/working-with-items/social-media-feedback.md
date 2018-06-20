---
ms.date: 06/12/2017
contributor: JKeithB
keywords: коллекции,powershell,командлет,psgallery
title: Отправка отзывов через социальные сети или комментарии
ms.openlocfilehash: a8e6097de4a565b504189b0b0488c45b6d78a8b6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Отправка отзывов через социальные сети или комментарии

Коллекция Powershell предоставляет пользователям два способа отправки общедоступных отзывов по элементу:

- Ссылки слева на странице, чтобы поделиться элементом в социальных сетях Facebook, LinkedIn и Twitter.
- Функция комментариев, чтобы опубликовать комментарии к элементу и сделать их доступными для авторов опубликованных компонентов.

## <a name="social-media-feedback"></a>Отзывы в социальных сетях

На каждый элемент в коллекции PowerShell есть ссылки для Facebook, LinkedIn и Twitter в левой части страницы.
Если вы щелкнете их, откроется сайт социальной сети и вы сможете быстро поделиться ссылкой на этот элемент.

Пользователям необходимо войти на сайт, на котором они хотят поделиться элементом коллекции PowerShell.

Мы рекомендуем делать это, если пользователь считает, что следует посоветовать этот элемент другим пользователям.
Коллекция PowerShell проверяет, сколько раз элемент был "рекомендован" на каждом сайте социальной сети, и отображает эти данные по элементу для каждого сайта социальной сети.
Так как отображается только количество рекомендаций, другие пользователи воспримут это как отметку "Нравится".


## <a name="comments"></a>Комментарии

Коллекции PowerShell используют службу LiveFyre, чтобы позволить пользователям комментировать элементы.
Пользователи, у которых есть советы или отзывы, могут использовать эту функцию, чтобы предоставить отзыв, который виден всем, кто посещает страницу элемента.
Владельцы элемента могут подписаться на этот отзыв и получать уведомления, когда кто-то публикует комментарий.

Система комментариев основана на отдельной службе LiveFyre. Этой службой не управляет корпорация Майкрософт, и она требует использования уникального имени для входа.
Когда вы решите впервые оставить комментарий или подписаться на комментарии к одному из своих элементов, вам будет предложено создать учетную запись LiveFyre.

Если вы создали учетную запись LiveFyre и вошли в систему, вы можете создать комментарий с отзывом об элементе, а затем щелкнуть "Опубликовать комментарий...". Комментарий появится не сразу.
Комментарии к элементам коллекции модерируют администраторы коллекции PowerShell. Модераторы просматривают все сообщения перед их публикацией и отображением для других пользователей.
Наша цель при модерировании комментариев состоит в том, чтобы они соответствовали нормам общественного поведения согласно [условиям использования](https://www.powershellgallery.com/policies/Terms) коллекции PowerShell.

Мы рекомендуем владельцам элементов подписываться на комментарии, которые публикуются в LiveFyre.
Для этого необходима учетная запись LiveFyre. Мы советуем использовать тот же адрес электронной почты, который используется при публикации элемента в LiveFyre.
Чтобы подписаться на комментарии, зайдите в LiveFyre и перейдите к любому элементу, где вы числитесь владельцем.
Под полем комментариев под каждым элементом вы увидите кнопку "+Подписаться".
После того как вы щелкните ее, LiveFyre будет отправлять письмо по зарегистрированному адресу электронной почты каждый раз, когда будут публиковаться новые комментарии к элементу.