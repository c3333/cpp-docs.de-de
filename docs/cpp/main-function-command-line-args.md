---
title: main Funktions-und Befehlszeilenargumente (C++)
description: Die- main Funktion ist der Einstiegspunkt für ein C++-Programm.
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- main
- wmain
- inline
- static
- _tmain
- void
- exit
- argc
- argv
- envp
- CreateProcess
- GetModuleFileName
- char
- wchar_t
- extern
ms.openlocfilehash: b27668c3c7ce77e4369af144bb8be4efb695e522
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499812"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>main Funktions-und Befehlszeilenargumente

Alle C++-Programme müssen über eine- `main` Funktion verfügen. Wenn Sie versuchen, ein C++ *. exe* -Projekt ohne eine main Funktion zu kompilieren, gibt der Compiler einen Fehler aus. (Dynamic-Link-Bibliotheken und- static Bibliotheken haben keine `main` Funktion.) `main` In der Funktion wird der Quellcode mit der Ausführung begonnen, aber bevor ein Programm `main` in die Funktion eintritt, static werden alle Klassenmember ohne explizite Initialisierer auf NULL festgelegt. In Microsoft C++ werden globale static Objekte auch vor dem Eintrag in initialisiert `main` . Einige Einschränkungen gelten für die `main` Funktion, die nicht für andere C++-Funktionen gelten. Die- `main` Funktion:

- Kann nicht überladen werden (siehe [Funktions Überladung](function-overloading.md)).
- Kann nicht als deklariert werden **`inline`** .
- Kann nicht als deklariert werden **`static`** .
- Ihre Adresse kann nicht übernommen werden.
- Kann nicht aufgerufen werden.

Die main -Funktion verfügt nicht über eine-Deklaration, da Sie in die-Sprache integriert ist. Wenn dies der Fall ist, sieht die Deklarations Syntax für wie folgt aus `main` :

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Microsoft-spezifisch**

Wenn in ihren Quelldateien Unicode-weite char acters verwendet werden, können Sie verwenden `wmain` , wobei es sich um die Wide char Acter-Version von handelt `main` . Die Deklarationssyntax für `wmain` lautet wie folgt:

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Sie können auch verwenden `_tmain` , das in t char . h definiert ist. `_tmain` wird in aufgelöst, `main` es sei denn, _UNICODE definiert ist. In diesem Fall wird `_tmain` in `wmain` aufgelöst.

Wenn kein Rückgabewert angegeben wird, gibt der Compiler einen Rückgabewert von 0 (null) an. Alternativ können die `main` -Funktion und die- `wmain` Funktion als Rückgabe **`void`** (kein Rückgabewert) deklariert werden. Wenn Sie `main` oder `wmain` als zurück **`void`** geben, können Sie keinen exit Code an den übergeordneten Prozess oder das Betriebssystem zurückgeben, indem Sie eine [Return](./program-termination.md) -Anweisung verwenden. Um einen exit Code zurückzugeben `main` , wenn oder `wmain` als deklariert wird **`void`** , müssen Sie die- [exit](./program-termination.md) Funktion verwenden.

**Ende Microsoft-spezifisch**

## <a name="command-line-arguments"></a>Befehlszeilenargumente

Die Argumente für `main` oder `wmain` ermöglichen eine bequeme Befehlszeilen-Analyse von Argumenten und optional Zugriff auf Umgebungsvariablen. Die Typen für `argc` und `argv` werden von der Programmiersprache definiert. Die Namen `argc` , `argv` und `envp` sind traditionell, Sie können Sie jedoch beliebig benennen.

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

Die Argumentdefinitionen sind wie folgt:

*argc*<br/>
Eine ganze Zahl, die die Anzahl von Argumenten enthält, die in folgen *argv* . Der- *argc* Parameter ist immer größer als oder gleich 1.

*argv*<br/>
Ein Array von Zeigern auf Zeichenfolgen, die auf NULL enden und von den Benutzern des Programms eingegebene Befehlszeilenargumente darstellen. `argv[0]`Gemäß der Konvention ist der Befehl, mit dem das Programm aufgerufen wird, `argv[1]` das erste Befehlszeilenargument usw., bis `argv[argc]` , das immer NULL ist. Informationen zum Unterdrücken der Befehlszeilen Verarbeitung finden Sie unter [Anpassen der Befehlszeilen Verarbeitung]() .

Das erste Befehlszeilenargument ist immer `argv[1]`, und das letzte ist `argv[argc - 1]`.

> [!NOTE]
> `argv[0]`Gemäß der Konvention ist der Befehl, mit dem das Programm aufgerufen wird. Es ist jedoch möglich, einen Prozess mit zu erzeugen [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) , und wenn Sie sowohl das erste als auch das zweite Argument (*lpApplicationName* und *lpCommandLine*) verwenden, ist möglich `argv[0]` erweise nicht der Name der ausführbaren Datei. verwenden Sie, [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) um den Namen der ausführbaren Datei und den voll qualifizierten Pfad abzurufen.

**Microsoft-spezifisch**

*envp*<br/>
Das *envp* Array, das eine gemeinsame Erweiterung in vielen UNIX-Systemen ist, wird in Microsoft C++ verwendet. Es ist ein Zeichenfolgenarray, das die Variablen darstellt, die in der Benutzerumgebung festgelegt werden. Das Array wird mit einem NULL-Eintrag beendet. Sie kann als ein Array von Zeigern auf **`char`** ( `char *envp[]` ) oder als Zeiger auf Zeiger auf **`char`** ( `char **envp` ) deklariert werden. Wenn `wmain` das Programm anstelle von verwendet `main` , verwenden Sie den- **`wchar_t`** Datentyp anstelle von **`char`** . Der an und über gegebene Umgebungsblock `main` `wmain` ist eine "fixierte" Kopie der aktuellen Umgebung. Wenn Sie anschließend die Umgebung über einen `putenv` -oder-Rückruf ändern `_wputenv` , ändert sich die aktuelle Umgebung (wie von `getenv` oder `_wgetenv` und der-oder-Variable zurückgegeben `_environ`  `_wenviron` ), aber der Block, auf den verweist, envp ändert sich nicht. Informationen zum Unterdrücken der Umgebungs Verarbeitung finden Sie unter [Anpassen der Befehlszeilen Verarbeitung]() . Dieses Argument ist in C ANSI-kompatibel, aber nicht in C++.

**Ende Microsoft-spezifisch**

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie die *argc* *argv* Argumente, und für Folgendes verwendet werden *envp* `main` :

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>Parsing C++-Befehlszeilenargumente

**Microsoft-spezifisch**

Beim Interpretieren von Argumenten, die in der Befehlszeile des Betriebssystems angegeben werden, verwendet der Microsoft C/C++-Startcode die folgenden Regeln:

- Argumente werden durch einen Leerraum (Leerzeichen oder Tabstopp) abgegrenzt.

- Der char Caretzeichen (^) wird nicht als Escapezeichen char oder Trennzeichen erkannt. Der char Acter wird vom Befehlszeilen Parser im Betriebssystem vollständig verarbeitet, bevor er an das- `argv` Array im Programm übergeben wird.

- Eine Zeichenfolge, die in doppelten Anführungszeichen ("*String*") eingeschlossen ist, wird als einzelnes Argument interpretiert, unabhängig von Leerraum, der in enthalten ist. Eine Zeichenfolge in Anführungszeichen kann in ein Argument eingebettet sein.

- Ein doppeltes Anführungszeichen, dem ein umgekehrter Schrägstrich ( \\ ") vorangestellt ist, wird als literales doppeltes Anführungszeichen char (") interpretiert.

- Ein umgekehrter Schrägstrich wird als solcher interpretiert, sofern er nicht unmittelbar vor einem Anführungszeichen steht.

- Wenn ein doppeltes Anführungszeichen auf eine gerade Anzahl umgekehrter Schrägstriche folgt, wird für jedes Paar umgekehrter Schrägstriche ein umgekehrter Schrägstrich im `argv`-Array platziert. Das doppelte Anführungszeichen wird als Zeichenfolgentrennzeichen interpretiert.

- Wenn ein doppeltes Anführungszeichen auf eine ungerade Anzahl umgekehrter Schrägstriche folgt, wird für jedes Paar umgekehrter Schrägstriche ein umgekehrter Schrägstrich in das Array eingefügt, `argv` und das doppelte Anführungszeichen wird durch den umgekehrten Schrägstrich "Escapezeichen" main , wodurch ein literales doppeltes Anführungszeichen (") eingefügt wird `argv` .

### <a name="example"></a>Beispiel

Das folgende Programm zeigt, wie Befehlszeilenargumente übergeben werden:

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

Die folgende Tabelle zeigt beispielhafte Eingaben und zu erwartende Ausgaben, wobei die Regeln in der vorangehenden Liste aufgezeigt werden.

### <a name="results-of-parsing-command-lines"></a>Ergebnisse der Befehlszeilen Verarbeitung

|Befehlszeileneingabe|argv[1]|argv[2]|argv€|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**Ende Microsoft-spezifisch**

## <a name="wildcard-expansion"></a>Platzhaltererweiterung

**Microsoft-spezifisch**

Sie können Platzhalter – das Fragezeichen (?) und das Sternchen (*) – verwenden, um Dateinamen- und Pfadargumente in der Befehlszeile anzugeben.

Befehlszeilenargumente werden von einer Routine namens `_setargv` (oder `_wsetargv` in der Wide char Acter-Umgebung) behandelt, die standardmäßig keine Platzhalter in separate Zeichen folgen im `argv` Zeichen folgen Array erweitert. Weitere Informationen zum Aktivieren der Platzhalter Erweiterung finden Sie unter Erweitern von Platzhalter [Argumenten](../c-language/expanding-wildcard-arguments.md).

**Ende Microsoft-spezifisch**

## <a name="customizing-c-command-line-processing"></a>Anpassen der C++-Befehlszeilenverarbeitung

**Microsoft-spezifisch**

Wenn das Programm keine Befehlszeilenargumente akzeptiert, können Sie ein wenig Platz sparen, indem Sie die Verwendung der Bibliotheksroutine unterdrücken, die die Befehlszeilenverarbeitung ausführt. Diese Routine wird aufgerufen `_setargv` und unter Platzhalter [Erweiterung]()beschrieben. Um die Verwendung zu unterdrücken, definieren Sie eine Routine, die in der Datei, die die Funktion enthält, nichts bewirkt `main` , und benennen Sie Sie `_setargv` . Der-Befehl `_setargv` wird dann durch die Definition von erfüllt `_setargv` , und die Bibliotheksversion wird nicht geladen.

Wenn Sie mit dem-Argument nie auf die Umgebungs Tabelle zugreifen `envp` , können Sie eine eigene leere Routine bereitstellen, die anstelle der `_setenvp` Umgebungs Verarbeitungsroutine verwendet wird. Ebenso wie bei der- `_setargv` Funktion `_setenvp` muss als ** extern "C"** deklariert werden.

Das Programm kann die-oder- `spawn` `exec` Familie von Routinen in der C-Lauf Zeit Bibliothek aufrufen. Wenn dies der Fall ist, sollten Sie die Umgebungs Verarbeitungsroutine nicht unterdrücken, da diese Routine verwendet wird, um eine Umgebung vom übergeordneten Prozess an den untergeordneten Prozess zu übergeben.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Grundlegende Konzepte](../cpp/basic-concepts-cpp.md)
