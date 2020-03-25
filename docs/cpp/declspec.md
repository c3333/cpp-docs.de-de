---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: e0c99ea9379aa6e29096250e8bd36ce3d4f183e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180224"
---
# <a name="__declspec"></a>__declspec

**Microsoft-spezifisch**

Die erweiterte Attribut Syntax zum Angeben von Speicher Klassen Informationen verwendet das **__declspec** -Schlüsselwort, das angibt, dass eine Instanz eines bestimmten Typs mit einem Microsoft-spezifischen Speicher Klassen Attribut gespeichert werden soll, das unten aufgeführt ist. Beispiele für andere Speicherklassenmodifizierer sind die **statischen** und **externen** Schlüsselwörter. Allerdings sind diese Schlüsselwörter Teil der ANSI-Spezifikation der Programmiersprachen C- und C++ und werden als solche nicht von der erweiterten Attributsyntax abgedeckt. Die erweiterte Attributsyntax vereinfacht und standardisiert Microsoft-spezifische Erweiterungen der Programmiersprachen C und C++.

## <a name="grammar"></a>Grammatik

*decl-Spezifizierer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *Extended-decl-modifier-* * **)**

*extended-decl-modifier-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modifier* *Extended-decl-modifier-netq*

*extended-decl-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Ausrichten (** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zuordnen ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Zuweisung**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**AppDomain**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;**veraltet** &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsisch**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Prozess**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Eigenschaft (** { **Get =** _get_func_name_ &#124; **, Put =** _put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**einschränken**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Spectre (noentschärfung)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**UUID ("** *comobjectguid* **")**

Die Deklarationsmodifizierersequenz ist durch Leerzeichen getrennt. Beispiele finden Sie in späteren Abschnitten.

Die erweiterte Attribut Grammatik unterstützt diese Microsoft-spezifischen Speicher Klassenattribute [: Align](../cpp/align-cpp.md), [zuordnen](../cpp/allocate.md), [Allocator](../cpp/allocator.md), [AppDomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [veraltet](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [DllImport](../cpp/dllexport-dllimport.md), [jitintrinsisch](../cpp/jitintrinsic.md), [Naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md), [Process](../cpp/process.md), [Limit](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [Selectany](../cpp/selectany.md), [ Spectre](../cpp/spectre.md)und [Thread](../cpp/thread.md). Außerdem werden diese COM-Objekt Attribute unterstützt: [Eigenschaft](../cpp/property-cpp.md) und [UUID](../cpp/uuid-cpp.md).

Die Speicher Klassenattribute **code_seg**, **dllexport**, **DllImport**, **Naked**, **noalias**, **nothrow**, **Property**, **Limit**, **Selectany**, **Thread**und **UUID** sind nur Eigenschaften der Deklaration des Objekts oder der Funktion, auf die Sie angewendet werden. Das **Thread** Attribut wirkt sich nur auf Daten und Objekte aus. Die **Naked** -und **Spectre** -Attribute wirken sich nur auf Funktionen aus. Die Attribute **DllImport** und **dllexport** wirken sich auf Funktionen, Daten und Objekte aus. Die Attribute " **Property**", " **Selectany**" und " **UUID** " betreffen com-Objekte.

Aus Gründen der Kompatibilität mit früheren Versionen ist **_declspec** ein Synonym für **__declspec** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

Die **__declspec** Schlüsselwörter sollten am Anfang einer einfachen Deklaration platziert werden. Der Compiler ignoriert ohne Warnung alle **__declspec** Schlüsselwörter, die nach * oder & und vor dem Variablen Bezeichner in einer Deklaration platziert werden.

Ein **__declspec** Attribut, das am Anfang einer Deklaration eines benutzerdefinierten Typs angegeben ist, gilt für die Variable dieses Typs. Beispiel:

```cpp
__declspec(dllimport) class X {} varX;
```

In diesem Fall wird das Attribut auf `varX` angewendet. Ein **__declspec** Attribut, das nach dem **Klassen** -oder **struct** -Schlüsselwort platziert wird, gilt für den benutzerdefinierten Typ. Beispiel:

```cpp
class __declspec(dllimport) X {};
```

In diesem Fall wird das Attribut auf `X` angewendet.

Die allgemeine Richtlinie für die Verwendung des **__declspec** -Attributs für einfache Deklarationen lautet wie folgt:

*decl-specifier-setq* *Init-declarator-List*;

*Decl-specifier-SSQ* sollte u. a. einen Basistyp (z. b. " **int**", " **float**", " **typedef**" oder einen Klassennamen), eine Speicher Klasse (z. b. " **static**", " **extern**") oder die **__declspec** Erweiterung enthalten. Die *Init-declarator-List* sollte unter anderem den Zeiger Teil der Deklarationen enthalten. Beispiel:

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

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[C-Speicherklassenattribute (erweitert)](../c-language/c-extended-storage-class-attributes.md)
