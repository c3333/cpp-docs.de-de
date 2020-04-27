---
title: Klasse von "-Klasse"
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
ms.openlocfilehash: 75177c195e83a4ab3ad2a6bd4d608d07f8c2234f
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168084"
---
# <a name="catlfilemappingbase-class"></a>Klasse von "-Klasse"

Diese Klasse stellt eine Speicher Abbild Datei dar.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
class CAtlFileMappingBase
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[' ' ' ' ' ' ' ' ' ': ' '](#catlfilemappingbase)|Der Konstruktor.|
|["": "'" Für ""](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[' ' ' ' ' ' ' ' ' ': ' '](#copyfrom)|Ruft diese Methode auf, um aus einem Datei Zuordnung-Objekt zu kopieren.|
|["": "".](#getdata)|Mit dieser Methode können Sie die Daten aus einem Datei Zuordnung-Objekt abrufen.|
|["" "" "" ".](#gethandle)|Ruft diese Methode auf, um das Datei Handle zurückzugeben.|
|["": "".](#getmappingsize)|Mit dieser Methode können Sie die Größe der Zuordnung von einem Datei Zuordnung-Objekt abrufen.|
|["": "".](#mapfile)|Rufen Sie diese Methode auf, um ein Datei Zuordnung-Objekt zu erstellen.|
|["": "".](#mapsharedmem)|Rufen Sie diese Methode auf, um ein Datei Zuordnungsobjekt zu erstellen, das vollständigen Zugriff auf alle Prozesse zulässt.|
|["Bullfilemappingbase:: openmapping"](#openmapping)|Ruft diese Methode auf, um ein Handle für das Datei Zuordnung-Objekt zurückzugeben.|
|[' ' ' ' ' ' ' ' ' ' ' ' ' ' '](#unmap)|Mit dieser Methode können Sie die Zuordnung eines Datei Zuordnungs Objekts aufheben.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[' ' ' ' ' ' "](#operator_eq)|Legt das aktuelle Datei Zuordnung-Objekt auf ein anderes Datei Zuordnung-Objekt fest.|

## <a name="remarks"></a>Bemerkungen

Die Datei Zuordnung ist die Zuordnung des Inhalts einer Datei zu einem Teil des virtuellen Adressraums eines Prozesses. Diese Klasse stellt Methoden zum Erstellen von Datei Zuordnungsobjekten bereit, die es Programmen ermöglichen, problemlos auf Daten zuzugreifen und diese freizugeben.

Weitere Informationen finden Sie unter [Datei Zuordnung](/windows/win32/Memory/file-mapping) in der Windows SDK.

## <a name="requirements"></a>Anforderungen

**Header:** atlfile. h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a>' ' ' ' ' ' ' ' ' ': ' '

Der Konstruktor.

```cpp
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Parameter

*orig*<br/>
Das ursprüngliche Datei Zuordnung-Objekt, das kopiert werden soll, um das neue-Objekt zu erstellen.

### <a name="remarks"></a>Bemerkungen

Erstellt ein neues Datei Zuordnung-Objekt, wobei optional ein vorhandenes-Objekt verwendet wird. Es ist immer noch [erforderlich, das Datei Zuordnungsobjekt](#mapfile) für eine bestimmte Datei zu öffnen oder zu erstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a>"": "'" Für ""

Der Destruktor.

```cpp
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle Ressourcen frei, die von der-Klasse zugeordnet werden, und [Ruft die Methode](#unmap) "-Methode (Methode)" auf.

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a>' ' ' ' ' ' ' ' ' ': ' '

Ruft diese Methode auf, um aus einem Datei Zuordnung-Objekt zu kopieren.

```cpp
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Parameter

*orig*<br/>
Das ursprüngliche Datei Zuordnung-Objekt, aus dem kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a>"": "".

Mit dieser Methode können Sie die Daten aus einem Datei Zuordnung-Objekt abrufen.

```cpp
void* GetData() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die Daten zurück.

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a>"" "" "" ".

Ruft diese Methode auf, um ein Handle für das Datei Zuordnung-Objekt zurückzugeben.

```cpp
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Rückgabewert

Gibt ein Handle für das Datei Zuordnung-Objekt zurück.

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a>"": "".

Mit dieser Methode können Sie die Größe der Zuordnung von einem Datei Zuordnung-Objekt abrufen.

```cpp
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Größe der Zuordnung zurück.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für die [Datei](#catlfilemappingbase)"" für "".

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a>"": "".

Rufen Sie diese Methode auf, um ein Datei Zuordnung-Objekt für die angegebene Datei zu öffnen oder zu erstellen.

```cpp
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Parameter

*hFile*<br/>
Handle für die Datei, aus der ein Mapping-Objekt erstellt werden soll. *hFile* muss gültig sein und kann nicht auf INVALID_HANDLE_VALUE festgelegt werden.

*nmappingsize*<br/>
Die Größe der Zuordnung. Wenn der Wert 0 ist, entspricht die maximale Größe des Datei Mapping-Objekts der aktuellen Größe der durch *hFile* identifizierten Datei.

*nOffset*<br/>
Der Dateioffset, bei dem die Zuordnung begonnen werden soll. Der Offset-Wert muss ein Vielfaches der Granularität der Speicher Belegung des Systems sein.

*dwmappingprotection*<br/>
Der für die Dateiansicht gewünschte Schutz, wenn die Datei zugeordnet wird. Weitere Informationen finden Sie unter *flprotect* [in der](/windows/win32/api/winbase/nf-winbase-createfilemappinga) Windows SDK.

*dwviewdesiredaccess*<br/>
Gibt den Typ des Zugriffs auf die Dateiansicht und somit den Schutz der Seiten an, die von der Datei zugeordnet werden. Weitere Informationen finden Sie in der Windows SDK unter *dwDesiredAccess* in [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) .

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Nachdem ein Datei Zuordnung-Objekt erstellt wurde, darf die Größe der Datei nicht größer sein als das Datei Zuordnung-Objekt. Wenn dies der Fall ist, sind nicht alle Inhalte der Datei für die Freigabe verfügbar. Weitere Informationen finden Sie unter " [kreatefilemapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) " und " [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) " in der Windows SDK.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für die [Datei](#catlfilemappingbase)"" für "".

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a>"": "".

Rufen Sie diese Methode auf, um ein Datei Zuordnungsobjekt zu erstellen, das vollständigen Zugriff auf alle Prozesse zulässt.

```cpp
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parameter

*nmappingsize*<br/>
Die Größe der Zuordnung. Wenn der Wert 0 ist, entspricht die maximale Größe des Datei Mapping-Objekts der aktuellen Größe des durch *szName*identifizierten Datei Mapping-Objekts.

*szName*<br/>
Der Name des Mapping-Objekts.

*pballesist vorhanden*<br/>
Verweist auf einen booleschen Wert, der auf true festgelegt ist, wenn das Zuordnungsobjekt bereits vorhanden war.

*lpsa*<br/>
Der Zeiger auf eine `SECURITY_ATTRIBUTES` -Struktur, die bestimmt, ob das zurückgegebene Handle von untergeordneten Prozessen geerbt werden kann. Weitere Informationen finden Sie unter *lpattributes* [in der](/windows/win32/api/winbase/nf-winbase-createfilemappinga) Windows SDK.

*dwmappingprotection*<br/>
Der für die Dateiansicht gewünschte Schutz, wenn die Datei zugeordnet wird. Weitere Informationen finden Sie `CreateFileMapping` in der Windows SDK unter *flprotect* .

*dwviewdesiredaccess*<br/>
Gibt den Typ des Zugriffs auf die Dateiansicht und somit den Schutz der Seiten an, die von der Datei zugeordnet werden. Weitere Informationen finden Sie in der Windows SDK unter *dwDesiredAccess* in [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) .

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

`MapShareMem`ermöglicht, dass ein vorhandenes Datei Zuordnungsobjekt, das von " [kreatefilemapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)" erstellt wurde, von Prozessen gemeinsam verwendet wird.

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a>"Bullfilemappingbase:: openmapping"

Ruft diese Methode auf, um ein benanntes Datei Zuordnung-Objekt für die angegebene Datei zu öffnen.

```cpp
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parameter

*szName*<br/>
Der Name des Mapping-Objekts. Wenn ein geöffnetes Handle für ein Datei Zuordnungs Objekt mit diesem Namen vorhanden ist und die Sicherheits Beschreibung für das Zuordnungs Objekt nicht mit dem Parameter *dwviewdesiredaccess* in Konflikt steht, wird der Öffnungsvorgang erfolgreich ausgeführt.

*nmappingsize*<br/>
Die Größe der Zuordnung. Wenn der Wert 0 ist, entspricht die maximale Größe des Datei Mapping-Objekts der aktuellen Größe des durch *szName*identifizierten Datei Mapping-Objekts.

*nOffset*<br/>
Der Dateioffset, bei dem die Zuordnung begonnen werden soll. Der Offset-Wert muss ein Vielfaches der Granularität der Speicher Belegung des Systems sein.

*dwviewdesiredaccess*<br/>
Gibt den Typ des Zugriffs auf die Dateiansicht und somit den Schutz der Seiten an, die von der Datei zugeordnet werden. Weitere Informationen finden Sie in der Windows SDK unter *dwDesiredAccess* in [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) .

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Fehler auf, wenn die Eingabeparameter ungültig sind.

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a>' ' ' ' ' ' "

Legt das aktuelle Datei Zuordnung-Objekt auf ein anderes Datei Zuordnung-Objekt fest.

```cpp
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Parameter

*orig*<br/>
Das aktuelle Datei Zuordnung-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das aktuelle-Objekt zurück.

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a>' ' ' ' ' ' ' ' ' ' ' ' ' ' '

Mit dieser Methode können Sie die Zuordnung eines Datei Zuordnungs Objekts aufheben.

```cpp
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) im Windows SDK.

## <a name="see-also"></a>Weitere Informationen:

[Klasse von "Klasse"](../../atl/reference/catlfilemapping-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
