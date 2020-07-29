---
title: Verwenden von TCHAR.H-Datentypen in _MBCS-Code
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: dd43c29d77c3351e8f597b474c4756ad3d45ef2b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215360"
---
# <a name="using-tcharh-data-types-with-_mbcs-code"></a>Verwenden von TCHAR.H-Datentypen in _MBCS-Code

Wenn die Manifest `_MBCS` -Konstante definiert ist, wird eine gegebene generische Text Routine einer der folgenden Arten von Routinen zugeordnet:

- Eine SBCS-Routine, die ordnungsgemäß Multibytes, Zeichen und Zeichenfolgen verarbeitet. In diesem Fall wird erwartet, dass die Zeichen folgen Argumente vom Typ sind **`char*`** . Beispielsweise wird `_tprintf` zugeordnet `printf` . die Zeichen folgen Argumente für `printf` sind vom Typ **`char*`** . Wenn Sie den `_TCHAR` generischen Text Datentyp für Ihre Zeichen folgen Typen verwenden, stimmen die formalen und tatsächlichen Parametertypen für die Suche `printf` auf, da `_TCHAR*` zugeordnet wird **`char*`** .

- Eine MBCS-spezifische Routine. In diesem Fall werden Zeichenfolgenargumente vom Typ `unsigned char*` erwartet. Beispielsweise wird `_tcsrev``_mbsrev` zugeordnet, wobei eine Zeichenfolge vom Typ `unsigned char*` erwartet und zurückgegeben wird. Wenn Sie den `_TCHAR` generischen Text Datentyp für Ihre Zeichen folgen Typen verwenden, gibt es einen potenziellen Typkonflikt, da dem `_TCHAR` Typ zugeordnet ist **`char`** .

Im Folgenden werden drei Lösungen vorgestellt, um einen solchen Typenkonflikt (und die daraus resultierenden C-Compilerwarnungen oder C++-Compilerfehler) zu verhindern:

- Verwendet das Standardverhalten. Tchar. h stellt generische Text Routine Prototypen für Routinen in den Laufzeitbibliotheken bereit, wie im folgenden Beispiel gezeigt.

    ```cpp
    char * _tcsrev(char *);
    ```

   Im Standardfall wird der Prototyp für `_tcsrev` `_mbsrev` durch einen Thunk in libc. lib zugeordnet. Dadurch werden die Typen der `_mbsrev` eingehenden Parameter und der ausgehende Rückgabewert von `_TCHAR*` (d `char *` . h.) in geändert `unsigned char *` . Diese Methode stellt Typübereinstimmungen bei der Verwendung von sicher `_TCHAR` , ist aufgrund des Funktions aufrufaufwands jedoch relativ langsam.

- Verwenden Sie Inlinefunktionen, indem Sie die folgende Präprozessoranweisung in Ihren Code integrieren.

    ```cpp
    #define _USE_INLINING
    ```

   Diese Methode bewirkt, dass ein Inline Funktions Thunk, der in Tchar. h bereitgestellt wird, die generische Text Routine direkt der entsprechenden MBCS-Routine zuordnet. Der folgende Code Ausschnitt aus TCHAR. h enthält ein Beispiel dafür, wie dies geschieht.

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   Wenn Sie Inlining verwenden können, ist dies die beste Lösung, da es Typübereinstimmung sicherstellt und keinen zusätzlichen Zeit- oder Kostenaufwand mit sich bringt.

- Verwenden Sie die direkte Zuordnung, indem Sie die folgende Präprozessoranweisung in Ihren Code integrieren.

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   Dieser Ansatz bietet eine schnelle Alternative, wenn Sie das Standardverhalten nicht verwenden möchten oder kein Inlining verwenden können. Dies bewirkt, dass die generische Text Routine von einem Makro direkt der MBCS-Version der Routine zugeordnet wird, wie im folgenden Beispiel von Tchar. h.

    ```cpp
    #define _tcschr _mbschr
    ```

   Wenn Sie diesen Ansatz verwenden, müssen Sie darauf achten, die Verwendung geeigneter Datentypen für Zeichen folgen Argumente und Zeichen folgen Rückgabewerte sicherzustellen. Um eine ordnungsgemäße Typübereinstimmung sicherzustellen, können Sie die Typumwandlung oder generischen Text vom Datentyp `_TXCHAR` verwenden. `_TXCHAR`wird dem Typ **`char`** in SBCS-Code zugeordnet, ist aber dem Typ **`unsigned char`** im MBCS-Code zugeordnet. Weitere Informationen zu generischen Text Makros finden Sie unter [generische Text](../c-runtime-library/generic-text-mappings.md) Zuordnungen in der *Lauf Zeit Bibliotheks Referenz*.

## <a name="see-also"></a>Weitere Informationen

[Zuordnungen für generischen Text in Tchar. h](../text/generic-text-mappings-in-tchar-h.md)
