---
title: 'Vorgehensweise: Migrieren auf -clr'
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
ms.openlocfilehash: 339b1f3172d8b82ece3e98f117f53ed399cbd4e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376078"
---
# <a name="how-to-migrate-to-clr"></a>Gewusst wie: Migrieren zu /clr

In diesem Thema werden Probleme behandelt, die beim Kompilieren von systemeigenem Code mit **/clr** auftreten (weitere Informationen finden Sie unter [/clr (Common Language Runtime Compilation).](../build/reference/clr-common-language-runtime-compilation.md) **Mit /clr** kann systemeigener C++-Code zusätzlich zu anderem systemeigenen C++-Code aufgerufen und von .NET-Assemblys aufgerufen und aufgerufen werden. Weitere Informationen zu den Vorteilen der Kompilierung mit **/clr**finden Sie unter [Gemischte (Native und Verwaltete) Assemblys](../dotnet/mixed-native-and-managed-assemblies.md) sowie [Systemeigene und .NET-Interoperabilität.](../dotnet/native-and-dotnet-interoperability.md)

## <a name="known-issues-compiling-library-projects-with-clr"></a>Bekannte Probleme beim Kompilieren von Bibliotheksprojekten mit /clr

Visual Studio enthält einige bekannte Probleme beim Kompilieren von Bibliotheksprojekten mit **/clr**:

- Ihr Code kann Typen zur Laufzeit mit [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname)abfragen. Wenn sich jedoch ein Typ in einer MSIL .dll befindet (kompiliert mit **/clr**), schlägt der Aufruf zu `FromName` , wenn er auftritt, bevor die statischen Konstruktoren in der verwalteten DLL ausgeführt werden (dieses Problem wird nicht angezeigt, wenn der FromName-Aufruf auftritt, nachdem Code in der verwalteten .dll ausgeführt wurde). Um dieses Problem zu umgehen, können Sie die Konstruktion des verwalteten statischen Konstruktors erzwingen, indem Sie in der verwalteten DLL eine Funktion definieren, sie exportieren und anschließend aus der nativen MFC-Anwendung aufrufen. Beispiel:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Kompilieren mit Visual C++

Bevor Sie **/clr** für ein beliebiges Modul in Ihrem Projekt verwenden, kompilieren und verknüpfen Sie Ihr systemeigenem Projekt zuerst mit Visual Studio 2010.

Die folgenden Schritte, in der Reihenfolge, bieten den einfachsten Pfad zu einer **/clr-Kompilierung.** Wichtig ist dabei, das Projekt nach jedem dieser Schritte zu kompilieren und auszuführen.

### <a name="versions-prior-to-visual-studio-2003"></a>Versionen vor Visual Studio 2003

Wenn Sie ein Upgrade auf Visual Studio 2010 von einer Version vor Visual Studio 2003 durchführen, werden möglicherweise Compilerfehler im Zusammenhang mit der erweiterten C++-Standardkonformität in Visual Studio 2003 angezeigt.

### <a name="upgrading-from-visual-studio-2003"></a>Upgrade von Visual Studio 2003

Projekte, die zuvor mit Visual Studio 2003 erstellt wurden, sollten ebenfalls zuerst ohne **/clr** kompiliert werden, da Visual Studio jetzt die ANSI/ISO-Konformität und einige änderungende Änderungen erhöht hat. Die Änderung, die wahrscheinlich die größte Aufmerksamkeit erfordert, sind [die Sicherheitsfeatures in der CRT](../c-runtime-library/security-features-in-the-crt.md). Code, der das CRT verwendet, löst sehr wahrscheinlich Veraltungswarnungen aus. Diese Warnungen können unterdrückt werden, aber die Migration zu den neuen [Sicherheitserweiterten Versionen von CRT-Funktionen](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) wird bevorzugt, da sie eine bessere Sicherheit bieten und Sicherheitsprobleme in Ihrem Code aufdecken können.

### <a name="upgrading-from-managed-extensions-for-c"></a>Aktualisieren von Managed Extensions für C++

Ab Visual Studio 2005 wird Code, der mit Managed Extensions für C++ geschrieben wurde, nicht unter **/clr**kompiliert.

## <a name="convert-c-code-to-c"></a>Konvertieren von C-Code in C++

Obwohl Visual Studio C-Dateien kompiliert, ist es notwendig, sie für eine **/clr-Kompilierung** in C++ zu konvertieren. Der tatsächliche Dateiname muss nicht geändert werden. Sie können **/Tp** verwenden (siehe [/Tc, /Tp, /TC, /TP (Quellendateityp angeben)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Beachten Sie, dass C++-Quellcodedateien zwar für **/clr**erforderlich sind, es jedoch nicht erforderlich ist, den Code neu zu berücksichtigen, um objektorientierte Paradigmen zu verwenden.

Es ist sehr wahrscheinlich, dass C-Code bei einer Kompilierung als C++-Datei gewisse Änderungen erfordert. Da die C++-Typsicherheitsregeln streng sind, müssen Typkonvertierungen explizit durch Umwandlungen vorgenommen werden. Beispielsweise gibt malloc einen void-Zeiger zurück, kann aber durch Umwandlung einem Zeiger zugewiesen werden, der auf einen beliebigen Typ in C zeigt:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Auch Funktionszeiger sind in C++ streng typsicher, deshalb muss der folgende C-Code geändert werden. Es ist das Beste, in C++ einen `typedef` zu erstellen, der den Funktionszeigertyp definiert, und diesen Typ zur Umwandlung von Funktionszeigern zu verwenden:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++ verlangt außerdem, dass Funktionen entweder einen Prototyp haben oder vollständig definiert sind, bevor auf sie verwiesen wird oder sie aufgerufen werden können.

Bezeichner, die in C-Code verwendet werden und in C++ Schlüsselwörter sind (z. B. **virtual**, **new**, **delete**, **bool**, **true**, **false**, etc.), müssen umbenannt werden. Dies kann im Allgemeinen durch einfache Such- und Ersetzungsvorgänge erfolgen.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Umkonfigurieren von Projekteinstellungen

Nachdem das Projekt in Visual Studio 2010 kompiliert und ausgeführt wurde, sollten Sie neue Projektkonfigurationen für **/clr** erstellen, anstatt die Standardkonfigurationen zu ändern. **/clr** ist mit einigen Compileroptionen nicht kompatibel, und durch das Erstellen separater Konfigurationen können Sie Ihr Projekt als systemneuzunativ oder verwaltet erstellen. Wenn **/clr** im Dialogfeld Eigenschaftenseiten ausgewählt ist, werden Projekteinstellungen deaktiviert, die nicht mit **/clr** kompatibel sind (und deaktivierte Optionen werden nicht automatisch wiederhergestellt, wenn **/clr** anschließend nicht ausgewählt wird).

### <a name="create-new-project-configurations"></a>Erstellen neuer Projektkonfigurationen

Sie können die Option **Einstellungen aus kopieren** im **Dialogfeld Neue Projektkonfiguration** (**Build** > **Configuration Manager** > **Active Solution Configuration** > **New**) verwenden, um eine Projektkonfiguration basierend auf Ihren vorhandenen Projekteinstellungen zu erstellen. Führen Sie dies einmal für die Debugkonfiguration und einmal für die Releasekonfiguration durch. Nachfolgende Änderungen können dann nur auf die **/clr** --spezifischen Konfigurationen angewendet werden, wobei die ursprünglichen Projektkonfigurationen intakt bleiben.

Projekte, die benutzerdefinierte Buildregeln verwenden, erfordern möglicherweise zusätzliche Aufmerksamkeit.

Dieser Schritt hat auf Projekte, die Makefiles verwenden, unterschiedliche Auswirkungen. In diesem Fall kann ein separates Buildziel konfiguriert oder eine versionspezifische Version für die **/clr-Kompilierung** aus einer Kopie des Originals erstellt werden.

### <a name="change-project-settings"></a>Ändern von Projekteinstellungen

**/clr** kann in der Entwicklungsumgebung ausgewählt werden, indem Sie den Anweisungen in [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md)folgen. Wie bereits erwähnt, werden in diesem Schritt automatisch sich widersprechende Projekteinstellungen deaktiviert.

> [!NOTE]
> Beim Aktualisieren einer verwalteten Bibliothek oder eines Webdienstprojekts aus Visual Studio 2003 wird die Compileroption **/Zl** der **Eigenschaftenseite Befehlszeile** hinzugefügt. Dadurch wird LNK2001 verursacht. Entfernen Sie **/Zl** von der **Eigenschaftenseite befehlszeilen,** um es aufzulösen. Weitere Informationen finden Sie unter [/Zl (Standardbibliotheksname auslassen)](../build/reference/zl-omit-default-library-name.md) und [Compiler- und Buildeigenschaften](../build/working-with-project-properties.md) festlegen. Oder fügen Sie msvcrt.lib und msvcmrt.lib der Eigenschaft **"Zusätzliche Abhängigkeiten"** des Linkers hinzu.

Bei Projekten, die mit makefiles erstellt wurden, müssen inkompatible Compileroptionen manuell deaktiviert werden, sobald **/clr** hinzugefügt wurde. Siehe /[/clr Einschränkungen](../build/reference/clr-restrictions.md) für Informationen zu Compileroptionen, die nicht mit **/clr**kompatibel sind.

### <a name="precompiled-headers"></a>Vorkompilierte Header

Vorkompilierte Header werden unter **/clr**unterstützt. Wenn Sie jedoch nur einige Ihrer CPP-Dateien mit **/clr** kompilieren (den Rest als nativ kompilieren), sind einige Änderungen erforderlich, da vorkompilierte Header, die mit **/clr** generiert wurden, nicht mit denen kompatibel sind, die ohne **/clr**generiert wurden. Diese Inkompatibilität ist auf die Tatsache zurückzuführen, dass **/clr** Metadaten generiert und erfordert. Module, die **/clr** kompiliert haben, können daher keine vorkompilierten Header verwenden, die keine Metadaten enthalten, und **Nicht-Clr-Module** können keine vorkompilierten Headerdateien verwenden, die Metadaten enthalten.

Die einfachste Möglichkeit, ein Projekt zu kompilieren, in dem einige Module **/clr** kompiliert werden, besteht darin, vorkompilierte Header vollständig zu deaktivieren. (Öffnen Sie im Dialogfeld der Eigenschaftenseiten des Projekts den Knoten C/C++, und wählen Sie Vorkompilierte Header aus. Ändern Sie dann die Eigenschaft „Erstellen/Verwenden“ vorkompilierter Header in „Vorkompilierte Header nicht verwenden“.)

Allerdings beschleunigen vorkompilierte Header insbesondere in großen Projekten die Kompilierung, insofern ist eine Deaktivierung dieser Funktion nicht wünschenswert. In diesem Fall ist es am besten, die **Dateien /clr** und non **/clr** so zu konfigurieren, dass separate vorkompilierte Header verwendet werden. Dies kann in einem Schritt geschehen, indem Sie die Module, die **/clr** kompiliert werden sollen, mit **dem Projektmappen-Explorer**mehrfach auswählen, mit der rechten Maustaste auf die Gruppe klicken und Eigenschaften auswählen. Ändern Sie dann die beiden Eigenschaften „PCH durch Datei erstellen/verwenden“ und „Vorkompilierte Headerdatei“ auf einen anderen Headerdateinamen bzw. eine andere PCH-Datei.

## <a name="fixing-errors"></a>Beheben von Fehlern

Das Kompilieren mit **/clr** kann zu Compiler-, Linker- oder Laufzeitfehlern führen. In diesem Abschnitt werden die häufigsten Probleme behandelt.

### <a name="metadata-merge"></a>Zusammenführen von Metadaten

Unterschiedliche Datentypversionen können den Linker scheitern lassen, weil die für die beiden Typen generierten Metadaten nicht übereinstimmen. (Dies wird in der Regel verursacht, wenn Member eines Typs bedingt definiert sind, die Bedingungen jedoch nicht für alle CPP-Dateien, die den Typ verwenden, identisch sind.) In diesem Fall schlägt der Linker fehl, wenn nur der Symbolname und der Name der zweiten OBJ-Datei gemeldet werden, in der der Typ definiert wurde. Es ist häufig hilfreich, die Reihenfolge zu ändern, in der die OBJ-Dateien an den Linker gesendet werden, um herauszufinden, wo sich die andere Version des Datentyps befindet.

### <a name="loader-lock-deadlock"></a>Ladeprogrammsperren-Deadlocks

Der "Loader Lock Deadlock" kann auftreten, ist jedoch deterministisch und wird zur Laufzeit erkannt und gemeldet. Ausführliche Hintergründe, Anleitungen und Lösungen finden Sie unter [Initialisierung gemischter Assemblys.](../dotnet/initialization-of-mixed-assemblies.md)

### <a name="data-exports"></a>Datenexporte

Das Exportieren von DLL-Daten ist fehleranfällig und daher nicht empfehlenswert. Das liegt daran, dass die Initialisierung des Datenabschnitts einer DLL nicht gewährleistet ist, solange kein verwalteter Teil der DLL ausgeführt wurde. Referenzmetadaten mit [#using Richtlinie](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Typsichtbarkeit

Native Typen sind standardmäßig privat. Das kann dazu führen, dass ein systemeigener Typ außerhalb der DLL nicht sichtbar ist. Beheben Sie diesen Fehler, indem Sie zu diesen Typen `public` hinzufügen.

### <a name="floating-point-and-alignment-issues"></a>Gleitkomma- und Ausrichtungsprobleme

`__controlfp`wird bei der Common Language Runtime nicht unterstützt (weitere Informationen finden Sie in [_control87, \__controlfp, _control87_2).](../c-runtime-library/reference/control87-controlfp-control87-2.md) Die CLR wird auch nicht [ausgerichtet](../cpp/align-cpp.md).

### <a name="com-initialization"></a>COM-Initialisierung

Die Common Language Runtime initialisiert COM automatisch beim Initialisieren eines Moduls. Bei automatischer Initialisierung wird COM als MTA initialisiert. Folglich führt explizites Initialisieren von COM zu Rückgabecodes, die angeben, dass COM bereits initialisiert ist. Wenn Sie versuchen, COM mit einem bestimmten Threadingmodell zu initialisieren, obwohl die CLR COM bereits mit einem anderen Threadingmodell initialisiert hat, kann die Anwendung möglicherweise nicht ausgeführt werden.

Die Common Language Runtime startet COM standardmäßig als MTA. Verwenden Sie [/CLRTHREADATTRIBUTE (CLR Thread Attribut festlegen),](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) um dies zu ändern.

### <a name="performance-issues"></a>Leistungsprobleme

Möglicherweise stellen Sie eine Verschlechterung der Leistung fest, wenn systemeigene für MSIL generierte C++-Methoden indirekt aufgerufen werden (durch virtuelle Funktionsaufrufe oder die Verwendung von Funktionszeigern). Weitere Informationen finden Sie unter [Double Thunking](../dotnet/double-thunking-cpp.md).

Wenn Sie von systemeigenem Code zu MSIL wechseln, werden Sie feststellen, dass das Workingset größer wird. Das liegt daran, dass die Common Language Runtime viele Funktionen enthält, die sicherstellen, dass Programme ordnungsgemäß ausgeführt werden. Wenn Ihre **/clr-Anwendung** nicht ordnungsgemäß ausgeführt wird, können Sie C4793 aktivieren (standardmäßig deaktiviert), weitere Informationen finden Sie unter [Compilerwarnung (Stufe 1 und 3) C4793.](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)

### <a name="program-crashes-on-shutdown"></a>Programmabstürze beim Herunterfahren

In manchen Fällen wird die CLR heruntergefahren, bevor die Ausführung des verwalteten Codes abgeschlossen ist. Die Ursache kann in der Verwendung von `std::set_terminate` und `SIGTERM` liegen. Weitere Informationen finden Sie unter [Signalkonstanten](../c-runtime-library/signal-constants.md) und [set_terminate.](../c-runtime-library/abnormal-termination.md)

## <a name="using-new-visual-c-features"></a>Verwenden neuer Visual C++-Funktionen

Nachdem Ihre Anwendung kompiliert, verlinkt und ausgeführt wurde, können Sie mit der Verwendung von .NET-Features in jedem Modul beginnen, das mit **/clr**kompiliert wurde. Weitere Informationen finden Sie unter [Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md).

Informationen zur .NET-Programmierung in Visual C++ finden Sie unter:

- [.NET Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Interoperabilität von nativem Code und .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Siehe auch

[Gemischte (native und verwaltete) Assemblys](../dotnet/mixed-native-and-managed-assemblies.md)
