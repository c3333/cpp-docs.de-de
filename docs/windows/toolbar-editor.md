---
title: Symbolleisten-Editor (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.toolbar.F1
- vc.editors.toolbar
- vc.editors.newtoolbarresource
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
- tool tips [C++], adding to toolbar buttons
- "\n in tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: ca7f031cbdcfc3378a0917e84b257fd7212563e1
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353024"
---
# <a name="toolbar-editor-c"></a>Symbolleisten-Editor (C++)

Mit dem Symbolleisten- **Editor** können Sie Symbolleisten Ressourcen erstellen und Bitmaps in Symbolleisten Ressourcen konvertieren. Der **Symbol** leisten-Editor verwendet eine grafische Anzeige, um eine Symbolleiste und Schaltflächen anzuzeigen, die der Darstellung in einer fertiggestellten Anwendung sehr ähnlich sind.

Das Fenster des Symbolleisten- **Editors** zeigt zwei Ansichten eines Schaltflächen Bilds an, identisch mit dem **Bild-Editor** -Fenster. In einem geteilten Balken werden die beiden Bereiche getrennt, und Sie können den Trennbalken von Seite zu Seite ziehen, um die relativen Größen der Bereiche zu ändern. Im aktiven Bereich wird ein Auswahl Rahmen angezeigt, und oberhalb der beiden Ansichten des Bilds befindet sich die Symbolleiste des Antragstellers.

![Symbolleisten-Editor](../mfc/media/vctoolbareditor.gif "vctoolbareditor")<br/>
**Symbolleisten-Editor**

Der **Symbol** leisten-Editor ähnelt dem **Bild-Editor** in der Funktionalität, und die Menü Elemente, die Grafiktools und das Bitmap-Raster zwischen den beiden sind identisch. Im Menü " **Bild** " gibt es einen Menübefehl, mit dem Sie zwischen dem Symbolleisten- **Editor** und dem **Bild-Editor**wechseln können. Weitere Informationen zur Verwendung der **Grafik** Symbolleiste, der **Farb** Palette oder des **bildmenüs** finden Sie unter [Bild](../windows/image-editor-for-icons.md)Bearbeitung.

Sie können eine neue Symbolleiste in einem C++-Projekt erstellen, indem Sie eine Bitmap umrechnen. Die Grafik aus der Bitmap wird in die Schaltflächen Bilder für eine Symbolleiste konvertiert. In der Regel enthält die Bitmap mehrere Schaltflächen Bilder auf einer einzelnen Bitmap, wobei für jede Schaltfläche ein Bild angezeigt wird. Bilder können eine beliebige Größe aufweisen, da der Standardwert 16 Pixel breit und die Höhe des Bilds ist. Sie können die Größe der Schaltflächen Bilder im Dialogfeld **neue Symbolleisten Ressource** angeben, wenn Sie im Bild- **Editor**im Menü **Bild** den Befehl **Symbolleiste** auswählen.

Im Dialogfeld **neue Symbolleisten Ressource** können Sie die Breite und die Höhe der Schaltflächen angeben, die einer Symbolleisten Ressource in einem C++-Projekt hinzugefügt werden. Der Standardwert ist 16 × 15 Pixel.

Eine Bitmap, die zum Erstellen einer Symbolleiste verwendet wird, hat eine maximale Breite von 2048. Wenn Sie also die **Schaltflächen breite** auf *512*festlegen, können Sie nur vier Schaltflächen verwenden. Wenn Sie die Breite auf *513*festlegen, können nur drei Schaltflächen vorhanden sein.

Das Dialogfeld **neue Symbolleisten Ressource** verfügt über die folgenden Eigenschaften:

|Eigenschaft|BESCHREIBUNG|
|---|---------------|
|**Schaltflächen breite**|Hier können Sie die Breite der Symbolleisten Schaltflächen, die Sie von einer Bitmap-Ressource in eine Symbolleisten Ressource wandeln, eingeben.|
|**Schaltflächen Höhe**|Hier können Sie die Höhe der Symbolleisten Schaltflächen, die Sie von einer Bitmap-Ressource in eine Symbolleisten Ressource wandeln, eingeben.|

> [!NOTE]
> Die Bilder werden auf die angegebene Breite und Höhe zugeschnitten, und die Farben werden so angepasst, dass Standard Symbolleisten Farben (16 Farben) verwendet werden.

Standardmäßig wird eine neue Schaltfläche oder eine leere Schaltfläche am rechten Ende der Symbolleiste angezeigt. Sie können diese Schaltfläche verschieben, bevor Sie Sie bearbeiten. Wenn Sie eine neue Schaltfläche erstellen, wird rechts neben der bearbeiteten Schaltfläche eine weitere leere Schaltfläche angezeigt. Wenn Sie eine Symbolleiste speichern, wird die leere Schaltfläche nicht gespeichert.

Eine Symbolleisten-Schaltfläche verfügt über die folgenden Eigenschaften:

|Eigenschaft|BESCHREIBUNG|
|--------------|-----------------|
|**ID**|Definiert die ID für die Schaltfläche. Die Dropdown Liste enthält allgemeine **ID** -Namen.|
|**Width**|Legt die Breite der Schaltfläche fest. Es werden 16 Pixel empfohlen.|
|**Height**|Legt die Höhe der Schaltfläche fest. Durch die Höhe einer Schaltfläche wird die Höhe aller Schaltflächen auf der Symbolleiste geändert. Es wird 15 Pixel empfohlen.|
|**Eingabeaufforderung**|Definiert die in der Statusleiste angezeigte Meldung. Durch das hinzu **fügen von** *\n* und eines Namens wird der Symbolleisten Schaltfläche eine QuickInfo Weitere Informationen finden [Sie unter So erstellen Sie eine QuickInfo für eine Symbolleisten Schaltfläche](#to-create-a-tool-tip-for-a-toolbar-button).|

**Breite** und **Höhe** gelten für alle Schaltflächen. Eine Bitmap, die zum Erstellen einer Symbolleiste verwendet wird, hat eine maximale Breite von 2048. Wenn Sie also die Schaltflächen breite auf *512*festlegen, können Sie nur vier Schaltflächen haben. Wenn Sie die Breite auf *513*festlegen, können Sie nur drei Schaltflächen verwenden.

## <a name="how-to"></a>Vorgehensweise

Der **Symbol** leisten-Editor ermöglicht Ihnen Folgendes:

### <a name="to-create-new-toolbars"></a>So erstellen Sie neue Symbolleisten

1. Klicken Sie in **Ressourcenansicht**mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie **Ressource hinzufügen**aus. Wenn Sie über eine vorhandene Symbolleiste in der *RC* -Datei verfügen, können Sie mit der rechten Maustaste auf den **Symbol** leisten Ordner klicken und **Symbolleiste einfügen**auswählen.

1. Wählen Sie im Dialogfeld **Ressource hinzufügen** in der Liste **Ressourcentyp** die Option **Symbolleiste** aus, und wählen Sie dann **neu**aus.

   Wenn ein Pluszeichen ( **+** ) neben dem Ressourcentyp der **Symbolleiste** angezeigt wird, bedeutet dies, dass Toolbar-Vorlagen verfügbar sind. Wählen Sie das Pluszeichen aus, um die Liste der Vorlagen zu erweitern, wählen Sie eine Vorlage aus, und wählen Sie **neu**aus.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>So konvertieren Sie Bitmaps in Symbolleisten Ressourcen

1. Öffnen Sie eine vorhandene Bitmap-Ressource im [Bild-Editor](../windows/image-editor-for-icons.md). Wenn die Bitmap nicht bereits in der *RC* -Datei vorhanden ist, klicken Sie mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie **importieren**aus. Navigieren Sie dann zu der Bitmap, die Sie der *RC* -Datei hinzufügen möchten, und wählen Sie **Öffnen**

1. Wechseln Sie zum Menü **Bild**  >  **Symbol**leisten-Editor.

   Das Dialogfeld **neue Symbolleisten Ressource** wird angezeigt. Sie können die Breite und Höhe der Symbolbilder entsprechend der Bitmap ändern. Das Symbolleisten Bild wird dann im Symbolleisten- **Editor**angezeigt.

1. Um die Konvertierung abzuschließen, ändern Sie die Befehls- **ID** der Schaltfläche mithilfe der [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window). Geben Sie die neue *ID* ein, oder wählen Sie eine **ID** aus der Dropdown Liste aus.

   > [!TIP]
   > Das **Eigenschaften** Fenster enthält eine PushPin-Schaltfläche in der Titelleiste. Wenn Sie diese Option aktivieren, wird die **automatisch im Hintergrund** für das Fenster aktiviert oder deaktiviert. Wenn Sie alle Eigenschaften der Symbolleisten-Schaltfläche durchlaufen möchten, ohne die einzelnen Eigenschaften Fenster erneut öffnen zu müssen, deaktivieren Sie **automatisch im Hintergrund** , damit das **Eigenschaften** Fenster stationär bleibt.

   Mithilfe der [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)können Sie auch die Befehls-IDs der Schaltflächen auf der neuen Symbolleiste ändern.

### <a name="to-manage-toolbar-buttons"></a>Verwalten von Symbolleisten-Schaltflächen

#### <a name="to-create-a-new-toolbar-button"></a>So erstellen Sie eine neue Symbolleisten-Schaltfläche

1. Erweitern Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources) den Ressourcen Ordner (z *. b. Projekt1. RC*).

1. Erweitern Sie den **Symbol** leisten Ordner, und wählen Sie eine Symbolleiste zum Bearbeiten aus. führen Sie dann einen der folgenden Schritte aus

   - Weisen Sie der leeren Schaltfläche am rechten Ende der Symbolleiste eine ID zu. Hierzu können Sie die **ID** -Eigenschaft im [Eigenschaften Fenster](/visualstudio/ide/reference/properties-window)bearbeiten. Beispielsweise können Sie einer Symbolleisten-Schaltfläche die gleiche ID wie eine Menüoption geben. Verwenden Sie in diesem Fall das Dropdown-Listenfeld, um die **ID** der Menüoption auszuwählen.

   - Wählen Sie im Bereich **Symbolleisten Ansicht** am rechten Ende der Symbolleiste die Schaltfläche leer aus, und beginnen Sie mit dem zeichnen. Eine Standard Schaltflächen-Befehls-ID wird zugewiesen (ID_BUTTON \<n> ).

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>So fügen Sie einer Symbolleiste ein Bild als Schaltfläche hinzu

1. Öffnen Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)die Symbolleiste, indem Sie darauf doppelklicken.

1. Öffnen Sie als nächstes das Image, das Sie der Symbolleiste hinzufügen möchten.

   > [!NOTE]
   > Wenn Sie das Bild in Visual Studio öffnen, wird es im Bild- **Editor**geöffnet. Sie können das Bild auch in anderen Grafikprogrammen öffnen.

1. Wechseln Sie zum **Menü "**  >  **Kopieren**".

1. Wechseln Sie zu Ihrer Symbolleiste, indem Sie die zugehörige Registerkarte am oberen Rand des Quell Fensters auswählen.

1. Wechseln Sie zum **Menü "**  >  **Einfügen**".

   Das Bild wird auf der Symbolleiste als neue Schaltfläche angezeigt.

#### <a name="to-move-a-toolbar-button"></a>Verschieben einer Symbolleisten-Schaltfläche

Ziehen Sie im Bereich der **Symbolleisten Ansicht** die Schaltfläche, die Sie verschieben möchten, an die neue Position auf der Symbolleiste.

- Wenn Sie Schaltflächen von einer Symbolleiste kopieren möchten, halten Sie die **STRG** -Taste gedrückt, und ziehen Sie die Schaltfläche im Bereich der **Symbolleisten Ansicht** entweder an die neue Position auf der Symbolleiste oder an eine Position auf einer anderen Symbolleiste.

- Zum Löschen einer Symbolleisten-Schaltfläche Wählen Sie die Symbolleisten Schaltfläche aus und ziehen Sie aus der Symbolleiste

- Um Leerzeichen zwischen Schaltflächen auf einer Symbolleiste einzufügen oder zu entfernen, ziehen Sie Sie entweder auf der Symbolleiste von oder auf eine andere.

|Aktion|Schritt|
|------|------|
|So fügen Sie ein Leerzeichen vor einer Schaltfläche ein, auf die kein Leerzeichen folgt|Ziehen Sie die Schaltfläche nach rechts oder nach unten, bis die Schaltfläche weiter ungefähr in der Mitte überlappt.|
|So fügen Sie ein Leerzeichen vor einer Schaltfläche ein, auf die ein Leerzeichen folgt und den nachfolgenden Bereich beibehalten|Ziehen Sie die Schaltfläche, bis der Rechte oder untere Rand nur die Schaltfläche "weiter" berührt oder nur überlappt.|
|So fügen Sie ein Leerzeichen vor einer Schaltfläche ein, der ein Leerzeichen folgt, und schließen Sie den folgenden Bereich|Ziehen Sie die Schaltfläche nach rechts oder nach unten, bis die Schaltfläche weiter ungefähr in der Mitte überlappt.|
|So entfernen Sie ein Leerzeichen zwischen Schaltflächen auf einer Symbolleiste|Ziehen Sie die Schaltfläche auf der einen Seite des Leerraums in Richtung der Schaltfläche auf der anderen Seite des Leerraums, bis die Schaltfläche "weiter" überschneidet.|

> [!NOTE]
> Wenn Sie auf der Seite der Schaltfläche, die Sie ziehen, nicht auf die Schaltfläche klicken, und Sie die Schaltfläche mehr als die Hälfte nach der angrenzenden Schaltfläche ziehen, fügt der Symbolleisten- **Editor** ein Leerzeichen auf der gegenüberliegenden Seite der Schaltfläche ein, die Sie ziehen.

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>So ändern Sie die Eigenschaften einer Symbolleisten-Schaltfläche

1. Wählen Sie in einem C++-Projekt die Symbolleisten Schaltfläche aus.

1. Geben Sie im [Eigenschaften Fenster](/visualstudio/ide/reference/properties-window)die neue ID in der **ID** -Eigenschaft ein, oder wählen Sie in der Dropdown Liste eine neue **ID**aus.

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>So erstellen Sie eine QuickInfo für eine Symbolleisten-Schaltfläche

1. Wählen Sie die Symbolleisten Schaltfläche

1. Fügen Sie im [Fenster Eigenschaften](/visualstudio/ide/reference/properties-window)im Feld **Eingabeaufforderung** eine Beschreibung der Schaltfläche für die Statusleiste und nach der Meldung hinzufügen `\n` und den QuickInfo-Namen hinzu.

Um z. b. die QuickInfo für die Schaltfläche " **Drucken** " in **WordPad**anzuzeigen:

1. Öffnen Sie **WordPad**.

1. Zeigen Sie mit dem Mauszeiger auf die **Druck** Symbolleisten-Schaltfläche, und beachten Sie, dass das Wort `Print` jetzt unter dem Mauszeiger ist.

1. Sehen Sie sich die Statusleiste am unteren Rand des **WordPad** -Fensters an, und beachten Sie, dass der Text jetzt angezeigt wird `Prints the active document` .

`Print` ist der QuickInfo-Name und `Prints the active document` die Beschreibung der Schaltfläche für die Statusleiste.

Wenn Sie diesen Effekt mithilfe des Symbolleisten- **Editors**wünschen, legen Sie die Eigenschaft **prompt** auf fest `Prints the active document\nPrint` .

## <a name="requirements"></a>Requirements (Anforderungen)

MFC oder ATL

## <a name="see-also"></a>Weitere Informationen

[Ressourcen-Editoren](../windows/resource-editors.md) 
 [Menüs und weitere Ressourcen](/windows/win32/menurc/resources)<br/>
[Eigenschaften von Symbolleisten-Schaltflächen](../windows/toolbar-button-properties.md)<br/>
