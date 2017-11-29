---
title: Andere Ausgabestreammanipulatoren mit einem Argument | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output streams, one-argument manipulators
ms.assetid: e381dee8-6b16-4cef-805a-4a6a1d2b696b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a3d453746b9f9af7219f181949ba9958c27a1577
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="other-one-argument-output-stream-manipulators"></a>Andere Ausgabestreammanipulatoren mit einem Argument
Im folgenden Beispiel wird eine `money`-Klasse verwendet, die ein `long`-Typ ist. Der `setpic`-Manipulator fügt eine „Bild“-Formatierungszeichenfolge zur Klasse hinzu, die vom überladenen Operator zum Einfügen des Datenstroms der Klasse `money` verwendet werden kann. Die Bildzeichenfolge wird als statische Variable in der `money`-Klasse und nicht als Datenmember einer Streamklasse gespeichert, sodass Sie keine neue Ausgabestreamklasse ableiten müssen.  
  
## <a name="example"></a>Beispiel  
  
```cpp  
// one_arg_output.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <iomanip>  
#include <string>  
using namespace std;  
  
typedef char* charp;  
  
class money   
{  
private:  
    long value;  
    static char *szCurrentPic;  
public:  
    money( long val ) { value = val; }  
    friend ostream& operator << ( ostream& os, money m ) {  
        // A more complete function would merge the picture  
        // with the value rather than simply appending it  
        os << m.value << '[' << money::szCurrentPic << ']';  
        return os;  
    }  
    static void setpic( char* szPic ) {  
        money::szCurrentPic = new char[strlen( szPic ) + 1];  
        strcpy_s( money::szCurrentPic, strlen( szPic ) + 1, szPic );  
    }  
};  
  
char *money::szCurrentPic;  // Static pointer to picture  
  
void fb( ios_base& os, char * somename )  
{  
   money::setpic(somename);  
/*  
   ostream *pos = dynamic_cast<ostream*>(&os);  
   if (pos)  
   {  
      for( int i=0; i < l; i++ )  
      (*pos) << ' ';  
   };  
*/  
}  
  
_Smanip<charp>  
   __cdecl setpic(char * somename)  
   {     
   return (_Smanip<charp>(&fb, somename));  
   }  
  
int main( )  
{  
    money amt = (long)35235.22;  
    cout << setiosflags( ios::fixed );  
    cout << setpic( "###,###,###.##" ) << "amount = " << amt << endl;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerdefinierte Manipulatoren mit Argumenten](../standard-library/custom-manipulators-with-arguments.md)
