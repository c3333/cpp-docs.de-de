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
ms.openlocfilehash: 5548bee36ac52dbd6add31241714b0404289be45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319197"
---
# <a name="atl-typedefs"></a>ATL-TypeDefs

Die Active Template Library enthält die folgenden typedefs.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Definiert als typedef basierend auf [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Definiert als typedef basierend auf [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Definiert als typedef basierend auf [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Definiert als typedef basierend auf [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Der Typ, der von [CUrl](../../atl/reference/curl-class.md) zum Angeben einer Portnummer verwendet wird.|
|[CComDispatchDriver](#ccomdispatchdriver)|Diese Klasse verwaltet COM-Schnittstellenzeiger.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Ruft die entsprechenden Threadmodellmethoden auf, unabhängig vom verwendeten Threadingmodell.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Ruft die entsprechenden Threadmodellmethoden auf, unabhängig vom verwendeten Threadingmodell.|
|[Ccontainedwindow](#ccontainedwindow)|Diese Klasse ist eine `CContainedWindowT`Spezialisierung von .|
|[CPath](#cpath)|Eine Spezialisierung von [CPathT](../../atl/reference/cpatht-class.md) mit `CString`.|
|[CPathA](#cpatha)|Eine Spezialisierung von [CPathT](../../atl/reference/cpatht-class.md) mit `CStringA`.|
|[CPathW](#cpathw)|Eine Spezialisierung von [CPathT](../../atl/reference/cpatht-class.md) mit `CStringW`.|
|[CSimpleValArray](#csimplevalarray)|Stellt ein Array zum Speichern einfacher Typen dar.|
|[DefaultThreadTraits](#defaultthreadtraits)|Die Standardmäßige Threadeigenschaftenklasse.|
|[LPCURL](#lpcurl)|Ein Zeiger auf ein konstantes [CUrl-Objekt.](../../atl/reference/curl-class.md)|
|[LPURL](#lpurl)|Ein Zeiger auf ein [CUrl-Objekt.](../../atl/reference/curl-class.md)|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

Definiert als typedef basierend auf _ATL_BASE_MODULE70.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Bemerkungen

Wird in jedem ATL-Projekt verwendet. Basierend auf [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Klassen, die Teil der ATL 7.0-Modulklassen sind, leiten sich von der _ATL_BASE_MODULE-Struktur ab.  Weitere Informationen zu ATL-Modulklassen finden Sie unter [COM-Modulklassen](../../atl/com-modules-classes.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcore.h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

Definiert als typedef basierend auf _ATL_COM_MODULE70.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Bemerkungen

Wird von ATL-Projekten verwendet, die COM-Funktionen verwenden. Basierend auf [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

Definiert als typedef basierend auf _ATL_MODULE70.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Anforderungen

**Header:**

### <a name="remarks"></a>Bemerkungen

Basierend auf [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

Definiert als typedef basierend auf _ATL_WIN_MODULE70.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Bemerkungen

Wird von allen ATL-Projekten verwendet, die Fensterfunktionen verwenden. Basierend auf [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

Der Typ, der von [CUrl](curl-class.md) zum Angeben einer Portnummer verwendet wird.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlutil.h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CComDispatchDriver

Diese Klasse verwaltet COM-Schnittstellenzeiger.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

Ruft die entsprechenden Threadmodellmethoden auf, unabhängig vom verwendeten Threadingmodell.

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

### <a name="remarks"></a>Bemerkungen

Je nach Threadingmodell, das von Der `CComGlobalsThreadModel` Anwendung verwendet wird, verweist der **typedef-Name** entweder auf [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oder [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Diese Klassen `typedef` stellen zusätzliche Namen bereit, um auf eine kritische Abschnittsklasse zu verweisen.

> [!NOTE]
> `CComGlobalsThreadModel`verweist nicht auf die Klasse [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Durch `CComGlobalsThreadModel` die Verwendung können Sie keine bestimmte Threadingmodellklasse angeben. Unabhängig vom verwendeten Threadingmodell werden die entsprechenden Methoden aufgerufen.

Zusätzlich zu `CComGlobalsThreadModel`, stellt ATL den **typedef-Namen** [CComObjectThreadModel](#ccomobjectthreadmodel)bereit. Die Klasse, auf `typedef` die von jeder Klasse verwiesen wird, hängt vom verwendeten Threadingmodell ab, wie in der folgenden Tabelle dargestellt:

|Typedef|Einzelnes Gewinden|Apartment-Threading|Kostenloses Einfädeln|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|E|E|M|
|`CComGlobalsThreadModel`|E|M|M|

S= `CComSingleThreadModel`; M=`CComMultiThreadModel`

Wird `CComObjectThreadModel` innerhalb einer einzelnen Objektklasse verwendet. Verwenden `CComGlobalsThreadModel` Sie es in einem Objekt, das für Ihr Programm global verfügbar ist, oder wenn Sie Modulressourcen über mehrere Threads hinweg schützen möchten.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>CComObjectThreadModel

Ruft die entsprechenden Threadmodellmethoden auf, unabhängig vom verwendeten Threadingmodell.

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

### <a name="remarks"></a>Bemerkungen

Je nach Threadingmodell, das von `typedef` `CComObjectThreadModel` Ihrer Anwendung verwendet wird, verweist der Name entweder auf [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oder [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Diese Klassen `typedef` stellen zusätzliche Namen bereit, um auf eine kritische Abschnittsklasse zu verweisen.

> [!NOTE]
> `CComObjectThreadModel`verweist nicht auf die Klasse [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Durch `CComObjectThreadModel` die Verwendung können Sie keine bestimmte Threadingmodellklasse angeben. Unabhängig vom verwendeten Threadingmodell werden die entsprechenden Methoden aufgerufen.

Zusätzlich zu `CComObjectThreadModel`, stellt ATL den **typedef-Namen** [CComGlobalsThreadModel](#ccomglobalsthreadmodel)bereit. Die Klasse, auf die von jedem **typedef** verwiesen wird, hängt vom verwendeten Threadingmodell ab, wie in der folgenden Tabelle dargestellt:

|Typedef|Einzelnes Gewinden|Apartment-Threading|Kostenloses Einfädeln|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|E|E|M|
|`CComGlobalsThreadModel`|E|M|M|

S= `CComSingleThreadModel`; M=`CComMultiThreadModel`

Wird `CComObjectThreadModel` innerhalb einer einzelnen Objektklasse verwendet. Verwenden `CComGlobalsThreadModel` Sie es in einem Objekt, das entweder für Ihr Programm global verfügbar ist oder wenn Sie Modulressourcen über mehrere Threads hinweg schützen möchten.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>Ccontainedwindow

Diese Klasse ist eine `CContainedWindowT`Spezialisierung von .

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

### <a name="remarks"></a>Bemerkungen

`CContainedWindow`ist eine Spezialisierung von [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Wenn Sie die Basisklasse oder -merkmale `CContainedWindowT` ändern möchten, verwenden Sie dies direkt.

## <a name="cpath"></a><a name="cpath"></a>CPath

Eine Spezialisierung von [CPathT](../../atl/reference/cpatht-class.md) mit `CString`.

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlpath.h

## <a name="cpatha"></a><a name="cpatha"></a>CPathA

Eine Spezialisierung von [CPathT](../../atl/reference/cpatht-class.md) mit `CStringA`.

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlpath.h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW

Eine Spezialisierung von [CPathT](../../atl/reference/cpatht-class.md) mit `CStringW`.

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlpath.h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValArray

Stellt ein Array zum Speichern einfacher Typen dar.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Bemerkungen

`CSimpleValArray`wird für das Erstellen und Verwalten von Arrays bereitgestellt, die einfache Datentypen enthalten. Es ist ein einfaches #define von [CSimpleArray](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsimpcoll.h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

Ein Zeiger auf ein konstantes [CUrl-Objekt.](../../atl/reference/curl-class.md)

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlutil.h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>DefaultThreadTraits

Die Standardmäßige Threadeigenschaftenklasse.

### <a name="syntax"></a>Syntax

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Bemerkungen

Wenn das aktuelle Projekt die Multithread-CRT verwendet, wird DefaultThreadTraits als CRTThreadTraits definiert. Andernfalls wird Win32ThreadTraits verwendet.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL

Ein Zeiger auf ein [CUrl-Objekt.](../../atl/reference/curl-class.md)

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlutil.h

## <a name="see-also"></a>Siehe auch

[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)<br/>
[Functions](../../atl/reference/atl-functions.md)<br/>
[Globale Variablen](../../atl/reference/atl-global-variables.md)<br/>
[Klassen und Strukturen](../../atl/reference/atl-classes.md)<br/>
[Makros](../../atl/reference/atl-macros.md)
