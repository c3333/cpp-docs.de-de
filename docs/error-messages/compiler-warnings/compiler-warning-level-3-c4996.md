---
title: Compilerwarnung (Stufe 3) C4996
description: Erläutert, warum Compilerwarnung C4996 geschieht, und beschreibt, was damit zu tun ist.
ms.date: 11/25/2019
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: 98662dc0b5439c1f8857e4f2ad259793a4d03e41
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2020
ms.locfileid: "79425040"
---
# <a name="compiler-warning-level-3-c4996"></a>Compilerwarnung (Stufe 3) C4996

Der Code verwendet eine Funktion, einen Klassenmember, eine Variable oder eine typedef, die als *veraltet*markiert ist. Symbole werden mithilfe eines __declspec-Modifizierers [(veraltet)](../../cpp/deprecated-cpp.md) oder des [ \[ \[ veralteten \] \] ](../../cpp/attributes.md) Attributs c++ 14 als veraltet markiert. Die tatsächliche C4996-Warnmeldung wird durch den- `deprecated` Modifizierer oder das-Attribut der Deklaration angegeben.

> [!IMPORTANT]
> Diese Warnung ist immer eine absichtliche Nachricht vom Autor der Header Datei, die das Symbol deklariert. Verwenden Sie das veraltete Symbol nicht, ohne die Konsequenzen zu verstehen.

## <a name="remarks"></a>Bemerkungen

Viele Funktionen, Element Funktionen, Vorlagen Funktionen und globale Variablen in Visual Studio-Bibliotheken sind *veraltet*. Einige, z. b. POSIX-und Microsoft-spezifische Funktionen, sind veraltet, da Sie nun einen anderen bevorzugten Namen haben. Einige C-Lauf Zeit Bibliotheksfunktionen sind veraltet, da Sie unsicher sind und eine sicherere Variante aufweisen. Andere sind veraltet, da sie veraltet sind. Die veralnungs Nachrichten enthalten in der Regel eine vorgeschlagene Ersetzung für die veraltete Funktion oder globale Variable.

## <a name="turn-off-the-warning"></a>Warnung deaktivieren

Zum Beheben eines C4996 Problems wird in der Regel empfohlen, den Code zu ändern. Verwenden Sie stattdessen die vorgeschlagenen Funktionen und globalen Variablen. Wenn Sie die vorhandenen Funktionen oder Variablen aus Gründen der Portabilität verwenden müssen, können Sie die Warnung deaktivieren.

Verwenden Sie das [Warning](../../preprocessor/warning.md) -Pragma, um die Warnung für eine bestimmte Codezeile zu deaktivieren `#pragma warning(suppress : 4996)` .

Verwenden Sie das warning-Pragma, um die Warnung in einer Datei zu deaktivieren `#pragma warning(disable : 4996)` .

Verwenden Sie die Befehlszeilenoption [/wd4996](../../build/reference/compiler-option-warning-level.md) , um die Warnung in Befehlszeilenbuilds Global zu deaktivieren.

So deaktivieren Sie die Warnung für ein gesamtes Projekt in der Visual Studio-IDE:

1. Öffnen Sie das Dialogfeld **Eigenschaften Seiten** für das Projekt. Informationen zur Verwendung des Dialog Felds "Eigenschaften Seiten" finden Sie unter [Eigenschaften Seiten](../../build/reference/property-pages-visual-cpp.md).

1. Wählen Sie die Seite **Konfigurations Eigenschaften**  >  **C/C++**  >  **erweitert** aus.

1. Bearbeiten Sie die Eigenschaft **bestimmte Warnungen deaktivieren** , um hinzuzufügen `4996` . Wählen Sie **OK** aus, um die Änderungen zu übernehmen.

Sie können auch Präprozessormakros verwenden, um bestimmte bestimmte Klassen von veralnungs Warnungen zu deaktivieren, die in den Bibliotheken verwendet werden. Diese Makros werden nachfolgend beschrieben.

So definieren Sie ein Präprozessormakro in Visual Studio:

1. Öffnen Sie das Dialogfeld **Eigenschaften Seiten** für das Projekt. Informationen zur Verwendung des Dialog Felds "Eigenschaften Seiten" finden Sie unter [Eigenschaften Seiten](../../build/reference/property-pages-visual-cpp.md).

1. Erweitern Sie **Konfigurations Eigenschaften > C/C++-> Präprozessor**.

1. Fügen Sie in der Eigenschaft **Präprozessordefinitionen** den Namen des Makros hinzu. Wählen Sie **OK** aus, um Ihre Änderung zu speichern, und erstellen Sie das Projekt anschließend neu.

Um ein Makro nur in bestimmten Quelldateien zu definieren, fügen Sie eine Zeile wie `#define EXAMPLE_MACRO_NAME` vor allen Zeilen hinzu, die eine Header Datei enthalten.

Im folgenden finden Sie einige der allgemeinen Quellen für C4996-Warnungen und-Fehler:

## <a name="posix-function-names"></a>POSIX-Funktionsnamen

**Der POSIX-Name für dieses Element ist veraltet. Verwenden Sie stattdessen den ISO C-und C++-konformen Namen:** *New-Name*. **Weitere Informationen finden Sie in der Online Hilfe.**

Microsoft hat einige POSIX-und Microsoft-spezifische Bibliotheksfunktionen in der CRT umbenannt, um die Einschränkungen C99 und c++ 03 für reservierte und globale Implementierungs definierte Namen einzuhalten. *Nur die Namen sind veraltet, nicht die Funktionen selbst*. In den meisten Fällen wurde dem Funktionsnamen ein führender unterstrich hinzugefügt, um einen übereinstimmenden Namen zu erstellen. Der Compiler gibt eine veralnungs Warnung für den ursprünglichen Funktionsnamen aus und schlägt den bevorzugten Namen vor.

Um dieses Problem zu beheben, empfiehlt es sich in der Regel, den Code so zu ändern, dass die vorgeschlagenen Funktionsnamen verwendet werden. Die aktualisierten Namen sind jedoch Microsoft-spezifisch. Wenn Sie die vorhandenen Funktionsnamen aus Gründen der Portabilität verwenden müssen, können Sie diese Warnungen deaktivieren. Die Funktionen sind nach wie vor in der Bibliothek unter ihren ursprünglichen Namen verfügbar.

Um veralnungs Warnungen für diese Funktionen zu deaktivieren, definieren Sie das Präprozessormakro ** \_ CRT \_ nonstdc \_ No \_ **. Sie können dieses Makro in der Befehlszeile definieren, indem Sie die-Option einschließen `/D_CRT_NONSTDC_NO_WARNINGS` .

## <a name="unsafe-crt-library-functions"></a>Unsichere CRT-Bibliotheksfunktionen

**Diese Funktion oder Variable ist möglicherweise unsicher. Verwenden Sie** stattdessen eine *sichere Version* **. Zum Deaktivieren der Veraltung verwenden Sie \_ CRT \_ Secure No- \_ \_ Warnungen.  Weitere Informationen finden Sie in der Online Hilfe.**

Microsoft hat einige CRT-und C++-Standard Bibliotheksfunktionen und Globals als veraltet markiert, da sicherere Versionen verfügbar sind. Die meisten der veralteten Funktionen ermöglichen den deaktivierten Lese-oder Schreibzugriff auf Puffer. Der Missbrauch kann zu schwerwiegenden Sicherheitsproblemen führen. Der Compiler gibt für diese Funktionen eine Veraltungswarnung aus und schlägt die bevorzugte Funktion vor.

Um dieses Problem zu beheben, empfiehlt es sich, stattdessen die Funktion oder Variable " *sichere Version* " zu verwenden. Manchmal ist dies aus Gründen der Portabilität oder der Abwärtskompatibilität nicht möglich. Vergewissern Sie sich, dass es nicht möglich ist, dass ein Puffer überschreiben oder Überschreiben in Ihrem Code erfolgt. Anschließend können Sie die Warnung deaktivieren.

Um veraltete Warnungen für diese Funktionen in der CRT zu deaktivieren, definieren Sie ** \_ CRT \_ Secure \_ No- \_ Warnungen**.

Um Warnungen zu veralteten globalen Variablen zu deaktivieren, definieren Sie ** \_ CRT \_ Secure \_ No- \_ Warnungen \_ Globals**.

Weitere Informationen zu diesen veralteten Funktionen und Globals finden Sie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) und [sicheren Bibliotheken: C++-Standard Bibliothek](../../standard-library/safe-libraries-cpp-standard-library.md).

## <a name="unsafe-standard-library-functions"></a>Unsichere Standard Bibliotheksfunktionen

__' Std::__*function_name*__:: deaktivierte \_ \_ Iteratoren:: \_ deprecate '-Aufruf an Std::__*function_name* **mit Parametern, die möglicherweise unsicher sind. bei diesem Aufruf wird vom Aufrufer geprüft, ob die übergebenen Werte richtig sind. Um diese Warnung zu deaktivieren, verwenden Sie-D \_ SCL \_ Secure \_ No \_ Warnungen. Weitere Informationen finden Sie in der Dokumentation zur Verwendung Visual C++ "geprüften Iteratoren"** .

Diese Warnung wird in Debugbuilds angezeigt, da bestimmte Vorlagen Funktionen der C++-Standard Bibliothek die Parameter nicht auf Richtigkeit überprüfen. Häufig liegt es daran, dass der Funktion nicht genügend Informationen zur Verfügung stehen, um Container Grenzen zu überprüfen. Oder, da Iteratoren möglicherweise falsch mit der-Funktion verwendet werden. Diese Warnung hilft Ihnen, diese Funktionen zu identifizieren, da Sie möglicherweise eine Quelle von ernsten Sicherheitslücken in Ihrem Programm sind. Weitere Informationen finden Sie unter über [prüfte Iteratoren](../../standard-library/checked-iterators.md).

Diese Warnung wird z. b. im Debugmodus angezeigt, wenn Sie anstelle eines einfachen Arrays einen Element Zeiger an übergeben `std::copy` . Um dieses Problem zu beheben, verwenden Sie ein entsprechend deklariertes Array, sodass die Bibliothek die Array Blöcke überprüfen und die Begrenzungen überprüfen kann.

```cpp
// C4996_copyarray.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_copyarray.cpp
#include <algorithm>

void example(char const * const src) {
    char dest[1234];
    char * pdest3 = dest + 3;
    std::copy(src, src + 42, pdest3); // C4996
    std::copy(src, src + 42, dest);   // OK, copy can tell that dest is 1234 elements
}
```

Mehrere Algorithmen der Standardbibliothek wurden in c++ 14 als "Dual-Range"-Versionen aktualisiert. Wenn Sie die Dual-Range-Versionen verwenden, bietet der zweite Bereich die erforderliche Überprüfung der Begrenzungen:

```cpp
// C4996_containers.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_containers.cpp
#include <algorithm>

bool example(
    char const * const left,
    const size_t leftSize,
    char const * const right,
    const size_t rightSize)
{
    bool result = false;
    result = std::equal(left, left + leftSize, right); // C4996
    // To fix, try this form instead:
    // result = std::equal(left, left + leftSize, right, right + rightSize); // OK
    return result;
}
```

In diesem Beispiel werden mehrere Möglichkeiten veranschaulicht, wie die Standardbibliothek verwendet werden kann, um die Iteratorverwendung zu prüfen, und wenn die überprüfte Verwendung gefährlich sein kann:

```cpp
// C4996_standard.cpp
// compile with: cl /EHsc /W4 /MDd C4996_standard.cpp
#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    // NOTE: This applies only when raw arrays are
    // given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (i.e. an overrun triggers undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(),
        stdext::make_checked_array_iterator(p7, 16),
        [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator
    // is marked as checked in debug mode, but it performs no checking,
    // so an overrun triggers undefined behavior
    int a8[16];
    int * p8 = a8;
    transform( v.begin(), v.end(),
        stdext::make_unchecked_array_iterator(p8),
        [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

Wenn Sie überprüft haben, dass der Code keinen Pufferüberlauf Fehler aufweisen kann, können Sie diese Warnung deaktivieren. Um die Warnungen für diese Funktionen zu deaktivieren, definieren Sie ** \_ SCL \_ Secure \_ No- \_ Warnungen**.

## <a name="checked-iterators-enabled"></a>Aktivierte Iteratoren aktiviert

C4996 kann auch auftreten, wenn Sie keinen überprüften Iterator verwenden, wenn `_ITERATOR_DEBUG_LEVEL` als 1 oder 2 definiert ist. Der Wert ist standardmäßig auf 2 festgelegt für buildbuildbuilds und auf 0 für Einzelhandels Builds. Weitere Informationen finden Sie unter über [prüfte Iteratoren](../../standard-library/checked-iterators.md).

```cpp
// C4996_checked.cpp
// compile with: /EHsc /W4 /MDd C4996_checked.cpp
#define _ITERATOR_DEBUG_LEVEL 2

#include <algorithm>
#include <iterator>

using namespace std;
using namespace stdext;

int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 10, 11, 12 };
    copy(a, a + 3, b + 1);   // C4996
    // try the following line instead:
    // copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK
}
```

## <a name="unsafe-mfc-or-atl-code"></a>Unsicherer MFC-oder ATL-Code

C4996 kann auftreten, wenn Sie MFC-oder ATL-Funktionen verwenden, die aus Sicherheitsgründen als veraltet eingestuft wurden.

Um dieses Problem zu beheben, wird dringend empfohlen, stattdessen den Code so zu ändern, dass aktualisierte Funktionen verwendet werden.

Informationen zum Unterdrücken dieser Warnungen finden Sie unter [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

## <a name="obsolete-crt-functions-and-variables"></a>Veraltete CRT-Funktionen und-Variablen

**Diese Funktion oder Variable wurde durch neuere Bibliotheks-oder Betriebssystemfunktionen ersetzt. Verwenden Sie** stattdessen *new_item* **. Weitere Informationen finden Sie in der Online Hilfe.**

Einige Bibliotheksfunktionen und globale Variablen wurden als veraltet gekennzeichnet. Diese Funktionen und Variablen werden möglicherweise in einer zukünftigen Version der Bibliothek entfernt. Der Compiler gibt für diese Elemente eine Veraltungswarnung aus und schlägt die bevorzugte Alternative vor.

Um dieses Problem zu beheben, empfiehlt es sich, den Code so zu ändern, dass er die vorgeschlagene Funktion oder Variable verwendet.

Um veralnungs Warnungen für diese Elemente zu deaktivieren, definieren Sie ** \_ CRT- \_ veraltete \_ keine \_ Warnungen**. Weitere Informationen finden Sie in der Dokumentation für die veraltete Funktion oder Variable.

## <a name="marshaling-errors-in-clr-code"></a>Marshalling von Fehlern in CLR-Code

C4996 kann auch auftreten, wenn Sie die CLR-Marshallingbibliothek verwenden. In diesem Fall ist C4996 ein Fehler, keine Warnung. Der Fehler tritt auf, wenn Sie [marshal_as](../../dotnet/marshal-as.md) für die Konvertierung zwischen zwei Datentypen verwenden, die eine [Marshal_context Klasse](../../dotnet/marshal-context-class.md)erfordern. Dieser Fehler kann auch angezeigt werden, wenn die Marshallingbibliothek keine Konvertierung unterstützt. Weitere Informationen über die Marshallingbibliothek finden Sie unter Übersicht über das Marshalling [in C++](../../dotnet/overview-of-marshaling-in-cpp.md).

In diesem Beispiel wird C4996 generiert, da die Marshallingbibliothek einen Kontext für die Konvertierung von einem `System::String` in einen erfordert `const char *` .

```cpp
// C4996_Marshal.cpp
// compile with: /clr
// C4996 expected
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = marshal_as<const char*>( message );
   return 0;
}
```

## <a name="example-user-defined-deprecated-function"></a>Beispiel: benutzerdefinierte veraltete Funktion

Sie können das veraltet-Attribut in Ihrem eigenen Code verwenden, um Aufrufer zu warnen, wenn Sie die Verwendung bestimmter Funktionen nicht mehr empfehlen. In diesem Beispiel wird C4996 an zwei Stellen generiert: einer für die Zeile, in der die veraltete Funktion deklariert ist, und einer für die Zeile, in der die Funktion verwendet wird.

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

[[deprecated]]
void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
