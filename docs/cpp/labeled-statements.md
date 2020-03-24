---
title: Anweisungen mit Bezeichnung
ms.date: 11/04/2016
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
ms.openlocfilehash: d971a0e9864aeada1db5f004ef70577512e78c76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179691"
---
# <a name="labeled-statements"></a>Anweisungen mit Bezeichnung

Bezeichnungen werden verwendet, um die Programmsteuerung direkt an die angegebene Anweisung zu übertragen.

```
identifier :  statement
case constant-expression :  statement
default :  statement
```

Der Umfang einer Bezeichnung ist die gesamte Funktion, in der diese deklariert wurde.

## <a name="remarks"></a>Bemerkungen

Es gibt drei Typen von bezeichneten Anweisungen. Alle verwenden einen Doppelpunkt, um einen Bezeichnungstyp von der Anweisung zu trennen. Die case- und default-Bezeichnungen sind für case-Anweisungen bestimmt.

```cpp
#include <iostream>
using namespace std;

void test_label(int x) {

    if (x == 1){
        goto label1;
    }
    goto label2;

label1:
    cout << "in label1" << endl;
    return;

label2:
    cout << "in label2" << endl;
    return;
}

int main() {
    test_label(1);  // in label1
    test_label(2);  // in label2
}
```

**Die GoTo-Anweisung**

Das Aussehen einer *bezeichnerbezeichnung* im Quell Programm deklariert eine Bezeichnung. Nur eine [goto](../cpp/goto-statement-cpp.md) -Anweisung kann die Steuerung an eine *bezeichnerbezeichnung* übertragen. Das folgende Code Fragment veranschaulicht die Verwendung der **goto** -Anweisung und eine *bezeichnerbezeichnung* :

Eine Bezeichnung kann nicht allein stehen, sondern muss immer an eine Anweisung angefügt werden. Wenn eine Bezeichnung allein benötigt wird, platzieren Sie nach ihr eine NULL-Anweisung.

Die Bezeichnung gilt funktionsweit und kann nicht innerhalb der Funktion erneut deklariert werden. Allerdings kann derselbe Name in verschiedenen Funktionen als Bezeichnung verwendet werden.

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
}

//Output: At Test2 label.
```

**Die Case-Anweisung**

Bezeichnungen, die nach dem **Case** -Schlüsselwort angezeigt werden, können nicht auch außerhalb einer **Switch** -Anweisung vorkommen. (Diese Einschränkung gilt auch für das **default** -Schlüsselwort.) Das folgende Code Fragment zeigt die korrekte Verwendung von **Case** -Bezeichnungen:

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );
      EndPaint( hWnd, &ps );
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-case-statement"></a>Bezeichnungen in der case-Anweisung

Bezeichnungen, die nach dem **Case** -Schlüsselwort angezeigt werden, können nicht auch außerhalb einer **Switch** -Anweisung vorkommen. (Diese Einschränkung gilt auch für das **default** -Schlüsselwort.) Das folgende Code Fragment zeigt die korrekte Verwendung von **Case** -Bezeichnungen:

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      // Obtain a handle to the device context.
      // BeginPaint will send WM_ERASEBKGND if appropriate.

      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );

      // Inform Windows that painting is complete.

      EndPaint( hWnd, &ps );
      break;

   case WM_CLOSE:
      // Close this window and all child windows.

      KillTimer( hWnd, TIMER1 );
      DestroyWindow( hWnd );
      if ( hWnd == hWndMain )
         PostQuitMessage( 0 );  // Quit the application.
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-goto-statement"></a>Bezeichnungen in der goto-Anweisung

Das Aussehen einer *bezeichnerbezeichnung* im Quell Programm deklariert eine Bezeichnung. Nur eine [goto](../cpp/goto-statement-cpp.md) -Anweisung kann die Steuerung an eine *bezeichnerbezeichnung* übertragen. Das folgende Code Fragment veranschaulicht die Verwendung der **goto** -Anweisung und eine *bezeichnerbezeichnung* :

Eine Bezeichnung kann nicht allein stehen, sondern muss immer an eine Anweisung angefügt werden. Wenn eine Bezeichnung allein benötigt wird, platzieren Sie nach ihr eine NULL-Anweisung.

Die Bezeichnung gilt funktionsweit und kann nicht innerhalb der Funktion erneut deklariert werden. Allerdings kann derselbe Name in verschiedenen Funktionen als Bezeichnung verwendet werden.

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
// At Test2 label.
}
```

## <a name="see-also"></a>Weitere Informationen

[Übersicht über C++-Anweisungen](../cpp/overview-of-cpp-statements.md)<br/>
[switch-Anweisung (C++)](../cpp/switch-statement-cpp.md)
