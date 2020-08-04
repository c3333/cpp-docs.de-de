---
title: Verwenden von Bibliotheken und Komponenten in C++-Projekten
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: 37c0120b7879678ad65dfbbffc17bd6d6791fdfe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229908"
---
# <a name="consuming-libraries-and-components"></a>Verwenden von Bibliotheken und Komponenten

In C++-Projekten ist oft der Aufruf von Funktionen oder der Zugriff auf Daten in einer Binärdatei wie einer statischen Bibliothek (LIB-Dateien), einer DLL, einer Komponente für Windows-Runtime, einer COM-Komponente oder einer .NET-Assembly erforderlich. In diesen Fällen müssen Sie das Projekt so konfigurieren, dass die Binärdatei zur Buildzeit gefunden werden kann. Die genauen Schritte hängen vom Typ Ihres Projekts, dem Typ der Binärdatei sowie davon ab, ob die Binärdatei in derselben Projektmappe wie Ihr Projekt erstellt wird.

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Verwenden von über vcpkg heruntergeladenen Bibliotheken

Wenn Sie eine Bibliothek verwenden möchten, die Sie mithilfe des Paket-Managers **vcpkg** heruntergeladen haben, können Sie die Anweisungen unten ignorieren. Weitere Informationen finden Sie unter [vcpkg: Ein C++-Paket-Manager für Windows, Linux und macOS](vcpkg.md#integrate-with-visual-studio-windows).

## <a name="consuming-static-libraries"></a>Verwenden von statischen Bibliotheken

Anleitung, wenn Ihr Projekt mit statischer Bibliothek in derselben Projektmappe erstellt wird:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>Schließen Sie die Headerdateien für die statische Bibliothek mithilfe von Anführungszeichen ein. In einer normalen Projektmappe beginnt der Pfad mit `../<library project name>`. IntelliSense unterstützt Sie bei der Suche danach.
2. Fügen Sie einen Verweis auf das Projekt mit statischer Bibliothek hinzu. Klicken Sie im **Projektmappen-Explorer** unter dem Projektknoten der Anwendung auf die Option **Verweise**, und wählen Sie dort die Option **Verweis hinzufügen** aus.

Anleitung, wenn die statische Bibliothek nicht Teil der Projektmappe ist:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten des Anwendungsprojekts, und wählen Sie die Option **Eigenschaften** aus.
2. Fügen Sie auf der Eigenschaftenseite **VC++-Verzeichnisse** unter **Bibliothekspfade** den Pfad zum Verzeichnis hinzu, in dem sich die LIB-Datei befindet, und fügen Sie unter **Includeverzeichnisse** den Pfad zu den Bibliotheksheaderdateien hinzu.  
3. Fügen Sie auf der Eigenschaftenseite **Linker > Eingabe** den Namen der LIB-Datei unter **Zusätzliche Abhängigkeiten** hinzu.

## <a name="dynamic-link-libraries"></a>Dynamic Link Librarys (DLLs)

Wenn die DLL als Teil derselben Projektmappe wie die der Anwendung erstellt wird, befolgen Sie dieselben Schritte wie für eine statische Bibliothek.

Wenn die DLL nicht Bestandteil der Projektmappe der Anwendung ist, benötigen Sie die DLL-Datei, die Header mit den Prototypen der exportierten Funktionen und Klassen und eine LIB-Datei, die die erforderlichen Verknüpfungsinformationen bereitstellt.

1. Kopieren Sie die DLL in den Ausgabeordner Ihres Projekts oder in einen anderen Ordner unter dem Standardsuchpfad für DLLs unter Windows. Weitere Informationen finden Sie unter [Suchreihenfolge für Dynamic Link Librarys](/windows/win32/dlls/dynamic-link-library-search-order).
2. Befolgen Sie die Schritte 1–3 für statische Bibliotheken, um die Pfade zu den Headern und der LIB-Datei bereitzustellen.

## <a name="com-objects"></a>COM-Objekte

Wenn Ihre native C++-Anwendung ein COM-Objekt verwenden muss und dieses Objekt *registriert* ist, müssen Sie nur CoCreateInstance aufrufen und die CLSID des Objekts übergeben. Das System findet und lädt CoCreateInstance in der Windows-Registrierung. Ein C++-/CLI-Projekt kann ein COM-Objekt auf dieselbe Weise verwenden, oder indem ein Verweis darauf in der Liste **Verweise hinzufügen > COM** hinzugefügt und es über den dazugehörigen [Runtime Callable Wrapper](/dotnet/framework/interop/runtime-callable-wrapper) verwendet wird.

## <a name="net-assemblies-and-windows-runtime-components"></a>.NET-Assemblys und Windows-Runtimekomponenten

In UWP- oder C++-/CLI-Projekten verwenden Sie .NET-Assemblys oder Windows-Runtimekomponenten, indem Sie einen *Verweis* auf die Assembly oder Komponente hinzufügen. Unter dem Knoten **Verweise** in einem UWP- oder C++-/CLI-Projekt finden Sie Verweise auf häufig verwendete Komponenten. Klicken Sie mit der rechten Maustaste auf den Knoten **Verweise** im **Projektmappen-Explorer**, um den **Verweis-Manager** zu öffnen und weitere Komponenten zu durchsuchen, die dem System bekannt sind. Klicken Sie auf die Schaltfläche **Durchsuchen**, um zu Ordnern zu navigieren, in denen sich benutzerdefinierte Komponenten befinden. Da .NET-Assemblys und Windows-Runtimekomponenten integrierte Typinformationen enthalten, können Sie ihre Methoden und Klassen anzeigen, indem Sie mit der rechten Maustaste darauf klicken und die Option **Im Objektkatalog anzeigen** auswählen.

## <a name="reference-properties"></a>Verweiseigenschaften

Jede Art von Verweis verfügt über Eigenschaften. Sie können die Eigenschaften anzeigen, indem Sie den Verweis im Projektmappen-Explorer auswählen und **ALT+EINGABE**drücken bzw. mit der rechten Maustaste klicken und **Eigenschaften**auswählen. Einige Eigenschaften sind schreibgeschützt, während andere geändert werden können. Allerdings müssen Sie diese Eigenschaften in der Regel nicht manuell ändern.

### <a name="activex-reference-properties"></a>ActiveX-Verweiseigenschaften

ActiveX-Verweiseigenschaften sind nur für Verweise auf COM-Komponenten verfügbar. Diese Eigenschaften werden nur angezeigt, wenn eine COM-Komponente im Bereich **Verweise** ausgewählt ist. Die Eigenschaften können nicht geändert werden.

- **Vollständiger Pfad des Steuerelements**

   Zeigt den Verzeichnispfad des Steuerelements an, auf das verwiesen wird.

- **GUID des Steuerelements**

   Zeigt de GUID für das ActiveX-Steuerelement an.

- **Steuerelementversion**

   Zeigt die Version des ActiveX-Steuerelements an, auf das verwiesen wird.

- **Typbibliotheksnamen**

   Zeigt den Namen der Typbibliothek an, auf die verwiesen wird.

- **Wrappertool**

   Zeigt das Tool an, das zum Erstellen der Interop-Assembly aus der COM-Bibliothek oder dem ActiveX-Steuerelement verwendet wird, auf die bzw. das verwiesen wird.

### <a name="assembly-reference-properties-ccli"></a>Assemblyverweiseigenschaften (C++/CLI)

Assemblyverweiseigenschaften sind nur für Verweise auf .NET Framework-Assemblys in C++-/CLI-Projekten verfügbar. Diese Eigenschaften werden nur angezeigt, wenn eine .NET Framework-Assembly im Bereich **Verweise** ausgewählt ist. Die Eigenschaften können nicht geändert werden.

- **Relativer Pfad**

   Zeigt den relativen Pfad vom Projektverzeichnis zur Assembly an, auf die verwiesen wird.

### <a name="build-properties"></a>Buildeigenschaften

Die folgenden Eigenschaften stehen für verschiedene Arten von Verweisen zur Verfügung. Sie ermöglichen Ihnen die Angabe, wie die Erstellung mit Verweisen erfolgen soll.

- **Lokale Kopie**

   Gibt an, ob die Assembly, auf die verwiesen wird, während eines Buildvorgangs automatisch an den Zielspeicherort kopiert wird.

- **Lokale Satellitenassemblys kopieren (C++/CLI)**

   Gibt an, ob die Satellitenassemblys der Assembly, auf die verwiesen wird, während eines Buildvorgangs automatisch an den Zielspeicherort kopiert werden. Wird nur verwendet, wenn **Lokale Kopie** den Wert **`true`** aufweist.

- **Verweisassemblyausgabe**

   Gibt an, dass die Assembly im Buildvorgang verwendet wird. Wenn **`true`** , wird die Assembly während des Buildvorgangs an der Befehlszeile des Compilers verwendet.

### <a name="project-to-project-reference-properties"></a>Interprojektverweiseigenschaften

Die folgenden Eigenschaften definieren einen *Verweis zwischen Projekten* von dem im Bereich **Verweise** ausgewählten Projekt auf ein anderes Projekt in derselben Projektmappe. Weitere Informationen finden Sie unter [Verwalten von Verweisen in einem Projekt](/visualstudio/ide/managing-references-in-a-project).

- **Bibliothekabhängigkeiten verknüpfen**

   Wenn diese Eigenschaft **True**ist, fügt das Projektsystem in das abhängige Projekt die LIB-Dateien ein, die vom unabhängigen Projekt erstellt werden. Normalerweise geben Sie **True**an.

- **Projektbezeichner**

   Identifiziert eindeutig das unabhängige Projekt. Der Eigenschaftswert ist eine interne System-GUID, die nicht geändert werden kann.

- **Bibliothekabhängigkeitseingaben verwenden**

   Wenn diese Eigenschaft **False**ist, fügt das Projektsystem nicht in das abhängige Projekt die OBJ-Dateien für die Bibliothek ein, die vom unabhängigen Projekt erstellt wurden. Folglich deaktiviert dieser Wert inkrementelles Verknüpfen. In der Regel geben Sie **False** an, da das Erstellen der Anwendung lange dauern kann, wenn viele unabhängige Projekte vorhanden sind.

### <a name="read-only-reference-properties-com--net"></a>Schreibgeschützte Verweiseigenschaften (COM & .NET)

Die folgenden Eigenschaften gelten für COM- und Assemblyverweise und können nicht geändert werden.

- **Assemblyname**

   Zeigt den Assemblynamen für die Assembly an, auf die verwiesen wird.

- **Kultur**

   Zeigt die Kultur des ausgewählten Verweises an.

- **Beschreibung**

   Zeigt die Beschreibung des ausgewählten Verweises an.

- **Vollständiger Pfad**

   Zeigt den Verzeichnispfad der Assembly an, auf die verwiesen wird.

- **Identity**

   Für die .NET Framework-Assemblys wird der vollständige Pfad angezeigt. Zeigt die GUID für COM-Komponenten an.

- **Bezeichnung**

   Zeigt die Bezeichnung des Verweises an.

- **Name**

   Zeigt den Namen des Verweises an.

- **Öffentliches Schlüsseltoken**

   Zeigt das öffentliche Schlüsseltoken zur Identifizierung der Assembly an, auf die verwiesen wird.

- **Starker Name**

   **`true`** , wenn die Assembly, auf die verwiesen wird, einen starken Namen besitzt. Eine Assembly mit starkem Namen verfügt über eine eindeutige Versionsangabe.

- **Version**

   Zeigt die Version der Assembly an, auf die verwiesen wird.

## <a name="see-also"></a>Siehe auch

[Windows C++-Projekteigenschaftenseitenverweis](reference/property-pages-visual-cpp.md)<br>
[Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio](working-with-project-properties.md)
