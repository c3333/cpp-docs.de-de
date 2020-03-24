---
title: 'NMAKE: Schwerwiegender Fehler U1059'
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 33be3312e1f0aaa7f1e8aad64b44ea9aefd25346
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182837"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE: Schwerwiegender Fehler U1059

> Syntax Fehler: "}" fehlt in Abhängigkeit.

Ein Suchpfad für einen abhängigen wurde falsch angegeben. Es wurde entweder ein Leerzeichen im Pfad oder die schließende geschweifte Klammer ( **}** ) ausgelassen.

Die Syntax für eine Verzeichnis Spezifikation für einen abhängigen ist

> **{** *Directories* **} abhängig**

Where- *Verzeichnisse* gibt einen oder mehrere Pfade an, die jeweils durch ein Semikolon ( **;** ) getrennt sind. Es sind keine Leerzeichen zulässig.

Wenn ein Teil oder ein anderer Suchpfad durch ein Makro ersetzt wird, stellen Sie sicher, dass keine Leerzeichen in der Makro Erweiterung vorhanden sind.
