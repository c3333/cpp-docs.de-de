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
ms.openlocfilehash: afd2edacefdf5d62b50a03c0a8c37f13ee5d9c9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371319"
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
Eine Kombination aus [ModuleType](moduletype-enumeration.md) einem oder mehreren ModuleType-Enumerationswerten.

## <a name="members"></a>Member

### <a name="protected-classes"></a>Geschützte Klassen

Name                                                                                | BESCHREIBUNG
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Modul::GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Ruft einen Ereignishandler auf, wenn das letzte Objekt im aktuellen Modul freigegeben wird. Der Ereignishandler wird durch einen Lambda, Functor oder Zeiger auf die Funktion angegeben.
[Modul::MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Ruft einen Ereignishandler auf, wenn das letzte Objekt im aktuellen Modul freigegeben wird. Der Ereignishandler wird von einem Objekt und seinem Zeiger-zu-eine-Methoden-Member angegeben.
[Modul::ReleaseNotifier](module-releasenotifier-class.md)               | Ruft einen Ereignishandler auf, wenn das letzte Objekt in einem Modul freigegeben wird.

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                             | BESCHREIBUNG
-------------------------------- | -----------------------------------------------------------
[Modul::-Modul](#tilde-module) | Deinitialisiert die aktuelle Instanz `Module` der Klasse.

### <a name="protected-constructors"></a>Geschützte Konstruktoren

Name                      | BESCHREIBUNG
------------------------- | ---------------------------------------------------
[Modul::Modul](#module) | Initialisiert eine neue Instanz der Klasse `Module`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                    | BESCHREIBUNG
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Modul::Erstellen](#create)                               | Erstellt eine Instanz eines Moduls.
[Modul::DecrementObjectCount](#decrementobjectcount)   | Dekrementiert die Anzahl der vom Modul nachverfolgten Objekte.
[Modul::GetActivationFactory](#getactivationfactory)   | Ruft eine Aktivierungsfactory für das Modul ab.
[Modul::GetClassObject](#getclassobject)               | Ruft einen Cache von Klassenfabriken ab.
[Modul::GetModule](#getmodule)                         | Erstellt eine Instanz eines Moduls.
[Modul::GetObjectCount](#getobjectcount)               | Ruft die Anzahl der von diesem Modul verwalteten Objekte ab.
[Modul::IncrementObjectCount](#incrementobjectcount)   | Erhöht die Anzahl der vom Modul nachverfolgten Objekte.
[Modul::RegisterCOMObject](#registercomobject)         | Registriert ein oder mehrere COM-Objekte, damit andere Anwendungen eine Verbindung zu ihnen herstellen können.
[Modul::RegisterObjects](#registerobjects)             | Registriert COM- oder Windows-Runtime-Objekte, damit andere Anwendungen eine Verbindung zu ihnen herstellen können.
[Modul::RegisterWinRTObject](#registerwinrtobject)     | Registriert ein oder mehrere Windows-Runtime-Objekte, damit andere Anwendungen eine Verbindung zu ihnen herstellen können.
[Modul::Beenden](#terminate)                         | Bewirkt, dass alle vom Modul instanziierten Fabriken heruntergefahren werden.
[Modul::UnregisterCOMObject](#unregistercomobject)     | Entregistriert ein oder mehrere COM-Objekte, wodurch verhindert wird, dass andere Anwendungen eine Verbindung zu ihnen herstellen.
[Modul::UnregisterObjects](#unregisterobjects)         | Die Registrierung der Objekte im angegebenen Modul wird aufheben, sodass andere Anwendungen keine Verbindung zu ihnen herstellen können.
[Modul::UnregisterWinRTObject](#unregisterwinrtobject) | Entregistriert ein oder mehrere Windows-Runtime-Objekte, sodass andere Anwendungen keine Verbindung zu ihnen herstellen können.

### <a name="protected-methods"></a>Geschützte Methoden

Name                      | BESCHREIBUNG
------------------------- | --------------------------------
[Modul::Erstellen](#create) | Erstellt eine Instanz eines Moduls.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                                         | BESCHREIBUNG
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Modul::objectCount_](#objectcount)         | Verfolgt, wie viele Klassen mit der [Make-Funktion](make-function.md) erstellt wurden.
[Modul::releaseNotifier_](#releasenotifier) | Hält einen Zeiger `ReleaseNotifier` auf ein Objekt.

### <a name="macros"></a>Makros

Name                                                                   | BESCHREIBUNG
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ActivatableClass](activatableclass-macros.md)              | Füllt einen internen Cache, der eine Factory enthält, die eine Instanz der angegebenen Klasse erstellen kann. Dieses Makro gibt standardmäßige Factory- und Gruppen-ID-Parameter an.
[ActivatableClassWithFactory](activatableclass-macros.md)   | Füllt einen internen Cache, der eine Factory enthält, die eine Instanz der angegebenen Klasse erstellen kann. Mit diesem Makro können Sie einen bestimmten Factoryparameter angeben.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Füllt einen internen Cache, der eine Factory enthält, die eine Instanz der angegebenen Klasse erstellen kann. Mit diesem Makro können Sie bestimmte Factory- und Gruppen-ID-Parameter angeben.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>Modul::-Modul

Deinitialisiert die aktuelle Instanz `Module` der Klasse.

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>Modul::Erstellen

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

*Rückruf*<br/>
Wird aufgerufen, wenn das letzte Instanzobjekt des Moduls freigegeben wird.

*Objekt*<br/>
Die *Objekt-* und *Methodenparameter* werden in Kombination verwendet. Zeigt auf das letzte Instanzobjekt, wenn das letzte Instanzobjekt im Modul freigegeben wird.

*Methode*<br/>
Die *Objekt-* und *Methodenparameter* werden in Kombination verwendet. Zeigt auf die Methode des letzten Instanzobjekts, wenn das letzte Instanzobjekt im Modul freigegeben wird.

### <a name="return-value"></a>Rückgabewert

Verweis auf das Modul.

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>Modul::DecrementObjectCount

Dekrementiert die Anzahl der vom Modul nachverfolgten Objekte.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl vor dem Dekrementvorgang.

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>Modul::GetActivationFactory

Ruft eine Aktivierungsfactory für das Modul ab.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parameter

*pActivatibleClassId*<br/>
IID einer Laufzeitklasse.

*ppIFactory*<br/>
Die IActivationFactory für die angegebene Laufzeitklasse.

*Servername*<br/>
Der Name einer Teilmenge von Klassenfabriken im aktuellen Modul. Geben Sie den Servernamen an, der im [ActivatableClassWithFactoryEx-Makro](activatableclass-macros.md) verwendet wird, oder geben `nullptr` Sie an, um den Standardservernamen abzurufen.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls wird das HRESULT von GetActivationFactory zurückgegeben.

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>Modul::GetClassObject

Retreives einen Cache von Klassenfabriken.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
Klassen-ID.

*riid*<br/>
Schnittstellen-ID, die Sie anfordern.

*Ppv*<br/>
Zeiger auf das zurückgegebene Objekt.

*Servername*<br/>
Der Servername, der `ActivatableClassWithFactory`entweder `ActivatableClassWithFactoryEx`im `ActivatableClass` , oder im Makro angegeben ist. oder `nullptr` um den Standardservernamen abzurufen.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur für COM, nicht für die Windows-Runtime. Diese Methode macht `IClassFactory` nur Methoden verfügbar.

## <a name="modulegetmodule"></a><a name="getmodule"></a>Modul::GetModule

Erstellt eine Instanz eines Moduls.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein Modul.

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>Modul::GetObjectCount

Ruft die Anzahl der von diesem Modul verwalteten Objekte ab.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Anzahl der von diesem Modul verwalteten Objekte.

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>Modul::IncrementObjectCount

Erhöht die Anzahl der vom Modul nachverfolgten Objekte.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl vor dem Inkrementvorgang.

## <a name="modulemodule"></a><a name="module"></a>Modul::Modul

Initialisiert eine neue Instanz der Klasse `Module`.

```cpp
Module();
```

### <a name="remarks"></a>Bemerkungen

Dieser Konstruktor ist geschützt und `new` kann nicht mit dem Schlüsselwort aufgerufen werden. Rufen Sie stattdessen entweder [Module::GetModule](#getmodule) oder [Module::Create](#create)auf.

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>Modul::objectCount_

Verfolgt, wie viele Klassen mit der [Make-Funktion](make-function.md) erstellt wurden.

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>Modul::RegisterCOMObject

Registriert ein oder mehrere COM-Objekte, damit andere Anwendungen eine Verbindung zu ihnen herstellen können.

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
Vollständig qualifizierter Name eines Servers.

*Clsids*<br/>
Ein Array von zu registrierenden CLSIDs.

*factories*<br/>
Ein Array von IUnknown-Schnittstellen der Klassenobjekte, deren Verfügbarkeit veröffentlicht wird.

*Cookies*<br/>
Wenn der Vorgang abgeschlossen ist, wird ein Array von Zeigern auf Werte angezeigt, die die registrierten Klassenobjekte identifizieren. Diese Werte werden später verwendet, um die Registrierung zu widerrufen.

*count*<br/>
Die Anzahl der zu registrierenden CLSIDs.

### <a name="return-value"></a>Rückgabewert

S_OK wenn Erfolgfu; Andernfalls ein HRESULT wie CO_E_OBJISREG, der den Grund für den Fehlgeschlagen des Vorgangs angibt.

### <a name="remarks"></a>Bemerkungen

Die COM-Objekte werden mit dem CLSCTX_LOCAL_SERVER-Enumerator der CLSCTX-Enumeration registriert.

Der Verbindungstyp zu den registrierten Objekten wird durch eine Kombination aus dem aktuellen *Comflag-Vorlagenparameter* und dem REGCLS_SUSPENDED Enumerator der REGCLS-Enumeration angegeben.

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>Modul::RegisterObjects

Registriert COM- oder Windows-Runtime-Objekte, damit andere Anwendungen eine Verbindung zu ihnen herstellen können.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parameter

*Modul*<br/>
Ein Array von COM- oder Windows-Runtime-Objekten.

*Servername*<br/>
Name des Servers, der die Objekte erstellt hat.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls ein HRESULT, das den Grund für den Fehler des Vorgangs angibt.

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>Modul::RegisterWinRTObject

Registriert ein oder mehrere Windows-Runtime-Objekte, damit andere Anwendungen eine Verbindung zu ihnen herstellen können.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Parameter

*Servername*<br/>
Ein Name, der eine Teilmenge der von diesem Vorgang betroffenen Objekte angibt.

*aktivatierbareClassIds*<br/>
Ein Array von aktivierbaren CLSIDs, die registriert werden sollen.

*Cookie*<br/>
Ein Wert, der die registrierten Klassenobjekte identifiziert. Dieser Wert wird später verwendet, um die Registrierung zu widerrufen.

*count*<br/>
Die Anzahl der zu registrierenden Objekte.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls ein Fehler HRESULT wie CO_E_OBJISREG, der den Grund für den Fehler des Vorgangs angibt.

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>Modul::releaseNotifier_

Hält einen Zeiger `ReleaseNotifier` auf ein Objekt.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>Modul::Beenden

Bewirkt, dass alle vom Modul instanziierten Fabriken heruntergefahren werden.

```cpp
void Terminate();
```

### <a name="remarks"></a>Bemerkungen

Gibt die Fabriken im Cache frei.

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>Modul::UnregisterCOMObject

Entregistriert ein oder mehrere COM-Objekte, wodurch verhindert wird, dass andere Anwendungen eine Verbindung zu ihnen herstellen.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parameter

*Servername*<br/>
(Nicht verwendet)

*Cookies*<br/>
Ein Array von Zeigern auf Werte, die die Klassenobjekte identifizieren, die nicht registriert werden sollen. Das Array wurde von der [RegisterCOMObject-Methode](#registercomobject) erstellt.

*count*<br/>
Die Anzahl der Klassen, die die Registrierung aufheben sollen.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn dieser Vorgang erfolgreich ist. Andernfalls ein Fehler HRESULT, der den Grund für den Fehler des Vorgangs angibt.

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>Modul::UnregisterObjects

Die Registrierung der Objekte im angegebenen Modul wird aufheben, sodass andere Anwendungen keine Verbindung zu ihnen herstellen können.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parameter

*Modul*<br/>
Zeiger auf ein Modul.

*Servername*<br/>
Ein qualifizierender Name, der eine Teilmenge der von diesem Vorgang betroffenen Objekte angibt.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn dieser Vorgang erfolgreich ist. Andernfalls ein Fehler HRESULT, der den Grund für den Fehler dieses Vorgangs angibt.

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>Modul::UnregisterWinRTObject

Entregistriert ein oder mehrere Windows-Runtime-Objekte, sodass andere Anwendungen keine Verbindung zu ihnen herstellen können.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parameter

*Cookie*<br/>
Ein Zeiger auf einen Wert, der das Klassenobjekt identifiziert, dessen Registrierung widerrufen werden soll.
