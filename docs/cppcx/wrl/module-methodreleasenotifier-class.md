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
ms.openlocfilehash: 5b0e5766fda878acb1fdc54a79ce162444eb06de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225721"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier-Klasse

Ruft einen Ereignishandler auf, wenn das letzte-Objekt im aktuellen Modul freigegeben wird. Der-Ereignishandler wird von einem-Objekt und seinem Pointer-to-a-method-Member angegeben.

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Objekts, dessen Member-Funktion der Ereignishandler ist.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                                                                 | Beschreibung
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module:: methodreleasenotifier:: methodreleasenotifier](#methodreleasenotifier-methodreleasenotifier) | Initialisiert eine neue Instanz der `Module::MethodReleaseNotifier`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

name                                                                   | Beschreibung
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module:: methodreleasenotifier:: aufrufen](#methodreleasenotifier-invoke) | Ruft den Ereignishandler auf, der dem aktuellen-Objekt zugeordnet ist `Module::MethodReleaseNotifier` .

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                                                                    | Beschreibung
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module:: methodreleasenotifier:: method_](#methodreleasenotifier-method) | Enthält einen Zeiger auf den-Ereignishandler für das aktuelle- `Module::MethodReleaseNotifier` Objekt.
[Module:: methodreleasenotifier:: object_](#methodreleasenotifier-object) | Enthält einen Zeiger auf das-Objekt, dessen Member-Funktion der Ereignishandler für das aktuelle- `Module::MethodReleaseNotifier` Objekt ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Module:: methodreleasenotifier:: aufrufen

Ruft den Ereignishandler auf, der dem aktuellen-Objekt zugeordnet ist `Module::MethodReleaseNotifier` .

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Module:: methodreleasenotifier:: method_

Enthält einen Zeiger auf den-Ereignishandler für das aktuelle- `Module::MethodReleaseNotifier` Objekt.

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Module:: methodreleasenotifier:: methodreleasenotifier

Initialisiert eine neue Instanz der `Module::MethodReleaseNotifier`-Klasse.

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Parameter

*object*<br/>
Ein Objekt, dessen Member-Funktion ein Ereignishandler ist.

*method*<br/>
Die Member-Funktion des Parameter *Objekts* , das der Ereignishandler ist.

*Abgabe*<br/>
Geben **`true`** Sie an, um den Aufruf der zugrunde liegenden [Module:: releasenotifier:: Release ()](module-releasenotifier-class.md#releasenotifier-release) -Methode zu aktivieren; andernfalls geben Sie an **`false`** .

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Module:: methodreleasenotifier:: object_

Enthält einen Zeiger auf das-Objekt, dessen Member-Funktion der Ereignishandler für das aktuelle- `Module::MethodReleaseNotifier` Objekt ist.

```cpp
T* object_;
```
