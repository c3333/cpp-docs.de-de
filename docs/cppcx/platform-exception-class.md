---
title: Platform::Exception-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
ms.openlocfilehash: bfdd8b3df720073e6b4a19cdb5b34db23e659fd0
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741968"
---
# <a name="platformexception-class"></a>Platform::Exception-Klasse

Stellt Fehler dar, die bei der Anwendungsausführung auftreten. Benutzerdefinierte Ausnahmeklassen können nicht von `Platform::Exception`abgeleitet werden. Wenn Sie eine benutzerdefinierte Ausnahme benötigen, können Sie `Platform::COMException` verwenden und ein app-spezifisches HRESULT angeben.

## <a name="syntax"></a>Syntax

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Member

Die `Exception` -Klasse erbt von der `Object` -Klasse und den Schnittstellen `IException`, `IPrintable`und `IEquatable` .

Die `Exception` -Klasse verfügt auch über die folgenden Arten von Membern.

### <a name="constructors"></a>Konstruktoren

|Member|Beschreibung|
|------------|-----------------|
|[Exception:: Exception](#ctor)|Initialisiert eine neue Instanz der `Exception`-Klasse.|

### <a name="methods"></a>Methoden

Die `Exception` -Klasse erbt die Methoden `Equals()`, `Finalize()`,`GetHashCode()`,`GetType()`,`MemberwiseClose()`und `ToString()` von [Platform::Object Class](../cppcx/platform-object-class.md)abgeleitet werden. Die `Exception` -Klasse verfügt auch über die folgende Methode.

|Member|Beschreibung|
|------------|-----------------|
|[Exception:: up Exception](#createexception)|Erstellt eine Ausnahme, die den angegebenen HRESULT-Wert darstellt.|

### <a name="properties"></a>Eigenschaften

Die Ausnahmeklasse verfügt auch über die folgenden Eigenschaften:

|Member|Beschreibung|
|------------|-----------------|
|[Exception:: HRESULT](#hresult)|Das HRESULT, das der Ausnahme entspricht.|
|[Exception:: Message](#message)|Eine Meldung, mit der die Ausnahme beschrieben wird. Dieser Wert ist schreibgeschützt und kann nicht geändert werden, nachdem `Exception` erstellt wurde.|

### <a name="requirements"></a>Anforderungen

**Mindestens unterstützter Client:** Windows 8

**Mindestens unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Metadaten:** Platform. winmd

## <a name="exceptioncreateexception-method"></a><a name="createexception"></a> Exception:: kreateexception-Methode

Erstellt ein Platform::Exception^ aus einem angegebenen HRESULT-Wert.

### <a name="syntax"></a>Syntax

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>Parameter

*Std.*<br/>
Ein HRESULT-Wert, den Sie in der Regel aus einem Aufruf an eine COM-Methode erhalten. Wenn der Wert 0 (null) ist, was S_OK entspricht, löst diese Methode [Platform:: InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) aus, da com-Methoden, die erfolgreich ausgeführt werden, keine Ausnahmen auslösen sollten.

*Nachricht*<br/>
Eine Zeichenfolge, die den Fehler beschreibt.

### <a name="return-value"></a>Rückgabewert

Eine Ausnahme, die den Fehler HRESULT darstellt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um eine Ausnahme aus einem HRESULT zu erstellen, die beispielsweise aus einem Aufruf einer COM-Schnittstellen-Methode zurückgegeben wird. Sie können die Überladung verwenden, die einen String^-Parameter erhält, um eine benutzerdefinierte Meldung bereitzustellen.

Es wird dringend empfohlen, mit der Verwendung von "" eine stark typisierte Ausnahme zu erstellen, anstatt eine [Platform:: COMException](../cppcx/platform-comexception-class.md) zu erstellen, die nur das HRESULT enthält.

## <a name="exceptionexception-constructor"></a><a name="ctor"></a> Exception:: Exception-Konstruktor

Initialisiert eine neue Instanz der Exception-Klasse.

### <a name="syntax"></a>Syntax

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>Parameter

*HRESULT*<br/>
Der Fehler HRESULT, der durch die Ausnahme repräsentiert wird.

*Nachricht*<br/>
Eine vom Benutzer angegebene Meldung, beispielsweise vorschreibender Text, der der Ausnahme zugeordnet ist. Im Allgemeinen sollten Sie die zweite Überladung verwenden, um eine beschreibende Meldung bereitzustellen, die möglichst spezifisch erläutert, wie und warum der Fehler aufgetreten ist.

## <a name="exceptionhresult-property"></a><a name="hresult"></a> Exception:: HRESULT-Eigenschaft

Das HRESULT, das der Ausnahme entspricht.

### <a name="syntax"></a>Syntax

```cpp
public:
    property int HResult { int get(); }
```

### <a name="property-value"></a>Eigenschaftswert

Der HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die meisten Ausnahmen fangen als COM-Fehler an, die als HRESULT-Werte zurückgegeben werden. C++/CX konvertiert diese Werte in Platform::Exception^-Objekte, und diese Eigenschaft speichert den Wert des ursprünglichen Fehlercodes.

## <a name="exceptionmessage-property"></a><a name="message"></a> Exception:: Message-Eigenschaft

Die Meldung, in der der Fehler beschrieben wird.

### <a name="syntax"></a>Syntax

```cpp
public:property String^ Message;
```

### <a name="property-value"></a>Eigenschaftswert

In den Ausnahmen, die aus der Windows Runtime stammen, ist dieses eine vom System bereitgestellte Beschreibung des Fehlers.

### <a name="remarks"></a>Bemerkungen

In Windows 8 ist diese Eigenschaft schreibgeschützt, da Ausnahmen in dieser Version der Windows-Runtime nur als HRESULTs über die ABI transportiert werden. Bei Windows 8.1 werden umfangreichere Ausnahmeinformationen über die ABI transportiert, und Sie können eine benutzerdefinierte Meldung bereitstellen, auf die andere Komponenten programmgesteuert zugreifen können. Weitere Informationen finden Sie unter [Ausnahmen (C++/CX)](../cppcx/exceptions-c-cx.md).

## <a name="see-also"></a>Weitere Informationen

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)
