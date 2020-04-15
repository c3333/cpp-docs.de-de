---
title: CInternetException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
ms.openlocfilehash: b0239afa2b984ccf93d661ec11f11013c89fd912
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372407"
---
# <a name="cinternetexception-class"></a>CInternetException-Klasse

Stellt eine Ausnahmebedingung dar, die sich auf einen Internetvorgang bezieht.

## <a name="syntax"></a>Syntax

```
class CInternetException : public CException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|Erstellt ein `CInternetException`-Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|Der Kontextwert, der dem Vorgang zugeordnet ist, der die Ausnahme verursacht hat.|
|[CInternetException::m_dwError](#m_dwerror)|Der Fehler, der die Ausnahme verursacht hat.|

## <a name="remarks"></a>Bemerkungen

Die `CInternetException` Klasse enthält zwei öffentliche Datenmember: Eines enthält den Der Ausnahme zugeordneten Fehlercode, und der andere enthält den Kontextbezeichner der Internetanwendung, die dem Fehler zugeordnet ist.

Weitere Informationen zu Kontextbezeichnern für Internetanwendungen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>CInternetException::CInternetException

Diese Memberfunktion wird `CInternetException` aufgerufen, wenn ein Objekt erstellt wird.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parameter

*dwError*<br/>
Der Fehler, der die Ausnahme verursacht hat.

### <a name="remarks"></a>Bemerkungen

Um eine CInternetException auszulösen, rufen Sie die globale MFC-Funktion [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)auf.

## <a name="cinternetexceptionm_dwcontext"></a><a name="m_dwcontext"></a>CInternetException::m_dwContext

Der Kontextwert, der dem zugehörigen Internetvorgang zugeordnet ist.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Bemerkungen

Der Kontextbezeichner wurde ursprünglich in [CInternetSession](../../mfc/reference/cinternetsession-class.md) angegeben und von MFC an [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- und [CInternetFile](../../mfc/reference/cinternetfile-class.md)-abgeleitete Klassen übergeben. Sie können diesen Standardwert überschreiben und jedem *dwContext-Parameter* einen Wert Ihrer Wahl zuweisen. *dwContext* ist jeder Operation des angegebenen Objekts zugeordnet. *dwContext* identifiziert die Statusinformationen des Vorgangs, die von [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)zurückgegeben werden.

## <a name="cinternetexceptionm_dwerror"></a><a name="m_dwerror"></a>CInternetException::m_dwError

Der Fehler, der die Ausnahme verursacht hat.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Bemerkungen

Bei diesem Fehlerwert kann es sich um einen Systemfehlercode in WINERROR handelt. H oder ein Fehlerwert von WININET. H.

Eine Liste der Win32-Fehlercodes finden Sie unter [Fehlercodes](/windows/win32/Debug/system-error-codes). Eine Liste der internetspezifischen Fehlermeldungen finden Sie unter . Beide Themen befinden sich im Windows SDK.

## <a name="see-also"></a>Siehe auch

[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CException-Klasse](../../mfc/reference/cexception-class.md)
