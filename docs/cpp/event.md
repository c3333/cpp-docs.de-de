---
title: __event
description: Erfahren Sie, wie Sie das Microsoft C++-Erweiterungs Schlüsselwort `__event` für die native Ereignis Behandlung verwenden.
ms.date: 11/20/2020
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.openlocfilehash: 1678699d9b66c1a49dd5ca2bb019a6229c37a031
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483138"
---
# <a name="__event-keyword"></a>`__event` Schlüsselwort

Deklariert ein Ereignis.

> [!NOTE]
> Ereignis Attribute in nativem C++ sind mit Standard-C++ nicht kompatibel. Sie werden nicht kompiliert, wenn Sie den [`/permissive-`](../build/reference/permissive-standards-conformance.md) Konformitäts Modus angeben.

## <a name="syntax"></a>Syntax

> **`__event`** *`member-function-declarator`* **`;`**\
> **`__event`** **`__interface`** *`interface-specifier`* **`;`**\
> **`__event`** *`data-member-declarator`* **`;`**

## <a name="remarks"></a>Bemerkungen

Das Microsoft-spezifische Schlüsselwort **`__event`** kann auf eine Element Funktionsdeklaration, eine Schnittstellen Deklaration oder eine Datenmember-Deklaration angewendet werden. Allerdings können Sie das- **`__event`** Schlüsselwort nicht verwenden, um einen Member einer-Klasse zu qualifizieren.

Je nachdem, ob Ereignisquelle und Empfänger systemeigenes C++, COM oder verwaltet (.NET Framework) sind, können Sie die folgenden Konstrukte als Ereignisse verwenden:

| Systemeigenes C++ | COM | Verwaltet (.NET Framework) |
|--|--|--|
| Memberfunktion | - | method |
| - | interface | - |
| - | - | Datenelement |

Verwenden [`__hook`](../cpp/hook.md) Sie in einem Ereignis Empfänger, um eine handlermember-Funktion einer Ereignismember-Funktion zuzuordnen. Nachdem Sie ein Ereignis mit dem **`__event`** Schlüsselwort erstellt haben, werden alle an dieses Ereignis angehängten Ereignishandler aufgerufen, wenn das Ereignis aufgerufen wird.

Eine **`__event`** Member-Funktionsdeklaration darf keine Definition aufweisen. eine Definition wird implizit generiert, sodass die Ereignismember-Funktion aufgerufen werden kann, als ob Sie eine normale Element Funktion wäre.

> [!NOTE]
> Eine auf Vorlagen basierende Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="native-events"></a>Native Ereignisse

Native Ereignisse sind Element Funktionen. Der Rückgabetyp ist normalerweise `HRESULT` oder **`void`** , kann jedoch ein beliebiger ganzzahliger Typ sein, einschließlich **`enum`** . Wenn ein Ereignis einen ganzzahligen Rückgabetyp verwendet, wird eine Fehlerbedingung definiert, wenn ein Ereignishandler einen Wert ungleich 0 (null) zurückgibt. In diesem Fall ruft das Ereignis, das ausgelöst wird, die anderen Delegaten auf.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Beispielcode finden Sie [unter Ereignis Behandlung in nativem C++](../cpp/event-handling-in-native-cpp.md) .

## <a name="com-events"></a>COM-Ereignisse

COM-Ereignisse sind Schnittstellen. Die Parameter einer Member-Funktion in einer Ereignis Quell Schnittstelle sollten *in* Parametern vorliegen, aber Sie werden nicht streng erzwungen. Der Grund hierfür ist *,* dass ein out-Parameter beim Multicasting nicht nützlich ist. Wenn Sie einen out-Parameter verwenden *,* wird eine Warnung der Stufe 1 ausgegeben.

Der Rückgabetyp ist normalerweise `HRESULT` oder **`void`** , kann jedoch ein beliebiger ganzzahliger Typ sein, einschließlich **`enum`** . Wenn ein Ereignis einen integralen Rückgabetyp verwendet und ein Ereignishandler einen Wert ungleich 0 (null) zurückgibt, handelt es sich um eine Fehlerbedingung. Das Ereignis, das ausgelöst wird, bricht die Aufrufe der anderen Delegaten ab. Der Compiler markiert eine Ereignis Quell Schnittstelle automatisch als [`source`](../windows/attributes/source-cpp.md) in der generierten IDL.

Das [`__interface`](../cpp/interface.md) Schlüsselwort ist nach **`__event`** für eine com-Ereignis Quelle immer erforderlich.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Beispielcode finden Sie [unter Ereignis Behandlung in com](../cpp/event-handling-in-com.md) .

## <a name="managed-events"></a>Verwaltete Ereignisse

Weitere Informationen zum Codieren von Ereignissen in der neuen Syntax finden Sie unter [Event](../extensions/event-cpp-component-extensions.md).

Verwaltete Ereignisse sind Datenmember oder Element Funktionen. Bei Verwendung mit einem Ereignis muss der Rückgabetyp eines Delegaten mit dem [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components)kompatibel sein. Der Rückgabetyp des Ereignishandlers muss dem Rückgabetyp des Delegaten entsprechen. Weitere Informationen zu Delegaten finden Sie unter Delegaten [und Ereignisse](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md). Wenn ein verwaltetes Ereignis ein Datenmember ist, muss ihr Typ ein Zeiger auf einen Delegaten sein.

In .NET Framework können Sie einen Datenmember behandeln, als wäre er eine Methode selbst (d. h. die `Invoke`-Methode des entsprechenden Delegaten). Zu diesem Zweck müssen Sie den Delegattyp für die Deklaration eines verwalteten ereignisdatenmembers vorab definieren. Im Gegensatz dazu definiert eine verwaltete Ereignismethode implizit den entsprechenden verwalteten Delegaten, wenn er nicht bereits definiert ist. Sie können beispielsweise einen Ereigniswert wie `OnClick` als Ereignis wie folgt angeben:

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Wenn Sie implizit ein verwaltetes Ereignis deklarieren, können Sie `add` -und- `remove` Accessoren angeben, die aufgerufen werden, wenn Ereignishandler hinzugefügt oder entfernt werden. Sie können auch die Member-Funktion definieren, die das Ereignis von außerhalb der Klasse aufruft (löst das Ereignis aus).

## <a name="example-native-events"></a>Beispiel: Native Ereignisse

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>Beispiel: com-Ereignisse

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

[Keywords](../cpp/keywords-cpp.md)\
[Ereignis Behandlung](../cpp/event-handling.md)\
[`event_source`](../windows/attributes/event-source.md)\
[`event_receiver`](../windows/attributes/event-receiver.md)\
[`__hook`](../cpp/hook.md)\
[`__unhook`](../cpp/unhook.md)\
[`__raise`](../cpp/raise.md)
