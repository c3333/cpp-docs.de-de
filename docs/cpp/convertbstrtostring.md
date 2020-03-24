---
title: ConvertBSTRToString
ms.date: 11/04/2016
f1_keywords:
- ConvertBSTRToString
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
ms.openlocfilehash: 1d0ad8727dd4d5ec06a45ec26c67dd3ad268f524
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189521"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString

**Microsoft-spezifisch**

Konvertiert einen `BSTR`-Wert in einen `char *`.

## <a name="syntax"></a>Syntax

```
char* __stdcall ConvertBSTRToString(BSTR pSrc);
```

#### <a name="parameters"></a>Parameter

*pSrc*<br/>
Eine BSTR-Variable.

## <a name="remarks"></a>Bemerkungen

**Convertbstrauto-String** ordnet eine Zeichenfolge zu, die Sie löschen müssen.

## <a name="example"></a>Beispiel

```cpp
// ConvertBSTRToString.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")

int main() {
   BSTR bstrText = ::SysAllocString(L"Test");
   wprintf_s(L"BSTR text: %s\n", bstrText);

   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);
   printf_s("char * text: %s\n", lpszText2);

   SysFreeString(bstrText);
   delete[] lpszText2;
}
```

```Output
BSTR text: Test
char * text: Test
```

**Ende Microsoft-spezifisch**

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<comutil. h >

**Lib:** comsuppw. lib oder comsuppwd. lib (siehe [/Zc: wchar_t (wchar_t ist System eigener Typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , um weitere Informationen zu erhalten)

## <a name="see-also"></a>Weitere Informationen

[Globale COM-Funktionen des Compilers](../cpp/compiler-com-global-functions.md)
