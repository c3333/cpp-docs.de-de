---
title: event (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- event
- event_cpp
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
ms.openlocfilehash: 8a0674defb0f5e81e0d1417bab5a282cf82b82b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195693"
---
# <a name="event--ccli-and-ccx"></a>event (C++/CLI und C++/CX)

Das Schlüsselwort **event** deklariert ein *Ereignis*, d.h. eine Benachrichtigung an registrierte Abonnenten (*Ereignishandler*), dass etwas geschehen ist, das für sie von Interesse ist.

## <a name="all-runtimes"></a>Alle Laufzeiten

C++/CX unterstützt das Deklarieren eines *Ereignismembers* oder eines *Ereignisblocks*. Ein Ereignismember ist die Kurzschreibweise für das Deklarieren eines Event-Blocks. Standardmäßig deklariert ein Ereignismember die Funktionen `add()`, `remove()` und `raise()`, die explizit in einem Event-Block deklariert werden. Um die Funktionen in einem Ereignismember anzupassen, deklarieren Sie stattdessen einen Event-Block und überschreiben Sie dann die Funktionen, die Sie benötigen.

### <a name="syntax"></a>Syntax

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Parameter

*Modifizierer*<br/>
Ein Modifizierer, der entweder für die Ereignisdeklaration oder eine Ereigniszugriffsmethode verwendet werden kann.  Mögliche Werte sind **`static`** und **`virtual`** .

*delegate*<br/>
Der [Delegat](delegate-cpp-component-extensions.md), mit dessen Signatur der Ereignishandler übereinstimmen muss.

*event_name*<br/>
Der Name des Ereignisses.

*return_value*<br/>
Der Rückgabewert der Ereigniszugriffsmethode.  Der Rückgabetyp muss sein, um überprüft werden zu können **`void`** .

*parameters*<br/>
(Optional) Parameter für die `raise`-Methode, die mit der Signatur des Parameters *delegate* übereinstimmen.

### <a name="remarks"></a>Bemerkungen

Ein Ereignis ist eine Zuordnung zwischen einem Delegaten und einer Memberfunktion (Ereignishandler), die auf das Auslösen des Ereignisses reagiert und es Clients beliebiger Klassen ermöglicht, Methoden zu registrieren, die mit der Signatur und dem Rückgabetyp des zugrundeliegenden Delegaten übereinstimmen.

Es gibt zwei Arten von Ereignisdeklarationen:

*event data member* (Ereignisdatenmember)<br/>
Der Compiler erstellt automatisch Speicherplatz für das Ereignis in Form eines Members des Delegattyps und erstellt interne Memberfunktionen `add()`, `remove()` und `raise()`. Ein Ereignisdatenmember muss innerhalb einer Klasse deklariert werden. Der Rückgabetyp des Rückgabetyps des Delegaten muss dem Rückgabetyp des Ereignishandlers entsprechen.

*event block* (Ereignisblock)<br/>
Ein Event-Block ermöglicht es Ihnen, das Verhalten der Methoden `add()`, `remove()` und `raise()` explizit zu deklarieren und anzupassen.

Sie können mithilfe von **operators+=** und **operator-=** einen Ereignishandler hinzufügen und entfernen oder die Methoden `add()` und `remove()` explizit aufrufen.

**event** ist ein kontextbezogenes Schlüsselwort. Weitere Informationen finden Sie unter [Kontextbezogene Schlüsselwörter](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Ereignisse (C++/CX)](../cppcx/events-c-cx.md).

Wenn Sie beabsichtigen, einen Ereignishandler hinzuzufügen und dann zu entfernen, müssen Sie die EventRegistrationToken-Struktur speichern, die durch den Vorgang des Hinzufügens zurückgegeben wird. Dann müssen Sie im Entfernungsvorgang die gespeicherte EventRegistrationToken-Struktur verwenden, um den zu entfernenden Ereignishandler zu identifizieren.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Mit dem **event**-Schlüsselwort können Sie ein Ereignis deklarieren. Ein Ereignis ist eine Methode, anhand derer eine Klasse Benachrichtigungen übermitteln kann, wenn etwas von Interesse geschieht.

### <a name="syntax"></a>Syntax

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Parameter

*Modifizierer*<br/>
Ein Modifizierer, der entweder für die Ereignisdeklaration oder eine Ereigniszugriffsmethode verwendet werden kann.  Mögliche Werte sind **`static`** und **`virtual`** .

*delegate*<br/>
Der [Delegat](delegate-cpp-component-extensions.md), mit dessen Signatur der Ereignishandler übereinstimmen muss.

*event_name*<br/>
Der Name des Ereignisses.

*return_value*<br/>
Der Rückgabewert der Ereigniszugriffsmethode.  Der Rückgabetyp muss sein, um überprüft werden zu können **`void`** .

*parameters*<br/>
(Optional) Parameter für die `raise`-Methode, die mit der Signatur des Parameters *delegate* übereinstimmen.

### <a name="remarks"></a>Bemerkungen

Ein Ereignis ist eine Zuordnung zwischen einem Delegaten und einer Memberfunktion (Ereignishandler), die auf das Auslösen des Ereignisses reagiert und es Clients beliebiger Klassen ermöglicht, Methoden zu registrieren, die mit der Signatur und dem Rückgabetyp des zugrundeliegenden Delegaten übereinstimmen.

Der Delegat kann eine oder mehrere zugeordnete Methoden haben, die aufgerufen werden, wenn der Code angibt, dass das Ereignis aufgetreten ist. Ein Ereignis in einem Programm kann für andere Programme verfügbar gemacht werden, die auf die .NET Framework Common Language Runtime abzielen.

Es gibt zwei Arten von Ereignisdeklarationen:

*event data members*<br/>
Speicher für das Ereignis in der Form eines Members des Delegattyps wird vom Compiler für Datenmemberereignisse erstellt.  Ein Ereignisdatenmember muss innerhalb einer Klasse deklariert werden. Dies wird auch als triviales Ereignis bezeichnet (siehe untenstehendes Codebeispiel).

*event blocks*<br/>
Über Ereignis-Blöcke können Sie das Verhalten der Add-, Remove- und Raise-Methoden anpassen, indem Sie Add-, Remove- und Raise-Methoden implementieren. Die Signatur der Add-, Remove- und Raise-Methoden muss mit der Signatur des Delegaten übereinstimmen.  Event-Block-Ereignisse sind keine Datenmember und jede Verwendung als Datenmember führt zu einem Compilerfehler.

Der Rückgabetyp des Ereignishandlers muss dem Rückgabetyp des Delegaten entsprechen.

In .NET Framework können Sie einen Datenmember behandeln, als wäre er eine Methode selbst (d. h. die `Invoke`-Methode des entsprechenden Delegaten). Sie müssen den Delegattyp vordefinieren, um einen verwalteten Ereignisdatenmember zu deklarieren. Im Gegensatz dazu definiert eine verwaltete Ereignismethode implizit den entsprechenden verwalteten Delegaten, sofern er noch nicht definiert ist.  Ein Codebeispiel finden Sie am Ende dieses Themas.

Wenn Sie ein verwaltetes Ereignis deklarieren, können Sie Add- und Remove-Zugriffsmethoden angeben, die aufgerufen werden, wenn Ereignishandler über die Operatoren „+=“ und „-=“ hinzugefügt oder entfernt werden. Die Add-, Remove- und Raise-Methoden können explizit aufgerufen werden.

Die folgenden Schritte müssen durchgeführt werden, um Ereignisse in Visual C++ zu erstellen und zu verwenden:

1. Erstellen oder Identifizieren eines Delegaten. Wenn Sie ein eigenes Ereignis definieren, müssen Sie auch sicherstellen, dass es einen Delegaten für die Verwendung mit dem **event**-Schlüsselwort gibt. Wenn das Ereignis vordefiniert ist, beispielsweise in .NET Framework, müssen die Consumer des Ereignisses lediglich den Namen des Delegaten kennen.

2. Erstellen Sie eine Klasse, die Folgendes enthält:

   - Ein aus dem Delegaten erstelltes Ereignis.

   - (Optional) Eine Methode, die überprüft, ob eine Instanz des mit dem **event**-Schlüsselwort deklarierten Delegaten vorhanden ist. Andernfalls muss diese Logik im Code eingefügt werden, durch den das Ereignis ausgelöst wird.

   - Methoden, die das Ereignis aufrufen. Diese Methoden können Überschreibungen von Funktionen der Basisklasse sein.

   Diese Klasse definiert das Ereignis.

3. Definieren Sie eine oder mehrere Klassen, die Methoden mit dem Ereignis verbinden. Jede dieser Klassen ordnet dem Ereignis in der Basisklasse eine oder mehrere Methoden zu.

4. Verwenden Sie das Ereignis:

   - Erstellen Sie ein Objekt der Klasse, die die Ereignisdeklaration enthält.

   - Erstellen Sie ein Objekt der Klasse, die die Ereignisdefinition enthält.

Weitere Informationen zu C++/CLI-Ereignissen finden Sie hier:

- [Ereignisse in einer Schnittstelle](../dotnet/how-to-use-events-in-cpp-cli.md)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Im folgenden Codebeispiel wird das Deklarieren von Paaren von Delegaten, Ereignissen und Ereignishandlers veranschaulicht, das Abonnieren (Hinzufügen) der Ereignishandler, das Aufrufen der Ereignishandler und dann das Kündigen des Abonnements (Entfernen) der Ereignishandler.

```cpp
// mcppv2_events.cpp
// compile with: /clr
using namespace System;

// declare delegates
delegate void ClickEventHandler(int, double);
delegate void DblClickEventHandler(String^);

// class that defines events
ref class EventSource {
public:
   event ClickEventHandler^ OnClick;   // declare the event OnClick
   event DblClickEventHandler^ OnDblClick;   // declare OnDblClick

   void FireEvents() {
      // raises events
      OnClick(7, 3.14159);
      OnDblClick("Hello");
   }
};

// class that defines methods that will called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }

   void OnMyDblClick(String^ str) {
      Console::WriteLine("OnDblClick: {0}", str);
   }
};

int main() {
   EventSource ^ MyEventSource = gcnew EventSource();
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   MyEventSource->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick += gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);

   // invoke events
   MyEventSource->FireEvents();

   // unhook handler to event
   MyEventSource->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick -= gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);
}
```

```Output
OnClick: 7, 3.14159

OnDblClick: Hello
```

Im folgenden Codebeispiel wird die Logik zum Generieren der `raise`-Methode eines trivialen Ereignisses veranschaulicht: Wenn das Ereignis einen oder mehrere Abonnenten aufweist, wird beim impliziten oder expliziten Aufrufen der `raise`-Methode der Delegat aufgerufen. Wenn der Rückgabetyp des Delegaten nicht ist **`void`** und wenn keine Ereignis Abonnenten vorhanden sind, `raise` gibt die Methode den Standardwert für den Delegattyp zurück. Wenn keine Ereignisabonnenten vorhanden sind, wird beim Aufrufen der `raise`-Methode einfach zurückgegeben und keine Ausnahme ausgelöst. Wenn der delegatrückgabetyp nicht ist **`void`** , wird der Delegattyp zurückgegeben.

```cpp
// trivial_events.cpp
// compile with: /clr /c
using namespace System;
public delegate int Del();
public ref struct C {
   int i;
   event Del^ MyEvent;

   void FireEvent() {
      i = MyEvent();
   }
};

ref struct EventReceiver {
   int OnMyClick() { return 0; }
};

int main() {
   C c;
   c.i = 687;

   c.FireEvent();
   Console::WriteLine(c.i);
   c.i = 688;

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();
   c.MyEvent += gcnew Del(MyEventReceiver, &EventReceiver::OnMyClick);
   Console::WriteLine(c.i);
}
```

```Output
0

688
```

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
