---
title: Schlüssel-WRL-APIs nach Kategorie
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: 8ac89f3286866ac61bac5ae256bdb448fe88f07d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213823"
---
# <a name="key-wrl-apis-by-category"></a>Schlüssel-WRL-APIs nach Kategorie

In den folgenden Tabellen sind die C++ Klassen, Strukturen, Funktionen und Makros der primären Windows-Runtime Vorlagen Bibliothek aufgeführt. Konstrukte in hilfsnamespaces und Klassen werden weggelassen. Diese Listen erweitern die API-Dokumentation, die nach Namespace angeordnet ist.

## <a name="classes"></a>Klassen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[ActivationFactory-Klasse](activationfactory-class.md)|Ermöglicht, dass eine oder mehrere Klassen durch die Windows-Runtime aktiviert werden.|
|[AsyncBase-Klasse](asyncbase-class.md)|Implementiert den asynchronen Zustandsautomat der Windows-Runtime.|
|[ClassFactory-Klasse](classfactory-class.md)|Implementiert die grundlegende Funktion der `IClassFactory`-Schnittstelle.|
|[ComPtr-Klasse](comptr-class.md)|Erstellt einen *intelligenten Zeigertyp* , der die Schnittstelle darstellt, die vom Vorlagenparameter angegeben wird. ComPtr verwaltet automatisch einen Verweiszähler für den zugrunde liegenden Schnittstellenzeiger und gibt die Schnittstelle frei, wenn der Verweiszähler auf 0 geht.|
|[Ereignisklasse (C++-Vorlagenbibliothek der Windows-Runtime)](event-class-wrl.md)|Stellt ein Ereignis dar.|
|[EventSource-Klasse](eventsource-class.md)|Stellt ein Ereignis dar. `EventSource`-Memberfunktionen fügen Ereignishandler hinzu, entfernen sie und rufen sie auf.|
|[FtmBase-Klasse](ftmbase-class.md)|Stellt ein Freethread-Marshaller-Objekt dar.|
|[HandleT-Klasse](handlet-class.md)|Stellt ein Handle für ein-Objekt dar.|
|[HString-Klasse](hstring-class.md)|Bietet Unterstützung für die Bearbeitung von HSTRING-Handles.|
|[HStringReference-Klasse](hstringreference-class.md)|Stellt ein HSTRING dar, das aus einer vorhandenen Zeichenfolge erstellt wird.|
|[Module-Klasse](module-class.md)|Stellt eine Auflistung von zugehörigen Objekten dar.|
|[Module::GenericReleaseNotifier-Klasse](module-genericreleasenotifier-class.md)|Ruft einen Ereignishandler auf, wenn das letzte-Objekt im aktuellen Modul freigegeben wird. Der-Ereignishandler wird von in einem Lambda-, Funktor-oder Zeiger auf eine Funktion angegeben.|
|[Module::MethodReleaseNotifier-Klasse](module-methodreleasenotifier-class.md)|Ruft einen Ereignishandler auf, wenn das letzte-Objekt im aktuellen Modul freigegeben wird. Der-Ereignishandler wird von einem-Objekt und seinem Pointer-to-a-method-Member angegeben.|
|[Module::ReleaseNotifier-Klasse](module-releasenotifier-class.md)|Ruft einen Ereignishandler auf, wenn das letzte-Objekt in einem Modul freigegeben wird.|
|[RoInitializeWrapper-Klasse](roinitializewrapper-class.md)|Initialisiert die Windows-Runtime.|
|[RuntimeClass-Klasse](runtimeclass-class.md)|Stellt eine instanziierte Klasse dar, die die angegebene Anzahl von Schnittstellen erbt, und gewährt Unterstützung für die angegebene Windows-Runtime, klassisches COM und schwache Verweise.|
|[SimpleActivationFactory-Klasse](simpleactivationfactory-class.md)|Stellt einen grundlegenden Mechanismus für das Erstellen einer Windows-Runtime oder einer klassischen COM-Basisklasse bereit.|
|[SimpleClassFactory-Klasse](simpleclassfactory-class.md)|Stellt einen grundlegenden Mechanismus zum Erstellen einer Basisklasse bereit.|
|[WeakRef-Klasse](weakref-class.md)|Stellt einen *schwachen Verweis* dar, der nur durch die Windows-Runtime und nicht durch die klassische COM verwendet werden kann. Ein schwacher Verweis repräsentiert ein Objekt, auf das möglicherweise zugegriffen werden kann.|

## <a name="structures"></a>Strukturen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[ChainInterfaces-Struktur](chaininterfaces-structure.md)|Gibt Überprüfungs- und Initialisierungsfunktionen an, die auf einen Satz von Schnittstellen-IDs angewendet werden können.|
|[CloakedIid-Struktur](cloakediid-structure.md)|Gibt dem `RuntimeClass`-, `Implements`-und `ChainInterfaces`-Vorlagen an, dass auf die angegebene Schnittstelle in der IID-Liste nicht zugegriffen werden kann.|
|[Implements-Struktur](implements-structure.md)|Implementiert `QueryInterface` und `GetIid` für die angegebenen Schnittstellen.|
|[MixIn-Struktur](mixin-structure.md)|Stellt sicher, dass eine Runtime-Klasse aus Windows-Runtime-Schnittstellen (sofern vorhanden) und dann aus klassischen COM-Schnittstellen abgeleitet wird.|

## <a name="functions"></a>Functions

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[ActivateInstance-Funktion](activateinstance-function.md)|Registriert eine Instanz eines angegebenen Typs, die in einer angegebenen Klassen-ID definiert ist, und ruft Sie ab.|
|[AsWeak-Funktion](asweak-function.md)|Ruft einen schwachen Verweis zur angegebenen Instanz ab.|
|[Rückruffunktion](callback-function-wrl.md)|Erstellt ein Objekt, dessen Memberfunktion eine Rückrufmethode ist.|
|[CreateActivationFactory-Funktion](createactivationfactory-function.md)|Erstellt eine Instanzen der angegebenen Klasse erstellende Factory, die durch die Windows-Runtime aktiviert werden kann.|
|[CreateClassFactory-Funktion](createclassfactory-function.md)|Erstellt eine Factory, die Instanzen der angegebenen Klasse erstellt.|
|[GetActivationFactory-Funktion](getactivationfactory-function.md)|Ruft eine aktivierungfactory für den Typ ab, der vom Vorlagen Parameter angegeben wird.|
|[Make-Funktion](make-function.md)|Initialisiert die angegebene Windows-Runtime-Klasse.|

## <a name="macros"></a>Makros

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[ActivatableClass-Makros](activatableclass-macros.md)|Füllt einen internen Cache mit einer Factory auf, mit der eine Instanz der angegebenen Klasse erstellt werden kann.|
|[InspectableClass-Makro](inspectableclass-macro.md)|Legt den Ablaufklassennamen und die Vertrauensebene fest.|

## <a name="see-also"></a>Weitere Informationen

[C++-Vorlagenbibliothek für Windows-Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)
