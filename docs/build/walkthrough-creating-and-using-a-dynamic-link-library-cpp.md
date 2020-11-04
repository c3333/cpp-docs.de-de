---
title: 'Exemplarische Vorgehensweise: Erstellen und Verwenden Ihrer eigenen Dynamic Link Library (C++)'
description: Verwenden Sie C++, um in Visual Studio eine Dynamic Link Library (DLL) für Windows zu erstellen.
ms.custom: conceptual
ms.date: 08/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 0018df31e19a3f1a68a1c4a0bde37d6fa2678406
ms.sourcegitcommit: 868838273eda35eb72c78dccf4121940dcc04706
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2020
ms.locfileid: "92924479"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Exemplarische Vorgehensweise: Erstellen und Verwenden Ihrer eigenen Dynamic Link Library (C++)

Diese exemplarische Vorgehensweise zeigt ausführlich, wie Sie die Visual Studio-IDE verwenden, um selbst eine DLL (Dynamic Link Library) mit Microsoft C++ (MSCV) zu erstellen. Danach wird gezeigt, wie die DLL aus einer anderen C++-App verwendet wird. DLLs (in UNIX-basierten Betriebssystemen auch als *freigegebene Bibliotheken* bezeichnet) gehören zu den nützlichsten Arten von Windows-Komponenten. Sie können damit Code und Ressourcen freigeben und die Größe von Apps verkleinern. DLLs vereinfachen die Wartung und Erweiterung Ihrer Apps.

In dieser exemplarischen Vorgehensweise erstellen Sie eine DLL, die einige mathematische Funktionen implementiert. Anschließend erstellen Sie eine Konsolen-App, die die Funktionen aus der DLL verwendet. Sie erhalten auch eine Einführung in einige der Programmierungstechniken und -konventionen, die in Windows-DLLs zum Einsatz kommen.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben behandelt:

- Erstellen eines DLL-Projekts in Visual Studio

- Hinzufügen von exportierten Funktionen und Variablen zur DLL

- Erstellen eines Konsolen-App-Projekts in Visual Studio

- Verwenden der aus der DLL importierten Funktionen und Variablen in der Konsolen-App

- Ausführen der fertigen App

Wie eine statisch verknüpfte Bibliothek _exportiert_ eine DLL Variablen, Funktionen und Ressourcen nach Namen. Eine Client-App _importiert_ die Namen, um diese Variablen, Funktionen und Ressourcen zu verwenden. Im Gegensatz zu einer statisch verknüpften Bibliothek stellt Windows die Verbindung zwischen den Importen in Ihrer App und den Exporten in einer DLL zur Lade- oder Laufzeit her, nicht zum Zeitpunkt der Verknüpfung. Zum Herstellen dieser Verbindungen erfordert Windows zusätzliche Informationen, die nicht Bestandteil des standardmäßigen C++-Kompilierungsmodells sind. Der MSVC-Compiler implementiert einige Microsoft-spezifische Erweiterungen für C++, um diese zusätzlichen Informationen bereitzustellen. Wir werden diese Erweiterungen im weiteren Verlauf näher erläutern.

In dieser exemplarischen Vorgehensweise werden zwei Visual Studio-Projektmappen erstellt: eine, die die DLL kompiliert, und eine andere, die die Client-App kompiliert. Die DLL verwendet die C-Aufrufkonvention. Sie kann von Apps aufgerufen werden, die in anderen Programmiersprachen geschrieben wurden, solange die Plattform, die Aufrufkonventionen und die Verknüpfungskonventionen übereinstimmen. Die Client-App verwendet _implizite Verknüpfungen_ , bei denen Windows die App zur Ladezeit mit der DLL verknüpft. Dank dieser Art der Verknüpfung kann die App die von der DLL bereitgestellten Funktionen genauso nutzen wie die Funktionen in einer statisch verknüpften Bibliothek.

In dieser exemplarischen Vorgehensweise werden einige gängige Situationen nicht behandelt. Die Verwendung von C++-DLLs durch andere Programmiersprachen wird im Code nicht veranschaulicht. Es wird nicht gezeigt, wie [eine DLL als reine Ressource](creating-a-resource-only-dll.md) erstellt oder das [explizite Verknüpfen](linking-an-executable-to-a-dll.md#linking-explicitly) verwendet werden, um DLLs zur Laufzeit anstatt zur Ladezeit zu laden. Keine Sorge: Für all diese Verfahren können Sie MSVC und Visual Studio verwenden.

Links mit weiteren Informationen zu DLLs finden Sie im Artikel [Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md). Weitere Informationen zu impliziten und expliziten Verknüpfungen finden Sie unter [Bestimmen der geeigneten Verknüpfungsmethode](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Informationen zum Erstellen von C++-DLLs zur Verwendung mit Programmiersprachen, die Verknüpfungskonventionen der Sprache C verwenden, finden Sie unter [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md). Informationen zum Erstellen von DLLs zur Verwendung mit .NET-Sprachen finden Sie unter [Aufrufen von DLL-Funktionen aus Visual Basic-Anwendungen heraus](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Voraussetzungen

- Ein Computer, auf dem Microsoft Windows 7 oder eine höhere Version ausgeführt wird. Für ein optimales Entwicklungserlebnis empfehlen wir Windows 10.

::: moniker range=">=msvc-150"

- Eine Kopie von Visual Studio. Informationen zum Herunterladen und Installieren von Visual Studio finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio). Wenn Sie das Installationsprogramm ausführen, stellen Sie sicher, dass die Workload **Desktopentwicklung mit C++** aktiviert ist. Machen Sie sich keine Sorgen, wenn Sie diese Workload beim Installieren von Visual Studio nicht installiert haben. Sie können das Installationsprogramm erneut ausführen und die Workload jetzt installieren.

   ![Desktopentwicklung mit C++](media/desktop-development-with-cpp.png "Desktopentwicklung mit C++")

::: moniker-end

::: moniker range="msvc-140"

- Eine Kopie von Visual Studio. Informationen zum Herunterladen und Installieren von Visual Studio 2015 finden Sie unter [Installieren von Visual Studio 2015](/visualstudio/install/install-visual-studio-2015?view=vs-2015&preserve-view=true). Verwenden Sie eine **benutzerdefinierte** Installation, um den C++-Compiler und die Tools zu installieren, da diese nicht standardmäßig installiert werden.

::: moniker-end

- Grundkenntnisse der Verwendung der Visual Studio-IDE. Wenn Sie bereits früher Windows-Desktop-Apps verwendet haben, dürften keine Verständnisprobleme auftreten. Eine Einführung finden Sie unter [Willkommen in der Visual Studio-IDE](/visualstudio/ide/visual-studio-ide).

- Grundlegende Kenntnisse der Programmiersprache C++. Keine Sorge: Wir verwenden keine allzu komplizierten Verfahren.

::: moniker range="msvc-150"

> [!NOTE]
> Bei dieser exemplarischen Vorgehensweise wird angenommen, dass Sie Visual Studio 2017, Version 15.9 oder höher verwenden. In einigen früheren Versionen von Visual Studio 2017 waren Fehler in den Codevorlagen aufgetreten, oder es wurden verschiedene Dialogfelder für die Benutzeroberfläche verwendet. Verwenden Sie den Visual Studio-Installer, um Visual Studio 2017 auf Version 15.9 oder höher zu aktualisieren und somit Probleme zu vermeiden.

::: moniker-end

## <a name="create-the-dll-project"></a>Erstellen des DLL-Projekts

Mit den folgenden Aufgaben erstellen Sie ein Projekt für Ihre DLL, fügen Code hinzu, und kompilieren das Projekt. Als Erstes starten Sie die Visual Studio-IDE und melden sich ggf. an. Die Anweisungen variieren leicht, je nachdem, welche Version von Visual Studio Sie verwenden. Stellen Sie sicher, dass Sie in der Dropdownliste links oben auf dieser Seite die richtige Version ausgewählt haben.

::: moniker range=">=msvc-160"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>So erstellen Sie ein DLL-Projekt in Visual Studio 2019

1. Klicken Sie in der Menüleiste auf **Datei**  > **Neu**  > **Projekt** , um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

   ![Erstellen eines neuen DLL-Projekts](media/create-new-dll-project-2019.png "Erstellen des MathLibrary-Projekts")

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++** , die **Plattform** auf **Windows** und den **Projekttyp** auf **Bibliothek** fest.

1. Klicken Sie in der gefilterten Projekttypliste zunächst auf **Dynamic Link Library (DLL)** und dann auf **Weiter**.

1. Geben Sie auf der Seite **Neues Projekt konfigurieren** in das Feld **Projektname** den Namen *MathLibrary* ein, um einen Namen für das Projekt festzulegen. Behalten Sie die Standardwerte für **Speicherort** und **Projektmappenname** bei. Legen Sie **Projektmappe** auf **Neue Projektmappe erstellen** fest. Deaktivieren Sie bei Bedarf die Option **Legen Sie die Projektmappe und das Projekt im selben Verzeichnis ab**.

1. Klicken Sie auf die Schaltfläche **Erstellen** , um das Projekt zu erstellen.

Wenn die Projektmappe erstellt wird, sehen Sie das generierte Projekt und die Quelldateien in Visual Studio im Fenster **Projektmappen-Explorer**.

![Screenshot des Visual Studio 2019-Fensters „Projektmappen-Explorer“, in dem die MathLibrary hervorgehoben ist](media/mathlibrary-solution-explorer-162.png "Generierte Projektmappe in Visual Studio")

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>So erstellen Sie ein DLL-Projekt in Visual Studio 2017

1. Klicken Sie auf der Menüleiste auf **Datei** > **Neu** > **Projekt** , um das Dialogfeld **Neues Projekt** zu öffnen.

1. Klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** auf **Installiert** > **Visual C++**  > **Windows Desktop**. Klicken Sie im mittleren Bereich auf **Dynamic Link Library (DLL)** . Geben Sie *MathLibrary* in das Feld **Name** ein, um einen Namen für das Projekt anzugeben. Behalten Sie die Standardwerte für **Speicherort** und **Projektmappenname** bei. Legen Sie **Projektmappe** auf **Neue Projektmappe erstellen** fest. Aktivieren Sie ggf. **Projektmappenverzeichnis erstellen**.

   ![Screenshot des Visual Studio 2017-Dialogfelds „Neues Projekt“, in dem „MathLibrary“ im Textfeld „Name“ eingegeben ist](media/mathlibrary-new-project-name-159.png "Benennen des MathLibrary-Projekts")

1. Wählen Sie die Schaltfläche **OK** aus, um das Projekt zu erstellen.

Wenn die Projektmappe erstellt wird, sehen Sie das generierte Projekt und die Quelldateien in Visual Studio im Fenster **Projektmappen-Explorer**.

![Screenshot des Visual Studio 2017-Fensters „Projektmappen-Explorer“, in dem die MathLibrary hervorgehoben ist](media/mathlibrary-solution-explorer-159.png "Generierte Projektmappe in Visual Studio")

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-dll-project-in-visual-studio-2015-and-older-versions"></a>So erstellen Sie ein DLL-Projekt in Visual Studio 2015 und älteren Versionen

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **Installiert** > **Vorlagen** , und wählen Sie **Visual C++** aus. Klicken Sie dann im mittleren Bereich auf **Win32-Konsolenanwendung**. Geben Sie *MathLibrary* in das Bearbeitungsfeld **Name** ein, um einen Namen für das Projekt anzugeben. Behalten Sie die Standardwerte für **Speicherort** und **Projektmappenname** bei. Legen Sie **Projektmappe** auf **Neue Projektmappe erstellen** fest. Aktivieren Sie ggf. **Projektmappenverzeichnis erstellen**.

   ![Screenshot des Visual Studio 2015-Dialogfelds „Neues Projekt“, in dem „MathLibrary“ im Textfeld „Name“ eingegeben ist](media/mathlibrary-project-name.png "Benennen des MathLibrary-Projekts")

1. Klicken Sie auf **OK** , um das Dialogfeld **Neues Projekt** zu schließen und den **Win32-Anwendungs-Assistenten** zu starten.

   ![Übersicht über den Win32-Anwendungs-Assistenten](media/mathlibrary-project-wizard-1.png "Übersicht über den Win32-Anwendungs-Assistenten")

1. Klicken Sie auf **Weiter**. Wählen Sie auf der Seite **Anwendungseinstellungen** unter **Anwendungstyp** die Option **DLL** aus.

   ![Erstellen einer DLL mit dem Win32-Anwendungs-Assistenten](media/mathlibrary-project-wizard-2.png "Erstellen einer DLL mit dem Win32-Anwendungs-Assistenten")

1. Wählen Sie die Schaltfläche **Fertig stellen** , um das Projekt zu erstellen.

Wenn der Assistent die Projektmappe erstellt hat, sehen Sie das generierte Projekt und die Quelldateien in Visual Studio im Fenster **Projektmappen-Explorer**.

![Screenshot des Visual Studio 2015-Fensters „Projektmappen-Explorer“, in dem die MathLibrary hervorgehoben ist](media/mathlibrary-solution-explorer-153.png "Generierte Projektmappe in Visual Studio")

::: moniker-end

Im Moment ist diese DLL noch nicht besonders nützlich. Als Nächstes erstellen Sie die Headerdatei, um die Funktionen zu deklarieren, die von der DLL exportiert werden. Danach fügen Sie die Funktionsdefinitionen zur DLL hinzu, um sie nützlicher zu machen.

### <a name="to-add-a-header-file-to-the-dll"></a>So fügen Sie der DLL eine Headerdatei hinzu

1. Um eine Headerdatei für Ihre Funktionen zu erstellen, wählen Sie auf der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

1. Wählen Sie im linken Bereich des Dialogfelds **Neues Element hinzufügen** die Option **Visual C++** aus. Wählen Sie im mittleren Bereich die Option **Headerdatei (.h)** . Geben Sie *MathLibrary.h* als Namen für die Headerdatei an.

   ![„Header hinzufügen“ im Dialogfeld „Neues Element hinzufügen“](media/mathlibrary-add-new-item-header-file.png "„Header hinzufügen“ im Dialogfeld „Neues Element hinzufügen“")

1. Klicken Sie auf die Schaltfläche **Hinzufügen** , um eine leere Headerdatei zu generieren, die in einem neuen Editor-Fenster angezeigt wird.

   ![Leere „MathLibrary.h“-Datei im Editor](media/edit-empty-mathlibrary-header.png "Leere „MathLibrary.h“-Datei im Editor")

1. Ersetzen Sie den Inhalt der Headerdatei durch diesen Code:

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

Diese Headerdatei deklariert einige Funktionen, um mit zwei Anfangswerten eine generalisierte Fibonacci-Folge zu erstellen. Ein Aufruf von `fibonacci_init(1, 1)` generiert die bekannte Fibonacci-Zahlenfolge.

Beachten Sie die Präprozessoranweisungen am Anfang der Datei. Die neue Projektvorlage für ein DLL-Projekt fügt den definierten Präprozessormakros **_PROJECTNAME_ &#95;EXPORTS** hinzu. In diesem Beispiel definiert Visual Studio **MATHLIBRARY&#95;EXPORTS** , wenn Ihr MathLibrary-DLL-Projekt erstellt wird.

Wenn das **MATHLIBRARY&#95;EXPORTS** -Makro definiert ist, legt das **MATHLIBRARY&#95;API** -Makro den Modifizierer `__declspec(dllexport)` in den Funktionsdeklarationen fest. Dieser Modifizierer weist den Compiler und Linker an, eine Funktion oder Variable aus der DLL zu exportieren, sodass sie von anderen Anwendungen verwendet werden kann. Wenn **MATHLIBRARY&#95;EXPORTS** nicht definiert ist, weil beispielsweise die Headerdatei in einer Clientanwendung enthalten ist, wendet **MATHLIBRARY&#95;API** den Modifizierer `__declspec(dllimport)` auf die Deklarationen an. Dieser Modifizierer optimiert den Import der Funktion oder Variablen in eine Anwendung. Weitere Informationen finden Sie unter [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>So fügen Sie der DLL eine Implementierung hinzu

::: moniker range=">=msvc-160"

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Quelldateien** und dann auf **Hinzufügen** > **Neues Element**. Erstellen Sie eine neue CPP-Datei namens *MathLibrary.cpp* auf die gleiche Art und Weise, wie Sie im vorherigen Schritt eine neue Headerdatei hinzugefügt haben.

1. Wählen Sie im Editor-Fenster die Registerkarte für **MathLibrary.cpp** aus, wenn diese bereits geöffnet ist. Andernfalls doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **MathLibrary.cpp** im Ordner **Quelldateien** des Projekts **MathLibrary** , um es zu öffnen.

1. Ersetzen Sie im Editor den Inhalt der Datei „MathLibrary.cpp“ durch den folgenden Code:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "pch.h" // use stdafx.h in Visual Studio 2017 and earlier
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

::: moniker-end

::: moniker range="<=msvc-150"

1. Wählen Sie im Editor-Fenster die Registerkarte für **MathLibrary.cpp** aus, wenn diese bereits geöffnet ist. Andernfalls doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **MathLibrary.cpp** im Ordner **Quelldateien** des Projekts **MathLibrary** , um es zu öffnen.

1. Ersetzen Sie im Editor den Inhalt der Datei „MathLibrary.cpp“ durch den folgenden Code:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019 and later
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

::: moniker-end

Um zu überprüfen, ob alles funktioniert, kompilieren Sie die Dynamic Link Library. Wählen Sie hierzu auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus. Die DLL und die zugehörige Compilerausgabe werden in einem Ordner namens *Debuggen* direkt unterhalb des Projektmappenordners abgelegt. Wenn Sie einen Releasebuild erstellen, wird die Ausgabe in einen Ordner namens *Release* abgelegt. Die Ausgabe sollte ungefähr wie folgt aussehen:

::: moniker range=">=msvc-160"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>pch.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="msvc-150"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="msvc-140"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

Herzlichen Glückwunsch! Sie haben mit Visual Studio eine DLL erstellt. Als Nächstes erstellen Sie eine Client-App, die die von der DLL exportierten Funktionen verwendet.

## <a name="create-a-client-app-that-uses-the-dll"></a>Erstellen einer Client-App, die die DLL verwendet

Überlegen Sie beim Erstellen einer DLL, wie Client-Apps diese verwenden. Clientquellcode muss zur Kompilierzeit über die Deklarationen verfügen, um die Funktionen aufzurufen oder auf die von einer DLL exportierten Daten zuzugreifen. Zur Linkzeit benötigt der Linker Informationen zum Auflösen von Funktionsaufrufen oder Datenzugriffen. Eine DLL stellt diese Informationen in einer *Importbibliothek* bereit. Diese Datei enthält Informationen zur Suche nach den Funktionen und Daten anstelle des eigentlichen Codes. Zur Laufzeit muss die DLL dem Client an einem Speicherort zur Verfügung stehen, den das Betriebssystem finden kann.

Unabhängig davon, ob es sich um Ihre eigene oder eine DLL von einem Drittanbieter handelt, benötigt Ihr Client-App-Projekt mehrere Informationen, um diese DLL zu verwenden. Es muss nach den Headern gesucht werden, die die DLL-Exporte, die Importbibliotheken für den Linker und die DLL selbst deklarieren. Eine Möglichkeit besteht darin, all diese Dateien in Ihr Clientprojekt zu kopieren. Da Drittanbieter-DLLs sich während der Entwicklung Ihres Clients wahrscheinlich nicht ändern, ist diese Methode möglicherweise die beste. Wenn Sie jedoch auch die DLL erstellen, sollten Sie eine Duplizierung besser vermeiden. Wenn Sie eine lokale Kopie der DLL-Dateien erstellen, die sich noch in der Entwicklungsphase befinden, könnte es passieren, dass Sie versehentlich eine Headerdatei nur in einer Kopie der DLL ändern oder eine veraltete Bibliothek verwenden.

Es empfiehlt sich, den Includepfad in Ihrem Clientprojekt so festzulegen, dass die DLL-Headerdateien direkt aus dem DLL-Projekt eingeschlossen werden, um nicht synchronen Code zu vermeiden. Legen Sie auch den Bibliothekspfad in Ihrem Clientprojekt so fest, dass die DLL-Importbibliotheken aus dem DLL-Projekt eingeschlossen sind. Zum Schluss kopieren Sie die kompilierte DLL aus dem DLL-Projekt in das Clientbuildausgabeverzeichnis. Mit diesem Schritt ermöglichen Sie es der Client-App, denselben DLL-Code zu verwenden.

::: moniker range=">=msvc-160"

### <a name="to-create-a-client-app-in-visual-studio"></a>So erstellen Sie eine Client-App in Visual Studio

1. Klicken Sie in der Menüleiste auf **Datei**  > **Neu**  > **Projekt** , um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++** , die **Plattform** auf **Windows** und den **Projekttyp** auf **Konsole** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**.

1. Geben Sie auf der Seite **Neues Projekt konfigurieren** in das Feld **Projektname** den Namen *MathClient* ein, um einen Namen für das Projekt festzulegen. Behalten Sie die Standardwerte für **Speicherort** und **Projektmappenname** bei. Legen Sie **Projektmappe** auf **Neue Projektmappe erstellen** fest. Deaktivieren Sie bei Bedarf die Option **Legen Sie die Projektmappe und das Projekt im selben Verzeichnis ab**.

   ![Screenshot des Dialogfelds „Neues Projekt erstellen“, in dem die Option „Konsolenanwendung“ hervorgehoben ist](media/mathclient-project-name-2019.png "Benennen des Clientprojekts")

1. Klicken Sie auf die Schaltfläche **Erstellen** , um das Clientprojekt zu erstellen.

Es wird ein kleines Konsolenanwendungsprojekt für Sie erstellt. Der Name der Hauptquelldatei ist derselbe wie der Projektname, den Sie zuvor eingegeben haben. In diesem Beispiel lautet der Name **MathClient.cpp**. Sie können die App kompilieren, aber verwenden Sie noch nicht Ihre DLL.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>So erstellen Sie eine Client-App in Visual Studio 2017

1. Klicken Sie auf der Menüleiste auf **Datei** > **Neu** > **Projekt** , um eine C++-App zu erstellen, die die erstellte DLL verwendet.

1. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Installiert** > **Visual C++** den Eintrag **Windows Desktop** aus. Klicken Sie im mittleren Bereich auf **Windows-Konsolenanwendung**. Geben Sie *MathClient* als Projektnamen im Bearbeitungsfeld **Name** ein.  Behalten Sie die Standardwerte für **Speicherort** und **Projektmappenname** bei. Legen Sie **Projektmappe** auf **Neue Projektmappe erstellen** fest. Aktivieren Sie ggf. **Projektmappenverzeichnis erstellen**.

   ![Screenshot des Dialogfelds „Neues Projekt“, in dem „Installiert“ > „Visual C plus plus“ > „Windows-Desktop“ ausgewählt, „Windows-Konsolenanwendung“ hervorgehoben und im Textfeld „Name“ der Text „MathClient“ eingegeben ist.](media/mathclient-new-project-name-159.png "Benennen des Clientprojekts")

1. Klicken Sie auf **OK** , um das Client-App-Projekt zu erstellen.

Es wird ein kleines Konsolenanwendungsprojekt für Sie erstellt. Der Name der Hauptquelldatei ist derselbe wie der Projektname, den Sie zuvor eingegeben haben. In diesem Beispiel lautet der Name **MathClient.cpp**. Sie können die App kompilieren, aber verwenden Sie noch nicht Ihre DLL.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-client-app-in-visual-studio-2015"></a>So erstellen Sie eine Client-App in Visual Studio 2015

1. Klicken Sie auf der Menüleiste auf **Datei** > **Neu** > **Projekt** , um eine C++-App zu erstellen, die die erstellte DLL verwendet.

1. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Installiert** > **Vorlagen** > **Visual C++** den Eintrag **Win32** aus. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung** aus. Geben Sie *MathClient* als Projektnamen im Bearbeitungsfeld **Name** ein. Behalten Sie die Standardwerte für **Speicherort** und **Projektmappenname** bei. Legen Sie **Projektmappe** auf **Neue Projektmappe erstellen** fest. Aktivieren Sie ggf. **Projektmappenverzeichnis erstellen**.

   ![Screenshot des Dialogfelds „Neues Projekt“, in dem „Installiert“ > „Vorlagen“ > „Visual C plus plus“ > „Win32“ ausgewählt, „Win32-Konsolenanwendung Visual C plus plus“ hervorgehoben und im Textfeld „Name“ der Text „MathClient“ eingegeben ist](media/mathclient-project-name.png "Benennen des Clientprojekts")

1. Klicken Sie auf **OK** , um das Dialogfeld **Neues Projekt** zu schließen und den **Win32-Anwendungs-Assistenten** zu starten. Wählen Sie auf der Seite **Übersicht** des Dialogfelds **Win32-Anwendungs-Assistent** die Schaltfläche **Weiter** .

1. Wählen Sie auf der Seite **Anwendungseinstellungen** unter **Anwendungstyp** die Option **Konsolenanwendung** aus, falls diese nicht bereits ausgewählt ist.

1. Wählen Sie die Schaltfläche **Fertig stellen** , um das Projekt zu erstellen.

Nach Abschluss des Assistenten wurde ein minimales Konsolenanwendungsprojekt für Sie erstellt. Der Name der Hauptquelldatei ist derselbe wie der Projektname, den Sie zuvor eingegeben haben. In diesem Beispiel lautet der Name **MathClient.cpp**. Sie können die App kompilieren, aber verwenden Sie noch nicht Ihre DLL.

::: moniker-end

Ihr Projekt muss die Datei *MathLibrary.h* enthalten, um als Nächstes die „MathLibrary“-Funktionen im Quellcode aufzurufen. Sie könnten diese Headerdatei in Ihr Client-App-Projekt kopieren und dann als vorhandenes Element zum Projekt hinzufügen. Diese Methode ist für Drittanbieterbibliotheken möglicherweise eine gute Wahl. Wenn Sie jedoch gleichzeitig am Code für die DLL und den Client arbeiten, sind die Headerdateien möglicherweise nicht mehr synchron. Legen Sie die Einstellungen für den Pfad **Zusätzliche Includeverzeichnisse** in Ihrem Projekt so fest, dass der Pfad zum ursprünglichen Header eingeschlossen wird, um dieses Problem zu vermeiden.

### <a name="to-add-the-dll-header-to-your-include-path"></a>So fügen Sie den DLL-Header zum Includepfad hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **MathClient** , um das Dialogfeld **Eigenschaftenseiten** zu öffnen.

1. Klicken Sie im Dropdownfeld **Konfiguration** auf die Option **Alle Konfigurationen** , wenn diese nicht bereits ausgewählt ist.

1. Klicken Sie im linken Bereich auf **Konfigurationseigenschaften** > **C/C++**  > **Allgemein**.

1. Wählen Sie im Eigenschaftenbereich das Dropdown-Steuerelement neben dem Bearbeitungsfeld für **Zusätzliche Includeverzeichnisse** aus, und klicken Sie auf **Bearbeiten**.

   ![Bearbeiten der Eigenschaft „Zusätzliche Includeverzeichnisse“](media/mathclient-additional-include-directories-property.png "Bearbeiten der Eigenschaft „Zusätzliche Includeverzeichnisse“")

1. Doppelklicken Sie im oberen Bereich des Dialogfelds **Zusätzliche Includeverzeichnisse** , um ein Bearbeitungssteuerelement zu aktivieren. Alternativ können Sie auf das Ordnersymbol klicken, um einen neuen Eintrag zu erstellen.

1. Geben Sie im Bearbeitungssteuerelement den Pfad zum Speicherort der Headerdatei **MathLibrary.h** an. Sie können auf das Steuerelement mit den drei Auslassungspunkten ( **...** ) klicken, um zum richtigen Ordner zu navigieren.

   Sie können auch einen relativen Pfad von den Clientquelldateien zum Ordner eingeben, der die DLL-Headerdateien enthält. Wenn Sie die Anweisungen befolgt und Ihr Clientprojekt in einer anderen Projektmappe als die DLL abgelegt haben, sollte der relative Pfad wie folgt aussehen:

   `..\..\MathLibrary\MathLibrary`

   Wenn sich die DLL und die Clientprojekte in derselben Projektmappe befinden, könnte der relative Pfad folgendermaßen aussehen:

   `..\MathLibrary`

   Wenn sich die DLL und die Clientprojekte in anderen Ordnern befinden, passen Sie den relativen Pfad entsprechend an. Sie können auch das Steuerelement mit den drei Auslassungspunkten verwenden, um nach dem Ordner zu suchen.

   ![Hinzufügen des Headerspeicherorts zur Eigenschaft „Zusätzliche Includeverzeichnisse“](media/mathclient-additional-include-directories.png "Hinzufügen des Headerspeicherorts zur Eigenschaft „Zusätzliche Includeverzeichnisse“")

1. Nachdem Sie den Pfad zur Headerdatei im Dialogfeld **Zusätzliche Includeverzeichnisse** eingegeben haben, klicken Sie auf die Schaltfläche **OK**. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf die Schaltfläche **OK** , um Ihre Änderungen zu speichern.

Jetzt können Sie die Datei **MathLibrary.h** einschließen und die von dieser Datei deklarierten Funktionen in Ihrer Clientanwendung verwenden. Ersetzen Sie den Inhalt von **MathClient.cpp** durch diesen Code:

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
// #include "pch.h" Uncomment for Visual Studio 2017 and earlier
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

Dieser Code kann kompiliert, jedoch nicht verknüpft werden. Wenn Sie die Client-App jetzt erstellen, werden in der Fehlerliste mehrere LNK2019-Fehler angezeigt. Das liegt daran, dass in Ihrem Projekt einige Informationen fehlen: Sie haben noch nicht angegeben, dass das Projekt eine Abhängigkeit von der *MathLibrary.lib* -Bibliothek aufweist. Außerdem haben Sie haben dem Linker nicht mitgeteilt, wie nach der Datei *MathLibrary.lib* gesucht werden soll.

Sie können die Bibliotheksdatei direkt in Ihr Client-App-Projekt kopieren, um dieses Problem zu beheben. Der Linker findet und verwendet diese automatisch. Wenn sich aber sowohl Bibliothek als auch Client-App noch in der Entwicklungsphase befinden, könnte dies jedoch zu Änderungen in einer Kopie führen, die in der anderen nicht widergespiegelt werden. Sie können die Eigenschaft **Zusätzliche Abhängigkeiten** festlegen, sodass dem Buildsystem mitgeteilt wird, dass Ihr Projekt von *MathLibrary.lib* abhängig ist, um dieses Problem zu vermeiden. Außerdem können Sie in Ihrem Projekt den Pfad **Zusätzliche Bibliotheksverzeichnisse** festlegen, sodass bei der Verknüpfung der Pfad zur ursprünglichen Bibliothek eingeschlossen wird.

### <a name="to-add-the-dll-import-library-to-your-project"></a>So fügen Sie die DLL-Importbibliothek zu Ihrem Projekt hinzu

1. Klicken Sie mit der rechten Maustaste auf den Knoten **MathClient** im **Projektmappen-Explorer** , und klicken Sie dann auf **Eigenschaften** , um das Dialogfeld **Eigenschaftenseiten** zu öffnen.

1. Klicken Sie im Dropdownfeld **Konfiguration** auf die Option **Alle Konfigurationen** , wenn diese nicht bereits ausgewählt ist. Dadurch wird sichergestellt, dass alle Eigenschaftsänderungen für Debug- und Releasebuilds gelten.

1. Klicken Sie im linken Bereich auf **Konfigurationseigenschaften** > **Linker** > **Eingabe**. Wählen Sie im Eigenschaftenbereich das Dropdown-Steuerelement neben dem Bearbeitungsfeld für **Zusätzliche Abhängigkeiten** aus, und klicken Sie auf **Bearbeiten**.

   ![Bearbeiten der Eigenschaft „Zusätzliche Abhängigkeiten“](media/mathclient-additional-dependencies-property.png "Bearbeiten der Eigenschaft „Zusätzliche Abhängigkeiten“")

1. Fügen Sie im Dialogfeld **Zusätzliche Abhängigkeiten** die Datei *MathLibrary.lib* zur Liste im oberen Bearbeitungssteuerelement hinzu.

   ![Hinzufügen der Bibliotheksabhängigkeit](media/mathclient-additional-dependencies.png "Hinzufügen der Bibliotheksabhängigkeit")

1. Klicken Sie auf **OK** , um zum Dialogfeld **Eigenschaftenseiten** zurückzukehren.

1. Klicken Sie im linken Bereich auf **Konfigurationseigenschaften** > **Linker** > **Allgemein**. Wählen Sie im Eigenschaftenbereich das Dropdown-Steuerelement neben dem Bearbeitungsfeld für **Zusätzliche Bibliotheksverzeichnisse** aus, und klicken Sie auf **Bearbeiten**.

   ![Bearbeiten der Eigenschaft „Zusätzliche Bibliotheksverzeichnisse“](media/mathclient-additional-library-directories-property.png "Bearbeiten der Eigenschaft „Zusätzliche Bibliotheksverzeichnisse“")

1. Doppelklicken Sie im oberen Bereich des Dialogfelds **Zusätzliche Bibliotheksverzeichnisse** , um ein Bearbeitungssteuerelement zu aktivieren. Geben Sie im Bearbeitungssteuerelement den Pfad zum Speicherort der Datei **MathLibrary.lib** an. Standardmäßig befindet sich diese Datei in einem Ordner namens *Debuggen* direkt unter dem DLL-Projektmappenordner. Wenn Sie einen Releasebuild erstellen, wird die Datei in einen Ordner namens *Release* abgelegt. Sie können das `$(IntDir)`-Makro verwenden, damit der Linker die DLL findet, unabhängig davon, welche Art von Build Sie erstellen. Wenn Sie die Anweisungen befolgt und Ihr Clientprojekt in einer anderen Projektmappe als das DLL-Projekt abgelegt haben, sollte der relative Pfad wie folgt aussehen:

   `..\..\MathLibrary\$(IntDir)`

   Wenn sich die DLL und die Clientprojekte an anderen Speicherorten befinden, passen Sie den relativen Pfad entsprechend an.

   ![Hinzufügen des Bibliotheksverzeichnisses](media/mathclient-additional-library-directories.png "Hinzufügen des Bibliotheksverzeichnisses")

1. Wenn Sie den Pfad zur Bibliotheksdatei im Dialogfeld **Zusätzliche Bibliotheksverzeichnisse** eingegeben haben, klicken Sie auf die Schaltfläche **OK** , um zum Dialogfeld **Eigenschaftenseiten** zurückzukehren. Klicken Sie auf **OK** , um die Änderungen an den Eigenschaften zu speichern.

Ihre Client-App kann jetzt erfolgreich kompiliert und verknüpft werden, aber noch sind nicht alle erforderlichen Komponenten für die Ausführung vorhanden. Wenn das Betriebssystem Ihre App lädt, sucht es nach der MathLibrary-DLL. Wenn die DLL in bestimmten Systemverzeichnissen, dem Umgebungspfad oder dem lokalen App-Verzeichnis nicht gefunden wird, kann die App nicht geladen werden. Abhängig vom Betriebssystem wird eine Fehlermeldung wie die folgende angezeigt:

![Fehlermeldung, dass MathLibrary-DLL nicht gefunden wurde](media/mathclient-system-error-mathlibrary-dll-not-found.png "Fehlermeldung, dass MathLibrary-DLL nicht gefunden wurde")

Eine Möglichkeit zum Vermeiden dieses Problems besteht darin, die DLL in das Verzeichnis zu kopieren, das Ihre ausführbare Clientdatei als Bestandteil des Buildprozesses enthält. Sie können Ihrem Projekt ein **Postbuildereignis** mit einem Befehl hinzufügen, der die DLL in Ihr Buildausgabeverzeichnis kopiert. Der hier angegebene Befehl kopiert die DLL nur, wenn diese fehlt oder geändert wurde. Es werden Makros verwendet, um basierend auf der Buildkonfiguration in die bzw. aus den Debug- oder Releasespeicherorten zu kopieren.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>So kopieren Sie die DLL in einem Postbuildereignis

1. Klicken Sie mit der rechten Maustaste auf den Knoten **MathClient** im **Projektmappen-Explorer** , und klicken Sie dann auf **Eigenschaften** , um das Dialogfeld **Eigenschaftenseiten** zu öffnen.

1. Wählen Sie im Dropdownfeld **Konfiguration** den Eintrag **Alle Konfigurationen** aus, falls dieser nicht bereits ausgewählt ist.

1. Klicken Sie im linken Bereich auf **Konfigurationseigenschaften** > **Buildereignisse** > **Postbuildereignis**.

1. Klicken Sie im Eigenschaftenbereich auf das Bearbeitungssteuerelement im Feld **Befehlszeile**. Wenn Sie die Anweisungen befolgt und Ihr Clientprojekt in einer anderen Projektmappe als das DLL-Projekt abgelegt haben, geben Sie diesen Befehl ein:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   Wenn sich die DLL und die Clientprojekte in anderen Verzeichnissen befinden, ändern Sie den relativen Pfad zur DLL entsprechend.

   ![Hinzufügen des Postbuildbefehls](media/mathclient-post-build-command-line.png "Hinzufügen des Postbuildbefehls")

1. Klicken Sie auf die Schaltfläche **OK** , um die Änderungen an den Projekteigenschaften zu speichern.

Jetzt sind alle Elemente vorhanden, die benötigt werden, damit die Client-App kompiliert und ausgeführt werden kann. Kompilieren Sie die Anwendung, in dem Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** auswählen. Das Fenster **Ausgabe** in Visual Studio sollte in Abhängigkeit von der von Ihnen installierten Version von Visual Studio in etwa wie folgt aussehen:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Herzlichen Glückwunsch: Sie haben eine Anwendung erstellt, die Funktionen in Ihrer DLL aufruft! Führen Sie Ihre Anwendung jetzt aus, um zu sehen, was passiert. Klicken Sie in der Menüleiste auf **Debuggen** > **Ohne Debuggen**. Visual Studio öffnet ein Befehlsfenster, in dem das Programm ausgeführt wird. Der letzte Teil der Ausgabe sollte wie folgt aussehen:

![Starten der Client-App ohne Debuggen](media/mathclient-run-without-debugging.png "Starten der Client-App ohne Debuggen")

Drücken Sie eine beliebige Taste, um das Befehlsfenster zu schließen.

Sie haben eine DLL und eine Clientanwendung erstellt – nun können Sie damit experimentieren. Legen Sie beispielsweise Haltepunkte im Code der Client-App fest, und führen Sie die App im Debugger aus. Sehen Sie sich an, was passiert, wenn Sie einen Bibliotheksaufruf schrittweise ausführen. Fügen Sie der Bibliothek weitere Funktionen hinzu, oder schreiben Sie eine weitere Client-App, die Ihre DLL verwendet.

Wenn Sie Ihre App bereitstellen, müssen Sie auch die DLL bereitstellen, die von der App verwendet wird. Die einfachste Möglichkeit, die von Ihnen erstellten oder von Drittanbietern eingeschlossenen DLLs zur Verfügung zu stellen, besteht darin, sie im gleichen Verzeichnis abzulegen, in dem sich auch Ihre App befindet. Dies wird als *lokale App-Bereitstellung* bezeichnet. Weitere Informationen zur Bereitstellung finden Sie unter [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Siehe auch

[Aufrufen von DLL-Funktionen aus Visual Basic-Anwendungen heraus](calling-dll-functions-from-visual-basic-applications.md)
