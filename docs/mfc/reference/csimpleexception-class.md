---
title: CSimpleException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
ms.openlocfilehash: eb94ba9e3d26b3cd910f23c3d4abb29d3b8b1cd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318365"
---
# <a name="csimpleexception-class"></a>CSimpleException-Klasse

Diese Klasse ist eine Basisklasse für ressourcenkritische MFC-Ausnahmen.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleException::CSimpleException](#csimpleexception)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleException::GetErrorMessage](#geterrormessage)|Stellt Text zu einem aufgetretenen Fehler bereit.|

## <a name="remarks"></a>Bemerkungen

`CSimpleException`ist die Basisklasse für ressourcenkritische MFC-Ausnahmen und behandelt den Besitz und die Initialisierung einer Fehlermeldung. Die folgenden `CSimpleException` Klassen verwenden als Basisklasse:

|||
|-|-|
|[CMemoryException-Klasse](../../mfc/reference/cmemoryexception-class.md)|Außerspeicher-Ausnahme|
|[CNotSupportedException-Klasse](../../mfc/reference/cnotsupportedexception-class.md)|Anforderungen für einen nicht unterstützten Vorgang|
|[CResourceException-Klasse](../../mfc/reference/cresourceexception-class.md)|Windows-Ressource nicht gefunden oder nicht verunstetzbar|
|[CUserException-Klasse](../../mfc/reference/cuserexception-class.md)|Ausnahme, die angibt, dass eine Ressource nicht gefunden wurde|
|[CInvalidArgException-Klasse](../../mfc/reference/cinvalidargexception-class.md)|Ausnahme, die ein ungültiges Argument angibt|

Da `CSimpleException` es sich um eine abstrakte `CSimpleException` Basisklasse handelt, können Sie ein Objekt nicht direkt deklarieren. Stattdessen müssen Sie abgeleitete Objekte wie die in der vorherigen Tabelle deklarieren. Wenn Sie eine eigene abgeleitete Klasse deklarieren, verwenden Sie die vorherigen Klassen als Modell.

Weitere Informationen finden Sie im Thema [CException Class](../../mfc/reference/cexception-class.md) und [In Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a>CSimpleException::CSimpleException

Der Konstruktor.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parameter

*bAutoDelete*<br/>
Geben Sie TRUE an, wenn der Speicher für das `CSimpleException` Objekt auf dem Heap zugewiesen wurde. Dies führt `CSimpleException` dazu, dass `Delete` das Objekt gelöscht wird, wenn die Memberfunktion aufgerufen wird, um die Ausnahme zu löschen. Geben Sie `CSimpleException` FALSE an, wenn sich das Objekt auf dem Stapel befindet oder ein globales Objekt ist. In diesem Fall `CSimpleException` wird das Objekt `Delete` nicht gelöscht, wenn die Memberfunktion aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Normalerweise müssten Sie diesen Konstruktor normalerweise nie direkt aufrufen. Eine Funktion, die eine Ausnahme auslöst, sollte eine Instanz einer `CException`-derived-Klasse erstellen und ihren Konstruktor aufrufen, oder sie sollte eine der MFC-Throw-Funktionen verwenden, z. B. [AfxThrowFileException](exception-processing.md#afxthrowfileexception), um einen vordefinierten Typ auszulösen.

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a>CSimpleException::GetErrorMessage

Rufen Sie diese Memberfunktion auf, um Text zu einem aufgetretenen Fehler bereitzustellen.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Parameter

*lpszError*<br/>
Ein Zeiger auf einen Puffer, der eine Fehlermeldung erhält.

*nMaxError*<br/>
Die maximale Anzahl von Zeichen, die der Puffer enthalten kann, einschließlich des NULL-Terminators.

*pnHelpContext*<br/>
Die Adresse eines UINT, der die Hilfekontext-ID erhält. Wenn NULL, wird keine ID zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; andernfalls 0, wenn kein Fehlermeldungstext verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Ausnahmebehandlung](../../mfc/exception-handling-in-mfc.md)
