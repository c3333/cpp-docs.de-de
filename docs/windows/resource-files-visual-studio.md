---
title: Ressourcendateien (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: 463c27959b049436e29f872c966bc276c6ef5f2d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507014"
---
# <a name="resource-files-c"></a>Ressourcendateien (C++)

> [!NOTE]
> Da Projekte in .NET-Programmiersprachen keine Ressourcenskriptdateien verwenden, müssen Sie Ihre Ressourcen im **Projektmappen-Explorer**. Verwenden Sie die [Bild](../windows/image-editor-for-icons.md) Bearbeitung und den [Binär-Editor](binary-editor.md) , um mit Ressourcen Dateien in verwalteten Projekten zu arbeiten.
>
> Bei den zu bearbeitenden verwalteten Ressourcen muss es sich um verknüpfte Ressourcen handeln. Das Bearbeiten eingebetteter Ressourcen wird von den Visual Studio-Ressourcen-Editoren nicht unterstützt.

Der Begriff " *Ressourcen Datei* " kann auf eine Reihe von Dateitypen verweisen, wie z. b.:

- Die Ressourcenskriptdatei (RC) eines Programms.

- Eine Ressourcenvorlagendatei (RCT).

- Eine einzelne Ressource, die als eigenständige Datei vorhanden ist. Dieser Typ enthält eine Bitmap, ein Symbol oder eine Cursor Datei, auf die von einer RC-Datei verwiesen wird.

- Eine von der Entwicklungsumgebung generierte Header Datei. Dieser Typ enthält `Resource.h` , auf den von einer RC-Datei verwiesen wird.

Ressourcen, die in anderen Dateitypen, z. b. exe-, dll-und res-Dateien, gefunden werden, werden als *Ressourcen*bezeichnet.

Sie können in Ihrem Projekt mit *Ressourcen Dateien* und *Ressourcen* arbeiten. Sie können auch mit solchen arbeiten, die nicht Teil des aktuellen Projekts sind oder außerhalb der Entwicklungsumgebung von Visual Studio erstellt wurden. Beispielsweise können Sie folgende Aktionen ausführen:

- Arbeiten mit geschachtelten und bedingt eingeschlossenen Ressourcendateien.

- Aktualisieren Sie vorhandene Ressourcen, oder konvertieren Sie Sie in Visual C++.

- Importieren oder Exportieren grafischer Ressourcendateien in die oder aus der aktuelle(n) Ressourcendatei.

- Einschließen gemeinsam verwendeter oder schreibgeschützter Bezeichner (Symbole), die von der Entwicklungsumgebung nicht geändert werden können.

- Einschließen von Ressourcen in die ausführbare Datei (. exe), die nicht bearbeitet werden müssen (oder nicht bearbeitet werden sollten), z. b. freigegebene Ressourcen zwischen mehreren Projekten.

- Einschließen von Ressourcentypen, die von der Entwicklungsumgebung nicht unterstützt werden.

Weitere Informationen zu Ressourcen finden Sie unter Erstellen von [Ressourcen](../windows/how-to-create-a-resource-script-file.md), [Verwalten](../windows/how-to-copy-resources.md)von Ressourcen und [einschließen von Ressourcen zur Kompilierzeit](../windows/how-to-include-resources-at-compile-time.md).

## <a name="editable-resources"></a>Bearbeitbare Ressourcen

Die folgenden Dateitypen können geöffnet werden, um die darin enthaltenen Ressourcen zu bearbeiten:

| Dateiname | BESCHREIBUNG |
|---|---|
| .rc | Ressourcen Skriptdateien |
| .rct | Ressourcen Vorlagen Dateien |
| .res | Ressourcendateien |
| RESX-Datei | Verwaltete Ressourcen Dateien |
| .exe | Ausführbare Dateien |
| .dll | Dynamic Link Library-Dateien |
| . BMP,. ico,. DIB,. cur | Bitmap-, Symbol-, Symbolleisten-und Cursor Dateien |

Beim Bearbeiten von Ressourcen arbeitet die Visual Studio-Umgebung mit und wirkt sich auf die folgenden Dateien aus:

| Dateiname | BESCHREIBUNG |
|---|---|
| Resource.h | Die von der Entwicklungsumgebung generierte Header Datei, die Symbol Definitionen enthält.<br/><br/>Fügen Sie diese Datei in die Quell Code Verwaltung ein. |
| Filename.aps | Binäre Version der aktuellen Ressourcen Skriptdatei, die für das schnelle Laden verwendet wird.<br /><br /> Ressourcen-Editoren lesen RC-oder Resource. h-Dateien nicht direkt. Der Ressourcen Compiler kompiliert Sie in. APS-Dateien, die von den Ressourcen-Editoren verwendet werden. Diese Datei ist ein Kompilierungsschritt und speichert nur symbolische Daten.<br/><br/>Wie bei einem normalen Kompilierungsprozess werden nicht symbolische Informationen, wie z. b. Kommentare, während des Kompilierungs Vorgangs verworfen.<br/><br/>Wenn die. APS-Datei nicht mit der RC-Datei synchronisiert ist, wird die RC-Datei neu generiert. Wenn Sie z. b. **Speichern**, überschreibt der Ressourcen-Editor die RC-Datei und die Datei "Resource. h". Alle Änderungen an den Ressourcen selbst bleiben in der RC-Datei enthalten, Kommentare werden jedoch immer verloren gehen, sobald die RC-Datei überschrieben wird. Weitere Informationen zum Beibehalten von Kommentaren finden Sie [unter Einschließen von Ressourcen zur Kompilierzeit](../windows/how-to-include-resources-at-compile-time.md).<br/><br/>In der Regel sollten Sie die. APS-Datei nicht in die Quell Code Verwaltung einschließen. |
| .rc | Ressourcenskriptdatei, die Skript für die Ressourcen im aktuellen Projekt enthält. Diese Datei wird bei jedem Speichern durch die .aps-Datei überschrieben.<br/><br/>Fügen Sie diese Datei in die Quell Code Verwaltung ein. |

## <a name="manifest-resources"></a>Manifestressourcen

In C++-Desktop Projekten sind Manifest-Ressourcen XML-Dateien, die die von einer Anwendung verwendeten Abhängigkeiten beschreiben. In Visual Studio wird von dieser vom MFC-Assistenten generierten Manifest-Datei z. b. definiert, welche Version der allgemeinen Windows-Steuerelement-DLLs von der Anwendung verwendet werden soll:

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

Für eine Windows XP-oder Windows Vista-Anwendung sollte die Manifestressource die aktuellste Version der allgemeinen Windows-Steuerelemente angeben, die von der Anwendung verwendet werden soll. Im obigen Beispiel wird die-Version verwendet `6.0.0.0` , die das [Syslink-Steuer](/windows/win32/Controls/syslink-overview)Element unterstützt.

> [!NOTE]
> Es kann nur eine Manifestressource pro Modul verwendet werden.

Um die in einer Manifestressource enthaltenen Versions-und Typinformationen anzuzeigen, öffnen Sie die Datei in einem XML-Viewer oder im Text-Editor von Visual Studio. Beim Öffnen einer Manifestressource aus [Ressourcenansicht](./how-to-create-a-resource-script-file.md)wird die Ressource im Binärformat geöffnet.

### <a name="to-open-a-manifest-resource"></a>So öffnen Sie eine Manifestressource

1. Öffnen Sie das Projekt in Visual Studio, und navigieren Sie zu **Projektmappen-Explorer**.

1. Erweitern Sie den Ordner **Ressourcen Dateien** , und klicken Sie dann:

   - Um im Text-Editor zu öffnen, doppelklicken Sie auf die *Manifest* -Datei.

   - Klicken Sie zum Öffnen in einem anderen Editor mit der rechten Maustaste auf die *Manifest* -Datei, und wählen Sie **Öffnen mit**aus. Geben Sie den zu verwendenden Editor an, und wählen Sie **Öffnen**.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Working with Resource Files (Arbeiten mit Ressourcendateien)](../windows/working-with-resource-files.md)<br/>
[Ressourcen Bezeichner (Symbole)](../windows/symbols-resource-identifiers.md)<br/>
[Ressourcen-Editoren](../windows/resource-editors.md)<br/>
