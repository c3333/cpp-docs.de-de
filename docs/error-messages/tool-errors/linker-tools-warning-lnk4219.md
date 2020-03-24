---
title: Linkertoolwarnung LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 4488539a4f7282180048f1e3530e62e35c3b339e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183097"
---
# <a name="linker-tools-warning-lnk4219"></a>Linkertoolwarnung LNK4219

Fixup-namens Korrektur Überlauf. Der Ziel Symbol Name "target" liegt außerhalb des gültigen Bereichs, wobei Thunk eingefügt werden.

Der Linker hat einen Thunk in eine Situation eingefügt, in der die Adresse oder der Offset nicht in die angegebene Anweisung passt, weil das Ziel Symbol zu weit vom Speicherort der Anweisung entfernt wurde.

Möglicherweise möchten Sie das Abbild neu anordnen (z. b. mithilfe der [/Order](../../build/reference/order-put-functions-in-order.md) -Option), um den zusätzlichen Dereferenzierungsebene zu vermeiden.
