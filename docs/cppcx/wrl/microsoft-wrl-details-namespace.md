---
title: Microsoft::WRL::Details-Namespace
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: 4e8d2e5a2c7e6655674c4e965cd7222d930dff9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213784"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details-Namespace

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Members

### <a name="classes"></a>Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ComPtrRef-Klasse](comptrref-class.md)|Stellt einen Verweis auf ein Objekt vom Typ comptr\<t > dar.|
|[ComPtrRefBase-Klasse](comptrrefbase-class.md)|Stellt die Basisklasse für die [comptrref](comptrref-class.md) -Klasse dar.|
|[DontUseNewUseMake-Klasse](dontusenewusemake-class.md)|Verhindert die Verwendung von Operator `new` in `RuntimeClass`. Folglich müssen Sie stattdessen die [make-Funktion](make-function.md) verwenden.|
|[EventTargetArray-Klasse](eventtargetarray-class.md)|Stellt ein Array von Ereignis Handlern dar.|
|[MakeAllocator-Klasse](makeallocator-class.md)|Ordnet Speicher für eine aktivierbare Klasse mit oder ohne Unterstützung für schwache Verweise zu.|
|[ModuleBase-Klasse](modulebase-class.md)|Stellt die Basisklasse der [Modul](module-class.md) Klassen dar.|
|[RemoveIUnknown-Klasse](removeiunknown-class.md)|Gibt einen Typ an, der einem `IUnknown`basierten Typ entspricht, aber nicht virtuelle `QueryInterface`-, `AddRef`-und `Release`-Methoden aufweist.|
|[WeakReference-Klasse](weakreference-class.md)|Stellt einen *schwachen Verweis* dar, der mit dem Windows-Runtime oder dem klassischen com verwendet werden kann. Ein schwacher Verweis repräsentiert ein Objekt, auf das möglicherweise zugegriffen werden kann.|

### <a name="structures"></a>Strukturen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ArgTraits-Struktur](argtraits-structure.md)|Deklariert eine angegebene delegatschnittstelle und eine anonyme Member-Funktion, die über eine angegebene Anzahl von Parametern verfügt.|
|[ArgTraitsHelper-Struktur](argtraitshelper-structure.md)|Unterstützt die Definition allgemeiner Merkmale von delegatargumenten.|
|[BoolStruct-Struktur](boolstruct-structure.md)|Definiert, ob ein `ComPtr` die Objekt Lebensdauer einer Schnittstelle verwaltet. `BoolStruct` wird intern vom [booltype ()](comptr-class.md#operator-microsoft-wrl-details-booltype) -Operator verwendet.|
|[CreatorMap-Struktur](creatormap-structure.md)|Enthält Informationen zum Initialisieren, registrieren und Aufheben der Registrierung von Objekten.|
|[DerefHelper-Struktur](derefhelper-structure.md)|Stellt einen dereferenzierten Zeiger auf den `T*` Template-Parameter dar.|
|[EnableIf-Struktur](enableif-structure.md)|Definiert einen Datenmember des Typs, der durch den zweiten Vorlagen Parameter angegeben wird, wenn der erste Vorlagen Parameter als `true`ausgewertet wird.|
|[FactoryCache-Struktur](factorycache-structure.md)|Enthält den Speicherort einer Klassenfactory und einen Wert, der ein registriertes Windows-Runtime-oder com-Klassenobjekt identifiziert.|
|[ImplementsBase-Struktur](implementsbase-structure.md)|Wird zum Überprüfen von Vorlagen Parametertypen in die- [Struktur implementiert](implements-structure.md).|
|[ImplementsHelper-Struktur](implementshelper-structure.md)|Hilft [bei der Implementierung der implementierten](implements-structure.md) -Struktur.|
|[InterfaceList-Struktur](interfacelist-structure.md)|Wird verwendet, um eine rekursive Liste von Schnittstellen zu erstellen.|
|[InterfaceListHelper-Struktur](interfacelisthelper-structure.md)|Erstellt einen `InterfaceList` Typ, indem die angegebenen Vorlagen Parameter Argumente rekursiv angewendet werden.|
|[InterfaceTraits-Struktur](interfacetraits-structure.md)|Implementiert allgemeine Merkmale einer Schnittstelle.|
|[InvokeHelper-Struktur](invokehelper-structure.md)|Stellt eine Implementierung der `Invoke()`-Methode basierend auf der angegebenen Anzahl und dem Typ von Argumenten bereit.|
|[IsBaseOfStrict-Struktur](isbaseofstrict-structure.md)|Testet, ob ein Typ die Basis eines anderen ist.|
|[IsSame-Struktur](issame-structure.md)|Testet, ob ein angegebener Typ mit einem anderen angegebenen Typ identisch ist.|
|[Nil-Struktur](nil-structure.md)|Gibt an, dass ein nicht angegebener optionaler Vorlagen Parameter angegeben wird.|
|[RemoveReference-Struktur](removereference-structure.md)|Entfernt den Verweis oder das rvalue-Verweis Merkmal aus dem angegebenen Klassen Vorlagen Parameter.|
|[RuntimeClassBase-Struktur](runtimeclassbase-structure.md)|Wird verwendet, um `RuntimeClass` in der [make](make-function.md) -Funktion zu erkennen.|
|[RuntimeClassBaseT-Struktur](runtimeclassbaset-structure.md)|Stellt Hilfsmethoden für `QueryInterface` Vorgänge und das erhalten von Schnittstellen-IDs bereit.|
|[VerifyInheritanceHelper-Struktur](verifyinheritancehelper-structure.md)|Testet, ob eine Schnittstelle von einer anderen Schnittstelle abgeleitet ist.|
|[VerifyInterfaceHelper-Struktur](verifyinterfacehelper-structure.md)|Überprüft, ob die Schnittstelle, die vom Vorlagen Parameter angegeben wird, bestimmte Anforderungen erfüllt.|

### <a name="enumerations"></a>Enumerationen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[AsyncStatusInternal-Enumeration](asyncstatusinternal-enumeration.md)|Gibt eine Zuordnung zwischen internen Enumerationen für den Zustand von asynchronen Vorgängen und die `Windows::Foundation::AsyncStatus` Enumeration an.|

### <a name="functions"></a>Functions

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ActivationFactoryCallback-Funktion](activationfactorycallback-function.md)|Ruft die aktivierungsfactory für die angegebene Aktivierungs-ID ab.|
|[Move-Funktion](move-function.md)|Verschiebt das angegebene Argument von einem Speicherort zu einem anderen.|
|[RaiseException-Funktion](raiseexception-function.md)|Löst eine Ausnahme im aufrufenden Thread aus.|
|[Swap-Funktion (WRL)](swap-function-wrl.md)|Tauscht die Werte der beiden angegebenen Argumente aus.|
|[TerminateMap-Funktion](terminatemap-function.md)|Fährt die Klassenfactorys im angegebenen Modul herunter.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Async. h, Client. h, corewrappers. h, Event. h, FTM. h, implementiert. h, Internal. h, Module. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers-Namespace](microsoft-wrl-wrappers-namespace.md)
