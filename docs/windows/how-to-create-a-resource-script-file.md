---
title: 'Vorgehensweise: Erstellen von RessourcenC++()'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
- language-specific template files [C++]
- resource templates
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: c997c7a1b2d7fb3a852a42fa78faf2be6074705e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866120"
---
# <a name="how-to-create-resources-c"></a>Vorgehensweise: Erstellen von RessourcenC++()

Sie können Ressourcen für Ihr Projekt erstellen, indem Sie folgende Schritte ausführen:

- Verwenden einer Ressourcen Skriptdatei.

   > [!NOTE]
   > Dieser Schritt ist erforderlich, bevor Sie Ressourcen hinzufügen.

- Hinzufügen von Ressourcen zu Ihrem Projekt und Verwenden der **Ressourcenansicht**.

- Verwenden einer Ressourcen Vorlage zum Erstellen von angepassten Ressourcen.

## <a name="use-resource-script-files"></a>Verwenden von Ressourcen Skriptdateien

Bevor Sie neue Ressourcen erstellen und zu Ihrem Projekt hinzufügen, müssen Sie zunächst eine Ressourcen Skriptdatei (. RC) erstellen.

> [!NOTE]
> Sie können einem vorhandenen Projekt, das in die Visual Studio-IDE geladen wurde, nur eine Ressourcen Skriptdatei hinzufügen. Sie können kein eigenständiges Ressourcen Skript außerhalb des Projekts erstellen, obwohl Ressourcen Vorlagen Dateien (. rct) jederzeit erstellt werden können.

### <a name="to-create-a-resource-script-file"></a>So erstellen Sie eine Ressourcen Skriptdatei

1. Legen Sie den Fokus auf den vorhandenen Projektordner in **Projektmappen-Explorer**, z. b. " *MyProject*".

   > [!NOTE]
   > Verwechseln Sie den Projektordner nicht mit dem Projektmappenordner in **Projektmappen-Explorer**. Wenn Sie den Fokus auf den **Projektmappenordner** legen, haben Sie nicht die gleichen Optionen für **Neues Element hinzufügen** .

1. Wechseln Sie im Menü zu **Projekt** > **Neues Element hinzufügen**.

1. Wählen Sie **den C++ visuellen** Ordner aus, und wählen Sie im rechten Bereich **Ressourcen Datei (. RC)** aus.

1. Geben Sie im Textfeld **Name** einen Namen für die Ressourcen Skriptdatei ein, und wählen Sie **Öffnen**aus.

### <a name="to-open-a-resource-script-file"></a>So öffnen Sie eine Ressourcen Skriptdatei

Sie können Ressourcen in einer Ressourcen Skriptdatei anzeigen, ohne dass ein Projekt geöffnet ist. Die Skriptdatei wird im Gegensatz zum **Ressourcenansicht**in einem Dokument Fenster geöffnet.

> [!NOTE]
> Einige Befehle sind nur verfügbar, wenn die Datei eigenständig geöffnet wird. das bedeutet, dass Sie außerhalb eines Projekts, ohne dass das Projekt zuerst geladen wird. Wenn Sie z. b. den Befehl " **Speichern** unter" verwenden und eine Datei mit einem anderen Format oder Dateinamen speichern möchten, muss die Datei eigenständig geöffnet werden.

- Um eine Ressourcen Skriptdatei außerhalb eines Projekts zu öffnen, navigieren Sie im Menü zu **Datei** > **Öffnen**, und wählen Sie dann **Datei**aus. Navigieren Sie zur Ressourcen Skriptdatei, markieren Sie die Datei, und wählen Sie **Öffnen**aus.

    > [!NOTE]
    > Es kann vorkommen, dass Sie den Inhalt der Ressourcen Skriptdatei Ihres Projekts anzeigen möchten, ohne die Ressourcen-Editoren zum Öffnen einer Ressource zu verwenden. Beispielsweise möchten Sie möglicherweise nach einer Zeichenfolge über alle Dialogfelder in der Ressourcendatei hinweg suchen, ohne dass Sie dafür jedes einzeln öffnen müssen. Sie können die Ressourcen Datei problemlos im Textformat öffnen, um alle darin enthaltenen Ressourcen anzuzeigen und globale Vorgänge abzuschließen, die vom Text-Editor unterstützt werden.
    >
    > Zum Öffnen einer Ressourcen Skriptdatei im Textformat verwenden Sie den Dropdown Pfeil auf der rechten Seite der Schaltfläche **Öffnen** im obigen Schritt, und wählen Sie **Öffnen mit**aus. Wählen Sie **Quellcode-Editor (Text)** aus, und wählen Sie in der Dropdown Liste **Öffnen als** die Option **Text** aus, und die Ressource wird im **Quellcode** -Editor geöffnet.

- Zum Öffnen mehrerer Ressourcen Skripts führen Sie den gleichen Schritt wie oben für jede Datei aus, die Sie öffnen möchten, z. b *. Quelle1. RC* und *Source2. RC*. Wenn dann beide RC-Dateien in separaten dokumentenfenstern geöffnet sind, verwenden Sie entweder das Menü **Fenster** , oder klicken Sie mit der rechten Maustaste auf eine der Dateien, und wählen Sie **neue horizontale Registerkarten Gruppe** oder **neue vertikale Registerkarten Gruppe**aus. Die Fenster werden nun gekachelt, sodass Sie Sie gleichzeitig anzeigen können.

> [!TIP]
> Sie können Ressourcen Skriptdateien öffnen, indem Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die RC-Datei klicken, **mit öffnen mit** und **Quellcode-Editor (Text)** auswählen.

Wenn Sie eine MFC-Anwendung (Microsoft Foundation Class) für Windows mit dem [MFC-Anwendungs-Assistenten](../mfc/reference/mfc-application-wizard.md)erstellen, generiert der Assistent einen grundlegenden Satz von Dateien, einschließlich einer Ressourcen Skriptdatei (RC-Datei), die die Kernfunktionen des MFC enthält. Diese MFC-spezifischen Funktionen sind jedoch nicht verfügbar, wenn eine RC-Datei für Windows-Anwendungen bearbeitet wird, die nicht auf MFC basieren. Dies umfasst Code-Assistenten, Menü Aufforderungs Zeichenfolgen, Listen Inhalte für Kombinations Feld-Steuerelemente und Hosting von ActiveX-Steuerelementen.

- Wenn Sie die MFC-Unterstützung mit der Ressourcen Skriptdatei öffnen möchten, markieren Sie in **Ressourcenansicht**den Ressourcen Ordner (z. b. *MFC. RC*). Legen Sie dann im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)den **MFC-Modus** auf " **true**" fest.

  > [!NOTE]
  > Zusätzlich zum Festlegen des **MFC-Modus**muss die RC-Datei Teil eines MFC-Projekts sein. Wenn Sie für eine RC-Datei in einem Win32-Projekt nur den **MFC-Modus** auf " **true** " festlegen, werden Ihnen keine MFC-Funktionen zugewiesen

## <a name="create-resources"></a>Erstellen von Ressourcen

Sie können eine Ressource als neue Standardressource erstellen, d. h. eine Ressource, die nicht auf einer Vorlage basiert, oder als eine Ressource, die nach einer Vorlage erstellt wurde.

Verwenden Sie das Fenster **Ressourcenansicht** , um Ressourcen Dateien anzuzeigen, die in Ihren Projekten enthalten sind. Wenn Sie den obersten Ordner erweitern, z. b *. Projekt1. RC*, werden die Ressourcentypen in dieser Datei angezeigt. Erweitern Sie jeden Ressourcentyp, um die einzelnen Ressourcen dieses Typs anzuzeigen.

> [!TIP]
> Um das Fenster **Ressourcenansicht** zu öffnen, navigieren Sie zur Menü **Ansicht** > **anderen Fenstern** > **Ressourcenansicht** , oder drücken Sie **STRG**+**UMSCHALT**+**E**.

Sie können auch mit der rechten Maustaste auf das **Ressourcenansicht** Fenster klicken, um ein Kontextmenü mit Befehlen zu öffnen, oder Doppelklicken Sie auf die Titelleiste, um das Fenster anzudocken und das Fenster abzudocken. Klicken Sie mit der rechten Maustaste auf die Titelleiste für Befehle, mit denen das Verhalten des Fensters gesteuert wird. Weitere Informationen finden Sie unter [Windows-Verwaltung](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Das **Ressourcenansicht** Fenster umfasst das Dialogfeld **Ressource hinzufügen** mit den folgenden Eigenschaften zum Hinzufügen von C++ Ressourcen zu einem Windows-Desktop Anwendungsprojekt:

| Eigenschaft | BESCHREIBUNG |
|---|---|
| **Ressourcentyp** | Geben Sie die Art der Ressource an, die Sie erstellen möchten.<br/><br/>Sie können die Ressourcen Kategorien Cursor und Dialogfeld erweitern, um zusätzliche Ressourcen anzuzeigen, die sich in befinden *. \Microsoft Visual Studio \<Version\>\vc\vkresourcetemplates\\< LCID\>\mfc.rct*. Wenn Sie RCT-Dateien hinzufügen müssen, platzieren Sie Sie entweder hier, oder geben Sie einen anderen [Includepfad](../windows/how-to-specify-include-directories-for-resources.md)an. Ressourcen, die auf der obersten Ebene in der Strukturansicht angezeigt werden, sind die Standard Ressourcen, die von Visual Studio bereitgestellt werden. Ressourcen in RCT-Dateien werden auf der zweiten Ebene unter der entsprechenden Kategorie angezeigt. Es gibt keine Voreinstellungs Beschränkung für die Anzahl von RCT-Dateien, die Sie hinzufügen können.<br/><br/> |
| **Neu** | Erstellen Sie eine Ressource basierend auf dem Typ, der im Feld **Ressourcentyp** ausgewählt ist, und öffnen Sie die Ressource im entsprechenden Editor.<br/><br/>Wenn Sie z. b. eine Dialogfeld Ressource erstellen, wird die Ressource im [Dialog-Editor](../windows/dialog-editor.md)geöffnet. |
| **Importieren** | Öffnen Sie das Dialogfeld **importieren** , um zu der Ressource zu navigieren, die Sie in das aktuelle Projekt importieren möchten.<br/><br/>Sie können eine Bitmap, ein Symbol, einen Cursor, HTML und einen Sound () importieren. WAV) oder benutzerdefinierte Ressourcen Datei. |
| **Benutzerdefiniert** | Öffnen Sie das Dialogfeld **neue benutzerdefinierte Ressource** , um eine benutzerdefinierte Ressource zu erstellen.<br/><br/>Enthält auch eine **Ressourcentyp** Eigenschaft, die ein Textfeld bereitstellt, in das Sie den Namen des benutzerdefinierten Ressourcentyps eingeben können. Visual C++ nutzt beim Beenden automatisch den Namen. Benutzerdefinierte Ressourcen werden nur im [Binär-Editor](../windows/binary-editor.md)bearbeitet. |

Wenn Sie eine neue Ressource erstellen, weist C++ das visuelle Element einen eindeutigen Namen zu, z. b. `IDD_Dialog1`. Sie können diese Ressourcen-ID anpassen, indem Sie die Ressourcen Eigenschaften entweder im zugehörigen Ressourcen-Editor oder im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)bearbeiten.

> [!NOTE]
> Geben Sie keinen Ressourcennamen oder eine ID an, der von Visual Studio reserviert ist. Reservierte Namen sind `DESIGNINFO`, `HWB`und `TEXTINCLUDE`, und die reservierte ID wird `255`.

### <a name="to-create-a-resource"></a>So erstellen Sie eine Ressource

- Wählen Sie in **Ressourcenansicht**die RC-Datei aus, und klicken Sie dann auf **Bearbeiten** > **Ressource hinzufügen** , und wählen Sie den Ressourcentyp aus, den Sie dem Projekt hinzufügen

   > [!TIP]
   > Sie können auch in **Ressourcenansicht** mit der rechten Maustaste auf die RC-Datei klicken und im Kontextmenü **Ressource hinzufügen** auswählen.

- Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektordner, wählen Sie > **Ressource hinzu** **fügen aus** , und wählen Sie den Ressourcentyp aus, den Sie dem Projekt hinzufügen

   > [!NOTE]
   > Wenn Sie nicht bereits über eine RC-Datei in Ihrem Projekt verfügen, wird ein solcher Schritt erstellt. Anschließend können Sie diesen Schritt wiederholen, um der neuen RC-Datei spezifische Ressourcentypen hinzuzufügen.

- Klicken Sie in [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code)mit der rechten Maustaste auf die Klasse, wählen Sie > **Ressource** **hinzufügen aus** , und wählen Sie den Ressourcentyp aus, den Sie dem Projekt hinzufügen

- Verwenden Sie das Menü **Projekt** > **Ressource hinzufügen**.

## <a name="use-resource-templates"></a>Verwenden von Ressourcen Vorlagen

Eine Ressourcen Vorlage ist eine angepasste Ressource, die Sie als RCT-Datei gespeichert haben. Eine Ressourcen Vorlage dient als Ausgangspunkt für das Erstellen von Ressourcen. Ressourcen Vorlagen sparen Zeit bei der Entwicklung zusätzlicher Ressourcen oder Ressourcengruppen, die Features gemeinsam nutzen, wie z. b. Standard Steuerelemente oder wiederholte Elemente. Wenn Sie z. b. eine Hilfe Schaltfläche mit einem Firmenlogo Symbol in mehrere Dialogfelder einschließen möchten, erstellen Sie eine neue Dialogfeld Vorlage, und passen Sie Sie mit der Schaltfläche Hilfe und dem Logo an.

Nachdem Sie eine Ressourcen Vorlage angepasst haben, speichern Sie die Änderungen im Vorlagen Ordner oder in dem im Include-Pfad angegebenen Speicherort, sodass die neue Ressourcen Vorlage unter dem Ressourcentyp im Dialogfeld **Ressource hinzufügen** angezeigt wird. Nun können Sie die neue Ressourcen Vorlage beliebig oft verwenden.

> [!NOTE]
> Der Ressourcen-Editor stellt automatisch eine eindeutige Ressourcen-ID bereit. Sie können die [Ressourcen Eigenschaften](../windows/changing-the-properties-of-a-resource.md) nach Bedarf überarbeiten.

> [!NOTE]
> Platzieren Sie sprachspezifische Vorlagen Dateien in Unterverzeichnissen des Hauptvorlagen Verzeichnisses. Beispielsweise werden nur englische Vorlagen Dateien *..\\< Verzeichnis der Ressourcen Vorlage\>\ 1033*.
>
> Visual Studio sucht nach neuen RCT-Dateien in *\Programme\Microsoft Visual Studio \<Version\>\vc\vkresourcetemplates*, *\Programme\Microsoft Visual Studio \<Version > \vc\vkresourcetemplates\\< LCID\>* (z. b. eine LCID von 1033 für Englisch) oder an einer beliebigen Stelle im [include-Pfad](../windows/how-to-specify-include-directories-for-resources.md). Wenn Sie Ihre RCT-Dateien lieber an einem anderen Speicherort speichern möchten, müssen Sie den Speicherort zum Includepfad hinzufügen.

### <a name="to-create-and-use-a-resource-template"></a>So erstellen und verwenden Sie eine Ressourcen Vorlage

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen** > **Neues Element hinzufügen**.

1. Wählen Sie im Bereich **Vorlagen:** die Option **Ressourcen Vorlagen Datei (. rct)** aus.

1. Geben Sie einen Namen und einen Speicherort für die neue *RCT* -Datei an, und wählen Sie **Öffnen**aus.

   Die neue *RCT* -Datei wird dem Projekt hinzugefügt und in **Projektmappen-Explorer** unter dem Ordner **Ressourcen** angezeigt.

1. Doppelklicken Sie auf die *RCT* -Datei, um Sie in einem Dokument Fenster zu öffnen. Um Ressourcen hinzuzufügen, klicken Sie mit der rechten Maustaste auf die Datei im Dokument Fenster, und wählen Sie **Ressource hinzufügen**.

   Sie können die hinzugefügten Ressourcen anpassen und die *RCT* -Datei speichern.

1. Klicken Sie im **Ressourcenansicht** Bereich mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie **Ressource hinzufügen**aus.

1. Wählen Sie das Pluszeichen ( **+** ) neben einer Ressource aus, um den Ressourcenknoten zu erweitern und die für diese Ressource verfügbaren Vorlagen anzuzeigen.

1. Doppelklicken Sie auf die Vorlage, die Sie verwenden möchten.

   Sie können die hinzugefügte Ressource nach Bedarf im Ressourcen-Editor ändern.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>So konvertieren Sie eine vorhandene Ressourcen Datei in eine Vorlage

Navigieren Sie mit der geöffneten Ressourcen Skriptdatei im Menü zu **Datei** > speichern Sie **\<*Dateinamen*> als**. Geben Sie einen Speicherort an, und wählen Sie **OK**.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Ressourcendateien](../windows/resource-files-visual-studio.md)<br/>
[Gewusst wie: Verwalten von Ressourcen](../windows/how-to-copy-resources.md)<br/>
[Vorgehensweise: Einfügen von Ressourcen zur Kompilierungszeit](../windows/how-to-include-resources-at-compile-time.md)<br/>