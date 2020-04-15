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
ms.openlocfilehash: 681f5a64c3e2902c66facbd4f0ac3a3663a7e79d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374252"
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
|[WeakRef::WeakRef-Konstruktor](#weakref)|Initialisiert eine neue Instanz der Klasse `WeakRef`.|
|[WeakRef::~WeakRef-Destruktor](#tilde-weakref)|Deinitialisiert die aktuelle Instanz `WeakRef` der Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[WeakRef::As-Methode](#as)|Legt den `ComPtr` angegebenen Zeigerparameter fest, um die angegebene Schnittstelle darzustellen.|
|[WeakRef::AsIID-Methode](#asiid)|Legt den `ComPtr` angegebenen Zeigerparameter fest, um die angegebene Schnittstellen-ID darzustellen.|
|[WeakRef::CopyTo-Methode](#copyto)|Weist einer Schnittstelle einen Zeiger zu, falls verfügbar zur angegebenen Zeigervariablen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[WeakRef::operator&-Operator](#operator-ampersand-operator)|Gibt `ComPtrRef` ein Objekt zurück, das das aktuelle `WeakRef` Objekt darstellt.|

## <a name="remarks"></a>Bemerkungen

Ein `WeakRef` Objekt verwaltet einen *starken Verweis*, der einem Objekt zugeordnet ist und gültig oder ungültig sein kann. Rufen `As()` Sie `AsIID()` die oder-Methode auf, um einen starken Verweis zu erhalten. Wenn der starke Verweis gültig ist, kann er auf das zugeordnete Objekt zugreifen. Wenn der starke Verweis ungültig ist (`nullptr`), ist der Zugriff auf das zugeordnete Objekt nicht möglich.

Ein `WeakRef` Objekt wird in der Regel verwendet, um ein Objekt darzustellen, dessen Vorhandensein von einem externen Thread oder einer anwendung gesteuert wird. Erstellen Sie beispielsweise `WeakRef` ein Objekt aus einem Verweis auf ein Dateiobjekt. Solange die Datei geöffnet ist, ist der starke Verweis gültig. Wenn die Datei aber geschlossen wird, wird der starke Verweis ungültig.

Beachten Sie, dass es eine Verhaltensänderung bei den Methoden [As](#as), [AsIID](#asiid) und [CopyTo](#copyto) im Windows 10 SDK gibt. Zuvor konnten Sie nach dem Aufruf einer `WeakRef` `nullptr` dieser Methoden die For überprüfen, um festzustellen, ob ein starker Verweis erfolgreich abgerufen wurde, wie im folgenden Code:

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

Dieser Code funktioniert bei Verwendung des Windows 10 SDKs (oder höher) nicht. Überprüfen Sie stattdessen den Zeiger, `nullptr`der für übergeben wurde.

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ComPtr`

`WeakRef`

## <a name="requirements"></a>Anforderungen

**Header:** client.h

**Namespace:** Microsoft::WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>WeakRef::-SchwachRef-Destruktor

Deinitialisiert die aktuelle Instanz `WeakRef` der Klasse.

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>WeakRef::As-Methode

Legt den `ComPtr` angegebenen Zeigerparameter fest, um die angegebene Schnittstelle darzustellen.

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

*Ptr*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Objekt, das den Parameter U darstellt, von einem Objekt mit dem Parameter *U*.

### <a name="return-value"></a>Rückgabewert

- S_OK, wenn dieser Vorgang erfolgreich ist. Andernfalls wird ein HRESULT, das den Grund für den `nullptr`Fehler vorgangsangegeben hat, und *ptr* auf festgelegt.

- S_OK, wenn dieser Vorgang erfolgreich `WeakRef` ist, aber das aktuelle Objekt wurde bereits freigegeben. Parameter *ptr* ist `nullptr`auf gesetzt.

- S_OK, wenn dieser Vorgang erfolgreich `WeakRef` ist, das aktuelle Objekt jedoch nicht vom Parameter *U*abgeleitet wird. Parameter *ptr* ist `nullptr`auf gesetzt.

### <a name="remarks"></a>Bemerkungen

Ein Fehler wird angezeigt, *U* wenn `IWeakReference`Parameter U ist `IInspectable`, oder nicht von abgeleitet wird.

Die erste Vorlage ist die Form, die Sie in Ihrem Code verwenden sollten. Die zweite Vorlage ist eine interne Hilfsspezialisierung, die C++-Sprachfeatures unterstützt, wie etwa das Schlüsselwort [auto](../../cpp/auto-cpp.md) zur Typableitung.

Ab dem Windows 10 SDK wird die `WeakRef` Instanz `nullptr` nicht festgelegt, wenn der schwache Verweis nicht abgerufen werden `WeakRef` konnte. `nullptr` Überprüfen Sie stattdessen `nullptr` *ptr* für .

## <a name="weakrefasiid-method"></a><a name="asiid"></a>WeakRef::AsIID-Methode

Legt den `ComPtr` angegebenen Zeigerparameter fest, um die angegebene Schnittstellen-ID darzustellen.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*Ptr*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Objekt, das den Parameter *riid*darstellt.

### <a name="return-value"></a>Rückgabewert

- S_OK, wenn dieser Vorgang erfolgreich ist. Andernfalls wird ein HRESULT, das den Grund für den `nullptr`Fehler vorgangsangegeben hat, und *ptr* auf festgelegt.

- S_OK, wenn dieser Vorgang erfolgreich `WeakRef` ist, aber das aktuelle Objekt wurde bereits freigegeben. Parameter *ptr* ist `nullptr`auf gesetzt.

- S_OK, wenn dieser Vorgang erfolgreich `WeakRef` ist, aber das aktuelle Objekt nicht vom Parameter *riid*abgeleitet wird. Parameter *ptr* ist `nullptr`auf gesetzt. (Weitere Informationen finden Sie in den Hinweisen.)

### <a name="remarks"></a>Bemerkungen

Ein Fehler wird angezeigt, wenn der Parameter `IInspectable` *riid* nicht von abgeleitet wird. Dieser Fehler hat Vorrang vor den Rückgabewert.

Die erste Vorlage ist die Form, die Sie in Ihrem Code verwenden sollten. Die zweite Vorlage (die hier nicht dargestellt, aber in der Headerdatei deklariert ist) ist eine interne Hilfsspezialisierung, die C++-Sprachfeatures unterstützt, wie etwa das Schlüsselwort [auto](../../cpp/auto-cpp.md) zur Typableitung.

Ab dem Windows 10 SDK wird die `WeakRef` Instanz `nullptr` nicht festgelegt, wenn der schwache Verweis nicht abgerufen werden `WeakRef` konnte. `nullptr` Überprüfen Sie stattdessen `nullptr` *ptr* für .

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>WeakRef::CopyTo-Methode

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
Zeiger auf `IInspectable` eine Schnittstelle. Ein Fehler wird angezeigt, wenn *U* nicht von `IInspectable`abgeleitet wird.

*riid*<br/>
Eine Schnittstellen-ID. Ein Fehler wird angezeigt, wenn *riid* nicht von `IWeakReference`abgeleitet wird.

*Ptr*<br/>
Ein doppelt indirekter Zeiger auf `IInspectable` `IWeakReference`oder .

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt. Weitere Informationen finden Sie unter **Bemerkungen**.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert „S_OK“ bedeutet, dass dieser Vorgang erfolgreich war, gibt aber nicht an, ob der schwache Verweis zu einem starken Verweis aufgelöst wurde. Wenn S_OK zurückgegeben wird, testen Sie, dass Parameter *p* ein starker Verweis ist. d. h., Parameter *p* `nullptr`ist nicht gleich .

Ab dem Windows 10 SDK wird die `WeakRef` Instanz `nullptr` nicht festgelegt, wenn der schwache Verweis nicht abgerufen werden `WeakRef` `nullptr`konnte. Überprüfen Sie stattdessen `nullptr` *ptr* für .

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>WeakRef::Operator-Operator&amp;

Gibt `ComPtrRef` ein Objekt zurück, das das aktuelle `WeakRef` Objekt darstellt.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Rückgabewert

Ein `ComPtrRef` Objekt, das `WeakRef` das aktuelle Objekt darstellt.

### <a name="remarks"></a>Bemerkungen

Dies ist ein interner Hilfsoperator, der nicht für die Verwendung in Ihrem Code gedacht ist.

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>WeakRef::WeakRef-Konstruktor

Initialisiert eine neue Instanz der Klasse `WeakRef`.

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

*Ptr*<br/>
Ein Zeiger, Verweis oder rvalue-Verweis auf ein vorhandenes `WeakRef` Objekt, das das aktuelle Objekt initialisiert.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert `WeakRef` ein leeres Objekt. Der zweite Konstruktor initialisiert ein `WeakRef` Objekt von `IWeakReference` einem Zeiger auf die Schnittstelle. Der dritte Konstruktor initialisiert ein `WeakRef` Objekt `ComPtr<IWeakReference>` aus einem Verweis auf ein Objekt. Der vierte und fünfte Konstruktor `WeakRef` initialisieren `WeakRef` ein Objekt aus einem anderen Objekt.
