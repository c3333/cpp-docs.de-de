---
title: CAtlFileMappingBase-Klasse
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
ms.openlocfilehash: 16eebfff4330a47888d1b60eaa993ee87d120f72
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748294"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase-Klasse

Diese Klasse stellt eine Speicherzuordnungsdatei dar.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CAtlFileMappingBase
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Der Konstruktor.|
|[CAtlFileMappingBase::-CAtlFileMappingBase](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlFileMappingBase::Kopievon](#copyfrom)|Rufen Sie diese Methode auf, um von einem Dateizuordnungsobjekt zu kopieren.|
|[CAtlFileMappingBase::GetData](#getdata)|Rufen Sie diese Methode auf, um die Daten aus einem Dateizuordnungsobjekt abzurufen.|
|[CAtlFileMappingBase::GetHandle](#gethandle)|Rufen Sie diese Methode auf, um das Dateihandle zurückzugeben.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Rufen Sie diese Methode auf, um die Zuordnungsgröße von einem Dateizuordnungsobjekt abzurufen.|
|[CAtlFileMappingBase::MapFile](#mapfile)|Rufen Sie diese Methode auf, um ein Dateizuordnungsobjekt zu erstellen.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Rufen Sie diese Methode auf, um ein Dateizuordnungsobjekt zu erstellen, das vollen Zugriff auf alle Prozesse ermöglicht.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Rufen Sie diese Methode auf, um ein Handle an das Dateizuordnungsobjekt zurückzugeben.|
|[CAtlFileMappingBase::Unmap](#unmap)|Rufen Sie diese Methode auf, um die Zuordnung eines Dateizuordnungsobjekts aufzuheben.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlFileMappingBase::Operator =](#operator_eq)|Legt das aktuelle Dateizuordnungsobjekt auf ein anderes Dateizuordnungsobjekt fest.|

## <a name="remarks"></a>Bemerkungen

Die Dateizuordnung ist die Zuordnung des Inhalts einer Datei mit einem Teil des virtuellen Adressraums eines Prozesses. Diese Klasse stellt Methoden zum Erstellen von Dateizuordnungsobjekten bereit, mit denen Programme problemlos auf Daten zugreifen und diese freigeben können.

Weitere Informationen finden Sie unter [Dateizuordnung](/windows/win32/Memory/file-mapping) im Windows SDK.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlfile.h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase

Der Konstruktor.

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Parameter

*Orig*<br/>
Das ursprüngliche Dateizuordnungsobjekt, das kopiert werden soll, um das neue Objekt zu erstellen.

### <a name="remarks"></a>Bemerkungen

Erstellt ein neues Dateizuordnungsobjekt, optional mit einem vorhandenen Objekt. Es ist weiterhin notwendig, [CAtlFileMappingBase::MapFile](#mapfile) aufzurufen, um das Dateizuordnungsobjekt für eine bestimmte Datei zu öffnen oder zu erstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a>CAtlFileMappingBase::-CAtlFileMappingBase

Der Destruktor.

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle von der Klasse zugewiesenen Ressourcen frei und ruft die [CAtlFileMappingBase::Unmap-Methode](#unmap) auf.

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a>CAtlFileMappingBase::Kopievon

Rufen Sie diese Methode auf, um von einem Dateizuordnungsobjekt zu kopieren.

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Parameter

*Orig*<br/>
Das ursprüngliche Dateizuordnungsobjekt, aus dem kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a>CAtlFileMappingBase::GetData

Rufen Sie diese Methode auf, um die Daten aus einem Dateizuordnungsobjekt abzurufen.

```cpp
void* GetData() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die Daten zurück.

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a>CAtlFileMappingBase::GetHandle

Rufen Sie diese Methode auf, um ein Handle an das Dateizuordnungsobjekt zurückzugeben.

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Rückgabewert

Gibt ein Handle an das Dateizuordnungsobjekt zurück.

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize

Rufen Sie diese Methode auf, um die Zuordnungsgröße von einem Dateizuordnungsobjekt abzurufen.

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Zuordnungsgröße zurück.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a>CAtlFileMappingBase::MapFile

Rufen Sie diese Methode auf, um ein Dateizuordnungsobjekt für die angegebene Datei zu öffnen oder zu erstellen.

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Parameter

*hDatei*<br/>
Handle für die Datei, aus der ein Zuordnungsobjekt erstellt werden soll. *hFile* muss gültig sein und kann nicht auf INVALID_HANDLE_VALUE festgelegt werden.

*nMappingSize*<br/>
Die Zuordnungsgröße. Wenn 0, entspricht die maximale Größe des Dateizuordnungsobjekts der aktuellen Größe der Datei, die von hFile identifiziert *wird.*

*nOffset*<br/>
Der Dateioffset, bei dem die Zuordnung beginnen soll. Der Offsetwert muss ein Vielfaches der Speicherzuweisungsgranularität des Systems sein.

*dwMappingProtection*<br/>
Der für die Dateiansicht gewünschte Schutz, wenn die Datei zugeordnet wird. Siehe *flProtect* in [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) im Windows SDK.

*dwViewDesiredAccess*<br/>
Gibt den Zugriffstyp für die Dateiansicht und damit den Schutz der seiten an, die der Datei zugeordnet sind. Siehe *dwDesiredAccess* in [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Nachdem ein Dateizuordnungsobjekt erstellt wurde, darf die Größe der Datei die Größe des Dateizuordnungsobjekts nicht überschreiten. Wenn dies der Fall ist, können nicht alle Inhalte der Datei gemeinsam verfügbar sein. Weitere Informationen finden Sie unter [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) und [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) im Windows SDK.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem

Rufen Sie diese Methode auf, um ein Dateizuordnungsobjekt zu erstellen, das vollen Zugriff auf alle Prozesse ermöglicht.

```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parameter

*nMappingSize*<br/>
Die Zuordnungsgröße. Wenn 0, entspricht die maximale Größe des Dateizuordnungsobjekts der aktuellen Größe des Dateizuordnungsobjekts, das durch *szName*identifiziert wird.

*Szname*<br/>
Der Name des Zuordnungsobjekts.

*pbAlreadyExisted*<br/>
Zeigt auf einen BOOL-Wert, der auf TRUE festgelegt ist, wenn das Zuordnungsobjekt bereits vorhanden ist.

*lpsa*<br/>
Der Zeiger auf `SECURITY_ATTRIBUTES` eine Struktur, die bestimmt, ob das zurückgegebene Handle von untergeordneten Prozessen geerbt werden kann. Siehe *lpAttributes* in [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) im Windows SDK.

*dwMappingProtection*<br/>
Der für die Dateiansicht gewünschte Schutz, wenn die Datei zugeordnet wird. Siehe *flProtect* in `CreateFileMapping` im Windows SDK.

*dwViewDesiredAccess*<br/>
Gibt den Zugriffstyp für die Dateiansicht und damit den Schutz der seiten an, die der Datei zugeordnet sind. Siehe *dwDesiredAccess* in [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

`MapShareMem`ermöglicht die gemeinsame Freigabe eines vorhandenen Dateizuordnungsobjekts, das von [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)erstellt wurde.

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a>CAtlFileMappingBase::OpenMapping

Rufen Sie diese Methode auf, um ein benanntes Dateizuordnungsobjekt für die angegebene Datei zu öffnen.

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parameter

*Szname*<br/>
Der Name des Zuordnungsobjekts. Wenn ein offenes Handle für ein Dateizuordnungsobjekt mit diesem Namen vorhanden ist und der Sicherheitsdeskriptor für das Zuordnungsobjekt nicht mit dem Parameter *dwViewDesiredAccess* in Konflikt steht, ist der offene Vorgang erfolgreich.

*nMappingSize*<br/>
Die Zuordnungsgröße. Wenn 0, entspricht die maximale Größe des Dateizuordnungsobjekts der aktuellen Größe des Dateizuordnungsobjekts, das durch *szName*identifiziert wird.

*nOffset*<br/>
Der Dateioffset, bei dem die Zuordnung beginnen soll. Der Offsetwert muss ein Vielfaches der Speicherzuweisungsgranularität des Systems sein.

*dwViewDesiredAccess*<br/>
Gibt den Zugriffstyp für die Dateiansicht und damit den Schutz der seiten an, die der Datei zugeordnet sind. Siehe *dwDesiredAccess* in [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn die Eingabeparameter ungültig sind.

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a>CAtlFileMappingBase::Operator =

Legt das aktuelle Dateizuordnungsobjekt auf ein anderes Dateizuordnungsobjekt fest.

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Parameter

*Orig*<br/>
Das aktuelle Dateizuordnungsobjekt.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das aktuelle Objekt zurück.

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a>CAtlFileMappingBase::Unmap

Rufen Sie diese Methode auf, um die Zuordnung eines Dateizuordnungsobjekts aufzuheben.

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) im Windows SDK.

## <a name="see-also"></a>Weitere Informationen

[CAtlFileMapping-Klasse](../../atl/reference/catlfilemapping-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
