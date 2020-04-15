---
title: CRecordView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: b706a80f91a3c952d80da13f453a807c775b9405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368355"
---
# <a name="crecordview-class"></a>CRecordView-Klasse

Eine Sicht, die Datenbankdatensätze in Steuerelementen anzeigt.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordView::CRecordView](#crecordview)|Erstellt ein `CRecordView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Gibt einen Wert ungleich Null zurück, wenn der aktuelle Datensatz der erste Datensatz im zugeordneten Recordset ist.|
|[CRecordView::IsonLastRecord](#isonlastrecord)|Gibt einen Wert ungleich Null zurück, wenn der aktuelle Datensatz der letzte Datensatz im zugeordneten Recordset ist.|
|[CRecordView::OnGetRecordset](#ongetrecordset)|Gibt einen Zeiger auf ein Objekt `CRecordset`einer Von abgeleiteten Klasse zurück. ClassWizard überschreibt diese Funktion für Sie und erstellt bei Bedarf das Recordset.|
|[CRecordView::OnMove](#onmove)||

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordView::OnMove](#onmove)|Wenn sich der aktuelle Datensatz geändert hat, aktualisiert er in der Datenquelle und wechselt dann zum angegebenen Datensatz (nächste, vorherige, erste oder letzte).|

## <a name="remarks"></a>Bemerkungen

Die Ansicht ist eine Formularansicht, die direkt mit einem `CRecordset` Objekt verbunden ist. Die Ansicht wird aus einer Dialogvorlagenressource erstellt `CRecordset` und zeigt die Felder des Objekts in den Steuerelementen der Dialogfeldvorlage an. Das `CRecordView` Objekt verwendet Dialogdatenaustausch (DDX) und Datensatzfeldaustausch (RFX), um die Verschiebung von Daten zwischen den Steuerelementen im Formular und den Feldern des Recordsets zu automatisieren. `CRecordView`stellt außerdem eine Standardimplementierung für den Wechsel zum ersten, nächsten, vorherigen oder letzten Datensatz und eine Schnittstelle zum Aktualisieren des aktuell angezeigten Datensatzes bereit.

> [!NOTE]
> Wenn Sie mit den DAO-Klassen (Data Access Objects) und nicht mit den ODBC-Klassen (Open Database Connectivity) arbeiten, verwenden Sie stattdessen die Klasse [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Die häufigste Möglichkeit zum Erstellen der Datensatzansicht ist der Anwendungs-Assistent. Der Anwendungs-Assistent erstellt sowohl die Datensatzansichtsklasse als auch die zugehörige Recordset-Klasse als Teil ihrer Skelettstarteranwendung. Wenn Sie die Datensatzansichtsklasse nicht mit dem Anwendungs-Assistenten erstellen, können Sie sie später mit ClassWizard erstellen. Wenn Sie einfach ein einzelnes Formular benötigen, ist der Anwendungs-Assistenten-Ansatz einfacher. Mit ClassWizard können Sie sich entscheiden, eine Datensatzansicht später im Entwicklungsprozess zu verwenden. Die Verwendung von ClassWizard zum separat erstellen und verbinden sie mit ClassWizard ist der flexibelste Ansatz, da Sie mehr Kontrolle beim Benennen der Recordsetklasse und ihrer haben. H/. CPP-Dateien. Mit diesem Ansatz können Sie auch mehrere Datensatzansichten für dieselbe Recordset-Klasse haben.

Um Endbenutzern den Wechsel von Datensatz zu Datensatz in der Datensatzansicht zu erleichtern, erstellt der Anwendungs-Assistent Menüressourcen (und optional Symbolleistenressourcen) für den Wechsel zum ersten, nächsten, vorherigen oder letzten Datensatz. Wenn Sie eine Datensatzansichtsklasse mit ClassWizard erstellen, müssen Sie diese Ressourcen selbst mit dem Menü und den Bitmap-Editoren erstellen.

Informationen zur Standardimplementierung für den Wechsel von `IsOnFirstRecord` `IsOnLastRecord` Datensatz zu Datensatz finden Sie unter und im Artikel [Verwenden einer Datensatzansicht](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView`verfolgt die Position des Benutzers im Recordset, damit die Datensatzansicht die Benutzeroberfläche aktualisieren kann. Wenn der Benutzer zu einem der beiden Enden des Recordsets wechselt, deaktiviert die Datensatzansicht Benutzeroberflächenobjekte ( z. B. Menüelemente oder Symbolleistenschaltflächen –, um weiter in die gleiche Richtung zu wechseln.

Weitere Informationen zum Deklarieren und Verwenden der Datensatzansicht und der Recordsetklassen finden Sie unter "Entwerfen und Erstellen einer Datensatzansicht" im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md). Weitere Informationen zur Funktionsweise von Datensatzansichten und deren Verwendung finden Sie im Artikel [Verwenden einer Datensatzansicht](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a>CRecordView::CRecordView

Wenn Sie ein Objekt eines `CRecordView`von abgeleiteten Typs erstellen, rufen Sie beide Formen des Konstruktors auf, um das Ansichtsobjekt zu initialisieren und die Dialogfeldressource zu identifizieren, auf der die Ansicht basiert.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parameter

*lpszTemplateName*<br/>
Enthält eine null-terminierte Zeichenfolge, die der Name einer Dialogfeldvorlagenressource ist.

*nIDTemplate*<br/>
Enthält die ID-Nummer einer Dialogfeldvorlagenressource.

### <a name="remarks"></a>Bemerkungen

Sie können die Ressource entweder anhand des Namens (übergeben Sie eine Zeichenfolge als Argument an den Konstruktor) oder durch ihre ID (übergeben Sie eine ganzzahlige Datei ohne Vorzeichen als Argument) identifizieren. Es wird empfohlen, eine Ressourcen-ID zu verwenden.

> [!NOTE]
> Die abgeleitete Klasse *muss* einen eigenen Konstruktor bereitstellen. Rufen Sie im Konstruktor der abgeleiteten `CRecordView::CRecordView` Klasse den Konstruktor mit dem Ressourcennamen oder der Ressourcen-ID als Argument auf, wie im folgenden Beispiel gezeigt.

`CRecordView::OnInitialUpdate`Aufrufe `UpdateData`, `DoDataExchange`die anruft . Dieser erste `DoDataExchange` Aufruf `CRecordView` zum Verbinden von `CRecordset` Steuerelementen (indirekt) mit Felddatenmembern, die von ClassWizard erstellt wurden. Diese Datenmember können erst verwendet werden, `CFormView::OnInitialUpdate` nachdem Sie die Basisklassenmemberfunktion aufrufen.

> [!NOTE]
> Wenn Sie ClassWizard verwenden, definiert der `CRecordView::IDD`Assistent einen **Enumerationswert** , gibt ihn in der Klassendeklaration an und verwendet ihn in der Memberinitialisierungsliste für den Konstruktor.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CRecordView::IsOnFirstRecord

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob der aktuelle Datensatz der erste Datensatz im Recordset-Objekt ist, der dieser Datensatzansicht zugeordnet ist.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der aktuelle Datensatz der erste Datensatz im Recordset ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nützlich, um eigene Implementierungen von Standardbefehlsaktualisierungshandlern zu schreiben, die von ClassWizard geschrieben wurden.

Wenn der Benutzer zum ersten Datensatz wechselt, deaktiviert das Framework alle Benutzeroberflächenobjekte, die Sie für den Wechsel zum ersten oder vorherigen Datensatz haben.

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CRecordView::IsonLastRecord

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob der aktuelle Datensatz der letzte Datensatz im Recordset-Objekt ist, das dieser Datensatzansicht zugeordnet ist.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der aktuelle Datensatz der letzte Datensatz im Recordset ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nützlich, um eigene Implementierungen der Standardbefehlsaktualisierungshandler zu schreiben, die ClassWizard schreibt, um eine Benutzeroberfläche für den Wechsel von Datensatz zu Datensatz zu unterstützen.

> [!CAUTION]
> Das Ergebnis dieser Funktion ist zuverlässig, außer dass die Ansicht das Ende des Recordsets erst erkennen kann, wenn der Benutzer an ihm vorbeigezogen ist. Der Benutzer muss über den letzten Datensatz hinausgehen, bevor die Datensatzansicht erkennen kann, dass alle Benutzeroberflächenobjekte für den Wechsel zum nächsten oder letzten Datensatz deaktiviert werden müssen. Wenn der Benutzer den letzten Datensatz und dann wieder zum letzten Datensatz (oder davor) wechselt, kann die Datensatzansicht die Position des Benutzers im Recordset nachverfolgen und Benutzeroberflächenobjekte ordnungsgemäß deaktivieren. `IsOnLastRecord`ist auch nach einem Aufruf der `OnRecordLast`Implementierungsfunktion, die den `CRecordset::MoveLast`Befehl ID_RECORD_LAST verarbeitet, unzuverlässig.

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a>CRecordView::OnGetRecordset

Gibt einen Zeiger `CRecordset`auf das -derived-Objekt zurück, das der Datensatzansicht zugeordnet ist.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CRecordset`ein -derived-Objekt, wenn das Objekt erfolgreich erstellt wurde. andernfalls ein NULL-Zeiger.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Memberfunktion überschreiben, um ein Recordset-Objekt zu erstellen oder abzuerhalten und einen Zeiger darauf zurückzugeben. Wenn Sie Ihre Datensatzansichtsklasse mit ClassWizard deklarieren, schreibt der Assistent eine Standardüberschreibung für Sie. Die Standardimplementierung von ClassWizard gibt den recordset-Zeiger zurück, der in der Datensatzansicht gespeichert ist, sofern vorhanden. Ist dies nicht der Fall, wird ein Recordset-Objekt `Open` des Typs erstellt, den Sie mit ClassWizard angegeben haben, und ruft seine Memberfunktion auf, um die Tabelle zu öffnen oder die Abfrage auszuführen, und gibt dann einen Zeiger auf das Objekt zurück.

Weitere Informationen und Beispiele finden Sie im Artikel [Datensatzansichten: Verwenden einer Datensatzansicht](../../data/using-a-record-view-mfc-data-access.md).

## <a name="crecordviewonmove"></a><a name="onmove"></a>CRecordView::OnMove

Rufen Sie diese Memberfunktion auf, um zu einem anderen Datensatz im Recordset zu wechseln und seine Felder in den Steuerelementen der Datensatzansicht anzuzeigen.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parameter

*nIDMoveCommand*<br/>
Einer der folgenden Standardbefehls-ID-Werte:

- ID_RECORD_FIRST Zum ersten Datensatz im Recordset wechseln.

- ID_RECORD_LAST Zum letzten Datensatz im Recordset wechseln.

- ID_RECORD_NEXT Zum nächsten Datensatz im Recordset wechseln.

- ID_RECORD_PREV Zum vorherigen Datensatz im Recordset wechseln.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Umzug erfolgreich war; andernfalls 0, wenn die Verschiebungsanforderung abgelehnt wurde.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung ruft `Move` die entsprechende `CRecordset` Memberfunktion des Objekts auf, das der Datensatzansicht zugeordnet ist.

Aktualisiert standardmäßig `OnMove` den aktuellen Datensatz in der Datenquelle, wenn der Benutzer ihn in der Datensatzansicht geändert hat.

Der Anwendungs-Assistent erstellt eine Menüressource mit menüelementen Erster Datensatz, Letzter Datensatz, Nächster Datensatz und Vorheriger Datensatz. Wenn Sie die Option Dockable Toolbar auswählen, erstellt der Anwendungs-Assistent auch eine Symbolleiste mit Schaltflächen, die diesen Befehlen entsprechen.

Wenn Sie den letzten Datensatz im Recordset hinter sich lassen, wird in der Datensatzansicht weiterhin der letzte Datensatz angezeigt. Wenn Sie den ersten Datensatz rückwärts verschieben, wird in der Datensatzansicht weiterhin der erste Datensatz angezeigt.

> [!CAUTION]
> Beim `OnMove` Aufrufen wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Rufen `OnUpdateRecordFirst`Sie die entsprechende Benutzeroberflächenaktualisierungshandlerfunktion auf ( , `OnUpdateRecordLast`, `OnUpdateRecordNext`, oder `OnUpdateRecordPrev` — vor dem entsprechenden Verschiebungsvorgang, um zu bestimmen, ob das Recordset Über Datensätze enthält.

## <a name="see-also"></a>Siehe auch

[CFormView-Klasse](../../mfc/reference/cformview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)<br/>
[CFormView-Klasse](../../mfc/reference/cformview-class.md)
