---
title: Ergebnisse des Aufrufbeispiels
ms.date: 11/19/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: 1bf5fe62b8ef2b7a37bf72b7a40e5d47af3f3961
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225877"
---
# <a name="results-of-calling-example"></a>Ergebnisse des Aufrufbeispiels

**Microsoft-spezifisch**

## <a name="__cdecl"></a>__cdecl

Der Name der C-ergänzten Funktion ist `_MyFunc` .

![Cdecl-Aufruf Konvention](../cpp/media/vc37i01.gif "CDECL-Aufrufkonvention") <br/>
Die **`__cdecl`** Aufruf Konvention

## <a name="__stdcall-and-thiscall"></a>thiscall und __stdcall

Der ergänzte C-Name ( **`__stdcall`** ) ist `_MyFunc@20` . Der C++ ergänzte Name ist Implementierungs spezifisch.

![&#95;&#95;stdcall-und thiscall-Aufruf Konventionen](../cpp/media/vc37i02.gif "&#95;&#95;stdcall-und thiscall-Aufruf Konventionen") <br/>
__stdcall- und thiscall-Aufrufkonventionen

## <a name="__fastcall"></a>__fastcall

Der ergänzte C-Name ( **`__fastcall`** ) ist `@MyFunc@20` . Der C++ ergänzte Name ist Implementierungs spezifisch.

![Aufruf Konvention für &#95;&#95;fastcall](../cpp/media/vc37i03.gif "Aufruf Konvention für &#95;&#95;fastcall") <br/>
__fastcall-Aufrufkonvention

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Aufruf Beispiel: Funktionsprototyp und Aufruf](../cpp/calling-example-function-prototype-and-call.md)
