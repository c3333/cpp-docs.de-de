---
title: Linkertoolwarnung LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: fda1fdb03a7629894f846bb20ed84df519239327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183305"
---
# <a name="linker-tools-warning-lnk4102"></a>Linkertoolwarnung LNK4102

Export des Lösch Dekonstruktors ' Name '; Image wird möglicherweise nicht ordnungsgemäß ausgeführt

Das Programm hat versucht, einen Lösch Dekonstruktor zu exportieren. Der resultierende Löschvorgang kann über eine DLL-Grenze erfolgen, sodass ein Prozess Arbeitsspeicher freigeben kann, der nicht der Besitzer ist. Stellen Sie sicher, dass das angegebene Symbol nicht in der DEF-Datei aufgeführt ist und dass das Symbol nicht als Argument der Option **/Import** oder **/Export** in der Linkerbefehlszeile aufgeführt ist.

Wenn Sie die C-Lauf Zeit Bibliothek neu erstellen, können Sie diese Meldung ignorieren.
