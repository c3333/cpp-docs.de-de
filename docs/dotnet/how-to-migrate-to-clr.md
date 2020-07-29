---
title: 'Vorgehensweise: Migrieren zu -clr'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
ms.openlocfilehash: 0c21fe585049ebce6383c5d8f673704e7362cd72
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225695"
---
# <a name="how-to-migrate-to-clr"></a>Gewusst wie: Migrieren zu /clr

In diesem Thema werden Probleme erläutert, die beim Kompilieren von System eigenem Code mit **/CLR** auftreten. Weitere Informationen finden Sie unter [/CLR (Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md) . **/CLR** ermöglicht, dass System eigener C++-Code zusätzlich zu anderem nativem C++-Code aufrufen und von .NET-Assemblys aufgerufen wird. Weitere Informationen zu den Vorteilen der Kompilierung mit **/CLR**finden Sie unter [gemischte (Native und verwaltete)](../dotnet/mixed-native-and-managed-assemblies.md) Assemblys und [Native und .NET-Interoperabilität](../dotnet/native-and-dotnet-interoperability.md) .

## <a name="known-issues-compiling-library-projects-with-clr"></a>Bekannte Probleme beim Kompilieren von Bibliotheksprojekten mit /clr

Visual Studio enthält einige bekannte Probleme beim Kompilieren von Bibliotheks Projekten mit **/CLR**:

- Der Code kann Typen zur Laufzeit mit [CRuntimeClass:: FromName](../mfc/reference/cruntimeclass-structure.md#fromname)Abfragen. Wenn sich jedoch ein Typ in einer MSIL. dll-Datei (mit **/CLR**kompiliert) befindet, schlägt der-Aufrufvorgang `FromName` möglicherweise fehl, wenn er vor der Ausführung der statischen Konstruktoren in der verwalteten DLL-Datei ausgeführt wird (das Problem wird nicht angezeigt, wenn der FromName-Befehl nach dem Ausführen von Code in der verwalteten DLL auftritt). Um dieses Problem zu umgehen, können Sie die Konstruktion des verwalteten statischen Konstruktors erzwingen, indem Sie in der verwalteten DLL eine Funktion definieren, sie exportieren und anschließend aus der nativen MFC-Anwendung aufrufen. Beispiel:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Kompilieren mit Visual C++

Bevor Sie **/CLR** für ein beliebiges Modul in Ihrem Projekt verwenden, müssen Sie zuerst das Native Projekt kompilieren und mit Visual Studio 2010 verknüpfen.

Die folgenden Schritte, gefolgt von der Reihenfolge, stellen den einfachsten Pfad zu einer **/CLR** -Kompilierung bereit. Wichtig ist dabei, das Projekt nach jedem dieser Schritte zu kompilieren und auszuführen.

### <a name="versions-prior-to-visual-studio-2003"></a>Versionen vor Visual Studio 2003

Wenn Sie von einer Version vor Visual Studio 2003 auf Visual Studio 2010 aktualisieren, werden möglicherweise Compilerfehler im Zusammenhang mit der erweiterten C++-Standardkonformität in Visual Studio 2003 angezeigt.

### <a name="upgrading-from-visual-studio-2003"></a>Aktualisieren von Visual Studio 2003

Projekte, die mit Visual Studio 2003 erstellt wurden, sollten zunächst auch ohne **/CLR** kompiliert werden, da Visual Studio nun die Kompatibilität von ANSI/ISO und einige wichtige Änderungen verbessert hat. Die Änderung, die wahrscheinlich die größte Aufmerksamkeit erfordert, sind die [Sicherheitsfunktionen in der CRT](../c-runtime-library/security-features-in-the-crt.md). Code, der das CRT verwendet, löst sehr wahrscheinlich Veraltungswarnungen aus. Diese Warnungen können unterdrückt werden, aber die Migration zu den neuen, mit der [Sicherheit erweiterten Versionen der CRT-Funktionen](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) wird bevorzugt, da Sie eine bessere Sicherheit bieten und Sicherheitsprobleme in Ihrem Code offenlegen können.

### <a name="upgrading-from-managed-extensions-for-c"></a>Aktualisieren von Managed Extensions für C++

Ab Visual Studio 2005 wird der mit Managed Extensions for C++ geschriebene Code nicht unter **/CLR**kompiliert.

## <a name="convert-c-code-to-c"></a>Konvertieren von C-Code in C++

Obwohl Visual Studio C-Dateien kompiliert, müssen diese für eine **/CLR** -Kompilierung in C++ konvertiert werden. Der tatsächliche Dateiname muss nicht geändert werden. Sie können **/tp** verwenden (siehe [/TC,/TP,/TC,/TP (Quell Dateityp angeben)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Beachten Sie, dass zwar C++-Quell Code Dateien für **/CLR**erforderlich sind, der Code jedoch nicht für die Verwendung objektorientierter Paradigmen umgestaltet werden muss.

Es ist sehr wahrscheinlich, dass C-Code bei einer Kompilierung als C++-Datei gewisse Änderungen erfordert. Da die C++-Typsicherheitsregeln streng sind, müssen Typkonvertierungen explizit durch Umwandlungen vorgenommen werden. Beispielsweise gibt malloc einen void-Zeiger zurück, kann aber durch Umwandlung einem Zeiger zugewiesen werden, der auf einen beliebigen Typ in C zeigt:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Auch Funktionszeiger sind in C++ streng typsicher, deshalb muss der folgende C-Code geändert werden. In C++ empfiehlt es sich, einen zu erstellen, **`typedef`** der den Funktions Zeigertyp definiert, und diesen Typ dann zum Umwandeln von Funktions Zeigern zu verwenden:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++ verlangt außerdem, dass Funktionen entweder einen Prototyp haben oder vollständig definiert sind, bevor auf sie verwiesen wird oder sie aufgerufen werden können.

Bezeichner, die in C-Code verwendet werden, der Schlüsselwörter in C++ ist (z. b. **`virtual`** , **`new`** , **`delete`** , **`bool`** , **`true`** , **`false`** usw.), müssen umbenannt werden. Dies kann im Allgemeinen durch einfache Such- und Ersetzungsvorgänge erfolgen.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Umkonfigurieren von Projekteinstellungen

Nachdem das Projekt in Visual Studio 2010 kompiliert und ausgeführt wurde, sollten Sie neue Projekt Konfigurationen für **/CLR** erstellen, anstatt die Standardkonfigurationen zu ändern. **/CLR** ist mit einigen Compileroptionen nicht kompatibel, und das Erstellen separater Konfigurationen ermöglicht Ihnen das Erstellen des Projekts als nativ oder verwaltet. Wenn im Dialogfeld Eigenschaften Seiten die Option **/CLR** ausgewählt wird, werden die Projekteinstellungen, die nicht mit **/CLR** kompatibel sind, deaktiviert (und deaktivierte Optionen werden nicht automatisch wieder hergestellt, wenn **/CLR** anschließend nicht ausgewählt wird).

### <a name="create-new-project-configurations"></a>Erstellen neuer Projektkonfigurationen

Sie können im **Dialog Feld neue Projekt Konfiguration** (**Build**Configuration Manager aktive Projektmappenkonfiguration neu) die Option **Einstellungen Kopieren von** verwenden  >  **Configuration Manager**  >  **Active Solution Configuration**  >  **New**, um eine Projekt Konfiguration basierend auf den vorhandenen Projekteinstellungen zu erstellen. Führen Sie dies einmal für die Debugkonfiguration und einmal für die Releasekonfiguration durch. Nachfolgende Änderungen können dann nur auf die **/CLR** -spezifischen Konfigurationen angewendet werden, wobei die ursprünglichen Projekt Konfigurationen unverändert bleiben.

Projekte, die benutzerdefinierte Buildregeln verwenden, erfordern möglicherweise zusätzliche Aufmerksamkeit.

Dieser Schritt hat auf Projekte, die Makefiles verwenden, unterschiedliche Auswirkungen. In diesem Fall kann ein separates Buildziel konfiguriert werden, oder die für die **/CLR** -Kompilierung spezifische Version kann aus einer Kopie der ursprünglichen erstellt werden.

### <a name="change-project-settings"></a>Ändern von Projekteinstellungen

**/CLR** kann in der Entwicklungsumgebung mithilfe der Anweisungen unter [/CLR (Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md)ausgewählt werden. Wie bereits erwähnt, werden in diesem Schritt automatisch sich widersprechende Projekteinstellungen deaktiviert.

> [!NOTE]
> Wenn Sie ein verwaltetes Bibliothek-oder Webdienst Projekt von Visual Studio 2003 aktualisieren, wird die **/Zl** -Compileroption auf der Eigenschaften Seite für die **Befehlszeile** hinzugefügt. Dadurch wird LNK2001 verursacht. Entfernen Sie **/Zl** von der Eigenschaften Seite für die **Befehlszeile** zum Auflösen. Weitere Informationen finden Sie unter [/ZL (Weglassen des Standard Bibliotheks namens)](../build/reference/zl-omit-default-library-name.md) und [Festlegen der Compiler-und Buildeigenschaften](../build/working-with-project-properties.md) . Oder fügen Sie msvcrt. lib und msvcmrt. lib der Eigenschaft **Zusätzliche Abhängigkeiten** des Linker hinzu.

Für Projekte, die mit Makefiles erstellt wurden, müssen nicht kompatible Compileroptionen manuell deaktiviert werden, sobald **/CLR** hinzugefügt wird. Weitere Informationen zu Compileroptionen, die nicht mit **/CLR**kompatibel sind, finden Sie unter/[/CLR-Einschränkungen](../build/reference/clr-restrictions.md) .

### <a name="precompiled-headers"></a>Vorkompilierte Header

Vorkompilierte Header werden unter **/CLR**unterstützt. Wenn Sie jedoch nur einige ihrer cpp-Dateien mit **/CLR** kompilieren (wobei der Rest als System eigen kompiliert wird), sind einige Änderungen erforderlich, da vorkompilierte Header, die mit **/CLR** generiert werden, nicht mit den Daten kompatibel sind, die ohne **/CLR**generiert wurden. Diese Inkompatibilität ist darauf zurückzuführen, dass **/CLR** Metadaten generiert und erfordert. Von Modulen kompilierte **/CLR** können daher keine vorkompilierten Header verwenden, die keine Metadaten enthalten, und nicht- **/CLR** -Module können keine vorkompilierten Header Dateien verwenden, die Meta-Daten enthalten.

Die einfachste Möglichkeit, ein Projekt zu kompilieren, in dem einige Module kompiliert werden **/CLR** besteht darin, vorkompilierte Header vollständig zu deaktivieren. (Öffnen Sie im Dialogfeld der Eigenschaftenseiten des Projekts den Knoten C/C++, und wählen Sie Vorkompilierte Header aus. Ändern Sie dann die Eigenschaft „Erstellen/Verwenden“ vorkompilierter Header in „Vorkompilierte Header nicht verwenden“.)

Allerdings beschleunigen vorkompilierte Header insbesondere in großen Projekten die Kompilierung, insofern ist eine Deaktivierung dieser Funktion nicht wünschenswert. In diesem Fall empfiehlt es sich, die Dateien **/CLR** und Non **/CLR** so zu konfigurieren, dass separate vorkompilierte Header verwendet werden. Dies kann in einem Schritt durch die Mehrfachauswahl der zu kompilierenden Module erfolgen **/CLR** indem Sie **Projektmappen-Explorer**mit der rechten Maustaste auf die Gruppe klicken und Eigenschaften auswählen. Ändern Sie dann die beiden Eigenschaften „PCH durch Datei erstellen/verwenden“ und „Vorkompilierte Headerdatei“ auf einen anderen Headerdateinamen bzw. eine andere PCH-Datei.

## <a name="fixing-errors"></a>Beheben von Fehlern

Das Kompilieren mit **/CLR** kann zu Compilerfehlern, Linkerfehlern oder Laufzeitfehlern führen. In diesem Abschnitt werden die häufigsten Probleme behandelt.

### <a name="metadata-merge"></a>Zusammenführen von Metadaten

Unterschiedliche Datentypversionen können den Linker scheitern lassen, weil die für die beiden Typen generierten Metadaten nicht übereinstimmen. (Dies ist normalerweise darauf zurückzuführen, dass Member eines Typs bedingt definiert werden, die Bedingungen für alle CPP-Dateien, die den-Typ verwenden, jedoch nicht identisch sind.) In diesem Fall schlägt der Linker fehl und meldet nur den Symbolnamen und den Namen der zweiten obj-Datei, in der der Typ definiert wurde. Es ist häufig hilfreich, die Reihenfolge zu ändern, in der die OBJ-Dateien an den Linker gesendet werden, um herauszufinden, wo sich die andere Version des Datentyps befindet.

### <a name="loader-lock-deadlock"></a>Ladeprogrammsperren-Deadlocks

Der loadersperrendeadlock kann auftreten, ist jedoch deterministisch und wird zur Laufzeit erkannt und gemeldet. Ausführliche Hintergrundinformationen, Anleitungen und Lösungen finden Sie unter [Initialisierung gemischter](../dotnet/initialization-of-mixed-assemblies.md) Assemblys.

### <a name="data-exports"></a>Datenexporte

Das Exportieren von DLL-Daten ist fehleranfällig und daher nicht empfehlenswert. Das liegt daran, dass die Initialisierung des Datenabschnitts einer DLL nicht gewährleistet ist, solange kein verwalteter Teil der DLL ausgeführt wurde. Verweisen Sie mit [#using-Direktive](../preprocessor/hash-using-directive-cpp.md)auf Metadaten.

### <a name="type-visibility"></a>Typsichtbarkeit

Native Typen sind standardmäßig privat. Das kann dazu führen, dass ein systemeigener Typ außerhalb der DLL nicht sichtbar ist. Beheben Sie diesen Fehler **`public`** , indem Sie diese Typen hinzufügen.

### <a name="floating-point-and-alignment-issues"></a>Gleitkomma- und Ausrichtungsprobleme

`__controlfp`wird im Common Language Runtime nicht unterstützt (Weitere Informationen finden Sie unter [_control87, _controlfp \_ _control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) ). Die CLR respektiert auch keine [Ausrichtung](../cpp/align-cpp.md).

### <a name="com-initialization"></a>COM-Initialisierung

Die Common Language Runtime initialisiert COM automatisch beim Initialisieren eines Moduls. Bei automatischer Initialisierung wird COM als MTA initialisiert. Folglich führt explizites Initialisieren von COM zu Rückgabecodes, die angeben, dass COM bereits initialisiert ist. Wenn Sie versuchen, COM mit einem bestimmten Threadingmodell zu initialisieren, obwohl die CLR COM bereits mit einem anderen Threadingmodell initialisiert hat, kann die Anwendung möglicherweise nicht ausgeführt werden.

Der Common Language Runtime startet com standardmäßig als MTA. Verwenden Sie [/CLRTHREADATTRIBUTE (CLR-Thread Attribut festlegen)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) , um dies zu ändern.

### <a name="performance-issues"></a>Leistungsprobleme

Möglicherweise stellen Sie eine Verschlechterung der Leistung fest, wenn systemeigene für MSIL generierte C++-Methoden indirekt aufgerufen werden (durch virtuelle Funktionsaufrufe oder die Verwendung von Funktionszeigern). Weitere Informationen hierzu finden Sie unter [Double Thunking](../dotnet/double-thunking-cpp.md).

Wenn Sie von systemeigenem Code zu MSIL wechseln, werden Sie feststellen, dass das Workingset größer wird. Das liegt daran, dass die Common Language Runtime viele Funktionen enthält, die sicherstellen, dass Programme ordnungsgemäß ausgeführt werden. Wenn die **/CLR** -Anwendung nicht ordnungsgemäß ausgeführt wird, möchten Sie möglicherweise C4793 aktivieren (standardmäßig deaktiviert). Weitere Informationen finden Sie unter [Compilerwarnung (Stufe 1 und 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) .

### <a name="program-crashes-on-shutdown"></a>Programmabstürze beim Herunterfahren

In manchen Fällen wird die CLR heruntergefahren, bevor die Ausführung des verwalteten Codes abgeschlossen ist. Die Ursache kann in der Verwendung von `std::set_terminate` und `SIGTERM` liegen. Weitere Informationen finden Sie unter [Signal Konstanten](../c-runtime-library/signal-constants.md) und [Set_terminate](../c-runtime-library/abnormal-termination.md) .

## <a name="using-new-visual-c-features"></a>Verwenden neuer Visual C++-Funktionen

Nachdem Ihre Anwendung kompiliert, Links und ausgeführt wurde, können Sie mit der Verwendung von .NET-Funktionen in jedem Modul beginnen, das mit **/CLR**kompiliert wurde. Weitere Informationen finden Sie unter [Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md).

Informationen zur .NET-Programmierung in Visual C++ finden Sie unter:

- [.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Native und .NET-Interoperabilität](../dotnet/native-and-dotnet-interoperability.md)

- [Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Siehe auch

[Gemischte (Native und verwaltete) Assemblys](../dotnet/mixed-native-and-managed-assemblies.md)
