---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: 2012ec98d8d40d60a7f12feb68bdc371e1616223
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189792"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Microsoft-spezifisch**

Löst eine [_com_error](../cpp/com-error-class.md) als Reaktion auf einen Fehler aus.

## <a name="syntax"></a>Syntax

```
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Parameter

*HR*<br/>
HRESULT-Informationen.

*perrinfo*<br/>
`IErrorInfo`-Objekt

## <a name="remarks"></a>Bemerkungen

**_com_raise_error**, die in \<comdef. h-> definiert ist, kann durch eine benutzerdefinierte Version desselben Namens und Prototyps ersetzt werden. Dies kann ausgeführt werden, wenn Sie `#import` verwenden möchten, jedoch nicht die C++-Ausnahmebehandlung. In diesem Fall könnte eine Benutzerversion von **_com_raise_error** eine `longjmp` ausführen oder ein Meldungs Feld anzeigen und anhalten. Die Benutzerversion sollte nicht zurückkehren. Denn die COM-Unterstützung des Compiler-Codes erwartet keine Rückkehr.

Sie können auch [_set_com_error_handler](../cpp/set-com-error-handler.md) verwenden, um die standardmäßige Fehler Behandlungs Funktion zu ersetzen.

Standardmäßig ist **_com_raise_error** wie folgt definiert:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**Ende Microsoft-spezifisch**

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<comdef. h >

**Lib:** Wenn die Compileroption für den wchar_t System eigen **ist** , verwenden Sie "comsuppw. lib" oder "comsuppwd. lib". Wenn **wchar_t den Typ** "Off" hat, verwenden Sie "comsupp. lib". Weitere Informationen finden Sie unter[/Zc:wchar_t (wchar_t ist der systemeigene Typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Weitere Informationen

[Globale COM-Funktionen des Compilers](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
