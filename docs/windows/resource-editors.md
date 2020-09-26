---
title: Ressourcen-Editoren (C++)
ms.date: 02/14/2019
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: 2552f9eea79aa0a3545d9746d85cacfbd9a3f25d
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353167"
---
# <a name="resource-editors-c"></a>Ressourcen-Editoren (C++)

Ein Ressourcen-Editor ist eine spezialisierte Umgebung zum Erstellen oder Ändern von Ressourcen, die in einem Visual Studio-Projekt enthalten sind. Die Ressourcen-Editoren von Visual Studio teilen Techniken und Schnittstellen, die Sie beim schnellen und einfachen Erstellen und Ändern von Anwendungsressourcen unterstützen. Mithilfe von Ressourcen-Editoren können Sie Ressourcen im entsprechenden Editor anzeigen und bearbeiten sowie Ressourcen in der Vorschau anzeigen.

Wenn Sie eine Ressource erstellen oder öffnen, wird automatisch der entsprechende Editor geöffnet.

> [!NOTE]
> Da verwaltete Projekte keine Ressourcen Skriptdateien verwenden, müssen Sie Ihre Ressourcen aus **Projektmappen-Explorer**öffnen. Sie können die [Bild](../windows/image-editor-for-icons.md) Bearbeitung und den [Binär-Editor](binary-editor.md) verwenden, um mit Ressourcen Dateien in verwalteten Projekten zu arbeiten. Bei den zu bearbeitenden verwalteten Ressourcen muss es sich um verknüpfte Ressourcen handeln. Das Bearbeiten eingebetteter Ressourcen wird von den Visual Studio-Ressourcen-Editoren nicht unterstützt.

|Verwenden Sie...|Zur Bearbeitung von...|
|----------------|----------------|
|[Zugriffstasten-Editor](../windows/accelerator-editor.md)|Zugriffstasten Tabellen in Visual Studio C++-Projekten.|
|[Binär-Editor](binary-editor.md)|Binäre Daten und benutzerdefinierte Ressourcen in Visual C++-, Visual Basic- oder Visual C#-Projekten.|
|[Dialog-Editor](../windows/dialog-editor.md)|Dialog Felder in Visual Studio C++-Projekten.|
|[Bild-Editor](../windows/image-editor-for-icons.md)|Bitmaps, Symbole, Cursor und andere Bilddateien in Visual C++-, Visual Basic- oder Visual C#-Projekten.|
|[Menü-Editor](../windows/menu-editor.md)|Menü Ressourcen in Visual Studio C++-Projekten.|
|[Ribbon-Editor](../mfc/ribbon-designer-mfc.md)|Menübandressourcen in MFC-Projekten.|
|[Zeichen folgen-Editor](../windows/string-editor.md)|Zeichen folgen Tabellen in Visual Studio C++-Projekten.|
|[Symbolleisten-Editor](../windows/toolbar-editor.md)|Symbolleisten Ressourcen in Visual Studio C++-Projekten. Der **Symbol** leisten-Editor ist Teil des **Bild-Editors**.|
|[Versions Informations-Editor](../windows/version-information-editor.md)|Versionsinformationen in Visual Studio C++-Projekten.|

> [!NOTE]
> Wenn das Projekt noch keine RC-Datei enthält, finden Sie weitere Informationen unter Gewusst [wie: Erstellen von Ressourcen](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Anzeigen und Bearbeiten von Ressourcen

Für jeden Ressourcentyp ist ein Ressourcen-Editor für diesen Ressourcentyp spezifisch. Mithilfe des zugeordneten Editors können Sie die Elemente einer Ressource neu anordnen, ändern, hinzufügen oder ändern. Sie können eine Ressource auch im Textformat und im Binärformat bearbeiten. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Ressourcen](../windows/how-to-create-a-resource-script-file.md).

Einige Ressourcentypen sind einzelne Dateien, die importiert und auf verschiedene Arten verwendet werden können. Dazu zählen Bitmaps, Symbole, Cursor, Symbolleisten und HTML-Dateien. Diese Ressourcen verfügen über Dateinamen und [Ressourcen](../windows/symbols-resource-identifiers.md)Bezeichner. Andere, z. b. Dialogfelder, Menüs und Zeichen folgen Tabellen in Win32-Projekten, sind nur als Teil einer Ressourcen Skriptdatei (. RC) oder einer Ressourcen Vorlagen Datei (. rct) vorhanden.

Ressourcen können auch außerhalb des Projekts bearbeitet werden, ohne dass das Projekt geöffnet ist. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Ressourcen](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Die Eigenschaften einer Ressource können mithilfe des Fensters **Eigenschaften** geändert werden.

- Um die Eigenschaften einer Ressource zu bearbeiten, klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf die Ressource, die Sie bearbeiten möchten, und wählen Sie **Eigenschaften**aus.  Ändern Sie dann im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)die Eigenschaften der Ressource.

- Um eine Änderung an den Eigenschaften einer Ressource rückgängig zu machen, stellen Sie sicher, dass Ihre Ressource den Fokus auf **Ressourcenansicht** hat, und wählen Sie im Menü **Bearbeiten** die Option **Rückgängig** aus.

### <a name="win32-resources"></a>Win32-Ressourcen

Sie können im [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources) Bereich auf Win32-Ressourcen zugreifen.

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>So zeigen Sie eine Win32-Ressource in einem Ressourcen-Editor an

1. Wechseln Sie zum Menü **anzeigen**  >  **anderer Windows**-  >  **Ressourcenansicht**.

1. Wenn das **Ressourcenansicht** Fenster nicht das oberste Fenster ist, wählen Sie die Registerkarte **Ressourcenansicht** aus, um Sie oben zu verschieben.

1. Erweitern Sie in **Ressourcenansicht**den Ordner für das Projekt, das die Ressourcen enthält, die Sie anzeigen möchten. Wenn Sie z. b. eine Dialogfeld Ressource anzeigen möchten, erweitern Sie den **Dialog** Ordner.

1. Doppelklicken Sie auf die Ressource, z. b. **IDD_ABOUTBOX**.

   Die Ressource wird im geeigneten Editor geöffnet. Beispielsweise wird für Dialog Ressourcen die Ressource im **Dialog-Editor**geöffnet.

#### <a name="to-delete-an-existing-win32-resource"></a>So löschen Sie eine vorhandene Win32-Ressource

1. Erweitern Sie in **Ressourcenansicht**den Knoten für einen Ressourcentyp.

1. Klicken Sie mit der rechten Maustaste auf die Ressource, die Sie löschen möchten, und wählen Sie **Löschen**.

> [!TIP]
> Sie können diese Methode auch verwenden, wenn die RC-Datei in einem Dokument Fenster außerhalb eines Projekts geöffnet ist.

### <a name="managed-project-resources"></a>Verwaltete Projektressourcen

Da verwaltete Projekte keine Ressourcen Skriptdateien verwenden, müssen Sie Ihre Ressourcen aus **Projektmappen-Explorer**öffnen. Verwenden Sie die [Bild](../windows/image-editor-for-icons.md) Bearbeitung und den [Binär-Editor](binary-editor.md) , um mit Ressourcen Dateien in verwalteten Projekten zu arbeiten. Verwaltete Ressourcen, die Sie bearbeiten möchten, müssen verknüpfte Ressourcen sein, und Visual Studio-Ressourcen-Editoren unterstützen die Bearbeitung von eingebetteten Ressourcen nicht

- Um eine verwaltete Ressource in einem Ressourcen-Editor anzuzeigen, doppelklicken Sie in **Projektmappen-Explorer**auf die Ressource, z. b. *Bitmap1.bmp*, und die Ressource wird im entsprechenden Editor geöffnet.

- Zum Löschen einer vorhandenen verwalteten Ressource klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Ressource, die Sie löschen möchten, und wählen Sie **Löschen**aus.

## <a name="preview-resources"></a>Vorschau der Ressourcen

Zeigen Sie eine Vorschau Ihrer Ressourcen an, damit Sie eine grafische Ressource anzeigen können, ohne Sie zu öffnen Die Vorschau ist auch für ausführbare Dateien nützlich, nachdem Sie sie kompiliert haben, da die Ressourcen Bezeichner in Zahlen geändert werden. Da diese numerischen Bezeichner häufig nicht genügend Informationen bereitstellen, hilft Ihnen die Vorschau der Ressourcen, Sie schnell zu identifizieren.

Die folgenden Ressourcentypen bieten eine Vorschau des visuellen Layouts: Bitmap, Dialog Feld, Symbol, Menü, Cursor, Symbolleiste.

Die folgenden Ressourcen bieten keine visuelle Vorschau: Accelerator, Manifest, Zeichen folgen Tabelle, Versionsinformationen

> [!NOTE]
> Zum Anzeigen einer Vorschau von Ressourcen ist Win32 erforderlich.

### <a name="to-preview-resources"></a>So übermitteln Sie Ressourcen

1. Wählen Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources) oder einem Dokument Fenster Ihre Ressource aus, z. b. **IDD_ABOUTBOX**.

1. Wählen Sie im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)die Schaltfläche **Eigenschaften Seiten** aus.

   > [!TIP]
   > Verwenden Sie eine Verknüpfung, wechseln Sie zu Menü **Anzeige**  >  **Eigenschaften Seiten**.

   Die **Eigenschaften** Seite für die Ressource wird geöffnet und zeigt eine Vorschau der Ressource an. Mithilfe der nach- **oben** -und **nach-unten** -Taste können Sie im Struktur Steuerelement in **Ressourcenansicht** oder im Dokument Fenster navigieren. Die **Eigenschaften** Seite wird geöffnet und zeigt alle Ressourcen an, die sich im Fokus befinden und in der Vorschau angezeigt werden können.

## <a name="requirements"></a>Requirements (Anforderungen)

Keine

## <a name="see-also"></a>Weitere Informationen

[Working with Resource Files (Arbeiten mit Ressourcendateien)](../windows/working-with-resource-files.md)<br/>
[Ressourcen Dateien](../windows/resource-files-visual-studio.md)<br/>
[Ressourcen Bezeichner (Symbole)](../windows/symbols-resource-identifiers.md)<br/>
