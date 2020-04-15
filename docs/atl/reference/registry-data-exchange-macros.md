---
title: Registrierungsdatenaustauschmakros
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: a7d580e4907cec40f97c0cead616665fff7b8a01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326070"
---
# <a name="registry-data-exchange-macros"></a>Registrierungsdatenaustauschmakros

Diese Makros führen Registrierungsdatenaustauschvorgänge aus.

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Markiert den Anfang der Registrierungsdatenaustauschzuordnung.|
|[END_RDX_MAP](#end_rdx_map)|Markiert das Ende der Registrierungsdatenaustauschzuordnung.|
|[RDX_BINARY](#rdx_binary)|Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ BYTE zu.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ CString zu.|
|[RDX_DWORD](#rdx_dword)|Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ DWORD zu.|
|[RDX_TEXT](#rdx_text)|Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ TCHAR zu.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlplus.h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP

Markiert den Anfang der Registrierungsdatenaustauschzuordnung.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Bemerkungen

Die folgenden Makros werden in der Registry Data Exchange-Zuordnung zum Lesen und Schreiben von Einträgen in der Systemregistrierung verwendet:

|Makro|BESCHREIBUNG|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ BYTE zu.|
|[RDX_DWORD](#rdx_dword)|Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ DWORD zu.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ CString zu.|
|[RDX_TEXT](#rdx_text)|Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ TCHAR zu.|

Die globale Funktion [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)oder die Memberfunktion mit demselben Namen, die von den BEGIN_RDX_MAP und END_RDX_MAP Makros erstellt wurde, sollten immer dann verwendet werden, wenn Der Code Daten zwischen der Systemregistrierung und den in der RDX-Zuordnung angegebenen Variablen austauschen muss.

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a>END_RDX_MAP

Markiert das Ende der Registrierungsdatenaustauschzuordnung.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a>RDX_BINARY

Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ BYTE zu.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parameter

*rootkey*<br/>
Der Stammdesschlüssel des Registrierungsschlüssels.

*Unterschlüssel*<br/>
Der Registrierungsunterschlüssel.

*Valuename*<br/>
Der Registrierungsschlüssel.

*Mitglied*<br/>
Die Membervariable, die dem angegebenen Registrierungseintrag zugeordnet werden soll.

*member_size*<br/>
Die Größe der Membervariablen in Bytes.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in Verbindung mit den BEGIN_RDX_MAP- und END_RDX_MAP-Makros verwendet, um eine Membervariable einem bestimmten Registrierungseintrag zuzuordnen. Die globale Funktion [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)oder die Memberfunktion mit demselben Namen, die von den BEGIN_RDX_MAP und END_RDX_MAP Makros erstellt wurde, sollten verwendet werden, um den Datenaustausch zwischen der Systemregistrierung und den Membervariablen in der RDX-Zuordnung durchzuführen.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT

Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ CString zu.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parameter

*rootkey*<br/>
Der Stammdesschlüssel des Registrierungsschlüssels.

*Unterschlüssel*<br/>
Der Registrierungsunterschlüssel.

*Valuename*<br/>
Der Registrierungsschlüssel.

*Mitglied*<br/>
Die Membervariable, die dem angegebenen Registrierungseintrag zugeordnet werden soll.

*member_size*<br/>
Die Größe der Membervariablen in Bytes.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in Verbindung mit den BEGIN_RDX_MAP- und END_RDX_MAP-Makros verwendet, um eine Membervariable einem bestimmten Registrierungseintrag zuzuordnen. Die globale Funktion [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)oder die Memberfunktion mit demselben Namen, die von den BEGIN_RDX_MAP und END_RDX_MAP Makros erstellt wurde, sollten verwendet werden, um den Datenaustausch zwischen der Systemregistrierung und den Membervariablen in der RDX-Zuordnung durchzuführen.

## <a name="rdx_dword"></a><a name="rdx_dword"></a>RDX_DWORD

Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ DWORD zu.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parameter

*rootkey*<br/>
Der Stammdesschlüssel des Registrierungsschlüssels.

*Unterschlüssel*<br/>
Der Registrierungsunterschlüssel.

*Valuename*<br/>
Der Registrierungsschlüssel.

*Mitglied*<br/>
Die Membervariable, die dem angegebenen Registrierungseintrag zugeordnet werden soll.

*member_size*<br/>
Die Größe der Membervariablen in Bytes.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in Verbindung mit den BEGIN_RDX_MAP- und END_RDX_MAP-Makros verwendet, um eine Membervariable einem bestimmten Registrierungseintrag zuzuordnen. Die globale Funktion [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)oder die Memberfunktion mit demselben Namen, die von den BEGIN_RDX_MAP und END_RDX_MAP Makros erstellt wurde, sollten verwendet werden, um den Datenaustausch zwischen der Systemregistrierung und den Membervariablen in der RDX-Zuordnung durchzuführen.

## <a name="rdx_text"></a><a name="rdx_text"></a>RDX_TEXT

Ordnet den angegebenen Registrierungseintrag einer angegebenen Membervariablen vom Typ TCHAR zu.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parameter

*rootkey*<br/>
Der Stammdesschlüssel des Registrierungsschlüssels.

*Unterschlüssel*<br/>
Der Registrierungsunterschlüssel.

*Valuename*<br/>
Der Registrierungsschlüssel.

*Mitglied*<br/>
Die Membervariable, die dem angegebenen Registrierungseintrag zugeordnet werden soll.

*member_size*<br/>
Die Größe der Membervariablen in Bytes.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in Verbindung mit den BEGIN_RDX_MAP- und END_RDX_MAP-Makros verwendet, um eine Membervariable einem bestimmten Registrierungseintrag zuzuordnen. Die globale Funktion [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)oder die Memberfunktion mit demselben Namen, die von den BEGIN_RDX_MAP und END_RDX_MAP Makros erstellt wurde, sollten verwendet werden, um den Datenaustausch zwischen der Systemregistrierung und den Membervariablen in der RDX-Zuordnung durchzuführen.

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
