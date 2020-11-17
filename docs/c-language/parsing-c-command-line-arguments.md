---
title: Analysieren von C-Befehlszeilenargumenten
description: Erfahren Sie, wie der Startcode der Microsoft C-Runtime Befehlszeilenargumente interpretiert, um die Parameter „argv“ und „argc“ zu erstellen.
ms.date: 11/09/2020
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- double quote marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
ms.openlocfilehash: 92921e91ee6bb37b2bf7b702a1b31ed045187b59
ms.sourcegitcommit: b38485bb3a9d479e0c5d64ffc3d841fa2c2b366f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441254"
---
# <a name="parsing-c-command-line-arguments"></a>Analysieren von C-Befehlszeilenargumenten

**Microsoft-spezifisch**

Beim Interpretieren von Argumenten, die in der Befehlszeile des Betriebssystems angegeben werden, verwendet der Microsoft C-Startcode die folgenden Regeln:

- Argumente werden durch einen Leerraum (Leerzeichen oder Tabstopp) abgegrenzt.

- Das erste Argument (`argv[0]`) wird besonders behandelt. Es repräsentiert den Programmnamen. Da es sich um einen gültigen Pfadnamen handeln muss, sind Bestandteile in doppelten geraden Anführungszeichen oben ( **`"`** ) zulässig. Die Anführungszeichen sind nicht in der Ausgabe von `argv[0]` enthalten. Die Anführungszeichen verhindern, dass bei den darin eingeschlossenen Bestandteilen Leerzeichen oder Tabstoppzeichen als Ende des Arguments interpretiert werden. Die weiter unten in dieser Liste aufgeführten Regeln gelten nicht.

- Eine in doppelte gerade Anführungszeichen oben eingeschlossene Zeichenfolge wird als einzelnes Argument interpretiert, unabhängig davon, ob darin Leerzeichen enthalten sind. Eine Zeichenfolge in Anführungszeichen kann in ein Argument eingebettet sein. Die Einfügemarke ( **`^`** ) wird nicht als Escape- oder Trennzeichen erkannt. Innerhalb einer in Anführungszeichen eingeschlossenen Zeichenfolge wird ein Paar aus doppelten Anführungszeichen als ein einzelnes doppeltes Anführungszeichen mit Escapezeichen interpretiert. Wenn die Befehlszeile endet, bevor ein schließendes doppeltes Anführungszeichen gefunden wird, werden alle bis dahin gelesenen Zeichen als letztes Argument ausgegeben.

- Wenn dem doppelten Anführungszeichen ein umgekehrter Schrägstrich ( **`\"`** ) vorangestellt ist, wird diese Zeichenfolge als tatsächliches doppeltes Anführungszeichen ( **`"`** ) interpretiert.

- Ein umgekehrter Schrägstrich wird als solcher interpretiert, sofern er nicht unmittelbar vor einem Anführungszeichen steht.

- Wenn ein doppeltes Anführungszeichen auf eine gerade Anzahl umgekehrter Schrägstriche folgt, wird für jedes Paar umgekehrter Schrägstriche ( **`\\`** ) ein umgekehrter Schrägstrich ( **`\`** ) im `argv`-Array platziert. Das doppelte Anführungszeichen ( **`"`** ) wird als Zeichenfolgentrennzeichen interpretiert.

- Wenn ein doppeltes Anführungszeichen auf eine ungerade Anzahl umgekehrter Schrägstriche folgt, wird für jedes Paar umgekehrter Schrägstriche ( **`\\`** ) ein umgekehrter Schrägstrich ( **`\`** ) im `argv`-Array platziert. Das doppelte Anführungszeichen wird durch den verbleibenden umgekehrten Schrägstrich als Escapesequenz interpretiert, sodass ein tatsächliches doppeltes Anführungszeichen ( **`"`** ) in `argv` platziert wird.

Diese Liste veranschaulicht die zuvor genannten Regeln anhand der an `argv` übergebenen interpretierten Ergebnisse für einige beispielhafte Befehlszeilenargumente. Die Ausgabe in der zweiten, dritten und vierten Spalte stammt aus dem ARGS.C-Programm, das auf die Liste folgt.

|Befehlszeileneingabe|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"a b c" d e`|`a b c`|`d`|`e`|
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|
|`a"b"" c d`|`ab" c d`|||

## <a name="example"></a>Beispiel

### <a name="code"></a>Code

```c
// ARGS.C illustrates the following variables used for accessing
// command-line arguments and environment variables:
// argc  argv  envp
//

#include <stdio.h>

int main( int argc, // Number of strings in array argv
char *argv[],      // Array of command-line argument strings
char **envp )      // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    printf_s( "\nCommand-line arguments:\n" );
    for( count = 0; count < argc; count++ )
        printf_s( "  argv[%d]   %s\n", count, argv[count] );

    // Display each environment variable.
    printf_s( "\nEnvironment variables:\n" );
    while( *envp != NULL )
        printf_s( "  %s\n", *(envp++) );

    return;
}
```

## <a name="comments"></a>Kommentare

Ein Beispiel für die Ausgabe dieses Programms ist:

```
Command-line arguments:
  argv[0]   C:\MSC\TEST.EXE

Environment variables:
  COMSPEC=C:\NT\SYSTEM32\CMD.EXE

  PATH=c:\nt;c:\binb;c:\binr;c:\nt\system32;c:\word;c:\help;c:\msc;c:\;
  PROMPT=[$p]
  TEMP=c:\tmp
  TMP=c:\tmp
  EDITORS=c:\binr
  WINDIR=c:\nt
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[main-Funktion und Programmausführung](../c-language/main-function-and-program-execution.md)
