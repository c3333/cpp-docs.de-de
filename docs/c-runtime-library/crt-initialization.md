---
title: CRT-Initialisierung
description: Beschreibt, wie die CRT den globalen Zustand in nativem Code initialisiert.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
ms.openlocfilehash: 25f1e2a7e5b7d91c729bb45bd79ba9a8720cead1
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589769"
---
# <a name="crt-initialization"></a>CRT-Initialisierung

In diesem Thema wird beschrieben, wie die CRT den globalen Zustand in nativem Code initialisiert.

Standardmäßig enthält der Linker die CRT-Bibliothek, die einen eigenen Startcode bereitstellt. Dieser Startcode initialisiert die CRT-Bibliothek, ruft globale Initialisierer auf und ruft dann die vom Benutzer bereitgestellte `main`-Funktion für Konsolenanwendungen auf.

## <a name="initializing-a-global-object"></a>Initialisieren eines globalen Objekts

Betrachten Sie folgenden Code:

```
int func(void)
{
    return 3;
}

int gi = func();

int main()
{
    return gi;
}
```

Laut dem C/C++-Standard muss `func()` aufgerufen werden, bevor `main()` ausgeführt wird. Doch wer ruft diese Funktion auf?

Eine Möglichkeit zum Ermitteln des Aufrufers besteht darin, einen Haltepunkt in festzulegen `func()` , die Anwendung zu Debuggen und den Stapel zu untersuchen. Dies ist möglich, da der CRT-Quellcode in Visual Studio enthalten ist.

Wenn Sie die Funktionen im Stapel durchsuchen, sehen Sie, dass die CRT eine Liste von Funktions Zeigern aufruft. Diese Funktionen ähneln `func()` , oder Konstruktoren für Klassen Instanzen.

Die CRT Ruft die Liste der Funktionszeiger vom Microsoft C++-Compiler ab. Wenn der Compiler einen globalen Initialisierer sieht, generiert er einen dynamischen Initialisierer im `.CRT$XCU` Abschnitt, wobei `CRT` der Abschnitts Name und `XCU` der Gruppenname ist. Um eine Liste dynamischer Initialisierer zu erhalten, führen Sie den Befehl **(dumpbin/all Main. obj**aus, und Durchsuchen Sie dann den `.CRT$XCU` Abschnitt. Dies trifft zu, wenn Main. cpp als C++-Datei kompiliert wird, nicht als C-Datei. Dies sieht in etwa wie im folgenden Beispiel aus:

```
SECTION HEADER #6
.CRT$XCU name
       0 physical address
       0 virtual address
       4 size of raw data
     1F2 file pointer to raw data (000001F2 to 000001F5)
     1F6 file pointer to relocation table
       0 file pointer to line numbers
       1 number of relocations
       0 number of line numbers
40300040 flags
         Initialized Data
         4 byte align
         Read Only

RAW DATA #6
  00000000: 00 00 00 00                                      ....

RELOCATIONS #6
                                               Symbol    Symbol
Offset    Type              Applied To         Index     Name
--------  ----------------  -----------------  --------  -------
00000000  DIR32             00000000           C         ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

CRT definiert zwei Zeiger:

- `__xc_a` in `.CRT$XCA`

- `__xc_z` in `.CRT$XCZ`

Keine der Gruppen hat andere Symbole definiert, außer `__xc_a` und `__xc_z` .

Wenn der Linker verschiedene `.CRT`-Gruppen liest, fasst er sie in einem Bereich zusammen und sortiert sie in alphabetischer Reihenfolge. Dies bedeutet, dass die benutzerdefinierten globalen Initialisierer (die der Microsoft Visual C++-Compiler in `.CRT$XCU` einfügt) immer nach `.CRT$XCA` und vor `.CRT$XCZ` kommen.

Der Abschnitt ähnelt dem folgenden Beispiel:

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

Daher verwendet die CRT-Bibliothek sowohl `__xc_a` als auch `__xc_z` , um den Anfang und das Ende der Liste der globalen Initialisierer zu ermitteln, da Sie nach dem Laden des Bilds im Arbeitsspeicher angeordnet werden.

## <a name="see-also"></a>Weitere Informationen

[Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md)
