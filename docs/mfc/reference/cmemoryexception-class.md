---
title: CMemoryException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 375b4227a25ae4c18cfd263eff4c3ec13f1304e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370008"
---
# <a name="cmemoryexception-class"></a>CMemoryException-Klasse

Stellt eine Ausnahmebedingung dar, die durch ungenügenden Arbeitsspeicher ausgelöst wird.

## <a name="syntax"></a>Syntax

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMemoryException::CMemoryException](#cmemoryexception)|Erstellt ein `CMemoryException`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Eine weitere Qualifizierung ist nicht erforderlich oder möglich. Speicherausnahmen werden automatisch von **neuen**ausgelöst. Wenn Sie ihre eigenen Speicherfunktionen schreiben, z. B. mithilfe `malloc`von , sind Sie für das Auslösen von Speicherausnahmen verantwortlich.

Weitere Informationen `CMemoryException`zu finden Sie im Artikel [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>CMemoryException::CMemoryException

Erstellt ein `CMemoryException`-Objekt.

```
CMemoryException();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Konstruktor nicht direkt, sondern rufen Sie die globale Funktion [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)auf. Diese globale Funktion kann in einer Nicht-Speicher-Situation erfolgreich sein, da sie das Ausnahmeobjekt in zuvor zugewiesenem Speicher erstellt. Weitere Informationen zur Ausnahmeverarbeitung finden Sie in den [Artikelausnahmen](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[CException-Klasse](cexception-class.md)<br/>
[Hierarchiediagramm](../hierarchy-chart.md)
