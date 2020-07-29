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
ms.openlocfilehash: 21db03fde267a366d4dd1bf747880951e7546058
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219611"
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
|[CRecordView:: CRecordView](#crecordview)|Erstellt ein `CRecordView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordView:: isonfirstrecord](#isonfirstrecord)|Gibt einen Wert ungleich 0 (null) zurück, wenn der aktuelle Datensatz der erste Datensatz im zugeordneten Recordset ist.|
|[CRecordView:: isonlastrecord](#isonlastrecord)|Gibt einen Wert ungleich 0 (null) zurück, wenn der aktuelle Datensatz der letzte Datensatz im zugeordneten Recordset ist.|
|[CRecordView:: OnGetRecordset](#ongetrecordset)|Gibt einen Zeiger auf ein Objekt einer Klasse zurück, die von abgeleitet ist `CRecordset` . Der ClassWizard überschreibt diese Funktion für Sie und erstellt bei Bedarf das Recordset.|
|[CRecordView:: OnMove](#onmove)||

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecordView:: OnMove](#onmove)|Wenn sich der aktuelle Datensatz geändert hat, aktualisiert ihn in der Datenquelle und wechselt dann zum angegebenen Datensatz ("Next", "Previous", "First" oder "Last").|

## <a name="remarks"></a>Bemerkungen

Die Ansicht ist eine Formularansicht, die direkt mit einem-Objekt verbunden ist `CRecordset` . Die Sicht wird aus einer Dialogfeld Vorlagen Ressource erstellt und zeigt die Felder des `CRecordset` -Objekts in den Steuerelementen der Dialogfeld Vorlage an. Das `CRecordView` -Objekt verwendet den Dialog Datenaustausch (DDX) und den Daten Satz Feld Austausch (RFX), um die Daten Verschiebung zwischen den Steuerelementen im Formular und den Feldern des Recordsets zu automatisieren. `CRecordView`stellt außerdem eine Standard Implementierung für den Wechsel zum ersten, nächsten, vorherigen oder letzten Datensatz und eine Schnittstelle zum Aktualisieren des Datensatzes bereit, der derzeit in der Ansicht angezeigt wird.

> [!NOTE]
> Verwenden Sie stattdessen die Klasse [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , wenn Sie mit den DAO-Klassen (Data Access Objects) anstelle der Open Database Connectivity-Klassen (ODBC) arbeiten. Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Die gängigste Methode zum Erstellen Ihrer Daten Satz Ansicht ist der Anwendungs-Assistent. Der Anwendungs-Assistent erstellt die Daten Satz Ansichts Klasse und die zugehörige Recordsetklasse als Teil ihrer Skeleton Starter-Anwendung. Wenn Sie die Daten Satz Ansichts Klasse nicht mit dem Anwendungs-Assistenten erstellen, können Sie Sie später mit dem Klassen-Assistenten erstellen. Wenn Sie einfach nur ein einzelnes Formular benötigen, ist der Ansatz des Anwendungs-Assistenten einfacher. Mit dem Klassen-Assistenten können Sie eine Daten Satz Ansicht später im Entwicklungsprozess verwenden. Die Verwendung von ClassWizard zum separaten Erstellen einer Daten Satz Ansicht und eines Recordsets und deren anschließende Verbindung ist der flexibelste Ansatz, da Sie mehr Kontrolle über die Benennung der Recordsetklasse und ihre haben. H/. Cpp-Dateien. Mit diesem Ansatz können Sie auch mehrere Daten Satz Sichten in derselben Recordsetklasse haben.

Damit Endbenutzer in der Daten Satz Ansicht problemlos von Datensatz zu Datensatz wechseln können, erstellt der Anwendungs-Assistent Menü Ressourcen (und optional Symbolleisten) für den Wechsel zum ersten, nächsten, vorherigen oder letzten Datensatz. Wenn Sie eine Daten Satz Ansichts Klasse mit ClassWizard erstellen, müssen Sie diese Ressourcen selbst mit dem Menü-und dem Bitmap-Editor erstellen.

Informationen zur Standard Implementierung für den Wechsel von Datensatz zu Datensatz finden Sie unter `IsOnFirstRecord` und `IsOnLastRecord` und im Artikel [Verwenden einer Daten Satz Ansicht](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView`verfolgt die Position des Benutzers im Recordset nach, damit die Daten Satz Ansicht die Benutzeroberfläche aktualisieren kann. Wenn der Benutzer zu einem Ende des Recordsets wechselt, deaktiviert die Daten Satz Ansicht Benutzeroberflächen Objekte – z. b. Menü Elemente oder Symbolleisten Schaltflächen –, damit Sie weiter in die gleiche Richtung wechseln können.

Weitere Informationen zum Deklarieren und Verwenden der Daten Satz Ansicht und der recordsetklassen finden Sie unter "Entwerfen und Erstellen einer Daten Satz Ansicht" im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md). Weitere Informationen zur Funktionsweise von Daten Satz Sichten und deren Verwendung finden Sie im Artikel [Verwenden einer Daten Satz Ansicht](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a>CRecordView:: CRecordView

Wenn Sie ein Objekt eines Typs erstellen, der von abgeleitet ist `CRecordView` , rufen Sie beide Formen des Konstruktors auf, um das View-Objekt zu initialisieren, und identifizieren Sie die Dialog Ressource, auf der die Sicht basiert.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parameter

*lpsztemplatename*<br/>
Enthält eine NULL-terminierte Zeichenfolge, die den Namen einer Dialogfeld Vorlagen Ressource ist.

*nidtemplate*<br/>
Enthält die ID-Nummer einer Dialogfeld Vorlagen Ressource.

### <a name="remarks"></a>Bemerkungen

Sie können entweder die Ressource anhand ihres Namens identifizieren (eine Zeichenfolge als Argument an den Konstruktor übergeben) oder über Ihre ID (übergeben Sie eine ganze Zahl ohne Vorzeichen als Argument). Es wird empfohlen, eine Ressourcen-ID zu verwenden.

> [!NOTE]
> Ihre abgeleitete Klasse *muss* ihren eigenen Konstruktor bereitstellen. Nennen Sie im Konstruktor ihrer abgeleiteten Klasse den Konstruktor `CRecordView::CRecordView` mit dem Ressourcennamen oder der ID als Argument, wie im folgenden Beispiel gezeigt.

`CRecordView::OnInitialUpdate`Ruft auf `UpdateData` , das aufruft `DoDataExchange` . Mit diesem ersten- `DoDataExchange` Befehl `CRecordView` werden Steuerelemente (indirekt) mit Felddatenmembern verbunden, die `CRecordset` von ClassWizard erstellt werden. Diese Datenmember können erst verwendet werden, nachdem Sie die Basisklassenmember-Funktion aufgerufen haben `CFormView::OnInitialUpdate` .

> [!NOTE]
> Wenn Sie den Klassen-Assistenten verwenden, wird vom Assistenten ein **`enum`** Wert definiert `CRecordView::IDD` , in der Klassen Deklaration angegeben und in der Initialisierungs Liste für den Konstruktor verwendet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CRecordView:: isonfirstrecord

Mit dieser Member-Funktion können Sie ermitteln, ob der aktuelle Datensatz der erste Datensatz im Recordset-Objekt ist, das dieser Daten Satz Ansicht zugeordnet ist.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn der aktuelle Datensatz der erste Datensatz im Recordset ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nützlich, wenn Sie eigene Implementierungen von standardmäßigen Befehls Update Handlern schreiben, die von ClassWizard geschrieben wurden.

Wenn der Benutzer zum ersten Datensatz wechselt, deaktiviert das Framework alle Benutzeroberflächen Objekte, die Sie für den Wechsel zum ersten oder vorherigen Datensatz besitzen.

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CRecordView:: isonlastrecord

Mit dieser Member-Funktion können Sie ermitteln, ob der aktuelle Datensatz der letzte Datensatz im Recordset-Objekt ist, das dieser Daten Satz Ansicht zugeordnet ist.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn der aktuelle Datensatz der letzte Datensatz im Recordset ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nützlich, um eigene Implementierungen der standardmäßigen Befehls Update Handler zu schreiben, die von ClassWizard geschrieben werden, um eine Benutzeroberfläche zum Wechseln von Datensatz zu Datensatz zu unterstützen.

> [!CAUTION]
> Das Ergebnis dieser Funktion ist zuverlässig, mit dem Unterschied, dass die Sicht das Ende des Recordsets erst erkennen kann, wenn der Benutzer es hinter ihm bewegt hat. Der Benutzer muss sich über den letzten Datensatz hinaus bewegen, bevor die Daten Satz Ansicht feststellen kann, dass alle Benutzeroberflächen Objekte zum Wechseln zum nächsten oder letzten Datensatz deaktiviert werden müssen. Wenn der Benutzer den letzten Datensatz überschreitet und dann zurück zum letzten Datensatz (oder davor) wechselt, kann die Daten Satz Ansicht die Position des Benutzers im Recordset nachverfolgen und die Benutzeroberflächen Objekte ordnungsgemäß deaktivieren. `IsOnLastRecord`ist nach einem Rückruf der-Implementierungs Funktion `OnRecordLast` , die den ID_RECORD_LAST Befehl verarbeitet, auch unzuverlässig `CRecordset::MoveLast` .

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a>CRecordView:: OnGetRecordset

Gibt einen Zeiger auf das `CRecordset` von abgeleitete Objekt zurück, das der Daten Satz Ansicht zugeordnet ist.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein von `CRecordset` abgeleitetes Objekt, wenn das Objekt erfolgreich erstellt wurde, andernfalls ein NULL-Zeiger.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Member-Funktion überschreiben, um ein Recordset-Objekt zu erstellen oder abzurufen und einen Zeiger darauf zurückzugeben. Wenn Sie Ihre Daten Satz Ansichts Klasse mit ClassWizard deklarieren, schreibt der Assistent eine Standard Überschreibung für Sie. Die Standard Implementierung von ClassWizard gibt den Recordset-Zeiger zurück, der in der Daten Satz Ansicht gespeichert ist, sofern vorhanden. Wenn dies nicht der Fall ist, wird ein Recordset-Objekt des Typs erstellt, den Sie mit ClassWizard angegeben haben, und seine Member-Funktion wird aufgerufen, `Open` um die Tabelle zu öffnen oder die Abfrage auszuführen. Anschließend wird ein Zeiger auf das Objekt zurückgegeben

Weitere Informationen und Beispiele finden Sie im Artikel [Daten Satz Ansichten: Verwenden einer Daten Satz Ansicht](../../data/using-a-record-view-mfc-data-access.md).

## <a name="crecordviewonmove"></a><a name="onmove"></a>CRecordView:: OnMove

Diese Member-Funktion aufrufen, um zu einem anderen Datensatz im Recordset zu wechseln und die zugehörigen Felder in den Steuerelementen der Daten Satz Ansicht anzuzeigen.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parameter

*nidmuvecommand*<br/>
Einer der folgenden Standard Befehls-ID-Werte:

- ID_RECORD_FIRST zum ersten Datensatz im Recordset wechseln.

- ID_RECORD_LAST zum letzten Datensatz im Recordset wechseln.

- ID_RECORD_NEXT zum nächsten Datensatz im Recordset wechseln.

- ID_RECORD_PREV zum vorherigen Datensatz im Recordset wechseln.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Verschiebung erfolgreich war. andernfalls 0, wenn die Verschiebungs Anforderung verweigert wurde.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung ruft die entsprechende `Move` Member-Funktion des-Objekts auf, das `CRecordset` der Daten Satz Ansicht zugeordnet ist.

Standardmäßig wird `OnMove` der aktuelle Datensatz in der Datenquelle aktualisiert, wenn der Benutzer ihn in der Daten Satz Ansicht geändert hat.

Der Anwendungs-Assistent erstellt eine Menü Ressource mit den Menü Elementen "erster Datensatz", "Letzter Datensatz", "Nächster Datensatz" und "Vorheriger Datensatz". Wenn Sie die Option andockbare Symbolleiste auswählen, erstellt der Anwendungs-Assistent auch eine Symbolleiste mit Schaltflächen, die diesen Befehlen entsprechen.

Wenn Sie den letzten Datensatz im Recordset überschreiten, wird in der Daten Satz Ansicht weiterhin der letzte Datensatz angezeigt. Wenn Sie sich rückwärts nach dem ersten Datensatz bewegen, wird in der Daten Satz Ansicht weiterhin der erste Datensatz angezeigt.

> [!CAUTION]
> Durch Aufrufen von `OnMove` wird eine Ausnahme ausgelöst, wenn das Recordset keine Datensätze enthält. Sie können die entsprechende benutzerschnittstellenaktualisierungs-Handlerfunktion – `OnUpdateRecordFirst` , `OnUpdateRecordLast` , `OnUpdateRecordNext` oder `OnUpdateRecordPrev` – vor dem entsprechenden Verschiebungs Vorgang aufzurufen, um zu bestimmen, ob das Recordset Datensätze aufweist

## <a name="see-also"></a>Weitere Informationen

[CFormView-Klasse](../../mfc/reference/cformview-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)<br/>
[CFormView-Klasse](../../mfc/reference/cformview-class.md)
