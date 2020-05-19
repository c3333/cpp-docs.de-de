---
title: Bewährte Methoden für die Optimierung
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 541114b4cbf7d3d063e48b50ab265b4c95c6237c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328454"
---
# <a name="optimization-best-practices"></a>Bewährte Methoden für die Optimierung

In diesem Dokument werden einige Best Practices für das Optimieren von C++-Programmen in Visual Studio beschrieben.

## <a name="compiler-and-linker-options"></a>Optionen für Compiler und Linker

### <a name="profile-guided-optimization"></a>Profilgesteuerte Optimierung

Visual C++ unterstützt die *profilgesteuerte Optimierung* (PGO). Diese Optimierung verwendet Profildaten aus früheren Ausführungen einer instrumentierten Version einer Anwendung, um eine spätere Optimierung der Anwendung zu erreichen. Das Verwenden der profilgesteuerte Optimierung (PGO) kann zeitaufwendig sein, sodass sie möglicherweise nicht von allen Entwicklern genutzt wird. Wir empfehlen jedoch, die profilgesteuerte Optimierung (PGO) für das endgültige Releasebuild eines Projekts zu verwenden. Weitere Informationen finden Sie unter [Profilgesteuerte Optimierungen](profile-guided-optimizations.md).

Außerdem wurden die *Optimierung des gesamten Programms* (auch Link-Zeitcodegenerierung genannt) sowie die **/O1**- und **/O2**-Optimierungen verbessert. Allgemein gilt, daß eine Anwendung, die mit einer dieser Optionen kompiliert wurde, sich durch eine höhere Geschwindigkeit auszeichnet als dieselbe Anwendung, die mit einem früheren Compiler kompiliert wurde.

Weitere Informationen finden Sie unter [/GL (Optimierung des gesamten Programms)](reference/gl-whole-program-optimization.md) und [/O1, /O2 (Größe minimieren, Geschwindigkeit maximieren)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Zu verwendende Optimierungsebene

Wenn es möglich ist, sollten endgültige Releasebuilds auf jeden Fall unter Verwendung der profilgesteuerten Optimierung (PGO) kompiliert werden. Falls eine profilgesteuerte Optimierung (PGO) nicht möglich sein sollte, weil z. B. die Infrastruktur zur Ausführung der instrumentierten Builds nicht ausreicht oder kein Zugang zu Szenarios besteht, wird das Ausführen des Buildvorgangs mit der Kompletten Programmoptimierung empfohlen.

Der **/Gy**-Switch ist auch sehr hilfreich. Er generiert ein separates COMDAT für jede Funktion und verleiht dem Linker dadurch mehr Flexibilität beim Entfernen COMDATs, auf die nicht verwiesen wird, und bei der COMDAT-Faltung. Der einzige Nachteil der Verwendung von **/Gy** ist, dass Probleme beim Debuggen entstehen können. Diese Option sollte also generell verwendet werden. Weitere Informationen finden Sie unter [/Gy (Funktionslevel-Linking aktivieren)](reference/gy-enable-function-level-linking.md).

Beim Verknüpfen in 64-Bit-Umgebungen wird die Verwendung der **/OPT:REF,ICF**-Linkeroption empfohlen, und in 32-Bit-Umgebungen wird **/OPT:REF** empfohlen. Weitere Informationen finden Sie unter [/OPT (Optimierungen)](reference/opt-optimizations.md).

Es wird dringend empfohlen, Debugsymbole zu generieren. Dies gilt sogar für optimierte Releasebuilds. Die Symbole beeinflussen den generierten Code nicht, erleichtern jedoch das ggf. nötige Debuggen der Anwendung sehr.

### <a name="floating-point-switches"></a>Gleitkommaswitches

Die **/Op**-Compileroption wurde entfernt, und die folgenden vier Compileroptionen für Gleitkommaoptimierungen wurden hinzugefügt:

|||
|-|-|
|**/fp:precise**|Dies ist die als Standard empfohlene Option, die in den meisten Fällen verwendet werden sollte.|
|**/fp:fast**|Empfohlen für die Fälle, in denen die Leistung von höchster Wichtigkeit ist, z. B. bei Spielen. Dies führt zur schnellsten Programmausführung.|
|**/fp:strict**|Empfohlen für die Fälle, in denen präzise Gleitkommaausnahmen und IEEE-Verhalten gewünscht werden. Dies führt zur langsamsten Programmausführung.|
|**/fp:except[-]**|Kann in Verbindung mit **/fp:strict** oder **/fp:precise** verwendet, nicht jedoch mit **/fp:fast**.|

Weitere Informationen finden Sie unter [/fp (Festlegen des Gleitkommaverhaltens)](reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>Optimierung mit declspecs

In diesem Abschnitt werden zwei declspecs erläutert, die zur Leistungssteigerung in Programmen verwendet werden können: `__declspec(restrict)` und `__declspec(noalias)`.

Die `restrict`-declspec kann nur auf Funktionsdeklarationen angewendet werden, die einen Zeiger zurückgeben, z. B. `__declspec(restrict) void *malloc(size_t size);`

Die `restrict`-declspec wird bei Funktionen verwendet, die Zeiger ohne Alias zurückgeben. Dieses Schlüsselwort wird für die C-Laufzeitbibliotheksimplementierung von `malloc` verwendet, da es niemals einen im aktuellen Programm bereits verwendeten Zeigerwert zurückgibt (außer bei unzulässigen Vorgängen, z. B. beim Verwenden von Speicher, nachdem dieser freigegeben wurde).

Die `restrict`-declspec liefert dem Compiler weitere Informationen zur Durchführung von Compileroptimierungen. Eine der schwierigsten Aufgaben des Compilers ist es, zu ermitteln, welche Zeiger als Alias für andere Zeiger dienen. Die Verwendung solcher Informationen ist für den Compiler ausgesprochen hilfreich.

Es muss aber erwähnt werden, dass diese Informationen vom Compiler als Zusicherung behandelt werden, d. h., sie werden vom Compiler nicht überprüft. Wenn das Programm diese `restrict`-declspec unpassend verwendet, führt dies u. U. zu einem fehlerhaften Verhalten des Programms.

Weitere Informationen finden Sie unter [restrict](../cpp/restrict.md).

Die `noalias`-declspec wird ebenfalls nur auf Funktionen angewendet, und sie gibt an, dass die Funktion eine halbreine Funktion ist. Eine halbreine Funktion ist eine Funktion, die nur lokale Variablen, Argumente und Dereferenzierungen der ersten Ebene von Argumenten ändert oder auf diese verweist. Diese declspec ist eine Zusicherung für den Compiler. Wenn die Funktion auf Globals oder auf Dereferenzierungen der zweiten Ebene von Zeigerargumenten verweist, generiert der Compiler u. U. Code, zum Abbruch der Anwendung führt.

Weitere Informationen finden Sie unter [noalias](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Optimierung mit Pragmas

Code kann auch mithilfe einer Reihe von nützlichen Pragmas optimiert werden. Zuerst wird `#pragma optimize` erläutert:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Mithilfe dieses Pragmas können Sie für jede einzelne Funktion eine bestimmte Optimierungsstufe festlegen. Diese Möglichkeit eignet sich hervorragend für jene seltenen Fälle, in denen die Anwendung abstürzt, sobald eine Funktion mithilfe der Optimierung kompiliert wurde. Mit diesem Pragma können Sie die Optimierungen für eine einzelne Funktion deaktivieren:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Weitere Informationen finden Sie unter [optimize](../preprocessor/optimize.md).

Das Inlining stellt eine der wichtigsten Optimierungen dar, die der Compiler durchführt. Daher sollen an dieser Stelle einige Pragmas erläutert werden, mit der dieses Verhalten geändert werden kann.

Mit `#pragma inline_recursion` kann angegeben werden, ob die Anwendung bei einem rekursiven Aufruf inlinefähig sein soll. Diese Option ist standardmäßig deaktiviert. Für die flache Rekursion bei kleinen Funktionen können Sie diese Option aktivieren. Weitere Informationen finden Sie unter [inline_recursion](../preprocessor/inline-recursion.md).

Außerdem steht mit `#pragma inline_depth` ein nützliches Pragma zur Beschränkung der Tiefe beim Inlining zur Verfügung. Dieses Pragma kann i. d. R. verwendet werden, wenn Sie die Größe des Programms oder einer Funktion beschränken möchten. Weitere Informationen finden Sie unter [inline_depth](../preprocessor/inline-depth.md).

## <a name="__restrict-and-__assume"></a>__restrict und \__assume

Es gibt mehrere Schlüsselwörter in Visual Studio, die die Leistung unterstützen können: [__restrict](../cpp/extension-restrict.md) und [__assume](../intrinsics/assume.md).

Zuerst muss darauf hingewiesen werden, dass es sich bei `__restrict` und `__declspec(restrict)` um zwei verschiedene Elemente handelt. Obwohl sie gewisse Gemeinsamkeiten aufweisen, unterscheidet sich ihre Semantik. `__restrict` ist ein Typqualifizierer, wie `const` oder `volatile`, wird aber ausschließlich für Zeigertypen eingesetzt.

Ein Zeiger, der durch `__restrict` modifiziert wird, wird als *__restrict-Zeiger* bezeichnet. Ein __restrict-Zeiger ist ein Zeiger, auf den nur über den \__restrict-Zeiger zugegriffen werden kann. Das heißt, mit einem anderen Zeiger kann nicht auf die Daten zugegriffen werden, auf die der \__restrict-Zeiger zeigt.

`__restrict` kann sich als ein sehr leistungsstarkes Tool für den Microsoft C++-Optimierer erweisen, sollte jedoch mit großer Umsicht verwendet werden. Wenn Sie dieses Tool unangemessen verwenden, führt der Optimierer u. U. eine Optimierung durch, die zum Abbruch der Anwendung führt.

Das `__restrict`-Schlüsselwort ersetzt die **/Oa**-Option aus vorherigen Versionen.

Mit `__assume` kann ein Entwickler den Compiler anweisen, Annahmen über den Wert einer Variablen zu treffen.

Beispielsweise teilt `__assume(a < 5);` dem Compiler mit, dass in dieser Zeile des Codes die Variable `a` kleiner als 5 ist. Auch dies ist eine Zusage für den Compiler. Wenn `a` an dieser Stelle im Programm 6 ist, entspricht das Verhalten des Programms nach der Optimierung des Compilers möglicherweise nicht Ihren Erwartungen. `__assume` ist vor Switch-Anweisungen und/oder bedingten Ausdrücken sehr nützlich.

Für `__assume` gelten einige Beschränkungen. Es handelt sich hierbei genau wie bei `__restrict` nur um einen Vorschlag, der vom Compiler ggf. ignoriert werden kann. Zum anderen funktioniert `__assume` derzeit nur mit Ungleichungen aus Variablen und Konstanten. Ungleichungen mit Symbolen werden nicht weitergegeben, beispielsweise „assume(a < b)“.

## <a name="intrinsic-support"></a>Unterstützung für systeminterne Funktionen

Systeminterne Funktionen werden bei Funktionsaufrufen verwendet, bei denen der Compiler auf ein systeminternes Wissen über den Aufruf zurückgreifen kann und keine Funktion in einer Bibliothek aufzurufen braucht. Stattdessen wird der Code für diese Funktion vom Compiler ausgegeben. Die Headerdatei \<intrin.h> enthält alle verfügbaren systeminternen Funktionen für die unterstützten Hardwareplattformen.

Dank systeminterner Funktionen können Programmierer tief in den Code gehen, ohne Assemblys zu verwenden. Die Verwendung systeminterner Funktionen hat mehrere Vorteile:

- Der Code ist besser portabel. Eine Reihe von systeminternen Funktionen sind auf verschiedenen CPU-Architekturen verfügbar.

- Der Code ist leichter lesbar, da er weiterhin in C/C++ geschrieben wird.

- Die Vorteile von Compileroptimierungen können für den Code genutzt werden. Mit der zunehmenden Verbesserung des Compilers verbessert sich auch die Codegenerierung für die systeminternen Funktionen.

Weitere Informationen finden Sie unter [Systeminterne Compilerfunktionen](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Ausnahmen

Die Verwendung von Ausnahmen ist mit Leistungseinbußen verbunden. Wenn Sie try-Blöcke verwenden, die das Ausführen bestimmter Optimierungen durch den Compiler verhindern, führt dies zu einer Reihe von Einschränkungen. Auf x86-Plattformen treten durch try-Blöcke weitere Leistungsminderungen auf, denn während der Codeausführung müssen zusätzliche Zustandsinformationen generiert werden. Auf den 64-Bit-Plattformen verschlechtern try-Blöcke die Leistung nicht so stark. Wenn jedoch eine Ausnahme ausgelöst wird, kann der Prozess für die Suche nach dem Handler und das Entladen des Stapels sehr aufwendig sein.

Deshalb wird empfohlen, try/catch-Blöcke so weit wie möglich zu vermeiden und sie nur dann in den Code einzufügen, wenn dies wirklich unabdingbar ist. Wenn Sie Ausnahmen verwenden müssen, sollten Sie wenn möglich auf synchrone Ausnahmen zurückgreifen. Weitere Informationen finden Sie unter [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Und nicht zu vergessen: Lösen Sie Ausnahmen nur für Ausnahmefälle aus. Das Verwenden von Ausnahmen für die allgemeine Ablaufsteuerung beeinträchtigt i. d. R. die Leistung.

## <a name="see-also"></a>Siehe auch

- [Codeoptimierung](optimizing-your-code.md)
