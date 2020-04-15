---
title: CNotSupportedException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
ms.openlocfilehash: b859b939baef018e69b245e597eea90e608253ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363195"
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException-Klasse

Stellt eine Ausnahme dar, die das Ergebnis der Anforderung einer nicht unterstützten Funktion ist.

## <a name="syntax"></a>Syntax

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Erstellt ein `CNotSupportedException`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Eine weitere Qualifizierung ist nicht erforderlich oder möglich.

Weitere Informationen zur `CNotSupportedException`Verwendung finden Sie im Artikel [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="cnotsupportedexceptioncnotsupportedexception"></a><a name="cnotsupportedexception"></a>CNotSupportedException::CNotSupportedException

Erstellt ein `CNotSupportedException`-Objekt.

```
CNotSupportedException();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Konstruktor nicht direkt, sondern rufen Sie die globale Funktion [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)auf. Weitere Informationen zur Ausnahmeverarbeitung finden Sie im Artikel [Exception Handling in MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[CException-Klasse](cexception-class.md)<br/>
[Hierarchiediagramm](../hierarchy-chart.md)
