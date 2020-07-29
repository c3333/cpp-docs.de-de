---
title: :::no-loc(main):::Funktions-und Befehlszeilenargumente (C++)
description: 'Die- :::no-loc(main)::: Funktion ist der Einstiegspunkt für ein C++-Programm.'
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- ':::no-loc(main):::'
- ':::no-loc(wmain):::'
- ':::no-loc(inline):::'
- ':::no-loc(static):::'
- ':::no-loc(_tmain):::'
- ':::no-loc(void):::'
- ':::no-loc(exit):::'
- ':::no-loc(argc):::'
- ':::no-loc(argv):::'
- ':::no-loc(envp):::'
- ':::no-loc(CreateProcess):::'
- ':::no-loc(GetModuleFileName):::'
- ':::no-loc(char):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(extern):::'
ms.openlocfilehash: 9fe7c7a0808584a70bffa541903866b3de364e5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213319"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>:::no-loc(main):::Funktions-und Befehlszeilenargumente

Alle C++-Programme müssen über eine- `:::no-loc(main):::` Funktion verfügen. Wenn Sie versuchen, ein C++ *. exe* -Projekt ohne eine :::no-loc(main)::: Funktion zu kompilieren, gibt der Compiler einen Fehler aus. (Dynamic-Link-Bibliotheken und- :::no-loc(static)::: Bibliotheken haben keine `:::no-loc(main):::` Funktion.) `:::no-loc(main):::`In der Funktion wird der Quellcode mit der Ausführung begonnen, aber bevor ein Programm `:::no-loc(main):::` in die Funktion eintritt, :::no-loc(static)::: werden alle Klassenmember ohne explizite Initialisierer auf NULL festgelegt. In Microsoft C++ werden globale :::no-loc(static)::: Objekte auch vor dem Eintrag in initialisiert `:::no-loc(main):::` . Einige Einschränkungen gelten für die `:::no-loc(main):::` Funktion, die nicht für andere C++-Funktionen gelten. Die- `:::no-loc(main):::` Funktion:

- Kann nicht überladen werden (siehe [Funktions Überladung](function-overloading.md)).
- Kann nicht als deklariert werden **`:::no-loc(inline):::`** .
- Kann nicht als deklariert werden **`:::no-loc(static):::`** .
- Ihre Adresse kann nicht übernommen werden.
- Kann nicht aufgerufen werden.

Die :::no-loc(main)::: -Funktion verfügt nicht über eine-Deklaration, da Sie in die-Sprache integriert ist. Wenn dies der Fall ist, sieht die Deklarations Syntax für wie folgt aus `:::no-loc(main):::` :

```cpp
int :::no-loc(main):::();
int :::no-loc(main):::(int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[]);
```

**Microsoft-spezifisch**

Wenn in ihren Quelldateien Unicode-weite :::no-loc(char)::: acters verwendet werden, können Sie verwenden `:::no-loc(wmain):::` , wobei es sich um die Wide :::no-loc(char)::: Acter-Version von handelt `:::no-loc(main):::` . Die Deklarationssyntax für `:::no-loc(wmain):::` lautet wie folgt:

```cpp
int :::no-loc(wmain):::( );
int :::no-loc(wmain):::(int :::no-loc(argc):::, :::no-loc(wchar_t)::: *:::no-loc(argv):::[], :::no-loc(wchar_t)::: *:::no-loc(envp):::[]);
```

Sie können auch verwenden `:::no-loc(_tmain):::` , das in t :::no-loc(char)::: . h definiert ist. `:::no-loc(_tmain):::`wird in aufgelöst, `:::no-loc(main):::` es sei denn, _UNICODE definiert ist. In diesem Fall wird `:::no-loc(_tmain):::` in `:::no-loc(wmain):::` aufgelöst.

Wenn kein Rückgabewert angegeben wird, gibt der Compiler einen Rückgabewert von 0 (null) an. Alternativ können die `:::no-loc(main):::` -Funktion und die- `:::no-loc(wmain):::` Funktion als Rückgabe **`:::no-loc(void):::`** (kein Rückgabewert) deklariert werden. Wenn Sie `:::no-loc(main):::` oder `:::no-loc(wmain):::` als zurück **`:::no-loc(void):::`** geben, können Sie keinen :::no-loc(exit)::: Code an den übergeordneten Prozess oder das Betriebssystem zurückgeben, indem Sie eine [Return](../cpp/return-statement-in-program-termination-cpp.md) -Anweisung verwenden. Um einen :::no-loc(exit)::: Code zurückzugeben `:::no-loc(main):::` , wenn oder `:::no-loc(wmain):::` als deklariert wird **`:::no-loc(void):::`** , müssen Sie die- [:::no-loc(exit):::](../cpp/:::no-loc(exit):::-function.md) Funktion verwenden.

**Ende Microsoft-spezifisch**

## <a name="command-line-arguments"></a>Befehlszeilenargumente

Die Argumente für `:::no-loc(main):::` oder `:::no-loc(wmain):::` ermöglichen eine bequeme Befehlszeilen-Analyse von Argumenten und optional Zugriff auf Umgebungsvariablen. Die Typen für `:::no-loc(argc):::` und `:::no-loc(argv):::` werden von der Programmiersprache definiert. Die Namen `:::no-loc(argc):::` , `:::no-loc(argv):::` und `:::no-loc(envp):::` sind traditionell, Sie können Sie jedoch beliebig benennen.

```cpp
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char):::* :::no-loc(argv):::[], :::no-loc(char):::* :::no-loc(envp):::[]);
int :::no-loc(wmain):::( int :::no-loc(argc):::, :::no-loc(wchar_t):::* :::no-loc(argv):::[], :::no-loc(wchar_t):::* :::no-loc(envp):::[]);
```

Die Argumentdefinitionen sind wie folgt:

*:::no-loc(argc):::*<br/>
Eine ganze Zahl, die die Anzahl von Argumenten enthält, die in folgen *:::no-loc(argv):::* . Der- *:::no-loc(argc):::* Parameter ist immer größer als oder gleich 1.

*:::no-loc(argv):::*<br/>
Ein Array von Zeigern auf Zeichenfolgen, die auf NULL enden und von den Benutzern des Programms eingegebene Befehlszeilenargumente darstellen. `:::no-loc(argv):::[0]`Gemäß der Konvention ist der Befehl, mit dem das Programm aufgerufen wird, `:::no-loc(argv):::[1]` das erste Befehlszeilenargument usw., bis `:::no-loc(argv):::[:::no-loc(argc):::]` , das immer NULL ist. Informationen zum Unterdrücken der Befehlszeilen Verarbeitung finden Sie unter [Anpassen der Befehlszeilen Verarbeitung](../cpp/customizing-cpp-command-line-processing.md) .

Das erste Befehlszeilenargument ist immer `:::no-loc(argv):::[1]`, und das letzte ist `:::no-loc(argv):::[:::no-loc(argc)::: - 1]`.

> [!NOTE]
> `:::no-loc(argv):::[0]`Gemäß der Konvention ist der Befehl, mit dem das Programm aufgerufen wird. Es ist jedoch möglich, einen Prozess mit zu erzeugen [:::no-loc(CreateProcess):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) , und wenn Sie sowohl das erste als auch das zweite Argument (*lpApplicationName* und *lpCommandLine*) verwenden, ist möglich `:::no-loc(argv):::[0]` erweise nicht der Name der ausführbaren Datei. verwenden Sie, [:::no-loc(GetModuleFileName):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) um den Namen der ausführbaren Datei und den voll qualifizierten Pfad abzurufen.

**Microsoft-spezifisch**

*:::no-loc(envp):::*<br/>
Das *:::no-loc(envp):::* Array, das eine gemeinsame Erweiterung in vielen UNIX-Systemen ist, wird in Microsoft C++ verwendet. Es ist ein Zeichenfolgenarray, das die Variablen darstellt, die in der Benutzerumgebung festgelegt werden. Das Array wird mit einem NULL-Eintrag beendet. Sie kann als ein Array von Zeigern auf **`:::no-loc(char):::`** ( `:::no-loc(char)::: *:::no-loc(envp):::[]` ) oder als Zeiger auf Zeiger auf **`:::no-loc(char):::`** ( `:::no-loc(char)::: **:::no-loc(envp):::` ) deklariert werden. Wenn `:::no-loc(wmain):::` das Programm anstelle von verwendet `:::no-loc(main):::` , verwenden Sie den- **`:::no-loc(wchar_t):::`** Datentyp anstelle von **`:::no-loc(char):::`** . Der an und über gegebene Umgebungsblock `:::no-loc(main):::` `:::no-loc(wmain):::` ist eine "fixierte" Kopie der aktuellen Umgebung. Wenn Sie anschließend die Umgebung über einen `putenv` -oder-Rückruf ändern `_wputenv` , ändert sich die aktuelle Umgebung (wie von `getenv` oder `_wgetenv` und der-oder-Variable zurückgegeben `_environ` `_wenviron` ), aber der Block, auf den verweist, :::no-loc(envp)::: ändert sich nicht. Informationen zum Unterdrücken der Umgebungs Verarbeitung finden Sie unter [Anpassen der Befehlszeilen Verarbeitung](../cpp/customizing-cpp-command-line-processing.md) . Dieses Argument ist in C ANSI-kompatibel, aber nicht in C++.

**Ende Microsoft-spezifisch**

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie die *:::no-loc(argc):::* *:::no-loc(argv):::* Argumente, und für Folgendes verwendet werden *:::no-loc(envp):::* `:::no-loc(main):::` :

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (:::no-loc(argc)::: == 2) && _stricmp( :::no-loc(argv):::[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; :::no-loc(envp):::[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << :::no-loc(envp):::[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>Parsing C++-Befehlszeilenargumente

**Microsoft-spezifisch**

Beim Interpretieren von Argumenten, die in der Befehlszeile des Betriebssystems angegeben werden, verwendet der Microsoft C/C++-Startcode die folgenden Regeln:

- Argumente werden durch einen Leerraum (Leerzeichen oder Tabstopp) abgegrenzt.

- Der :::no-loc(char)::: Caretzeichen (^) wird nicht als Escapezeichen :::no-loc(char)::: oder Trennzeichen erkannt. Der :::no-loc(char)::: Acter wird vom Befehlszeilen Parser im Betriebssystem vollständig verarbeitet, bevor er an das- `:::no-loc(argv):::` Array im Programm übergeben wird.

- Eine Zeichenfolge, die in doppelten Anführungszeichen ("*String*") eingeschlossen ist, wird als einzelnes Argument interpretiert, unabhängig von Leerraum, der in enthalten ist. Eine Zeichenfolge in Anführungszeichen kann in ein Argument eingebettet sein.

- Ein doppeltes Anführungszeichen, dem ein umgekehrter Schrägstrich ( \\ ") vorangestellt ist, wird als literales doppeltes Anführungszeichen :::no-loc(char)::: (") interpretiert.

- Ein umgekehrter Schrägstrich wird als solcher interpretiert, sofern er nicht unmittelbar vor einem Anführungszeichen steht.

- Wenn ein doppeltes Anführungszeichen auf eine gerade Anzahl umgekehrter Schrägstriche folgt, wird für jedes Paar umgekehrter Schrägstriche ein umgekehrter Schrägstrich im `:::no-loc(argv):::`-Array platziert. Das doppelte Anführungszeichen wird als Zeichenfolgentrennzeichen interpretiert.

- Wenn ein doppeltes Anführungszeichen auf eine ungerade Anzahl umgekehrter Schrägstriche folgt, wird für jedes Paar umgekehrter Schrägstriche ein umgekehrter Schrägstrich in das Array eingefügt, `:::no-loc(argv):::` und das doppelte Anführungszeichen wird durch den umgekehrten Schrägstrich "Escapezeichen" :::no-loc(main)::: , wodurch ein literales doppeltes Anführungszeichen (") eingefügt wird `:::no-loc(argv):::` .

### <a name="example"></a>Beispiel

Das folgende Programm zeigt, wie Befehlszeilenargumente übergeben werden:

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::,      // Number of strings in array :::no-loc(argv):::
          :::no-loc(char)::: *:::no-loc(argv):::[],   // Array of command-line argument strings
          :::no-loc(char)::: *:::no-loc(envp):::[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < :::no-loc(argc):::; count++ )
         cout << "  :::no-loc(argv):::[" << count << "]   "
                << :::no-loc(argv):::[count] << "\n";
}
```

Die folgende Tabelle zeigt beispielhafte Eingaben und zu erwartende Ausgaben, wobei die Regeln in der vorangehenden Liste aufgezeigt werden.

### <a name="results-of-parsing-command-lines"></a>Ergebnisse der Befehlszeilen Verarbeitung

|Befehlszeileneingabe|:::no-loc(argv):::[1]|:::no-loc(argv):::[2]|:::no-loc(argv):::€|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**Ende Microsoft-spezifisch**

## <a name="wildcard-expansion"></a>Platzhaltererweiterung

**Microsoft-spezifisch**

Sie können Platzhalter – das Fragezeichen (?) und das Sternchen (*) – verwenden, um Dateinamen- und Pfadargumente in der Befehlszeile anzugeben.

Befehlszeilenargumente werden von einer Routine namens `_set:::no-loc(argv):::` (oder `_wset:::no-loc(argv):::` in der Wide :::no-loc(char)::: Acter-Umgebung) behandelt, die standardmäßig keine Platzhalter in separate Zeichen folgen im `:::no-loc(argv):::` Zeichen folgen Array erweitert. Weitere Informationen zum Aktivieren der Platzhalter Erweiterung finden Sie unter Erweitern von Platzhalter [Argumenten](../c-language/expanding-wildcard-arguments.md).

**Ende Microsoft-spezifisch**

## <a name="customizing-c-command-line-processing"></a>Anpassen der C++-Befehlszeilenverarbeitung

**Microsoft-spezifisch**

Wenn das Programm keine Befehlszeilenargumente akzeptiert, können Sie ein wenig Platz sparen, indem Sie die Verwendung der Bibliotheksroutine unterdrücken, die die Befehlszeilenverarbeitung ausführt. Diese Routine wird aufgerufen `_set:::no-loc(argv):::` und unter Platzhalter [Erweiterung](../cpp/wildcard-expansion.md)beschrieben. Um die Verwendung zu unterdrücken, definieren Sie eine Routine, die in der Datei, die die Funktion enthält, nichts bewirkt `:::no-loc(main):::` , und benennen Sie Sie `_set:::no-loc(argv):::` . Der-Befehl `_set:::no-loc(argv):::` wird dann durch die Definition von erfüllt `_set:::no-loc(argv):::` , und die Bibliotheksversion wird nicht geladen.

Wenn Sie mit dem-Argument nie auf die Umgebungs Tabelle zugreifen `:::no-loc(envp):::` , können Sie eine eigene leere Routine bereitstellen, die anstelle der `_set:::no-loc(envp):::` Umgebungs Verarbeitungsroutine verwendet wird. Ebenso wie bei der- `_set:::no-loc(argv):::` Funktion `_set:::no-loc(envp):::` muss als ** :::no-loc(extern)::: "C"** deklariert werden.

Das Programm kann die-oder- `spawn` `exec` Familie von Routinen in der C-Lauf Zeit Bibliothek aufrufen. Wenn dies der Fall ist, sollten Sie die Umgebungs Verarbeitungsroutine nicht unterdrücken, da diese Routine verwendet wird, um eine Umgebung vom übergeordneten Prozess an den untergeordneten Prozess zu übergeben.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Grundlegende Konzepte](../cpp/basic-concepts-cpp.md)
