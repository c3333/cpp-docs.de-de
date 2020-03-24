---
title: Linkertoolwarnung LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 43fae7d0f19f96998d2e1a1739bc3e596bbd9ea9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194199"
---
# <a name="linker-tools-warning-lnk4037"></a>Linkertoolwarnung LNK4037

>'*Symbol*' ist nicht vorhanden. erten

Das ergänzte namens *Symbol* konnte nicht mithilfe der Option [/Order](../../build/reference/order-put-functions-in-order.md) geordnet werden, da es nicht im Programm gefunden werden konnte. Überprüfen Sie die Spezifikation des *Symbols* in der Auftrags Antwortdatei. Weitere Informationen finden Sie in der Linkeroption [/Order (in Reihenfolge einfügen)](../../build/reference/order-put-functions-in-order.md) .

> [!NOTE]
> Der Link kann keine statischen Funktionen Sortieren, da statische Funktionsnamen keine öffentlichen Symbolnamen sind. Wenn **/Order** angegeben wird, wird diese Linker-Warnung für jedes Symbol in der Auftrags Antwortdatei generiert, das entweder statisch ist oder nicht gefunden wurde.
