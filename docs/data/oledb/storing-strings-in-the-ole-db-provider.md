---
title: Speichern von Zeichenfolgen im OLE DB-Anbieter
ms.date: 05/09/2019
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: 1d6d2b73495d5ca6e275b13ed3c430f8169179d4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079109"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Speichern von Zeichenfolgen im OLE DB-Anbieter

> [!NOTE]
> Der ATL-OLE DB-Anbieter-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

In „*Custom*RS.h“ erstellt der **ATL-OLE DB-Anbieter-Assistent** einen Standardbenutzereintrag namens `CWindowsFile`. Um die beiden Zeichenfolgen zu behandeln, ändern Sie `CWindowsFile` wie im folgenden Code gezeigt:

```cpp
////////////////////////////////////////////////////////////////////////
class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
DWORD dwBookmark;
static const int iSize = 256;    // Add this
TCHAR szCommand[iSize];          // Add this
TCHAR szText[iSize];             // Add this
TCHAR szCommand2[iSize];         // Add this
TCHAR szText2[iSize];            // Add this

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)

   PROVIDER_COLUMN_ENTRY_STR("Command", 6, szCommand)    // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text", 7, szText)          // Add this
   PROVIDER_COLUMN_ENTRY_STR("Command2", 8, szCommand2)  // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text2", 9, szText2)        // Add this
END_PROVIDER_COLUMN_MAP()

   bool operator==(const CCustomWindowsFile& am) // This is optional
   {
      return (lstrcmpi(cFileName, am.cFileName) == 0);
   }
};
```

Die Datenelemente `szCommand` und `szText` stellen die zwei Zeichenfolgen dar, wobei `szCommand2` und `szText2` bei Bedarf zusätzliche Spalten haben. Das Datenelement `dwBookmark` ist für diesen einfachen schreibgeschützten Anbieter nicht erforderlich, wird aber später verwendet, um eine `IRowsetLocate`-Schnittstelle hinzuzufügen; siehe [Erweitern des einfachen schreibgeschützten Anbieters](../../data/oledb/enhancing-the-simple-read-only-provider.md). Der `==`-Operator vergleicht Instanzen (Implementierung dieses Operators ist optional).

Wenn dies abgeschlossen ist, können Sie die Funktionalität des [Einlesens von Zeichenfolgen in den OLE DB-Anbieter](../../data/oledb/reading-strings-into-the-ole-db-provider.md) hinzufügen.

## <a name="see-also"></a>Weitere Informationen

[Implementieren des einfachen schreibgeschützten Anbieters](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
