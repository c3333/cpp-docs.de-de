---
title: '`main` Funktions-und Befehlszeilenargumente (C++)'
description: Die- `main` Funktion ist der Einstiegspunkt für ein C++-Programm.
ms.date: 11/19/2020
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
ms.openlocfilehash: 8a5ed43bdacf5d9d6dd2cbc5d1c56783c82b8e9a
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483216"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>`main` Funktions-und Befehlszeilenargumente

Alle C++-Programme müssen über eine- `main` Funktion verfügen. Wenn Sie versuchen, ein C++-Programm ohne eine `main` Funktion zu kompilieren, löst der Compiler einen Fehler aus. (Dynamic-Link-Bibliotheken und- static Bibliotheken haben keine `main` Funktion.) `main` In der Funktion wird der Quellcode mit der Ausführung begonnen, aber bevor ein Programm `main` in die Funktion eintritt, static werden alle Klassenmember ohne explizite Initialisierer auf NULL festgelegt. In Microsoft C++ werden globale static Objekte auch vor dem Eintrag in initialisiert `main` . Einige Einschränkungen gelten für die `main` Funktion, die für keine anderen C++-Funktionen gelten. Die- `main` Funktion:

- Kann nicht überladen werden (siehe [Funktions Überladung](./function-overloading.md)).
- Kann nicht als deklariert werden **`inline`** .
- Kann nicht als deklariert werden **`static`** .
- Die Adresse kann nicht übernommen werden.
- Kann nicht von Ihrem Programm aufgerufen werden.

## <a name="the-no-locmain-function-signature"></a>Die `main` Funktions Signatur

Die `main` -Funktion verfügt nicht über eine-Deklaration, da Sie in die-Sprache integriert ist. Wenn dies der Fall ist, sieht die Deklarations Syntax für wie folgt aus `main` :

```cpp
int main();
int main(int argc, char *argv[]);
```

Wenn in kein Rückgabewert angegeben wird `main` , gibt der Compiler einen Rückgabewert von 0 (null) an.

## <a name="standard-command-line-arguments"></a>Standard Befehlszeilenargumente

Die Argumente für `main` ermöglichen eine bequeme Befehlszeilen-Analyse von Argumenten. Die Typen für `argc` und `argv` werden von der Programmiersprache definiert. Die Namen `argc` und `argv` sind traditionell, Sie können Sie aber beliebig benennen.

Die Argumentdefinitionen sind wie folgt:

*`argc`*\
Eine ganze Zahl, die die Anzahl von Argumenten enthält, die in folgen *argv* . Der- *argc* Parameter ist immer größer als oder gleich 1.

*`argv`*\
Ein Array von Zeigern auf Zeichenfolgen, die auf NULL enden und von den Benutzern des Programms eingegebene Befehlszeilenargumente darstellen. `argv[0]`Gemäß der Konvention ist der Befehl, mit dem das Programm aufgerufen wird. `argv[1]` ist das erste Befehlszeilenargument. Das letzte Argument in der Befehlszeile ist `argv[argc - 1]` , und `argv[argc]` ist immer NULL.

Informationen dazu, wie die Befehlszeilen Verarbeitung unterdrückt wird, finden Sie unter [Anpassen der Befehlszeilen Verarbeitung in C++](#customize).

> [!NOTE]
> Gemäß der Konvention `argv[0]` ist der Dateiname des Programms. Unter Windows ist es jedoch möglich, einen Prozess mit zu erzeugen [`CreateProcess`](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) . Wenn Sie sowohl das erste als auch das zweite Argument ( *`lpApplicationName`* und *`lpCommandLine`* ) verwenden, ist `argv[0]` möglicherweise nicht der Name der ausführbaren Datei. Mit können Sie [`GetModuleFileName`](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) den Namen der ausführbaren Datei und den voll qualifizierten Pfad abrufen.

## <a name="microsoft-specific-extensions"></a>Microsoft-spezifische Erweiterungen

In den folgenden Abschnitten wird das Microsoft-spezifische Verhalten beschrieben.

## <a name="the-no-locwmain-function-and-no-loc_tmain-macro"></a>Die `wmain` Funktion und das `_tmain` Makro

Wenn Sie den Quellcode für die Verwendung von Unicode-weiten Zugriffs char Punkten entwerfen, können Sie den Microsoft-spezifischen Einstiegspunkt verwenden, bei dem es sich um `wmain` die Wide char Acter-Version von handelt `main` . Hier ist die effektive Deklarations Syntax für `wmain` :

```cpp
int wmain();
int wmain(int argc, wchar_t *argv[]);
```

Sie können auch den Microsoft-spezifischen verwenden `_tmain` , bei dem es sich um ein in definiertes Präprozessormakro handelt *`tchar.h`* . `_tmain` wird in aufgelöst, `main` sofern nicht `_UNICODE` definiert ist. In diesem Fall wird `_tmain` in `wmain` aufgelöst. Das `_tmain` Makro und andere Makros, die mit beginnen, `_t` sind nützlich für Code, der separate Versionen für schmale und Breite char actersets erstellen muss. Weitere Informationen finden Sie unter [Verwenden von generischen Text](../c-runtime-library/using-generic-text-mappings.md)Zuordnungen.

## <a name="returning-no-locvoid-from-no-locmain"></a>Rückgabe `void` von main

Als Microsoft-Erweiterung können die `main` -Funktion und die- `wmain` Funktion als Rückgabe **`void`** (kein Rückgabewert) deklariert werden. Diese Erweiterung ist auch in einigen anderen Compilern verfügbar, aber ihre Verwendung ist nicht empfehlenswert. Es ist für die Symmetrie verfügbar, wenn keinen `main` Wert zurückgibt.

Wenn Sie `main` oder `wmain` als zurück **`void`** geben, können Sie keinen exit Code an den übergeordneten Prozess oder das Betriebssystem zurückgeben, indem Sie eine-Anweisung verwenden [`return`](./program-termination.md) . Um einen exit Code zurückzugeben `main` , wenn oder `wmain` als deklariert wird **`void`** , müssen Sie die- [`exit`](./program-termination.md) Funktion verwenden.

## <a name="the-no-locenvp-command-line-argument"></a>Das `envp` Befehlszeilenargument

Die `main` `wmain` Signaturen oder ermöglichen eine optionale Microsoft-spezifische Erweiterung für den Zugriff auf Umgebungsvariablen. Diese Erweiterung ist auch in anderen Compilern für Windows-und UNIX-Systeme üblich. Der Name *`envp`* ist traditionell, aber Sie können den Umgebungsparameter beliebig benennen. Im folgenden finden Sie die effektiven Deklarationen für die Argumentlisten, die den Umgebungsparameter enthalten:

```cpp
int main(int argc, char* argv[], char* envp[]);
int wmain(int argc, wchar_t* argv[], wchar_t* envp[]);
```

*`envp`*\
Der optionale- *`envp`* Parameter ist ein Array von Zeichen folgen, die die Variablen darstellen, die in der Benutzerumgebung festgelegt sind. Das Array wird mit einem NULL-Eintrag beendet. Sie kann als ein Array von Zeigern auf **`char`** ( `char *envp[]` ) oder als Zeiger auf Zeiger auf **`char`** ( `char **envp` ) deklariert werden. Wenn `wmain` das Programm anstelle von verwendet `main` , verwenden Sie den- **`wchar_t`** Datentyp anstelle von **`char`** .

Der an und über gegebene Umgebungsblock `main` `wmain` ist eine "fixierte" Kopie der aktuellen Umgebung. Wenn Sie die Umgebung später ändern, indem Sie einen- `putenv` oder-Rückruf ausführen, ändert sich `_wputenv` die aktuelle Umgebung (wie von `getenv` oder `_wgetenv` und der-oder-Variable zurückgegeben `_environ`  `_wenviron` ), aber der Block, auf den verweist, wird *`envp`* nicht geändert. Weitere Informationen zum Unterdrücken der Umgebungs Verarbeitung finden Sie unter [Anpassen der Befehlszeilen Verarbeitung in C++](#customize). Das- *`envp`* Argument ist mit dem C89-Standard kompatibel, jedoch nicht mit C++-Standards.

### <a name="example-arguments-to-no-locmain"></a>Beispiel Argumente für `main`

Im folgenden Beispiel wird gezeigt, wie die *`argc`* *`argv`* Argumente, und für Folgendes verwendet werden *`envp`* `main` :

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

## <a name="parsing-c-command-line-arguments"></a>Analysieren von C++-Befehlszeilenargumenten

Die vom Microsoft C/C++-Code verwendeten Befehlszeilen-Regel Regeln sind Microsoft-spezifisch. Der Startcode der Laufzeit verwendet diese Regeln, wenn in der Befehlszeile des Betriebssystems angegebene Argumente interpretiert werden:

- Argumente werden durch einen Leerraum (Leerzeichen oder Tabstopp) abgegrenzt.

- Das erste Argument (`argv[0]`) wird besonders behandelt. Es repräsentiert den Programmnamen. Da es sich um einen gültigen Pfadnamen handeln muss, sind Bestandteile in doppelten geraden Anführungszeichen oben ( **`"`** ) zulässig. Die Anführungszeichen sind nicht in der Ausgabe von `argv[0]` enthalten. Die in doppelten Anführungszeichen eingeschlossene Teile verhindern die Interpretation eines leer Zeichens oder eines Registerkarten- char acters als Ende des Arguments. Die weiter unten in dieser Liste aufgeführten Regeln gelten nicht.

- Eine Zeichenfolge, die in doppelten Anführungszeichen eingeschlossen ist, wird als einzelnes Argument interpretiert, das möglicherweise Leerzeichen enthält char . Eine Zeichenfolge in Anführungszeichen kann in ein Argument eingebettet sein. Der **`^`** Caretzeichen () wird nicht als Escapezeichen char oder Trennzeichen erkannt. Innerhalb einer in Anführungszeichen eingeschlossenen Zeichenfolge wird ein Paar aus doppelten Anführungszeichen als ein einzelnes doppeltes Anführungszeichen mit Escapezeichen interpretiert. Wenn die Befehlszeile endet, bevor eine schließende doppelte Anführungszeichen gefunden wird, char werden alle bisher gelesenen acters als letztes Argument ausgegeben.

- Wenn dem doppelten Anführungszeichen ein umgekehrter Schrägstrich ( **`\"`** ) vorangestellt ist, wird diese Zeichenfolge als tatsächliches doppeltes Anführungszeichen ( **`"`** ) interpretiert.

- Ein umgekehrter Schrägstrich wird als solcher interpretiert, sofern er nicht unmittelbar vor einem Anführungszeichen steht.

- Wenn ein doppeltes Anführungszeichen auf eine gerade Anzahl umgekehrter Schrägstriche folgt, wird für jedes Paar umgekehrter Schrägstriche ( **`\\`** ) ein umgekehrter Schrägstrich ( **`\`** ) im `argv`-Array platziert. Das doppelte Anführungszeichen ( **`"`** ) wird als Zeichenfolgentrennzeichen interpretiert.

- Wenn ein doppeltes Anführungszeichen auf eine ungerade Anzahl umgekehrter Schrägstriche folgt, wird für jedes Paar umgekehrter Schrägstriche ( **`\\`** ) ein umgekehrter Schrägstrich ( **`\`** ) im `argv`-Array platziert. Das doppelte Anführungszeichen wird vom umgekehrten Schrägstrich als Escapesequenz interpretiert main und bewirkt, dass ein literales doppeltes Anführungszeichen ( **`"`** ) in eingefügt wird `argv` .

### <a name="example-of-command-line-argument-parsing"></a>Beispiel für die Analyse-Befehlszeilenargumente

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

### <a name="results-of-parsing-command-lines"></a>Ergebnisse der Befehlszeilen Verarbeitung

Die folgende Tabelle zeigt beispielhafte Eingaben und zu erwartende Ausgaben, wobei die Regeln in der vorangehenden Liste aufgezeigt werden.

| Befehlszeilen Eingabe | argv[1] | argv[2] | argv€ |
|--|--|--|--|
| `"abc" d e` | `abc` | `d` | `e` |
| `a\\b d"e f"g h` | `a\\b` | `de fg` | `h` |
| `a\\\"b c d` | `a\"b` | `c` | `d` |
| `a\\\\"b c" d e` | `a\\b c` | `d` | `e` |
| `a"b"" c d` | `ab" c d` |  |  |

## <a name="wildcard-expansion"></a>Platzhaltererweiterung

*Mit dem* Microsoft-Compiler können Sie optional Platzhalter char -acters, das Fragezeichen ( **`?`** ) und das Sternchen ( **`*`** ) verwenden, um Dateinamen-und Pfad Argumente in der Befehlszeile anzugeben.

Befehlszeilenargumente werden von einer internen Routine im Lauf Zeit Startcode behandelt, der standardmäßig keine Platzhalter in separate Zeichen folgen im Zeichen folgen `argv` Array erweitert. Sie können die Erweiterung für Platzhalter aktivieren, indem Sie die *`setargv.obj`* Datei ( *`wsetargv.obj`* Datei für `wmain` ) in die **`/link`** Compileroptionen oder die **`LINK`** Befehlszeile einschließen.

Weitere Informationen zu den Optionen für den Runtime-Start Linker finden Sie unter [Link Optionen](../c-runtime-library/link-options.md).

## <a name="customize-c-command-line-processing"></a><a name="customize"/> Anpassen der C++-Befehlszeilen Verarbeitung

Wenn das Programm keine Befehlszeilenargumente akzeptiert, können Sie die Verarbeitungsroutine für die Befehlszeile unterdrücken, um eine kleine Menge an Speicherplatz zu sparen. Um die Verwendung zu unterdrücken, schließen *`noarg.obj`* Sie die Datei (für `main` und `wmain` ) in die **`/link`** Compileroptionen oder die **`LINK`** Befehlszeile ein.

Wenn Sie auf die Umgebungs Tabelle nicht über das- *`envp`* Argument zugreifen, können Sie auch die interne Umgebungs Verarbeitungsroutine unterdrücken. Um die Verwendung zu unterdrücken, schließen *`noenv.obj`* Sie die Datei (für `main` und `wmain` ) in die **`/link`** Compileroptionen oder die **`LINK`** Befehlszeile ein.

Das Programm kann die-oder- `spawn` `exec` Familie von Routinen in der C-Lauf Zeit Bibliothek aufrufen. Wenn dies der Fall ist, sollten Sie die Umgebungs Verarbeitungsroutine nicht unterdrücken, da Sie verwendet wird, um eine Umgebung vom übergeordneten Prozess an den untergeordneten Prozess zu übergeben.

## <a name="see-also"></a>Siehe auch

[Grundlegende Konzepte](../cpp/basic-concepts-cpp.md)
