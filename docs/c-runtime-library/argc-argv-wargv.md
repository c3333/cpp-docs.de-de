---
title: __argc, __argv, __wargv
description: Beschreibt die globalen Konstanten der Microsoft C-Lauf Zeit Bibliothek __argc , __argv und __wargv .
ms.date: 11/04/2016
api_name:
- __wargv
- __argv
- __argc
api_location:
- msvcrt120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __argv
- __argc
- __wargv
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
no-loc:
- __argc
- __argv
- __wargv
- main
- wmain
ms.openlocfilehash: 02c130be0d2dcb8e48d2bb5c75438c94003fc9dd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507591"
---
# <a name="no-loc__argc-no-loc__argv-no-loc__wargv"></a>__argc, __argv, __wargv

Die globale Variable `__argc` zählt die Anzahl von Befehlszeilenargumenten, die an das Programm übergeben werden. `__argv` ist ein Zeiger auf ein Array mit Einzelbytezeichen oder Multibyte-Zeichensätzen, die die Programmargumente enthalten, und `__wargv` ist ein Zeiger auf ein Array mit Breitzeichen-Zeichenfolgen, die die Programmargumente enthalten. Diese globalen Variablen stellen die Argumente für `main` oder `wmain` bereit.

## <a name="syntax"></a>Syntax

```C
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Bemerkungen

In einem Programm, das die Funktion `main` verwendet, werden `__argc` und `__argv` beim Programmstart über die Befehlszeile initialisiert, die zum Starten des Programms verwendet wird. Die Befehlszeile wird in einzelne Argumente analysiert, und Platzhalter werden erweitert. Das Zählen der Argumente wird `__argc` zugewiesen, die Argumentzeichenfolgen werden auf dem Heap zugeordnet, und ein Zeiger zum Array der Argumente wird `__argv` zugewiesen. In einem Programm, das für die Verwendung von Breitzeichen und einer `wmain`-Funktion kompiliert ist, werden die Argumente analysiert und Platzhalter als Breitzeichen-Zeichenfolgen erweitert. Außerdem wird ein Zeiger zum Array der Argumentzeichenfolgen zu `__wargv` zugewiesen.

Für portablen Code wird die Verwendung der an `main` übergebenen Argumente empfohlen, um die Befehlszeilenargumente in Ihrem Programm abzurufen.

### <a name="generic-text-routine-mappings"></a>Zuordnungen von generischen Text Routinen

|Tchar.h-Routine|_UNICODE nicht definiert|_UNICODE definiert|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>Requirements (Anforderungen)

|Globale Variable|Erforderlicher Header|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|

`__argc`, `__argv` und `__wargv` sind Microsoft-Erweiterungen. Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Globale Variablen](../c-runtime-library/global-variables.md)\
[main Funktions-und Befehlszeilenargumente (C++)](../cpp/main-function-command-line-args.md)\
[Verwendung wmain von anstelle von main](../cpp/main-function-command-line-args.md)
