---
title: 'Gewusst wie: Definieren und Installieren eines globalen Ausnahmehandlers'
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: 27666702a548c0c71b7e25597a1927520968b124
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544976"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Gewusst wie: Definieren und Installieren eines globalen Ausnahmehandlers

Im folgenden Codebeispiel wird veranschaulicht, wie nicht behandelte Ausnahmen aufgezeichnet werden können. Das Beispiel Formular enthält eine Schaltfläche, die, wenn Sie gedrückt wird, einen NULL-Verweis ausführt, wodurch eine Ausnahme ausgelöst wird. Diese Funktion stellt einen typischen Code Fehler dar. Die resultierende Ausnahme wird vom Anwendungs weiten Ausnahmehandler abgefangen, der von der Main-Funktion installiert wird.

Dies wird erreicht, indem ein Delegat an das <xref:System.Windows.Forms.Application.ThreadException> Ereignis gebunden wird. In diesem Fall werden nachfolgende Ausnahmen an die `App::OnUnhandled`-Methode gesendet.

## <a name="example"></a>Beispiel

```cpp
// global_exception_handler.cpp
// compile with: /clr
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Drawing;
using namespace System::Windows::Forms;

ref class MyForm : public Form
{
   Button^ b;
public:
   MyForm( )
   {
      b = gcnew Button( );
      b->Text = "Do Null Access";
      b->Size = Drawing::Size(150, 30);
      b->Click += gcnew EventHandler(this, &MyForm::OnClick);
      Controls->Add(b);
   }
   void OnClick(Object^ sender, EventArgs^ args)
   {
      // do something illegal, like call through a null pointer...
      Object^ o = nullptr;
      o->ToString( );
   }
};

ref class App
{
public:
   static void OnUnhandled(Object^ sender, ThreadExceptionEventArgs^ e)
   {
      MessageBox::Show(e->Exception->Message, "Global Exeception");
      Application::ExitThread( );
   }
};

int main()
{
   Application::ThreadException += gcnew
      ThreadExceptionEventHandler(App::OnUnhandled);

   MyForm^ form = gcnew MyForm( );
   Application::Run(form);
}
```

## <a name="see-also"></a>Siehe auch

[Behandlung von Ausnahmen](../extensions/exception-handling-cpp-component-extensions.md)
