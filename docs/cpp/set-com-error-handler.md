---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: debad733f351c710ada342e29fa95a4d1ff03b7d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749805"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

Ersetzt die Standardfunktion für die COM-Fehlerbehandlung. **_set_com_error_handler** ist Microsoft-spezifisch.

## <a name="syntax"></a>Syntax

```cpp
void __stdcall _set_com_error_handler(
   void (__stdcall *pHandler)(
      HRESULT hr,
      IErrorInfo* perrinfo
   )
);
```

#### <a name="parameters"></a>Parameter

*pHandler*<br/>
Zeiger auf die Ersetzungsfunktion.

*Hr*<br/>
HRESULT-Informationen.

*perrinfo*<br/>
`IErrorInfo`-Objekt

## <a name="remarks"></a>Bemerkungen

Standardmäßig [verarbeitet _com_raise_error](../cpp/com-raise-error.md) alle COM-Fehler. Sie können dieses Verhalten ändern, indem Sie **_set_com_error_handler** verwenden, um Ihre eigene Fehlerbehandlungsfunktion aufzurufen.

Die Ersetzungsfunktion muss über eine Signatur verfügen, die der von `_com_raise_error` entspricht.

## <a name="example"></a>Beispiel

```cpp
// _set_com_error_handler.cpp
// compile with /EHsc
#include <stdio.h>
#include <comdef.h>
#include <comutil.h>

// Importing ado dll to attempt to establish an ado connection.
// Not related to _set_com_error_handler
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")

void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)
{
   throw "Unable to establish the connection!";
}

int main()
{
   _set_com_error_handler(_My_com_raise_error);
   _bstr_t bstrEmpty(L"");
   _ConnectionPtr Connection = NULL;
   try
   {
      Connection.CreateInstance(__uuidof(Connection));
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);
   }
   catch(char* errorMessage)
   {
      printf("Exception raised: %s\n", errorMessage);
   }

   return 0;
}
```

```Output
Exception raised: Unable to establish the connection!
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** \<comdef.h>

**Lib:** Wenn die Compileroption **/Zc:wchar_t** angegeben ist (Standardeinstellung), verwenden Sie comsuppw.lib oder comsuppwd.lib. Wenn die Compileroption **/Zc:wchar_t-** angegeben ist, verwenden Sie comsupp.lib. Weitere Informationen, einschließlich zum Festlegen dieser Option in der IDE, finden Sie unter [/Zc:wchar_t (wchar_t ist Systemeigener Typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Weitere Informationen

[Globale COM-Funktionen des Compilers](../cpp/compiler-com-global-functions.md)
