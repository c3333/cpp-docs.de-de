---
title: CResourceException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: 557bfe1cc41c3dda65bd95d7d687820c0b9862b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368330"
---
# <a name="cresourceexception-class"></a>CResourceException-Klasse

Wird generiert, wenn Windows eine angeforderte Ressource nicht finden oder zuordnen kann.

## <a name="syntax"></a>Syntax

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|Erstellt ein `CResourceException`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Eine weitere Qualifizierung ist nicht erforderlich oder möglich.

Weitere Informationen zur `CResourceException`Verwendung finden Sie im Artikel [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cresourceexceptioncresourceexception"></a><a name="cresourceexception"></a>CResourceException::CResourceException

Erstellt ein `CResourceException`-Objekt.

```
CResourceException();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Konstruktor nicht direkt, sondern rufen Sie die globale Funktion [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)auf. Weitere Informationen zu Ausnahmen finden Sie im Artikel [Exception Handling in MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[CException-Klasse](cexception-class.md)<br/>
[Hierarchiediagramm](../hierarchy-chart.md)
