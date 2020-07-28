---
title: Verwenden von TCHAR.H-Datentypen mit _MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
ms.openlocfilehash: d1aab0c21a348e4b1a6e85a7adb7f7f8ea1587b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188634"
---
# <a name="using-tcharh-data-types-with-_mbcs"></a>Verwenden von TCHAR.H-Datentypen mit _MBCS

**Microsoft-spezifisch**

Wie aus die Tabelle mit den Zuordnungen für generische Textroutinen hervorgeht (siehe [Zuordnungen für generischen Text](../c-runtime-library/generic-text-mappings.md)), wird eine bestimmte generische Textroutine einer der folgenden Arten von Routinen zugeordnet, wenn die Manifestkonstante **_MBCS** definiert ist:

- Eine SBCS-Routine, die ordnungsgemäß Multibytes, Zeichen und Zeichenfolgen verarbeitet. In diesem Fall werden Zeichenfolgenargumente vom Typ **char&#42;** erwartet. Zum Beispiel wird **_tprintf** zu **printf** zugeordnet. Die Zeichenfolgenargumente für **printf** sind vom Typ **char&#42;**. Wenn Sie generischen Text vom Datentyp **_TCHAR** für Ihre Zeichenfolgentypen verwenden, stimmen die formalen und tatsächlichen Parametertypen für **printf** überein, da **_TCHAR&#42;** zu **char&#42;** zugeordnet wird.

- Eine MBCS-spezifische Routine. In diesem Fall werden Zeichenfolgenargumente vom Typ __unsigned char&#42;__ erwartet. Zum Beispiel wird **_tcsrev** zu **_mbsrev** zugeordnet, was eine Zeichenfolge vom Typ __unsigned char&#42;__ erwartet und zurückgibt. Wenn Sie den **_TCHAR** generischen Text Datentyp für Ihre Zeichen folgen Typen verwenden, gibt es einen potenziellen Typkonflikt, da **_TCHAR** dem-Typ zugeordnet ist **`char`** .

Im Folgenden werden drei Lösungen vorgestellt, um einen solchen Typenkonflikt (und die daraus resultierenden C-Compilerwarnungen oder C++-Compilerfehler) zu verhindern:

- Verwendet das Standardverhalten. TCHAR.H enthält Prototypen von generischen Textroutinen für Routinen in Laufzeitbibliotheken, wie im folgenden Beispiel gezeigt wird.

   ```C
   char *_tcsrev(char *);
   ```

   Im Standardfall wird der Prototyp für **_tcsrev** über einen Thunk in LIBC.LIB **_mbsrev** zugeordnet. Dadurch werden die Typen der eingehenden **_mbsrev**-Parameter und der ausgehende Rückgabewert aus **_TCHAR &#42;** (z.B. **char &#42;**) in **unsigned char &#42;** geändert. Diese Methode stellt Typübereinstimmung bei Verwendung von **T_CHAR** sicher, ist aufgrund des Mehraufwands für den Funktionsaufruf jedoch relativ langsam.

- Verwenden Sie Inlinefunktionen, indem Sie die folgende Präprozessoranweisung in Ihren Code integrieren.

   ```C
   #define _USE_INLINING
   ```

   Diese Methode verursacht einen Inlinefunktionsthunk in TCHAR.H, um die generische Textroutine direkt der entsprechenden MBCS-Routine zuzuordnen. Mit dem folgenden Codeauszug aus TCHAR.H wird ein einfaches Beispiel für diesen Vorgang gezeigt.

   ```C
   __inline char *_tcsrev(char *_s1)
   {return (char *)_mbsrev((unsigned char *)_s1);}
   ```

   Wenn Sie Inlining verwenden können, ist dies die beste Lösung, da es Typübereinstimmung sicherstellt und keinen zusätzlichen Zeit- oder Kostenaufwand mit sich bringt.

- Verwenden Sie die direkte Zuordnung, indem Sie die folgende Präprozessoranweisung in Ihren Code integrieren.

   ```C
   #define _MB_MAP_DIRECT
   ```

   Dieser Ansatz bietet eine schnelle Alternative, wenn Sie das Standardverhalten nicht verwenden möchten oder kein Inlining verwenden können. Es bewirkt, dass die durch ein Makro zuzuordnende generische Textroutine direkt der MBCS-Version der Routine zugeordnet wird, wie im folgenden Beispiel aus TCHAR.H gezeigt wird.

   ```C
   #define _tcschr _mbschr
   ```

Wenn Sie diesen Ansatz verwenden, müssen Sie in jedem Fall sicherstellen, dass die entsprechenden Datentypen für Zeichenfolgenargumente und -rückgabewerte verwendet werden. Zum Sicherstellen einer ordnungsgemäßen Typübereinstimmung können Sie die Typumwandlung oder generischen Text des Datentyps **_TXCHAR** verwenden. **_TXCHAR** wird dem Typ **`char`** in SBCS-Code zugeordnet, ist aber dem Typ **`unsigned char`** im MBCS-Code zugeordnet. Weitere Informationen zu generischen Textmakros finden Sie unter [Zuordnungen für generischen Text](../c-runtime-library/generic-text-mappings.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Internationalisierung](../c-runtime-library/internationalization.md)<br/>
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
