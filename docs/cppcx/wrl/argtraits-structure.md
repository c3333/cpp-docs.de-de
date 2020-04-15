---
title: ArgTraits-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
- event/Microsoft::WRL::Details::ArgTraits::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraits structure
- Microsoft::WRL::Details::ArgTraits::args constant
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
ms.openlocfilehash: 16c44d861ebbbc98fa1bffb62a00d1989c0c803c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377171"
---
# <a name="argtraits-structure"></a>ArgTraits-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template<typename TMemberFunction>
struct ArgTraits;

template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;

template<typename TDelegateInterface, typename TArg1>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;

template<typename TDelegateInterface, typename TArg1, typename TArg2>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>Parameter

*TMemberFunction*<br/>
Typname-Parameter für eine ArgTraits-Struktur, die keiner `Invoke` Methodensignatur entsprechen kann.

*TDelegateInterface*<br/>
Eine Delegatschnittstelle.

*TArg1*<br/>
Der Typ des ersten `Invoke` Arguments der Methode.

*Targ2*<br/>
Der Typ des zweiten `Invoke` Arguments der Methode.

*Targ3*<br/>
Der Typ des dritten `Invoke` Arguments der Methode.

*TArg4*<br/>
Der Typ des vierten `Invoke` Arguments der Methode.

*TArg5*<br/>
Der Typ des fünften `Invoke` Arguments der Methode.

*TArg6*<br/>
Der Typ des sechsten `Invoke` Arguments der Methode.

*Targ7*<br/>
Der Typ des siebten `Invoke` Arguments der Methode.

*TArg8*<br/>
Der Typ des achten `Invoke` Arguments der Methode.

*TArg9*<br/>
Der Typ des neunten `Invoke` Arguments der Methode.

## <a name="remarks"></a>Bemerkungen

Die `ArgTraits` Struktur deklariert eine angegebene Delegatschnittstelle und eine anonyme Memberfunktion mit einer angegebenen Anzahl von Parametern.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name       | BESCHREIBUNG
---------- | ----------------------
`Arg1Type` | Der typedef für TArg1.
`Arg2Type` | Der typedef für TArg2.
`Arg3Type` | Der typedef für TArg3.
`Arg4Type` | Der typedef für TArg4.
`Arg5Type` | Der typedef für TArg5.
`Arg6Type` | Der typedef für TArg6.
`Arg7Type` | Der typedef für TArg7.
`Arg8Type` | Der typedef für TArg8.
`Arg9Type` | Der typedef für TArg9.

### <a name="public-constants"></a>Öffentliche Konstanten

Name                     | BESCHREIBUNG
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits::args](#args) | Zählt die Anzahl der Parameter `Invoke` für die Methode einer Delegatschnittstelle.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ArgTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="argtraitsargs"></a><a name="args"></a>ArgTraits::args

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Bemerkungen

Zählt die Anzahl der Parameter `Invoke` für die Methode einer Delegatschnittstelle. Wenn `args` es sich um -1 handelt, `Invoke` kann keine Übereinstimmung für die Methodensignatur vorhanden sein.
