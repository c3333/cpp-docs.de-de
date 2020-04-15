---
title: COleDispatchException-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
ms.openlocfilehash: 4572b639b757569d8e3cfa731f99c123762f3900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375066"
---
# <a name="coledispatchexception-class"></a>COleDispatchException-Klasse

Behandelt Ausnahmen, die für die `IDispatch` -OLE-Schnittstelle (eine Schlüsselkomponente der OLE-Automatisierung) spezifisch sind.

## <a name="syntax"></a>Syntax

```
class COleDispatchException : public CException
```

## <a name="members"></a>Member

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Hilfekontext für Fehler.|
|[COleDispatchException::m_strDescription](#m_strdescription)|Verbale Fehlerbeschreibung.|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Hilfedatei zur `m_dwHelpContext`Verwendung mit .|
|[COleDispatchException::m_strSource](#m_strsource)|Anwendung, die die Ausnahme generiert hat.|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-spezifischer Fehlercode.|

## <a name="remarks"></a>Bemerkungen

Wie die anderen Ausnahmeklassen, die von der `CException` Basisklasse abgeleitet wurden, `COleDispatchException` können die Makros THROW, THROW_LAST, TRY, CATCH, AND_CATCH und END_CATCH verwendet werden.

Im Allgemeinen sollten Sie [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) aufrufen, `COleDispatchException` um ein Objekt zu erstellen und zu senden.

Weitere Informationen zu Ausnahmen finden Sie in den Artikeln [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md) und [Exceptions: OLE Exceptions](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="coledispatchexceptionm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>COleDispatchException::m_dwHelpContext

Identifiziert einen Hilfekontext in der Hilfe Ihrer Anwendung (. HLP)-Datei.

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>Bemerkungen

Dieser Member wird von der Funktion [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) festgelegt, wenn eine Ausnahme ausgelöst wird.

### <a name="example"></a>Beispiel

  Siehe dazu das Beispiel für [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strdescription"></a><a name="m_strdescription"></a>COleDispatchException::m_strDescription

Enthält eine verbale Fehlerbeschreibung, z. B. "Festplatte voll".

```
CString m_strDescription;
```

### <a name="remarks"></a>Bemerkungen

Dieser Member wird von der Funktion [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) festgelegt, wenn eine Ausnahme ausgelöst wird.

### <a name="example"></a>Beispiel

  Siehe dazu das Beispiel für [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strhelpfile"></a><a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile

Das Framework füllt diese Zeichenfolge mit dem Namen der Hilfedatei der Anwendung aus.

```
CString m_strHelpFile;
```

## <a name="coledispatchexceptionm_strsource"></a><a name="m_strsource"></a>COleDispatchException::m_strSource

Das Framework füllt diese Zeichenfolge mit dem Namen der Anwendung aus, die die Ausnahme generiert hat.

```
CString m_strSource;
```

### <a name="example"></a>Beispiel

  Siehe dazu das Beispiel für [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_wcode"></a><a name="m_wcode"></a>COleDispatchException::m_wCode

Enthält einen anwendungsspezifischen Fehlercode.

```
WORD m_wCode;
```

### <a name="remarks"></a>Bemerkungen

Dieser Member wird von der Funktion [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) festgelegt, wenn eine Ausnahme ausgelöst wird.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDispatchDriver-Klasse](../../mfc/reference/coledispatchdriver-class.md)<br/>
[COleException-Klasse](../../mfc/reference/coleexception-class.md)
