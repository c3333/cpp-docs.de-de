---
title: Unterstützen des Freethreadings im Anbieter
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: 50e05b70a782dd343031443540790697e980c994
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209542"
---
# <a name="supporting-free-threading-in-your-provider"></a>Unterstützen des Freethreadings im Anbieter

Alle OLE DB Anbieter Klassen sind Thread sicher, und Registrierungseinträge werden entsprechend festgelegt. Es empfiehlt sich, ein kostenloses Threading zu unterstützen, um ein hohes Maß an Leistung in mehr Benutzer Situationen zu gewährleisten. Damit der Anbieter Thread sicher bleibt, müssen Sie überprüfen, ob der Code ordnungsgemäß blockiert ist. Wenn Sie Daten schreiben oder speichern, muss der Zugriff mit kritischen Abschnitten blockiert werden.

Jedes OLE DB Provider-Vorlagen Objekt verfügt über einen eigenen kritischen Abschnitt. Um die Blockierung zu vereinfachen, muss jede neue Klasse, die Sie erstellen, eine Vorlagen Klasse sein, die den Namen der übergeordneten Klasse als Argument annimmt.

Im folgenden Beispiel wird gezeigt, wie Sie Ihren Code blockieren:

```cpp
template <class T>
class CMyObject<T> : public...

HRESULT MyObject::MyMethod(void)
{
   T* pT = (T*)this;      // this gets the parent class

// You don't need to do anything if you are only reading information

// If you want to write information, do the following:
   pT->Lock();         // engages critical section in the object
   ...;                // write whatever information you wish
   pT->Unlock();       // disengages the critical section
}
```

Weitere Informationen zum Schutz kritischer Abschnitte mit `Lock` und `Unlock`finden Sie unter [Multithreading: Verwenden der Synchronisierungs Klassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

Stellen Sie sicher, dass alle Methoden, die Sie überschreiben (z. b. `Execute`) Thread sicher sind.

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB-Anbietervorlagen](../../data/oledb/working-with-ole-db-provider-templates.md)
