---
title: CSocketAddr-Klasse
ms.date: 10/22/2018
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
ms.openlocfilehash: 66d33d62212389a2b0f318250c1c16a99167c6eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330685"
---
# <a name="csocketaddr-class"></a>CSocketAddr-Klasse

Diese Klasse stellt Methoden zum Konvertieren von Hostnamen in Hostadressen bereit und unterstützt sowohl IPv4- als auch IPV6-Formate.

## <a name="syntax"></a>Syntax

```
class CSocketAddr
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|Rufen Sie diese Methode auf, um den angegebenen Hostnamen in die Hostadresse zu konvertieren.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Rufen Sie diese Methode auf, um den IPv4-Hostnamen in die Hostadresse zu konvertieren.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Rufen Sie diese Methode auf, um den IPv6-Hostnamen in die Hostadresse zu konvertieren.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Rufen Sie diese Methode auf, um einen `addrinfo` Zeiger auf ein bestimmtes Element in der Liste zurückzugeben.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Rufen Sie diese Methode auf, `addrinfo` um einen Zeiger auf die Liste zurückzugeben.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bietet einen agnostischen ANSATZ für die IP-Version zum Suchen von Netzwerkadressen für die Verwendung mit Windows-Socket-API-Funktionen und Socket-Wrappern in Bibliotheken.

Die Member dieser Klasse, die zum Nachschlagen von Netzwerkadressen verwendet werden, verwenden die Win32-API-Funktion [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). Die ANSI- oder UNICODE-Version der Funktion wird aufgerufen, je nachdem, ob Ihr Code für ANSI oder UNICODE kompiliert wird.

Diese Klasse unterstützt sowohl IPv4- als auch IPv6-Netzwerkadressen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsocket.h

## <a name="csocketaddrcsocketaddr"></a><a name="csocketaddr"></a>CSocketAddr::CSocketAddr

Der Konstruktor.

```
CSocketAddr();
```

### <a name="remarks"></a>Bemerkungen

Erstellt ein `CSocketAddr` neues Objekt und initialisiert die verknüpfte Liste mit Antwortinformationen über den Host.

## <a name="csocketaddrfindaddr"></a><a name="findaddr"></a>CSocketAddr::FindAddr

Rufen Sie diese Methode auf, um den angegebenen Hostnamen in die Hostadresse zu konvertieren.

```
int FindAddr(
    const TCHAR *szHost,
    const TCHAR *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const TCHAR *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>Parameter

*szHost*<br/>
Der Hostname oder die gepunktete IP-Adresse.

*szPortOrServiceName*<br/>
Die Portnummer oder der Name des Dienstes auf dem Host.

*nPortNo*<br/>
Die Portnummer.

*Flaggen*<br/>
0 oder Kombination aus AI_PASSIVE, AI_CANONNAME oder AI_NUMERICHOST.

*addr_family*<br/>
Adressfamilie (z. B. PF_INET).

*sock_type*<br/>
Sockettyp (z. B. SOCK_STREAM).

*ai_proto*<br/>
Protokoll (z. B. IPPROTO_IP oder IPPROTO_IPV6).

### <a name="return-value"></a>Rückgabewert

Gibt Null zurück, wenn die Adresse erfolgreich berechnet wurde. Gibt bei einem Fehler einen Fehlercode ungleich Null von Null zurück. Bei Erfolg wird die berechnete Adresse in einer verknüpften Liste gespeichert, auf die mit `CSocketAddr::GetAddrInfoList` und `CSocketAddr::GetAddrInfo`verwiesen werden kann.

### <a name="remarks"></a>Bemerkungen

Der Parameter Hostname kann entweder im IPv4- oder IPv6-Format vorliegen. Diese Methode ruft die Win32-API-Funktion [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) auf, um die Konvertierung durchzuführen.

## <a name="csocketaddrfindinet4addr"></a><a name="findinet4addr"></a>CSocketAddr::FindINET4Addr

Rufen Sie diese Methode auf, um den IPv4-Hostnamen in die Hostadresse zu konvertieren.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parameter

*szHost*<br/>
Der Hostname oder die gepunktete IP-Adresse.

*nPortNo*<br/>
Die Portnummer.

*Flaggen*<br/>
0 oder Kombination aus AI_PASSIVE, AI_CANONNAME oder AI_NUMERICHOST.

*sock_type*<br/>
Sockettyp (z. B. SOCK_STREAM).

### <a name="return-value"></a>Rückgabewert

Gibt Null zurück, wenn die Adresse erfolgreich berechnet wurde. Gibt bei einem Fehler einen Fehlercode ungleich Null von Null zurück. Bei Erfolg wird die berechnete Adresse in einer verknüpften Liste gespeichert, auf die mit `CSocketAddr::GetAddrInfoList` und `CSocketAddr::GetAddrInfo`verwiesen werden kann.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft die Win32-API-Funktion [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) auf, um die Konvertierung durchzuführen.

## <a name="csocketaddrfindinet6addr"></a><a name="findinet6addr"></a>CSocketAddr::FindINET6Addr

Rufen Sie diese Methode auf, um den IPv6-Hostnamen in die Hostadresse zu konvertieren.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parameter

*szHost*<br/>
Der Hostname oder die gepunktete IP-Adresse.

*nPortNo*<br/>
Die Portnummer.

*Flaggen*<br/>
0 oder Kombination aus AI_PASSIVE, AI_CANONNAME oder AI_NUMERICHOST.

*sock_type*<br/>
Sockettyp (z. B. SOCK_STREAM).

### <a name="return-value"></a>Rückgabewert

Gibt Null zurück, wenn die Adresse erfolgreich berechnet wurde. Gibt bei einem Fehler einen Fehlercode ungleich Null von Null zurück. Bei Erfolg wird die berechnete Adresse in einer verknüpften Liste gespeichert, auf die mit `CSocketAddr::GetAddrInfoList` und `CSocketAddr::GetAddrInfo`verwiesen werden kann.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft die Win32-API-Funktion [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) auf, um die Konvertierung durchzuführen.

## <a name="csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo

Rufen Sie diese Methode auf, um einen `addrinfo` Zeiger auf ein bestimmtes Element in der Liste zurückzugeben.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Verweis auf ein bestimmtes Element in der [addrinfo-Liste.](/windows/win32/api/ws2def/ns-ws2def-addrinfow)

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger `addrinfo` auf die Struktur zurück, auf die *nIndex* in der verknüpften Liste verweist, die Antwortinformationen über den Host enthält.

## <a name="csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList

Rufen Sie diese Methode auf, `addrinfo` um einen Zeiger auf die Liste zurückzugeben.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Rückgabewert

Zeigen Sie auf eine verknüpfte `addrinfo` Liste einer oder mehrerer Strukturen, die Antwortinformationen über den Host enthalten. Weitere Informationen finden Sie unter [addrinfo-Struktur](/windows/win32/api/ws2def/ns-ws2def-addrinfow).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
