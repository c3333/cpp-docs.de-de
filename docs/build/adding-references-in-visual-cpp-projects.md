---
title: Verarbeiten von Bibliotheken und Komponenten C++ in Projekten
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: a8cd13e27859d09bcaaca1f5f6f1c2750b908fe6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078785"
---
# <a name="consuming-libraries-and-components"></a>Verarbeiten von Bibliotheken und Komponenten

Häufig muss ein C++ Projektfunktionen aufrufen oder auf Daten in einer binären Datei zugreifen, wie z. b. statische Bibliothek (LIB-Dateien), dll, Windows-Runtime Komponente, COM-Komponente oder .NET-Assembly. In diesen Fällen müssen Sie das Projekt so konfigurieren, dass es diese Binärdatei zur Buildzeit finden kann. Die spezifischen Schritte richten sich nach dem Typ des Projekts, dem Typ der Binärdatei und dem, ob die Binärdatei in der gleichen Projekt Mappe wie das Projekt erstellt wird.

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Verarbeiten von Bibliotheken, die über vcpkg heruntergeladen wurden

Wenn Sie eine Bibliothek nutzen möchten, die Sie mit dem **vcpkg** -Paket-Manager heruntergeladen haben, können Sie die nachfolgenden Anweisungen ignorieren. Weitere Informationen finden Sie [unter vcpkg C++ : ein Paket-Manager für Windows, Linux und MacOS](vcpkg.md#integrate-with-visual-studio-windows) .

## <a name="consuming-static-libraries"></a>Verwenden statischer Bibliotheken

Wenn Ihr statisches Bibliotheksprojekt in derselben Projekt Mappe erstellt wird:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>Schließen Sie die Header Datei (en) für die statische Bibliothek in Anführungszeichen ein. In einer typischen Lösung beginnt der Pfad mit `../<library project name>`. IntelliSense hilft Ihnen, es zu finden.
2. Fügen Sie einen Verweis auf das statische Bibliotheksprojekt hinzu. Klicken Sie in **Projektmappen-Explorer** unter dem Knoten Anwendungsprojekt mit der rechten Maustaste auf **Verweise** , und wählen Sie **Verweis hinzufügen**aus.

Wenn die statische Bibliothek nicht Teil der Projekt Mappe ist:

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten Anwendungsprojekt, und wählen Sie dann **Eigenschaften**aus.
2. Fügen Sie auf der Eigenschaften Seite für **VC + +-Verzeichnisse** den Pfad zum Verzeichnis hinzu, in dem sich die LIB-Datei in **Bibliotheks Pfaden** befindet, und fügen Sie den Pfad zu den Bibliotheks Header Dateien in den Includeverzeichnissen hinzu. **Include Directories**  
3. Fügen Sie auf der Eigenschaften Seite **Linker > Eingabe** den Namen der LIB-Datei **zusätzlichen Abhängigkeiten**hinzu.

## <a name="dynamic-link-libraries"></a>Dynamic Link Libraries

Wenn die dll als Teil derselben Projekt Mappe wie die Anwendung erstellt wird, führen Sie dieselben Schritte wie für eine statische Bibliothek aus.

Wenn die dll nicht Teil der Anwendungslösung ist, benötigen Sie die DLL-Datei, die Header (e) mit Prototypen für die exportierten Funktionen und Klassen sowie eine LIB-Datei, die die erforderlichen Verknüpfungs Informationen bereitstellt.

1. Kopieren Sie die dll in den Ausgabeordner des Projekts oder in einen anderen Ordner im standardmäßigen Windows-Suchpfad für DLLs. Siehe [Such Reihenfolge der Dynamic-Link-Bibliothek](/windows/win32/dlls/dynamic-link-library-search-order).
2. Führen Sie die Schritte 1-3 für statische Bibliotheken aus, um die Pfade zu den Headern und der LIB-Datei bereitzustellen.

## <a name="com-objects"></a>COM-Objekte

Wenn Ihre Native C++ Anwendung ein COM-Objekt verwenden muss und dieses Objekt *registriert*ist, müssen Sie lediglich cokreateinstance aufrufen und die CLSID des Objekts übergeben. Das System findet es in der Windows-Registrierung und lädt es. Ein C++/CLI-Projekt kann ein COM-Objekt auf die gleiche Weise nutzen, oder durch Hinzufügen eines Verweises auf das Objekt aus der Liste **Verweise > com hinzufügen** und Verarbeiten dieses Objekts über seinen [Runtime Callable Wrapper](/dotnet/framework/interop/runtime-callable-wrapper).

## <a name="net-assemblies-and-windows-runtime-components"></a>.NET-Assemblys und Windows-Runtime Komponenten

In UWP- C++oder/CLI-Projekten nutzen Sie .NET-Assemblys oder Windows-Runtime Komponenten, indem Sie einen *Verweis* auf die Assembly oder Komponente hinzufügen. Unter dem Knoten **Verweise** in einem UWP- C++oder/CLI-Projekt sehen Sie Verweise auf häufig verwendete Komponenten. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Verweise** , um den **Verweis-Manager** aufzurate und die zusätzlichen Komponenten zu durchsuchen, die dem System bekannt sind. Klicken Sie auf die Schaltfläche **Durchsuchen** , um zu einem beliebigen Ordner zu navigieren, in dem sich eine benutzerdefinierte Da .NET-Assemblys und Windows-Runtime Komponenten integrierte Typinformationen enthalten, können Sie Ihre Methoden und Klassen anzeigen, indem Sie mit der rechten Maustaste klicken und **in Objektkatalog anzeigen**wählen.

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

Assemblyverweiseigenschaften sind nur für Verweise auf .NET Framework C++Assemblys in/CLI-Projekten verfügbar. Diese Eigenschaften werden nur angezeigt, wenn im Bereich **Verweise** eine .NET Framework Assembly ausgewählt wird. Die Eigenschaften können nicht geändert werden.

- **Relativer Pfad**

   Zeigt den relativen Pfad vom Projektverzeichnis zur Assembly an, auf die verwiesen wird.

### <a name="build-properties"></a>Buildeigenschaften

Die folgenden Eigenschaften stehen für verschiedene Arten von Verweisen zur Verfügung. Sie ermöglichen Ihnen die Angabe, wie die Erstellung mit Verweisen erfolgen soll.

- **Lokale Kopie**

   Gibt an, ob die Assembly, auf die verwiesen wird, während eines Buildvorgangs automatisch an den Zielspeicherort kopiert wird.

- **Lokale Satellitenassemblys kopieren (C++/CLI)**

   Gibt an, ob die Satellitenassemblys der Assembly, auf die verwiesen wird, während eines Buildvorgangs automatisch an den Zielspeicherort kopiert werden. Wird nur verwendet, wenn **Lokale Kopie** den Wert **true** aufweist.

- **Verweisassemblyausgabe**

   Gibt an, dass die Assembly im Buildvorgang verwendet wird. Wenn **true**, wird die Assembly während des Buildvorgangs in der Befehlszeile des Compilers verwendet.

### <a name="project-to-project-reference-properties"></a>Interprojektverweiseigenschaften

Die folgenden Eigenschaften definieren einen *Projekt-zu-Projekt-Verweis* aus dem Projekt, das im Bereich **Verweise** ausgewählt ist, auf ein anderes Projekt in derselben Projekt Mappe. Weitere Informationen finden Sie unter [Verwalten von Verweisen in einem Projekt](/visualstudio/ide/managing-references-in-a-project).

- **Bibliothekabhängigkeiten verknüpfen**

   Wenn diese Eigenschaft **True**ist, fügt das Projektsystem in das abhängige Projekt die LIB-Dateien ein, die vom unabhängigen Projekt erstellt werden. Normalerweise geben Sie **True**an.

- **Projektbezeichner**

   Identifiziert eindeutig das unabhängige Projekt. Der Eigenschaftswert ist eine interne System-GUID, die nicht geändert werden kann.

- **Bibliothekabhängigkeitseingaben verwenden**

   Wenn diese Eigenschaft **False**ist, fügt das Projektsystem nicht in das abhängige Projekt die OBJ-Dateien für die Bibliothek ein, die vom unabhängigen Projekt erstellt wurden. Folglich deaktiviert dieser Wert inkrementelles Verknüpfen. In der Regel geben Sie **False** an, da das Erstellen der Anwendung lange dauern kann, wenn viele unabhängige Projekte vorhanden sind.

### <a name="read-only-reference-properties-com--net"></a>Schreibgeschützte Verweis Eigenschaften (com & .net)

Die folgenden Eigenschaften gelten für COM- und Assemblyverweise und können nicht geändert werden.

- **Assemblyname**

   Zeigt den Assemblynamen für die Assembly an, auf die verwiesen wird.

- **Kultur**

   Zeigt die Kultur des ausgewählten Verweises an.

- **Beschreibung**

   Zeigt die Beschreibung des ausgewählten Verweises an.

- **Vollständiger Pfad**

   Zeigt den Verzeichnispfad der Assembly an, auf die verwiesen wird.

- **Identität**

   Für die .NET Framework-Assemblys wird der vollständige Pfad angezeigt. Zeigt die GUID für COM-Komponenten an.

- **Label**

   Zeigt die Bezeichnung des Verweises an.

- **Name**

   Zeigt den Namen des Verweises an.

- **Öffentliches Schlüsseltoken**

   Zeigt das öffentliche Schlüsseltoken zur Identifizierung der Assembly an, auf die verwiesen wird.

- **Starker Name**

   `true` , wenn die Assembly, auf die verwiesen wird, einen starken Namen hat. Eine Assembly mit starkem Namen verfügt über eine eindeutige Versionsangabe.

- **Version**

   Zeigt die Version der Assembly an, auf die verwiesen wird.

## <a name="see-also"></a>Weitere Informationen

[C++Referenz zur Projekteigenschaften Seite](reference/property-pages-visual-cpp.md)<br>
[Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio](working-with-project-properties.md)