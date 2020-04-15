---
title: Implements-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: 223f37d7cabbd0b8cd238582773c05d7b9eaabf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371410"
---
# <a name="implements-structure"></a>Implements-Struktur

Implementiert `QueryInterface` und `GetIid` für die angegebenen Schnittstellen.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>Parameter

*I0*<br/>
Die nullte Schnittstellen-ID. (Erforderlich)

*I1*<br/>
Die erste Schnittstellen-ID. (Optional)

*I2*<br/>
Die zweite Schnittstellen-ID. (Optional)

*I3*<br/>
Die dritte Schnittstellen-ID. (Optional)

*I4*<br/>
Die vierte Schnittstellen-ID. (Optional)

*I5*<br/>
Die fünfte Schnittstellen-ID. (Optional)

*I6*<br/>
Die sechste Schnittstellen-ID. (Optional)

*I7*<br/>
Die siebte Schnittstellen-ID. (Optional)

*I8*<br/>
Die achte Schnittstellen-ID. (Optional)

*I9*<br/>
Die neunte Schnittstellen-ID. (Optional)

*Flaggen*<br/>
Konfigurationsflags für die Klasse. Eine oder mehrere RuntimeClassType-Enumerationen, die in einer [RuntimeClassFlags-Struktur](runtimeclassflags-structure.md) angegeben sind. [RuntimeClassType](runtimeclasstype-enumeration.md)

## <a name="remarks"></a>Bemerkungen

Leitet aus der Liste der angegebenen Schnittstellen ab und `QueryInterface` implementiert `GetIid`Hilfsvorlagen für und .

Jeder *I0-über-I9-Schnittstellenparameter* `IUnknown`muss `IInspectable`entweder von , oder von der [ChainInterfaces-Vorlage](chaininterfaces-structure.md) abstammen. *I9* Der *Parameter flags* bestimmt, `IUnknown` ob `IInspectable`Unterstützung für oder generiert wird.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

| Name        | BESCHREIBUNG                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Ein Synonym für `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Geschützte Methoden

| Name                                              | BESCHREIBUNG                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implementierungen::CanCastTo](#cancastto)               | Ruft einen Zeiger auf die angegebene Schnittstelle ab.                                                                    |
| [Implementierungen::CastToUnknown](#casttounknown)       | Ruft einen Zeiger auf `IUnknown` die zugrunde liegende Schnittstelle ab.                                                        |
| [Implementierungen::FillArrayWithIid](#fillarraywithiid) | Fügt die durch den aktuellen Vorlagenparameter Null in das angegebene Arrayelement angegebene Schnittstellen-ID ein. |

### <a name="protected-constants"></a>Geschützte Konstanten

| Name                              | BESCHREIBUNG                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implementierungen::IidCount](#iidcount) | Enthält die Anzahl der implementierten Schnittstellen-IDs. |

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL

## <a name="implementscancastto"></a><a name="cancastto"></a>Implementierungen::CanCastTo

Ruft einen Zeiger auf die angegebene Schnittstelle ab.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Ein Verweis auf eine Schnittstellen-ID.

*Ppv*<br/>
Wenn erfolgreich, ein Zeiger auf die Schnittstelle von *riid*angegeben .

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls ein HRESULT, das den Fehler angibt, z. B. E_NOINTERFACE.

### <a name="remarks"></a>Bemerkungen

Dies ist eine interne Hilfsfunktion, die einen QueryInterface-Vorgang ausführt.

## <a name="implementscasttounknown"></a><a name="casttounknown"></a>Implementierungen::CastToUnknown

Ruft einen Zeiger auf `IUnknown` die zugrunde liegende Schnittstelle ab.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Rückgabewert

Dieser Vorgang ist immer `IUnknown` erfolgreich und gibt den Zeiger zurück.

### <a name="remarks"></a>Bemerkungen

Interne Hilfsfunktion.

## <a name="implementsfillarraywithiid"></a><a name="fillarraywithiid"></a>Implementierungen::FillArrayWithIid

Fügt die durch den aktuellen Vorlagenparameter Null in das angegebene Arrayelement angegebene Schnittstellen-ID ein.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Ein nullbasierter Index, der das Startarrayelement für diesen Vorgang angibt. Wenn dieser Vorgang abgeschlossen ist, wird der *Index* um 1 erhöht.

*iids*<br/>
Ein Array vom Typ IID.

### <a name="remarks"></a>Bemerkungen

Interne Hilfsfunktion.

## <a name="implementsiidcount"></a><a name="iidcount"></a>Implementierungen::IidCount

Enthält die Anzahl der implementierten Schnittstellen-IDs.

```cpp
static const unsigned long IidCount;
```
