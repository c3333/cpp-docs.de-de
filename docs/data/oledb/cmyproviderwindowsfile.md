---
title: CCustomWindowsFile
ms.date: 10/22/2018
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
ms.openlocfilehash: 103a1ce5568c6137994056e574ce8eec04511d8f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079744"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

Der Assistent erstellt eine Klasse mit einer Daten Zeile. in diesem Fall wird es als `CCustomWindowsFile`bezeichnet. Der folgende Code für `CCustomWindowsFile` wird vom Assistenten generiert und listet alle Dateien in einem Verzeichnis mit der `WIN32_FIND_DATA`-Struktur auf. `CCustomWindowsFile` erbt von der `WIN32_FIND_DATA` Struktur:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` wird die [Benutzerdaten Satz-Klasse](../../data/oledb/user-record.md) genannt, da Sie auch eine Karte enthält, die die Spalten im Rowset des Anbieters beschreibt. Die Anbieter Spalten Zuordnung enthält einen Eintrag für jedes Feld im Rowset mithilfe der PROVIDER_COLUMN_ENTRY Makros. Die Makros geben Spaltennamen, Ordinalzahl und Offset zu einem Struktur Eintrag an. Die Anbieter Spalten Einträge im obigen Code enthalten Offsets in die `WIN32_FIND_DATA` Struktur. Wenn der Consumer `IRowset::GetData`aufruft, werden die Daten in einem zusammenhängenden Puffer übertragen. Anstatt Zeigerarithmetik zu machen, können Sie mit der Zuordnung einen Datenmember angeben.

Die `CCustomRowset`-Klasse enthält auch die `Execute`-Methode. in `Execute` werden die Daten tatsächlich aus der systemeigenen Quelle gelesen. Der folgende Code zeigt die `Execute` Methode, die vom Assistenten generiert wurde. Die-Funktion verwendet die Win32-`FindFirstFile` und `FindNextFile`-APIs, um Informationen zu den Dateien im Verzeichnis abzurufen und Sie in Instanzen der `CCustomWindowsFile`-Klasse zu platzieren.

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

Das zu durchsuchende Verzeichnis wird durch `m_strCommandText`angezeigt. Diese enthält den Text, der durch die `ICommandText`-Schnittstelle im Command-Objekt dargestellt wird. Wenn kein Verzeichnis angegeben ist, wird das aktuelle Verzeichnis verwendet.

Die-Methode erstellt einen Eintrag für jede Datei (entsprechend einer Zeile) und platziert Sie im `m_rgRowData` Datenmember. Die `CRowsetImpl`-Klasse definiert den `m_rgRowData` Datenmember. Die Daten in diesem Array werden in der gesamten Tabelle angezeigt und in den Vorlagen verwendet.

## <a name="see-also"></a>Weitere Informationen

[Vom Anbieter-Assistenten generierte Dateien](../../data/oledb/provider-wizard-generated-files.md)<br/>
