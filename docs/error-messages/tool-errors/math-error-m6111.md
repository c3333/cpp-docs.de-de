---
title: Mathematischer Fehler M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 986c0e53edcddfc47eb9ba970f3c32385e0a57d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225188"
---
# <a name="math-error-m6111"></a>Mathematischer Fehler M6111

Stapel Unterlauf

Ein Gleit Komma Vorgang führte zu einem Stapel Unterlauf für den 8087/287/387-Coprozessor oder den Emulator.

Dieser Fehler tritt häufig auf, wenn eine Funktion aufgerufen wird **`long double`** , die keinen Wert zurückgibt. Im folgenden Beispiel wird dieser Fehler generiert, wenn kompiliert und ausgeführt wird:

```
long double ld() {};
main ()
{
  ld();
}
```

Das Programm endet mit dem Exitcode 139.
