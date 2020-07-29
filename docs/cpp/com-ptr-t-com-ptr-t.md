---
title: _com_ptr_t::_com_ptr_t
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::_com_ptr_t
helpviewer_keywords:
- _com_ptr_t method [C++]
ms.assetid: 0c00620a-28d2-4f60-ae4a-1696be36137e
ms.openlocfilehash: e8d3d09bf385cb9fdaa02d460952fadbf83bc193
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233794"
---
# <a name="_com_ptr_t_com_ptr_t"></a>_com_ptr_t::_com_ptr_t

**Microsoft-spezifisch**

Erstellt ein **_com_ptr_t** -Objekt.

## <a name="syntax"></a>Syntax

```cpp
// Default constructor.
// Constructs a NULL smart pointer.
_com_ptr_t() throw();

// Constructs a NULL smart pointer. The NULL argument must be zero.
_com_ptr_t(
   int null
);

// Constructs a smart pointer as a copy of another instance of the
// same smart pointer. AddRef is called to increment the reference
// count for the encapsulated interface pointer.
_com_ptr_t(
   const _com_ptr_t& cp
) throw();

// Move constructor (Visual Studio 2015 Update 3 and later)
_com_ptr_t(_com_ptr_t&& cp) throw();

// Constructs a smart pointer from a raw interface pointer of this
// smart pointer's type. If fAddRef is true, AddRef is called
// to increment the reference count for the encapsulated
// interface pointer. If fAddRef is false, this constructor
// takes ownership of the raw interface pointer without calling AddRef.
_com_ptr_t(
   Interface* pInterface,
   bool fAddRef
) throw();

// Construct pointer for a _variant_t object.
// Constructs a smart pointer from a _variant_t object. The
// encapsulated VARIANT must be of type VT_DISPATCH or VT_UNKNOWN, or
// it can be converted into one of these two types. If QueryInterface
// fails with an E_NOINTERFACE error, a NULL smart pointer is
// constructed.
_com_ptr_t(
   const _variant_t& varSrc
);

// Constructs a smart pointer given the CLSID of a coclass. This
// function calls CoCreateInstance, by the member function
//  CreateInstance, to create a new COM object and then queries for
// this smart pointer's interface type. If QueryInterface fails with
// an E_NOINTERFACE error, a NULL smart pointer is constructed.
explicit _com_ptr_t(
   const CLSID& clsid,
   IUnknown* pOuter = NULL,
   DWORD dwClsContext = CLSCTX_ALL
);

// Calls CoCreateClass with provided CLSID retrieved from string.
explicit _com_ptr_t(
   LPCWSTR str,
   IUnknown* pOuter = NULL,
   DWORD dwClsContext = CLSCTX_ALL
);

// Constructs a smart pointer given a multibyte character string that
// holds either a CLSID (starting with "{") or a ProgID. This function
// calls CoCreateInstance, by the member function CreateInstance, to
// create a new COM object and then queries for this smart pointer's
// interface type. If QueryInterface fails with an E_NOINTERFACE error,
// a NULL smart pointer is constructed.
explicit _com_ptr_t(
   LPCSTR str,
   IUnknown* pOuter = NULL,
   DWORD dwClsContext = CLSCTX_ALL
);

// Saves the interface.
template<>
_com_ptr_t(
   Interface* pInterface
) throw();

// Make sure correct ctor is called
template<>
_com_ptr_t(
   LPSTR str
);

// Make sure correct ctor is called
template<>
_com_ptr_t(
   LPWSTR str
);

// Constructs a smart pointer from a different smart pointer type or
// from a different raw interface pointer. QueryInterface is called to
// find an interface pointer of this smart pointer's type. If
// QueryInterface fails with an E_NOINTERFACE error, a NULL smart
// pointer is constructed.
template<typename _OtherIID>
_com_ptr_t(
   const _com_ptr_t<_OtherIID>& p
);

// Constructs a smart-pointer from any IUnknown-based interface pointer.
template<typename _InterfaceType>
_com_ptr_t(
   _InterfaceType* p
);

// Disable conversion using _com_ptr_t* specialization of
// template<typename _InterfaceType> _com_ptr_t(_InterfaceType* p)
template<>
explicit _com_ptr_t(
   _com_ptr_t* p
);
```

### <a name="parameters"></a>Parameter

*pinterface*<br/>
Ein unformatierter Schnittstellenzeiger.

*abadressf*<br/>
Wenn **`true`** , `AddRef` wird aufgerufen, um den Verweis Zähler für den gekapselten Schnittstellen Zeiger zu erhöhen.

*erfolgen*<br/>
Ein **_com_ptr_t** -Objekt.

*cker*<br/>
Ein unformatierter Schnittstellen Zeiger, dessen Typ sich vom Typ des intelligenten Zeigers dieses **_com_ptr_t** Objekts unterscheidet.

*varSrc*<br/>
Ein `_variant_t`-Objekt.

*CLSID*<br/>
Der `CLSID` einer Co-Klasse.

*dwClsContext*<br/>
Kontext für die Ausführung von ausführbarem Code.

*lpcStr*<br/>
Eine Multibytezeichenfolge, die entweder eine `CLSID` (beginnend mit "**{**") oder enthält `ProgID` .

*pouter*<br/>
Das äußere unbekannte für die [Aggregation](/windows/win32/com/aggregation).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
