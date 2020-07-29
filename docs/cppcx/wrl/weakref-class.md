---
title: WeakRef-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
- client/Microsoft::WRL::WeakRef::~WeakRef
- client/Microsoft::WRL::WeakRef::As
- client/Microsoft::WRL::WeakRef::AsIID
- client/Microsoft::WRL::WeakRef::CopyTo
- client/Microsoft::WRL::WeakRef::operator&
- client/Microsoft::WRL::WeakRef::WeakRef
helpviewer_keywords:
- Microsoft::WRL::WeakRef class
- Microsoft::WRL::WeakRef::~WeakRef, destructor
- Microsoft::WRL::WeakRef::As method
- Microsoft::WRL::WeakRef::AsIID method
- Microsoft::WRL::WeakRef::CopyTo method
- Microsoft::WRL::WeakRef::operator& operator
- Microsoft::WRL::WeakRef::WeakRef, constructor
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
ms.openlocfilehash: 715a823784aaa75f9abe349ef0a7ddc9e5d607d1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218350"
---
# <a name="weakref-class"></a>WeakRef-Klasse

Stellt einen *schwachen Verweis* dar, der nur durch die Windows-Runtime und nicht durch die klassische COM verwendet werden kann. Ein schwacher Verweis repräsentiert ein Objekt, auf das möglicherweise zugegriffen werden kann.

## <a name="syntax"></a>Syntax

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[WeakRef::WeakRef-Konstruktor](#weakref)|Initialisiert eine neue Instanz der `WeakRef`-Klasse.|
|[WeakRef::~WeakRef-Destruktor](#tilde-weakref)|Deinitialisiert die aktuelle Instanz der- `WeakRef` Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[WeakRef::As-Methode](#as)|Legt den angegebenen `ComPtr` Zeiger Parameter fest, der die angegebene Schnittstelle darstellt.|
|[WeakRef::AsIID-Methode](#asiid)|Legt den angegebenen `ComPtr` Zeiger Parameter fest, der die angegebene Schnittstellen-ID darstellt.|
|[WeakRef::CopyTo-Methode](#copyto)|Weist einer Schnittstelle einen Zeiger zu, falls verfügbar zur angegebenen Zeigervariablen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[WeakRef::operator&-Operator](#operator-ampersand-operator)|Gibt ein- `ComPtrRef` Objekt zurück, das das aktuelle- `WeakRef` Objekt darstellt.|

## <a name="remarks"></a>Bemerkungen

Ein `WeakRef` -Objekt verwaltet einen *starken Verweis*, der einem-Objekt zugeordnet ist und gültig oder ungültig sein kann. Rufen Sie die- `As()` oder- `AsIID()` Methode auf, um einen starken Verweis abzurufen. Wenn der starke Verweis gültig ist, kann er auf das zugeordnete Objekt zugreifen. Wenn der starke Verweis ungültig ist ( **`nullptr`** ), ist der Zugriff auf das zugeordnete Objekt nicht möglich.

Ein- `WeakRef` Objekt wird normalerweise verwendet, um ein Objekt darzustellen, dessen vorhanden sein durch einen externen Thread oder eine externe Anwendung gesteuert wird. Erstellen Sie z. b `WeakRef` . ein-Objekt aus einem Verweis auf ein Datei Objekt. Solange die Datei geöffnet ist, ist der starke Verweis gültig. Wenn die Datei aber geschlossen wird, wird der starke Verweis ungültig.

Beachten Sie, dass es eine Verhaltensänderung bei den Methoden [As](#as), [AsIID](#asiid) und [CopyTo](#copyto) im Windows 10 SDK gibt. Zuvor konnten Sie nach dem Aufrufen einer dieser Methoden die für prüfen, `WeakRef` **`nullptr`** um zu bestimmen, ob ein starker Verweis erfolgreich abgerufen wurde, wie im folgenden Code:

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)
{
    wprintf(L"Couldn’t get strong ref!");
}
```

Dieser Code funktioniert bei Verwendung des Windows 10 SDKs (oder höher) nicht. Überprüfen Sie stattdessen den Zeiger, der für übergebenen wurde **`nullptr`** .

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ComPtr`

`WeakRef`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** client.h

**Namespace:** Microsoft::WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>Weakref:: ~ weakref-Dekonstruktor

Deinitialisiert die aktuelle Instanz der- `WeakRef` Klasse.

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>Weakref:: As-Methode

Legt den angegebenen `ComPtr` Zeiger Parameter fest, der die angegebene Schnittstelle darstellt.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>Parameter

*U*<br/>
Eine Schnittstellen-ID.

*ptr*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein-Objekt, das den Parameter *U*darstellt.

### <a name="return-value"></a>Rückgabewert

- S_OK, wenn dieser Vorgang erfolgreich ist. andernfalls ein HRESULT, das den Grund für den fehlgeschlagenen Vorgang angibt, und *ptr* auf festgelegt ist **`nullptr`** .

- S_OK, wenn dieser Vorgang erfolgreich ist, das aktuelle `WeakRef` Objekt aber bereits freigegeben wurde. Der *ptr* -Parameter ist auf festgelegt **`nullptr`** .

- S_OK, wenn dieser Vorgang erfolgreich ist, das aktuelle `WeakRef` Objekt aber nicht vom Parameter *U*abgeleitet ist. Der *ptr* -Parameter ist auf festgelegt **`nullptr`** .

### <a name="remarks"></a>Bemerkungen

Ein Fehler wird ausgegeben, wenn der Parameter *U* ist `IWeakReference` oder nicht von abgeleitet ist `IInspectable` .

Die erste Vorlage ist die Form, die Sie in Ihrem Code verwenden sollten. Die zweite Vorlage ist eine interne Hilfsspezialisierung, die C++-Sprachfeatures unterstützt, wie etwa das Schlüsselwort [auto](../../cpp/auto-cpp.md) zur Typableitung.

Beginnend mit dem Windows 10 SDK legt diese Methode die-Instanz nicht `WeakRef` auf fest, **`nullptr`** Wenn der schwache Verweis nicht abgerufen werden konnte. Daher sollten Sie Code zur Fehlerüberprüfung vermeiden, der die `WeakRef` für prüft **`nullptr`** . Überprüfen Sie stattdessen *ptr* auf **`nullptr`** .

## <a name="weakrefasiid-method"></a><a name="asiid"></a>Weakref:: asiid-Methode

Legt den angegebenen `ComPtr` Zeiger Parameter fest, der die angegebene Schnittstellen-ID darstellt.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*ptr*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein Objekt, das den Parameter " *riid*" darstellt.

### <a name="return-value"></a>Rückgabewert

- S_OK, wenn dieser Vorgang erfolgreich ist. andernfalls ein HRESULT, das den Grund für den fehlgeschlagenen Vorgang angibt, und *ptr* auf festgelegt ist **`nullptr`** .

- S_OK, wenn dieser Vorgang erfolgreich ist, das aktuelle `WeakRef` Objekt aber bereits freigegeben wurde. Der *ptr* -Parameter ist auf festgelegt **`nullptr`** .

- S_OK, wenn dieser Vorgang erfolgreich ist, das aktuelle `WeakRef` Objekt aber nicht vom Parameter *riid*abgeleitet ist. Der *ptr* -Parameter ist auf festgelegt **`nullptr`** . (Weitere Informationen finden Sie in den Hinweisen.)

### <a name="remarks"></a>Bemerkungen

Wenn der Parameter " *riid* " nicht von abgeleitet ist, wird ein Fehler ausgegeben `IInspectable` . Dieser Fehler hat Vorrang vor den Rückgabewert.

Die erste Vorlage ist die Form, die Sie in Ihrem Code verwenden sollten. Die zweite Vorlage (die hier nicht dargestellt, aber in der Headerdatei deklariert ist) ist eine interne Hilfsspezialisierung, die C++-Sprachfeatures unterstützt, wie etwa das Schlüsselwort [auto](../../cpp/auto-cpp.md) zur Typableitung.

Beginnend mit dem Windows 10 SDK legt diese Methode die-Instanz nicht `WeakRef` auf fest, **`nullptr`** Wenn der schwache Verweis nicht abgerufen werden konnte. Daher sollten Sie Code zur Fehlerüberprüfung vermeiden, der die `WeakRef` für prüft **`nullptr`** . Überprüfen Sie stattdessen *ptr* auf **`nullptr`** .

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>Weakref:: CopyTo-Methode

Weist einer Schnittstelle einen Zeiger zu, falls verfügbar zur angegebenen Zeigervariablen.

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>Parameter

*U*<br/>
Zeiger auf eine- `IInspectable` Schnittstelle. Wenn *U* nicht von abgeleitet ist, wird ein Fehler ausgegeben `IInspectable` .

*riid*<br/>
Eine Schnittstellen-ID. Wenn *riid* nicht von abgeleitet ist, wird ein Fehler ausgegeben `IWeakReference` .

*ptr*<br/>
Ein doppelt indirekter Zeiger auf `IInspectable` oder `IWeakReference` .

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt. Weitere Informationen finden Sie unter " **Hinweise**".

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert „S_OK“ bedeutet, dass dieser Vorgang erfolgreich war, gibt aber nicht an, ob der schwache Verweis zu einem starken Verweis aufgelöst wurde. Wenn S_OK zurückgegeben wird, testen Sie, ob der Parameter *p* ein starker Verweis ist. Das heißt, dass der Parameter *p* nicht gleich ist **`nullptr`** .

Beginnend mit dem Windows 10 SDK legt diese Methode die-Instanz nicht `WeakRef` auf fest, **`nullptr`** Wenn der schwache Verweis nicht abgerufen werden konnte. Daher sollten Sie Code zur Fehlerüberprüfung vermeiden, der die `WeakRef` für prüft **`nullptr`** . Überprüfen Sie stattdessen *ptr* auf **`nullptr`** .

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>Weakref:: Operator- &amp; Operator

Gibt ein- `ComPtrRef` Objekt zurück, das das aktuelle- `WeakRef` Objekt darstellt.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Rückgabewert

Ein- `ComPtrRef` Objekt, das das aktuelle- `WeakRef` Objekt darstellt.

### <a name="remarks"></a>Bemerkungen

Dabei handelt es sich um einen internen Hilfsoperator, der nicht für die Verwendung im Code vorgesehen ist.

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>Weakref:: weakref-Konstruktor

Initialisiert eine neue Instanz der `WeakRef`-Klasse.

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>Parameter

*ptr*<br/>
Ein Zeiger, ein Verweis oder ein rvalue-Verweis auf ein vorhandenes Objekt, das das aktuelle-Objekt initialisiert `WeakRef` .

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert ein leeres- `WeakRef` Objekt. Der zweite Konstruktor initialisiert ein- `WeakRef` Objekt von einem Zeiger auf die- `IWeakReference` Schnittstelle. Der dritte Konstruktor initialisiert ein- `WeakRef` Objekt aus einem Verweis auf ein- `ComPtr<IWeakReference>` Objekt. Der vierte und fünfte Konstruktoren initialisiert ein- `WeakRef` Objekt aus einem anderen- `WeakRef` Objekt.
