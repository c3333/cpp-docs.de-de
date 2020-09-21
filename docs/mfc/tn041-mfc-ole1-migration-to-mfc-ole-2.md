---
title: 'TN041: MFC-OLE1 Migration zu MFC-OLE 2'
ms.date: 10/18/2018
helpviewer_keywords:
- OLE1 [MFC]
- migrating OLE1 to OLE2
- migration [MFC], OLE1 to OLE2
- OLE2 [MFC]
- porting OLE1 to OLE2
- converting OLE1 to OLE2
- upgrading Visual C++ applications [MFC], OLE1 to OLE2
- TN041
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
ms.openlocfilehash: 7d0381983481278b1410ae0ff11463519d4cbb34
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743151"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041: MFC/OLE1-Migration zu MFC/OLE 2

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

## <a name="general-issues-relating-to-migration"></a>Allgemeine Probleme im Zusammenhang mit der Migration

Eines der Entwurfs Ziele für die OLE 2-Klassen in MFC 2,5 (und höher) bestand darin, einen Großteil derselben Architektur beizubehalten, die in MFC 2,0 für OLE 1,0-Unterstützung vorhanden ist. Infolgedessen sind viele der gleichen OLE-Klassen in MFC 2,0 in dieser MFC-Version ( `COleDocument` , `COleServerDoc` , `COleClientItem` , `COleServerItem` ) vorhanden. Außerdem sind viele der APIs in diesen Klassen exakt identisch. Allerdings unterscheidet sich OLE 2 erheblich von OLE 1,0, sodass Sie erwarten können, dass sich einige der Details geändert haben. Wenn Sie mit der OLE1-Unterstützung von MFC 2.0 vertraut sind, werden Sie sich zu Hause mit der MFC-Unterstützung für 2,0 fühlen.

Wenn Sie eine vorhandene MFC/OLE1-Anwendung in eine vorhandene MFC/-Anwendung einfügen und ihr eine OLE 2-Funktionalität hinzufügen, sollten Sie diese Notiz zuerst In diesem Hinweis werden einige allgemeine Probleme behandelt, die bei der Portierung ihrer OLE1-Funktionalität auf MFC/OLE 2 auftreten können. Anschließend werden die Probleme erläutert, die beim Portieren von zwei in MFC 2,0 enthaltenen Anwendungen entdeckt werden: MFC-OLE-Beispiele [OCLIENT](../overview/visual-cpp-samples.md) und [Hierarchien](../overview/visual-cpp-samples.md).

## <a name="mfc-documentview-architecture-is-important"></a>MFC-Dokument-/Ansichtarchitektur ist wichtig

Wenn Ihre Anwendung die Dokument-/Ansichtsarchitektur von MFC nicht verwendet und Sie der Anwendung OLE 2-Unterstützung hinzufügen möchten, können Sie jetzt zu Dokument/Ansicht wechseln. Viele der Vorteile der OLE 2-Klassen von MFC werden nur erreicht, wenn Ihre Anwendung die integrierte Architektur und die Komponenten von MFC verwendet.

Das Implementieren eines Servers oder Containers ohne Verwendung der MFC-Architektur ist möglich, wird jedoch nicht empfohlen.

## <a name="use-mfc-implementation-instead-of-your-own"></a>Verwenden Sie anstelle ihrer eigenen MFC-Implementierung.

MFC `CToolBar` -Klassen für die Implementierung von Klassen, wie z. b., und, `CStatusBar` `CScrollView` verfügen über integrierten Sonderfall Code für die Unterstützung von OLE 2. Wenn Sie diese Klassen in Ihrer Anwendung verwenden können, profitieren Sie von den in der Anwendung einfügenden Anstrengungen, um Sie auf OLE zu erkennen. Auch hier ist es möglich, für diese Zwecke "Rollout"-Klassen zu nutzen, aber es ist nicht empfehlenswert. Wenn Sie eine ähnliche Funktionalität implementieren müssen, ist der MFC-Quellcode eine hervorragende Referenz für den Umgang mit einigen der präzisere Punkte von OLE (insbesondere bei der direkten Aktivierung).

## <a name="examine-the-mfc-sample-code"></a>Überprüfen des MFC-Beispielcodes

Es gibt eine Reihe von MFC-Beispielen, die OLE-Funktionalität enthalten. Jede dieser Anwendungen implementiert OLE aus einem anderen Winkel:

- [Hierarchien](../overview/visual-cpp-samples.md) Ist hauptsächlich für die Verwendung als Serveranwendung gedacht. Sie war in MFC 2,0 als MFC/OLE1-Anwendung enthalten und wurde zu MFC/OLE 2 portiert und anschließend so erweitert, dass viele OLE-Funktionen implementiert werden, die in OLE 2 verfügbar sind.

- [OCLIENT](../overview/visual-cpp-samples.md) Dabei handelt es sich um eine eigenständige Containeranwendung, die viele der OLE-Features aus der Sicht eines Containers veranschaulichen soll. Außerdem wurde sie von MFC 2,0 portiert und dann erweitert, um viele der erweiterten OLE-Funktionen zu unterstützen, wie z. b. benutzerdefinierte Zwischenablage Formate und Links zu eingebetteten Elementen.

- [DRAWCLI](../overview/visual-cpp-samples.md) Diese Anwendung implementiert die Unterstützung von OLE-Containern ähnlich wie OCLIENT, mit der Ausnahme, dass dies innerhalb des Frameworks eines vorhandenen objektorientierten Zeichnungs Programms erfolgt. Es zeigt Ihnen, wie Sie Unterstützung für OLE-Container implementieren und in Ihre vorhandene Anwendung integrieren können.

- [SUPERPAD](../overview/visual-cpp-samples.md) Diese Anwendung ist auch eine feine eigenständige Anwendung, ist auch ein OLE-Server. Die von ihm implementierte Serverunterstützung ist ziemlich minimalistisch. Besonders interessant ist, wie es OLE-Zwischenablage Dienste zum Kopieren von Daten in die Zwischenablage verwendet, aber die Funktionalität verwendet, die in das Windows-Steuerelement "Edit" integriert ist, um die Zwischenablage Funktionalität zu implementieren Dies zeigt eine interessante Mischung aus herkömmlicher Nutzung der Windows-API sowie die Integration in die neuen OLE-APIs.

Weitere Informationen zu den Beispielanwendungen finden Sie in der MFC-Beispiel Hilfe.

## <a name="case-study-oclient-from-mfc-20"></a>Fallstudie: OCLIENT von MFC 2,0

Wie bereits erläutert, war [OCLIENT](../overview/visual-cpp-samples.md) in MFC 2,0 enthalten und implementierte OLE mit MFC/OLE1. Im folgenden werden die Schritte beschrieben, mit denen diese Anwendung anfänglich zur Verwendung der MFC/OLE 2-Klassen konvertiert wurde. Nach Abschluss des ersten Ports wurden einige Features hinzugefügt, um die MFC/OLE-Klassen besser zu veranschaulichen. Diese Features werden hier nicht behandelt. Weitere Informationen zu diesen erweiterten Features finden Sie im Beispiel selbst.

> [!NOTE]
> Compilerfehler und Schritt-für-Schritt-Prozess wurden mit Visual C++ 2,0 erstellt. Bestimmte Fehlermeldungen und Speicherorte haben sich möglicherweise mit Visual C++ 4,0 geändert, die konzeptionellen Informationen sind jedoch weiterhin gültig.

### <a name="getting-it-up-and-running"></a>Einrichten und ausführen

Der Ansatz zum Portieren des OCLIENT-Beispiels für MFC/OLE besteht darin, den Vorgang zu starten und die offensichtlichen Compilerfehler zu beheben, die sich ergeben. Wenn Sie das OCLIENT-Beispiel von MFC 2,0 verwenden und dieses unter dieser MFC-Version kompilieren, werden Sie feststellen, dass es nicht möglich ist, dass viele Fehler behoben werden müssen. Die Fehler in der Reihenfolge, in der Sie aufgetreten sind, sind unten beschrieben.

### <a name="compile-and-fix-errors"></a>Kompilieren und Beheben von Fehlern

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

Der erste Fehler betrifft `COleClientItem::Draw` . In MFC/OLE1 hat es mehr Parameter benötigt, als die MFC/OLE-Version benötigt. Die zusätzlichen Parameter waren oft nicht notwendig und in der Regel NULL (wie in diesem Beispiel). Diese MFC-Version kann automatisch die Werte für die lpwbounds ermitteln, wenn es sich bei dem CDC, der als gezeichnete CDC dient, um einen metadateidc handelt. Außerdem ist der pformatdc-Parameter nicht mehr erforderlich, da das Framework von dem "Attribut-DC" des übergebenen PDC erstellt wird. Um dieses Problem zu beheben, entfernen Sie einfach die beiden zusätzlichen NULL-Parameter zum Zeichnen-Befehl.

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

Die obigen Fehler ergeben sich aus der Tatsache, dass für alle `COleClientItem::CreateXXXX` Funktionen in MFC/OLE1 ein eindeutiger Name an das Element weitergegeben werden muss. Dies war eine Voraussetzung für die zugrunde liegende OLE-API. Dies ist in MFC/OLE 2 nicht erforderlich, da von OLE 2 nicht DDE als zugrunde liegender Kommunikationsmechanismus verwendet wird (der Name wurde in DDE-Konversationen verwendet). Um dieses Problem zu beheben, können Sie die `CreateNewName` Funktion und alle Verweise darauf entfernen. Es ist einfach herauszufinden, was jede MFC/OLE-Funktion in dieser Version erwartet, indem Sie den Cursor auf den-Befehl platzieren und F1 drücken.

Ein weiterer Bereich, der sich erheblich unterscheidet, ist die Behandlung der Zwischenablage von OLE Mit OLE1 haben Sie die Windows-Zwischenablage-APIs verwendet, die mit der Zwischenablage interagieren. Bei OLE 2 erfolgt dies mit einem anderen Mechanismus. Die MFC/OLE1-APIs gehen davon aus, dass die Zwischenablage geöffnet war, bevor Sie ein- `COleClientItem` Objekt in die Zwischenablage kopieren Dies ist nicht mehr erforderlich und führt dazu, dass alle MFC/OLE-Zwischenablage Vorgänge fehlschlagen. Wenn Sie den Code bearbeiten, um Abhängigkeiten zu entfernen `CreateNewName` , sollten Sie auch den Code entfernen, der die Windows-Zwischenablage öffnet und schließt.

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

Diese Fehler resultieren aus dem- `CMainView::OnInsertObject` Handler. Die Handhabung des Befehls "neues Objekt einfügen" ist ein weiterer Bereich, in dem sich etwas geändert hat. In diesem Fall ist es am einfachsten, einfach die ursprüngliche Implementierung mit der von AppWizard für eine neue OLE-Container Anwendung zusammenzuführen. Tatsächlich handelt es sich hierbei um eine Technik, die Sie zum Portieren von anderen Anwendungen anwenden können. In MFC/OLE1 haben Sie das Dialogfeld "Objekt einfügen" durch Aufrufen der `AfxOleInsertDialog` Funktion angezeigt. In dieser Version erstellen Sie ein `COleInsertObject` Dialog Objekt und einen aufzurufenden `DoModal` . Außerdem werden neue OLE-Elemente mit einer **CLSID** anstelle einer ClassName-Zeichenfolge erstellt. Das Endergebnis sollte in etwa wie folgt aussehen.

```cpp
COleInsertDialog dlg;
if (dlg.DoModal() != IDOK)
    return;

BeginWaitCursor();

CRectItem* pItem = NULL;
TRY
{
    // First create the C++ object
    pItem = GetDocument()->CreateItem();
    ASSERT_VALID(pItem);

    // Initialize the item from the dialog data.
    if (!dlg.CreateItem(pItem))
        AfxThrowMemoryException();
            // any exception will do
    ASSERT_VALID(pItem);

    // run the object if appropriate
    if (dlg.GetSelectionType() == COleInsertDialog::createNewItem)
        pItem->DoVerb(OLEIVERB_SHOW, this);

    // update right away
    pItem->UpdateLink();
    pItem->UpdateItemRectFromServer();

    // set selection to newly inserted item
    SetSelection(pItem);
    pItem->Invalidate();
}
CATCH (CException, e)
{
    // clean up item
    if (pItem != NULL)
        GetDocument()->DeleteItem(pItem);

    AfxMessageBox(IDP_FAILED_TO_CREATE);
}
END_CATCH

EndWaitCursor();
```

> [!NOTE]
> Das Einfügen eines neuen Objekts unterscheidet sich möglicherweise von der Anwendung):

Außerdem muss eingeschlossen \<afxodlgs.h> werden, das die Deklaration für die Dialogfeld `COleInsertObject` Klasse sowie die anderen Standard Dialogfelder enthält, die von MFC bereitgestellt werden.

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

Diese Fehler werden durch die Tatsache verursacht, dass einige OLE1-Konstanten in OLE 2 geändert wurden, auch wenn Sie im Konzept identisch sind. In diesem Fall `OLEVERB_PRIMARY` wurde in geändert `OLEIVERB_PRIMARY` . Sowohl in OLE1 als auch in OLE 2 wird das primäre Verb normalerweise von einem Container ausgeführt, wenn der Benutzer auf ein Element doppelklickt.

Außerdem `DoVerb` nimmt nun einen zusätzlichen Parameter an – einen Zeiger auf eine Ansicht ( `CView` *). Dieser Parameter wird nur verwendet, um "visuelle Bearbeitung" (oder direkte Aktivierung) zu implementieren. Nun legen Sie diesen Parameter auf NULL fest, da Sie diese Funktion zurzeit nicht implementieren.

Um sicherzustellen, dass das Framework nie versucht, direkt zu aktivieren, sollten Sie Folgendes überschreiben `COleClientItem::CanActivate` :

```cpp
BOOL CRectItem::CanActivate()
{
    return FALSE;
}
```

```Output
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function
```

In MFC/OLE1 `COleClientItem::GetBounds` wurden und `SetBounds` zum Abfragen und Bearbeiten des Wertebereichs eines Elements verwendet (die `left` -und-Member `top` waren immer null). In MFC/OLE 2 wird dies direkt von und unter `COleClientItem::GetExtent` stützt `SetExtent` , die sich mit einer **Größe** oder `CSize` stattdessen befassen.

Der Code für die neuen Aufrufe setitemrectdeserver und updateitemrectfromserver sieht wie folgt aus:

```cpp
BOOL CRectItem::UpdateItemRectFromServer()
{
    ASSERT(m_bTrackServerSize);
    CSize size;
    if (!GetExtent(&size))
        return FALSE;    // blank

    // map from HIMETRIC to screen coordinates
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.LPtoDP(&size);
    }
    // just set the item size
    if (m_rect.Size() != size)
    {
        // invalidate the old size/position
        Invalidate();
        m_rect.right = m_rect.left + size.cx;
        m_rect.bottom = m_rect.top + size.cy;
        // as well as the new size/position
        Invalidate();
    }
    return TRUE;
}

BOOL CRectItem::SetItemRectToServer()
{
    // set the official bounds for the embedded item
    CSize size = m_rect.Size();
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.DPtoLP(&size);
    }
    TRY
    {
        SetExtent(size);    // may do a wait
    }
    CATCH(CException, e)
    {
        return FALSE;  // links will not allow SetBounds
    }
    END_CATCH
    return TRUE;
}
```

```Output
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function
```

In MFC/OLE1 wurden synchrone API-Aufrufe von einem Container zu einem Server *simuliert*, da OLE1 in vielen Fällen in der Regel asynchron war. Vor dem Verarbeiten von Befehlen vom Benutzer musste nach einem ausstehenden asynchronen aufzurufen suchen. MFC/OLE1 hat die `COleClientItem::InWaitForRelease` Funktion dafür bereitgestellt. In MFC/OLE 2 ist dies nicht erforderlich, daher können Sie die Überschreibung von OnCommand in CMainFrame alle entfernen.

An diesem Punkt wird OCLIENT kompiliert und verknüpft.

### <a name="other-necessary-changes"></a>Weitere erforderliche Änderungen

Es gibt nur wenige Dinge, die nicht ausgeführt werden, da OCLIENT jedoch nicht ausgeführt werden kann. Es ist besser, diese Probleme jetzt anstatt später zu beheben.

Zunächst ist es erforderlich, die OLE-Bibliotheken zu initialisieren. Dies erfolgt durch Aufrufen `AfxOleInit` von aus `InitInstance` :

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

Es ist auch eine gute Idee, auf virtuelle Funktionen für Änderungen der Parameterliste zu überprüfen. Eine dieser Funktionen ist `COleClientItem::OnChange` , überschrieben in jeder MFC/OLE-Containeranwendung. Wenn Sie sich die Online Hilfe Ansehen, sehen Sie, dass ein zusätzliches ' DWORD dwparam ' hinzugefügt wurde. Das neue crectitem:: OnChange-Element sieht wie folgt aus:

```cpp
void
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)
{
    if (m_bTrackServerSize && !UpdateItemRectFromServer())
    {
        // Blank object
        if (wNotification == OLE_CLOSED)
        {
            // no data received for the object - destroy it
            ASSERT(!IsVisible());
            GetDocument()->DeleteItem(this);
            return; // no update (item is gone now)
        }
    }
    if (wNotification != OLE_CLOSED)
        Dirty();
    Invalidate();
    // any change will cause a redraw
}
```

In MFC/OLE1 haben Container Anwendungen die Document-Klasse von abgeleitet `COleClientDoc` . In MFC/OLE 2 wurde diese Klasse entfernt und durch ersetzt `COleDocument` (diese neue Organisation vereinfacht das Erstellen von Container-/Server-Anwendungen). Es gibt eine **#define** , die `COleClientDoc` zugeordnet ist, um das `COleDocument` Portieren von MFC/OLE1-Anwendungen zu MFC/OLE 2 (z. b. OCLIENT) zu vereinfachen. Eine der Features, die nicht von `COleDocument` bereitgestellt wurde und die von bereitgestellt wurde, `COleClientDoc` sind die Standard Zuordnungs Einträge der Befehls Meldung. Dies geschieht, damit Server Anwendungen, die `COleDocument` (indirekt) verwenden, nicht den mehr Aufwand dieser Befehls Handler verwenden, es sei denn, es handelt sich um eine Container-/Server-Anwendung. Sie müssen der cmaindoc-Meldungs Zuordnung die folgenden Einträge hinzufügen:

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

Die Implementierung aller dieser Befehle ist in, d `COleDocument` . h. die Basisklasse für das Dokument.

An diesem Punkt ist OCLIENT eine funktionale OLE-Container-Anwendung. Es ist möglich, Elemente eines beliebigen Typs (OLE1 oder OLE 2) einzufügen. Da der erforderliche Code zum Aktivieren der direkten Aktivierung nicht implementiert ist, werden Elemente ähnlich wie bei OLE1 in einem separaten Fenster bearbeitet. Im nächsten Abschnitt werden die erforderlichen Änderungen erläutert, um die direkte Bearbeitung (auch "visuelle Bearbeitung" genannt) zu aktivieren.

### <a name="adding-visual-editing"></a>Hinzufügen der visuellen Bearbeitung

Eines der interessantesten Features von OLE ist die direkte Aktivierung (oder "visuelle Bearbeitung"). Diese Funktion ermöglicht es der Serveranwendung, Teile der Benutzeroberfläche des Containers zu übernehmen, um eine nahtlose Bearbeitungs Schnittstelle für den Benutzer bereitzustellen. Zum Implementieren der direkten Aktivierung für OCLIENT müssen einige besondere Ressourcen hinzugefügt werden, sowie zusätzlicher Code. Diese Ressourcen und der Code werden normalerweise von AppWizard bereitgestellt – tatsächlich wurde ein Großteil des Codes an dieser Stelle direkt aus einer neuen AppWizard-Anwendung mit "Container"-Unterstützung entnommen.

Zuerst muss eine Menü Ressource hinzugefügt werden, die verwendet wird, wenn ein Element vorhanden ist, das direkt aktiv ist. Sie können diese zusätzliche Menü Ressource in Visual C++ erstellen, indem Sie die IDR_OCLITYPE Ressource kopieren und alle außer den Datei-und Fenster-Popups entfernen. Zwischen den Popups "Datei" und "Fenster" werden zwei Trennlinien eingefügt, um die Trennung von Gruppen anzugeben (es sollte wie folgt aussehen: Datei &#124;&#124; Fenster). Weitere Informationen zur Bedeutung dieser Trennzeichen und zur Zusammenführung der Server-und Container Menüs finden Sie unter [Menüs und Ressourcen:](../mfc/menus-and-resources-menu-merging.md)Zusammenführen von Menüs.

Nachdem Sie diese Menüs erstellt haben, müssen Sie dem Framework über diese Informationen informieren. Dies erfolgt durch Aufrufen von `CDocTemplate::SetContainerInfo` für die Dokument Vorlage, bevor Sie Sie der Dokumentvorlagen Liste in ihrer InitInstance hinzufügen. Der neue Code zum Registrieren der Dokument Vorlage sieht wie folgt aus:

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

Die IDR_OLECLITYPE_INPLACE Ressource ist die spezielle direkte Ressource, die in Visual C++ erstellt wurde.

Um die direkte Aktivierung zu aktivieren, müssen sich einige Dinge sowohl in der `CView` abgeleiteten Klasse (CMainView) als auch in der `COleClientItem` abgeleiteten Klasse (crectitem) ändern. Alle diese außer Kraft setzungen werden von AppWizard bereitgestellt, und der größte Teil der Implementierung erfolgt direkt in einer standardmäßigen AppWizard-Anwendung.

Im ersten Schritt dieses Ports wurde die direkte Aktivierung vollständig durch Überschreiben von deaktiviert `COleClientItem::CanActivate` . Diese außer Kraft Setzung sollte entfernt werden, um die direkte Aktivierung zuzulassen. Außerdem wurde NULL an alle Aufrufe an `DoVerb` (es gibt zwei davon), da die Bereitstellung der Ansicht nur für die direkte Aktivierung notwendig war. Damit die direkte Aktivierung vollständig implementiert werden kann, ist es erforderlich, die richtige Ansicht im-Befehl zu übergeben `DoVerb` . Einer dieser Aufrufe ist `CMainView::OnInsertObject` :

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

Eine andere ist in `CMainView::OnLButtonDblClk` :

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

Es muss überschrieben werden `COleClientItem::OnGetItemPosition` . Dadurch wird dem Server mitgeteilt, wo das Fenster in Relation zum Fenster des Containers platziert werden soll, wenn das Element direkt aktiviert wird. Für OCLIENT ist die Implementierung trivial:

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

Die meisten Server implementieren auch, was als "direkte Größe der Größe" bezeichnet wird. Dadurch kann das Server Fenster verkleinert und verschoben werden, während der Benutzer das Element bearbeitet. Der Container muss an dieser Aktion teilnehmen, da sich das Verschieben oder Ändern der Größe des Fensters in der Regel auf die Position und Größe innerhalb des Container Dokuments selbst auswirkt. Die-Implementierung für OCLIENT synchronisiert das interne Rechteck, das durch m_rect verwaltet wird, mit der neuen Position und Größe.

```cpp
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)
{
    ASSERT_VALID(this);

    if (!COleClientItem::OnChangeItemPosition(rectPos))
        return FALSE;

    Invalidate();
    m_rect = rectPos;
    Invalidate();
    GetDocument()->SetModifiedFlag();

    return TRUE;
}
```

An diesem Punkt ist ausreichend Code vorhanden, damit ein Element direkt aktiviert werden kann, und um die Größe zu ändern und das Element zu bearbeiten, wenn es aktiv ist, aber kein Code ermöglicht es dem Benutzer, die Bearbeitungs Sitzung zu beenden. Obwohl einige Server diese Funktionalität selbst bereitstellen, indem Sie den escapeschlüssel verarbeiten, wird empfohlen, dass Container zwei Möglichkeiten zur Deaktivierung eines Elements bieten: (1) durch Klicken außerhalb des Elements und (2) durch Drücken der Escapetaste.

Fügen Sie für den escapeschlüssel eine Zugriffstaste mit Visual C++ hinzu, die den VK_ESCAPE Key einem Befehl zuordnet, ID_CANCEL_EDIT den Ressourcen hinzugefügt wird. Der Handler für diesen Befehl folgt:

```cpp
// The following command handler provides the standard
// keyboard user interface to cancel an in-place
// editing session.void CMainView::OnCancelEdit()
{
    // Close any in-place active item on this view.
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->Close();
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);
}
```

Um den Fall zu behandeln, in dem der Benutzer außerhalb des Elements klickt, fügen Sie den folgenden Code am Anfang von hinzu `CMainView::SetSelection` :

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

Wenn ein Element direkt aktiv ist, sollte es den Fokus haben. Um sicherzustellen, dass dies der Fall ist, wird OnSetFocus behandelt, sodass der Fokus immer an das aktive Element übertragen wird, wenn die Ansicht den Fokus erhält:

```cpp
// Special handling of OnSetFocus and OnSize are required
// when an object is being edited in-place.
void CMainView::OnSetFocus(CWnd* pOldWnd)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);

    if (pActiveItem != NULL &&
        pActiveItem->GetItemState() == COleClientItem::activeUIState)
    {
        // need to set focus to this item if it is same view
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();
        if (pWnd != NULL)
        {
            pWnd->SetFocus();   // don't call the base class
            return;
        }
    }

    CView::OnSetFocus(pOldWnd);
}
```

Wenn die Größe der Sicht geändert wird, müssen Sie das aktive Element Benachrichtigen, dass sich das Clippingrechteck geändert hat. Zu diesem Zweck stellen Sie einen Handler für Folgendes bereit `OnSize` :

```cpp
void CMainView::OnSize(UINT nType, int cx, int cy)
{
    CView::OnSize(nType, cx, cy);
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->SetItemRects();
}
```

## <a name="case-study-hiersvr-from-mfc-20"></a>Fallstudie: HIERSVR von MFC 2,0

[HIERSVR](../overview/visual-cpp-samples.md) ist auch in MFC 2,0 enthalten und OLE mit MFC/OLE1 implementiert. In diesem Hinweis werden die Schritte kurz beschrieben, mit denen diese Anwendung anfänglich für die Verwendung der MFC/OLE 2-Klassen konvertiert wurde. Nach Abschluss des ersten Ports wurden einige Features hinzugefügt, um die MFC/OLE 2-Klassen besser zu veranschaulichen. Diese Features werden hier nicht behandelt. Weitere Informationen zu diesen erweiterten Features finden Sie im Beispiel selbst.

> [!NOTE]
> Compilerfehler und Schritt-für-Schritt-Prozess wurden mit Visual C++ 2,0 erstellt. Bestimmte Fehlermeldungen und Speicherorte haben sich möglicherweise mit Visual C++ 4,0 geändert, die konzeptionellen Informationen sind jedoch weiterhin gültig.

### <a name="getting-it-up-and-running"></a>Einrichten und ausführen

Der Ansatz zum Portieren des Hierarchie Beispiels an MFC/OLE besteht darin, den Vorgang zu starten und die offensichtlichen Compilerfehler zu beheben, die sich ergeben. Wenn Sie das Hierarchie Beispiel von MFC 2,0 verwenden und dieses unter dieser Version von MFC kompilieren, werden Sie feststellen, dass es nicht zu lösende Fehler gibt (obwohl es mehr als mit dem OCLIENT-Beispiel gibt). Die Fehler in der Reihenfolge, in der Sie normalerweise auftreten, werden unten beschrieben.

### <a name="compile-and-fix-errors"></a>Kompilieren und Beheben von Fehlern

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

Dieser erste Fehler weist auf ein viel größeres Problem mit der- `InitInstance` Funktion für-Server hin. Die für einen OLE-Server erforderliche Initialisierung ist wahrscheinlich eine der größten Änderungen, die Sie an ihrer MFC/OLE1-Anwendung vornehmen müssen, damit Sie ausgeführt werden kann. Das beste ist, zu sehen, was AppWizard für einen OLE-Server erstellt, und den Code nach Bedarf zu ändern. Hier sind einige Punkte zu beachten:

Es ist erforderlich, die OLE-Bibliotheken zu initialisieren, indem Sie aufrufen. `AfxOleInit`

Aufrufen von setserverinfo für das Dokumentvorlagen Objekt, um Server Ressourcen Handles und Lauf Zeit Klassen Informationen festzulegen, die nicht mit dem-Konstruktor festgelegt werden können `CDocTemplate` .

Zeigen Sie das Hauptfenster der Anwendung nicht an, wenn/Embedding in der Befehlszeile vorhanden ist.

Sie benötigen eine **GUID** für Ihr Dokument. Dies ist ein eindeutiger Bezeichner für den Dokumenttyp (128 Bits). Der AppWizard erstellt einen für Sie – wenn Sie also das hier beschriebene Verfahren zum Kopieren des neuen Codes aus einer neuen, vom AppWizard generierten Serveranwendung verwenden, können Sie einfach die GUID aus der Anwendung "stehlen". Wenn dies nicht der Wert ist, können Sie das GUIDGEN.EXE-Hilfsprogramm im bin-Verzeichnis verwenden.

Sie müssen `COleTemplateServer` das Objekt mit der Dokument Vorlage verbinden, indem Sie aufrufen `COleTemplateServer::ConnectTemplate` .

Aktualisieren Sie die Systemregistrierung, wenn Ihre Anwendung eigenständig ausgeführt wird. Dies ist der Fall, wenn der Benutzer den verschiebt. Die exe-Datei für Ihre Anwendung, die von Ihrem neuen Speicherort ausgeführt wird, aktualisiert die Windows-System Registrierungsdatenbank, sodass Sie auf den neuen Speicherort verweist.

Nachdem alle diese Änderungen basierend auf dem, was von AppWizard für erstellt `InitInstance` wurde, angewendet wurden, `InitInstance` sollte die (und verwandte GUID) für HIERSVR wie folgt lauten:

```cpp
// this is the GUID for HIERSVR documents
static const GUID BASED_CODE clsid =
{ 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };

/////////////////////////////////////////////////////////////////////////////
// COLEServerApp initialization

BOOL COLEServerApp::InitInstance()
{
    // OLE 2 initialization
    if (!AfxOleInit())
    {
        AfxMessageBox("Initialization of the OLE failed!");
        return FALSE;
    }

    // Standard initialization
    LoadStdProfileSettings();   // Load standard INI file options

    // Register document templates
    CDocTemplate* pDocTemplate;
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,
        RUNTIME_CLASS(CServerDoc),
        RUNTIME_CLASS(CMDIChildWnd),
        RUNTIME_CLASS(CServerView));
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);
    AddDocTemplate(pDocTemplate);

    // create main MDI Frame window
    CMainFrame* pMainFrame = new CMainFrame;
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))
        return FALSE;
    m_pMainWnd = pMainFrame;

    SetDialogBkColor(); // gray look

    // enable file manager drag/drop and DDE Execute open
    m_pMainWnd->DragAcceptFiles();
    EnableShellOpen();

    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);
    COleTemplateServer::RegisterAll();

    // try to launch as an OLE server
    if (RunEmbedded())
    {
        // "short-circuit" initialization -- run as server!
        return TRUE;
    }
    m_server.UpdateRegistry();
    RegisterShellFileTypes();

    // not run as OLE server, so show the main window
    if (m_lpCmdLine[0] == '\0')
    {
        // create a new (empty) document
        OnFileNew();
    }
    else
    {
        // open an existing document
        OpenDocumentFile(m_lpCmdLine);
    }

    pMainFrame->ShowWindow(m_nCmdShow);
    pMainFrame->UpdateWindow();

    return TRUE;
}
```

Sie werden feststellen, dass der obige Code auf eine neue Ressourcen-ID verweist, IDR_HIERSVRTYPE_SRVR_EMB. Dies ist die Menü Ressource, die verwendet werden soll, wenn ein Dokument bearbeitet wird, das in einen anderen Container eingebettet ist. In MFC/OLE1 wurden die Menü Elemente, die für die Bearbeitung eines eingebetteten Elements spezifisch sind, dynamisch geändert. Wenn beim Bearbeiten eines eingebetteten Elements anstelle eines dateibasierten Dokuments eine ganz andere Menüstruktur verwendet wird, ist es viel einfacher, unterschiedliche Benutzeroberflächen für diese zwei separaten Modi bereitzustellen. Wie Sie später sehen werden, wird eine vollständig separate Menü Ressource verwendet, wenn ein eingebettetes Objekt direkt bearbeitet wird.

Um diese Ressource zu erstellen, laden Sie das Ressourcen Skript in Visual C++ und kopieren Sie die vorhandene IDR_HIERSVRTYPE Menü Ressource. Benennen Sie die neue Ressource in "IDR_HIERSVRTYPE_SRVR_EMB" um (Dies ist die gleiche Benennungs Konvention, die von AppWizard verwendet wird). Als nächstes ändern Sie "Datei speichern" in "Datei Update". ID_FILE_UPDATE die Befehls-ID. Ändern Sie auch "Datei speichern unter" in "Datei speichern unter". ID_FILE_SAVE_COPY_AS die Befehls-ID. Das Framework stellt die Implementierung beider Befehle bereit.

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

Es gibt eine Reihe von Fehlern, die sich aus der außer Kraft Setzung von ergeben `OnSetData` , da Sie sich auf den **OleStatus** -Typ bezieht. **OleStatus** war die Methode, mit der OLE1 Fehler zurückgegeben wurde. Dies wurde in " **HRESULT** " in OLE 2 geändert, obwohl MFC in der Regel ein **HRESULT** in einen-Wert konvertiert, `COleException` der den Fehler enthält. In diesem speziellen Fall ist die außer Kraft `OnSetData` Setzung von nicht mehr erforderlich, daher ist es am einfachsten, Sie zu entfernen.

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

Der `COleServerItem` Konstruktor nimmt einen zusätzlichen "bool"-Parameter an. Dieses Flag bestimmt, wie die Speicherverwaltung für die `COleServerItem` Objekte erfolgt. Wenn Sie diese Einstellung auf "true" festlegen, verarbeitet das Framework die Speicherverwaltung dieser Objekte – Sie wird gelöscht, wenn Sie nicht mehr benötigt werden. HIERSVR verwendet `CServerItem` (abgeleitet von `COleServerItem` ) Objekten als Teil der systemeigenen Daten, daher legen Sie dieses Flag auf false fest. Hierdurch kann HIERSVR ermitteln, wann die einzelnen Server Elemente gelöscht werden.

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

Da diese Fehler impliziert sind, gibt es einige "Pure-Virtual"-Funktionen, die in "CServerItem" nicht überschrieben wurden. Höchstwahrscheinlich wird dies durch die Tatsache verursacht, dass die Parameterliste von OnDraw geändert wurde. Um diesen Fehler zu beheben, ändern Sie `CServerItem::OnDraw` wie folgt (und die Deklaration in svritem. h):

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

Der neue Parameter ist "rsize". Dies ermöglicht es Ihnen, die Größe der Zeichnung einzugeben, wenn dies bequem ist. Diese Größe muss in **HIMETRIC**liegen. In diesem Fall ist es nicht praktisch, diesen Wert in auszufüllen, sodass das Framework aufruft, `OnGetExtent` um den Block abzurufen. Damit dies funktioniert, müssen Sie Folgendes implementieren `OnGetExtent` :

```cpp
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)
{
    if (dwDrawAspect != DVASPECT_CONTENT)
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);

    rSize = CalcNodeSize();
    return TRUE;
}
```

```Output
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'
```

In der CServerItem:: calcnodesize-Funktion wird die Elementgröße in **HIMETRIC** konvertiert und in *m_rectBounds*gespeichert. Der nicht dokumentierte '*m_rectBounds*'-Member von ist `COleServerItem` nicht vorhanden (er wurde teilweise durch *m_sizeExtent*ersetzt, aber in OLE 2 hat dieser Member eine etwas andere Verwendung als *m_rectBounds* in OLE1). Anstatt die **himetrikgröße** in diese Member-Variable festzulegen, geben Sie Sie zurück. Dieser Rückgabewert wird in `OnGetExtent` , zuvor implementiert, verwendet.

```cpp
CSize CServerItem::CalcNodeSize()
{
    CClientDC dcScreen(NULL);

    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,
        m_strDescription.GetLength());
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);

    // set suggested HIMETRIC size
    CSize size(m_sizeNode.cx, m_sizeNode.cy);
    dcScreen.SetMapMode(MM_HIMETRIC);
    dcScreen.DPtoLP(&size);
    return size;
}
```

CServerItem überschreibt ebenfalls `COleServerItem::OnGetTextData` . Diese Funktion ist in MFC/OLE veraltet und wird durch einen anderen Mechanismus ersetzt. Die MFC 3,0-Version des MFC-OLE-Beispiel [Hierarchien](../overview/visual-cpp-samples.md) implementiert diese Funktionalität durch Überschreiben von `COleServerItem::OnRenderFileData` . Diese Funktion ist für diesen Basisport nicht wichtig, sodass Sie die ongettextdata-außer Kraft Setzung entfernen können.

Es gibt noch viele weitere Fehler in "svritem. cpp", die nicht behandelt wurden. Sie sind keine "echten" Fehler – sondern nur Fehler, die durch vorherige Fehler verursacht wurden.

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` unterstützt das- `bIncludeNative` Flag nicht mehr. Die nativen Daten (die von der Serialisierungsfunktion des Server Elements geschriebenen Daten) werden immer kopiert, sodass Sie den ersten Parameter entfernen. Außerdem löst `CopyToClipboard` eine Ausnahme aus, wenn ein Fehler auftritt, anstatt false zurückzugeben. Ändern Sie den Code für CServerView:: oneditcopy wie folgt:

```cpp
void CServerView::OnEditCopy()
{
    if (m_pSelectedNode == NULL)
        AfxThrowNotSupportedException();

    TRY
    {
        m_pSelectedNode->CopyToClipboard(TRUE);
    }
    CATCH_ALL(e)
    {
        AfxMessageBox("Copy to clipboard failed");
    }
    END_CATCH_ALL
}
```

Obwohl es mehr Fehler gab, die sich aus der Kompilierung der MFC 2,0-Version von Hierarchien ergeben, als für dieselbe Version von OCLIENT vorhanden waren, waren tatsächlich weniger Änderungen vorhanden.

An diesem Punkt werden Hierarchien und Verknüpfungen als OLE-Server kompiliert und als OLE-Server verwendet, aber ohne das direkte Bearbeitungs Feature, das als Nächstes implementiert wird.

### <a name="adding-visual-editing"></a>Hinzufügen der visuellen Bearbeitung

Zum Hinzufügen der "visuellen Bearbeitung" (oder der direkten Aktivierung) zu dieser Serveranwendung müssen Sie nur einige Dinge erledigen:

- Sie benötigen eine spezielle Menü Ressource, die verwendet werden soll, wenn das Element direkt aktiv ist.

- Diese Anwendung verfügt über eine Symbolleiste, sodass Sie eine Symbolleiste mit nur einer Teilmenge der normalen Symbolleiste benötigen, damit Sie mit den Menübefehlen übereinstimmen, die auf dem Server verfügbar sind (entspricht der oben erwähnten Menü Ressource).

- Sie benötigen eine neue, von abgeleitete Klasse `COleIPFrameWnd` , die die direkte Benutzeroberfläche bereitstellt (ähnlich wie CMainFrame, abgeleitet von `CMDIFrameWnd` , stellt die MDI-Benutzeroberfläche bereit).

- Sie müssen das Framework über diese besonderen Ressourcen und Klassen informieren.

Die Menü Ressource kann leicht erstellt werden. Führen Sie Visual C++ aus, und kopieren Sie die Menü Ressource IDR_HIERSVRTYPE in eine Menü Ressource mit dem Namen IDR_HIERSVRTYPE_SRVR_IP. Ändern Sie das Menü, sodass nur die Popups "Bearbeiten" und "Hilfe" verbleiben. Fügen Sie dem Menü zwischen den Menüs "Bearbeiten" und "Hilfe" zwei Trennzeichen hinzu (es sollte wie folgt aussehen: Edit &#124;&#124; Help). Weitere Informationen dazu, was diese Trennzeichen bedeuten und wie die Server-und Container Menüs zusammengeführt werden, finden Sie unter [Menüs und Ressourcen:](../mfc/menus-and-resources-menu-merging.md)Zusammenführen von Menüs.

Die Bitmap für die Teilmengen-Symbolleiste kann leicht erstellt werden, indem Sie die Schaltflächen aus einer neuen, von AppWizard generierten Anwendung mit aktivierter Option "Server" kopieren. Diese Bitmap kann dann in Visual C++ importiert werden. Stellen Sie sicher, dass Sie der Bitmap eine ID IDR_HIERSVRTYPE_SRVR_IP geben.

Die von abgeleitete Klasse `COleIPFrameWnd` kann auch von einer von AppWizard generierten Anwendung mit Serverunterstützung kopiert werden. Kopieren Sie beide Dateien, IpFrame. Cpp und IpFrame. H, und fügen Sie Sie dem Projekt hinzu. Stellen Sie sicher, dass der- `LoadBitmap` Rückruf auf IDR_HIERSVRTYPE_SRVR_IP verweist, die im vorherigen Schritt erstellte Bitmap.

Nachdem Sie alle neuen Ressourcen und Klassen erstellt haben, fügen Sie den erforderlichen Code hinzu, damit das Framework diese Informationen kennt (und weiß, dass diese Anwendung jetzt direkte Bearbeitung unterstützt). Dies erfolgt durch Hinzufügen von weiteren Parametern zum-Befehl `SetServerInfo` in der- `InitInstance` Funktion:

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

Sie kann jetzt direkt in jedem Container ausgeführt werden, der auch die direkte Aktivierung unterstützt. Aber es gibt einen kleinen Fehler, der im Code noch immer noch vorhanden ist. HIERSVR unterstützt ein Kontextmenü, das angezeigt wird, wenn der Benutzer die Rechte Maustaste drückt. Dieses Menü funktioniert, wenn Hierarchien vollständig geöffnet ist, aber nicht funktioniert, wenn eine Einbettung direkt bearbeitet wird. Der Grund kann an diese einzelne Codezeile in CServerView:: onrbuttondown angeheftet werden:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

Beachten Sie den Verweis auf `AfxGetApp()->m_pMainWnd` . Wenn der Server direkt aktiviert ist, verfügt er über ein Hauptfenster und m_pMainWnd festgelegt ist, ist aber normalerweise unsichtbar. Außerdem verweist dieses Fenster auf das *Haupt* Fenster der Anwendung, das MDI-Rahmen Fenster, das angezeigt wird, wenn der Server vollständig geöffnet ist oder eigenständig ausgeführt wird. Er verweist nicht auf das aktive Rahmen Fenster – das, wenn direkt aktiviert ein Rahmen Fenster ist, das von abgeleitet wird `COleIPFrameWnd` . Um das richtige aktive Fenster selbst bei der direkten Bearbeitung zu erhalten, fügt diese MFC-Version eine neue Funktion,, hinzu `AfxGetMainWnd` . Im Allgemeinen sollten Sie diese Funktion anstelle von verwenden `AfxGetApp()->m_pMainWnd` . Dieser Code muss wie folgt geändert werden:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

Nun verfügen Sie über einen OLE-Server, der für die funktionale direkte Aktivierung minimal aktiviert ist. Es sind jedoch noch viele Features in MFC/OLE 2 verfügbar, die in MFC/OLE1 nicht verfügbar waren. Weitere Ideen zu den Funktionen, die Sie möglicherweise implementieren möchten, finden Sie im Hierarchie Beispiel. Einige der Funktionen, die von Hierarchien implementiert werden, sind im folgenden aufgeführt:

- Zoom für das echte WYSIWYG-Verhalten in Bezug auf den Container.

- Drag & Drop und ein benutzerdefiniertes Zwischenablage Format.

- Scrollen des Container Fensters, wenn die Auswahl geändert wird.

Das Hierarchie Beispiel in MFC 3,0 verwendet auch einen etwas anderen Entwurf für seine Server Elemente. Dadurch wird der Arbeitsspeicher gespart, und ihre Verknüpfungen können flexibler werden. Bei Version 2,0 von Hierarchien ist jeder Knoten in der Struktur *-a* `COleServerItem` . `COleServerItem` erfordert etwas mehr Aufwand als für jeden dieser Knoten unbedingt erforderlich ist, aber `COleServerItem` für jeden aktiven Link ist ein erforderlich. Allerdings sind zu jedem Zeitpunkt nur sehr wenige aktive Links vorhanden. Um dies effizienter zu gestalten, trennt die Hierarchien in dieser MFC-Version den Knoten von `COleServerItem` . Sie verfügt sowohl über einen CServerNode als auch über eine- `CServerItem` Klasse. Der `CServerItem` (abgeleitet von `COleServerItem` ) wird nur bei Bedarf erstellt. Sobald der Container (oder die Container) die Verwendung dieser speziellen Verknüpfung zu diesem bestimmten Knoten beendet hat, wird das CServerItem-Objekt, das dem CServerNode zugeordnet ist, gelöscht. Dieser Entwurf ist effizienter und flexibler. Die Flexibilität tritt beim Umgang mit mehreren Auswahl Links ein. Keines dieser beiden Versionen von Hierarchien unterstützt Mehrfachauswahl, aber es ist viel einfacher, Links zu dieser Auswahl mit der MFC 3,0-Version von HIERSVR hinzuzufügen (und zu unterstützen), da der `COleServerItem` von den nativen Daten getrennt ist.

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise nach Zahl](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise nach Kategorie](../mfc/technical-notes-by-category.md)
