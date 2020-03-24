---
title: 'NMAKE: Schwerwiegender Fehler U1035'
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 3eda424574dfa48901cf4dc6aea3b28beb739dc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193718"
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE: Schwerwiegender Fehler U1035

Syntax Fehler: das Trennzeichen ': ' oder ' = ' wurde erwartet.

Es wurde entweder ein Doppelpunkt ( **:** ) oder ein Gleichheitszeichen ( **=** ) erwartet.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Ein Doppelpunkt hat nicht auf ein Ziel folgt.

1. Ein Doppelpunkt und kein Leerzeichen (z. b. ein:) folgte einem Ziel mit nur einem Buchstaben. NMAKE interpretiert ihn als Laufwerk Spezifikation.

1. Ein Doppelpunkt hat nicht auf eine Rückschluss Regel folgen.

1. Auf eine Makro Definition folgt kein Gleichheitszeichen.

1. Ein Zeichen gefolgt von einem umgekehrten Schrägstrich ( **\\** ), der zum Fortsetzen eines Befehls in eine neue Zeile verwendet wurde.

1. Eine Zeichenfolge, die keiner NMAKE-Syntax Regel entsprach, ist aufgetreten.

1. Das Makefile wurde von einem Textprozessor formatiert.
