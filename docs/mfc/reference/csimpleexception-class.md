---
title: Csimpleexception-Klasse
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
ms.openlocfilehash: afd83c1ddd6f68b10c5cc8c47c0e939bbd01b6c2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840712"
---
# <a name="csimpleexception-class"></a>Csimpleexception-Klasse

Diese Klasse ist eine Basisklasse für ressourcenkritische MFC-Ausnahmen.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[Csimpleexception:: csimpleexception](#csimpleexception)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Csimpleexception:: getErrorMessage](#geterrormessage)|Stellt Text zu einem Fehler bereit, der aufgetreten ist.|

## <a name="remarks"></a>Bemerkungen

`CSimpleException` ist die Basisklasse für Ressourcen kritische MFC-Ausnahmen und übernimmt den Besitz und die Initialisierung einer Fehlermeldung. Die folgenden Klassen verwenden `CSimpleException` als Basisklasse:

|Name|Beschreibung|
|-|-|
|[Cmemoryexception-Klasse](../../mfc/reference/cmemoryexception-class.md)|Ausnahme wegen nicht genügend Arbeitsspeichers|
|[Cnotsupportedexception-Klasse](../../mfc/reference/cnotsupportedexception-class.md)|Anforderungen für einen nicht unterstützten Vorgang|
|["Kresourceexception"-Klasse](../../mfc/reference/cresourceexception-class.md)|Windows-Ressource nicht gefunden oder nicht erstellbar|
|[Cuserexception-Klasse](../../mfc/reference/cuserexception-class.md)|Eine Ausnahme, die angibt, dass eine Ressource nicht gefunden wurde.|
|[Cinvalidargexception-Klasse](../../mfc/reference/cinvalidargexception-class.md)|Eine Ausnahme, die ein ungültiges Argument angibt.|

Da `CSimpleException` eine abstrakte Basisklasse ist, können Sie ein- `CSimpleException` Objekt nicht direkt deklarieren. Stattdessen müssen Sie abgeleitete Objekte deklarieren, wie z. b. die in der vorherigen Tabelle. Wenn Sie Ihre eigene abgeleitete Klasse deklarieren, verwenden Sie die vorherigen Klassen als Modell.

Weitere Informationen finden Sie im Thema zur [CException-Klasse](../../mfc/reference/cexception-class.md) und [Ausnahmebehandlung (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFX. h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a> Csimpleexception:: csimpleexception

Der Konstruktor.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parameter

*Bauto DELETE*<br/>
Geben Sie true an, wenn der Speicher für das `CSimpleException` Objekt auf dem Heap zugeordnet wurde. Dadurch wird das `CSimpleException` Objekt gelöscht, wenn die Member- `Delete` Funktion aufgerufen wird, um die Ausnahme zu löschen. Geben Sie false an, wenn `CSimpleException` sich das Objekt im Stapel befindet oder wenn es sich um ein globales Objekt handelt. In diesem Fall wird das `CSimpleException` Objekt nicht gelöscht, wenn die `Delete` Member-Funktion aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Dieser Konstruktor muss normalerweise niemals direkt aufgerufen werden. Eine Funktion, die eine Ausnahme auslöst, sollte eine Instanz einer von `CException` abgeleiteten Klasse erstellen und deren Konstruktor aufzurufen, oder Sie sollte eine der MFC-Throw-Funktionen, wie z. b. [afxthrowfileexception](exception-processing.md#afxthrowfileexception), verwenden, um einen vordefinierten Typ auszulösen.

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a> Csimpleexception:: getErrorMessage

Mit dieser Member-Funktion können Sie Text zu einem Fehler bereitstellen, der aufgetreten ist.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Parameter

*lpszError*<br/>
Ein Zeiger auf einen Puffer, der eine Fehlermeldung empfängt.

*nMaxError*<br/>
Die maximale Anzahl von Zeichen, die der Puffer aufnehmen kann, einschließlich des NULL-Terminator.

*pnHelpContext*<br/>
Die Adresse eines uint, von dem die Hilfe Kontext-ID empfangen wird. Wenn der Wert NULL ist, wird keine ID zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Funktion erfolgreich ist. andernfalls 0, wenn kein Fehlermeldungs Text verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [CException:: getErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Ausnahmebehandlung](../../mfc/exception-handling-in-mfc.md)
