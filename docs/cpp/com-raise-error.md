---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: f5efbe98a489a380c4e9be5a0e40603be2a409c0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745080"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Microsoft Specific**

Wirft als Reaktion auf einen Fehler einen [_com_error](../cpp/com-error-class.md) aus.

## <a name="syntax"></a>Syntax

```cpp
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Parameter

*Hr*<br/>
HRESULT-Informationen.

*perrinfo*<br/>
`IErrorInfo`-Objekt

## <a name="remarks"></a>Bemerkungen

**_com_raise_error**, die \<in comdef.h> definiert ist, kann durch eine vom Benutzer geschriebene Version mit demselben Namen und Prototyp ersetzt werden. Dies kann ausgeführt werden, wenn Sie `#import` verwenden möchten, jedoch nicht die C++-Ausnahmebehandlung. In diesem Fall kann **_com_raise_error** eine Benutzerversion von `longjmp` _com_raise_error entscheiden, ein Meldungsfeld zu tun oder anzuzeigen und anzuhalten. Die Benutzerversion sollte nicht zurückkehren. Denn die COM-Unterstützung des Compiler-Codes erwartet keine Rückkehr.

Sie können auch [_set_com_error_handler](../cpp/set-com-error-handler.md) verwenden, um die Standardfunktion für die Fehlerbehandlung zu ersetzen.

Standardmäßig ist **_com_raise_error** wie folgt definiert:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**END Microsoft Spezifisch**

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** \<comdef.h>

**Lib:** Wenn die **wchar_t Native Type-Compileroption** aktiviert ist, verwenden Sie comsuppw.lib oder comsuppwd.lib. Wenn wchar_t Native Type deaktiviert **ist,** verwenden Sie comsupp.lib. Weitere Informationen finden Sie unter[/Zc:wchar_t (wchar_t ist der systemeigene Typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Weitere Informationen

[Globale COM-Funktionen des Compilers](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
