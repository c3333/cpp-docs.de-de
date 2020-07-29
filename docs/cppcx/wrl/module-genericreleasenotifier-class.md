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
ms.openlocfilehash: 7437f4e1f6874d4c708780a146e1761ac6d98305
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225734"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier-Klasse

Ruft einen Ereignishandler auf, wenn das letzte-Objekt im aktuellen Modul freigegeben wird. Der-Ereignishandler wird von in einem Lambda-, Funktor-oder Zeiger auf eine Funktion angegeben.

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Datenmembers, der den Speicherort des Ereignis Handlers enthält.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                                                                     | Beschreibung
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module:: generifileasenotifier:: generikreleasenotifier](#genericreleasenotifier-genericreleasenotifier) | Initialisiert eine neue Instanz der `Module::GenericReleaseNotifier`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

name                                                                     | Beschreibung
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module:: generikreleasenotifier:: aufrufen](#genericreleasenotifier-invoke) | Ruft den Ereignishandler auf, der dem aktuellen-Objekt zugeordnet ist `Module::GenericReleaseNotifier` .

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                                                                          | Beschreibung
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module:: generikreleasenotifier:: callback_](#genericreleasenotifier-callback) | Enthält den Lambda-, Funktor-oder Zeiger-zu-Funktions-Ereignishandler, der dem aktuellen-Objekt zugeordnet ist `Module::GenericReleaseNotifier` .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>Module:: generikreleasenotifier:: callback_

Enthält den Lambda-, Funktor-oder Zeiger-zu-Funktions-Ereignishandler, der dem aktuellen-Objekt zugeordnet ist `Module::GenericReleaseNotifier` .

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>Module:: generifileasenotifier:: generikreleasenotifier

Initialisiert eine neue Instanz der `Module::GenericReleaseNotifier`-Klasse.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Parameter

*Rück*<br/>
Ein Lambda-, Funktor-oder Zeiger-zu-Funktions-Ereignishandler, der mit dem Funktions Operator "Klammern" () aufgerufen werden kann `()` .

*Abgabe*<br/>
Geben **`true`** Sie an, um den Aufruf der zugrunde liegenden [Module:: releasenotifier:: Release ()](module-releasenotifier-class.md#releasenotifier-release) -Methode zu aktivieren; andernfalls geben Sie an **`false`** .

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>Module:: generikreleasenotifier:: aufrufen

Ruft den Ereignishandler auf, der dem aktuellen-Objekt zugeordnet ist `Module::GenericReleaseNotifier` .

```cpp
void Invoke();
```
