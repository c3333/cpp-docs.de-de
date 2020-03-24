---
title: 'Ressourcencompiler: Fehler RC2104'
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: d4a06f88e4a73da6b711d108a1f79c14fae0907c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191638"
---
# <a name="resource-compiler-error-rc2104"></a>Ressourcencompiler: Fehler RC2104

Undefiniertes Schlüsselwort oder Schlüsselname: Schlüssel

Das angegebene Schlüsselwort oder der Schlüsselname ist nicht definiert.

Dieser Fehler wird häufig durch einen Tippfehler in die Definition der Ressource oder in der zugehörigen Header-Datei verursacht. Er kann auch durch eine fehlende Headerdatei verursacht werden.

Um das Problem zu beheben, suchen Sie die Header-Datei, die das definierte Schlüsselwort oder den Schlüsselnamen enthält und stellen Sie sicher, dass er in Ihrer Ressourcendatei enthalten ist und dass das Schlüsselwort oder der Schlüsselname richtig geschrieben ist. Wenn das Projekt mit einem vorkompilierten Header erstellt wurde und Sie es anschließend entfernen, stellen Sie sicher, dass die Ressourcendatei erforderliche Header enthält.

Um die definierten Schlüsselwörter und Schlüsselnamen in der Ressourcen Datei zu überprüfen, öffnen Sie in Visual Studio das Fenster **Ressourcenansicht** – wählen Sie in der Menüleiste **Ansicht**, **Ressourcenansicht**– aus, und öffnen Sie dann das Kontextmenü für die RC-Datei, und klicken Sie auf **Ressourcen Symbole** , um die Liste der definierten Symbole anzuzeigen. Um die enthaltenen Header zu ändern, öffnen Sie das Kontextmenü für die RC-Datei, und wählen Sie **Ressource enthält**.

Wenn Sie diese Meldung erhalten:

```
undefined keyword or key name: MFT_STRING
```

Öffnen Sie \MCL\MFC\Include\AfxRes.h, und fügen Sie diese Eingüge-Direktive ein:

```
#include <winresrc.h>
```
