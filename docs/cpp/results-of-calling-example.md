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
ms.openlocfilehash: edbeb187e568b833673d91ef70ff57fbd460659c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179054"
---
# <a name="results-of-calling-example"></a>Ergebnisse des Aufrufbeispiels

**Microsoft-spezifisch**

## <a name="__cdecl"></a>__cdecl

Der Name der C-ergänzten Funktion ist `_MyFunc`.

![Cdecl-Aufruf Konvention](../cpp/media/vc37i01.gif "CDECL-Aufrufkonvention") <br/>
Die **__cdecl** -Aufruf Konvention

## <a name="__stdcall-and-thiscall"></a>thiscall und __stdcall

Der ergänzte C-Name ( **__stdcall**) ist `_MyFunc@20`. Der C++ ergänzte Name ist Implementierungs spezifisch.

![&#95;&#95;Aufruf Konventionen von stdcall und thiscall](../cpp/media/vc37i02.gif "&#95;&#95;Aufruf Konventionen von stdcall und thiscall") <br/>
__stdcall- und thiscall-Aufrufkonventionen

## <a name="__fastcall"></a>__fastcall

Der ergänzte C-Name ( **__fastcall**) ist `@MyFunc@20`. Der C++ ergänzte Name ist Implementierungs spezifisch.

![Aufruf Konvention für &#95; &#95;fastcall](../cpp/media/vc37i03.gif "Aufruf Konvention für &#95; &#95;fastcall") <br/>
__fastcall-Aufrufkonvention

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Aufrufbeispiel:Funktionsprototyp und Aufruf](../cpp/calling-example-function-prototype-and-call.md)
