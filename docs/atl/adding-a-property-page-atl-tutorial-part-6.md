---
title: Hinzufügen einer Eigenschaftenseite (ATL-Lernprogramm, Teil 6)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
ms.openlocfilehash: 467ae19c372e24b2d368002cb83367b7087136fd
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078767"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Hinzufügen einer Eigenschaftenseite (ATL-Lernprogramm, Teil 6)

> [!NOTE]
> Der ATL-OLE DB-Anbieter-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

Eigenschaftenseiten werden als separate COM-Objekte implementiert, sodass sie bei Bedarf gemeinsam genutzt werden können. In diesem Schritt führen Sie die folgenden Aufgaben aus, um dem Steuerelement eine Eigenschaftenseite hinzuzufügen:

- Erstellen der Eigenschaftenseitenressource

- Hinzufügen von Code zum Erstellen und Verwalten der Eigenschaftenseite

- Hinzufügen der Eigenschaftenseite zum Steuerelement

## <a name="creating-the-property-page-resource"></a>Erstellen der Eigenschaftenseitenressource

Um dem Steuerelement eine Eigenschaftenseite hinzuzufügen, verwenden Sie die Vorlage für ATL-Eigenschaftenseiten.

### <a name="to-add-a-property-page"></a>So fügen Sie eine Eigenschaftenseite hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf `Polygon`.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** > **Neues Element**.

1. Wählen Sie aus der Liste der Vorlagen **ATL** > **ATL-Eigenschaftenseite** aus, und klicken Sie auf **Hinzufügen**.

1. Wenn der **ATL-Eigenschaftenseiten-Assistent** angezeigt wird, geben Sie *PolyProp* als **Kurznamen** ein.

1. Klicken Sie auf **Zeichenfolgen**, um die Seite **Zeichenfolgen** zu öffnen, und geben Sie **&Polygon** als **Titel** ein.

   Der **Titel** der Eigenschaftenseite ist die Zeichenfolge, die auf der Registerkarte für diese Seite angezeigt wird. Die **Dokumentzeichenfolge** ist eine Beschreibung, die von einem Eigenschaftenframe in einer Statuszeile oder QuickInfo angezeigt wird. Beachten Sie, dass der standardmäßige Eigenschaftenframe diese Zeichenfolge derzeit nicht verwendet, Sie können also den Standardinhalt beibehalten. Da Sie an diesem Punkt keine **Hilfedatei** generieren, löschen Sie den Eintrag in diesem Textfeld.

1. Klicken Sie auf **Fertig stellen** – das Eigenschaftenseitenobjekt wird erstellt.

Die folgenden drei Dateien werden erstellt:

|Datei|BESCHREIBUNG|
|----------|-----------------|
|PolyProp.h|Enthält die C++-Klasse `CPolyProp`, die die Eigenschaftenseite implementiert.|
|PolyProp.cpp|Enthält die Datei „PolyProp.h“.|
|PolyProp.rgs|Das Registrierungsskript, das das Eigenschaftenseitenobjekt registriert.|

Es werden auch folgende Codeänderungen vorgenommen:

- Die neue Eigenschaftenseite wird zur Objekteintragszuordnung in „Polygon.cpp“ hinzugefügt.

- Die Klasse `PolyProp` wird zur Datei „Polygon.idl“ hinzugefügt.

- Die neue Registrierungsskriptdatei „PolyProp.rgs“ wird zur Projektressource hinzugefügt.

- Der Projektressource für die Eigenschaftenseite wird eine Dialogfeldvorlage hinzugefügt.

- Die von Ihnen angegebenen Eigenschaftenzeichenfolgen werden zur Tabelle mit Ressourcenzeichenfolgen hinzugefügt.

Fügen Sie jetzt die Felder hinzu, die auf der Eigenschaftenseite angezeigt werden sollen.

### <a name="to-add-fields-to-the-property-page"></a>So fügen Sie der Eigenschaftenseite Felder hinzu

1. Doppelklicken Sie im **Projektmappen-Explorer** auf die Ressourcendatei „Polygon.rc“. Dadurch wird die **Ressourcenansicht** geöffnet.

1. Erweitern Sie in der **Ressourcenansicht** den Knoten `Dialog`, und doppelklicken Sie auf `IDD_POLYPROP`. Beachten Sie, dass das angezeigte Dialogfeld leer ist, bis auf einen Text, der angibt, dass Sie hier Ihre Steuerelemente einfügen können.

1. Wählen Sie diesen Text aus, und ändern Sie im Fenster `Sides:`Eigenschaften**den Text für**Beschriftung**zu**.

1. Passen Sie die Größe des Beschriftungsfelds an die Textgröße an.

1. Ziehen Sie ein **Bearbeitungssteuerelement** aus der **Toolbox** rechts neben die Beschriftung.

1. Als Letztes ändern Sie die **ID** des Bearbeitungssteuerelements im Fenster `IDC_SIDES`Eigenschaften**zu**.

Damit ist der Prozess der Erstellung der Eigenschaftenseitenressource abgeschlossen.

## <a name="adding-code-to-create-and-manage-the-property-page"></a>Hinzufügen von Code zum Erstellen und Verwalten der Eigenschaftenseite

Nachdem Sie die Eigenschaftenseitenressource erstellt haben, müssen Sie jetzt den Implementierungscode schreiben.

Als Erstes ermöglichen Sie es der `CPolyProp`-Klasse, die Anzahl von Seiten in Ihrem Objekt festzulegen, wenn die Schaltfläche **Anwenden** betätigt wird.

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>So ändern Sie die Anwenden-Funktion zum Festlegen der Anzahl von Seiten

1. Ersetzen Sie die Funktion `Apply` in „PolyProp.h“ durch den folgenden Code:

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

An eine Eigenschaftenseite können mehrere Clients gleichzeitig angefügt sein, deshalb wird die `Apply`-Funktion in einer Schleife ausgeführt und ruft `put_Sides` für jeden Client mit dem Wert auf, der aus dem Bearbeitungsfeld abgerufen wurde. Sie verwenden die Klasse [CComQIPtr](../atl/reference/ccomqiptr-class.md), `QueryInterface` in jedem Objekt ausführt, um die `IPolyCtl`-Schnittstelle aus der `IUnknown`-Schnittstelle abzurufen (gespeichert im `m_ppUnk`-Array).

Der Code überprüft jetzt, ob das Festlegen der `Sides`-Eigenschaft tatsächlich funktioniert hat. Bei einem Fehler zeigt der Code ein Meldungsfeld mit den Fehlerdetails aus der `IErrorInfo`-Schnittstelle an. In der Regel fragt ein Container ein Objekt nach der `ISupportErrorInfo`-Schnittstelle ab und ruft zuerst `InterfaceSupportsErrorInfo` auf, um zu ermitteln, ob das Objekt das Festlegen von Fehlerinformationen unterstützt. Sie können diese Aufgabe überspringen.

[CComPtr](../atl/reference/ccomptr-class.md) kümmert sich automatisch um die Verweiszählung, sodass ein Aufruf von `Release` in der Schnittstelle nicht erforderlich ist. `CComBSTR` hilft Ihnen bei der BSTR-Verarbeitung, damit Sie den finalen Aufruf von `SysFreeString` nicht ausführen müssen. Sie können auch eine der unterschiedlichen Klassen für die Zeichenfolgenkonvertierung verwenden, um BSTR bei Bedarf konvertieren zu können (aus diesem Grund befindet sich das USES_CONVERSION-Makro am Anfang der Funktion).

Sie müssen auch das Änderungsflag der Eigenschaftenseite festlegen, um anzugeben, dass die Schaltfläche **Anwenden** aktiviert werden muss. Dies erfolgt, wenn ein Benutzer den Wert im Bearbeitungsfeld **Seiten** ändert.

### <a name="to-handle-the-apply-button"></a>So verarbeiten Sie die Schaltfläche „Anwenden“

1. Klicken Sie in der **Klassenansicht** mit der rechten Maustaste auf `CPolyProp`, und klicken Sie im Kontextmenü auf **Eigenschaften**.

1. Klicken Sie im Fenster **Eigenschaften** auf das Symbol **Ereignisse**.

1. Erweitern Sie in der Ereignisliste den Knoten `IDC_SIDES`.

1. Wählen Sie `EN_CHANGE` aus, und klicken Sie im Dropdownmenü auf der rechten Seite auf **\<Hinzufügen> OnEnChangeSides**. Die Deklaration des Handlers `OnEnChangeSides` wird zu „Polyprop.h“ hinzugefügt, die Handlerimplementierung zu „Polyprop.cpp“.

Als Nächstes ändern Sie den Handler.

### <a name="to-modify-the-onenchangesides-method"></a>So ändern Sie die OnEnChangeSides-Methode

1. Fügen Sie folgenden Code in „Polyprop.cpp“ zur `OnEnChangeSides`-Methode hinzu (löschen Sie dabei sämtlichen Code, den der Assistent eingefügt hat):

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

`OnEnChangeSides` wird aufgerufen, wenn eine `WM_COMMAND`-Meldung mit der `EN_CHANGE`-Benachrichtigung für das `IDC_SIDES`-Steuerelement gesendet wird. `OnEnChangeSides` ruft dann `SetDirty` auf, und übergibt TRUE, um anzugeben, dass die Eigenschaftenseite geändert wurde und die Schaltfläche **Anwenden** aktiviert werden muss.

## <a name="adding-the-property-page-to-the-control"></a>Hinzufügen der Eigenschaftenseite zum Steuerelement

Die Vorlage und der Assistent für ATL-Eigenschaftenseiten fügen die Eigenschaftenseite nicht automatisch zu Ihrem Steuerelement hinzu, weil mehrere Steuerelemente in Ihrem Projekt vorhanden sein können. Sie müssen einen Eintrag zur Eigenschaftenzuordnung des Steuerelements hinzufügen.

### <a name="to-add-the-property-page"></a>So fügen Sie die Eigenschaftenseite hinzu

1. Öffnen Sie „PolyCtl.h“, und fügen Sie die folgenden Zeilen zur Eigenschaftenzuordnung hinzu:

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

Die Eigenschaftenzuordnung des Steuerelements sieht jetzt folgendermaßen aus:

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

Sie hätten auch ein `PROP_PAGE`-Makro mit der CLSID Ihrer Eigenschaftenseite hinzufügen können. Wenn Sie aber das `PROP_ENTRY`-Makro wie gezeigt verwenden, wird der Wert der `Sides`-Eigenschaft auch gespeichert, wenn das Steuerelement gespeichert wird.

Die drei Parameter im Makro sind die Beschreibung der Eigenschaft, die DISPID der Eigenschaft und die CLSID der Eigenschaftenseite, in der sich die Eigenschaft befindet. Dies ist nützlich, wenn Sie z.B. das Steuerelement in Visual Basic laden und die Anzahl von Seiten zur Entwurfszeit festlegen. Da die Anzahl von Seiten gespeichert wird, wird dieser Wert beim erneuten Laden des Visual Basic-Projekts wiederhergestellt.

## <a name="building-and-testing-the-control"></a>Erstellen und Testen des Steuerelements

Jetzt erstellen Sie das Steuerelement und fügen es in einen Testcontainer für ActiveX-Steuerelemente ein. Klicken Sie im **Testcontainer** im Menü **Bearbeiten** auf **PolyCtl-Klassenobjekt**. Die Eigenschaftenseite wird mit den von Ihnen hinzugefügten Informationen angezeigt.

Die Schaltfläche **Anwenden** ist anfangs deaktiviert. Beginnen Sie mit der Eingabe eines Werts in das Feld **Seiten**. Die Schaltfläche **Anwenden** wird aktiviert. Wenn Sie den Wert fertig eingegeben haben, klicken Sie auf die Schaltfläche **Anwenden**. Die Anzeige des Steuerelements ändert sich, und die Schaltfläche **Anwenden** ist wieder deaktiviert. Geben Sie einen ungültigen Wert ein. Es wird ein Meldungsfeld mit der Fehlerbeschreibung angezeigt, die Sie über die `put_Sides`-Funktion festgelegt haben.

Als Nächstes fügen Sie Ihr Steuerelement auf einer Webseite ein.

[Zurück zu Schritt 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [Weiter zu Schritt 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>Weitere Informationen

[Tutorial](../atl/active-template-library-atl-tutorial.md)
