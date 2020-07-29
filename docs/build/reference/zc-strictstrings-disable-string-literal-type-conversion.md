---
title: /Zc:strictStrings (Zeichenfolgenliteral-Typkonvertierung deaktivieren)
ms.date: 03/06/2018
f1_keywords:
- /Zc:strictStrings
- strictStrings
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
ms.openlocfilehash: df880ed64fa472ff55eb5ee0d17caacf56228ab6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211891"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>`/Zc:strictStrings`(Konvertierung von zeichenfolgenliteraltypen deaktivieren)

Wenn angegeben, erfordert der Compiler **`const`** eine strikte qualifizierenden Konformität für Zeiger, die mithilfe von Zeichenfolgenliteralen initialisiert werden.

## <a name="syntax"></a>Syntax

> **`/Zc:strictStrings`**[**`-`**]

## <a name="remarks"></a>Bemerkungen

Wenn **`/Zc:strictStrings`** angegeben wird, erzwingt der Compiler die standardmäßigen C++- **`const`** Qualifizierer für Zeichen folgen Literale, `const char` `const wchar_t` abhängig von der Deklaration als Typ ' Array von ' oder ' Array von '. Zeichenfolgenliterale sind unveränderlich. Der Versuch, den Inhalt von einem von ihnen zu ändern, führt zu einem Zugriffsverletzungsfehler in der Laufzeit. Sie müssen einen Zeichen folgen Zeiger als deklarieren, **`const`** um ihn mithilfe eines Zeichenfolgenliterals zu initialisieren, oder einen expliziten verwenden, **`const_cast`** um einen nicht-Zeiger zu initialisieren **`const`** . Standardmäßig oder wenn **`/Zc:strictStrings-`** angegeben wird, erzwingt der Compiler die standardmäßigen C++- **`const`** Qualifizierungen für Zeichen folgen Zeiger nicht, die mithilfe von Zeichenfolgenliteralen initialisiert werden.

Die **`/Zc:strictStrings`** Option ist standardmäßig deaktiviert. [`/permissive-`](permissive-standards-conformance.md)Diese Option wird von der-Compileroption implizit festgelegt, aber Sie kann mithilfe von überschrieben werden **`/Zc:strictStrings-`** .

Verwenden Sie die- **`/Zc:strictStrings`** Option, um die Kompilierung falscher Codes zu verhindern. Dieses Beispiel zeigt, wie ein einfacher Deklarationsfehler zu einem Absturz während der Laufzeit führt:

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

Wenn **`/Zc:strictStrings`** aktiviert ist, meldet derselbe Code einen Fehler in der Deklaration von `str` .

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

Wenn Sie verwenden, **`auto`** um einen Zeichen folgen Zeiger zu deklarieren, erstellt der Compiler die richtige **`const`** Zeigertyp Deklaration für Sie. Der Versuch, den Inhalt eines Zeigers zu ändern, **`const`** wird vom Compiler als Fehler gemeldet.

> [!NOTE]
> Die C++-Standard Bibliothek in Visual Studio 2013 unterstützt die- **`/Zc:strictStrings`** Compileroption in Debugbuilds nicht. Wenn in ihrer Buildausgabe mehrere [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) -Fehler angezeigt werden, kann dies die Ursache sein.

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** in include, **`/Zc:strictStrings`** und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen

[`/Zc`Konformitäts](zc-conformance.md)<br/>
