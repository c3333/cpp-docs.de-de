---
title: Registrierungsdaten Austausch-Makros
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
ms.openlocfilehash: 507db77b525c526fe1cd47c7d75c34e15a6a0628
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834543"
---
# <a name="registry-data-exchange-macros"></a>Registrierungsdaten Austausch-Makros

Diese Makros führen Registrierungsdaten Austausch Vorgänge aus.

|Name|Beschreibung|
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Markiert den Anfang der Registrierungsdaten Austausch-Zuordnung.|
|[END_RDX_MAP](#end_rdx_map)|Markiert das Ende der Registrierungsdaten Austausch-Karte.|
|[RDX_BINARY](#rdx_binary)|Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Member-Variablen vom Typ "Byte" zu.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Element Variablen vom Typ CString zu.|
|[RDX_DWORD](#rdx_dword)|Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Element Variablen des Typs DWORD zu.|
|[RDX_TEXT](#rdx_text)|Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Element Variablen des Typs "TCHAR" zu.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLPLUS. h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a> BEGIN_RDX_MAP

Markiert den Anfang der Registrierungsdaten Austausch-Zuordnung.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Bemerkungen

Die folgenden Makros werden innerhalb der Registrierungsdaten Austausch-Zuordnung verwendet, um Einträge in der Systemregistrierung zu lesen und zu schreiben:

|Makro|Beschreibung|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Member-Variablen vom Typ "Byte" zu.|
|[RDX_DWORD](#rdx_dword)|Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Element Variablen des Typs DWORD zu.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Element Variablen vom Typ CString zu.|
|[RDX_TEXT](#rdx_text)|Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Element Variablen des Typs "TCHAR" zu.|

Die globale Funktion " [registrydataexchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)" oder die Element Funktion mit dem gleichen Namen, die mit den Makros "BEGIN_RDX_MAP" und "END_RDX_MAP" erstellt wurde, sollte immer dann verwendet werden, wenn Ihr Code Daten zwischen der Systemregistrierung und den Variablen austauschen muss, die in der RDX-Karte angegeben sind

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a> END_RDX_MAP

Markiert das Ende der Registrierungsdaten Austausch-Karte.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a> RDX_BINARY

Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Member-Variablen vom Typ "Byte" zu.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parameter

*RootKey*<br/>
Der Stamm des Registrierungsschlüssels.

*Unterschlüssel*<br/>
Der Registrierungs Unterschlüssel.

*valueName*<br/>
Der Registrierungsschlüssel.

*Kollege*<br/>
Die Element Variable, die dem angegebenen Registrierungs Eintrag zugeordnet werden soll.

*member_size*<br/>
Die Größe der Element Variablen in Bytes.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in Verbindung mit den Makros für BEGIN_RDX_MAP und END_RDX_MAP verwendet, um eine Member-Variable einem angegebenen Registrierungs Eintrag zuzuordnen. Die globale Funktion " [registrydataexchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)" oder die Element Funktion mit dem gleichen Namen, die mit den Makros "BEGIN_RDX_MAP" und "END_RDX_MAP" erstellt wurde, sollte verwendet werden, um Datenaustausch zwischen der Systemregistrierung und den Element Variablen in der RDX-Zuordnung auszuführen.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a> RDX_CSTRING_TEXT

Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Element Variablen vom Typ CString zu.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parameter

*RootKey*<br/>
Der Stamm des Registrierungsschlüssels.

*Unterschlüssel*<br/>
Der Registrierungs Unterschlüssel.

*valueName*<br/>
Der Registrierungsschlüssel.

*Kollege*<br/>
Die Element Variable, die dem angegebenen Registrierungs Eintrag zugeordnet werden soll.

*member_size*<br/>
Die Größe der Element Variablen in Bytes.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in Verbindung mit den Makros für BEGIN_RDX_MAP und END_RDX_MAP verwendet, um eine Member-Variable einem angegebenen Registrierungs Eintrag zuzuordnen. Die globale Funktion " [registrydataexchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)" oder die Element Funktion mit dem gleichen Namen, die mit den Makros "BEGIN_RDX_MAP" und "END_RDX_MAP" erstellt wurde, sollte verwendet werden, um Datenaustausch zwischen der Systemregistrierung und den Element Variablen in der RDX-Zuordnung auszuführen.

## <a name="rdx_dword"></a><a name="rdx_dword"></a> RDX_DWORD

Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Element Variablen des Typs DWORD zu.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parameter

*RootKey*<br/>
Der Stamm des Registrierungsschlüssels.

*Unterschlüssel*<br/>
Der Registrierungs Unterschlüssel.

*valueName*<br/>
Der Registrierungsschlüssel.

*Kollege*<br/>
Die Element Variable, die dem angegebenen Registrierungs Eintrag zugeordnet werden soll.

*member_size*<br/>
Die Größe der Element Variablen in Bytes.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in Verbindung mit den Makros für BEGIN_RDX_MAP und END_RDX_MAP verwendet, um eine Member-Variable einem angegebenen Registrierungs Eintrag zuzuordnen. Die globale Funktion " [registrydataexchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)" oder die Element Funktion mit dem gleichen Namen, die mit den Makros "BEGIN_RDX_MAP" und "END_RDX_MAP" erstellt wurde, sollte verwendet werden, um Datenaustausch zwischen der Systemregistrierung und den Element Variablen in der RDX-Zuordnung auszuführen.

## <a name="rdx_text"></a><a name="rdx_text"></a> RDX_TEXT

Ordnet den angegebenen Registrierungs Eintrag einer angegebenen Element Variablen des Typs "TCHAR" zu.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parameter

*RootKey*<br/>
Der Stamm des Registrierungsschlüssels.

*Unterschlüssel*<br/>
Der Registrierungs Unterschlüssel.

*valueName*<br/>
Der Registrierungsschlüssel.

*Kollege*<br/>
Die Element Variable, die dem angegebenen Registrierungs Eintrag zugeordnet werden soll.

*member_size*<br/>
Die Größe der Element Variablen in Bytes.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in Verbindung mit den Makros für BEGIN_RDX_MAP und END_RDX_MAP verwendet, um eine Member-Variable einem angegebenen Registrierungs Eintrag zuzuordnen. Die globale Funktion " [registrydataexchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)" oder die Element Funktion mit dem gleichen Namen, die mit den Makros "BEGIN_RDX_MAP" und "END_RDX_MAP" erstellt wurde, sollte verwendet werden, um Datenaustausch zwischen der Systemregistrierung und den Element Variablen in der RDX-Zuordnung auszuführen.

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
