---
title: Microsoft::WRL-Namespace
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
ms.openlocfilehash: c92251dacbfa17e8f1ac0cbdc41aa9b06118ac91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213771"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL-Namespace

Definiert die grundlegenden Typen, die die Windows-Runtime C++ Vorlagen Bibliothek bilden.

## <a name="syntax"></a>Syntax

```cpp
namespace Microsoft::WRL;
```

## <a name="members"></a>Members

### <a name="typedefs"></a>TypeDefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt | InhibitWeakReference>`|

### <a name="classes"></a>Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ActivationFactory-Klasse](activationfactory-class.md)|Ermöglicht, dass eine oder mehrere Klassen durch die Windows-Runtime aktiviert werden.|
|[AsyncBase-Klasse](asyncbase-class.md)|Implementiert den asynchronen Zustandsautomat der Windows-Runtime.|
|[ClassFactory-Klasse](classfactory-class.md)|Implementiert die grundlegende Funktion der `IClassFactory`-Schnittstelle.|
|[ComPtr-Klasse](comptr-class.md)|Erstellt einen *intelligenten Zeigertyp* , der die Schnittstelle darstellt, die vom Vorlagenparameter angegeben wird. ComPtr verwaltet automatisch einen Verweiszähler für den zugrunde liegenden Schnittstellenzeiger und gibt die Schnittstelle frei, wenn der Verweiszähler auf 0 geht.|
|[DeferrableEventArgs-Klasse](deferrableeventargs-class.md)|Eine für die Ereignisargumenttypen für Verzögerungen verwendete Vorlagenklasse.|
|[EventSource-Klasse](eventsource-class.md)|Stellt ein Ereignis dar. `EventSource`-Memberfunktionen fügen Ereignishandler hinzu, entfernen sie und rufen sie auf.|
|[FtmBase-Klasse](ftmbase-class.md)|Stellt ein Freethread-Marshaller-Objekt dar.|
|[Module-Klasse](module-class.md)|Stellt eine Auflistung von zugehörigen Objekten dar.|
|[RuntimeClass-Klasse](runtimeclass-class.md)|Stellt eine instanziierte Klasse dar, die die angegebene Anzahl von Schnittstellen erbt, und gewährt Unterstützung für die angegebene Windows-Runtime, klassisches COM und schwache Verweise.|
|[SimpleActivationFactory-Klasse](simpleactivationfactory-class.md)|Stellt einen grundlegenden Mechanismus für das Erstellen einer Windows-Runtime oder einer klassischen COM-Basisklasse bereit.|
|[SimpleClassFactory-Klasse](simpleclassfactory-class.md)|Stellt einen grundlegenden Mechanismus zum Erstellen einer Basisklasse bereit.|
|[WeakRef-Klasse](weakref-class.md)|Stellt einen *schwachen Verweis* dar, der nur durch die Windows-Runtime und nicht durch die klassische COM verwendet werden kann. Ein schwacher Verweis repräsentiert ein Objekt, auf das möglicherweise zugegriffen werden kann.|

### <a name="structures"></a>Strukturen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ChainInterfaces-Struktur](chaininterfaces-structure.md)|Gibt Überprüfungs- und Initialisierungsfunktionen an, die auf einen Satz von Schnittstellen-IDs angewendet werden können.|
|[CloakedIid-Struktur](cloakediid-structure.md)|Gibt dem `RuntimeClass`-, `Implements`-und `ChainInterfaces`-Vorlagen an, dass auf die angegebene Schnittstelle in der IID-Liste nicht zugegriffen werden kann.|
|[Implements-Struktur](implements-structure.md)|Implementiert `QueryInterface` und `GetIid` für die angegebenen Schnittstellen.|
|[MixIn-Struktur](mixin-structure.md)|Stellt sicher, dass eine Runtime-Klasse aus Windows-Runtime-Schnittstellen (sofern vorhanden) und dann aus klassischen COM-Schnittstellen abgeleitet wird.|
|[RuntimeClassFlags-Struktur](runtimeclassflags-structure.md)|Enthält den Typ für eine Instanz einer [runtimeclass](runtimeclass-class.md).|

### <a name="enumerations"></a>Enumerationen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[AsyncResultType-Enumeration](asyncresulttype-enumeration.md)|Gibt den Ergebnistyp an, der von der `GetResults()` Methode zurückgegeben wird.|
|[ModuleType-Enumeration](moduletype-enumeration.md)|Gibt an, ob ein Modul einen In-Process-Server oder einen Out-of-Process-Server unterstützen sollte.|
|[RuntimeClassType-Enumeration](runtimeclasstype-enumeration.md)|Gibt den Typ der unterstützten [runtimeclass](runtimeclass-class.md) -Instanz an.|

### <a name="functions"></a>Functions

|Name|BESCHREIBUNG|
|----------|-----------------|
|[AsWeak-Funktion](asweak-function.md)|Ruft einen schwachen Verweis zur angegebenen Instanz ab.|
|[Rückruffunktion (WRL)](callback-function-wrl.md)|Erstellt ein Objekt, dessen Memberfunktion eine Rückrufmethode ist.|
|[CreateActivationFactory-Funktion](createactivationfactory-function.md)|Erstellt eine Instanzen der angegebenen Klasse erstellende Factory, die durch die Windows-Runtime aktiviert werden kann.|
|[CreateClassFactory-Funktion](createclassfactory-function.md)|Erstellt eine Factory, die Instanzen der angegebenen Klasse erstellt.|
|[Make-Funktion](make-function.md)|Initialisiert die angegebene Windows-Runtime-Klasse.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Async. h, Client. h, corewrappers. h, Event. h, FTM. h, implementiert. h, Internal. h, Module. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Wrappers-Namespace](microsoft-wrl-wrappers-namespace.md)
