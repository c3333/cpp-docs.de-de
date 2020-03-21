---
title: Erstellen des Projekts (ATL-Lernprogramm, Teil 1)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: 31ecee084f620256820a685df1f0e6891046fb8f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075329"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Erstellen des Projekts (ATL-Lernprogramm, Teil 1)

In diesem Tutorial werden Sie Schritt für Schritt durch ein nicht attributiertes ATL-Projekt geführt, das ein ActiveX-Objekt erstellt, das ein Polygon anzeigt. Das-Objekt enthält Optionen, mit denen der Benutzer die Anzahl der Seiten, die das Polygon bilden, ändern kann, und den Code, um die Anzeige zu aktualisieren.

> [!NOTE]
> Dieses Tutorial erstellt denselben Quellcode wie das Polygon-Beispiel. Wenn Sie die manuelle Eingabe des Quellcodes vermeiden möchten, können Sie ihn aus dem [Polygon-Beispiel Abstract](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon)herunterladen. Sie können dann auf den Polygon-Quellcode verweisen, während Sie das Tutorial durcharbeiten, oder Sie verwenden, um in Ihrem eigenen Projekt nach Fehlern zu suchen.
> Öffnen Sie zum Kompilieren " *PCH. h* " (*stdafx. h* in Visual Studio 2017 und früher), und ersetzen Sie Folgendes:
>
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
>
> durch
>
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
>
> Der Compiler beschwert sich immer noch darüber, `regsvr32` nicht ordnungsgemäß beendet wird, aber Sie sollten trotzdem die DLL des Steuer Elements erstellt haben und zur Verwendung verfügbar sein.

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>So erstellen Sie das anfängliche ATL-Projekt mithilfe des ATL-Projekt-Assistenten

1. In Visual Studio 2017 und früher: **Datei** > **Neues** > **Projekt**. Öffnen Sie die Registerkarte " **Visual C++**  ", und wählen Sie **MFC/ATL**aus. Wählen Sie **ATL-Projekt**aus.

   In Visual Studio 2019: Wählen Sie **Datei** > **Neues** > **Projekt**aus, geben Sie "ATL" in das Suchfeld ein, und wählen Sie **ATL-Projekt**aus.

1. Geben Sie *Polygon* als Projektnamen ein.

    Der Speicherort für den Quellcode wird normalerweise standardmäßig auf \Users\\\<username > \source\repos festgestellt, und ein neuer Ordner wird automatisch erstellt.

1. Übernehmen Sie in Visual Studio 2019 die Standardwerte, und klicken Sie auf **OK**.
   Klicken Sie in Visual Studio 2017 auf **OK** , um den **ATL-Projekt** -Assistenten zu öffnen. Klicken Sie auf **Anwendungseinstellungen** , um die verfügbaren Optionen anzuzeigen. Da dieses Projekt ein-Steuerelement erstellt und ein-Steuerelement ein Prozess interner Server sein muss, belassen Sie den **Anwendungstyp** als dll. Klicken Sie auf **OK**.

Visual Studio erstellt das Projekt durch die Erstellung mehrerer Dateien. Sie können diese Dateien in **Projektmappen-Explorer** anzeigen, indem Sie das `Polygon`-Objekt erweitern. Die Dateien sind unten aufgeführt.

::: moniker range="<=vs-2017"

|Datei|BESCHREIBUNG|
|----------|-----------------|
|Polygon.cpp|Enthält die Implementierung von `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`und `DllUnregisterServer`. Enthält auch die Objekt Zuordnung, bei der es sich um eine Liste der ATL-Objekte in Ihrem Projekt handelt. Diese ist anfänglich leer.|
|Polygon.def|Diese Modul Definitionsdatei stellt dem Linker Informationen zu den von der dll benötigten Exporten bereit.|
|Polygon.idl|Die Sprachdatei der Schnittstellen Definition, in der die für die Objekte spezifischen Schnittstellen beschrieben werden.|
|Polygon.rgs|Dieses Registrierungs Skript enthält Informationen zum Registrieren der Programm-dll.|
|Polygon.rc|Die Ressourcen Datei, die anfänglich die Versionsinformationen und eine Zeichenfolge enthält, die den Projektnamen enthält.|
|Resource.h|Die Headerdatei für die Ressourcendatei|
|Polygonps.def|Diese Modul Definitionsdatei bietet dem Linker Informationen zu den Exporten, die für den Proxy und Stubcode erforderlich sind, die Aufrufe über mehrere Apartments hinweg unterstützen.|
|stdafx.cpp|Die Datei, die *stdafx. h*`#include`.|
|stdafx.h|Die Datei, die die ATL-Header Dateien `#include` und vorkompiliert.|

::: moniker-end

::: moniker range=">=vs-2019"

|Datei|BESCHREIBUNG|
|----------|-----------------|
|Polygon.cpp|Enthält die Implementierung von `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`und `DllUnregisterServer`. Enthält auch die Objekt Zuordnung, bei der es sich um eine Liste der ATL-Objekte in Ihrem Projekt handelt. Diese ist anfänglich leer.|
|Polygon.def|Diese Modul Definitionsdatei stellt dem Linker Informationen zu den von der dll benötigten Exporten bereit.|
|Polygon.idl|Die Sprachdatei der Schnittstellen Definition, in der die für die Objekte spezifischen Schnittstellen beschrieben werden.|
|Polygon.rgs|Dieses Registrierungs Skript enthält Informationen zum Registrieren der Programm-dll.|
|Polygon.rc|Die Ressourcen Datei, die anfänglich die Versionsinformationen und eine Zeichenfolge enthält, die den Projektnamen enthält.|
|Resource.h|Die Headerdatei für die Ressourcendatei|
|Polygonps.def|Diese Modul Definitionsdatei bietet dem Linker Informationen zu den Exporten, die für den Proxy und Stubcode erforderlich sind, die Aufrufe über mehrere Apartments hinweg unterstützen.|
|PCH. cpp|Die Datei, die " *PCH. h*" `#include`.|
|PCH. h|Die Datei, die die ATL-Header Dateien `#include` und vorkompiliert.|

::: moniker-end

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt `Polygon`.

1. Klicken Sie im Kontextmenü auf **Eigenschaften**.

1. Klicken Sie auf **Linker**. Ändern Sie die Option **pro Benutzer Umleitung** in **Ja**.

1. Klicken Sie auf **OK**.

Im nächsten Schritt fügen Sie dem Projekt ein-Steuerelement hinzu.

[In Schritt 2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>Weitere Informationen

[Tutorial](../atl/active-template-library-atl-tutorial.md)
