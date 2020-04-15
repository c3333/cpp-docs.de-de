---
title: Initialisieren und Beenden der DAO-Datenbank-Engine
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 62460e8e55f70b8cb0743f1d044636d25121050d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365896"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Initialisieren und Beenden der DAO-Datenbank-Engine

DAO wird mit Access-Datenbanken verwendet und wird über Office 2013 unterstützt. DAO 3.6 ist die endgültige Version und gilt als veraltet. Bei Verwendung von MFC-DAO-Objekten muss das DAO-Datenbankmodul zuerst initialisiert und dann beendet werden, bevor die Anwendung oder DLL beendet wird. Diese Aufgaben `AfxDaoInit` `AfxDaoTerm`werden von zwei Funktionen ausgeführt.

### <a name="dao-database-engine-initialization-and-termination"></a>Initialisieren und Beenden der DAO-Datenbank-Engine

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Initialisiert das DAO-Datenbankmodul.|
|[AfxDaoTerm](#afxdaoterm)|Beendet das DAO-Datenbankmodul.|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a>AfxDaoInit

Diese Funktion initialisiert das DAO-Datenbankmodul.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Bemerkungen

In den meisten Fällen müssen Sie `AfxDaoInit` nicht aufrufen, da die Anwendung sie automatisch aufruft, wenn sie benötigt wird.

Weitere Informationen und ein Beispiel `AfxDaoInit`für den Aufruf finden Sie unter [Technische Anmerkung 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a>AfxDaoTerm

Diese Funktion beendet das DAO-Datenbankmodul.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Bemerkungen

In der Regel müssen Sie diese Funktion nur in einer regulären MFC-DLL aufrufen. Eine Anwendung ruft `AfxDaoTerm` automatisch auf, wenn sie benötigt wird.

Rufen Sie in regulären `AfxDaoTerm` MFC-DLLs vor der `ExitInstance` Funktion auf, aber schließlich wurden MFC-DAO-Objekte zerstört.

Weitere Informationen finden Sie unter [Technische Anmerkung 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
