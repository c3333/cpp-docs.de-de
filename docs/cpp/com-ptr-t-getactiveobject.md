---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: ea8059a039b77811dd54d4a4937ad746b7ca0937
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170800"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft-spezifisch**

Hängt an eine vorhandene Instanz eines-Objekts an, wenn ein `CLSID` oder `ProgID`angegeben wird.

## <a name="syntax"></a>Syntax

```
HRESULT GetActiveObject(
   const CLSID& rclsid
) throw( );
HRESULT GetActiveObject(
   LPCWSTR clsidString
) throw( );
HRESULT GetActiveObject(
   LPCSTR clsidStringA
) throw( );
```

#### <a name="parameters"></a>Parameter

*rclsid*<br/>
Die `CLSID` eines-Objekts.

*clsidstring*<br/>
Eine Unicode-Zeichenfolge, die entweder eine `CLSID` (beginnend mit " **{** ") oder eine `ProgID`enthält.

*clsidstrauinga*<br/>
Eine Multibytezeichenfolge, die die ANSI-Codepage verwendet, die entweder eine `CLSID` (beginnend mit " **{** ") oder eine `ProgID`enthält.

## <a name="remarks"></a>Bemerkungen

Diese Member-Funktionen rufen **GetActiveObject** auf, um einen Zeiger auf ein aktuell registriertes Objekt abzurufen, das bei OLE registriert wurde, und dann Abfragen für den Schnittstellentyp dieses intelligenten Zeigers. Das Zeigerergebnis wird dann innerhalb dieses `_com_ptr_t`-Objekts gekapselt. `Release` wird aufgerufen, um den Verweis Zähler für den zuvor gekapselten Zeiger zu verringern. Diese Routine gibt das HRESULT zurück, um einen Erfolg oder Fehler anzugeben.

- **GetActiveObject (** `rclsid` **)** Wird an eine vorhandene Instanz eines-Objekts angefügt, wenn ein `CLSID`angegeben wird.

- **GetActiveObject (** `clsidString` **)** Hängt an eine vorhandene Instanz eines Objekts an, wenn eine Unicode-Zeichenfolge vorhanden ist, die entweder eine `CLSID` (beginnend mit " **{** ") oder eine `ProgID`enthält.

- **GetActiveObject (** `clsidStringA` **)** Hängt an eine vorhandene Instanz eines Objekts an, wenn eine Multibytezeichenfolge vorhanden ist, die entweder eine `CLSID` (beginnend mit " **{** ") oder eine `ProgID`enthält. Ruft [multibytedewidechar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)auf, bei dem davon ausgegangen wird, dass die Zeichenfolge in der ANSI-Codepage statt in einer OEM-Codepage ist.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
