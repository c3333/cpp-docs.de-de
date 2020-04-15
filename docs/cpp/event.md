---
title: __event
ms.date: 11/04/2016
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
ms.openlocfilehash: f8935408c6e9b43347d4ad6088505a461e254ae2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366301"
---
# <a name="__event"></a>__event

Deklariert ein Ereignis.

## <a name="syntax"></a>Syntax

```
__event method-declarator;
__event __interface interface-specifier;
__event member-declarator;
```

## <a name="remarks"></a>Bemerkungen

Das Schlüsselwort **__event** kann auf eine Methodendeklaration, eine Schnittstellendeklaration oder eine Datenmemberdeklaration angewendet werden. Sie können jedoch das **Schlüsselwort __event** nicht verwenden, um einen Member einer geschachtelten Klasse zu qualifizieren.

Je nachdem, ob Ereignisquelle und Empfänger systemeigenes C++, COM oder verwaltet (.NET Framework) sind, können Sie die folgenden Konstrukte als Ereignisse verwenden:

|Systemeigenes C++|COM|Verwaltet (.NET Framework)|
|------------------|---------|--------------------------------|
|Methode|—|Methode|
|—|interface|—|
|—|—|Datenelement|

Verwenden Sie [__hook](../cpp/hook.md) in einem Ereignisempfänger, um einer Ereignismethode eine Handlermethode zuzuordnen. Beachten Sie, dass nach dem Erstellen eines Ereignisses mit dem **Schlüsselwort __event** alle Ereignishandler, die anschließend an dieses Ereignis angeschlossen sind, aufgerufen werden, wenn das Ereignis aufgerufen wird.

Eine **__event** __event-Methodendeklaration kann keine Definition haben. eine Definition wird implizit generiert, sodass die Ereignismethode aufgerufen werden kann, als wäre sie eine gewöhnliche Methode.

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="native-events"></a>Systemeigene Ereignisse

Systemeigene Ereignisse sind Methoden. Der Rückgabetyp ist in der Regel HRESULT oder **void**, kann jedoch ein beliebiger integraler Typ sein, einschließlich einer **Enumerat**. Wenn ein Ereignis einen ganzzahligen Rückgabetyp verwendet, ist für den Fall, dass ein Ereignishandler einen Wert ungleich 0 (null) zurückgibt, eine Fehlerbedingung definiert. In diesem Fall werden durch das ausgelöste Ereignis die anderen Delegaten aufgerufen.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Beispielcode finden Sie [unter Ereignisbehandlung in nativem C++.](../cpp/event-handling-in-native-cpp.md)

## <a name="com-events"></a>COM-Ereignisse

COM-Ereignisse sind Schnittstellen. Die Parameter einer Methode in einer Ereignisquellschnittstelle sollten *sich in* Parametern begeben (dies wird jedoch nicht streng erzwungen), da ein *out-Parameter* beim Multicasting nicht nützlich ist. Eine Warnung der Stufe 1 wird ausgegeben, wenn Sie einen *out-Parameter* verwenden.

Der Rückgabetyp ist in der Regel HRESULT oder **void**, kann jedoch ein beliebiger integraler Typ sein, einschließlich **enum**. Wenn ein Ereignis einen ganzzahligen Rückgabetyp verwendet und ein Ereignishandler einen Wert ungleich 0 (null) zurückgibt, handelt es sich um eine Fehlerbedingung. In diesem Fall werden durch das ausgelöste Ereignis Aufrufe anderer Delegaten abgebrochen. Beachten Sie, dass der Compiler automatisch eine Ereignisquellschnittstelle als [Quelle](../windows/attributes/source-cpp.md) in der generierten IDL markiert.

Das [__interface](../cpp/interface.md) Schlüsselwort ist immer erforderlich, nachdem **__event** für eine COM-Ereignisquelle.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Unter [Ereignisbehandlung in COM](../cpp/event-handling-in-com.md) für Beispielcode.

## <a name="managed-events"></a>Verwaltete Ereignisse

Informationen zu Codierungsereignissen in der neuen Syntax finden Sie unter [ereignis](../extensions/event-cpp-component-extensions.md).

Verwaltete Ereignisse sind Datenmember oder Methoden. Bei Verwendung mit einem Ereignis muss der Rückgabetyp eines Delegaten mit der [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components)konform sein. Der Rückgabetyp des Ereignishandlers muss dem Rückgabetyp des Delegaten entsprechen. Weitere Informationen zu Delegaten finden Sie unter [Delegaten und Ereignisse](../dotnet/delegates-and-events.md). Wenn ein verwaltetes Ereignis ein Datenmember ist, muss ihr Typ ein Zeiger auf einen Delegaten sein.

In .NET Framework können Sie einen Datenmember behandeln, als wäre er eine Methode selbst (d. h. die `Invoke`-Methode des entsprechenden Delegaten). Sie müssen den Delegattyp vordefinieren, um einen verwalteten Ereignisdatenmember zu deklarieren. Im Gegensatz dazu definiert eine verwaltete Ereignismethode implizit den entsprechenden verwalteten Delegaten, sofern er noch nicht definiert ist. Sie können beispielsweise einen Ereigniswert wie `OnClick` als Ereignis wie folgt angeben:

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Wenn Sie implizit ein verwaltetes Ereignis deklarieren, können Sie Add- und Remove-Zugriffsmethoden angeben, die aufgerufen werden, wenn Ereignishandler hinzugefügt oder entfernt werden. Sie können auch die Methode definieren, die das Ereignis außerhalb der Klasse aufruft (auslöst).

## <a name="example-native-events"></a>Beispiel: Systemeigene Ereignisse

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>Beispiel: COM-Ereignisse

```cpp
// EventHandling_COM_Event.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT MyEvent();
};
[ coclass, uuid("00000000-0000-0000-0000-000000000003"),  event_source(com) ]
class CSource : public IEventSource {
public:
   __event __interface IEventSource;
   HRESULT FireEvent() {
      __raise MyEvent();
      return S_OK;
   }
};
```

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)<br/>
[Ereignisbehandlung](../cpp/event-handling.md)<br/>
[Event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)
