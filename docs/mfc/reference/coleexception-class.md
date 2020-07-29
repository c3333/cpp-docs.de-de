---
title: COleException-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
ms.openlocfilehash: c82099d816bc8ee8c179e9d4656f474156a629a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233196"
---
# <a name="coleexception-class"></a>COleException-Klasse

Stellt eine Ausnahmebedingung dar, die sich auf einen OLE-Vorgang bezieht.

## <a name="syntax"></a>Syntax

```
class COleException : public CException
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[COleException::P rocess](#process)|Übersetzt eine abgefangene Ausnahme in einen OLE-Rückgabecode.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[COleException:: m_sc](#m_sc)|Enthält den Statuscode, der den Grund für die Ausnahme angibt.|

## <a name="remarks"></a>Bemerkungen

Die- `COleException` Klasse enthält einen öffentlichen Datenmember, der den Statuscode enthält, der den Grund für die Ausnahme angibt.

Im Allgemeinen sollten Sie kein- `COleException` Objekt direkt erstellen. stattdessen sollten Sie [AfxThrowOleException](exception-processing.md#afxthrowoleexception)aufzurufen.

Weitere Informationen zu Ausnahmen finden Sie in den Artikeln [Ausnahmebehandlung (MFC)](../../mfc/exception-handling-in-mfc.md) und [Ausnahmen: OLE-Ausnahmen](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a>COleException:: m_sc

Dieser Datenmember enthält den OLE-Statuscode, der den Grund für die Ausnahme angibt.

```
SCODE m_sc;
```

### <a name="remarks"></a>Bemerkungen

Der Wert dieser Variablen wird von [AfxThrowOleException](exception-processing.md#afxthrowoleexception)festgelegt.

Weitere Informationen zu SCODE finden Sie unter [Struktur von com-Fehler Codes](/windows/win32/com/structure-of-com-error-codes) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a>COleException::P rocess

Mit der Funktion " **Process** Member" wird eine abgefangene Ausnahme in einen OLE-Statuscode übersetzt.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parameter

*panyexception*<br/>
Zeiger auf eine abgefangene Ausnahme.

### <a name="return-value"></a>Rückgabewert

Ein OLE-Statuscode.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Funktion ist **`static`** .

Weitere Informationen zu SCODE finden Sie unter [Struktur von com-Fehler Codes](/windows/win32/com/structure-of-com-error-codes) in der Windows SDK.

### <a name="example"></a>Beispiel

  Siehe dazu das Beispiel für [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel für CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
