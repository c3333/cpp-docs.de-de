---
title: Einschränkungen für "/clr"
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: 641e83cb85b6282e8c4c82dfed8c4b44fc4a7e8f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223901"
---
# <a name="clr-restrictions"></a>Einschränkungen für "/clr"

Beachten Sie die folgenden Einschränkungen für die Verwendung von **/clr**:

- In einem strukturierten Ausnahmehandler bestehen Einschränkungen in der Verwendung von `_alloca` bei der Kompilierung mit **/clr**. Weitere Informationen finden Sie unter [_alloca](../../c-runtime-library/reference/alloca.md).

- Die Verwendung der Fehlerprüfung zur Laufzeit ist mit **/clr** ungültig. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden von systemeigenen Laufzeitprüfungen](/visualstudio/debugger/how-to-use-native-run-time-checks).

- Wenn **/clr** zum Kompilieren eines Programms verwendet wird, das nur C++-Standardsyntax verwendet, gelten die folgenden Richtlinien für die Verwendung von Inlineassembly:

  - Bei Inlineassemblycode, der Kenntnis des nativen Stapellayouts unterstellt, Aufrufkonventionen außerhalb der aktuellen Funktion oder anderen spezifischen Informationen über den Computer kann es zu einem Fehler kommen, wenn diese Kenntnis auf den Stapelrahmen für eine verwaltete Funktion angewendet wird. Funktionen, die Inlineassemblycode enthalten, werden als nicht verwaltete Funktionen erstellt, als ob sie in einem separaten Modul platziert wären, das ohne **/clr** kompiliert wird.

  - Inlineassemblycode in Funktionen, die als Kopie konstruierte Funktionsparameter übergeben, wird nicht unterstützt.

- Die [vprintf-Funktionen](../../c-runtime-library/vprintf-functions.md) können aus einem mit **/clr** kompilierten Programm nicht aufgerufen werden.

- Der Modifizierer [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) wird unter /clr ignoriert.

- Die mit [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) festgelegte Übersetzerfunktion betrifft nur Catches in nicht verwaltetem Code. Weitere Informationen finden Sie unter [Ausnahmebehandlung](../../extensions/exception-handling-cpp-component-extensions.md).

- Der Vergleich von Funktionszeigern ist unter **/clr** nicht zulässig.

- Die Verwendung von Funktionen ohne vollständige Prototypen ist unter **/clr** nicht zulässig.

- Die folgenden Compileroptionen werden mit **/clr** nicht unterstützt:

  - **/EHsc** und **/EHs** (**/clr** impliziert **/EHa** (siehe [/EH (Ausnahmebehandlungsmodell)](eh-exception-handling-model.md))

  - **/fp:strict** und **/fp:except** (siehe [/fp (Festlegen des Gleitkommaverhaltens)](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/GM](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/Zi](z7-zi-zi-debug-information-format.md)

- Die Kombination der Präprozessordefinition `_STATIC_CPPLIB` (`/D_STATIC_CPPLIB`) und der Compileroption **/clr** wird nicht unterstützt. Dies rührt daher, dass die Definition zum Linken Ihrer Anwendung mit der statischen C++-Multithread-Standardbibliothek führen würde, was nicht unterstützt wird. Weitere Informationen finden Sie im Thema [/MD, /MT, /LD (Laufzeitbibliothek verwenden)](md-mt-ld-use-run-time-library.md).

- Bei der Verwendung von **/Zi** mit **/clr**, gibt es Auswirkungen auf die Leistung. Weitere Informationen finden Sie unter [/Zi](z7-zi-zi-debug-information-format.md).

- Wenn Sie ein breit Zeichen an eine .NET Framework Ausgabe Routine übergeben, ohne auch [/Zc: wchar_t](zc-wchar-t-wchar-t-is-native-type.md) anzugeben, oder ohne das Zeichen in umwandeln zu müssen, **`__wchar_t`** wird die Ausgabe als angezeigt `unsigned short int` . Beispiel:

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md) wird beim Kompilieren mit **/clr** ignoriert, es sei denn, eine Funktion steht unter `#pragma` [unmanaged](../../preprocessor/managed-unmanaged.md) oder die Funktion muss zu nativ kompiliert werden. In diesem Fall generiert der Compiler die Warnung C4793, die standardmäßig deaktiviert ist.

- Informationen zu den Anforderungen an die Funktionssignatur einer verwalteten Anwendung finden Sie unter [/ENTRY](entry-entry-point-symbol.md).

- Mit **/openmp** und **/clr** kompilierte Anwendungen können nur in einem einzelnen Appdomain-Prozess ausgeführt werden.  Weitere Informationen finden Sie unter [/openmp (OpenMP 2.0-Unterstützung aktivieren)](openmp-enable-openmp-2-0-support.md).

- Funktionen, die eine variable Anzahl von Argumenten (Varargs) akzeptieren, werden als native Funktionen generiert. Alle verwalteten Datentypen an der variablen Argumentposition werden in native Typen gemarshallt. Beachten Sie, dass es sich bei <xref:System.String?displayProperty=fullName>-Typen tatsächlich um Zeichenfolgen aus Breitzeichen handelt, sie aber in Zeichenfolgen aus Einzelbytezeichen gemarshallt werden. Wenn ein printf-Spezifizierer „%S (wchar_t*)“ ist, wird er stattdessen zu einer „%s“-Zeichenfolge gemarshallt.

- Bei der Verwendung des va_arg-Makros erhalten Sie beim Kompilieren mit **/clr:pure** möglicherweise unerwartete Ergebnisse. Weitere Informationen finden Sie unter [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). Die Compileroptionen **/clr:pure** und **/clr:safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 und höher nicht unterstützt. Code, der "pure" oder "safe" sein muss, sollte nach C# portiert werden.

- Aus verwaltetem Code sollten keine Funktionen aufgerufen werden, die einen Stackwalk ausführen,um Parameterinformationen (Funktionsargumente) abzurufen; die P/Invoke-Schicht bewirkt, dass die Informationen weiter unten im Stapel platziert sind.  Kompilieren Sie beispielsweise nicht proxy/stub mit **/clr**.

- Funktionen werden wann immer möglich in verwalteten Code kompiliert, aber nicht alle C++-Konstrukte können in verwalteten Code übersetzt werden.  Diese Bestimmung erfolgt Funktion für Funktion. Wenn irgendein Teil einer Funktion nicht in verwalteten Code konvertiert werden kann, wird stattdessen die gesamte Funktion in nativen Code konvertiert. Die folgenden Fälle hindern den Compiler an der Generierung von verwaltetem Code.

  - Vom Compiler generierte Thunks oder Hilfsfunktionen. Für alle Funktionsaufrufe mithilfe eines Funktionszeigers, einschließlich virtueller Funktionsaufrufe, werden native Thunks generiert.

  - Funktionen, die `setjmp` oder `longjmp` aufrufen.

  - Funktionen, die bestimmte intrinsische Routinen verwenden, um Computerressourcen direkt zu bearbeiten. Beispielsweise führen die Verwendung von `__enable` und `__disable`, `_ReturnAddress` und `_AddressOfReturnAddress` oder von Multimedia-Intrinsics alle zu nativem Code.

  - Funktionen, die auf die Anweisung `#pragma unmanaged` folgen. (Beachten Sie, dass die Umkehrung, `#pragma managed`, ebenfalls unterstützt wird.)

  - Eine Funktion, die Verweise auf ausgerichtete Typen enthält, d.h. Typen, die mithilfe von `__declspec(align(...))` deklariert wurden.

## <a name="see-also"></a>Siehe auch

- [/clr (Common Language Runtime-Kompilierung)](clr-common-language-runtime-compilation.md)
