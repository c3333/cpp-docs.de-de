---
title: Platform::COMException-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::COMException::HResult
- VCCORLIB/Platform::COMException::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: 1d0d36ec16303d6bdaa5f2344cd5d48fba03c8bf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444293"
---
# <a name="platformcomexception-class"></a>Platform::COMException-Klasse

Stellt COM-Fehler dar, die beim Ausführen einer Anwendung auftreten. COMException ist die Basisklasse für einen Satz vordefinierter Standardausnahmen.

## <a name="syntax"></a>Syntax

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Members

Die COMException-Klasse erbt von der Object-Klasse und den Schnittstellen IException, IPrintable und IEquatable.

COMException verfügt auch über die folgenden Membertypen.

**Konstruktoren**

|Member|BESCHREIBUNG|
|------------|-----------------|
|[COMException](#ctor)|Initialisiert eine neue Instanz der COMException-Klasse.|

**Methoden**

Die COMException-Klasse erbt die Methoden Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() und ToString() von der [Platform::Object Class](../cppcx/platform-object-class.md).

**Eigenschaften**

Die COMException-Klasse verfügt auch über die folgenden Eigenschaften.

|Member|BESCHREIBUNG|
|------------|-----------------|
|[Exception:: HRESULT](#hresult)|Das HRESULT, das der Ausnahme entspricht.|
|[Exception:: Message](#message)|Meldung, in der die Ausnahme beschrieben wird.|

## <a name="derived-exceptions"></a>Abgeleitete Ausnahmen

Die folgenden vordefinierten Ausnahmen werden von COMException abgeleitet. Sie unterscheiden sich von COMException nur im Namen, im Namen des Konstruktors und dem zugrunde liegenden HRESULT-Wert.

|Name|Zugrunde liegendes HRESULT|BESCHREIBUNG|
|----------|------------------------|-----------------|
|COMException|*Benutzerdefiniertes HRESULT*|Wird ausgelöst, wenn ein COM-Methodenaufruf ein unbekanntes HRESULT zurückgibt.|
|AccessDeniedException|E_ACCESSDENIED|Wird ausgelöst, wenn der Zugriff auf eine Ressource oder eine Funktion verweigert wird.|
|ChangedStateException|E_CHANGED_STATE|Wird ausgelöst, wenn Methoden eines Auflistungsiterators oder einer Auflistungsansicht aufgerufen werden, nachdem die übergeordnete Auflistung geändert wurde. Hierdurch werden die Ergebnisse der Methode ungültig.|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Wird ausgelöst, wenn eine COM-Klasse nicht registriert wurde.|
|DisconnectedException|RPC_E_DISCONNECTED|Wird ausgelöst, wenn ein Objekt von den Clients getrennt wurde.|
|FailureException|E_FAIL|Wird ausgelöst, wenn ein Vorgang fehlschlägt.|
|InvalidArgumentException|E_INVALIDARG|Wird ausgelöst, wenn eines der Argumente für eine Methode ungültig ist.|
|InvalidCastException|E_NOINTERFACE|Wird ausgelöst, wenn ein Typ nicht in einen anderen Typ umgewandelt werden kann.|
|NotImplementedException|E_NOTIMPL|Wird ausgelöst, wenn eine Schnittstellenmethode nicht bei der Klasse implementiert wurde.|
|NullReferenceException|E_POINTER|Wird ausgelöst, wenn der Versuch gemacht wird, einen Verweis auf ein NULL-Objekt zu dereferenzieren.|
|OperationCanceledException|E_ABORT|Wird nach dem Abbrechen eines Vorgangs ausgelöst.|
|OutOfBoundsException|E_BOUNDS|Wird ausgelöst, wenn ein Vorgang versucht, auf Daten außerhalb des gültigen Bereichs zuzugreifen.|
|OutOfMemoryException|E_OUTOFMEMORY|Wird ausgelöst, wenn nicht genügend Arbeitsspeicher vorhanden ist, um den Vorgang abzuschließen.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Mindestens unterstützter Client:** Windows 8

**Mindestens unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Metadaten:** platform.winmd

## <a name="ctor"></a>COMException:: COMException-Konstruktor

Initialisiert eine neue Instanz der COMException-Klasse.

### <a name="syntax"></a>Syntax

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>Parameter

*HRESULT*<br/>
Der Fehler HRESULT, der durch die Ausnahme repräsentiert wird.

## <a name="hresult"></a>COMException:: HRESULT-Eigenschaft

Das HRESULT, das der Ausnahme entspricht.

### <a name="syntax"></a>Syntax

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>Eigenschaftswert

Ein HRESULT-Wert, der den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zur Interpretation des HRESULT-Werts finden Sie unter [Struktur von com-Fehler Codes](/windows/win32/com/structure-of-com-error-codes).

## <a name="message"></a>COMException:: Message-Eigenschaft

Meldung, in der die Ausnahme beschrieben wird.

### <a name="syntax"></a>Syntax

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>Eigenschaftswert

Eine Beschreibung der Ausnahme.

## <a name="see-also"></a>Weitere Informationen

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)
