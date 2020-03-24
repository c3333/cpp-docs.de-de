---
title: Benutzerdatensätze
ms.date: 05/09/2019
f1_keywords:
- COLUMN_ENTRY_MAP
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
ms.openlocfilehash: 94a70b48793d44eda4fd76d9b59460418cfbc032
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209442"
---
# <a name="user-records"></a>Benutzerdatensätze

> [!NOTE]
> Der ATL-OLE DB-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können diese Funktionalität weiterhin manuell hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Consumers ohne Assistent](creating-a-consumer-without-using-a-wizard.md).

Um einen statischen Accessor (d.h. einen von `CAccessor` abgeleiteten Accessor) zu verwenden, muss der Consumer über einen Benutzerdatensatz verfügen. Der Benutzerdatensatz ist eine C++-Klasse, die Datenelemente zum Verarbeiten von Ein- oder Ausgabe enthält. Der **ATL-OLE DB-Consumer-Assistent** generiert einen Benutzerdatensatz für den Consumer. Sie können dem Benutzerdatensatz Methoden für optionale Aufgaben wie das Behandeln von Kommentaren hinzufügen.

Der folgende Code zeigt einen Beispieldatensatz, der Befehle behandelt. Im Benutzerdatensatz repräsentiert BEGIN_COLUMN_MAP ein Datenrowset, das dem Consumer von einem Anbieter übergeben wird. BEGIN_PARAM_MAP stellt einen Satz von Befehlsparametern dar. In diesem Beispiel wird eine [CCommand](../../data/oledb/ccommand-class.md)-Klasse verwendet, um die Befehlsparameter zu behandeln. Die Datenmember in den Zuordnungseinträgen stellen Offsets in einen zusammenhängenden Arbeitsspeicherblock für jede Instanz der Klasse dar. Die COLUMN_ENTRY-Makros entsprechen den PROVIDER_COLUMN_ENTRY-Makros auf der Anbieterseite.

Weitere Informationen zu den Makros COLUMN_MAP und PARAM_MAP finden Sie unter [Macros for OLE DB Consumer Templates](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md) (Makros für OLE DB-Consumervorlagen).

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="wizard-generated-user-records"></a>Vom Assistenten generierte Benutzerdatensätze

Wenn Sie den **ATL OLE DB-Consumer-Assistenten** zum Erstellen eines Consumers verwenden, haben Sie die Wahl, ob Sie OLE DB-Vorlagen oder OLE DB-Attribute verwenden möchten. Der generierte Code ist in beiden Fällen unterschiedlich. Weitere Informationen zu diesem Code finden Sie unter [Vom Consumer-Assistenten generierte Klassen](../../data/oledb/consumer-wizard-generated-classes.md).

## <a name="user-record-support-for-multiple-accessors"></a>Benutzerdatensatzunterstützung für mehrere Accessoren

Weitere Informationen zu den Szenarien, in denen Sie mehrere Accessoren verwenden müssen, finden Sie unter [Verwenden mehrerer Zugriffsmethoden für ein Rowset](../../data/oledb/using-multiple-accessors-on-a-rowset.md).

Im folgenden Beispiel wird der Benutzerdatensatz geändert, sodass mehrere Accessoren für das Rowset unterstützt werden. Anstelle von BEGIN_COLUMN_MAP und END_COLUMN_MAP werden [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) und [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) für jeden Accessor verwendet. Das BEGIN_ACCESSOR-Makro gibt die Accessorzahl (Offset von 0 (null)) an, und ob der Accessor ein Autoaccessor ist. Autoaccessoren rufen `GetData` auf, um Daten automatisch bei einem Aufruf von [MoveNext](../../data/oledb/crowset-movenext.md) abzurufen. Bei nicht automatischen Accessoren müssen Sie die Daten explizit abrufen. Verwenden Sie einen nicht automatischen Accessor bei der Bindung eines großen Datenfelds (z.B. eines Bitmapbilds), das Sie nicht für jeden Datensatz abrufen möchten.

```cpp
class CMultiArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor
    COLUMN_ENTRY(1, m_szFirstName)
    COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor
    COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)
