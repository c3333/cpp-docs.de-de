---
title: "Schwache Verweise und unterbrochene Zyklen (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
caps.latest.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 12
---
# Schwache Verweise und unterbrochene Zyklen (C++/CX)
In jedem Typsystem, dem Verweiszählung zugrunde liegt, können Verweise auf Typen *zyklisch* sein, d. h. ein Objekt kann auf ein zweites Objekt verweisen, dieses auf ein drittes Objekt, usw., bis das letzte Objekt zurück zum ersten Objekt verweist. In einem Verweiszyklus können Objekte nicht ordnungsgemäß gelöscht werden, wenn der Verweiszähler eines Objekts null wird. Zur Behebung dieses Problem stellt [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] die [Platform::WeakReference\-Klasse](../cppcx/platform-weakreference-class.md)\-Klasse bereit. Ein `WeakReference`\-Objekt unterstützt die [Resolve](../cppcx/weakreference-resolve-method-platform-namespace.md)\-Methode, die NULL zurückgibt, wenn das Objekt nicht mehr vorhanden ist, oder eine [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md)\-Ausnahme auslöst, wenn das Objekt nicht vom Typ  `T` ist.  
  
 `WeakReference` muss beispielsweise verwendet werden, wenn der `this` Zeiger in einem Lambda\-Ausdruck erfasst wird, der einen Ereignishandler definieren soll. Es wird empfohlen, benannte Methoden zu verwenden, wenn Sie Ereignishandler definieren, aber wenn Sie ein Lambda für einen Ereignishandler verwenden möchten. Wenn Sie einen Verweiszählungszyklus in einer anderer Situation unterbrechen müssen, verwenden Sie `WeakReference`. Im Folgenden ein Beispiel:  
  
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
  
 Wenn ein Ereignishandler eine `DisconnectedException` auslöst, wird der Handler aus der Abonnentenliste entfernt.  
  
## Siehe auch  
 [\(NOTINBUILD\) Weiterführende Themen](http://msdn.microsoft.com/de-de/1ccff0cf-a6cc-47ef-a05f-eba6307b3ced)