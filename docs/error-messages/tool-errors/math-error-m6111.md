---
title: Mathematischer Fehler M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: e8abedf6a326a826d0c8ac513b15037c8bf89bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173690"
---
# <a name="math-error-m6111"></a>Mathematischer Fehler M6111

Stapel Unterlauf

Ein Gleit Komma Vorgang führte zu einem Stapel Unterlauf für den 8087/287/387-Coprozessor oder den Emulator.

Dieser Fehler wird häufig durch einen aufzurufenden `long double` Funktion verursacht, die keinen Wert zurückgibt. Im folgenden Beispiel wird dieser Fehler generiert, wenn kompiliert und ausgeführt wird:

```
long double ld() {};
main ()
{
  ld();
}
```

Das Programm endet mit dem Exitcode 139.
