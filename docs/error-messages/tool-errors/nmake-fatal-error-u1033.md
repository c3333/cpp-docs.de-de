---
title: 'NMAKE: Schwerwiegender Fehler U1033'
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 4511b15c84479c3531a3bea85964e2768de0181f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173386"
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE: Schwerwiegender Fehler U1033

Syntax Fehler: "String" ist unerwartet.

Die Zeichenfolge ist nicht Teil der gültigen Syntax für ein Makefile.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Wenn sich der schließende Satz von spitzen Klammern ( **<<** ) für eine Inline Datei nicht am Anfang einer Zeile befindet, tritt der folgende Fehler auf:

    ```
    syntax error : 'EOF' unexpected
    ```

1. Wenn eine Makro Definition in Makefile ein Gleichheitszeichen ( **=** ) ohne einen vorangehenden Namen enthielt oder wenn der definierte Name ein Makro ist, das zu "Nothing" erweitert wird, tritt der folgende Fehler auf:

    ```
    syntax error : '=' unexpected
    ```

1. , Wenn sich das Semikolon ( **;** ) in einer Kommentarzeile in den-Tools befinden. Die ini befindet sich nicht am Anfang der Zeile, der folgende Fehler tritt auf:

    ```
    syntax error : ';' unexpected
    ```

1. Wenn Makefile von einem Textprozessor formatiert wurde, kann der folgende Fehler auftreten:

    ```
    syntax error : ':' unexpected
    ```
