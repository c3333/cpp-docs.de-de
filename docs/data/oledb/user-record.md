---
title: Benutzerdatensatz
ms.date: 05/09/2019
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: 4a8fb6c9eeee3736501a04a095bdd763de16de7d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079002"
---
# <a name="user-record"></a>Benutzerdatensatz

> [!NOTE]
> Der ATL-OLE DB-Anbieter-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

Der Benutzerdatensatz stellt den Code und die Datenstruktur bereit, die die Spaltendaten für ein Rowset repräsentieren. Ein Benutzerdatensatz kann zum Zeitpunkt der Kompilierung oder zur Laufzeit erstellt werden. Wenn Sie einen Anbieter mit dem **ATL-OLE DB-Anbieter-Assistenten** erstellen, erstellt der Assistent einen Standardbenutzereintrag. Dieser sieht so aus (vorausgesetzt, Sie haben als Anbieternamen [Kurznamen] *MyProvider* angegeben):

```cpp
class CWindowsFile:
   public WIN32_FIND_DATA
{
public:
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
  
};
```

Die OLE DB-Anbietervorlagen verarbeiten alle OLE DB-Aspekte für Interaktionen mit dem Client. Um die für eine Antwort benötigten Spaltendaten abzurufen, ruft der Anbieter die `GetColumnInfo`-Funktion auf, die Sie im Benutzerdatensatz platzieren müssen. Sie können `GetColumnInfo` im Benutzerdatensatz explizit außer Kraft setzen, z.B. durch Deklaration in der H-Datei, wie hier gezeigt wird:

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)
```

Dies entspricht:

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

Implementieren Sie anschließend `GetColumnInfo` in der CPP-Datei des Benutzerdatensatzes.

Die PROVIDER_COLUMN_MAP-Makros bieten Unterstützung beim Erstellen einer `GetColumnInfo`-Funktion:

- BEGIN_PROVIDER_COLUMN_MAP definiert den Funktionsprototyp und ein statisches Array aus `ATLCOLUMNINFO`-Strukturen.

- PROVIDER_COLUMN_ENTRY definiert und initialisiert ein einzelnes `ATLCOLUMNINFO`-Element.

- END_PROVIDER_COLUMN_MAP schließt das Array und die Funktion. Es platziert außerdem die Arrayelementanzahl im *pcCols*-Parameter.

Wenn ein Benutzerdatensatz zur Laufzeit erstellt wird, verwendet `GetColumnInfo` den *pThis*-Parameter, um einen Zeiger auf ein Rowset oder eine Befehlsinstanz abzurufen. Befehle und Rowsets müssen die `IColumnsInfo`-Schnittstelle unterstützen, damit Spalteninformationen aus diesem Zeiger verwendet werden können.

`CommandClass` und `RowsetClass` sind der Befehl und das Rowset, die den Benutzerdatensatz verwenden.

Ein ausführlicheres Beispiel zum Außerkraftsetzen von `GetColumnInfo` in einem Benutzerdatensatz finden Sie unter [Dynamisches Festlegen der an den Consumer zurückgegebenen Spalten](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Weitere Informationen

[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
