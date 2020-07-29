---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: 945202beca6c5deb525bd19886b947331f6f3ac3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228946"
---
# `__declspec`

**Microsoft-spezifisch**

Die erweiterte Attribut Syntax zum Angeben von Speicher Klassen Informationen verwendet das- **`__declspec`** Schlüsselwort, das angibt, dass eine Instanz eines bestimmten Typs mit einem Microsoft-spezifischen Speicher Klassen Attribut gespeichert werden soll, das unten aufgeführt ist. Beispiele für andere Speicherklassenmodifizierer sind **`static`** die **`extern`** Schlüsselwörter und. Allerdings sind diese Schlüsselwörter Teil der ANSI-Spezifikation der Programmiersprachen C- und C++ und werden als solche nicht von der erweiterten Attributsyntax abgedeckt. Die erweiterte Attributsyntax vereinfacht und standardisiert Microsoft-spezifische Erweiterungen der Programmiersprachen C und C++.

## <a name="grammar"></a>Grammatik

*decl-Spezifizierer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__declspec (`**  *Extended-decl-modifier-TQ*  **`)`**

*extended-decl-modifier-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modifier* *Extended-decl-modifier-* *

*extended-decl-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`align(`** *#* **`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocate("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocator`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`appdomain`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`code_seg("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`deprecated`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllexport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`jitintrinsic`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noalias`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noinline`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noreturn`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`nothrow`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`novtable`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`process`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`property(`**{ **`get=`** _get_func_name_ &#124; **`,put=`** _put_func_name_ }**`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`restrict`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`safebuffers`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`selectany`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`spectre(nomitigation)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`uuid("`***Comobjectguid***`")`**

Die Deklarationsmodifizierersequenz ist durch Leerzeichen getrennt. Beispiele finden Sie in späteren Abschnitten.

Die erweiterte Attribut Grammatik unterstützt diese Microsoft-spezifischen Speicher Klassenattribute: [`align`](../cpp/align-cpp.md) , [`allocate`](../cpp/allocate.md) , [`allocator`](../cpp/allocator.md) , [`appdomain`](../cpp/appdomain.md) , [`code_seg`](../cpp/code-seg-declspec.md) , [`deprecated`](../cpp/deprecated-cpp.md) , [`dllexport`](../cpp/dllexport-dllimport.md) , [`dllimport`](../cpp/dllexport-dllimport.md) , [`jitintrinsic`](../cpp/jitintrinsic.md) , [`naked`](../cpp/naked-cpp.md) , [`noalias`](../cpp/noalias.md) , [`noinline`](../cpp/noinline.md) , [`noreturn`](../cpp/noreturn.md) , [`nothrow`](../cpp/nothrow-cpp.md) , [`novtable`](../cpp/novtable.md) , [`process`](../cpp/process.md) , [`restrict`](../cpp/restrict.md) ,,, [`safebuffers`](../cpp/safebuffers.md) [`selectany`](../cpp/selectany.md) [`spectre`](../cpp/spectre.md) und [`thread`](../cpp/thread.md) . Sie unterstützt auch die folgenden COM-Objekt Attribute: [`property`](../cpp/property-cpp.md) und [`uuid`](../cpp/uuid-cpp.md) .

Die **`code_seg`** **`dllexport`** **`dllimport`** **`naked`** Speicher Klassenattribute,,,, **`noalias`** , **`nothrow`** ,,,, **`property`** **`restrict`** **`selectany`** **`thread`** und **`uuid`** sind nur Eigenschaften der Deklaration des Objekts oder der Funktion, auf die Sie angewendet werden. Das **`thread`** -Attribut wirkt sich nur auf Daten und Objekte aus. Die **`naked`** **`spectre`** Attribute und wirken sich nur auf Funktionen aus. Die **`dllimport`** **`dllexport`** Attribute und wirken sich auf Funktionen, Daten und Objekte aus. Die **`property`** **`selectany`** Attribute, und **uu' ID** betreffen com-Objekte.

Aus Gründen der Kompatibilität mit früheren Versionen ist **`_declspec`** ein Synonym für, **`__declspec`** es sei denn, die Compileroption [/Za \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

Die **`__declspec`** Schlüsselwörter sollten am Anfang einer einfachen Deklaration platziert werden. Der Compiler ignoriert ohne Warnung alle **`__declspec`** Schlüsselwörter nach * oder & und vor dem Variablen Bezeichner in einer Deklaration.

Ein- **`__declspec`** Attribut, das am Anfang einer benutzerdefinierten Typdeklaration angegeben wird, gilt für die Variable dieses Typs. Beispiel:

```cpp
__declspec(dllimport) class X {} varX;
```

In diesem Fall wird das Attribut auf `varX` angewendet. Ein- **`__declspec`** Attribut, das nach dem- **`class`** oder-Schlüsselwort platziert wird **`struct`** , gilt für den benutzerdefinierten Typ. Beispiel:

```cpp
class __declspec(dllimport) X {};
```

In diesem Fall wird das Attribut auf `X` angewendet.

Die allgemeine Richtlinie für die Verwendung des- **`__declspec`** Attributs für einfache Deklarationen lautet wie folgt:

*decl-specifier-setq* *Init-declarator-List*;

*Decl-specifier-SSQ* sollte u. a. einen Basistyp (z. b., **`int`** **`float`** , **`typedef`** oder einen Klassennamen), eine Speicher Klasse (z. b. **`static`** **`extern`** ) oder die **`__declspec`** Erweiterung enthalten. Die *Init-declarator-List* sollte unter anderem den Zeiger Teil der Deklarationen enthalten. Beispiel:

```cpp
__declspec(selectany) int * pi1 = 0;   //Recommended, selectany & int both part of decl-specifier
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator
```

Mit folgendem Code wird z. B. eine ganzzahlige threadlokale Variable deklariert und mit einem Wert initialisiert:

```cpp
// Example of the __declspec keyword
__declspec( thread ) int tls_i = 1;
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[C-Speicherklassenattribute (erweitert)](../c-language/c-extended-storage-class-attributes.md)
