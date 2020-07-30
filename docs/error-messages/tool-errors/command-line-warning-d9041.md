---
title: Befehlszeilenwarnung D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: e685e9bd0ffb58065f20f466131f8894baaf359f
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389726"
---
# <a name="command-line-warning-d9041"></a>Befehlszeilenwarnung D9041

> Ungültiger Wert "*Option-Wert*" für "/*options Name*"; Annahme von '*angenommenen-Value*'; "/Analyze" den Befehlszeilenoptionen beim Angeben dieser Warnung hinzufügen

Der-,-,-oder-Befehlszeilenoption wurde eine Code Analyse-Warnungs Nummer hinzugefügt **`/wd`** , **`/we`** **`/wo`** **`/wl`** ohne auch die **`/analyze`** Befehlszeilenoption anzugeben. Um diesen Fehler zu beheben, fügen Sie entweder die **`/analyze`** Befehlszeilenoption hinzu, oder entfernen Sie die ungültige Warnungs Nummer aus der entsprechenden **`/w`** Befehlszeilenoption.

## <a name="example"></a>Beispiel

Im folgenden Befehlszeilen Beispiel wird die Warnung D9041 generiert:

```cmd
cl /EHsc /LD /wd6001 filename.cpp
```

Fügen Sie die Befehlszeilenoption hinzu, um die Warnung zu beheben **`/analyze`** . Wenn **`/analyze`** für Ihre Version des Compilers nicht unterstützt wird, entfernen Sie die ungültige Warnungs Nummer aus der- **`/wd`** Option.

## <a name="see-also"></a>Siehe auch

[Befehlszeilenfehler D8000 bis D9000](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC-Compileroptionen](../../build/reference/compiler-options.md)
