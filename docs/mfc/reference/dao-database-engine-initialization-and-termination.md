---
title: Initialisieren und Beenden der DAO-Datenbank-Engine
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 0a70dd396a87315a96224edccf13250a2927cd99
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837592"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Initialisieren und Beenden der DAO-Datenbank-Engine

DAO wird für Access-Datenbanken verwendet und wird von Office 2013 unterstützt. DAO 3,6 ist die endgültige Version, die als veraltet eingestuft wird. Bei der Verwendung von MFC-DAO-Objekten muss das DAO-Datenbankmodul zunächst initialisiert und dann beendet werden, bevor die Anwendung oder dll abgebrochen wird. Zwei Funktionen, `AfxDaoInit` und `AfxDaoTerm` , führen diese Aufgaben aus.

### <a name="dao-database-engine-initialization-and-termination"></a>Initialisieren und Beenden der DAO-Datenbank-Engine

|Name|Beschreibung|
|-|-|
|[AfxDaoInit](#afxdaoinit)|Initialisiert die DAO-Datenbank-Engine.|
|[AfxDaoTerm](#afxdaoterm)|Beendet das DAO-Datenbankmodul.|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a> Afxdaoinit

Mit dieser Funktion wird die DAO-Datenbank-Engine initialisiert.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Bemerkungen

In den meisten Fällen müssen Sie nicht aufrufen, `AfxDaoInit` da die Anwendung Sie automatisch aufruft, wenn Sie benötigt wird.

Weitere Informationen und ein Beispiel für den Aufruf von `AfxDaoInit` finden Sie im [technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdao. h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a> AfxDaoTerm

Diese Funktion beendet das DAO-Datenbankmodul.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Bemerkungen

In der Regel müssen Sie diese Funktion nur in einer regulären MFC-DLL abrufen. eine Anwendung wird automatisch aufgerufen, `AfxDaoTerm` Wenn Sie benötigt wird.

In regulären MFC-DLLs wird `AfxDaoTerm` vor der- `ExitInstance` Funktion aufgerufen, aber nachdem alle MFC-DAO-Objekte zerstört wurden.

Weitere Informationen finden Sie im [technischen Hinweis 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdao. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
