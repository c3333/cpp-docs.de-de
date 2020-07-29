---
title: /Zc:throwingNew (throw-Ausdrücke des Operators „new“ annehmen)
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: 7593107a280995145d252efa76e0a88bddbd2275
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211865"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (throw-Ausdrücke des Operators „new“ annehmen)

Wenn die **/Zc: throwingnew** -Option angegeben wird, optimiert der Compiler Aufrufe von, `operator new` um Überprüfungen für eine Rückgabe des NULL-Zeigers zu überspringen. Diese Option weist den Compiler an, davon auszugehen, dass alle verknüpften Implementierungen von `operator new` und benutzerdefinierten Zuweisungen dem C++-Standard entsprechen und bei Zuordnungs Fehlern ausgelöst werden. Standardmäßig generiert der Compiler in Visual Studio für diese Aufrufe pessimistisch Null-Überprüfungen (**/Zc: throwingnew-**), da Benutzer mit einer nicht auslösenden Implementierung von verknüpfen `operator new` oder benutzerdefinierte zuordnerroutinen schreiben können, die NULL-Zeiger zurückgeben.

## <a name="syntax"></a>Syntax

> **/Zc: throwingnew**[ **-** ]

## <a name="remarks"></a>Bemerkungen

Seit ISO c++ 98 hat der Standardwert angegeben, den der Standard [Operator new](../../standard-library/new-operators.md#op_new) auslöst, `std::bad_alloc` Wenn die Speicher Belegung fehlschlägt. Versionen von Visual C++ bis zu Visual Studio 6,0 haben bei einem Zuordnungs Fehler einen NULL-Zeiger zurückgegeben. Ab Visual Studio 2002 `operator new` entspricht dem Standard und löst bei einem Fehler aus. Zur Unterstützung von Code, der den älteren Zuordnungs Stil verwendet, stellt Visual Studio eine lintier Bare Implementierung von `operator new` in nothrownew. obj bereit, die bei einem Fehler einen NULL-Zeiger zurückgibt. Standardmäßig generiert der Compiler auch Defensive NULL-Prüfungen, um zu verhindern, dass dieser ältere Typzuweisung einen sofortigen Absturz bei einem Fehler verursacht. Die Option **/Zc: throwingnew** weist den Compiler an, diese Null-Überprüfungen auszulassen, wobei angenommen wird, dass alle verknüpften Speicher Belegungen dem Standard entsprechen. Dies gilt nicht für explizite nicht auslösende `operator new` Überladungen, die mithilfe eines zusätzlichen Parameters vom Typ deklariert werden `std::nothrow_t` und über eine explizite **`noexcept`** Spezifikation verfügen.

Zum Erstellen eines Objekts im Free-Speicher generiert der Compiler den Code, um seinen Speicher zuzuordnen, und ruft dann seinen Konstruktor auf, um den Arbeitsspeicher zu initialisieren. Da der MSVC-Compiler normalerweise nicht feststellen kann, ob dieser Code mit einer nicht konformen, nicht auslösenden Zuweisung verknüpft wird, generiert er standardmäßig auch eine NULL-Überprüfung, bevor der Konstruktor aufgerufen wird. Dies verhindert eine NULL-Zeiger Dereferenzierung im konstruktorbefehl, wenn eine nicht auslösende Zuordnung fehlschlägt. In den meisten Fällen sind diese Überprüfungen nicht erforderlich, da die Standard `operator new` Zuweisungen anstelle von Null-Zeigern auslösen. Die Überprüfungen haben auch unglückliche Nebeneffekte. Wenn Sie die Codegröße blohe, überfluten Sie den Verzweigungs präktor, und Sie behindern andere nützliche Compileroptimierungen, wie z. b. die devirtualisierung oder die Konstante Propagierung aus dem initialisierten Objekt. Die Überprüfungen sind nur vorhanden, um Code zu unterstützen, der mit *nothrownew. obj* verknüpft ist oder über benutzerdefinierte nicht konforme `operator new` Implementierungen verfügt. Wenn Sie nicht konform verwenden `operator new` , empfiehlt es sich, **/Zc: throwingnew** zu verwenden, um Ihren Code zu optimieren.

Die Option **/Zc: throwingnew** ist standardmäßig deaktiviert, und die [/permissive-](permissive-standards-conformance.md) -Option ist nicht betroffen.

Wenn Sie mit der Link-Zeit Codegenerierung (Link-Time Code Generation, LTCG) kompilieren, müssen Sie **/Zc: throwingnew**nicht angeben. Wenn Ihr Code mit LTCG kompiliert wird, kann der Compiler erkennen, ob die standardmäßige, konforme `operator new` Implementierung verwendet wird. Wenn dies der Fall ist, lässt der Compiler die Null-Überprüfungen automatisch aus. Der Linker sucht nach dem **/ThrowingNew** -Flag, um zu ermitteln, ob die Implementierung von `operator new` konform ist. Sie können dieses Flag für den Linker angeben, indem Sie diese Direktive in die Quelle für die neue Implementierung des benutzerdefinierten Operators einschließen:

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie im Dropdown Menü **Konfiguration** die Option **alle Konfigurationen**aus.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** , um **/Zc: throwingnew** oder **/Zc: throwingnew** zu schließen, und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)<br/>
[/Zc (Übereinstimmung)](zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[Ausnahmespezifikationen (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Beenden (Ausnahme)](../../standard-library/exception-functions.md#terminate)<br/>
