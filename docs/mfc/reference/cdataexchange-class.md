---
title: CDataExchange-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
ms.openlocfilehash: fd1bce7de7ac323dc3099ab4938306768eb95a35
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754621"
---
# <a name="cdataexchange-class"></a>CDataExchange-Klasse

Unterstützt die Routinen für den Dialogdatenaustausch (Dialog Data Exchange, DDX) und die Dialogfelddatenvalidierung (Dialog Data Validation, DDV), die von den Microsoft Foundation-Klassen verwendet werden.

## <a name="syntax"></a>Syntax

```
class CDataExchange
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDataExchange::CDataExchange](#cdataexchange)|Erstellt ein `CDataExchange`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDataExchange::Fail](#fail)|Wird aufgerufen, wenn die Validierung fehlschlägt. Setzt den Fokus auf das vorherige Steuerelement zurück und löst eine Ausnahme aus.|
|[CDataExchange::PrepareCtrl](#preparectrl)|Bereitet das angegebene Steuerelement für den Datenaustausch oder die Validierung vor. Wird für Nicht-Edit-Steuerelemente verwendet.|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Bereitet das angegebene Bearbeitungssteuerelement für den Datenaustausch oder die Validierung vor.|
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Bereitet das angegebene OLE-Steuerelement für den Datenaustausch oder die Validierung vor. Wird für Nicht-Edit-Steuerelemente verwendet.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Flag für die Richtung von DDX und DDV.|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|Das Dialogfeld oder Fenster, in dem der Datenaustausch stattfindet.|

## <a name="remarks"></a>Bemerkungen

`CDataExchange`hat keine Basisklasse.

Verwenden Sie diese Klasse, wenn Sie Datenaustauschroutinen für benutzerdefinierte Datentypen oder Steuerelemente schreiben oder wenn Sie eigene Datenvalidierungsroutinen schreiben. Weitere Informationen zum Schreiben Ihrer eigenen DDX- und DDV-Routinen finden Sie unter [Technische Anmerkung 26](../../mfc/tn026-ddx-and-ddv-routines.md). Eine Übersicht über DDX und DDV finden Sie unter [DialogDatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md) und [Dialogfelder](../../mfc/dialog-boxes.md).

Ein `CDataExchange` Objekt stellt die Kontextinformationen bereit, die für dDX und DDV erforderlich sind. Das Flag *m_bSaveAndValidate* ist FALSE, wenn DDX verwendet wird, um die Anfangswerte von Dialogsteuerelementen aus Datenmembern auszufüllen. Das Flag *m_bSaveAndValidate* ist TRUE, wenn DDX verwendet wird, um die aktuellen Werte von Dialogsteuerelementen in Datenmember festzulegen, und wenn DDV zum Überprüfen der Datenwerte verwendet wird. Wenn die DDV-Validierung fehlschlägt, zeigt die DDV-Prozedur ein Meldungsfeld an, in dem der Eingabefehler erläutert wird. Die DDV-Prozedur `Fail` ruft dann auf, um den Fokus auf das beanstandete Steuerelement zurückzusetzen und eine Ausnahme auszulösen, um den Validierungsprozess zu beenden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CDataExchange`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="cdataexchangecdataexchange"></a><a name="cdataexchange"></a>CDataExchange::CDataExchange

Rufen Sie diese Memberfunktion auf, um ein `CDataExchange` Objekt zu erstellen.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>Parameter

*pDlgWnd*<br/>
Ein Zeiger auf das übergeordnete Fenster, das das Steuerelement enthält. Normalerweise handelt es sich um ein [CDialog](../../mfc/reference/cdialog-class.md)-derived-Objekt.

*bSaveAndValidate*<br/>
Wenn TRUE, überprüft dieses Objekt Daten und schreibt dann Daten aus den Steuerelementen in die Member. Wenn FALSE, verschiebt dieses Objekt Daten von Membern in Steuerelemente.

### <a name="remarks"></a>Bemerkungen

Erstellen `CDataExchange` Sie ein Objekt selbst, um zusätzliche Informationen im Datenaustauschobjekt zu speichern, die an die [CWnd::DoDataExchange-Memberfunktion](../../mfc/reference/cwnd-class.md#dodataexchange) Ihres Fensters übergeben werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

## <a name="cdataexchangefail"></a><a name="fail"></a>CDataExchange::Fail

Das Framework ruft diese Memberfunktion auf, wenn ein DDV-Vorgang (Dialogdatenvalidierung) fehlschlägt.

```cpp
void Fail();
```

### <a name="remarks"></a>Bemerkungen

`Fail`stellt den Fokus und die Auswahl auf das Steuerelement wieder her, dessen Überprüfung fehlgeschlagen ist (wenn ein Steuerelement wiederhergestellt werden muss). `Fail`löst dann eine Ausnahme vom Typ [CUserException](../../mfc/reference/cuserexception-class.md) aus, um den Validierungsprozess zu beenden. Die Ausnahme bewirkt, dass ein Meldungsfeld angezeigt wird, in dem der Fehler angezeigt wird. Nachdem die DDV-Validierung fehlschlägt, kann der Benutzer Daten im beanstandeten Steuerelement erneut eingeben.

Implementierer benutzerdefinierter DDV-Routinen können von ihren Routinen aufrufen, `Fail` wenn eine Validierung fehlschlägt.

Weitere Informationen zum Schreiben Ihrer eigenen DDX- und DDV-Routinen finden Sie unter [Technische Anmerkung 26](../../mfc/tn026-ddx-and-ddv-routines.md). Eine Übersicht über DDX und DDV finden Sie unter [DialogDatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md) und [Dialogfeldthemen](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_bsaveandvalidate"></a><a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate

Dieses Flag gibt die Richtung eines DDX-Vorgangs (Dialogdatenaustausch) an.

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Bemerkungen

Das Flag ist ungleich Null, wenn das `CDataExchange` Objekt verwendet wird, um Daten aus den Dialogfeldsteuerelementen in Dialogklassen-Datenmember zu verschieben, nachdem der Benutzer die Steuerelemente bearbeitet hat. Das Flag ist Null, wenn das Objekt zum Initialisieren von Dialogsteuerelementen aus Dialogklassendatenmembern verwendet wird.

Das Flag ist auch während der Dialogdatenvalidierung (DDV) ungleich Null.

Weitere Informationen zum Schreiben Ihrer eigenen DDX- und DDV-Routinen finden Sie unter [Technische Anmerkung 26](../../mfc/tn026-ddx-and-ddv-routines.md). Eine Übersicht über DDX und DDV finden Sie unter [DialogDatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md) und [Dialogfeldthemen](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_pdlgwnd"></a><a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd

Enthält einen Zeiger auf das [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) für das Dialogdatenaustausch (DDX) oder Validierung (DDV) stattfindet.

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Bemerkungen

Dieses Objekt ist normalerweise ein [CDialog-Objekt.](../../mfc/reference/cdialog-class.md) Implementierer benutzerdefinierter DDX- oder DDV-Routinen können diesen Zeiger verwenden, um Zugriff auf das Dialogfeld zu erhalten, das die Steuerelemente enthält, auf denen sie ausgeführt werden.

Weitere Informationen zum Schreiben Ihrer eigenen DDX- und DDV-Routinen finden Sie unter [Technische Anmerkung 26](../../mfc/tn026-ddx-and-ddv-routines.md). Eine Übersicht über DDX und DDV finden Sie unter [DialogDatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md) und [Dialogfeldthemen](../../mfc/dialog-boxes.md).

## <a name="cdataexchangepreparectrl"></a><a name="preparectrl"></a>CDataExchange::PrepareCtrl

Das Framework ruft diese Memberfunktion auf, um das angegebene Steuerelement für den Dialogdatenaustausch (DDX) und die Validierung (DDV) vorzubereiten.

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>Parameter

*nIDC*<br/>
Die ID des Steuerelements, das für DDX oder DDV vorbereitet werden soll.

### <a name="return-value"></a>Rückgabewert

Der HWND des Steuerelements, das für DDX oder DDV vorbereitet wird.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [Stattdessen PrepareEditCtrl](#prepareeditctrl) für Bearbeitungssteuerelemente. Verwenden Sie diese Memberfunktion für alle anderen Steuerelemente.

Die Vorbereitung besteht darin, die HWND des Steuerelements in der `CDataExchange` Klasse zu speichern. Das Framework verwendet dieses Handle, um den Fokus im Falle eines DDX- oder DDV-Fehlers auf das zuvor fokussierte Steuerelement wiederherzustellen.

Implementierer von benutzerdefinierten DDX- oder `PrepareCtrl` DDV-Routinen sollten alle Nicht-Edit-Steuerelemente aufrufen, für die sie Daten über DDX austauschen oder Daten über DDV validieren.

Weitere Informationen zum Schreiben Ihrer eigenen DDX- und DDV-Routinen finden Sie unter [Technische Anmerkung 26](../../mfc/tn026-ddx-and-ddv-routines.md). Eine Übersicht über DDX und DDV finden Sie unter [DialogDatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md) und [Dialogfeldthemen](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl

Das Framework ruft diese Memberfunktion auf, um das angegebene Bearbeitungssteuerelement für den Dialogdatenaustausch (DDX) und die Validierung (DDV) vorzubereiten.

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>Parameter

*nIDC*<br/>
Die ID des Bearbeitungssteuerelements, das für DDX oder DDV vorbereitet werden soll.

### <a name="return-value"></a>Rückgabewert

Die HWND des Bearbeitungssteuerelements, das für DDX oder DDV vorbereitet wird.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie stattdessen [PrepareCtrl](#preparectrl) für alle Steuerelemente, die nicht bearbeitet werden.

Die Vorbereitung besteht aus zwei Dingen. `PrepareEditCtrl` Speichert zunächst die HWND des `CDataExchange` Steuerelements in der Klasse. Das Framework verwendet dieses Handle, um den Fokus im Falle eines DDX- oder DDV-Fehlers auf das zuvor fokussierte Steuerelement wiederherzustellen. Zweitens `PrepareEditCtrl` wird ein Flag `CDataExchange` in der Klasse festgelegt, um anzugeben, dass das Steuerelement, dessen Daten ausgetauscht oder überprüft werden, ein Bearbeitungssteuerelement ist.

Implementierer von benutzerdefinierten DDX- oder `PrepareEditCtrl` DDV-Routinen sollten alle Bearbeitungssteuerelemente aufrufen, für die sie Daten über DDX austauschen oder Daten über DDV validieren.

Weitere Informationen zum Schreiben Ihrer eigenen DDX- und DDV-Routinen finden Sie unter [Technische Anmerkung 26](../../mfc/tn026-ddx-and-ddv-routines.md). Eine Übersicht über DDX und DDV finden Sie unter [DialogDatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md) und [Dialogfeldthemen](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a>CDataExchange::PrepareOleCtrl

Das Framework ruft diese Memberfunktion auf, um das angegebene OLE-Steuerelement für den Dialogdatenaustausch (DDX) und die Validierung (DDV) vorzubereiten.

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>Parameter

*nIDC*<br/>
Die ID des OLE-Steuerelements, das für DDX oder DDV vorbereitet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die OLE-Steuerungssite.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [stattdessen PrepareEditCtrl](#prepareeditctrl) für Bearbeitungssteuerelemente oder [PrepareCtrl](#preparectrl) für alle anderen Nicht-OLE-Steuerelemente.

Implementierer benutzerdefinierter DDX- oder DDV-Routinen sollten alle OLE-Steuerelemente aufrufen, `PrepareOleCtrl` für die sie Daten über DDX austauschen oder Daten über DDV validieren.

Weitere Informationen zum Schreiben Ihrer eigenen DDX- und DDV-Routinen finden Sie unter [Technische Anmerkung 26](../../mfc/tn026-ddx-and-ddv-routines.md). Eine Übersicht über DDX und DDV finden Sie unter [DialogDatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md) und [Dialogfeldthemen](../../mfc/dialog-boxes.md).

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)
