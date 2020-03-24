---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 2ec4e90c8f0c1009cc47e9022a09b3b8f7dbb284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190000"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Microsoft-spezifisch**

Erstellt eine neue Instanz eines-Objekts, wenn ein `CLSID` oder `ProgID`angegeben wird.

## <a name="syntax"></a>Syntax

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>Parameter

*rclsid*<br/>
Die `CLSID` eines-Objekts.

*clsidstring*<br/>
Eine Unicode-Zeichenfolge, die entweder eine `CLSID` (beginnend mit " **{** ") oder eine `ProgID`enthält.

*clsidstrauinga*<br/>
Eine Multibytezeichenfolge, die die ANSI-Codepage verwendet, die entweder eine `CLSID` (beginnend mit " **{** ") oder eine `ProgID`enthält.

*dwClsContext*<br/>
Kontext für die Ausführung von ausführbarem Code.

*pouter*<br/>
Das äußere unbekannte für die [Aggregation](../atl/aggregation.md).

## <a name="remarks"></a>Bemerkungen

Diese Memberfunktionen rufen `CoCreateInstance` auf, um ein neues COM-Objekt zu erstellen, und fragen dann den Schnittstellentyp dieses intelligenten Zeigers ab. Das Zeigerergebnis wird dann innerhalb dieses `_com_ptr_t`-Objekts gekapselt. `Release` wird aufgerufen, um den Verweis Zähler für den zuvor gekapselten Zeiger zu verringern. Diese Routine gibt das HRESULT zurück, um einen Erfolg oder Fehler anzugeben.

- " **Kreatumstance" (** *rclsid* **,** *dwClsContext* **)** Erstellt eine neue Instanz eines-Objekts, wenn ein `CLSID`angegeben wird.

- " **Kreatumstance" (** *clsidstring* **,** *dwClsContext* **)** Erstellt eine neue Instanz eines-Objekts mit einer angegebenen Unicode-Zeichenfolge, die entweder eine `CLSID` (beginnend mit " **{** ") oder eine `ProgID`enthält.

- " **Kreatanstance" (** *clsidstrauinga* **,** *dwClsContext* **)** Erstellt eine neue Instanz eines-Objekts, wenn eine Multibytezeichenfolge angegeben wird, die entweder eine `CLSID` (beginnend mit " **{** ") oder eine `ProgID`enthält. Ruft [multibytedewidechar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)auf, bei dem davon ausgegangen wird, dass die Zeichenfolge in der ANSI-Codepage statt in einer OEM-Codepage ist.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
