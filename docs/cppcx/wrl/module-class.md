---
title: Module-Klasse
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
- module/Microsoft::WRL::Module::Create
- module/Microsoft::WRL::Module::DecrementObjectCount
- module/Microsoft::WRL::Module::GetActivationFactory
- module/Microsoft::WRL::Module::GetClassObject
- module/Microsoft::WRL::Module::GetModule
- module/Microsoft::WRL::Module::GetObjectCount
- module/Microsoft::WRL::Module::IncrementObjectCount
- module/Microsoft::WRL::Module::Module
- module/Microsoft::WRL::Module::objectCount_Data
- module/Microsoft::WRL::Module::RegisterCOMObject
- module/Microsoft::WRL::Module::RegisterObjects
- module/Microsoft::WRL::Module::RegisterWinRTObject
- module/Microsoft::WRL::Module::releaseNotifier_
- module/Microsoft::WRL::Module::Terminate
- module/Microsoft::WRL::Module::~Module
- module/Microsoft::WRL::Module::UnregisterCOMObject
- module/Microsoft::WRL::Module::UnregisterObjects
- module/Microsoft::WRL::Module::UnregisterWinRTObject
helpviewer_keywords:
- Microsoft::WRL::Module class
- Microsoft::WRL::Module::Create method
- Microsoft::WRL::Module::DecrementObjectCount method
- Microsoft::WRL::Module::GetActivationFactory method
- Microsoft::WRL::Module::GetClassObject method
- Microsoft::WRL::Module::GetModule method
- Microsoft::WRL::Module::GetObjectCount method
- Microsoft::WRL::Module::IncrementObjectCount method
- Microsoft::WRL::Module::Module, constructor
- Microsoft::WRL::Module::objectCount_ data member
- Microsoft::WRL::Module::RegisterCOMObject method
- Microsoft::WRL::Module::RegisterObjects method
- Microsoft::WRL::Module::RegisterWinRTObject method
- Microsoft::WRL::Module::releaseNotifier_ data member
- Microsoft::WRL::Module::Terminate method
- Microsoft::WRL::Module::~Module, destructor
- Microsoft::WRL::Module::UnregisterCOMObject method
- Microsoft::WRL::Module::UnregisterObjects method
- Microsoft::WRL::Module::UnregisterWinRTObject method
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
ms.openlocfilehash: f7930247c979c111a7f4798e35ebe7aa95209f37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225747"
---
# <a name="module-class"></a>Module-Klasse

Stellt eine Auflistung von zugehörigen Objekten dar.

## <a name="syntax"></a>Syntax

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>Parameter

*moduleType*<br/>
Eine Kombination aus einem oder mehreren [ModuleType](moduletype-enumeration.md) -Enumerationswerten.

## <a name="members"></a>Member

### <a name="protected-classes"></a>Geschützte Klassen

Name                                                                                | Beschreibung
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module:: generikreleasenotifier](module-genericreleasenotifier-class.md) | Ruft einen Ereignishandler auf, wenn das letzte-Objekt im aktuellen Modul freigegeben wird. Der-Ereignishandler wird von in einem Lambda-, Funktor-oder Zeiger auf eine Funktion angegeben.
[Module:: methodreleasenotifier](module-methodreleasenotifier-class.md)   | Ruft einen Ereignishandler auf, wenn das letzte-Objekt im aktuellen Modul freigegeben wird. Der-Ereignishandler wird von einem-Objekt und seinem Pointer-to-a-method-Member angegeben.
[Module:: releasenotifier](module-releasenotifier-class.md)               | Ruft einen Ereignishandler auf, wenn das letzte-Objekt in einem Modul freigegeben wird.

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                             | Beschreibung
-------------------------------- | -----------------------------------------------------------
[Module:: ~-Modul](#tilde-module) | Deinitialisiert die aktuelle Instanz der- `Module` Klasse.

### <a name="protected-constructors"></a>Geschützte Konstruktoren

Name                      | Beschreibung
------------------------- | ---------------------------------------------------
[Module:: Module](#module) | Initialisiert eine neue Instanz der `Module`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

name                                                    | Beschreibung
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module:: Create](#create)                               | Erstellt eine Instanz eines Moduls.
[Modul::D ecrementobjectcount](#decrementobjectcount)   | Dekremente die Anzahl der Objekte, die vom Modul nachverfolgt werden.
[Module:: getactivationfactory](#getactivationfactory)   | Ruft eine aktivierungfactory für das Modul ab.
[Module:: GetClassObject](#getclassobject)               | Ruft einen Cache von Klassenfactorys ab.
[Module:: GetModule](#getmodule)                         | Erstellt eine Instanz eines Moduls.
[Module:: getobjectcount](#getobjectcount)               | Ruft die Anzahl der-Objekte ab, die von diesem Modul verwaltet werden.
[Module:: incrementobjectcount](#incrementobjectcount)   | Erhöht die Anzahl der Objekte, die vom Modul nachverfolgt werden.
[Module:: registercomobject](#registercomobject)         | Registriert mindestens ein COM-Objekt, sodass andere Anwendungen eine Verbindung mit Ihnen herstellen können.
[Module:: registerobjects](#registerobjects)             | Registriert com-oder Windows-Runtime-Objekte, sodass andere Anwendungen eine Verbindung mit Ihnen herstellen können.
[Module:: registerwinrtobject](#registerwinrtobject)     | Registriert mindestens ein Windows-Runtime Objekt, damit andere Anwendungen eine Verbindung mit Ihnen herstellen können.
[Module:: beenden](#terminate)                         | Bewirkt, dass alle vom Modul instanziierten Factorys heruntergefahren werden.
[Module:: unregistercomobject](#unregistercomobject)     | Hebt die Registrierung eines oder mehrerer COM-Objekte auf, wodurch verhindert wird, dass andere Anwendungen eine Verbindung mit Ihnen herstellen.
[Module:: unregisterobjects](#unregisterobjects)         | Hebt die Registrierung der Objekte im angegebenen Modul auf, sodass andere Anwendungen keine Verbindung mit Ihnen herstellen können.
[Module:: unregisterwinrtobject](#unregisterwinrtobject) | Hebt die Registrierung eines oder mehrerer Windows-Runtime Objekte auf, sodass andere Anwendungen keine Verbindung mit Ihnen herstellen können.

### <a name="protected-methods"></a>Geschützte Methoden

Name                      | Beschreibung
------------------------- | --------------------------------
[Module:: Create](#create) | Erstellt eine Instanz eines Moduls.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                                         | Beschreibung
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module:: objectCount_](#objectcount)         | Verfolgt, wie viele Klassen mit der [make](make-function.md) -Funktion erstellt wurden.
[Module:: releaseNotifier_](#releasenotifier) | Enthält einen Zeiger auf ein- `ReleaseNotifier` Objekt.

### <a name="macros"></a>Makros

Name                                                                   | Beschreibung
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ActivatableClass](activatableclass-macros.md)              | Füllt einen internen Cache mit einer Factory auf, mit der eine Instanz der angegebenen Klasse erstellt werden kann. Dieses Makro gibt Standardfactory-und Gruppen-ID-Parameter an.
[ActivatableClassWithFactory](activatableclass-macros.md)   | Füllt einen internen Cache mit einer Factory auf, mit der eine Instanz der angegebenen Klasse erstellt werden kann. Mit diesem Makro können Sie einen bestimmten Factory-Parameter angeben.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Füllt einen internen Cache mit einer Factory auf, mit der eine Instanz der angegebenen Klasse erstellt werden kann. Mit diesem Makro können Sie bestimmte Factory-und Gruppen-ID-Parameter angeben.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>Module:: ~-Modul

Deinitialisiert die aktuelle Instanz der- `Module` Klasse.

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>Module:: Create

Erstellt eine Instanz eines Moduls.

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Modultyp.

*Rück*<br/>
Wird aufgerufen, wenn das letzte Instanzobjekt des Moduls freigegeben wird.

*object*<br/>
Die *Objekt* -und *Methoden* Parameter werden in Kombination verwendet. Verweist auf das letzte Instanzobjekt, wenn das letzte Instanzobjekt im Modul freigegeben wird.

*method*<br/>
Die *Objekt* -und *Methoden* Parameter werden in Kombination verwendet. Verweist auf die-Methode des letzten Instanzobjekts, wenn das letzte Instanzobjekt im Modul freigegeben wird.

### <a name="return-value"></a>Rückgabewert

Verweis auf das Modul.

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>Modul::D ecrementobjectcount

Dekremente die Anzahl der Objekte, die vom Modul nachverfolgt werden.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Rückgabewert

Der Zähler vor dem Dekrement-Vorgang.

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>Module:: getactivationfactory

Ruft eine aktivierungfactory für das Modul ab.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parameter

*pactivatibleclassid*<br/>
IID einer Lauf Zeit Klasse.

*ppifactory*<br/>
Die iactivationfactory für die angegebene Lauf Zeit Klasse.

*Servername*<br/>
Der Name einer Teilmenge der Klassenfactorys im aktuellen Modul. Geben Sie den Servernamen an, der im [activatableclasswithfactoryex](activatableclass-macros.md) -Makro verwendet wird, oder geben **`nullptr`** Sie an, um den Standard Servernamen zu erhalten.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls das von getactivationfactory zurückgegebene HRESULT.

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>Module:: GetClassObject

Gibt einen Cache von Klassenfactorys zurück.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parameter

*CLSID*<br/>
Klassen-ID.

*riid*<br/>
Die von Ihnen angeforderungsschnittstellen-ID.

*PPV*<br/>
Zeiger auf das zurückgegebene Objekt.

*Servername*<br/>
Der Servername, der entweder im-,-oder-Makro angegeben ist, `ActivatableClassWithFactory` `ActivatableClassWithFactoryEx` `ActivatableClass` oder **`nullptr`** , um den Standard Servernamen zu erhalten.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für com, nicht für die Windows-Runtime. Diese Methode macht nur `IClassFactory` Methoden verfügbar.

## <a name="modulegetmodule"></a><a name="getmodule"></a>Module:: GetModule

Erstellt eine Instanz eines Moduls.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein Modul.

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>Module:: getobjectcount

Ruft die Anzahl der-Objekte ab, die von diesem Modul verwaltet werden.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Anzahl von Objekten, die von diesem Modul verwaltet werden.

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>Module:: incrementobjectcount

Erhöht die Anzahl der Objekte, die vom Modul nachverfolgt werden.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Rückgabewert

Der Zähler vor dem Inkrement-Vorgang.

## <a name="modulemodule"></a><a name="module"></a>Module:: Module

Initialisiert eine neue Instanz der `Module`-Klasse.

```cpp
Module();
```

### <a name="remarks"></a>Bemerkungen

Dieser Konstruktor ist geschützt und kann nicht mit dem- **`new`** Schlüsselwort aufgerufen werden. Rufen Sie stattdessen entweder [Module:: GetModule](#getmodule) oder [Module:: Create](#create)auf.

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>Module:: objectCount_

Verfolgt, wie viele Klassen mit der [make](make-function.md) -Funktion erstellt wurden.

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>Module:: registercomobject

Registriert mindestens ein COM-Objekt, sodass andere Anwendungen eine Verbindung mit Ihnen herstellen können.

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>Parameter

*Servername*<br/>
Voll qualifizierter Name eines Servers.

*CLSIDs*<br/>
Ein Array von CLSIDs, die registriert werden sollen.

*factories*<br/>
Ein Array von IUnknown-Schnittstellen der Klassen Objekte, deren Verfügbarkeit veröffentlicht wird.

*cookies*<br/>
Wenn der Vorgang abgeschlossen ist, ein Array von Zeigern auf Werte, mit denen die registrierten Klassen Objekte identifiziert werden. Diese Werte werden später verwendet, um die Registrierung aufzuheben.

*count*<br/>
Die Anzahl der zu registrierenden CLSIDs.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, z. b. CO_E_OBJISREG, das den Grund für den Fehler des Vorgangs angibt.

### <a name="remarks"></a>Bemerkungen

Die COM-Objekte werden mit dem CLSCTX_LOCAL_SERVER Enumerator der CLSCTX-Enumeration registriert.

Der Verbindungstyp zu den registrierten Objekten wird durch eine Kombination aus dem aktuellen *comflag* -Vorlagen Parameter und dem REGCLS_SUSPENDED Enumerator der REGCLS-Enumeration angegeben.

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>Module:: registerobjects

Registriert com-oder Windows-Runtime-Objekte, sodass andere Anwendungen eine Verbindung mit Ihnen herstellen können.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parameter

*Mond*<br/>
Ein Array von com-oder Windows-Runtime-Objekten.

*Servername*<br/>
Der Name des Servers, der die Objekte erstellt hat.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Grund für den fehlgeschlagenen Vorgang angibt.

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>Module:: registerwinrtobject

Registriert mindestens ein Windows-Runtime Objekt, damit andere Anwendungen eine Verbindung mit Ihnen herstellen können.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Parameter

*Servername*<br/>
Ein Name, der eine Teilmenge von Objekten angibt, die von diesem Vorgang betroffen sind.

*activatableclassids*<br/>
Ein Array von aktivierbaren CLSIDs, die registriert werden sollen.

*KS*<br/>
Ein-Wert, der die-Klassen Objekte identifiziert, die registriert wurden. Dieser Wert wird später verwendet, um die Registrierung aufzuheben.

*count*<br/>
Die Anzahl der zu registrierenden-Objekte.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehler HRESULT, z. b. CO_E_OBJISREG, der den Grund für den Fehler des Vorgangs angibt.

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>Module:: releaseNotifier_

Enthält einen Zeiger auf ein- `ReleaseNotifier` Objekt.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>Module:: beenden

Bewirkt, dass alle vom Modul instanziierten Factorys heruntergefahren werden.

```cpp
void Terminate();
```

### <a name="remarks"></a>Bemerkungen

Gibt die Factorys im Cache frei.

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>Module:: unregistercomobject

Hebt die Registrierung eines oder mehrerer COM-Objekte auf, wodurch verhindert wird, dass andere Anwendungen eine Verbindung mit Ihnen herstellen.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parameter

*Servername*<br/>
Genutzt

*cookies*<br/>
Ein Array von Zeigern auf-Werte, die die Klassen Objekte identifizieren, deren Registrierung aufgehoben werden soll. Das Array wurde von der [registercomobject](#registercomobject) -Methode erstellt.

*count*<br/>
Die Anzahl der Klassen, deren Registrierung aufgehoben werden soll.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn dieser Vorgang erfolgreich ist. andernfalls ein Fehler HRESULT, der den Grund für den fehlgeschlagenen Vorgang angibt.

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>Module:: unregisterobjects

Hebt die Registrierung der Objekte im angegebenen Modul auf, sodass andere Anwendungen keine Verbindung mit Ihnen herstellen können.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parameter

*Mond*<br/>
Zeiger auf ein Modul.

*Servername*<br/>
Ein qualifizierender Name, der eine Teilmenge von Objekten angibt, die von diesem Vorgang betroffen sind.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn dieser Vorgang erfolgreich ist. andernfalls ein Fehler HRESULT, der angibt, warum dieser Vorgang nicht ausgeführt werden konnte.

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>Module:: unregisterwinrtobject

Hebt die Registrierung eines oder mehrerer Windows-Runtime Objekte auf, sodass andere Anwendungen keine Verbindung mit Ihnen herstellen können.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parameter

*KS*<br/>
Ein Zeiger auf einen Wert, der das Klassenobjekt identifiziert, dessen Registrierung aufgehoben werden soll.
