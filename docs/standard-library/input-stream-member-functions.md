---
title: Eingabestream-Memberfunktionen
ms.date: 07/19/2019
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: 8aa211a03bb6e9b1d910db360066b4a2ca76571a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233170"
---
# <a name="input-stream-member-functions"></a>Eingabestream-Memberfunktionen

Eingabestream-Memberfunktionen werden für Datenträgereingaben verwendet.

## <a name="open"></a><a name="vclrftheopenfunctionforinputstreamsanchor11"></a>eren

Wenn Sie einen Eingabedatei Datenstrom ( `ifstream` ) verwenden, müssen Sie diesen Stream einer bestimmten Datenträger Datei zuordnen. Hierfür können Sie den-Konstruktor verwenden, oder Sie können die- `open` Funktion verwenden. In beiden Fällen sind die Argumente gleich.

Im Allgemeinen geben Sie ein [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) -Flag an, wenn Sie die Datei öffnen, die einem Eingabestream zugeordnet ist (der Standardmodus ist `ios::in` ). Eine Liste der `openmode` Flags finden Sie unter [ios_base:: openmode](../standard-library/ios-base-class.md#openmode). Die Flags können mit dem bitweisen OR-Operator ( &#124; ) kombiniert werden.

Um eine Datei zu lesen, verwenden Sie zuerst die `fail` Member-Funktion, um zu bestimmen, ob Sie vorhanden ist:

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="get"></a><a name="vclrfthegetfunctionanchor12"></a>Erhalten

Die nicht formatierte `get` Member-Funktion funktioniert wie der- `>>` Operator mit zwei Ausnahmen. Zunächst enthält die `get` -Funktion Leerzeichen, während der Extraktor Leerraum ausschließt, wenn das- `skipws` Flag festgelegt ist (Standardeinstellung). Zweitens `get` ist es weniger wahrscheinlich, dass die Funktion einen gebundenen Ausgabestream ( `cout` z. b.) verursacht.

Eine Variation der `get` -Funktion gibt eine Puffer Adresse und die maximale Anzahl der zu lesenden Zeichen an. Dies hilft dabei, die Anzahl der Zeichen einzuschränken, die zu einer bestimmten Variable gesendet werden, wie dieses Beispiel zeigt:

```cpp
// ioo_get_function.cpp
// compile with: /EHsc
// Type up to 24 characters and a terminating character.
// Any remaining characters can be extracted later.
#include <iostream>
using namespace std;

int main()
{
   char line[25];
   cout << " Type a line terminated by carriage return\n>";
   cin.get( line, 25 );
   cout << line << endl;
}
```

### <a name="input"></a>Eingabe

```Input
1234
```

### <a name="sample-output"></a>Beispielausgabe

```Output
1234
```

## <a name="getline"></a><a name="vclrfthegetlinefunctionanchor13"></a>getline

Die `getline` Member-Funktion ähnelt der- `get` Funktion. Beide Funktionen ermöglichen ein drittes Argument, das abschließende Zeichen für die Eingabe angibt. Der Standardwert ist das Zeilenumbruchzeichen. Beide Funktionen reservieren ein Zeichen für das benötigte abschließende Zeichen. Behält jedoch `get` das abschließende Zeichen im Stream bei und `getline` entfernt das abschließende Zeichen.

Im folgenden Beispiel wird ein abschließendes Zeichen für den Eingabestream angegeben:

```cpp
// getline_func.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char line[100];
   cout << " Type a line terminated by 't'" << endl;
   cin.getline( line, 100, 't' );
   cout << line;
}
```

### <a name="input"></a>Eingabe

```Input
test
```

## <a name="read"></a><a name="vclrfthereadfunctionanchor14"></a>dazu

Die `read` Member-Funktion liest Bytes aus einer Datei in einen angegebenen Speicherbereich. Das Längenargument bestimmt die Anzahl gelesener Bytes. Wenn Sie dieses Argument nicht einfügen, wird das Lesen beendet, sobald das physische Ende der Datei erreicht ist, oder, bei einer Textmodusdatei, wenn ein eingebettetes `EOF`-Zeichen gelesen wird.

Dieses Beispiel liest einen binären Datensatz aus einer Lohnabrechnungsdatei in eine Struktur:

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main()
{
   struct
   {
      double salary;
      char name[23];
   } employee;

   ifstream is( "payroll" );
   if( is ) {  // ios::operator void*()
      is.read( (char *) &employee, sizeof( employee ) );
      cout << employee.name << ' ' << employee.salary << endl;
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

Das Programm geht davon aus, dass die Datensätze genau so formatiert sind, wie von der Struktur angegeben, ohne abschließende Wagen Rücklauf-oder Zeilenvorschub Zeichen.

## <a name="seekg-and-tellg"></a><a name="vclrftheseekgandtellgfunctionsanchor7"></a>seekg und Tellg

Eingabedatei-Streams behalten einen internen Zeiger auf der Position in der Datei, in der Daten als Nächstes gelesen werden. Legen Sie diesen Zeiger mit der `seekg`-Funktion fest, wie hier gezeigt:

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main( )
{
   char ch;

   ifstream tfile( "payroll" );
   if( tfile ) {
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)
      while ( tfile.good() ) { // EOF or failure stops the reading
         tfile.get( ch );
         if( !ch ) break;      // quit on null
         cout << ch;
      }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

Um mithilfe `seekg` von Daten Satz orientierte Daten Verwaltungssysteme zu implementieren, Multiplizieren Sie die Größe des Datensatzes mit fester Länge mit der Datensatznummer, um die Byte Position relativ zum Dateiende zu erhalten, und verwenden Sie dann das- `get` Objekt, um den Datensatz zu lesen.

Die `tellg`-Memberfunktion gibt die aktuelle Dateiposition zum Lesen zurück. Dieser Wert ist vom Typ `streampos` , der **`typedef`** in definiert ist \<iostream> . Das folgende Beispiel liest eine Datei und zeigt Meldungen an, die die Positionen der Leerzeichen zeigen.

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main( )
{
   char ch;
   ifstream tfile( "payroll" );
   if( tfile ) {
       while ( tfile.good( ) ) {
          streampos here = tfile.tellg();
          tfile.get( ch );
          if ( ch == ' ' )
             cout << "\nPosition " << here << " is a space";
       }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

## <a name="close"></a><a name="vclrftheclosefunctionforinputstreamsanchor15"></a>ihrer

Die `close` Member-Funktion schließt die einem Eingabedatei Datenstrom zugeordnete Datenträger Datei und gibt das Datei Handle des Betriebssystems frei. Der [`ifstream`](../standard-library/basic-ifstream-class.md) debugtor schließt die Datei für Sie, aber Sie können die-Funktion verwenden, `close` Wenn Sie eine andere Datei für das gleiche Streamobjekt öffnen müssen.

## <a name="see-also"></a>Siehe auch

[Eingabestreams](../standard-library/input-streams.md)
