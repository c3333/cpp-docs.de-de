---
title: CEnumerator-Klasse
ms.date: 11/04/2016
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
ms.openlocfilehash: d0fa5f381dba4f67934007d59dbdaf4450bcfb60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211795"
---
# <a name="cenumerator-class"></a>CEnumerator-Klasse

Verwendet ein OLE DB Enumeratorobjekt, das die [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) -Schnittstelle zum Zurückgeben eines Rowsets verfügbar macht, das alle Datenquellen und Enumeratoren beschreibt.

## <a name="syntax"></a>Syntax

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

|||
|-|-|
|[Suchen](#find)|Durchsucht die verfügbaren Anbieter (Datenquellen) mit dem angegebenen Namen.|
|[GetMoniker](#getmoniker)|Ruft die `IMoniker`-Schnittstelle für den aktuellen Datensatz ab.|
|[Öffnen](#open)|Öffnet den Enumerator.|

## <a name="remarks"></a>Bemerkungen

Sie können die `ISourcesRowset` Daten indirekt von dieser Klasse abrufen.

## <a name="cenumeratorfind"></a><a name="find"></a>Cenzuerator:: Find

Sucht unter Verfügbare Anbieter nach einem angegebenen Namen.

### <a name="syntax"></a>Syntax

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>Parameter

*szsearchname*<br/>
in Der Name, nach dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

**true** , wenn der Name gefunden wurde. Andernfalls lautet der Wert **false**.

### <a name="remarks"></a>Bemerkungen

Dieser Name wird dem `SOURCES_NAME`-Member der [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) -Schnittstelle zugeordnet.

## <a name="cenumeratorgetmoniker"></a><a name="getmoniker"></a>Cenenerator:: getmoniker

Analysiert den anzeigen Amen, um die Komponente der Zeichenfolge zu extrahieren, die in einen Moniker konvertiert werden kann.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>Parameter

*ppmoniker*<br/>
vorgenommen Der Moniker, der aus dem anzeigen Amen ([ceneneratoraccessor:: m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) der aktuellen Zeile analysiert wurde.

*lpszdisplayname*<br/>
in Der anzuteilbare Anzeige Name.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cenumeratoropen"></a><a name="open"></a>Centoerator:: Open

Bindet den Moniker für den Enumerator, wenn ein solcher angegeben ist, und ruft dann das Rowset für den Enumerator durch Aufrufen von [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85))ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>Parameter

*pmoniker*<br/>
in Ein Zeiger auf einen Moniker für einen Enumerator.

*pclsid*<br/>
in Ein Zeiger auf die `CLSID` eines Enumerators.

*enumerator*<br/>
in Ein Verweis auf einen Enumerator.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="see-also"></a>Weitere Informationen

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
