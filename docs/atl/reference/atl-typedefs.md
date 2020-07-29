---
title: ATL-TypeDefs
ms.date: 11/04/2016
f1_keywords:
- atlcore/ATL::_ATL_BASE_MODULE
- atlbase/ATL::_ATL_COM_MODULE
- atlbase/ATL::_ATL_MODULE
- atlbase/ATL::_ATL_WIN_MODULE
- atlutil/ATL::ATL_URL_PORT
- atlbase/ATL::CComDispatchDriver
- atlbase/ATL::CComGlobalsThreadModel
- atlbase/ATL::CComObjectThreadModel
- atlwin/ATL::CContainedWindow
- atlpath/ATL::CPath
- atlpath/ATL::CPathA
- atlpath/ATL::CPathW
- " atlsimpcoll/ATL::CSimpleValArray"
- " atlutil/ATL::LPCURL"
- atlbase/ATL::DefaultThreadTraits
- atlutil/ATL::LPURL
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
ms.openlocfilehash: a6b1ce33fe201338a0cc9356f2ef86e598629fd6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228036"
---
# <a name="atl-typedefs"></a>ATL-TypeDefs

Die Active Template Library enthält die folgenden Typedefs.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Definiert als typedef basierend auf [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Definiert als typedef basierend auf [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Definiert als typedef basierend auf [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Definiert als typedef basierend auf [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Der Typ, der von [CUrl](../../atl/reference/curl-class.md) zum Angeben einer Portnummer verwendet wird.|
|[Ccomdispatchdriver](#ccomdispatchdriver)|Diese Klasse verwaltet com-Schnittstellen Zeiger.|
|[Ccomglobalsthread Model](#ccomglobalsthreadmodel)|Ruft die entsprechenden Thread Modell Methoden auf, unabhängig davon, welches Threading Modell verwendet wird.|
|[Ccomobjectthreadmodel](#ccomobjectthreadmodel)|Ruft die entsprechenden Thread Modell Methoden auf, unabhängig davon, welches Threading Modell verwendet wird.|
|[CContainedWindow](#ccontainedwindow)|Diese Klasse ist eine Spezialisierung von `CContainedWindowT` .|
|[CPath](#cpath)|Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CString` .|
|[Cpytha](#cpatha)|Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CStringA` .|
|[Cpathw](#cpathw)|Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CStringW` .|
|[Csimplevalarray](#csimplevalarray)|Stellt ein Array zum Speichern von einfachen Typen dar.|
|[Defaultthreadmerkmalen](#defaultthreadtraits)|Die standardmäßige Thread Merkmale-Klasse.|
|[Lpcurl](#lpcurl)|Ein Zeiger auf ein konstantes [CUrl](../../atl/reference/curl-class.md) -Objekt.|
|[Lpurl](#lpurl)|Ein Zeiger auf ein [CUrl](../../atl/reference/curl-class.md) -Objekt.|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

Definiert als typedef basierend auf _ATL_BASE_MODULE70.

```cpp
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Bemerkungen

Wird in jedem ATL-Projekt verwendet. Basierend auf [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Klassen, die Teil der ATL 7,0-Modul Klassen sind, werden von der _ATL_BASE_MODULE Struktur abgeleitet.  Weitere Informationen zu ATL-Modul Klassen finden Sie unter [com modules Classes](../../atl/com-modules-classes.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcore. h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

Definiert als typedef basierend auf _ATL_COM_MODULE70.

```cpp
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Bemerkungen

Wird von ATL-Projekten verwendet, die com-Funktionen verwenden. Basierend auf [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

Definiert als typedef basierend auf _ATL_MODULE70.

```cpp
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header**

### <a name="remarks"></a>Bemerkungen

Basierend auf [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

Definiert als typedef basierend auf _ATL_WIN_MODULE70.

```cpp
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Bemerkungen

Wird von ATL-Projekten verwendet, die windowingfunktionen verwenden. Basierend auf [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

Der Typ, der von [CUrl](curl-class.md) zum Angeben einer Portnummer verwendet wird.

```cpp
typedef WORD ATL_URL_PORT;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlutil. h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>Ccomdispatchdriver

Diese Klasse verwaltet com-Schnittstellen Zeiger.

```cpp
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>Ccomglobalsthread Model

Ruft die entsprechenden Thread Modell Methoden auf, unabhängig davon, welches Threading Modell verwendet wird.

```cpp
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>Bemerkungen

Abhängig vom Threading Modell, das von Ihrer Anwendung verwendet wird **`typedef`** , `CComGlobalsThreadModel` verweist der Name entweder auf [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oder [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Diese Klassen stellen zusätzliche **`typedef`** Namen bereit, um auf eine kritische Abschnitts Klasse zu verweisen.

> [!NOTE]
> `CComGlobalsThreadModel`verweist nicht auf Klasse [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md).

Wenn Sie verwenden, wird `CComGlobalsThreadModel` eine bestimmte Threading Modell Klasse nicht angegeben. Unabhängig davon, welches Threading Modell verwendet wird, werden die entsprechenden Methoden aufgerufen.

Zusätzlich zu `CComGlobalsThreadModel` stellt ATL den **`typedef`** Namen [ccomobjectthreadmodel](#ccomobjectthreadmodel)bereit. Die Klasse, auf die jeweils verwiesen wird **`typedef`** , hängt vom verwendeten Threading Modell ab, wie in der folgenden Tabelle dargestellt:

|Typedef|Single Threading|Apartment Threading|Kostenloses Threading|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|E|E|M|
|`CComGlobalsThreadModel`|E|M|M|

S = `CComSingleThreadModel` ; M =`CComMultiThreadModel`

Verwendung `CComObjectThreadModel` innerhalb einer einzelnen Objektklasse. Verwenden `CComGlobalsThreadModel` Sie in einem Objekt, das für Ihr Programm Global verfügbar ist, oder wenn Sie Modul Ressourcen über mehrere Threads hinweg schützen möchten.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>Ccomobjectthreadmodel

Ruft die entsprechenden Thread Modell Methoden auf, unabhängig davon, welches Threading Modell verwendet wird.

```cpp
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComObjectThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>Bemerkungen

Abhängig vom Threading Modell, das von Ihrer Anwendung verwendet wird **`typedef`** , `CComObjectThreadModel` verweist der Name entweder auf [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oder [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Diese Klassen stellen zusätzliche **`typedef`** Namen bereit, um auf eine kritische Abschnitts Klasse zu verweisen.

> [!NOTE]
> `CComObjectThreadModel`verweist nicht auf Klasse [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md).

Wenn Sie verwenden, wird `CComObjectThreadModel` eine bestimmte Threading Modell Klasse nicht angegeben. Unabhängig davon, welches Threading Modell verwendet wird, werden die entsprechenden Methoden aufgerufen.

Zusätzlich zu `CComObjectThreadModel` wird von ATL der **`typedef`** Name [ccomglobalsthlmodel](#ccomglobalsthreadmodel)bereitstellt. Die Klasse, auf die jeweils verwiesen wird **`typedef`** , hängt vom verwendeten Threading Modell ab, wie in der folgenden Tabelle dargestellt:

|Typedef|Single Threading|Apartment Threading|Kostenloses Threading|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|E|E|M|
|`CComGlobalsThreadModel`|E|M|M|

S = `CComSingleThreadModel` ; M =`CComMultiThreadModel`

Verwendung `CComObjectThreadModel` innerhalb einer einzelnen Objektklasse. Verwenden `CComGlobalsThreadModel` Sie in einem Objekt, das für Ihr Programm Global verfügbar ist, oder wenn Sie Modul Ressourcen über mehrere Threads hinweg schützen möchten.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>CContainedWindow

Diese Klasse ist eine Spezialisierung von `CContainedWindowT` .

```cpp
typedef CContainedWindowT<CWindow> CContainedWindow;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

### <a name="remarks"></a>Bemerkungen

`CContainedWindow`ist eine Spezialisierung von [ccontainedwindowt](../../atl/reference/ccontainedwindowt-class.md). Wenn Sie die Basisklasse oder die Merkmale ändern möchten, verwenden Sie `CContainedWindowT` direkt.

## <a name="cpath"></a><a name="cpath"></a>CPath

Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CString` .

```cpp
typedef CPathT<CString> CPath;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlpath. h

## <a name="cpatha"></a><a name="cpatha"></a>Cpytha

Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CStringA` .

```cpp
typedef CPathT<CStringA> CPathA;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlpath. h

## <a name="cpathw"></a><a name="cpathw"></a>Cpathw

Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CStringW` .

```cpp
typedef ATL::CPathT<CStringW> CPathW;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlpath. h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>Csimplevalarray

Stellt ein Array zum Speichern von einfachen Typen dar.

```cpp
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Bemerkungen

`CSimpleValArray`wird zum Erstellen und Verwalten von Arrays bereitgestellt, die einfache Datentypen enthalten. Es handelt sich um eine einfache #define von [CSimpleArray](../../atl/reference/csimplearray-class.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlsimpcoll. h

## <a name="lpcurl"></a><a name="lpcurl"></a>Lpcurl

Ein Zeiger auf ein konstantes [CUrl](../../atl/reference/curl-class.md) -Objekt.

```cpp
typedef const CUrl* LPCURL;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlutil. h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>Defaultthreadmerkmalen

Die standardmäßige Thread Merkmale-Klasse.

### <a name="syntax"></a>Syntax

```cpp
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Bemerkungen

Wenn das aktuelle Projekt die multithreadcrt verwendet, wird defaultthreadmerkmalen als crtthreadmerkmalen definiert. Andernfalls wird Win32ThreadTraits verwendet.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="lpurl"></a><a name="lpurl"></a>Lpurl

Ein Zeiger auf ein [CUrl](../../atl/reference/curl-class.md) -Objekt.

```cpp
typedef CUrl* LPURL;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlutil. h

## <a name="see-also"></a>Siehe auch

[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)<br/>
[Funktionen](../../atl/reference/atl-functions.md)<br/>
[Globale Variablen](../../atl/reference/atl-global-variables.md)<br/>
[Klassen und Strukturen](../../atl/reference/atl-classes.md)<br/>
[Makros](../../atl/reference/atl-macros.md)
