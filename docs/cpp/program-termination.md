---
title: C++ Programm Beendigung
description: 'Beschreibt die Methoden für :::no-loc(exit)::: ein C++-Programm.'
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- :::no-loc(exit):::ing applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- ':::no-loc(exit):::'
- ':::no-loc(abort):::'
- ':::no-loc(return):::'
- ':::no-loc(main):::'
- ':::no-loc(atexit):::'
- ':::no-loc(void):::'
ms.openlocfilehash: 216aef5dbe8d110f9d75d43b5009b89fc5bfda51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227178"
---
# <a name="c-program-termination"></a>C++ Programm Beendigung

In C++ können Sie :::no-loc(exit)::: ein Programm auf folgende Weise ausführen:

- Ruft die- [:::no-loc(exit):::](:::no-loc(exit):::-function.md) Funktion auf.
- Ruft die- [:::no-loc(abort):::](:::no-loc(abort):::-function.md) Funktion auf.
- Führen Sie eine [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) Anweisung von aus `:::no-loc(main):::` .

## <a name="no-locexit-function"></a>:::no-loc(exit):::-Funktion

Die [:::no-loc(exit):::](../c-runtime-library/reference/:::no-loc(exit):::-:::no-loc(exit):::-:::no-loc(exit):::.md) Funktion, die in deklariert \<stdlib.h> wird, beendet ein C++-Programm. Der Wert, der als Argument für bereitgestellt `:::no-loc(exit):::` wird :::no-loc(return)::: , wird als Programm :::no-loc(return)::: Code oder Code an das Betriebssystem übergeben :::no-loc(exit)::: . Gemäß :::no-loc(return)::: der Konvention bedeutet ein Code von 0 (null), dass das Programm erfolgreich abgeschlossen wurde. Sie können die Konstanten EXIT_FAILURE und EXIT_SUCCESS verwenden, die auch in definiert \<stdlib.h> sind, um den Erfolg oder Misserfolg des Programms anzugeben.

Das Ausgeben einer- **`:::no-loc(return):::`** Anweisung aus der- `:::no-loc(main):::` Funktion entspricht dem Aufrufen der- `:::no-loc(exit):::` Funktion mit dem- :::no-loc(return)::: Wert als Argument.

## <a name="no-locabort-function"></a>:::no-loc(abort):::-Funktion

Die [:::no-loc(abort):::](../c-runtime-library/reference/:::no-loc(abort):::.md) Funktion, die auch in der standardmäßigen Includedatei deklariert \<stdlib.h> wird, beendet ein C++-Programm. Der Unterschied zwischen `:::no-loc(exit):::` und `:::no-loc(abort):::` besteht darin, dass `:::no-loc(exit):::` die C++-Lauf Zeit Beendigungs Verarbeitung stattfinden kann (globale objektdedeprozesse werden aufgerufen), während `:::no-loc(abort):::` das Programm sofort beendet. Die- `:::no-loc(abort):::` Funktion umgeht den normalen Zerstörungsprozess für initialisierte globale statische Objekte. Außerdem werden alle speziellen Verarbeitungsvorgänge umgangen, die mithilfe der- [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) Funktion angegeben wurden.

## <a name="no-locatexit-function"></a>:::no-loc(atexit):::-Funktion

Verwenden Sie die- [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) Funktion, um Aktionen anzugeben, die vor der Programm Beendigung ausgeführt werden. Vor der **:::no-loc(atexit):::** Ausführung der-Verarbeitungs Funktion werden keine globalen statischen Objekte, die vor dem-Befehl initialisiert wurden, zerstört :::no-loc(exit)::: .

## <a name="no-locreturn-statement-in-no-locmain"></a>:::no-loc(return):::Anweisung in:::no-loc(main):::

Die Ausgabe einer- [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) Anweisung aus `:::no-loc(main):::` ist funktional äquivalent zum Aufrufen der- `:::no-loc(exit):::` Funktion. Betrachten Sie das folgenden Beispiel:

```cpp
// :::no-loc(return):::_statement.cpp
#include <stdlib.h>
int :::no-loc(main):::()
{
    :::no-loc(exit):::( 3 );
    :::no-loc(return)::: 3;
}
```

Die `:::no-loc(exit):::` -und- **`:::no-loc(return):::`** Anweisungen im vorherigen Beispiel sind funktionell identisch. C++ erfordert jedoch, dass Funktionen, die :::no-loc(return)::: andere Typen als **`:::no-loc(void):::`** :::no-loc(return)::: einen-Wert aufweisen. Mit der- **`:::no-loc(return):::`** Anweisung können Sie :::no-loc(return)::: einen Wert von aus `:::no-loc(main):::` .

## <a name="destruction-of-static-objects"></a>Zerstörung statischer Objekte

Wenn Sie `:::no-loc(exit):::` eine-Anweisung von aufzurufen oder Ausführen **`:::no-loc(return):::`** `:::no-loc(main):::` , werden statische Objekte in umgekehrter Reihenfolge ihrer Initialisierung zerstört (nach dem-aufzurufen, `:::no-loc(atexit):::` sofern vorhanden). Das folgende Beispiel zeigt, wie so eine Initialisierung und Bereinigung funktionieren.

### <a name="example"></a>Beispiel

Im folgenden Beispiel werden die statischen Objekte `sd1` und `sd2` vor dem Eintrag in erstellt und initialisiert `:::no-loc(main):::` . Nachdem das Programm mithilfe der **`:::no-loc(return):::`** -Anweisung beendet wurde, `sd2` wird zuerst zerstört und dann `sd1` . Der Destruktor für die Klasse `ShowData` schließt die Dateien, die diesen statischen Objekten zugeordnet sind.

```cpp
// using_:::no-loc(exit):::_or_:::no-loc(return):::1.cpp
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
   :::no-loc(void)::: Disp( char *szData ) {
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

int :::no-loc(main):::() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

Eine andere Möglichkeit zum Schreiben des Codes besteht darin, die `ShowData`-Objekte mit dem Blockbereich zu deklarieren, sodass sie zerstört werden, wenn sie den Gültigkeitsbereich verlassen:

```cpp
int :::no-loc(main):::() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Siehe auch

[:::no-loc(main):::Funktions-und Befehlszeilenargumente](:::no-loc(main):::-function-command-line-args.md)
