---
title: COleDocument-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDocument
- AFXOLE/COleDocument
- AFXOLE/COleDocument::COleDocument
- AFXOLE/COleDocument::AddItem
- AFXOLE/COleDocument::ApplyPrintDevice
- AFXOLE/COleDocument::EnableCompoundFile
- AFXOLE/COleDocument::GetInPlaceActiveItem
- AFXOLE/COleDocument::GetNextClientItem
- AFXOLE/COleDocument::GetNextItem
- AFXOLE/COleDocument::GetNextServerItem
- AFXOLE/COleDocument::GetPrimarySelectedItem
- AFXOLE/COleDocument::GetStartPosition
- AFXOLE/COleDocument::HasBlankItems
- AFXOLE/COleDocument::OnShowViews
- AFXOLE/COleDocument::RemoveItem
- AFXOLE/COleDocument::UpdateModifiedFlag
- AFXOLE/COleDocument::OnEditChangeIcon
- AFXOLE/COleDocument::OnEditConvert
- AFXOLE/COleDocument::OnEditLinks
- AFXOLE/COleDocument::OnFileSendMail
- AFXOLE/COleDocument::OnUpdateEditChangeIcon
- AFXOLE/COleDocument::OnUpdateEditLinksMenu
- AFXOLE/COleDocument::OnUpdateObjectVerbMenu
- AFXOLE/COleDocument::OnUpdatePasteLinkMenu
- AFXOLE/COleDocument::OnUpdatePasteMenu
helpviewer_keywords:
- COleDocument [MFC], COleDocument
- COleDocument [MFC], AddItem
- COleDocument [MFC], ApplyPrintDevice
- COleDocument [MFC], EnableCompoundFile
- COleDocument [MFC], GetInPlaceActiveItem
- COleDocument [MFC], GetNextClientItem
- COleDocument [MFC], GetNextItem
- COleDocument [MFC], GetNextServerItem
- COleDocument [MFC], GetPrimarySelectedItem
- COleDocument [MFC], GetStartPosition
- COleDocument [MFC], HasBlankItems
- COleDocument [MFC], OnShowViews
- COleDocument [MFC], RemoveItem
- COleDocument [MFC], UpdateModifiedFlag
- COleDocument [MFC], OnEditChangeIcon
- COleDocument [MFC], OnEditConvert
- COleDocument [MFC], OnEditLinks
- COleDocument [MFC], OnFileSendMail
- COleDocument [MFC], OnUpdateEditChangeIcon
- COleDocument [MFC], OnUpdateEditLinksMenu
- COleDocument [MFC], OnUpdateObjectVerbMenu
- COleDocument [MFC], OnUpdatePasteLinkMenu
- COleDocument [MFC], OnUpdatePasteMenu
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
ms.openlocfilehash: 1500035cb8be3036678090918154829aace48d2f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753878"
---
# <a name="coledocument-class"></a>COleDocument-Klasse

Die Basisklasse für OLE-Dokumente, die visuelle Bearbeitung unterstützen.

## <a name="syntax"></a>Syntax

```
class COleDocument : public CDocument
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDocument::COleDocument](#coledocument)|Erstellt ein `COleDocument`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDocument::AddItem](#additem)|Fügt der Liste der vom Dokument verwalteten Elemente ein Element hinzu.|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Legt das Druckzielgerät für alle Clientelemente im Dokument fest.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Bewirkt, dass Dokumente im OLE Structured Storage-Dateiformat gespeichert werden.|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Gibt das OLE-Element zurück, das derzeit aktiv ist.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Ruft das nächste Clientelement zum Iterieren ab.|
|[COleDocument::GetNextItem](#getnextitem)|Ruft das nächste Dokumentelement zum Iterieren ab.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Ruft das nächste Serverelement zum Iterieren ab.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Gibt das primäre ausgewählte OLE-Element im Dokument zurück.|
|[COleDocument::GetStartPosition](#getstartposition)|Ruft die Anfangsposition ab, um mit der Iteration zu beginnen.|
|[COleDocument::HasBlankItems](#hasblankitems)|Sucht nach leeren Elementen im Dokument.|
|[COleDocument::OnShowViews](#onshowviews)|Wird aufgerufen, wenn das Dokument sichtbar oder unsichtbar wird.|
|[COleDocument::RemoveItem](#removeitem)|Entfernt ein Element aus der Liste der Elemente, die vom Dokument verwaltet werden.|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Markiert das Dokument als geändert, wenn eines der enthaltenen OLE-Elemente geändert wurde.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Behandelt Ereignisse im Menübefehl Symbol ändern.|
|[COleDocument::OnEditConvert](#oneditconvert)|Behandelt die Konvertierung eines eingebetteten oder verknüpften Objekts von einem Typ in einen anderen.|
|[COleDocument::OnEditLinks](#oneditlinks)|Behandelt Ereignisse im Befehl Links im Menü Bearbeiten.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Sendet eine E-Mail-Nachricht mit dem angehängten Dokument.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Wird vom Framework aufgerufen, um die Befehlsbenutzeroberfläche für die Menüoption Symbol bearbeiten/ändern zu aktualisieren.|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Wird vom Framework aufgerufen, um die Befehlsbenutzeroberfläche für die Menüoption Bearbeiten/Links zu aktualisieren.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Wird vom Framework aufgerufen, um die Befehlsbenutzeroberfläche für die Menüoption *Bearbeiten/Objektname* und das Verb-Untermenü, auf das von Edit/ *ObjectName*zugegriffen wird, zu aktualisieren.|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Wird vom Framework aufgerufen, um die Befehlsbenutzeroberfläche für die Menüoption "Spezial einfügen" zu aktualisieren.|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Wird vom Framework aufgerufen, um die Befehlsbenutzeroberfläche für die Menüoption Einfügen zu aktualisieren.|

## <a name="remarks"></a>Bemerkungen

`COleDocument`wird von `CDocument`abgeleitet, wodurch Ihre OLE-Anwendungen die Dokument-/Ansichtsarchitektur verwenden können, die von der Microsoft Foundation-Klassenbibliothek bereitgestellt wird.

`COleDocument`behandelt ein Dokument als eine Auflistung von [CDocItem-Objekten](../../mfc/reference/cdocitem-class.md) zum Behandeln von OLE-Elementen. Sowohl Container- als auch Serveranwendungen erfordern eine solche Architektur, da ihre Dokumente OLE-Elemente enthalten können müssen. Die [Klassen COleServerItem](../../mfc/reference/coleserveritem-class.md) und [COleClientItem,](../../mfc/reference/coleclientitem-class.md) die beide von `CDocItem`abgeleitet sind, verwalten die Interaktionen zwischen Anwendungen und OLE-Elementen.

Wenn Sie eine einfache Containeranwendung schreiben, leiten `COleDocument`Sie Ihre Dokumentklasse von ab. Wenn Sie eine Containeranwendung schreiben, die die Verknüpfung mit den eingebetteten Elementen in den Dokumenten unterstützt, leiten Sie Ihre Dokumentklasse von [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)ab. Wenn Sie eine Serveranwendung oder eine Kombination von Container/Server schreiben, leiten Sie Ihre Dokumentklasse von [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)ab. `COleLinkingDoc`und `COleServerDoc` werden `COleDocument`von abgeleitet, so dass diese Klassen `COleDocument` `CDocument`alle in und verfügbaren Dienste erben.

Um `COleDocument`zu verwenden, leiten Sie daraus eine Klasse ab und fügen Sie Funktionen zum Verwalten der Nicht-OLE-Daten der Anwendung sowie eingebetteter oder verknüpfter Elemente hinzu. Wenn Sie `CDocItem`-abgeleitete Klassen definieren, um die systemeigenen Daten der `COleDocument` Anwendung zu speichern, können Sie die von Ihnen definierte Standardimplementierung verwenden, um sowohl Ihre OLE- als auch Ihre Nicht-OLE-Daten zu speichern. Sie können auch eigene Datenstrukturen entwerfen, um Ihre Nicht-OLE-Daten getrennt von den OLE-Elementen zu speichern. Weitere Informationen finden Sie im Artikel [Container: Zusammengesetzte Dateien](../../mfc/containers-compound-files.md)..

`CDocument`unterstützt das Versenden Ihres Dokuments per E-Mail, wenn E-Mail-Support (MAPI) vorhanden ist. `COleDocument`hat [OnFileSendMail](#onfilesendmail) aktualisiert, um zusammengesetzte Dokumente korrekt zu verarbeiten. Weitere Informationen finden Sie in den Artikeln [MAPI](../../mfc/mapi.md) und [MAPI Support in MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxole.h

## <a name="coledocumentadditem"></a><a name="additem"></a>COleDocument::AddItem

Rufen Sie diese Funktion auf, um dem Dokument ein Element hinzuzufügen.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeiger auf das hinzugefügte Dokumentelement.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Funktion nicht explizit aufrufen, `COleClientItem` wenn `COleServerItem` sie vom or-Konstruktor aufgerufen wird, der einen Zeiger auf ein Dokument akzeptiert.

## <a name="coledocumentapplyprintdevice"></a><a name="applyprintdevice"></a>COleDocument::ApplyPrintDevice

Rufen Sie diese Funktion auf, um das Druckzielgerät für alle eingebetteten [COleClientItem-Elemente](../../mfc/reference/coleclientitem-class.md) im Containerdokument Ihrer Anwendung zu ändern.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parameter

*Ptd*<br/>
Zeiger auf `DVTARGETDEVICE` eine Datenstruktur, die Informationen über das neue Druckzielgerät enthält. Kann den Wert NULL haben.

*Ppd*<br/>
Zeiger auf `PRINTDLG` eine Datenstruktur, die Informationen über das neue Druckzielgerät enthält. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion aktualisiert das Druckzielgerät für alle Elemente, aktualisiert jedoch nicht den Präsentationscache für diese Elemente. Um den Präsentationscache für ein Element zu aktualisieren, rufen Sie [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)auf.

Die Argumente für diese Funktion enthalten Informationen, die OLE zum Identifizieren des Zielgeräts verwendet. Die [PRINTDLG-Struktur](/windows/win32/api/commdlg/ns-commdlg-printdlga) enthält Informationen, die Windows zum Initialisieren des allgemeinen Dialogfelds Drucken verwendet. Nachdem der Benutzer das Dialogfeld geschlossen hat, gibt Windows Informationen über die Auswahl des Benutzers in dieser Struktur zurück. Das `m_pd` Element eines [CPrintDialog-Objekts](../../mfc/reference/cprintdialog-class.md) ist eine `PRINTDLG` Struktur.

Weitere Informationen finden Sie in der [PRINTDLG-Struktur](/windows/win32/api/commdlg/ns-commdlg-printdlga) im Windows SDK.

Weitere Informationen finden Sie in der [DVTARGETDEVICE-Struktur](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) im Windows SDK.

## <a name="coledocumentcoledocument"></a><a name="coledocument"></a>COleDocument::COleDocument

Erstellt ein `COleDocument`-Objekt.

```
COleDocument();
```

## <a name="coledocumentenablecompoundfile"></a><a name="enablecompoundfile"></a>COleDocument::EnableCompoundFile

Rufen Sie diese Funktion auf, wenn Sie das Dokument im Format der zusammengesetzten Datei speichern möchten.

```cpp
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
Gibt an, ob die Unterstützung zusammengesetzter Dateien aktiviert oder deaktiviert ist.

### <a name="remarks"></a>Bemerkungen

Dies wird auch als strukturierter Speicher bezeichnet. Normalerweise rufen Sie diese Funktion aus `COleDocument`dem Konstruktor Ihrer -derived-Klasse auf. Weitere Informationen zu zusammengesetzten Dokumenten finden Sie im Artikel [Container: Zusammengesetzte Dateien](../../mfc/containers-compound-files.md)..

Wenn Sie diese Memberfunktion nicht aufrufen, werden Dokumente in einem nicht strukturierten ("flachen") Dateiformat gespeichert.

Nachdem die Unterstützung für zusammengesetzte Dateien für ein Dokument aktiviert oder deaktiviert wurde, sollte die Einstellung während der Lebensdauer des Dokuments nicht geändert werden.

## <a name="coledocumentgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>COleDocument::GetInPlaceActiveItem

Rufen Sie diese Funktion auf, um das OLE-Element abzurufen, das derzeit im Rahmenfenster aktiviert ist und die von *pWnd*identifizierte Ansicht enthält.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, in dem das Containerdokument angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das einzelne, aktive OLE-Element; NULL, wenn sich derzeit kein OLE-Element im Status "in-place active" befindet.

## <a name="coledocumentgetnextclientitem"></a><a name="getnextclientitem"></a>COleDocument::GetNextClientItem

Rufen Sie diese Funktion wiederholt auf, um auf jedes der Clientelemente in Ihrem Dokument zuzugreifen.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Ein Verweis auf einen POSITION-Wert, `GetNextClientItem`der durch einen vorherigen Aufruf von festgelegt wurde; Der Anfangswert wird `GetStartPosition` von der Memberfunktion zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das nächste Clientelement im Dokument oder NULL, wenn keine weiteren Clientelemente vorhanden sind.

### <a name="remarks"></a>Bemerkungen

Nach jedem Aufruf wird der Wert von *pos* für das nächste Element im Dokument festgelegt, das möglicherweise ein Clientelement ist oder nicht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

## <a name="coledocumentgetnextitem"></a><a name="getnextitem"></a>COleDocument::GetNextItem

Rufen Sie diese Funktion wiederholt auf, um auf jedes Element in Ihrem Dokument zuzugreifen.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Ein Verweis auf einen POSITION-Wert, `GetNextItem`der durch einen vorherigen Aufruf von festgelegt wurde; Der Anfangswert wird `GetStartPosition` von der Memberfunktion zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Dokumentelement an der angegebenen Position.

### <a name="remarks"></a>Bemerkungen

Nach jedem Aufruf wird der Wert von *pos* auf den POSITION-Wert des nächsten Elements im Dokument festgelegt. Wenn das abgerufene Element das letzte Element im Dokument ist, ist der neue Wert von *pos* NULL.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

## <a name="coledocumentgetnextserveritem"></a><a name="getnextserveritem"></a>COleDocument::GetNextServerItem

Rufen Sie diese Funktion wiederholt auf, um auf jedes der Serverelemente in Ihrem Dokument zuzugreifen.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Ein Verweis auf einen POSITION-Wert, `GetNextServerItem`der durch einen vorherigen Aufruf von festgelegt wurde; Der Anfangswert wird `GetStartPosition` von der Memberfunktion zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das nächste Serverelement im Dokument oder NULL, wenn keine Serverelemente mehr vorhanden sind.

### <a name="remarks"></a>Bemerkungen

Nach jedem Aufruf wird der Wert von *pos* für das nächste Element im Dokument festgelegt, das möglicherweise ein Serverelement ist oder nicht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

## <a name="coledocumentgetprimaryselecteditem"></a><a name="getprimaryselecteditem"></a>COleDocument::GetPrimarySelectedItem

Wird vom Framework aufgerufen, um das aktuell ausgewählte OLE-Element in der angegebenen Ansicht abzurufen.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parameter

*Pview*<br/>
Zeigen Sie mit dem Zeiger auf das aktive Ansichtsobjekt, das das Dokument anzeigt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das einzelne, ausgewählte OLE-Element; NULL, wenn keine OLE-Elemente ausgewählt sind oder wenn mehr als eins ausgewählt ist.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung durchsucht die Liste der enthaltenen OLE-Elemente nach einem einzelnen ausgewählten Element und gibt einen Zeiger darauf zurück. Wenn kein Element ausgewählt ist oder mehr als ein Element ausgewählt ist, gibt die Funktion NULL zurück. Sie müssen die `CView::IsSelected` Memberfunktion in Ihrer Ansichtsklasse überschreiben, damit diese Funktion funktioniert. Überschreiben Sie diese Funktion, wenn Sie über eine eigene Methode zum Speichern enthaltener OLE-Elemente verfügen.

## <a name="coledocumentgetstartposition"></a><a name="getstartposition"></a>COleDocument::GetStartPosition

Rufen Sie diese Funktion auf, um die Position des ersten Elements im Dokument abzurufen.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der verwendet werden kann, um mit der Iterierung durch die Elemente des Dokuments zu beginnen; NULL, wenn das Dokument keine Elemente enthält.

### <a name="remarks"></a>Bemerkungen

Übergeben Sie den `GetNextItem` `GetNextClientItem`zurückgegebenen `GetNextServerItem`Wert an , oder .

## <a name="coledocumenthasblankitems"></a><a name="hasblankitems"></a>COleDocument::HasBlankItems

Rufen Sie diese Funktion auf, um zu bestimmen, ob das Dokument leere Elemente enthält.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dokument leere Elemente enthält; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein leeres Element ist ein Element, dessen Rechteck leer ist.

## <a name="coledocumentoneditchangeicon"></a><a name="oneditchangeicon"></a>COleDocument::OnEditChangeIcon

Zeigt das Dialogfeld OLE-Änderungssymbol an und ändert das Symbol, das das aktuell ausgewählte OLE-Element darstellt, in das Symbol, das der Benutzer im Dialogfeld auswählt.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Bemerkungen

`OnEditChangeIcon`erstellt und startet `COleChangeIconDialog` ein Dialogfeld Symbol ändern.

## <a name="coledocumentoneditconvert"></a><a name="oneditconvert"></a>COleDocument::OnEditConvert

Zeigt das Dialogfeld OLE Konvertieren an und konvertiert oder aktiviert das aktuell ausgewählte OLE-Element entsprechend der Benutzerauswahl im Dialogfeld.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Bemerkungen

`OnEditConvert`erstellt und startet `COleConvertDialog` ein Dialogfeld Konvertieren.

Ein Beispiel für die Konvertierung ist das Konvertieren eines Microsoft Word-Dokuments in ein WordPad-Dokument.

## <a name="coledocumentoneditlinks"></a><a name="oneditlinks"></a>COleDocument::OnEditLinks

Zeigt das Dialogfeld OLE Bearbeiten/Links an.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Bemerkungen

`OnEditLinks`erstellt und startet `COleLinksDialog` ein Dialogfeld Links, in dem der Benutzer die verknüpften Objekte ändern kann.

## <a name="coledocumentonfilesendmail"></a><a name="onfilesendmail"></a>COleDocument::OnFileSendMail

Sendet eine Nachricht über den residenten E-Mail-Host (falls vorhanden) mit dem Dokument als Anlage.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Bemerkungen

`OnFileSendMail`Aufrufe `OnSaveDocument` zum Serialisieren (Speichern) von unbenannten und geänderten Dokumenten in eine temporäre Datei, die dann per E-Mail gesendet wird. Wenn das Dokument nicht geändert wurde, wird keine temporäre Datei benötigt. das Original gesendet wird. `OnFileSendMail`lädt MAPI32. DLL, wenn sie noch nicht geladen wurde.

Im Gegensatz `OnFileSendMail` zur `CDocument`Implementierung von für verarbeitet diese Funktion zusammengesetzte Dateien korrekt.

Weitere Informationen finden Sie in den [MapI-Themen](../../mfc/mapi.md) und [mapI-Support in MFC-Artikeln.](../../mfc/mapi-support-in-mfc.md)

## <a name="coledocumentonshowviews"></a><a name="onshowviews"></a>COleDocument::OnShowViews

Das Framework ruft diese Funktion auf, nachdem sich der Sichtbarkeitsstatus des Dokuments geändert hat.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parameter

*bVisible*<br/>
Gibt an, ob das Dokument sichtbar oder unsichtbar geworden ist.

### <a name="remarks"></a>Bemerkungen

Die Standardversion dieser Funktion bewirkt nichts. Überschreiben Sie es, wenn Ihre Anwendung eine spezielle Verarbeitung durchführen muss, wenn sich die Sichtbarkeit des Dokuments ändert.

## <a name="coledocumentonupdateeditchangeicon"></a><a name="onupdateeditchangeicon"></a>COleDocument::OnUpdateEditChangeIcon

Wird vom Framework aufgerufen, um den Befehl Symbol ändern im Menü Bearbeiten zu aktualisieren.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf `CCmdUI` eine Struktur, die das Menü darstellt, das den Aktualisierungsbefehl generiert hat. Der Updatehandler `Enable` ruft die `CCmdUI` Memberfunktion der Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Bemerkungen

`OnUpdateEditChangeIcon`aktualisiert die Benutzeroberfläche des Befehls, je nachdem, ob im Dokument ein gültiges Symbol vorhanden ist oder nicht. Überschreiben Sie diese Funktion, um das Verhalten zu ändern.

## <a name="coledocumentonupdateeditlinksmenu"></a><a name="onupdateeditlinksmenu"></a>COleDocument::OnUpdateEditLinksMenu

Wird vom Framework aufgerufen, um den Befehl Links im Menü Bearbeiten zu aktualisieren.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf `CCmdUI` eine Struktur, die das Menü darstellt, das den Aktualisierungsbefehl generiert hat. Der Updatehandler `Enable` ruft die `CCmdUI` Memberfunktion der Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Bemerkungen

Beginnend mit dem ersten OLE-Element im Dokument greift `OnUpdateEditLinksMenu` jedes Element zu, testet, ob es sich bei dem Element um eine Verknüpfung handelt, und aktiviert, wenn es sich um eine Verknüpfung handelt, den Befehl Links. Überschreiben Sie diese Funktion, um das Verhalten zu ändern.

## <a name="coledocumentonupdateobjectverbmenu"></a><a name="onupdateobjectverbmenu"></a>COleDocument::OnUpdateObjectVerbMenu

Wird vom Framework aufgerufen, um den *ObjectName-Befehl* im Menü Bearbeiten und das Verb-Untermenü, auf das über den *Befehl ObjectName* zugegriffen wird, zu aktualisieren, wobei *ObjectName* der Name des ole-Objekts ist, das in das Dokument eingebettet ist.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf `CCmdUI` eine Struktur, die das Menü darstellt, das den Aktualisierungsbefehl generiert hat. Der Updatehandler `Enable` ruft die `CCmdUI` Memberfunktion der Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Bemerkungen

`OnUpdateObjectVerbMenu`aktualisiert *ObjectName* die Benutzeroberfläche des ObjectName-Befehls, je nachdem, ob ein gültiges Objekt im Dokument vorhanden ist oder nicht. Wenn ein Objekt vorhanden ist, ist der *ObjectName-Befehl* im Menü Bearbeiten aktiviert. Wenn dieser Menübefehl ausgewählt ist, wird das Untermenü Verb angezeigt. Das Untermenü Verb enthält alle Verbbefehle, die für das Objekt verfügbar sind, z. B. Bearbeiten, Eigenschaften usw. Überschreiben Sie diese Funktion, um das Verhalten zu ändern.

## <a name="coledocumentonupdatepastelinkmenu"></a><a name="onupdatepastelinkmenu"></a>COleDocument::OnUpdatePasteLinkMenu

Wird vom Framework aufgerufen, um zu bestimmen, ob ein verknüpftes OLE-Element aus der Zwischenablage eingefügt werden kann.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf `CCmdUI` eine Struktur, die das Menü darstellt, das den Aktualisierungsbefehl generiert hat. Der Updatehandler `Enable` ruft die `CCmdUI` Memberfunktion der Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Bemerkungen

Der Menübefehl "Spezial einfügen" ist aktiviert oder deaktiviert, je nachdem, ob das Element in das Dokument eingefügt werden kann oder nicht.

## <a name="coledocumentonupdatepastemenu"></a><a name="onupdatepastemenu"></a>COleDocument::OnUpdatePasteMenu

Wird vom Framework aufgerufen, um zu bestimmen, ob ein eingebettetes OLE-Element aus der Zwischenablage eingefügt werden kann.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf `CCmdUI` eine Struktur, die das Menü darstellt, das den Aktualisierungsbefehl generiert hat. Der Updatehandler `Enable` ruft die `CCmdUI` Memberfunktion der Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Bemerkungen

Der Menübefehl und die Schaltfläche Menü einfügen sind aktiviert oder deaktiviert, je nachdem, ob das Element in das Dokument eingefügt werden kann oder nicht.

## <a name="coledocumentremoveitem"></a><a name="removeitem"></a>COleDocument::RemoveItem

Rufen Sie diese Funktion auf, um ein Element aus dem Dokument zu entfernen.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeigen Sie auf das zu entfernende Dokumentelement.

### <a name="remarks"></a>Bemerkungen

In der Regel müssen Sie diese Funktion nicht explizit aufrufen. es wird von den Destruktoren für `COleClientItem` und `COleServerItem`aufgerufen.

## <a name="coledocumentupdatemodifiedflag"></a><a name="updatemodifiedflag"></a>COleDocument::UpdateModifiedFlag

Rufen Sie diese Funktion auf, um das Dokument als geändert zu markieren, wenn eines der enthaltenen OLE-Elemente geändert wurde.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Bemerkungen

Auf diese Weise kann das Framework den Benutzer auffordern, das Dokument vor dem Schließen zu speichern, auch wenn die systemeigenen Daten im Dokument nicht geändert wurden.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CONTAINER](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument-Klasse](../../mfc/reference/cdocument-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
