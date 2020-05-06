---
title: Naked-Funktionen
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions
- functions [C++], naked
- prolog code
- epilog code
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
ms.openlocfilehash: b752dd6fa378bc1275e8a7da90420aa2b8247e4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232814"
---
# <a name="naked-functions"></a>Naked-Funktionen

**Microsoft-spezifisch**

Das `naked`-Speicherklassenattribut ist eine Microsoft-spezifische Erweiterung der Programmiersprache C. Der Compiler generiert Code ohne Prolog- und Epilogcode für Funktionen, die mit dem `naked`-Speicherklassenattribut deklariert werden. Sie können diese Funktion verwenden, um eigene Prolog-/Epilogcodesequenzen mithilfe von Inlineassemblercode zu schreiben. Naked-Funktionen sind vor allem beim Schreiben von virtuellen Gerätetreibern hilfreich.

Da das `naked`-Attribut nur für die Definition einer Funktion relevant ist und kein Typmodifizierer ist, müssen naked-Funktionen die erweiterte Attributsyntax verwenden, die in [Erweiterte Speicherklassenattribute](../c-language/c-extended-storage-class-attributes.md) beschrieben wird.

Das folgende Beispiel definiert eine Funktion mit dem `naked`-Attribut:

```
__declspec( naked ) int func( formal_parameters )
{
   /* Function body */
}
```

Oder auch:

```
#define Naked   __declspec( naked )

Naked int func( formal_parameters )
{
   /* Function body */
}
```

Das `naked`-Attribut wirkt sich nur auf die Codegenerierung des Compilers für die Prolog- und Epilogsequenzen der Funktion aus. Es hat keine Auswirkungen auf den Code, der zum Aufrufen solcher Funktionen generiert wird. Daher gilt das `naked`-Attribut nicht als Teil des Typs der Funktion, und Funktionszeiger dürfen nicht das `naked`-Attribut enthalten. Darüber hinaus kann das `naked`-Attribut nicht auf eine Datendefinition angewendet werden. Durch folgenden Code werden z. B. Fehler verursacht:

```
__declspec( naked ) int i;  /* Error--naked attribute not */
                            /* permitted on data declarations. */
```

Das `naked`-Attribut ist nur für die Funktionsdefinition relevant und kann nicht im Funktionsprototyp angegeben werden. In der folgenden Deklaration wird ein Compilerfehler generiert:

```
__declspec( naked ) int func();   /* Error--naked attribute not */
                     /* permitted on function declarations.    */   \
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Funktionsdefinitionen](../c-language/c-function-definitions.md)
