---
title: /Zc:implicitNoexcept (implizite Ausnahmespezifizierer)
ms.date: 03/06/2018
f1_keywords:
- /Zc:implicitNoexcept
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
ms.openlocfilehash: bb1a632ffe684ac0777d0089a2edfd514bf66d0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223797"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (implizite Ausnahmespezifizierer)

Wenn die **/Zc: implicitnowith** -Option angegeben wird, fügt der Compiler einen impliziten [noexception](../../cpp/noexcept-cpp.md) -Ausnahme Bezeichner zu compilerdefinierten speziellen Member-Funktionen und zu benutzerdefinierten Debuggern und-dezuordnungen hinzu. Standardmäßig ist **/Zc: implicitnoaußer** aktiviert, um dem ISO c++ 11-Standard zu entsprechen. Wenn Sie diese Option deaktivieren, wird **`noexcept`** impliziter Zugriff auf benutzerdefinierte Dekonstruktoren und dezuordnungs-und compilerdefinierte sondermember-Funktionen deaktiviert.

## <a name="syntax"></a>Syntax

> **/Zc: implicitnoaußer**[ **-** ]

## <a name="remarks"></a>Bemerkungen

**/Zc: implicitnoaußer** weist den Compiler an, Abschnitt 15,4 des Standards ISO c++ 11 zu befolgen. Sie fügt implizit einen **`noexcept`** ausnahmespezifizierer zu jeder implizit deklarierten oder explizit vordefinierten speziellen Element Funktion hinzu – den Standardkonstruktor, den Kopierkonstruktor, den bewegungskonstruktor, den destrukturtor, den Kopier Zuweisungs Operator oder den Verschiebungs Zuweisungs Operator – und jede benutzerdefinierte dezuordnungs Funktion. Ein benutzerdefinierter Deallokator verfügt über einen impliziten `noexcept(true)`-Ausnahmebezeichner. Für benutzerdefinierte Destruktoren ist `noexcept(true)` der implizite Ausnahmebezeichner, es sei denn eine enthaltene Elementklasse oder Basisklasse weist einen Destruktor auf, der nicht `noexcept(true)` ist. Für vom Compiler generierte spezielle Memberfunktionen ist `noexcept(false)` der implizite Ausnahmebezeichner, wenn eine von dieser Funktion aufgerufene Funktion `noexcept(false)` ist. Andernfalls ist `noexcept(true)` der implizite Ausnahmebezeichner.

Der Compiler generiert keinen impliziten ausnahmespezifizierer für Funktionen, die mithilfe expliziter- **`noexcept`** oder- **`throw`** Spezifizierer oder eines- `__declspec(nothrow)` Attributs deklariert wurden.

**/Zc: implicitnoaußer** ist standardmäßig aktiviert. Die [/permissive-](permissive-standards-conformance.md) -Option hat keine Auswirkung auf **/Zc: implicitnoaußer**.

Wenn die Option durch Angabe von **/Zc: implicitnoaußer-** deaktiviert wird, werden vom Compiler keine impliziten ausnahmespezifizierer generiert. Dieses Verhalten ist identisch mit Visual Studio 2013, bei der debugtoren und dezuordnungen, die keine ausnahmespezifizierer hatten, über-Anweisungen verfügen können **`throw`** . Wenn **/Zc: implicitnoaußer** angegeben wird und eine- **`throw`** Anweisung zur Laufzeit in einer Funktion mit einem impliziten Spezifizierer gefunden wird, wird standardmäßig `noexcept(true)` ein sofortiger Aufruf von ausgelöst, und das `std::terminate` normale Entwicklungs Verhalten bei Ausnahme Handlern ist nicht garantiert. Um diese Situation zu identifizieren, generiert der Compiler [Compilerwarnung (Stufe 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Wenn **`throw`** beabsichtigt ist, empfiehlt es sich, die Funktionsdeklaration so zu ändern, dass Sie einen expliziten `noexcept(false)` Spezifizierer anstelle von **/Zc: implicitnoaußer-** verwendet.

Dieses Beispiel zeigt, wie sich ein benutzerdefinierter Dekonstruktor ohne expliziter ausnahmespezifizierer verhält, wenn die **/Zc: implicitnoaußer** -Option festgelegt oder deaktiviert wird. Um das Verhalten beim Festlegen anzuzeigen, kompilieren Sie mithilfe von `cl /EHsc /W4 implicitNoexcept.cpp` . Kompilieren Sie mithilfe von, um das Verhalten bei der Deaktivierung anzuzeigen `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp` .

```cpp
// implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp

#include <iostream>
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS
#include <exception>    // for std::set_terminate

void my_terminate()
{
    std::cout << "Unexpected throw caused std::terminate" << std::endl;
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;
    std::exit(EXIT_FAILURE);
}

struct A {
    // Explicit noexcept overrides implicit exception specification
    ~A() noexcept(false) {
        throw 1;
    }
};

struct B : public A {
    // Compiler-generated ~B() definition inherits noexcept(false)
    ~B() = default;
};

struct C {
    // By default, the compiler generates an implicit noexcept(true)
    // specifier for this user-defined destructor. To enable it to
    // throw an exception, use an explicit noexcept(false) specifier,
    // or compile by using /Zc:implicitNoexcept-
    ~C() {
        throw 1; // C4297, calls std::terminate() at run time
    }
};

struct D : public C {
    // This destructor gets the implicit specifier of its base.
    ~D() = default;
};

int main()
{
    std::set_terminate(my_terminate);

    try
    {
        {
            B b;
        }
    }
    catch (...)
    {
        // exception should reach here in all cases
        std::cout << "~B Exception caught" << std::endl;
    }
    try
    {
        {
            D d;
        }
    }
    catch (...)
    {
        // exception should not reach here if /Zc:implicitNoexcept
        std::cout << "~D Exception caught" << std::endl;
    }
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;
    return EXIT_SUCCESS;
}
```

Bei der Kompilierung mit der Standardeinstellung **/Zc: implicitnoaußer**generiert das Beispiel diese Ausgabe:

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

Bei der Kompilierung mit der **-Einstellung/Zc: implicitnoaußer-**, generiert das Beispiel diese Ausgabe:

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** , um **/Zc: implicitnoaußer** oder **/Zc: implicitnoaußer** zu schließen, und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Siehe auch

[/Zc (Übereinstimmung)](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Ausnahme Spezifikationen (Throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[aufzu](../../standard-library/exception-functions.md#terminate)<br/>
