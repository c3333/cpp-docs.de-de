---
title: CreatorMap-Struktur
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
ms.openlocfilehash: 1527f81694d1d809d585f3f6504c0e6433a2c26b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372600"
---
# <a name="creatormap-structure"></a>CreatorMap-Struktur

Unterstützt die Windows Runtime C++-Vorlagenbibliotheksinfrastruktur und ist nicht für die direkte Verwendung aus Ihrem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Bemerkungen

Enthält Informationen zum Initialisieren, Registrieren und Aufheben der Registrierung von Objekten.

`CreatorMap` enthält folgende Informationen:

- Initialisieren, Registrieren und Aufheben der Registrierung von Objekten.

- Vergleichen von Aktivierungsdaten in Abhängigkeit von einer klassischen COM- oder Windows-Runtime-Factory.

- Informationen zum Factorycache und zum Servernamen für eine Schnittstelle.

## <a name="members"></a>Member

### <a name="public-data-members"></a>Öffentliche Datenmember

Name                                          | BESCHREIBUNG
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | Stellt eine Objekt-ID dar, die entweder durch eine klassische COM-Klassen-ID oder einen Windows-Runtime-Namen identifiziert wird.
[CreatorMap::factoryCache](#factorycache)     | Speichert den Zeiger auf den `CreatorMap`Factorycache für die .
[CreatorMap::factoryCreator](#factorycreator) | Erstellt eine Factory `CreatorMap`für die angegebene .
[CreatorMap::serverName](#servername)         | Speichert den Servernamen `CreatorMap`für die .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CreatorMap`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="creatormapactivationid"></a><a name="activationid"></a>CreatorMap::activationId

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
Eine Schnittstellen-ID.

*getRuntimeName*<br/>
Eine Funktion, die den Windows-Laufzeitnamen eines Objekts abruft.

### <a name="remarks"></a>Bemerkungen

Stellt eine Objekt-ID dar, die entweder durch eine klassische COM-Klassen-ID oder einen Windows-Laufzeitnamen identifiziert wird.

## <a name="creatormapfactorycache"></a><a name="factorycache"></a>CreatorMap::factoryCache

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Bemerkungen

Speichert den Zeiger auf den `CreatorMap`Factorycache für die .

## <a name="creatormapfactorycreator"></a><a name="factorycreator"></a>CreatorMap::factoryCreator

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Parameter

*currentflags*<br/>
Einer der RuntimeClassType-Enumeratoren. [RuntimeClassType](runtimeclasstype-enumeration.md)

*Eintrag*<br/>
Eine CreatorMap.

*iidClassFactory*<br/>
Die Schnittstellen-ID einer Klassenfactory.

*Fabrik*<br/>
Wenn der Vorgang abgeschlossen ist, wird die Adresse einer Klassenfabrik.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Erstellt eine Factory für die angegebene CreatorMap.

## <a name="creatormapservername"></a><a name="servername"></a>CreatorMap::serverName

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Bemerkungen

Speichert den Servernamen für die CreatorMap.
