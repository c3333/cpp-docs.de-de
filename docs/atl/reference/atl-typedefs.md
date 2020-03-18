---
title: ATL-Typedefs
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
ms.openlocfilehash: f3db32e85ea9cba1e946db6259c00c621650e969
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423603"
---
# <a name="atl-typedefs"></a>ATL-Typedefs

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
|[CContainedWindow](#ccontainedwindow)|Diese Klasse ist eine Spezialisierung von `CContainedWindowT`.|
|[CPath](#cpath)|Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CString`.|
|[Cpytha](#cpatha)|Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CStringA`.|
|[Cpathw](#cpathw)|Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CStringW`.|
|[Csimplevalarray](#csimplevalarray)|Stellt ein Array zum Speichern von einfachen Typen dar.|
|[Defaultthreadmerkmalen](#defaultthreadtraits)|Die standardmäßige Thread Merkmale-Klasse.|
|[Lpcurl](#lpcurl)|Ein Zeiger auf ein konstantes [CUrl](../../atl/reference/curl-class.md) -Objekt.|
|[Lpurl](#lpurl)|Ein Zeiger auf ein [CUrl](../../atl/reference/curl-class.md) -Objekt.|

##  <a name="_atl_base_module"></a>_ATL_BASE_MODULE

Definiert als typedef basierend auf _ATL_BASE_MODULE70.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Hinweise

Wird in jedem ATL-Projekt verwendet. Basierend auf [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Klassen, die Teil der ATL 7,0-Modul Klassen sind, werden von der _ATL_BASE_MODULE Struktur abgeleitet.  Weitere Informationen zu ATL-Modul Klassen finden Sie unter [com modules Classes](../../atl/com-modules-classes.md).

## <a name="requirements"></a>Voraussetzungen

**Header:** atlcore. h

##  <a name="_atl_com_module"></a>_ATL_COM_MODULE

Definiert als typedef basierend auf _ATL_COM_MODULE70.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Hinweise

Wird von ATL-Projekten verwendet, die com-Funktionen verwenden. Basierend auf [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Voraussetzungen

**Header:** atlbase. h

##  <a name="_atl_module"></a>_ATL_MODULE

Definiert als typedef basierend auf _ATL_MODULE70.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Voraussetzungen

**Header:**

### <a name="remarks"></a>Hinweise

Basierend auf [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

##  <a name="_atl_win_module"></a>_ATL_WIN_MODULE

Definiert als typedef basierend auf _ATL_WIN_MODULE70.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Hinweise

Wird von ATL-Projekten verwendet, die windowingfunktionen verwenden. Basierend auf [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Voraussetzungen

**Header:** atlbase. h

##  <a name="atl_url_port"></a>ATL_URL_PORT

Der Typ, der von [CUrl](curl-class.md) zum Angeben einer Portnummer verwendet wird.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atlutil. h

##  <a name="ccomdispatchdriver"></a>Ccomdispatchdriver

Diese Klasse verwaltet com-Schnittstellen Zeiger.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atlbase. h

##  <a name="ccomglobalsthreadmodel"></a>Ccomglobalsthread Model

Ruft die entsprechenden Thread Modell Methoden auf, unabhängig davon, welches Threading Modell verwendet wird.

```
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

### <a name="remarks"></a>Hinweise

Abhängig vom Threading Modell, das von Ihrer Anwendung verwendet wird, verweist der **typedef** -Name `CComGlobalsThreadModel` entweder auf [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oder [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Diese Klassen stellen zusätzliche `typedef` Namen bereit, um auf eine kritische Abschnitts Klasse zu verweisen.

> [!NOTE]
> `CComGlobalsThreadModel` verweist nicht auf Klasse [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md).

Wenn Sie `CComGlobalsThreadModel` verwenden, werden Sie von der Angabe einer bestimmten Threading Modell Klasse befreit. Unabhängig davon, welches Threading Modell verwendet wird, werden die entsprechenden Methoden aufgerufen.

Zusätzlich zu `CComGlobalsThreadModel`stellt ATL den **typedef** -Namen [ccomobjectthreadmodel](#ccomobjectthreadmodel)bereit. Die Klasse, auf die von den einzelnen `typedef` verwiesen wird, hängt vom verwendeten Threading Modell ab, wie in der folgenden Tabelle dargestellt:

|Typedef|Single Threading|Apartment Threading|Kostenloses Threading|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

Verwenden Sie `CComObjectThreadModel` innerhalb einer einzelnen Objektklasse. Verwenden Sie `CComGlobalsThreadModel` in einem Objekt, das für Ihr Programm Global verfügbar ist, oder wenn Sie Modul Ressourcen über mehrere Threads hinweg schützen möchten.

## <a name="requirements"></a>Voraussetzungen

**Header:** atlbase. h

##  <a name="ccomobjectthreadmodel"></a>Ccomobjectthreadmodel

Ruft die entsprechenden Thread Modell Methoden auf, unabhängig davon, welches Threading Modell verwendet wird.

```
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

### <a name="remarks"></a>Hinweise

Abhängig vom Threading Modell, das von Ihrer Anwendung verwendet wird, verweist der `typedef` Name `CComObjectThreadModel` entweder auf [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oder [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Diese Klassen stellen zusätzliche `typedef` Namen bereit, um auf eine kritische Abschnitts Klasse zu verweisen.

> [!NOTE]
> `CComObjectThreadModel` verweist nicht auf Klasse [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md).

Wenn Sie `CComObjectThreadModel` verwenden, werden Sie von der Angabe einer bestimmten Threading Modell Klasse befreit. Unabhängig davon, welches Threading Modell verwendet wird, werden die entsprechenden Methoden aufgerufen.

Zusätzlich zu `CComObjectThreadModel`stellt ATL den **typedef** -Namen [ccomglobalsthlmodel](#ccomglobalsthreadmodel)bereit. Die Klasse, auf die jede **typedef** verweist, hängt vom verwendeten Threading Modell ab, wie in der folgenden Tabelle gezeigt:

|Typedef|Single Threading|Apartment Threading|Kostenloses Threading|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

Verwenden Sie `CComObjectThreadModel` innerhalb einer einzelnen Objektklasse. Verwenden Sie `CComGlobalsThreadModel` in einem Objekt, das für Ihr Programm Global verfügbar ist, oder wenn Sie Modul Ressourcen über mehrere Threads hinweg schützen möchten.

## <a name="requirements"></a>Voraussetzungen

**Header:** atlbase. h

##  <a name="ccontainedwindow"></a>CContainedWindow

Diese Klasse ist eine Spezialisierung von `CContainedWindowT`.

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atlwin. h

### <a name="remarks"></a>Hinweise

`CContainedWindow` ist eine Spezialisierung von [ccontainedwindowt](../../atl/reference/ccontainedwindowt-class.md). Wenn Sie die Basisklasse oder die Merkmale ändern möchten, verwenden Sie `CContainedWindowT` direkt.

##  <a name="cpath"></a>CPath

Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CString`.

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atlpath. h

##  <a name="cpatha"></a>Cpytha

Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CStringA`.

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atlpath. h

##  <a name="cpathw"></a>Cpathw

Eine Spezialisierung von [cpatht](../../atl/reference/cpatht-class.md) mithilfe von `CStringW`.

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atlpath. h

##  <a name="csimplevalarray"></a>Csimplevalarray

Stellt ein Array zum Speichern von einfachen Typen dar.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Hinweise

`CSimpleValArray` wird zum Erstellen und Verwalten von Arrays bereitgestellt, die einfache Datentypen enthalten. Es handelt sich um eine einfache #define von [CSimpleArray](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Voraussetzungen

**Header:** atlsimpcoll. h

##  <a name="lpcurl"></a>Lpcurl

Ein Zeiger auf ein konstantes [CUrl](../../atl/reference/curl-class.md) -Objekt.

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atlutil. h

##  <a name="defaultthreadtraits"></a>Defaultthreadmerkmalen

Die standardmäßige Thread Merkmale-Klasse.

### <a name="syntax"></a>Syntax

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Hinweise

Wenn das aktuelle Projekt die multithreadcrt verwendet, wird defaultthreadmerkmalen als crtthreadmerkmalen definiert. Andernfalls wird Win32ThreadTraits verwendet.

## <a name="requirements"></a>Voraussetzungen

**Header:** atlbase. h

##  <a name="lpurl"></a>Lpurl

Ein Zeiger auf ein [CUrl](../../atl/reference/curl-class.md) -Objekt.

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atlutil. h

## <a name="see-also"></a>Siehe auch

[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)<br/>
[Funktionen](../../atl/reference/atl-functions.md)<br/>
[Globale Variablen](../../atl/reference/atl-global-variables.md)<br/>
[Klassen und Strukturen](../../atl/reference/atl-classes.md)<br/>
[Makros](../../atl/reference/atl-macros.md)
