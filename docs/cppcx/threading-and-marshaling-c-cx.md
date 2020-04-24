---
title: Threading und Marshalling (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: 6b57366df5f466ffe49e4c0b46e05b1eed515535
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032485"
---
# <a name="threading-and-marshaling-ccx"></a>Threading und Marshalling (C++/CX)

In den allermeisten Fällen kann von jedem Thread aus auf Instanzen von Windows-Runtime-Klassen zugegriffen werden, z. B. auf Standard-C++-Objekte. Solche Klassen werden als "agil" bezeichnet. Eine kleine Anzahl von Windows-Runtime-Klassen, die mit Windows ausgeliefert werden, sind jedoch nicht agil und müssen mehr wie COM-Objekte als Standard-C++-Objekte verbraucht werden. Sie müssen zwar kein COM-Experte sein, um nicht agile Klassen zu verwenden, aber das Threadmodell dieser Klassen sowie ihr Marshallingverhalten beachten. Dieser Artikel ist ein Leitfaden für die seltenen Fälle, in denen Sie die Instanz einer nicht agilen Klasse verarbeiten müssen.

## <a name="threading-model-and-marshaling-behavior"></a>Threadmodell und Marshallingverhalten

Eine Windows-Runtime-Klasse kann den gleichzeitigen Threadzugriff auf verschiedene Weise unterstützen, wie durch zwei Attribute angezeigt wird, die darauf angewendet werden:

- Das Attribut`ThreadingModel` kann einen der Werte STA, MTA oder Both besitzen, die durch die Enumeration `ThreadingModel` definiert werden.

- Das Attribut`MarshallingBehavior` kann einen der Werte Agile, None oder Standard besitzen, die durch die Enumeration `MarshallingType` definiert werden.

Das Attribut `ThreadingModel` gibt an, wo die Klasse bei der Aktivierung geladen wird: Nur in einem Benutzeroberflächenthread-Kontext (STA), nur in einem Hintergrundthread-Kontext (MTA) oder im Kontext des Threads, der das Objekt erstellt (Both). Die Werte des `MarshallingBehavior` -Attributs beziehen sich darauf, wie sich das Objekt im jeweiligen Threadkontext verhält. In den meisten Fällen benötigen Sie keine Kenntnisse über diese Details.  Von den Klassen, die von der Windows-API bereitgestellt werden, haben ungefähr 90 Prozent `ThreadingModel`=Both und `MarshallingType`=Agile. Das bedeutet, dass sie Threadingdetails auf niedriger Ebene transparent und effizient verarbeiten können.   Wenn Sie `ref new` verwenden, um eine "agile" Klasse zu erstellen, können Sie Methoden dafür aus dem Haupt-App-Thread oder aus einem oder mehreren Arbeitsthreads aufrufen.  Das heißt, Sie können von jeder Stelle im Code aus eine agile Klasse verwenden – unabhängig davon, ob sie von Windows oder von einem Drittanbieter bereitgestellt wird. Sie müssen nicht auf das Threadingmodell oder das Marshallingverhalten der Klasse achten.

## <a name="consuming-windows-runtime-components"></a>Verwenden von Windows-Runtime-Komponenten

Wenn Sie eine universelle Windows-Plattform-App erstellen, können Sie sowohl mit agilen als auch mit nicht agilen Komponenten interagieren. Wenn Sie mit nicht agilen Komponenten interagieren, wird möglicherweise die folgende Warnung angezeigt.

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Compilerwarnung C4451 beim Verwenden nicht agiler Klassen

Aus verschiedenen Gründen können einige Klassen nicht agil sein. Wenn Sie auf Instanzen von nicht agilen Klassen sowohl über einen Benutzeroberflächenthread als auch über einen Hintergrundthread zugreifen, achten Sie besonders darauf, das richtige Verhalten zur Laufzeit sicherzustellen. Der Microsoft C++-Compiler gibt Warnungen aus, wenn Sie eine nicht agile Laufzeitklasse in Ihrer App im globalen Bereich instanziieren oder einen nicht agilen Typ als Klassenmember in einer Verweisklasse deklarieren, die selbst als agil markiert ist.

Von den nicht agilen Klassen sind diejenigen am einfachsten zu behandeln, die `ThreadingModel`=Both und `MarshallingType`=Standard haben.  Sie können diese Klassen agil machen, indem Sie einfach die Hilfsklasse `Agile<T>` verwenden.   Das folgende Beispiel zeigt eine Deklaration eines nicht agilen Objekts des Typs `Windows::Security::Credentials::UI::CredentialPickerOptions^`und die Compilerwarnung, die infolgedessen ausgegeben wird.

```

ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return _myOptions;
            }
        }
    private:
        Windows::Security::Credentials::UI::CredentialPickerOptions^ _myOptions;
    };
```

Hier ist die Warnung, die ausgegeben wird:

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

Wenn Sie im Member- oder im globalen Gültigkeitsbereich zu einem Objekt einen Verweis hinzufügen, der das Marshallingverhalten "Standard" hat, gibt der Compiler eine Warnung aus, die Sie auffordert, den Typ stattdessen in `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` zu umschließen. Wenn Sie `Agile<T>`verwenden, können Sie die Klasse wie jede andere agile Klasse nutzen. Verwenden Sie in diesem Fall `Platform::Agile<T>` :

- Die nicht agile Variable wird im globalen Gültigkeitsbereich deklariert.

- Die nicht agile Variable wird im Klassengültigkeitsbereich deklariert, und es besteht die Möglichkeit, dass verwendeter Code den Zeiger einschmuggelt, d. h. ihn in einem anderen Apartment ohne das richtige Marshalling verwendet.

Ist keine dieser Bedingungen zutreffend, können Sie die enthaltende Klasse als nicht agil markieren. Mit anderen Worten, Sie sollten nicht-agile Objekte direkt nur in nicht-agilen Klassen\<und nicht-agile Objekte über Platform::Agile T> in agilen Klassen halten.

Im folgenden Beispiel wird gezeigt, wie Sie `Agile<T>` verwenden müssen, damit Sie die Warnung sicher ignorieren können.

```

#include <agile.h>
ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return m_myOptions.Get();
            }
        }
    private:
        Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions^> m_myOptions;

    };
```

Beachten Sie, dass `Agile` nicht als Rückgabewert oder Parameter in einer Verweisklasse übergeben werden kann. Die Methode `Agile<T>::Get()` gibt ein "handle-to-object" (^) zurück, das Sie über die Anwendungsbinärdateischnittstelle (ABI) in einer öffentlichen Methode oder Eigenschaft übergeben können.

Wenn Sie einen Verweis auf eine Windows-Runtime-Klasse in proc erstellen, die ein Marshallingverhalten von "Keine" aufweist, `Platform::Agile<T>`gibt der Compiler die Warnung C4451 aus, schlägt jedoch nicht vor, dass Sie die Verwendung in Betracht ziehen.  Der Compiler kann über diese Warnung hinaus keine Hilfe anbieten, sodass es in Ihrer Verantwortung liegt, die Klasse richtig zu verwenden und sicherzustellen, dass der Code STA-Komponenten nur aus dem Benutzeroberflächenthread und MTA-Komponenten nur aus einem Hintergrundthread aufruft.

## <a name="authoring-agile-windows-runtime-components"></a>Erstellen agiler Windows-Runtime-Komponenten

Wenn Sie eine Ref-Klasse in C++/CX definieren, ist sie `ThreadingModel`standardmäßig agil, d. h. sie hat =Beide und `MarshallingType`=Agile.  Wenn Sie die Windows-Runtime-C++-Vorlagenbibliothek verwenden, können Sie Ihre `FtmBase`Klasse agil gestalten, indem Sie von von ableiten, der die `FreeThreadedMarshaller`verwendet.  Wenn Sie eine Klasse erstellen, die `ThreadingModel`=Both oder `ThreadingModel`=MTA hat, überprüfen Sie, ob die Klasse threadsicher ist.

Sie können das Threadingmodell und das Marshallingverhalten einer Verweisklasse ändern. Wenn Sie Änderungen vornehmen, die die Klasse zu "nicht agil" rendern, müssen Sie die Auswirkungen verstehen, die mit diesen Änderungen verbunden sind.

Das folgende Beispiel zeigt, wie Sie eine Laufzeitklasse in einer Windows-Runtime-Klassenbibliothek anwenden `MarshalingBehavior` und `ThreadingModel` Attribute zuweisen. Wenn eine App die DLL verwendet und das Schlüsselwort `ref new` benutzt, um ein `MySTAClass` -Klassenobjekt zu aktivieren, ist das Objekt in einem Singlethread-Apartment aktiviert und unterstützt kein Marshalling.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

In einer unversiegelten Klasse müssen die Marshalling- und Threadingattribute festgelegt sein, damit der Compiler überprüfen kann, ob abgeleitete Klassen für diese Attribute den gleichen Wert haben. Wenn die Klasse diese Einstellungen nicht aufweist, generiert der Compiler einen Fehler, und es findet keine Kompilierung statt. Jede Klasse, die von einer unversiegelten Klasse abgeleitet ist, generiert in den folgenden Fällen einen Compilerfehler:

- Die Attribute `ThreadingModel` und `MarshallingBehavior` sind in der abgeleiteten Klasse nicht definiert.

- Die Werte der Attribute `ThreadingModel` und `MarshallingBehavior` stimmen in der abgeleiteten Klasse nicht mit denen in der Basisklasse überein.

Die Threading- und Marshallinginformationen, die von einer Windows-Runtime-Komponente eines Drittanbieters benötigt werden, werden in den App-Manifestregistrierungsinformationen für die Komponente angegeben. Es wird empfohlen, alle Windows-Runtime-Komponenten agil zu gestalten. Dadurch wird sichergestellt, dass Clientcode die Komponente von jedem Thread in der App aufrufen kann. Außerdem wird dadurch die Leistung dieser Aufrufe verbessert, da sie direkte Aufrufe sind, die kein Marshalling haben. Wenn Sie die Klasse auf diese Weise erstellen, braucht Clientcode `Platform::Agile<T>` nicht zu verwenden, um die Klasse zu nutzen.

## <a name="see-also"></a>Weitere Informationen

[ThreadingModel](/uwp/api/windows.foundation.metadata.threadingmodel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
