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
ms.openlocfilehash: b92c796fdaa972966dcbfa85b1e34f267b6c629c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426492"
---
# <a name="coledocument-class"></a>COleDocument-Klasse

Die Basisklasse für OLE-Dokumente, die visuelle Bearbeitung unterstützen.

## <a name="syntax"></a>Syntax

```
class COleDocument : public CDocument
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[COleDocument:: COleDocument](#coledocument)|Erstellt ein `COleDocument`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COleDocument:: AddItem](#additem)|Fügt der Liste der Elemente, die vom Dokument verwaltet werden, ein Element hinzu.|
|[COleDocument:: applyprintdevice](#applyprintdevice)|Legt das Druck Zielgerät für alle Client Elemente im Dokument fest.|
|[COleDocument:: EnableCompoundFile](#enablecompoundfile)|Bewirkt, dass Dokumente mit dem OLE-strukturierten Speicherdatei Format gespeichert werden.|
|[COleDocument:: getinplaceactiveitem](#getinplaceactiveitem)|Gibt das OLE-Element zurück, das derzeit aktiv ist.|
|[COleDocument:: getnextclientitem](#getnextclientitem)|Ruft das nächste Client Element für die Iteration ab.|
|[COleDocument:: GetNextItem](#getnextitem)|Ruft das nächste Dokument Element für die Iteration ab.|
|[COleDocument:: getnextserveritem](#getnextserveritem)|Ruft das nächste Server Element für die Iteration ab.|
|[COleDocument:: getprimaryselecteditem](#getprimaryselecteditem)|Gibt das primäre ausgewählte OLE-Element im Dokument zurück.|
|[COleDocument:: GetStartPosition](#getstartposition)|Ruft die Anfangsposition ab, an der die Iterationen beginnen soll.|
|[COleDocument:: hasblankitems](#hasblankitems)|Prüft, ob leere Elemente im Dokument enthalten sind.|
|[COleDocument:: onshowviews](#onshowviews)|Wird aufgerufen, wenn das Dokument sichtbar oder unsichtbar wird.|
|[COleDocument:: RemoveItem](#removeitem)|Entfernt ein Element aus der Liste der Elemente, die vom Dokument verwaltet werden.|
|[COleDocument:: updatemodifiedflag](#updatemodifiedflag)|Markiert das Dokument als geändert, wenn eines der enthaltenen OLE-Elemente geändert wurde.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COleDocument:: oneditchangeicon](#oneditchangeicon)|Behandelt Ereignisse im Menübefehl zum Ändern des Symbols.|
|[COleDocument:: oneditconvert](#oneditconvert)|Behandelt die Konvertierung eines eingebetteten oder verknüpften Objekts von einem Typ in einen anderen.|
|[COleDocument:: oneditlinks](#oneditlinks)|Behandelt Ereignisse im Befehl "Links" im Menü "Bearbeiten".|
|[COleDocument:: OnFileSendMail](#onfilesendmail)|Sendet eine e-Mail-Nachricht mit angefügtem Dokument.|
|[COleDocument:: onupdateeditchangeicon](#onupdateeditchangeicon)|Wird von Framework aufgerufen, um die Befehls Benutzeroberfläche für die Menüoption "Symbol bearbeiten/ändern" zu aktualisieren.|
|[COleDocument:: onupdateeditlinksmenu](#onupdateeditlinksmenu)|Wird von Framework aufgerufen, um die Befehls Benutzeroberfläche für die Menüoption "Bearbeiten/Links" zu aktualisieren.|
|[COleDocument:: onupdateobjectverbmenu](#onupdateobjectverbmenu)|Wird von Framework aufgerufen, um die Befehls Benutzeroberfläche für die Menüoption Bearbeiten/ *objectName* und das Untermenü Verb zu aktualisieren, auf das von "Edit/ *objectName*" zugegriffen wird.|
|[COleDocument:: onupdatepstelinkmenu](#onupdatepastelinkmenu)|Wird von Framework aufgerufen, um die Befehls Benutzeroberfläche für die Menüoption "Kontext einfügen" zu aktualisieren.|
|[COleDocument:: onupdatepastemenu](#onupdatepastemenu)|Wird von Framework aufgerufen, um die Befehls Benutzeroberfläche für die Menüoption "Einfügen" zu aktualisieren.|

## <a name="remarks"></a>Hinweise

`COleDocument` wird von `CDocument`abgeleitet, mit dem Ihre OLE-Anwendungen die vom Microsoft Foundation Class-Bibliothek bereitgestellte Dokument-/Ansichtarchitektur verwenden können.

`COleDocument` behandelt ein Dokument als eine Auflistung von [CDocItem](../../mfc/reference/cdocitem-class.md) -Objekten, um OLE-Elemente zu verarbeiten. Für Container-und Server Anwendungen ist eine solche Architektur erforderlich, da Ihre Dokumente OLE-Elemente enthalten müssen. Die Klassen [COleServerItem](../../mfc/reference/coleserveritem-class.md) und [COleClientItem](../../mfc/reference/coleclientitem-class.md) , die von `CDocItem`abgeleitet sind, verwalten die Interaktionen zwischen Anwendungen und OLE-Elementen.

Wenn Sie eine einfache Containeranwendung schreiben, leiten Sie die Dokument Klasse von `COleDocument`ab. Wenn Sie eine Containeranwendung schreiben, die das Verknüpfen mit den in den Dokumenten enthaltenen eingebetteten Elementen unterstützt, leiten Sie die Dokument Klasse von [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)ab. Wenn Sie eine Serveranwendung oder einen Kombinations Container/-Server schreiben, leiten Sie die Dokument Klasse von [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)ab. `COleLinkingDoc` und `COleServerDoc` werden aus `COleDocument`abgeleitet, sodass diese Klassen alle in `COleDocument` und `CDocument`verfügbaren Dienste erben.

Um `COleDocument`zu verwenden, leiten Sie eine Klasse davon ab, und fügen Sie Funktionen zum Verwalten der nicht-OLE-Daten der Anwendung sowie eingebetteter oder verknüpfter Elemente hinzu. Wenn Sie `CDocItem`von abgeleitete Klassen definieren, um die systemeigenen Daten der Anwendung zu speichern, können Sie die von `COleDocument` definierte Standard Implementierung verwenden, um sowohl OLE-als auch nicht-OLE-Daten zu speichern. Sie können auch eigene Datenstrukturen entwerfen, um Ihre nicht-OLE-Daten getrennt von den OLE-Elementen zu speichern. Weitere Informationen finden Sie im Artikel [Container: Verbund Dateien](../../mfc/containers-compound-files.md).

`CDocument` unterstützt das Senden Ihres Dokuments per e-Mail, wenn der e-Mail-Support (MAPI) vorhanden ist. `COleDocument` hat [OnFileSendMail](#onfilesendmail) aktualisiert, um zusammengesetzte Dokumente ordnungsgemäß zu verarbeiten. Weitere Informationen finden Sie in den Artikeln [MAPI](../../mfc/mapi.md) -und [MAPI-Unterstützung in MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Voraussetzungen

**Header:** Afxole. h

##  <a name="additem"></a>COleDocument:: AddItem

Mit dieser Funktion können Sie dem Dokument ein Element hinzufügen.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parameter

*pitem*<br/>
Zeiger auf das Dokument Element, das hinzugefügt wird.

### <a name="remarks"></a>Hinweise

Sie müssen diese Funktion nicht explizit aufrufen, wenn Sie vom `COleClientItem` oder `COleServerItem` Konstruktor aufgerufen wird, der einen Zeiger auf ein Dokument akzeptiert.

##  <a name="applyprintdevice"></a>COleDocument:: applyprintdevice

Mit dieser Funktion können Sie das druckzielgerät für alle eingebetteten [COleClientItem](../../mfc/reference/coleclientitem-class.md) -Elemente im Container Dokument Ihrer Anwendung ändern.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parameter

*ptd*<br/>
Zeiger auf eine `DVTARGETDEVICE` Datenstruktur, die Informationen über das neue druckzielgerät enthält. Kann NULL sein.

*PPD*<br/>
Zeiger auf eine `PRINTDLG` Datenstruktur, die Informationen über das neue druckzielgerät enthält. Kann NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Funktion erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion aktualisiert das druckzielgerät für alle Elemente, aktualisiert jedoch nicht den Präsentations Cache für diese Elemente. Um den Präsentations Cache für ein Element zu aktualisieren, müssen Sie [COleClientItem:: UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)aufrufen.

Die Argumente für diese Funktion enthalten Informationen, die von OLE verwendet werden, um das Zielgerät zu identifizieren. Die [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) -Struktur enthält Informationen, die Windows verwendet, um das Dialogfeld für den allgemeinen Druck zu initialisieren. Nachdem der Benutzer das Dialogfeld geschlossen hat, gibt Windows Informationen zur Auswahl des Benutzers in dieser Struktur zurück. Der `m_pd` Member eines [CPrintDialog](../../mfc/reference/cprintdialog-class.md) -Objekts ist eine `PRINTDLG` Struktur.

Weitere Informationen finden Sie in der [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) -Struktur in der Windows SDK.

Weitere Informationen finden Sie in der " [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) "-Struktur in der Windows SDK.

##  <a name="coledocument"></a>COleDocument:: COleDocument

Erstellt ein `COleDocument`-Objekt.

```
COleDocument();
```

##  <a name="enablecompoundfile"></a>COleDocument:: EnableCompoundFile

Diese Funktion wird aufgerufen, wenn Sie das Dokument mit dem Verbund Dateiformat speichern möchten.

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*benabel*<br/>
Gibt an, ob die Unterstützung von Verbund Dateien aktiviert oder deaktiviert ist.

### <a name="remarks"></a>Hinweise

Dies wird auch als strukturierter Speicher bezeichnet. Diese Funktion wird in der Regel vom Konstruktor Ihrer `COleDocument`abgeleiteten Klasse aufgerufen. Weitere Informationen zu Verbund Dokumenten finden Sie im Artikel [Container: Verbund Dateien](../../mfc/containers-compound-files.md).

Wenn Sie diese Member-Funktion nicht aufzurufen, werden Dokumente in einem nicht strukturierten Dateiformat ("Flat") gespeichert.

Nachdem die Unterstützung für Verbund Dateien für ein Dokument aktiviert oder deaktiviert wurde, sollte die Einstellung während der Lebensdauer des Dokuments nicht geändert werden.

##  <a name="getinplaceactiveitem"></a>COleDocument:: getinplaceactiveitem

Mit dieser Funktion können Sie das OLE-Element abrufen, das momentan im Rahmen Fenster mit der durch *pwnd*identifizierten Ansicht aktiviert ist.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Zeiger auf das Fenster, in dem das Container Dokument angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das einzelne, direkte aktive OLE-Element; NULL, wenn sich zurzeit kein OLE-Element im Zustand "direkt aktiv" befindet.

##  <a name="getnextclientitem"></a>COleDocument:: getnextclientitem

Diese Funktion wird wiederholt aufgerufen, um auf die einzelnen Client Elemente in Ihrem Dokument zuzugreifen.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*pos*<br/>
Ein Verweis auf einen Positionswert, der durch einen vorherigen-`GetNextClientItem`festgelegt wurde. der Anfangswert wird von der `GetStartPosition` Member-Funktion zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das nächste Client Element im Dokument oder NULL, wenn keine weiteren Client Elemente vorhanden sind.

### <a name="remarks"></a>Hinweise

Nach jedem-Aufrufwert wird der Wert von *POS* für das nächste Element im Dokument festgelegt, das möglicherweise kein Client Element ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

##  <a name="getnextitem"></a>COleDocument:: GetNextItem

Diese Funktion wird wiederholt aufgerufen, um auf die einzelnen Elemente im Dokument zuzugreifen.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*pos*<br/>
Ein Verweis auf einen Positionswert, der durch einen vorherigen-`GetNextItem`festgelegt wurde. der Anfangswert wird von der `GetStartPosition` Member-Funktion zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Dokument Element an der angegebenen Position.

### <a name="remarks"></a>Hinweise

Nach jedem-Rückruf wird der Wert von *POS* auf den Positionswert des nächsten Elements im Dokument festgelegt. Wenn das abgerufene Element das letzte Element im Dokument ist, ist der neue Wert von *POS* NULL.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

##  <a name="getnextserveritem"></a>COleDocument:: getnextserveritem

Diese Funktion wird wiederholt aufgerufen, um auf die einzelnen Server Elemente in Ihrem Dokument zuzugreifen.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*pos*<br/>
Ein Verweis auf einen Positionswert, der durch einen vorherigen-`GetNextServerItem`festgelegt wurde. der Anfangswert wird von der `GetStartPosition` Member-Funktion zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das nächste Server Element im Dokument oder NULL, wenn keine weiteren Server Elemente vorhanden sind.

### <a name="remarks"></a>Hinweise

Nach jedem-Aufrufwert wird der Wert von *POS* für das nächste Element im Dokument festgelegt, wobei es sich möglicherweise um ein Server Element handelt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

##  <a name="getprimaryselecteditem"></a>COleDocument:: getprimaryselecteditem

Wird von Framework aufgerufen, um das aktuell ausgewählte OLE-Element in der angegebenen Ansicht abzurufen.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parameter

*pView*<br/>
Zeiger auf das aktive Ansichts Objekt, in dem das Dokument angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das einzelne, ausgewählte OLE-Element. NULL, wenn keine OLE-Elemente ausgewählt sind oder wenn mehr als ein Element ausgewählt ist.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung durchsucht die Liste der enthaltenen OLE-Elemente nach einem einzelnen ausgewählten Element und gibt einen Zeiger darauf zurück. Wenn kein Element ausgewählt ist, oder wenn mehr als ein Element ausgewählt ist, gibt die Funktion NULL zurück. Sie müssen die `CView::IsSelected` Member-Funktion in der Ansichts Klasse überschreiben, damit diese Funktion funktioniert. Überschreiben Sie diese Funktion, wenn Sie eine eigene Methode zum Speichern enthaltener OLE-Elemente besitzen.

##  <a name="getstartposition"></a>COleDocument:: GetStartPosition

Mit dieser Funktion können Sie die Position des ersten Elements im Dokument abrufen.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der verwendet werden kann, um mit dem Durchlaufen der Dokument Elemente zu beginnen. NULL, wenn das Dokument keine Elemente enthält.

### <a name="remarks"></a>Hinweise

Übergeben Sie den zurückgegebenen Wert an `GetNextItem`, `GetNextClientItem`oder `GetNextServerItem`.

##  <a name="hasblankitems"></a>COleDocument:: hasblankitems

Diese Funktion wird aufgerufen, um zu bestimmen, ob das Dokument leere Elemente enthält.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn das Dokument leere Elemente enthält. andernfalls 0.

### <a name="remarks"></a>Hinweise

Ein leeres Element ist ein Element, dessen Rechteck leer ist.

##  <a name="oneditchangeicon"></a>COleDocument:: oneditchangeicon

Zeigt das Dialogfeld OLE-Änderungs Symbol an und ändert das Symbol, das das aktuell ausgewählte OLE-Element darstellt, in das Symbol, das der Benutzer im Dialogfeld auswählt.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Hinweise

`OnEditChangeIcon` erstellt und öffnet das Dialogfeld `COleChangeIconDialog` Symbol ändern.

##  <a name="oneditconvert"></a>COleDocument:: oneditconvert

Zeigt das Dialogfeld OLE Convert an und konvertiert oder aktiviert das aktuell ausgewählte OLE-Element entsprechend der Benutzer Auswahl im Dialogfeld.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Hinweise

`OnEditConvert` erstellt und öffnet das Dialogfeld `COleConvertDialog` konvertieren.

Ein Beispiel für die Konvertierung ist das Konvertieren eines Microsoft Word-Dokuments in ein WordPad-Dokument.

##  <a name="oneditlinks"></a>COleDocument:: oneditlinks

Zeigt das Dialogfeld OLE-Bearbeitung/-Links an.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Hinweise

`OnEditLinks` erstellt und öffnet ein Dialogfeld `COleLinksDialog` Links, das es dem Benutzer ermöglicht, die verknüpften Objekte zu ändern.

##  <a name="onfilesendmail"></a>COleDocument:: OnFileSendMail

Sendet eine Nachricht über den residenten Mailhost (sofern vorhanden) mit dem Dokument als Anlage.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Hinweise

`OnFileSendMail` wird `OnSaveDocument` aufgerufen, um unbenannte und geänderte Dokumente in eine temporäre Datei zu serialisieren (speichern), die dann per elektronischer e-Mail gesendet wird. Wenn das Dokument nicht geändert wurde, wird keine temporäre Datei benötigt. das Original wird gesendet. `OnFileSendMail` lädt Datei "Mapi32. DLL, wenn Sie nicht bereits geladen wurde.

Anders als bei der Implementierung von `OnFileSendMail` für `CDocument`verarbeitet diese Funktion Verbund Dateien ordnungsgemäß.

Weitere Informationen finden Sie in den [MAPI-Themen](../../mfc/mapi.md) und [in der MAPI-Unterstützung in MFC](../../mfc/mapi-support-in-mfc.md) -Artikeln.

##  <a name="onshowviews"></a>COleDocument:: onshowviews

Das Framework ruft diese Funktion auf, nachdem sich der Sichtbarkeits Status des Dokuments geändert hat.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parameter

*bvisible*<br/>
Gibt an, ob das Dokument sichtbar oder unsichtbar geworden ist.

### <a name="remarks"></a>Hinweise

Die Standardversion dieser Funktion führt keine Aktion aus. Überschreiben Sie diese, wenn Ihre Anwendung eine besondere Verarbeitung durchführen muss, wenn sich die Sichtbarkeit des Dokuments ändert.

##  <a name="onupdateeditchangeicon"></a>COleDocument:: onupdateeditchangeicon

Wird von Framework aufgerufen, um den Befehl "Symbol ändern" im Menü "Bearbeiten" zu aktualisieren.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf eine `CCmdUI`-Struktur, die das Menü darstellt, das den Update-Befehl generiert hat. Der Update Handler Ruft die `Enable` Member-Funktion der `CCmdUI` Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Hinweise

`OnUpdateEditChangeIcon` aktualisiert die Benutzeroberfläche des Befehls, je nachdem, ob ein gültiges Symbol im Dokument vorhanden ist. Überschreiben Sie diese Funktion, um das Verhalten zu ändern.

##  <a name="onupdateeditlinksmenu"></a>COleDocument:: onupdateeditlinksmenu

Wird von Framework aufgerufen, um den Link Befehl im Menü "Bearbeiten" zu aktualisieren.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf eine `CCmdUI`-Struktur, die das Menü darstellt, das den Update-Befehl generiert hat. Der Update Handler Ruft die `Enable` Member-Funktion der `CCmdUI` Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Hinweise

Beginnend mit dem ersten OLE-Element im Dokument `OnUpdateEditLinksMenu` auf jedes Element zugreift, testet, ob das Element ein Link ist, und aktiviert, wenn es sich um einen Link handelt, den Link-Befehl. Überschreiben Sie diese Funktion, um das Verhalten zu ändern.

##  <a name="onupdateobjectverbmenu"></a>COleDocument:: onupdateobjectverbmenu

Wird von Framework aufgerufen, um den *objectName* -Befehl im Menü Bearbeiten und das Untermenü Verb zu aktualisieren, auf das über den *objectName* -Befehl zugegriffen wird, wobei *objectName* der Name des OLE-Objekts ist, das in das Dokument eingebettet ist.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf eine `CCmdUI`-Struktur, die das Menü darstellt, das den Update-Befehl generiert hat. Der Update Handler Ruft die `Enable` Member-Funktion der `CCmdUI` Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Hinweise

`OnUpdateObjectVerbMenu` aktualisiert die Benutzeroberfläche des *objectName* -Befehls, je nachdem, ob im Dokument ein gültiges Objekt vorhanden ist. Wenn ein Objekt vorhanden ist, wird der *objectName* -Befehl im Menü "Bearbeiten" aktiviert. Wenn dieser Menübefehl ausgewählt ist, wird das Untermenü Verb angezeigt. Das Untermenü Verb enthält alle Verb Befehle, die für das Objekt verfügbar sind, wie z. b. "Bearbeiten", "Eigenschaften" usw. Überschreiben Sie diese Funktion, um das Verhalten zu ändern.

##  <a name="onupdatepastelinkmenu"></a>COleDocument:: onupdatepstelinkmenu

Wird von Framework aufgerufen, um zu bestimmen, ob ein verknüpftes OLE-Element aus der Zwischenablage eingefügt werden kann.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf eine `CCmdUI`-Struktur, die das Menü darstellt, das den Update-Befehl generiert hat. Der Update Handler Ruft die `Enable` Member-Funktion der `CCmdUI` Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Hinweise

Der Befehl speziellen Menübefehl Einfügen ist aktiviert oder deaktiviert, je nachdem, ob das Element in das Dokument eingefügt werden kann oder nicht.

##  <a name="onupdatepastemenu"></a>COleDocument:: onupdatepastemenu

Wird von Framework aufgerufen, um zu bestimmen, ob ein eingebettetes OLE-Element aus der Zwischenablage eingefügt werden kann.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf eine `CCmdUI`-Struktur, die das Menü darstellt, das den Update-Befehl generiert hat. Der Update Handler Ruft die `Enable` Member-Funktion der `CCmdUI` Struktur über *pCmdUI* auf, um die Benutzeroberfläche zu aktualisieren.

### <a name="remarks"></a>Hinweise

Je nachdem, ob das Element in das Dokument eingefügt werden kann, werden der Menübefehl und die Schaltfläche "Einfügen" aktiviert oder deaktiviert.

##  <a name="removeitem"></a>COleDocument:: RemoveItem

Diese Funktion wird aufgerufen, um ein Element aus dem Dokument zu entfernen.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parameter

*pitem*<br/>
Zeiger auf das zu entfernende Dokument Element.

### <a name="remarks"></a>Hinweise

Sie müssen diese Funktion in der Regel nicht explizit aufzurufen. Sie wird von den de-dektoren für `COleClientItem` und `COleServerItem`aufgerufen.

##  <a name="updatemodifiedflag"></a>COleDocument:: updatemodifiedflag

Diese Funktion wird aufgerufen, um das Dokument als geändert zu markieren, wenn eines der enthaltenen OLE-Elemente geändert wurde.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Hinweise

Dadurch kann das Framework den Benutzer auffordern, das Dokument vor dem Schließen zu speichern, auch wenn die nativen Daten im Dokument nicht geändert wurden.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel Container](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument-Klasse](../../mfc/reference/cdocument-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
