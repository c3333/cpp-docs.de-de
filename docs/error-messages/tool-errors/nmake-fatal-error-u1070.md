---
title: 'NMAKE: Schwerwiegender Fehler U1070'
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 008d49df3460cb7cf760e4b278db20da444555fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182772"
---
# <a name="nmake-fatal-error-u1070"></a>NMAKE: Schwerwiegender Fehler U1070

Cycle in Makro Definition "macroname"

Die angegebene Makro Definition enthielt ein Makro, dessen Definition das angegebene Makro enthielt. Die zirkulären Makro Definitionen sind ungültig.

## <a name="example"></a>Beispiel

Die folgenden Makro Definitionen

```
ONE=$(TWO)
TWO=$(ONE)
```

Führen Sie den folgenden Fehler aus:

```
cycle in macro definition 'TWO'
```
