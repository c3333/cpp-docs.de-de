---
title: CInternetConnection-Klasse
ms.date: 11/04/2016
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
ms.openlocfilehash: 6649986f279e010a833b31157922cb4fd1ea8613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372423"
---
# <a name="cinternetconnection-class"></a>CInternetConnection-Klasse

Verwaltet die Verbindung mit einem Internetserver.

## <a name="syntax"></a>Syntax

```
class CInternetConnection : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|Erstellt ein `CInternetConnection`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|Ruft die Kontext-ID für dieses Verbindungsobjekt ab.|
|[CInternetConnection::GetServerName](#getservername)|Ruft den Namen des Servers ab, der der Verbindung zugeordnet ist.|
|[CInternetConnection::GetSession](#getsession)|Ruft einen Zeiger auf das [CInternetSession-Objekt](../../mfc/reference/cinternetsession-class.md) ab, das der Verbindung zugeordnet ist.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Ein Handle für eine Internetsitzung.|

## <a name="remarks"></a>Bemerkungen

Sie ist die Basisklasse für die MFC-Klassen [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md)und [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Jede dieser Klassen bietet zusätzliche Funktionen für die Kommunikation mit dem jeweiligen FTP-, HTTP- oder Gopherserver.

Um direkt mit einem Internetserver kommunizieren zu können, `CInternetConnection` benötigen Sie ein [CInternetSession-Objekt](../../mfc/reference/cinternetsession-class.md) und ein Objekt.

Weitere Informationen zur Funktionsweise der WinInet-Klassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a>CInternetConnection::CInternetConnection

Diese Memberfunktion wird `CInternetConnection` aufgerufen, wenn ein Objekt erstellt wird.

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pSession*<br/>
Ein Zeiger auf ein [CInternetSession-Objekt.](../../mfc/reference/cinternetsession-class.md)

*pstrServer*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Servernamen enthält.

*nPort*<br/>
Die Nummer, die den Internetport für diese Verbindung identifiziert.

*dwContext*<br/>
Der Kontextbezeichner für das `CInternetConnection` Objekt. Weitere Informationen zu *dwContext*finden Sie unter **Hinweise** .

### <a name="remarks"></a>Bemerkungen

Du nennst `CInternetConnection` dich nie; Rufen Sie stattdessen die [CInternetSession-Memberfunktion](../../mfc/reference/cinternetsession-class.md) für den Verbindungstyp auf, den Sie einrichten möchten:

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

Der Standardwert für *dwContext* wird von `CInternetConnection`MFC an das -derived-Objekt aus dem [CInternetSession-Objekt](../../mfc/reference/cinternetsession-class.md) gesendet, das das **InternetConnection**-derived-Objekt erstellt hat. Der Standardwert ist auf 1 festgelegt. Sie können jedoch explizit einen bestimmten Kontextbezeichner im [CInternetSession-Konstruktor](../../mfc/reference/cinternetsession-class.md#cinternetsession) für die Verbindung zuweisen. Das Objekt und alle Arbeiten, die es ausführt, werden dieser Kontext-ID zugeordnet. Der Kontextbezeichner wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für das Objekt bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

## <a name="cinternetconnectiongetcontext"></a><a name="getcontext"></a>CInternetConnection::GetContext

Rufen Sie diese Memberfunktion auf, um die Kontext-ID für diese Sitzung abzurufen.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Rückgabewert

Die anwendungsbezogene Kontext-ID.

### <a name="remarks"></a>Bemerkungen

Die Kontext-ID wurde ursprünglich in [CInternetSession](../../mfc/reference/cinternetsession-class.md) angegeben und an `CInternetConnection`- und [CInternetFile](../../mfc/reference/cinternetfile-class.md)- abgeleitete Klassen weitergegeben, es sei denn, sie wird im Aufruf einer Funktion, die die Verbindung öffnet, anders angegeben. Die Kontext-ID ist jedem Vorgang des angegebenen Objekts zugeordnet und identifiziert die Statusinformationen des Vorgangs, die von [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)zurückgegeben werden.

Weitere Informationen dazu, wie `GetContext` mit anderen WinInet-Klassen zur Bereitstellung von Benutzerstatusinformationen funktioniert, finden Sie im Artikel Internet First [Steps: WinInet](../../mfc/wininet-basics.md) für weitere Informationen zum Kontextbezeichner.

## <a name="cinternetconnectiongetservername"></a><a name="getservername"></a>CInternetConnection::GetServerName

Rufen Sie diese Memberfunktion auf, um den Namen des Servers abzurufen, der dieser Internetverbindung zugeordnet ist.

```
CString GetServerName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des Servers, mit dem dieses Verbindungsobjekt arbeitet.

## <a name="cinternetconnectiongetsession"></a><a name="getsession"></a>CInternetConnection::GetSession

Rufen Sie diese Memberfunktion auf, `CInternetSession` um einen Zeiger auf das Objekt abzurufen, das dieser Verbindung zugeordnet ist.

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CInternetSession-Objekt,](../../mfc/reference/cinternetsession-class.md) das diesem Internetverbindungsobjekt zugeordnet ist.

## <a name="cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetConnection::operator HINTERNET

Verwenden Sie diesen Operator, um das Handle auf API-Ebene für die aktuelle Internetsitzung abzusuchen.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
