---
title: Module::GenericReleaseNotifier-Klasse
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
ms.openlocfilehash: e3cc8e33d596fb1d3ecc4a94fee7971a50ffe596
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371305"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier-Klasse

Ruft einen Ereignishandler auf, wenn das letzte Objekt im aktuellen Modul freigegeben wird. Der Ereignishandler wird durch einen Lambda, Functor oder Zeiger auf die Funktion angegeben.

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Datenmembers, der den Speicherort des Ereignishandlers enthält.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                                                                     | BESCHREIBUNG
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Modul::GenericReleaseNotifier::GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | Initialisiert eine neue Instanz der Klasse `Module::GenericReleaseNotifier`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                                     | BESCHREIBUNG
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Modul::GenericReleaseNotifier::Invoke](#genericreleasenotifier-invoke) | Ruft den Ereignishandler auf, der dem aktuellen `Module::GenericReleaseNotifier` Objekt zugeordnet ist.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                                                                          | BESCHREIBUNG
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Modul::GenericReleaseNotifier::callback_](#genericreleasenotifier-callback) | Enthält den Lambda-, Functor- oder Zeiger-zu-Funktions-Ereignishandler, der dem aktuellen `Module::GenericReleaseNotifier` Objekt zugeordnet ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>Modul::GenericReleaseNotifier::callback_

Enthält den Lambda-, Functor- oder Zeiger-zu-Funktions-Ereignishandler, der dem aktuellen `Module::GenericReleaseNotifier` Objekt zugeordnet ist.

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>Modul::GenericReleaseNotifier::GenericReleaseNotifier

Initialisiert eine neue Instanz der Klasse `Module::GenericReleaseNotifier`.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Parameter

*Rückruf*<br/>
Ein Lambda-, Functor- oder Zeiger-zu-Funktions-Ereignishandler, der mit dem Funktionsoperator Klammern (`()`) aufgerufen werden kann.

*Release*<br/>
Geben `true` Sie an, dass das Aufrufen der zugrunde liegenden [Module::ReleaseNotifier::Release()-Methode](module-releasenotifier-class.md#releasenotifier-release) aktiviert werden soll. Andernfalls geben `false`Sie an.

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>Modul::GenericReleaseNotifier::Invoke

Ruft den Ereignishandler auf, der dem aktuellen `Module::GenericReleaseNotifier` Objekt zugeordnet ist.

```cpp
void Invoke();
```
