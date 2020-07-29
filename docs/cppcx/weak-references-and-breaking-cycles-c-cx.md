---
title: Schwache Verweise und unterbrochene Zyklen (C++/CX)
ms.date: 01/22/2017
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
ms.openlocfilehash: 04ba70c148121de520b470bd727b26e756858011
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214931"
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>Schwache Verweise und unterbrochene Zyklen (C++/CX)

In jedem Typsystem, dem Verweiszählung zugrunde liegt, können Verweise auf Typen *zyklisch*sein, d. h. ein Objekt kann auf ein zweites Objekt verweisen, dieses auf ein drittes Objekt, usw., bis das letzte Objekt zurück zum ersten Objekt verweist. In einem Verweiszyklus können Objekte nicht ordnungsgemäß gelöscht werden, wenn der Verweiszähler eines Objekts null wird. Um Sie bei der Behebung dieses Problems zu unterstützen, stellt C++/CX die [Platform:: WeakReference-Klassen](../cppcx/platform-weakreference-class.md) Klasse bereit. Ein `WeakReference` -Objekt unterstützt die [Resolve](../cppcx/platform-weakreference-class.md#resolve) -Methode, die NULL zurückgibt, wenn das Objekt nicht mehr vorhanden ist, oder eine [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) -Ausnahme auslöst, wenn das Objekt nicht vom Typ `T`ist.

Ein Szenario, in dem `WeakReference` verwendet werden muss, ist, wenn der **`this`** Zeiger in einem Lambda-Ausdruck aufgezeichnet wird, der verwendet wird, um einen Ereignishandler zu definieren. Es wird empfohlen, benannte Methoden zu verwenden, wenn Sie Ereignishandler definieren, aber wenn Sie ein Lambda für einen Ereignishandler verwenden möchten. Wenn Sie einen Verweiszählungszyklus in einer anderer Situation unterbrechen müssen, verwenden Sie `WeakReference`. Beispiel:

```

using namespace Platform::Details;
using namespace Windows::UI::Xaml;
using namespace Windows::UI::Xaml::Input;
using namespace Windows::UI::Xaml::Controls;

Class1::Class1()
{
    // Class1 has a reference to m_Page
    m_Page = ref new Page();

    // m_Page will have a reference to this Class1
    // so create a weak reference to this
    WeakReference wr(this);
    m_Page->DoubleTapped += ref new DoubleTappedEventHandler(
        [wr](Object^ sender, DoubleTappedRoutedEventArgs^ args)
    {
       // Use the weak reference to get the object
       Class1^ c = wr.Resolve<Class1>();
       if (c != nullptr)
       {
           c->m_eventFired = true;
       }
       else
       {
           // Inform the event that this handler should be removed
           // from the subscriber list
           throw ref new DisconnectedException();
       }
    });
}

}
```

Wenn ein Ereignishandler eine `DisconnectedException`auslöst, wird der Handler aus der Abonnentenliste entfernt.
