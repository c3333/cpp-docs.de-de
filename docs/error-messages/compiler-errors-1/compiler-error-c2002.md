---
title: Compilerfehler C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: c37a9b94be837248c8025a4fc069d8a242128542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208246"
---
# <a name="compiler-error-c2002"></a>Compilerfehler C2002

Ungültige breit Zeichen Konstante.

Die Multibyte-Zeichen Konstante ist ungültig.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Die breit Zeichen Konstante enthält mehr Bytes als erwartet.

1. Der Standard Header STDDEF. h ist nicht eingeschlossen.

1. Breit Zeichen können nicht mit normalen Zeichenfolgenliteralen verkettet werden.

1. Einer breit Zeichen Konstante muss das Zeichen ' L ' vorangestellt sein:

    ```
    L'mbconst'
    ```

1. Für Microsoft C++müssen die Textargumente einer Präprozessordirektive ASCII sein. Beispielsweise ist die-Direktive, `#pragma message(L"string")`, ungültig.
