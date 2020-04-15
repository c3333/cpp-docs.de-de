---
title: Module::MethodReleaseNotifier-Klasse
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: c641f150b6f029facffa62f7b47c7da32138735e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371287"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier-Klasse

Ruft einen Ereignishandler auf, wenn das letzte Objekt im aktuellen Modul freigegeben wird. Der Ereignishandler wird von einem Objekt und seinem Zeiger-zu-eine-Methoden-Member angegeben.

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Objekts, dessen Memberfunktion der Ereignishandler ist.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                                                                 | BESCHREIBUNG
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Modul::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Initialisiert eine neue Instanz der Klasse `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                                   | BESCHREIBUNG
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Modul::MethodReleaseNotifier::Invoke](#methodreleasenotifier-invoke) | Ruft den Ereignishandler auf, der dem aktuellen `Module::MethodReleaseNotifier` Objekt zugeordnet ist.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                                                                    | BESCHREIBUNG
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Modul::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | Hält einen Zeiger auf den Ereignishandler für das aktuelle `Module::MethodReleaseNotifier` Objekt.
[Modul::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | Hält einen Zeiger auf das Objekt, dessen Memberfunktion `Module::MethodReleaseNotifier` der Ereignishandler für das aktuelle Objekt ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Modul::MethodReleaseNotifier::Invoke

Ruft den Ereignishandler auf, der dem aktuellen `Module::MethodReleaseNotifier` Objekt zugeordnet ist.

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Modul::MethodReleaseNotifier::method_

Hält einen Zeiger auf den Ereignishandler für das aktuelle `Module::MethodReleaseNotifier` Objekt.

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Modul::MethodReleaseNotifier::MethodReleaseNotifier

Initialisiert eine neue Instanz der Klasse `Module::MethodReleaseNotifier`.

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Parameter

*Objekt*<br/>
Ein Objekt, dessen Memberfunktion ein Ereignishandler ist.

*Methode*<br/>
Die Memberfunktion des *Parameterobjekts,* das der Ereignishandler ist.

*Release*<br/>
Geben `true` Sie an, dass das Aufrufen der zugrunde liegenden [Module::ReleaseNotifier::Release()-Methode](module-releasenotifier-class.md#releasenotifier-release) aktiviert werden soll. Andernfalls geben `false`Sie an.

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Modul::MethodReleaseNotifier::object_

Hält einen Zeiger auf das Objekt, dessen Memberfunktion `Module::MethodReleaseNotifier` der Ereignishandler für das aktuelle Objekt ist.

```cpp
T* object_;
```
