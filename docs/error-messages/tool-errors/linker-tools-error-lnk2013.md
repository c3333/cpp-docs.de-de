---
title: Linkertoolfehler LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 6ad3f40f06e64422b393edb457a0dcf419828b6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194745"
---
# <a name="linker-tools-error-lnk2013"></a>Linkertoolfehler LNK2013

Fixup-Typ Fixup-Überlauf. Ziel 'Symbolname' ist außerhalb des Bereichs

Der Linker kann die erforderliche Adresse bzw. den Offset in die angegebene Anweisung nicht finden, da die Entfernung zwischen Zielsymbol und Anweisung zu groß ist.

Sie können dieses Problem beheben, indem Sie mehrere Images erstellen oder indem Sie die Option [/Order](../../build/reference/order-put-functions-in-order.md) verwenden, damit sich die Anweisung und das Ziel näher beieinander befinden.

Wenn der Symbolname ein benutzerdefiniertes (und kein vom Compiler generiertes) Symbol ist, können Sie auch versuchen, den Fehler mithilfe der folgenden Maßnahmen zu beheben:

- Ändern Sie die statische Funktion in eine nicht statische Funktion.

- Benennen Sie den Codeabschnitt mit der statischen Funktion um, sodass er dem Namen des Aufrufers entspricht.

Überprüfen Sie mit `DUMPBIN /SYMBOLS`, ob eine Funktion statisch ist.
