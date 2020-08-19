---
title: static_assert
ms.date: 07/29/2019
f1_keywords:
- static_assert_cpp
helpviewer_keywords:
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
ms.openlocfilehash: 55181193e0364c1c6b758365c674f8e2c8a3f4c7
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560633"
---
# <a name="static_assert"></a>static_assert

Überprüft eine Softwareassertion zur Kompilierzeit. Wenn der angegebene Konstante Ausdruck ist **`false`** , zeigt der Compiler die angegebene Meldung an, sofern eine vorhanden ist, und bei der Kompilierung tritt ein Fehler auf C2338 auf; andernfalls hat die Deklaration keine Auswirkungen.

## <a name="syntax"></a>Syntax

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // C++17 (Visual Studio 2017 and later)
```

### <a name="parameters"></a>Parameter

*Constant-Expression*\
Ein ganzzahliger konstanter Ausdruck, der in einen booleschen Wert konvertiert werden kann. Wenn der ausgewertete Ausdruck NULL (false) ist, wird der *String-literalparameter* angezeigt, und bei der Kompilierung tritt ein Fehler auf. Wenn der Ausdruck ungleich 0 (true) ist, **`static_assert`** hat die Deklaration keine Auswirkungen.

*String-Literale*\
Eine Meldung, die angezeigt wird, wenn der *Constant-Expression-* Parameter 0 (null) ist. Die Meldung ist eine Zeichenfolge im [Basis Zeichensatz](../c-language/ascii-character-set.md) des Compilers. Das heißt, es handelt sich nicht um [Multibytezeichen-oder breit Zeichen](../c-language/multibyte-and-wide-characters.md).

## <a name="remarks"></a>Bemerkungen

Der *Constant-Expression-* Parameter einer **`static_assert`** Deklaration stellt eine *Software*Assertion dar. Eine Softwareassertion gibt eine Bedingung an, die an einer bestimmten Stelle im Programm "true" sein muss. Wenn die Bedingung true ist, hat die- **`static_assert`** Deklaration keine Auswirkungen. Wenn die Bedingung "false" lautet, schlägt die-Übersetzung fehl, der Compiler zeigt die Meldung im *String-literalparameter* an, und die Kompilierung schlägt mit einem Fehler fehl. In Visual Studio 2017 und höher ist der String-literalparameter optional.

Die- **`static_assert`** Deklaration testet eine Software-Assertion zur Kompilierzeit. Im Gegensatz dazu testen die [Funktionen ASSERT-Makro und _ASSERT und _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) eine Software-Assertion zur Laufzeit und verursachen eine Lauf Zeit Kosten in Raum oder Zeit. Die- **`static_assert`** Deklaration ist besonders nützlich für das Debuggen von Vorlagen, da Vorlagen Argumente im *Constant-Expression-* Parameter enthalten sein können.

Der Compiler überprüft die- **`static_assert`** Deklaration auf Syntax Fehler, wenn die-Deklaration gefunden wird. Der Compiler wertet den *Constant-Expression-* Parameter sofort aus, wenn er nicht von einem Vorlagen Parameter abhängt. Andernfalls wertet der Compiler den *Constant-Expression-* Parameter aus, wenn die Vorlage instanziiert wird. Daher gibt der Compiler möglicherweise eine Diagnosemeldung aus: einmal, wenn die Deklaration gefunden wird, und noch einmal, wenn die Vorlage instanziiert wird.

Sie können das **`static_assert`** Schlüsselwort im Namespace, in der Klasse oder im Block Bereich verwenden. (Das- **`static_assert`** Schlüsselwort ist technisch gesehen eine Deklaration, obwohl es keinen neuen Namen in Ihr Programm einführt, da es im Namespace Bereich verwendet werden kann.)

## <a name="description"></a>BESCHREIBUNG

Im folgenden Beispiel verfügt die- **`static_assert`** Deklaration über einen Namespace Bereich. Da der Compiler die Größe des Typs `void *` kennt, wird der Ausdruck sofort ausgewertet.

## <a name="example"></a>Beispiel

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description"></a>BESCHREIBUNG

Im folgenden Beispiel verfügt die- **`static_assert`** Deklaration über einen Klassen Bereich. Der **`static_assert`** überprüft, ob ein Vorlagen Parameter ein *Plain Old Data* (Pod)-Typ ist. Der Compiler überprüft die **`static_assert`** Deklaration, wenn er deklariert wird, wertet den *Constant-Expression-* Parameter jedoch erst aus, wenn die `basic_string` Klassen Vorlage in instanziiert wird `main()` .

## <a name="example"></a>Beispiel

```cpp
#include <type_traits>
#include <iosfwd>
namespace std {
template <class CharT, class Traits = std::char_traits<CharT> >
class basic_string {
    static_assert(std::is_pod<CharT>::value,
                  "Template argument CharT must be a POD type in class template basic_string");
    // ...
    };
}

struct NonPOD {
    NonPOD(const NonPOD &) {}
    virtual ~NonPOD() {}
};

int main()
{
    std::basic_string<char> bs;
}
```

## <a name="description"></a>BESCHREIBUNG

Im folgenden Beispiel verfügt die- **`static_assert`** Deklaration über einen Block Bereich. **`static_assert`** Mit wird überprüft, ob die Größe der VMPage-Struktur gleich der Seitegröße des virtuellen Arbeitsspeichers des Systems ist.

## <a name="example"></a>Beispiel

```cpp
#include <sys/param.h> // defines PAGESIZE
class VMMClient {
public:
    struct VMPage { // ...
           };
    int check_pagesize() {
    static_assert(sizeof(VMPage) == PAGESIZE,
        "Struct VMPage must be the same size as a system virtual memory page.");
    // ...
    }
// ...
};
```

## <a name="see-also"></a>Weitere Informationen

[Assertion und benutzerdefinierte Meldungen (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
[#Error-Direktive (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[Assert-Makro, _ASSERT _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Vorlagen](../cpp/templates-cpp.md)<br/>
[ASCII-Zeichensatz](../c-language/ascii-character-set.md)<br/>
[Deklarationen und Definitionen](declarations-and-definitions-cpp.md)
