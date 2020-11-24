---
title: Event-Schlüsselwort (C++/CLI und C++/CX)
description: Erfahren Sie, wie Sie das Microsoft C++ Component Extensions-Schlüsselwort verwenden `event` .
ms.date: 11/20/2020
ms.topic: reference
f1_keywords:
- event
- event_cpp
helpviewer_keywords:
- event keyword [C++]
ms.openlocfilehash: 6a2fa97140f747b4afc380b57f8f7c71f08875db
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483242"
---
# <a name="event-keyword-ccli-and-ccx"></a>`event` -Schlüsselwort (C++/CLI und C++/CX)

Mit dem- **`event`** Schlüsselwort wird ein *Ereignis* deklariert, bei dem es sich um eine Benachrichtigung an registrierte Abonnenten (*Ereignishandler*) handelt, die von Interesse ist.

## <a name="all-runtimes"></a>Alle Laufzeiten

C++/CX unterstützt das Deklarieren eines *Ereignismembers* oder eines *Ereignisblocks*. Ein Ereignismember ist die Kurzschreibweise für das Deklarieren eines Event-Blocks. Standardmäßig deklariert ein Ereignismember die Funktionen `add`, `remove` und `raise`, die explizit in einem Event-Block deklariert werden. Um die Funktionen in einem Ereignismember anzupassen, deklarieren Sie stattdessen einen Event-Block und überschreiben Sie dann die Funktionen, die Sie benötigen.

### <a name="syntax"></a>Syntax

```cpp
// event data member
modifier event delegate^ event_name;

// event block
modifier event delegate^ event_name
{
   modifier return_value add(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Parameter

*Modifizierer*\
Ein Modifizierer, der entweder für die Ereignisdeklaration oder eine Ereigniszugriffsmethode verwendet werden kann.  Mögliche Werte sind **`static`** und **`virtual`** .

*Führers*\
Der [Delegat](delegate-cpp-component-extensions.md), mit dessen Signatur der Ereignishandler übereinstimmen muss.

*event_name*\
Der Name des Ereignisses.

*return_value*\
Der Rückgabewert der Ereigniszugriffsmethode.  Der Rückgabetyp muss sein, um überprüft werden zu können **`void`** .

*Metern*\
(Optional) Parameter für die `raise`-Methode, die mit der Signatur des Parameters *delegate* übereinstimmen.

### <a name="remarks"></a>Bemerkungen

Ein Ereignis ist eine Zuordnung zwischen einem Delegaten und einem *Ereignishandler*. Ein Ereignishandler ist eine Member-Funktion, die antwortet, wenn das Ereignis ausgelöst wird. Dadurch können Clients aus beliebigen Klassen Methoden registrieren, die der Signatur und dem Rückgabetyp des Delegaten entsprechen.

Es gibt zwei Arten von Ereignisdeklarationen:

*ereignisdatenmember*\
Der Compiler erstellt automatisch Speicherplatz für das Ereignis in Form eines Members des Delegattyps und erstellt interne Memberfunktionen `add`, `remove` und `raise`. Ein Ereignisdatenmember muss innerhalb einer Klasse deklariert werden. Der Rückgabetyp des Rückgabetyps des Delegaten muss dem Rückgabetyp des Ereignishandlers entsprechen.

*Ereignisblock*\
Ein Event-Block ermöglicht es Ihnen, das Verhalten der Methoden `add`, `remove` und `raise` explizit zu deklarieren und anzupassen.

Sie können und verwenden, `operator +=` `operator -=` um einen Ereignishandler hinzuzufügen oder zu entfernen, oder die `add` -Methode und die- `remove` Methode explizit aufzurufen.

**`event`** ist ein kontextsensitiv Schlüsselwort. Weitere Informationen finden Sie unter [Kontextbezogene Schlüsselwörter](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Ereignisse (C++/CX)](../cppcx/events-c-cx.md).

Um einen Ereignishandler hinzuzufügen und zu einem späteren Zeitpunkt zu entfernen, speichern Sie die Struktur, die `EventRegistrationToken` vom Vorgang zurückgegeben wird `add` . Verwenden Sie dann im- `remove` Vorgang die gespeicherte-Struktur, `EventRegistrationToken` um den Ereignishandler zu identifizieren, der entfernt werden soll.

### <a name="requirements"></a>Anforderungen

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Mit dem **event**-Schlüsselwort können Sie ein Ereignis deklarieren. Ein Ereignis ist eine Methode, anhand derer eine Klasse Benachrichtigungen übermitteln kann, wenn etwas von Interesse geschieht.

### <a name="syntax"></a>Syntax

```cpp
// event data member
modifier event delegate^ event_name;

// event block
modifier event delegate^ event_name
{
   modifier return_value add(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Parameter

*Modifizierer*\
Ein Modifizierer, der entweder für die Ereignisdeklaration oder eine Ereigniszugriffsmethode verwendet werden kann.  Mögliche Werte sind **`static`** und **`virtual`** .

*Führers*\
Der [Delegat](delegate-cpp-component-extensions.md), mit dessen Signatur der Ereignishandler übereinstimmen muss.

*event_name*\
Der Name des Ereignisses.

*return_value*\
Der Rückgabewert der Ereigniszugriffsmethode.  Der Rückgabetyp muss sein, um überprüft werden zu können **`void`** .

*Metern*\
(Optional) Parameter für die `raise`-Methode, die mit der Signatur des Parameters *delegate* übereinstimmen.

### <a name="remarks"></a>Bemerkungen

Ein Ereignis ist eine Zuordnung zwischen einem Delegaten und einem *Ereignishandler*. Ein Ereignishandler ist eine Member-Funktion, die antwortet, wenn das Ereignis ausgelöst wird. Dadurch können Clients aus beliebigen Klassen Methoden registrieren, die der Signatur und dem Rückgabetyp des zugrunde liegenden Delegaten entsprechen.

Der Delegat kann über mindestens eine zugeordnete Methode verfügen. Diese Methoden werden aufgerufen, wenn Ihr Code angibt, dass das Ereignis aufgetreten ist. Ein Ereignis in einem Programm kann für andere Programme verfügbar gemacht werden, die auf die .NET Framework Common Language Runtime abzielen.

Es gibt zwei Arten von Ereignis Deklarationen:

*ereignisdatenmember*\
Der Compiler erstellt Speicher für Datenmember-Ereignisse als Member des Delegattyps. Ein Ereignisdatenmember muss innerhalb einer Klasse deklariert werden. Dies wird auch als *triviales Ereignis* bezeichnet. Ein Beispiel finden Sie im Codebeispiel.

*Ereignisblöcke*\
Mithilfe von Ereignisblöcken können Sie das Verhalten der `add` `remove` Methoden, und anpassen, indem Sie die Methoden, `raise` `add` und implementieren `remove` `raise` . Die Signatur der `add` Methoden, `remove` und `raise` muss mit der Signatur des Delegaten identisch sein. Ereignisse von Ereignisblöcken sind keine Datenmember. Jede Verwendung als Datenmember generiert einen Compilerfehler.

Der Rückgabetyp des Ereignishandlers muss dem Rückgabetyp des Delegaten entsprechen.

In .NET Framework können Sie einen Datenmember behandeln, als wäre er eine Methode selbst (d. h. die `Invoke`-Methode des entsprechenden Delegaten). Zu diesem Zweck müssen Sie den Delegattyp für die Deklaration eines verwalteten ereignisdatenmembers vorab definieren. Im Gegensatz dazu definiert eine verwaltete Ereignismethode implizit den entsprechenden verwalteten Delegaten, wenn er nicht bereits definiert ist. Ein Beispiel finden Sie im Codebeispiel am Ende dieses Artikels.

Wenn Sie ein verwaltetes Ereignis deklarieren, können Sie `add` -und- `remove` Accessoren angeben, die aufgerufen werden, wenn Ereignishandler mithilfe von Operatoren und hinzugefügt oder entfernt werden **`+=`** **`-=`** . Die `add` `remove` Methoden, und `raise` können explizit aufgerufen werden.

Die folgenden Schritte müssen ausgeführt werden, um Ereignisse in Microsoft C++ zu erstellen und zu verwenden:

1. Erstellen oder Identifizieren eines Delegaten. Wenn Sie ein eigenes Ereignis definieren, müssen Sie auch sicherstellen, dass es einen Delegaten gibt, der mit dem Schlüsselwort verwendet werden kann **`event`** . Wenn das Ereignis vordefiniert ist, beispielsweise in .NET Framework, müssen die Consumer des Ereignisses lediglich den Namen des Delegaten kennen.

2. Erstellen Sie eine Klasse, die Folgendes enthält:

   - Ein aus dem Delegaten erstelltes Ereignis.

   - Optionale Eine Methode, die überprüft, ob eine Instanz des Delegaten vorhanden ist, der mit dem- **`event`** Schlüsselwort deklariert wurde. Andernfalls muss diese Logik im Code eingefügt werden, durch den das Ereignis ausgelöst wird.

   - Methoden, die das Ereignis aufrufen. Diese Methoden können Überschreibungen von Funktionen der Basisklasse sein.

   Diese Klasse definiert das Ereignis.

3. Definieren Sie eine oder mehrere Klassen, die Methoden mit dem Ereignis verbinden. Jede dieser Klassen ordnet dem Ereignis in der Basisklasse eine oder mehrere Methoden zu.

4. Verwenden Sie das Ereignis:

   - Erstellen Sie ein Objekt der Klasse, die die Ereignisdeklaration enthält.

   - Erstellen Sie ein Objekt der Klasse, die die Ereignisdefinition enthält.

Weitere Informationen zu C++/CLI-Ereignissen finden Sie unter [Ereignisse in einer Schnittstelle](../dotnet/how-to-use-events-in-cpp-cli.md).

### <a name="requirements"></a>Anforderungen

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Codebeispiel veranschaulicht das Deklarieren von Paaren von Delegaten, Ereignissen und Ereignis Handlern. Es wird gezeigt, wie Sie die Ereignishandler abonnieren (hinzufügen), aufrufen und anschließend kündigen (entfernen).

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

Im folgenden Codebeispiel wird die Logik zum Generieren der- `raise` Methode eines trivialen Ereignisses veranschaulicht. Wenn mindestens ein Abonnent für das Ereignis vorhanden ist, führt der Aufruf der `raise`-Methode implizit oder explizit zum Aufruf des Delegaten. Wenn der Rückgabetyp des Delegaten nicht ist **`void`** und wenn keine Ereignis Abonnenten vorhanden sind, `raise` gibt die Methode den Standardwert für den Delegattyp zurück. Wenn keine Ereignis Abonnenten vorhanden sind, wird beim Aufrufen der `raise` -Methode sofort zurückgegeben, und es wird keine Ausnahme ausgelöst. Wenn der delegatrückgabetyp nicht ist **`void`** , wird der Delegattyp zurückgegeben.

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

## <a name="see-also"></a>Siehe auch

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)
