---
title: Dynamisches Layout
ms.date: 09/09/2019
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
ms.openlocfilehash: 3108e7bae0be216dfb877d03c87fdc17ef7d69f2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624752"
---
# <a name="dynamic-layout"></a>Dynamisches Layout

Mit MFC in Visual Studio 2015 können Sie Dialogfelder erstellen, in denen der Benutzer die Größe ändern kann, und Sie können steuern, wie das Layout an die Größe angepasst wird. Beispielsweise können Sie Schaltflächen am unteren Rand eines Dialogfelds anfügen, sodass sie sich immer am unteren Rand befinden. Sie können auch bestimmte Steuerelemente einrichten, wie z. B. Textfelder, Listenfelder und Bearbeitungsfelder, die erweitert werden, wenn der Benutzer das Dialogfeld erweitert.

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Angeben dynamischer Layouteinstellungen für ein MFC-Dialogfeld

Wenn der Benutzer die Größe eines Dialogfelds ändert, können die Steuerelemente im Dialogfeld in der Größe verändert oder in X- und Y-Richtung verschoben werden. Die Änderung in der Größe oder Position eines Steuerelements, wenn der Benutzer die Größe eines Dialogfelds ändert, wird als dynamisches Layout bezeichnet. Folgendes ist z. B. ein Dialogfeld vor dem Ändern der Größe:

![Dialogfeld vor dem Ändern der Größe.](../mfc/media/mfcdynamiclayout4.png "Dialogfeld vor dem Ändern der Größe.")

Nach dem Ändern der Größe ist der Listenfeldbereich vergrößert, um weitere Elemente anzuzeigen, und die Schaltflächen wurden entlang der rechten unteren Ecke verschoben:

![Dialogfeld nach dem Ändern der Größe.](../mfc/media/mfcdynamiclayout5.png "Dialogfeld nach dem Ändern der Größe.")

Sie können das dynamische Layout steuern, indem Sie die Details für jedes Steuerelement im Ressourcen-Editor in der IDE angeben, oder Sie können dies Programm gesteuert durchführen, indem Sie auf das `CMFCDynamicLayout` -Objekt für ein bestimmtes Steuerelement zugreifen und die Eigenschaften festlegen.

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Festlegen der Eigenschaften für das dynamische Layout im Ressourcen-Editor

Sie können das dynamische Layoutverhalten für ein Dialogfeld festlegen, ohne Code schreiben zu müssen, nämlich mit dem Ressourcen-Editor.

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>So legen Sie Eigenschaften für das dynamische Layout im Ressourcen-Editor fest

1. Öffnen Sie bei einem geöffneten MFC-Projekt das Dialogfeld, das Sie im Dialog-Editor bearbeiten möchten.

   ![Öffnen Sie das Dialogfeld im Ressourcen-Editor.](../mfc/media/mfcdynamiclayout3.png "Öffnen Sie das Dialogfeld im Ressourcen-Editor.")

1. Wählen Sie ein Steuerelement aus, und legen Sie im **Eigenschaften** Fenster (in **Klassenansicht**) dessen Eigenschaften für dynamisches Layout fest. Der Abschnitt **dynamischer Layout** im **Eigenschaften** Fenster enthält die Eigenschaften Verschiebungstyp, **Moving Type** **Größentyp**und, abhängig von den für diese Eigenschaften ausgewählten Werten, bestimmte Eigenschaften, die definieren, wie viele Steuerelemente verschoben oder geändert werden. **Moving Type** Der Verschiebungstyp bestimmt, wie ein Steuerelement verschoben wird, wenn die Größe des Dialog Felds geändert wird. Der **Sizing-Typ** bestimmt, wie die Größe eines Steuer Elements geändert wird, wenn sich die Größe des Dialog Felds ändert. Der Verschiebungstyp und der **Größen Anpassungs Typ** können **Horizontal**, **vertikal**, **beides**oder **None** sein, je nach den Dimensionen, die Sie dynamisch ändern möchten. **Moving Type** Horizontal ist die X-Dimension. Vertikal ist die Y-Richtung.

1. Wenn Sie möchten, dass ein Steuerelement, z. b. eine Schaltfläche, eine festgelegte Größe hat und in der unteren rechten Ecke angezeigt wird, wie es bei den Schaltflächen **OK** oder **Abbrechen** üblich ist, legen Sie den **Größentyp** auf **None**fest, und legen Sie den Verschiebungstyp auf **beide** **Moving Type** Legen Sie für die Werte zum **Verschieben von X** und zum **Verschieben von Y** unter Verschiebungstyp den Wert 100% fest, damit das Steuerelement in der unteren rechten Ecke einen festgelegten Abstand bleibt. **Moving Type**

   ![Dynamisches Layout](../mfc/media/mfcdynamiclayout1.png "Dynamisches Layout")

1. Angenommen, Sie haben auch ein Steuerelement, das erweitert werden soll, wenn das Dialogfeld erweitert wird. In der Regel kann ein Benutzer ein Dialogfeld erweitern, um ein mehrzeiliges Bearbeitungsfeld zu erweitern und die Größe des Textbereichs zu erhöhen, oder er erweitert möglicherweise ein Listensteuerelement, um mehr Daten anzuzeigen. Legen Sie in diesem Fall den **Typ der Größe** auf beide fest, und legen Sie den Verschiebungstyp auf keine fest. **Moving Type** Legen Sie anschließend die Werte für **Größe X** und **Größen** Anpassung auf 100 fest.

   ![Dynamische Layouteinstellungen](../mfc/media/mfcdynamiclayout2.png "Dynamische Layouteinstellungen")

1. Experimentieren Sie mit anderen Werten, die möglicherweise für Ihre Steuerelemente sinnvoll sind. Für ein Dialogfeld mit einem einzeiligen Textfeld kann der **Größentyp** beispielsweise auf **Horizontal** festgelegt werden.

### <a name="setting-dynamic-layout-properties-programmatically"></a>Programmgesteuertes Festlegen von Eigenschaften für das dynamische Layout

Das vorherige Verfahren eignet sich für das Angeben der Einstellungen für das dynamische Layout für einen Dialog zur Entwurfszeit, aber wenn Sie das dynamische Layout zur Laufzeit steuern möchten, können Sie Eigenschaften für das dynamische Layout programmgesteuert festlegen.

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>So legen Sie Eigenschaften für das dynamische Layout programmgesteuert fest

1. Suchen oder erstellen Sie eine Position im Implementierungscode der Dialogfeldklasse, an dem Sie das dynamische Layout für den Dialog angeben möchten. Sie können z. B. eine Methode wie `AdjustLayout` im Dialogfeld hinzufügen und von Positionen aus aufrufen, an denen das Layout geändert werden muss. Sie können dies zuerst vom Konstruktor aus oder nach dem Vornehmen von Änderungen am Dialog aufrufen.

1. Aufrufen Sie für das Dialogfeld [getdynamiclayout](reference/cwnd-class.md#getdynamiclayout), eine Methode der- `CWnd` Klasse. `GetDynamicLayout` gibt einen Zeiger auf ein `CMFCDynamicLayout` -Objekt zurück.

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

1. Verwenden Sie für das erste Steuerelement, zu dem Sie dynamisches Verhalten hinzufügen möchten, die statischen Methoden der dynamischen Layoutklasse, um [die Struktur zu erstellen, die die](reference/cmfcdynamiclayout-class.md#movesettings_structure) Art der Anpassung des Steuer Elements codiert. Wählen Sie dazu zuerst die entsprechende statische Methode aus: [cmfcdynamiclayout:: muvehorizontal](reference/cmfcdynamiclayout-class.md#movehorizontal), [cmfcdynamiclayout:: "muvevertical](reference/cmfcdynamiclayout-class.md#movevertical)", " [cmfcdynamiclayout:: muvenone](reference/cmfcdynamiclayout-class.md#movenone)" oder " [cmfcdynamiclayout:: muvehorizontalandvertical](reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)". Sie übergeben eine Prozentzahl für die horizontalen bzw. vertikalen Aspekte der Verschiebung. Diese statischen Methoden geben alle ein neu erstelltes „MoveSettings“-Objekt zurück, mit dem Sie das Verschiebeverhalten eines Steuerelements angeben können.

   Beachten Sie, dass 100 eine exakte Verschiebung gemäß der Größenänderung des Dialogs bedeutet, wodurch der Rand eines Steuerelement in einem festen Abstand zum neuen Rahmen bleibt.

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

1. Führen Sie die gleichen Schritte für das Größen Verhalten aus, bei dem der [sizesettings](reference/cmfcdynamiclayout-class.md#sizesettings_structure) -Typ verwendet wird. Um beispielsweise anzugeben, dass die Größe eines Steuerelements nicht geändert wird, wenn sich die Größe des Dialogfelds ändert, verwenden Sie folgenden Code:

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

1. Fügen Sie das Steuerelement mit der [cmfcdynamiclayout:: AddItem](reference/cmfcdynamiclayout-class.md#additem) -Methode zum dynamischen Layout-Manager hinzu. Es gibt zwei Überladungen für verschiedene Möglichkeiten zum Angeben des gewünschten Steuerelements. Eine verwendet den Fensterhandle (HWND) des Steuerelements, und die andere die Steuerelement-ID.

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

1. Wiederholen Sie den Vorgang für jedes Steuerelement, das verschoben oder dessen Größe geändert werden muss.

1. Bei Bedarf kann die [cmfcdynamiclayout:: hasitem](reference/cmfcdynamiclayout-class.md#hasitem) -Methode verwenden, um zu bestimmen, ob ein Steuerelement bereits in der Liste der Steuerelemente vorhanden ist, die dynamischen Layoutänderungen unterliegen, oder die [cmfcdynamiclayout:: IsEmpty](reference/cmfcdynamiclayout-class.md#isempty) -Methode, um zu bestimmen, ob Steuerelemente vorhanden sind, die Änderungen unterliegen.

1. Um das Dialogfeld Layout zu aktivieren, nennen Sie die [CWnd:: enabledynamiclayout](reference/cwnd-class.md#enabledynamiclayout) -Methode.

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

1. Wenn der Benutzer das nächste Mal die Größe des Dialog Felds ändert, wird die [cmfcdynamiclayout:: Adjust](reference/cmfcdynamiclayout-class.md#adjust) -Methode aufgerufen, die die Einstellungen tatsächlich anwendet.

1. Wenn Sie das dynamische Layout deaktivieren möchten, können Sie [CWnd:: enabledynamiclayout](reference/cwnd-class.md#enabledynamiclayout) mit **false** als für den *benabled* -Parameter aufrufen.

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>So legen Sie das dynamische Layout programmgesteuert aus einer Ressourcendatei fest

1. Verwenden Sie die [cmfcdynamiclayout:: muvehorizontalandvertical](reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) -Methode, um einen Ressourcennamen in der relevanten Ressourcen Skriptdatei (RC-Datei) anzugeben, die Informationen zum dynamischen Layout angibt, wie im folgenden Beispiel gezeigt:

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

   Die benannte Ressource muss auf ein Dialogfeld verweisen, das Layoutinformationen in Form eines **AFX_DIALOG_LAYOUT** Eintrags in der Ressourcen Datei enthält, wie im folgenden Beispiel gezeigt:

    ```RC
    /////////////////////////////////////////////////////////////////////////////
    //
    // AFX_DIALOG_LAYOUT
    //

    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6400,
    0x0028,
    0x643c,
    0x0028
    END

    IDD_DIALOG1 AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6464,
    0x0000,
    0x6464,
    0x0000,
    0x0000,
    0x6464,
    0x0000,
    0x0000

    END
    ```

## <a name="see-also"></a>Siehe auch

[CMFCDynamicLayout-Klasse](reference/cmfcdynamiclayout-class.md)<br/>
[Steuerelementklassen](control-classes.md)<br/>
[Dialogfeldklassen](dialog-box-classes.md)<br/>
[Dialog-Editor](../windows/dialog-editor.md)<br/>
[Dynamisches Dialog Feld Layout für MFC in Visual C++ 2015](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
