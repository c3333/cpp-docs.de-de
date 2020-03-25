---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: cfe3631086515e4e31c7d4188d46e3a7440662b7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177949"
---
# <a name="naked-c"></a>naked (C++)

**Microsoft-spezifisch**

Der Compiler generiert Code ohne Prolog-und Epilogcode für Funktionen, die mit dem **Naked** -Attribut deklariert werden. Sie können diese Funktion verwenden, um eigene Prolog-/Epilogcodesequenzen mithilfe von Inlineassemblercode zu schreiben. Naked-Funktionen sind vor allem beim Schreiben von virtuellen Gerätetreibern hilfreich.  Beachten Sie, dass das **Naked** -Attribut nur in x86 und Arm gültig ist und auf x64 nicht verfügbar ist.

## <a name="syntax"></a>Syntax

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Bemerkungen

Da das **Naked** -Attribut nur für die Definition einer Funktion relevant ist und kein Typmodifizierer ist, müssen Naked-Funktionen die erweiterte Attribut Syntax und das [__declspec](../cpp/declspec.md) -Schlüsselwort verwenden.

Der Compiler kann keine Inline Funktion für eine Funktion generieren, die mit dem naked-Attribut markiert ist, auch wenn die Funktion ebenfalls mit dem [__forceinline](inline-functions-cpp.md) -Schlüsselwort markiert ist.

Der Compiler gibt einen Fehler aus, wenn das **Naked** -Attribut auf etwas anderes als die Definition einer nicht-Member-Methode angewendet wird.

## <a name="examples"></a>Beispiele

Dieser Code definiert eine Funktion mit dem **Naked** -Attribut:

```
__declspec( naked ) int func( formal_parameters ) {}
```

Oder auch:

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

Das **Naked** -Attribut wirkt sich nur auf die Art der Codegenerierung des Compilers für die Prolog-und epilogsequenzen der Funktion aus. Es hat keine Auswirkungen auf den Code, der zum Aufrufen solcher Funktionen generiert wird. Folglich wird das **Naked** -Attribut nicht als Teil des Funktions Typs angesehen, und Funktionszeiger dürfen nicht über das **Naked** -Attribut verfügen. Außerdem kann das **Naked** -Attribut nicht auf eine Datendefinition angewendet werden. Beispielsweise wird mit diesem Codebeispiel ein Fehler generiert:

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

Das **Naked** -Attribut ist nur für die Definition der Funktion relevant und kann nicht im Prototyp der Funktion angegeben werden. Beispielsweise wird mit dieser Deklaration ein Compilerfehler generiert:

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Naked-Funktionsaufrufe](../cpp/naked-function-calls.md)
