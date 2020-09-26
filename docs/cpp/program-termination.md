---
title: C++ Programm Beendigung
description: Beschreibt die Methoden für exit ein C++-Programm.
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- exit
- abort
- return
- main
- atexit
- void
ms.openlocfilehash: fd0c7699ae032b5551f4fbc37eb3b7fa999a168f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352920"
---
# <a name="c-program-termination"></a>C++ Programm Beendigung

In C++ können Sie exit ein Programm auf folgende Weise ausführen:

- Ruft die- [exit](../c-runtime-library/reference/exit-exit-exit.md) Funktion auf.
- Ruft die- [abort](../c-runtime-library/reference/abort.md) Funktion auf.
- Führen Sie eine [return](return-statement-cpp.md) Anweisung von aus `main` .

## <a name="no-locexit-function"></a>exit-Funktion

Die [exit](../c-runtime-library/reference/exit-exit-exit.md) Funktion, die in deklariert \<stdlib.h> wird, beendet ein C++-Programm. Der Wert, der als Argument für bereitgestellt `exit` wird return , wird als Programm return Code oder Code an das Betriebssystem übergeben exit . Gemäß return der Konvention bedeutet ein Code von 0 (null), dass das Programm erfolgreich abgeschlossen wurde. Sie können die Konstanten EXIT_FAILURE und EXIT_SUCCESS verwenden, die auch in definiert \<stdlib.h> sind, um den Erfolg oder Misserfolg des Programms anzugeben.

Das Ausgeben einer- **`return`** Anweisung aus der- `main` Funktion entspricht dem Aufrufen der- `exit` Funktion mit dem- return Wert als Argument.

## <a name="no-locabort-function"></a>abort-Funktion

Die [abort](../c-runtime-library/reference/abort.md) Funktion, die auch in der standardmäßigen Includedatei deklariert \<stdlib.h> wird, beendet ein C++-Programm. Der Unterschied zwischen `exit` und `abort` besteht darin, dass `exit` die C++-Lauf Zeit Beendigungs Verarbeitung stattfinden kann (globale objektdedeprozesse werden aufgerufen), während `abort` das Programm sofort beendet. Die- `abort` Funktion umgeht den normalen Zerstörungsprozess für initialisierte globale statische Objekte. Außerdem werden alle speziellen Verarbeitungsvorgänge umgangen, die mithilfe der- [atexit](../c-runtime-library/reference/atexit.md) Funktion angegeben wurden.

## <a name="no-locatexit-function"></a>atexit-Funktion

Verwenden Sie die- [atexit](../c-runtime-library/reference/atexit.md) Funktion, um Aktionen anzugeben, die vor der Programm Beendigung ausgeführt werden. Vor der **atexit** Ausführung der-Verarbeitungs Funktion werden keine globalen statischen Objekte, die vor dem-Befehl initialisiert wurden, zerstört exit .

## <a name="no-locreturn-statement-in-no-locmain"></a>return Anweisung in main

Die Ausgabe einer- [return](return-statement-cpp.md) Anweisung aus `main` ist funktional äquivalent zum Aufrufen der- `exit` Funktion. Betrachten Sie das folgende Beispiel:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Die `exit` -und- **`return`** Anweisungen im vorherigen Beispiel sind funktionell identisch. C++ erfordert jedoch, dass Funktionen, die return andere Typen als **`void`** return einen-Wert aufweisen. Mit der- **`return`** Anweisung können Sie return einen Wert von aus `main` .

## <a name="destruction-of-static-objects"></a>Zerstörung statischer Objekte

Wenn Sie `exit` eine-Anweisung von aufzurufen oder Ausführen **`return`** `main` , werden statische Objekte in umgekehrter Reihenfolge ihrer Initialisierung zerstört (nach dem-aufzurufen, `atexit` sofern vorhanden). Das folgende Beispiel zeigt, wie so eine Initialisierung und Bereinigung funktionieren.

### <a name="example"></a>Beispiel

Im folgenden Beispiel werden die statischen Objekte `sd1` und `sd2` vor dem Eintrag in erstellt und initialisiert `main` . Nachdem das Programm mithilfe der **`return`** -Anweisung beendet wurde, `sd2` wird zuerst zerstört und dann `sd1` . Der Destruktor für die Klasse `ShowData` schließt die Dateien, die diesen statischen Objekten zugeordnet sind.

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

Eine andere Möglichkeit zum Schreiben des Codes besteht darin, die `ShowData`-Objekte mit dem Blockbereich zu deklarieren, sodass sie zerstört werden, wenn sie den Gültigkeitsbereich verlassen:

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Weitere Informationen

[main Funktions-und Befehlszeilenargumente](main-function-command-line-args.md)
