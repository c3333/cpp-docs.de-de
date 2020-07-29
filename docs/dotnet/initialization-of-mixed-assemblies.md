---
title: Initialisierung gemischter Assemblys
ms.date: 03/09/2018
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: c0f84474e86f0287469a31c310ab0e7e70c8a22c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225643"
---
# <a name="initialization-of-mixed-assemblies"></a>Initialisierung gemischter Assemblys

Windows-Entwickler müssen immer die Loadersperre warnen, wenn Sie Code während ausführen `DllMain` . Beim Umgang mit C++/CLR-Assemblys mit gemischtem Modus müssen jedoch einige zusätzliche Aspekte berücksichtigt werden.

Der Code in [DllMain](/windows/win32/Dlls/dllmain) darf nicht auf die .NET Common Language Runtime (CLR) zugreifen. Dies bedeutet, dass `DllMain` keine verwalteten Funktionen direkt oder indirekt aufrufen sollte. verwalteter Code sollte in nicht deklariert oder implementiert werden, `DllMain` und es sollte weder Garbage Collection noch das automatische Laden von Bibliotheken innerhalb von stattfinden `DllMain` .

## <a name="causes-of-loader-lock"></a>Ursachen für die Loadersperre

Mit der Einführung der .NET-Plattform gibt es zwei unterschiedliche Mechanismen für das Laden eines Ausführungs Moduls (exe oder dll): einen für Windows, der für nicht verwaltete Module verwendet wird, und einen für die CLR, der .NET-Assemblys lädt. Das Problem beim Laden gemischter DLLs konzentriert sich auf den Loader des Microsoft Windows-Betriebssystems.

Wenn eine Assembly, die nur .NET-Konstrukte enthält, in einen Prozess geladen wird, kann der CLR-Loader alle notwendigen Lade- und Initialisierungsaufgaben selbst ausführen. Jedoch muss bei gemischten Assemblys auch das Windows-Ladeprogramm verwendet werden, da sie nativen Code und native Daten enthalten können.

Das Windows-Lade Modul stellt sicher, dass kein Code auf Code oder Daten in dieser DLL zugreifen kann, bevor Sie initialisiert wurde, und dass kein Code die dll redundant laden kann, während Sie teilweise initialisiert ist. Zu diesem Zweck verwendet das Windows-Lade Modul einen Prozess-globalen kritischen Abschnitt (häufig als "Loadersperre" bezeichnet), der den unsicheren Zugriff während der Initialisierung des Moduls verhindert. Daher ist der Ladevorgang für viele klassische Deadlockszenarien anfällig. Bei gemischten Assemblys erhöhen die folgenden zwei Szenarien das Deadlockrisiko:

- Erstens: Wenn Benutzer versuchen, in Microsoft Intermediate Language (MSIL) kompilierte Funktionen auszuführen, wenn die Loadersperre aufrechterhalten wird (z. b. aus `DllMain` oder in statischen Initialisierern), kann dies zu einem Deadlock führen. Beachten Sie den Fall, in dem die MSIL-Funktion auf einen Typ in einer Assembly verweist, die nicht geladen wurde. Die CLR versucht, diese Assembly automatisch zu laden, was erfordern kann, dass das Windows-Ladeprogramm von der Loadersperre blockiert wird. Ein Deadlock tritt auf, da die Loadersperre bereits von Code an früherer Stelle in der-Rückruf Sequenz gespeichert wird. Das Ausführen von MSIL unter der Loadersperre garantiert jedoch nicht, dass ein Deadlock auftritt, sodass dieses Szenario schwierig zu diagnostizieren und zu beheben ist. In einigen Fällen, z. b. wenn die DLL des referenzierten Typs keine nativen Konstrukte enthält und alle Abhängigkeiten keine nativen Konstrukte enthalten, ist es nicht erforderlich, dass das Windows-Lade Modul die .NET-Assembly des referenzierten Typs lädt. Darüber hinaus wurden die erforderliche Assembly oder ihre gemischten nativen/.NET-Abhängigkeiten möglicherweise bereits durch anderen Code geladen. Folglich kann die Vorhersage eines Deadlocks schwierig sein und abhängig von der Konfiguration des Zielcomputers variieren.

- Zweitens hat die CLR beim Laden von DLLs in den Versionen 1,0 und 1,1 der .NET Framework angenommen, dass die Loadersperre nicht aufrechterhalten wurde, und hat mehrere Aktionen ausgeführt, die unter der Loadersperre ungültig sind. Vorausgesetzt, dass die Loadersperre nicht aufrechterhalten wird, ist eine gültige Annahme für reine .NET-DLLs, aber da gemischte DLLs Native Initialisierungs Routinen ausführen, benötigen Sie das Native Windows-Lade Modul und somit die Loadersperre. Also bestand bei den Versionen 1.0 und 1.1 von .NET Framework auch dann die geringe Möglichkeit eines nichtdeterministischen Deadlocks, wenn der Entwickler nicht versuchte, MSIL-Funktionen während der DLL-Initialisierung auszuführen.

Der gesamte Nichtdeterminismus wurde aus dem Prozess des Ladens gemischter DLLs entfernt. Dies wurde mit diesen Änderungen erreicht:

- Die CLR geht beim Laden von gemischten DLLs nicht mehr von falschen Annahmen aus.

- Nicht verwaltete und verwaltete Initialisierung erfolgen in zwei separaten und unterschiedlichen Stufen. Die nicht verwaltete Initialisierung wird zuerst ausgeführt (über DllMain), und die verwaltete Initialisierung erfolgt anschließend über eine. NET-unterstütztes `.cctor` Konstrukt. Letzteres ist für den Benutzer vollständig transparent, wenn **/Zl** oder **/NODEFAULTLIB** verwendet wird. Weitere Informationen finden Sie unter[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md) und [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) .

Die Loadersperre kann zwar immer noch auftreten, jetzt aber reproduzierbar, und wird erkannt. Wenn `DllMain` MSIL-Anweisungen enthält, generiert der Compiler die Warnung [Compilerwarnung (Stufe 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Darüber hinaus versucht die CRT oder die CLR, Versuche zu erkennen und zu melden, die MSIL unter der Loadersperre auszuführen. CRT-Erkennung führt zum Laufzeitdiagnose-C-Laufzeitfehler R6033.

Im weiteren Verlauf dieses Dokuments werden die verbleibenden Szenarien, für die MSIL unter der Loadersperre ausgeführt werden kann, Lösungen für das Problem unter jedem dieser Szenarien und Debugverfahren beschrieben.

## <a name="scenarios-and-workarounds"></a>Szenarien und Problemumgehungen

Es gibt mehrere Situationen, in denen Benutzercode MSIL unter der Loadersperre ausführen kann. Der Entwickler muss sicherstellen, dass die Benutzercodeimplementierung nicht versucht, in allen diesen Fällen MSIL-Anweisungen auszuführen. In den folgenden Unterabschnitten werden alle Möglichkeiten mit einer Erläuterung der Problemlösung in den häufigsten Fällen beschrieben.

### <a name="dllmain"></a>DllMain

Die- `DllMain` Funktion ist ein benutzerdefinierter Einstiegspunkt für eine DLL. Wenn vom Benutzer nicht anders angegeben, wird `DllMain` jedes Mal aufgerufen, wenn ein Prozess oder Thread der enthaltenden DLL angefügt oder davon getrennt wird. Da dieser Aufruf auftreten kann, während die Loadersperre aktiv ist, sollte keine benutzerdefinierte `DllMain` -Funktion in MSIL kompiliert werden. Darüber hinaus kann keine Funktion in der Aufrufstruktur, die in `DllMain` wurzelt, in MSIL kompiliert werden. Um hier Probleme zu lösen, sollte der Codeblock, der `DllMain` definiert, mit „#pragma“ `unmanaged`geändert werden. Das gleiche sollte für jede Funktion getan werden, die `DllMain` aufruft.

In Fällen, in denen diese Funktionen eine Funktion aufrufen müssen, die eine MSIL-Implementierung für andere aufrufende Kontexte erfordert, kann eine Duplizierungsstrategie verwendet werden, wo .NET und eine native Version der gleichen Funktion erstellt werden.

Alternativ kann, wenn `DllMain` nicht erforderlich ist bzw. nicht unter der Loadersperre ausgeführt werden muss, die vom Benutzer bereitgestellte `DllMain` Implementierung entfernt und damit das Problem gelöst werden.

Wenn DllMain versucht, MSIL direkt auszuführen, führt dies zu [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) . Der Compiler kann jedoch keine Fälle erkennen, in denen DllMain eine Funktion in einem anderen Modul aufruft, das wiederum versucht, MSIL auszuführen.

Weitere Informationen zu diesem Szenario finden Sie unter [Hindernisse bei der Diagnose](#impediments-to-diagnosis).

### <a name="initializing-static-objects"></a>Initialisieren von statischen Objekten

Initialisieren von statischen Objekten kann zu Deadlocks führen, wenn ein dynamischer Initialisierer erforderlich ist. In einfachen Fällen, z. b. Wenn eine statische Variable einem Wert zugewiesen wird, der zum Zeitpunkt der Kompilierung bekannt ist, ist keine dynamische Initialisierung erforderlich, sodass kein Deadlockrisiko besteht. Allerdings erfordern alle statischen Variablen, die durch Funktionsaufrufe, Konstruktoraufrufe oder Ausdrücke initialisiert werden, die zur Kompilierzeit nicht ausgewertet werden können, während der Initialisierung des Moduls auszuführenden Code.

Der folgende Code zeigt Beispiele für statische Initialisierer, die dynamische Initialisierung erfordern: ein Funktionsaufruf, eine Objektkonstruktion und eine Initialisierung eines Zeigers. (Diese Beispiele sind nicht statisch, sondern werden im globalen Gültigkeitsbereich als definiert angenommen, der die gleiche Auswirkung hat.)

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

Das Deadlockrisiko hängt davon ab, ob das enthaltende Modul mit **/clr** kompiliert, und ob MSIL ausgeführt wird. Insbesondere wenn die statische Variable ohne **/clr** kompiliert wird (oder sich in einem #pragma- `unmanaged` -Block befindet), und der dynamische Initialisierer erforderlich ist, um ihre Ergebnisse der Ausführung der MSIL-Anweisungen zu initialisieren, kann ein Deadlock auftreten. Dies liegt daran, dass bei Modulen, die ohne **/CLR**kompiliert werden, die Initialisierung statischer Variablen von DllMain durchgeführt wird. Im Gegensatz dazu werden statische Variablen, die mit **/CLR** kompiliert werden, von initialisiert `.cctor` , nachdem die nicht verwaltete Initialisierungsphase abgeschlossen und die Loadersperre freigegeben wurde.

Es gibt eine Reihe von Lösungen zu einem Deadlock, das durch die dynamische Initialisierung von statischen Variablen verursacht wird (etwa nach erforderlichem Zeitaufwand zum Beheben des Problems angeordnet):

- Die Quelldatei, die die statische Variable enthält, kann mit **/clr**kompiliert werden.

- Alle von der statischen Variablen aufgerufenen Funktionen können mit der #pragma- `unmanaged` -Richtlinie in nativen Code kompiliert werden.

- Duplizieren Sie manuell den Code, von dem die statische Variable abhängig ist, sodass Sie eine .NET- und eine native Version mit unterschiedlichen Namen bereitstellen. Entwickler können dann die native Version der nativen statischen Initialisierer aufrufen und die .NET-Version an anderer Stelle.

### <a name="user-supplied-functions-affecting-startup"></a>Benutzerdefinierte Funktionen, die den Start beeinflussen

Es gibt mehrere benutzerdefinierte Funktionen, von denen Bibliotheken zur Initialisierung beim Start abhängig sind. Beispielsweise werden beim globalen Überladen von Operatoren in C++, z. b. den **`new`** **`delete`** Operatoren und, die vom Benutzer bereitgestellten Versionen überall verwendet, einschließlich der Initialisierung und Zerstörung der C++-Standard Bibliothek. Folglich werden von der C++-Standard Bibliothek und vom Benutzer bereitgestellte statische Initialisierer alle vom Benutzer bereitgestellten Versionen dieser Operatoren aufrufen.

Wenn die vom Benutzer bereitgestellten Versionen in MSIL kompiliert werden, versuchen diese Initialisierer, MSIL-Anweisungen ausführen, während die Loadersperre aktiviert ist. Ein vom Benutzer bereitgestellter `malloc` hat die gleichen folgen. Um dieses Problem zu lösen, müssen alle diese Überladungen oder benutzerdefinierten Definitionen als nativer Code mit der #pragma- `unmanaged` -Richtlinie implementiert werden.

Weitere Informationen zu diesem Szenario finden Sie unter [Hindernisse bei der Diagnose](#impediments-to-diagnosis).

### <a name="custom-locales"></a>Benutzerdefinierte Gebietsschemas

Wenn der Benutzer ein benutzerdefiniertes globales Gebiets Schema bereitstellt, wird dieses Gebiets Schema zum Initialisieren aller zukünftigen e/a-Streams verwendet, einschließlich Datenströme, die statisch initialisiert werden. Wenn dieses globale Gebietsschemaobjekt in MSIL kompiliert wird, können in MSIL kompilierte Gebietsschemaobjekt-Memberfunktionen aufgerufen werden, während die Loadersperre aktiviert ist.

Es gibt drei Optionen zur Lösung dieses Problems:

Die Quelldateien, die alle globalen E/A-Stromdefinitionen enthalten, können mit der Option **/clr** kompiliert werden. Dadurch wird verhindert, dass Ihre statischen Initialisierer unter der Loadersperre ausgeführt werden.

Die Funktionsdefinitionen des benutzerdefinierten Gebietsschemas können mit der #pragma- `unmanaged` -Richtlinie in nativen Code kompiliert werden.

Legen Sie das benutzerdefinierte Gebietsschema nicht als globales Gebietsschema fest, solange die Loadersperre nicht freigegeben ist. Konfigurieren Sie dann explizit die während der Initialisierung mit dem benutzerdefinierten Gebietsschema erstellten E/A-Ströme.

## <a name="impediments-to-diagnosis"></a>Diagnosehindernisse

In einigen Fällen ist es schwierig, die Quelle von Deadlocks zu erkennen. In den folgenden Unterabschnitten werden diese Szenarien und die Möglichkeiten, diese Probleme zu umgehen, erörtert.

### <a name="implementation-in-headers"></a>Implementierung in Headern

In bestimmten Fällen können Funktionsimplementierungen in Headerdateien die Diagnose erschweren. Inlinefunktionen und Vorlagencode erfordern, dass Funktionen in einer Headerdatei angegeben werden.  Die Programmiersprache C++ gibt die One Definition Rule (Eine-Definition-Regel) an, die erzwingt, dass alle Implementierungen von Funktionen gleichen Namens semantisch gleichwertig sind. In der Folge muss der C++-Linker beim Zusammenführen von Objektdateien, die doppelte Implementierungen einer bestimmten Funktion aufweisen, nichts Spezielles berücksichtigen.

Vor Visual Studio 2005 wählt der Linker einfach die größte dieser semantisch äquivalenten Definitionen aus, um vorwärts Deklarationen zu unterstützen, und Szenarios, in denen verschiedene Optimierungs Optionen für verschiedene Quelldateien verwendet werden. Es wird ein Problem für gemischte Native/. NET-DLLs erstellt.

Da derselbe Header sowohl in C++-Dateien mit aktiviertem und deaktiviertem **/CLR** enthalten sein kann oder ein #include in einen-Block eingebunden werden kann `#pragma unmanaged` , ist es möglich, sowohl MSIL-als auch native Versionen von Funktionen zu haben, die Implementierungen in Headern bereitstellen. Die Semantik von MSIL- und nativen Implementierungen unterscheidet sich in Bezug auf die Initialisierung unter der Loadersperre, was effektiv die One Definition Rule verletzt. Wenn also der Linker die größte Implementierung wählt, könnte er selbst dann die MSIL-Version einer Funktion wählen, wenn sie explizit an anderer Stelle mit der nicht verwalteten #pragma-Direktive in nativen Code kompiliert wäre. Um sicherzustellen, dass eine MSIL-Version einer Vorlage oder Inline Funktion niemals unter der Loadersperre aufgerufen wird, muss jede Definition jeder solchen Funktion, die unter der Loadersperre aufgerufen wird, mit der- `#pragma unmanaged` Direktive geändert werden. Wenn die Header Datei von einem Drittanbieter abgeleitet ist, ist es am einfachsten, diese Änderung vorzunehmen, indem Sie die-Direktive per Push und Pop an `#pragma unmanaged` die #include-Direktive für die problematische Header Datei senden. (Ein Beispiel finden Sie [unter Managed, nicht verwaltet](../preprocessor/managed-unmanaged.md) .) Diese Strategie funktioniert jedoch nicht bei Headern, die anderen Code enthalten, der .NET-APIs direkt aufruft.

Zur Erleichterung für Benutzer, die sich mit Loadersperren auseinandersetzen müssen, wählt der Linker die native Implementierung über die verwaltete Direktive, wenn er mit beiden konfrontiert wird. Mit dieser Standardeinstellung werden die oben genannten Probleme vermieden. Aufgrund ungelöster Probleme mit dem Compiler gibt es jedoch zwei Ausnahmen von dieser Regel in dieser Version:

- Der Aufrufe einer Inline Funktion erfolgt über einen globalen statischen Funktionszeiger. Dieses Szenario ist bemerkenswert, da virtuelle Funktionen über globale Funktionszeiger aufgerufen werden. Beispiel:

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>Diagnose im Debugmodus

Alle Diagnosen von Loadersperrenproblemen sollten mit Debugbuilds erfolgen. Releasebuilds bringen vielleicht keine Diagnoseergebnisse, und die im Releasemodus durchgeführten Optimierungen könnten einige der „MSIL unter Loadersperre“-Szenarien verdecken.

## <a name="how-to-debug-loader-lock-issues"></a>Debuggen von Problemen mit Loadersperren

Die Diagnose, die die CLR beim Aufruf einer MSIL-Funktion generiert, bewirkt, dass die CLR die Ausführung unterbricht. Dies bewirkt wiederum, dass die Visual C++ Debugger im gemischten Modus ebenfalls angehalten wird, wenn die zu debuggende Komponente ausgeführt wird. Beim Anfügen an den Prozess ist es jedoch nicht möglich, eine verwaltete Aufruf Liste für die zu debuggende Komponente mit dem gemischten Debugger zu erhalten.

Um die bestimmte MSIL-Funktion zu identifizieren, die unter der Loadersperre aufgerufen wurde, sollten Entwickler die folgenden Schritte ausführen:

1. Stellen Sie sicher, dass für „mscoree.dll“ und „mscorwks.dll“ Symbole verfügbar sind.

   Sie können die Symbole auf zwei Arten verfügbar machen. Erstens können die PDBs für „mscoree.dll“ und „mscorwks.dll“ dem Symbolsuchpfad hinzugefügt werden. Öffnen Sie das Dialogfeld Symbol Suchpfad Optionen, um Sie hinzuzufügen. (Wählen Sie **im Menü** Extras die **Option Optionen**aus. Öffnen Sie im linken Bereich des Dialog Felds **Optionen** den Knoten **Debuggen** , und wählen Sie **Symbole**aus.) Fügen Sie den Pfad zum mscoree.dll und mscorwks.dll PDB-Dateien der Suchliste hinzu. Diese PDB-Dateien werden in den %VSINSTALLDIR%\SDK\v2.0\symbols installiert. Wählen Sie **OK** aus.

   Zweitens können die PDBs für „mscoree.dll“ und „mscorwks.dll“ vom Microsoft-Symbolserver heruntergeladen werden. Öffnen Sie zum Konfigurieren des Symbolservers das Dialogfeld für die Symbolsuchpfad-Optionen. (Wählen Sie **im Menü** Extras die **Option Optionen**aus. Öffnen Sie im linken Bereich des Dialog Felds **Optionen** den Knoten **Debuggen** , und wählen Sie **Symbole**aus.) Fügen Sie diesen Suchpfad der Suchliste hinzu: `https://msdl.microsoft.com/download/symbols` . Fügen Sie dem Symbolservercache-Textfeld ein Symbolcacheverzeichnis hinzu. Wählen Sie **OK** aus.

1. Legen Sie den Debugmodus auf nur nativ fest.

   Öffnen Sie das **Eigenschaften** Raster für das Startprojekt in der Projekt Mappe. Wählen Sie **Konfigurationseigenschaften** > **Debuggen** aus. Legen Sie den **Debuggertyp** auf **nur native**fest.

1. Starten Sie den Debugger (F5).

1. Wenn die **/CLR** -Diagnose generiert wurde, wählen Sie **wiederholen** aus, und wählen Sie dann unter **brechen**aus.

1. Öffnen Sie das Fenster „Aufrufliste“. (Wählen Sie in der Menüleiste **Debuggen**  >  aus. **Windows**  >  Die **aufrufsstapel**.) Der problematische `DllMain` oder statische Initialisierer wird mit einem grünen Pfeil gekennzeichnet. Wenn die auslösende Funktion nicht erkannt wird, müssen die folgenden Schritte ausgeführt werden, um sie zu finden.

1. Öffnen Sie das **direkt** Fenster (Klicken Sie in der Menüleiste auf **Debuggen**von  >  **Fenstern**  >  **direkt**.)

1. Geben Sie `.load sos.dll` im **direkt** Fenster ein, um den SOS-Debugdienst zu laden.

1. Geben Sie `!dumpstack` im **direkt** Fenster ein, um eine komplette Liste des internen **/CLR** -Stapels zu erhalten.

1. Suchen Sie nach der ersten (am unteren Rand des Stapels liegenden) Instanz von _CorDllMain (wenn `DllMain` das Problem verursacht) oder _VTableBootstrapThunkInitHelperStub oder GetTargetForVTableEntry (wenn ein statischer Initialisierer das Problem verursacht). Der Stapeleintrag direkt unterhalb dieses Aufrufs ist der Aufruf der MSIL-implementierten Funktion, die eine Ausführung unter der Loadersperre versuchte.

1. Wechseln Sie zu der Quelldatei und der Zeilennummer, die im vorherigen Schritt identifiziert wurden, und beheben Sie das Problem mithilfe der Szenarien und Lösungen, die im Abschnitt Szenarios beschrieben werden.

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung

Im folgenden Beispiel wird gezeigt, wie Sie die Loadersperre vermeiden, indem Sie Code aus `DllMain` in den Konstruktor eines globalen Objekts verschieben.

In diesem Beispiel gibt es ein Global verwaltetes Objekt, dessen Konstruktor das verwaltete Objekt enthält, das sich ursprünglich in befand `DllMain` . Der zweite Teil dieses Beispiels verweist auf die Assembly und erstellt eine Instanz des verwalteten Objekts, um den Modulkonstruktor aufzurufen, der die Initialisierung durchführt.

### <a name="code"></a>Code

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker does not throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

In diesem Beispiel werden Probleme bei der Initialisierung gemischter Assemblys veranschaulicht:

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

Mit diesem Code wird die folgende Ausgabe generiert:

```Output
Module ctor initializing based on global instance of class.

Test called so linker does not throw away unused object.
```

## <a name="see-also"></a>Siehe auch

[Gemischte (Native und verwaltete) Assemblys](../dotnet/mixed-native-and-managed-assemblies.md)
