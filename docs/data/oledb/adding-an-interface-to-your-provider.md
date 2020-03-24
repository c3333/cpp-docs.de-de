---
title: Hinzufügen einer Schnittstelle zum Anbieter
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: b13d1224388dc7d3218dea1c70b5aa8a595fcbdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212330"
---
# <a name="adding-an-interface-to-your-provider"></a>Hinzufügen einer Schnittstelle zum Anbieter

> [!NOTE]
> Der ATL-OLE DB-Anbieter-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

Bestimmen Sie, welchem Objekt Sie die Schnittstelle hinzufügen möchten (in der Regel Datenquellen-, Rowset-, Befehls- oder Sitzungsobjekte, die vom **OLE DB-Anbieter-Assistent** erstellt werden). Es kann passieren, dass das Objekt, dem Sie die Schnittstelle hinzufügen müssen, von Ihrem Anbieter noch nicht unterstützt wird. Führen Sie in diesem Fall den **ATL-OLE DB-Anbieter-Assistenten** aus, um das Objekt zu erstellen. Klicken Sie in der **Klassenansicht** mit der rechten Maustaste auf das Projekt. Klicken Sie im Kontextmenü auf **Hinzufügen** > **Neues Element**, und wählen Sie **Installiert** > **Visual C++**  > **ATL** aus. Klicken Sie dann auf **ATL-OLE DB-Anbieter**. Möglicherweise ist es eine gute Idee, den Schnittstellencode in einem separaten Verzeichnis zu speichern und die Dateien dann in Ihr Anbieterprojekt zu kopieren.

Wenn Sie eine neue Klasse erstellt haben, um die Schnittstelle zu unterstützen, legen Sie das Objekt so fest, dass es von dieser Klasse erbt. Sie können z.B. die Klasse `IRowsetIndexImpl` zu einem Rowsetobjekt hinzufügen:

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

Fügen Sie die Schnittstelle mit dem COM_INTERFACE_ENTRY-Makro zu COM_MAP im Objekt hinzu. Wenn keine Zuordnung vorhanden ist, erstellen Sie eine. Beispiel:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Verketten Sie für das Rowsetobjekt die Zuordnung des übergeordneten Objekts, sodass das Objekt an die übergeordnete Klasse delegieren kann. In diesem Beispiel fügen Sie das COM_INTERFACE_ENTRY_CHAIN-Makro zur Zuordnung hinzu:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB-Anbietervorlagen](../../data/oledb/working-with-ole-db-provider-templates.md)
