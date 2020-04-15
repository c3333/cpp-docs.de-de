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
ms.openlocfilehash: 737c9e669990f4de6ae18cdc7662c131ad61516f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375014"
---
# <a name="coleexception-class"></a>COleException-Klasse

Stellt eine Ausnahmebedingung dar, die sich auf einen OLE-Vorgang bezieht.

## <a name="syntax"></a>Syntax

```
class COleException : public CException
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleException::PRocess](#process)|Übersetzt eine abgefangene Ausnahme in einen OLE-Rückgabecode.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|Enthält den Statuscode, der den Grund für die Ausnahme angibt.|

## <a name="remarks"></a>Bemerkungen

Die `COleException` Klasse enthält einen öffentlichen Datenmember, der den Statuscode enthält, der den Grund für die Ausnahme angibt.

Im Allgemeinen sollten Sie `COleException` ein Objekt nicht direkt erstellen. Stattdessen sollten Sie [AfxThrowOleException](exception-processing.md#afxthrowoleexception)aufrufen.

Weitere Informationen zu Ausnahmen finden Sie in den Artikeln [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md) und [Exceptions: OLE Exceptions](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a>COleException::m_sc

Dieser Datenmember enthält den OLE-Statuscode, der den Grund für die Ausnahme angibt.

```
SCODE m_sc;
```

### <a name="remarks"></a>Bemerkungen

Der Wert dieser Variablen wird von [AfxThrowOleException](exception-processing.md#afxthrowoleexception)festgelegt.

Weitere Informationen zu SCODE finden Sie unter [Struktur von COM-Fehlercodes](/windows/win32/com/structure-of-com-error-codes) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a>COleException::PRocess

Rufen Sie die **Prozessmemberfunktion** auf, um eine abgefangene Ausnahme in einen OLE-Statuscode zu übersetzen.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parameter

*pAnyException*<br/>
Zeiger auf eine abgefangene Ausnahme.

### <a name="return-value"></a>Rückgabewert

Ein OLE-Statuscode.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Funktion ist **statisch**.

Weitere Informationen zu SCODE finden Sie unter [Struktur von COM-Fehlercodes](/windows/win32/com/structure-of-com-error-codes) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe dazu das Beispiel für [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
