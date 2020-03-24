---
title: Befehlszeilenwarnung D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 7c685a1ca3195ad4ab52bab8b5d32b1a51534b24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196574"
---
# <a name="command-line-warning-d9041"></a>Befehlszeilenwarnung D9041

Ungültiger Wert "Value" für "/Option"; "Wert" wird angenommen; "/Analyze" den Befehlszeilenoptionen beim Angeben dieser Warnung hinzufügen

Der **/WD**-, **/We**-, **/wo**-oder **/WL** -Befehlszeilenoption wurde eine Code Analyse-Warnungs Nummer hinzugefügt, ohne auch die **/analyze** -Befehlszeilenoption anzugeben. Fügen Sie zum Beheben dieses Fehlers entweder die Befehlszeilenoption " **/analyze** " hinzu, oder entfernen Sie die ungültige Warnungs Nummer aus der entsprechenden **/w** -Befehlszeilenoption.

## <a name="example"></a>Beispiel

Im folgenden Befehlszeilen Beispiel wird die Warnung D9041 generiert:

```
cl /EHsc /LD /wd6001 filename.cpp
```

Fügen Sie die **/analyze** -Befehlszeilenoption hinzu, um die Warnung zu beheben. Wenn **/analyze** für Ihre Version des Compilers nicht unterstützt wird, entfernen Sie die ungültige Warnungs Nummer aus der **/WD** -Option.

## <a name="see-also"></a>Weitere Informationen

[Befehlszeilenfehler D8000 bis D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC-Compileroptionen](../../build/reference/compiler-options.md)
