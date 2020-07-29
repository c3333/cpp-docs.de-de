---
title: Cmemoryexception-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 71b17e777db9d6351192da7cffd075b3a64553bd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222926"
---
# <a name="cmemoryexception-class"></a>Cmemoryexception-Klasse

Stellt eine Ausnahmebedingung dar, die durch ungenügenden Arbeitsspeicher ausgelöst wird.

## <a name="syntax"></a>Syntax

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[Cmemoryexception:: cmemoryexception](#cmemoryexception)|Erstellt ein `CMemoryException`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Es ist keine weitere Qualifizierung erforderlich oder möglich. Speicher Ausnahmen werden automatisch von ausgelöst **`new`** . Wenn Sie z. b. eigene Speicherfunktionen mit schreiben, `malloc` sind Sie für das Auslösen von Speicher Ausnahmen verantwortlich.

Weitere Informationen zu finden Sie im `CMemoryException` Artikel [Ausnahmebehandlung (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFX. h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>Cmemoryexception:: cmemoryexception

Erstellt ein `CMemoryException`-Objekt.

```
CMemoryException();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Konstruktor nicht direkt, sondern stattdessen die globale Funktion [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Diese globale Funktion kann in einer nicht genügend Arbeitsspeicher Situation auftreten, da Sie das Ausnahme Objekt in zuvor zugewiesener Arbeitsspeicher erstellt. Weitere Informationen zur Ausnahme Verarbeitung finden Sie im Artikel [Ausnahmen](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[CException-Klasse](cexception-class.md)<br/>
[Hierarchie Diagramm](../hierarchy-chart.md)
