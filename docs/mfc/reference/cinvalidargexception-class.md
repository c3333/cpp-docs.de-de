---
title: CInvalidArgException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: b28b6e84043b85a8117694a67ff5fff13e7c786b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372366"
---
# <a name="cinvalidargexception-class"></a>CInvalidArgException-Klasse

Diese Klasse stellt eine Ausnahmebedingung für ein ungültiges Argument dar.

## <a name="syntax"></a>Syntax

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|Der Konstruktor.|

## <a name="remarks"></a>Bemerkungen

Ein `CInvalidArgException` Objekt stellt eine ungültige Argumentausnahmebedingung dar.

Weitere Informationen zur Ausnahmebehandlung finden Sie im [CException-Klassenthema](../../mfc/reference/cexception-class.md) und [in der Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="cinvalidargexceptioncinvalidargexception"></a><a name="cinvalidargexception"></a>CInvalidArgException::CInvalidArgException

Der Konstruktor.

```
CInvalidArgException();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Konstruktor nicht direkt. rufen Sie die globale Funktion **AfxThrowInvalidArgException**auf.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CSimpleException-Klasse](../../mfc/reference/csimpleexception-class.md)
