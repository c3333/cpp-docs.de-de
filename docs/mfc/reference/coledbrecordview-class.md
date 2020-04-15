---
title: COleDBRecordView-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: de9c602cb747ee3d4449df479530e55ce907cb8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366105"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView-Klasse

Eine Sicht, die Datenbankdatensätze in Steuerelementen anzeigt.

## <a name="syntax"></a>Syntax

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|Erstellt ein `COleDBRecordView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Gibt einen Standard-HRESULT-Wert zurück.|
|[COleDBRecordView::OnMove](#onmove)|Aktualisiert den aktuellen Datensatz (falls schmutzig) in der Datenquelle und wechselt dann zum angegebenen Datensatz (nächste, vorherige, erste oder letzte).|

## <a name="remarks"></a>Bemerkungen

Die Ansicht ist eine Formularansicht, die direkt mit einem `CRowset` Objekt verbunden ist. Die Ansicht wird aus einer Dialogvorlagenressource erstellt `CRowset` und zeigt die Felder des Objekts in den Steuerelementen der Dialogfeldvorlage an. Das `COleDBRecordView` Objekt verwendet Dialogdatenaustausch (Dialogdatenaustausch, DDX) und die in `CRowset`integrierte Navigationsfunktionalität, um die Verschiebung von Daten zwischen den Steuerelementen im Formular und den Feldern des Rowsets zu automatisieren. `COleDBRecordView`stellt außerdem eine Standardimplementierung für den Wechsel zum ersten, nächsten, vorherigen oder letzten Datensatz und eine Schnittstelle zum Aktualisieren des aktuell angezeigten Datensatzes bereit.

Sie können DDX-Funktionen `COleDbRecordView` verwenden, um Daten direkt aus dem Datenbankrecordset abzurufen und in einem Dialogsteuerelement anzuzeigen. Sie sollten `DDX_*` die Methoden `DDX_Text`(z. `DDX_Field*` B. `DDX_FieldText`) `COleDbRecordView`verwenden und nicht die Funktionen (z. B. ) mit . `DDX_FieldText`funktioniert nicht `COleDbRecordView` `DDX_FieldText` mit, da ein `CRecordset*` zusätzliches `CRecordView`Argument `CDaoRecordset*` vom `CDaoRecordView`Typ (für ) oder (für ) verwendet wird.

> [!NOTE]
> Wenn Sie mit den DAO-Klassen (Data Access Objects) und nicht mit den OLE DB Consumer Template-Klassen arbeiten, verwenden Sie stattdessen die Klasse [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

`COleDBRecordView`verfolgt die Position des Benutzers im Rowset, damit die Datensatzansicht die Benutzeroberfläche aktualisieren kann. Wenn der Benutzer zu einem der beiden Enden des Rowsets wechselt, deaktiviert die Datensatzansicht Benutzeroberflächenobjekte ( z. B. Menüelemente oder Symbolleistenschaltflächen –, um weiter in die gleiche Richtung zu wechseln.

Weitere Informationen zu Rowsetklassen finden Sie im Artikel [Verwenden von OLE DB-Consumervorlagen.For](../../data/oledb/ole-db-consumer-templates-cpp.md) more information about rowset classes, see the Using OLE DB Consumer Templates article.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxoledb.h

## <a name="coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView

Erstellt ein `COleDBRecordView`-Objekt.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parameter

*lpszTemplateName*<br/>
Enthält eine null-terminierte Zeichenfolge, die der Name einer Dialogfeldvorlagenressource ist.

*nIDTemplate*<br/>
Enthält die ID-Nummer einer Dialogfeldvorlagenressource.

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Objekt eines `COleDBRecordView`von abgeleiteten Typs erstellen, rufen Sie einen der Konstruktoren auf, um das Ansichtsobjekt zu erstellen und die Dialogfeldressource zu identifizieren, auf der die Ansicht basiert. Sie können die Ressource entweder anhand des Namens (übergeben Sie eine Zeichenfolge als Argument an den Konstruktor) oder anhand ihrer ID (übergeben Sie eine ganzzahlige Datei ohne Vorzeichen als Argument) identifizieren.

> [!NOTE]
> Die abgeleitete Klasse *muss* einen eigenen Konstruktor bereitstellen. Rufen Sie im Konstruktor den `COleDBRecordView::COleDBRecordView`Konstruktor , mit dem Ressourcennamen oder der Ressourcen-ID als Argument auf.

## <a name="coledbrecordviewongetrowset"></a><a name="ongetrowset"></a>COleDBRecordView::OnGetRowset

Gibt ein Handle für das **CRowset<>** Objekt zurück, das der Datensatzansicht zugeordnet ist.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Memberfunktion überschreiben, um ein Rowset-Objekt zu erstellen oder abzuerhalten und ein Handle an dieses zurückzugeben. Wenn Sie Ihre Datensatzansichtsklasse mit ClassWizard deklarieren, schreibt der Assistent eine Standardüberschreibung für Sie. Die Standardimplementierung von ClassWizard gibt das in der Datensatzansicht gespeicherte Rowset-Handle zurück, sofern vorhanden. Ist dies nicht der Fall, wird ein Rowset-Objekt `Open` des Typs erstellt, den Sie mit ClassWizard angegeben haben, und ruft seine Memberfunktion auf, um die Tabelle zu öffnen oder die Abfrage auszuführen, und gibt dann ein Handle an das Objekt zurück.

> [!NOTE]
> Vor MFC 7.0, `OnGetRowset` gab einen `CRowset`Zeiger auf zurück. Wenn Sie Code `OnGetRowset`haben, der aufruft, müssen Sie den Rückgabetyp in die templatisierte Klasse **CRowset<>** ändern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Weitere Informationen und Beispiele finden Sie im Artikel [Datensatzansichten: Verwenden einer Datensatzansicht](../../data/using-a-record-view-mfc-data-access.md).

## <a name="coledbrecordviewonmove"></a><a name="onmove"></a>COleDBRecordView::OnMove

Wechselt zu einem anderen Datensatz im Rowset, und zeigt seine Felder in den Steuerelementen der Datensatzansicht an.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parameter

*nIDMoveCommand*<br/>
Einer der folgenden Standardbefehls-ID-Werte:

- ID_RECORD_FIRST – Wechseln Sie zum ersten Datensatz im Recordset.

- ID_RECORD_LAST – Wechseln Sie zum letzten Datensatz im Recordset.

- ID_RECORD_NEXT — Wechseln Sie zum nächsten Datensatz im Recordset.

- ID_RECORD_PREV — Wechseln Sie zum vorherigen Datensatz im Recordset.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Umzug erfolgreich war; andernfalls 0, wenn die Verschiebungsanforderung abgelehnt wurde.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung ruft `Move` die entsprechende `CRowset` Memberfunktion des Objekts auf, das der Datensatzansicht zugeordnet ist.

Aktualisiert standardmäßig `OnMove` den aktuellen Datensatz in der Datenquelle, wenn der Benutzer ihn in der Datensatzansicht geändert hat.

Der Anwendungs-Assistent erstellt eine Menüressource mit menüelementen Erster Datensatz, Letzter Datensatz, Nächster Datensatz und Vorheriger Datensatz. Wenn Sie die Option Dockable Toolbar auswählen, erstellt der Anwendungs-Assistent auch eine Symbolleiste mit Schaltflächen, die diesen Befehlen entsprechen.

Wenn Sie den letzten Datensatz im Recordset hinter sich lassen, wird in der Datensatzansicht weiterhin der letzte Datensatz angezeigt. Wenn Sie den ersten Datensatz rückwärts verschieben, wird in der Datensatzansicht weiterhin der erste Datensatz angezeigt.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
