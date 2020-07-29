---
title: CRowsetImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
- CRowsetImpl::m_strCommandText
- CRowsetImpl.m_strCommandText
- CRowsetImpl::m_strIndexText
- CRowsetImpl.m_strIndexText
helpviewer_keywords:
- CRowsetImpl class
- NameFromDBID method
- SetCommandText method
- GetColumnInfo method
- GetCommandFromID method
- ValidateCommandID method
- m_rgRowData
- m_strCommandText
- m_strIndexText
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
ms.openlocfilehash: 35a80503597b7e59ec10618b9c8e18e0e69f018e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221509"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl-Klasse

Stellt eine standardmäßige OLE DB-rowsetimplementierung bereit, ohne dass eine mehrfache Vererbung vieler Implementierungs Schnittstellen erforderlich ist.

## <a name="syntax"></a>Syntax

```cpp
template <
   class T,
   class Storage,
   class CreatorClass,
   class ArrayType = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class RowsetInterface = IRowsetImpl <T, IRowset>
>
class CRowsetImpl :
   public CComObjectRootEx<CreatorClass::_ThreadModel>,
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die Klasse des Benutzers, die von abgeleitet wird `CRowsetImpl` .

*Storage*<br/>
Die Benutzerdaten Satz-Klasse.

*"Kreatorclass"*<br/>
Die Klasse, die Eigenschaften für das Rowset enthält. in der Regel der Befehl.

*ArrayType*<br/>
Die Klasse, die als Speicher für die Daten des Rowsets fungiert. Dieser Parameter ist standardmäßig `CAtlArray` , kann jedoch jede Klasse sein, die die erforderliche Funktionalität unterstützt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[NameFromDBID](#namefromdbid)|Extrahiert eine Zeichenfolge aus einer `DBID` und kopiert sie in das an *BSTR über gegebene BSTR* .|
|[SetCommandText](#setcommandtext)|Überprüft und speichert die `DBID` s in den beiden Zeichen folgen ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) und [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|

### <a name="overridable-methods"></a>Über schreibbare Methoden

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Ruft Spalten Informationen für eine bestimmte Client Anforderung ab.|
|[GetCommandFromID](#getcommandfromid)|Prüft, ob einer oder beide Parameter Zeichen folgen Werte enthalten. wenn dies der Fall ist, werden die Zeichen folgen Werte in die Datenelemente [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) und [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)kopiert.|
|[ValidateCommandID](#validatecommandid)|Prüft, ob eine oder beide `DBID` s Zeichen folgen Werte enthalten. wenn dies der Fall ist, werden Sie in die Datenmember [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) und [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)kopiert.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_rgRowData](#rgrowdata)|Standardmäßig eine, `CAtlArray` die eine Vorlage für das Benutzerdaten Satz-Vorlagen Argument für vorweist `CRowsetImpl` . Eine weitere arraytypklasse kann verwendet werden, indem das `ArrayType` Vorlagen Argument in geändert wird `CRowsetImpl` .|
|[m_strCommandText](#strcommandtext)|Enthält den anfänglichen Befehl des Rowsets.|
|[m_strIndexText](#strindextext)|Enthält den Anfangs Index des Rowsets.|

## <a name="remarks"></a>Bemerkungen

`CRowsetImpl`stellt über Schreibungen in Form von statischen Upcasts bereit. Die Methoden steuern die Art und Weise, in der ein bestimmtes Rowset Befehls Text überprüft. Sie können eine eigene Klasse erstellen, `CRowsetImpl` indem Sie Ihre Implementierungs Schnittstellen mehrfach geerbt machen. Die einzige Methode, für die Sie die Implementierung bereitstellen müssen, ist `Execute` . Abhängig vom Typ des Rowsets, das Sie erstellen, erwarten die Ersteller-Methoden verschiedene Signaturen für `Execute` . Wenn Sie z. b. eine von `CRowsetImpl` abgeleitete Klasse zum Implementieren eines Schemarowsets verwenden, weist die- `Execute` Methode die folgende Signatur auf:

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

Wenn Sie eine `CRowsetImpl` von abgeleitete Klasse erstellen, um das Rowset eines Befehls oder einer Sitzung zu implementieren, weist die `Execute` Methode die folgende Signatur auf:

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

Um eine der von `CRowsetImpl` abgeleiteten Methoden zu implementieren `Execute` , müssen Sie die internen Datenpuffer ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)) auffüllen.

## <a name="crowsetimplnamefromdbid"></a><a name="namefromdbid"></a>Crowabtimpl:: namefromdbid

Extrahiert eine Zeichenfolge aus einer `DBID` und kopiert sie in das an *BSTR über gegebene BSTR* .

### <a name="syntax"></a>Syntax

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>Parameter

*pdbid*<br/>
in Ein Zeiger auf das, `DBID` aus dem eine Zeichenfolge extrahiert werden soll.

*bstr*<br/>
in Ein [CComBSTR](../../atl/reference/ccombstr-class.md) -Verweis, um eine Kopie der `DBID` Zeichenfolge zu platzieren.

*bindex*<br/>
[in] **`true`** , wenn ein Index `DBID` ;, **`false`** Wenn eine Tabelle ist `DBID` .

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard. Abhängig davon, ob `DBID` eine Tabelle oder ein Index (durch *bindex*bezeichnet) ist, gibt die Methode entweder DB_E_NOINDEX oder DB_E_NOTABLE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von den `CRowsetImpl` Implementierungen von [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) und [getcommandfromid](../../data/oledb/crowsetimpl-getcommandfromid.md)aufgerufen.

## <a name="crowsetimplsetcommandtext"></a><a name="setcommandtext"></a>CRowsetImpl:: SetCommandText

Überprüft und speichert die `DBID` s in den beiden Zeichen folgen ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) und [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).

### <a name="syntax"></a>Syntax

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parameter

*pTableID*<br/>
in Ein Zeiger auf den, der `DBID` die Tabellen-ID darstellt.

*pIndexID*<br/>
in Ein Zeiger auf den, der `DBID` die Index-ID darstellt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Die- `SetCommentText` Methode wird von `CreateRowset` , einer statischen Vorlagen basierten Methode von, aufgerufen `IOpenRowsetImpl` .

Diese Methode delegiert ihre Arbeit, indem [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) und [getcommandfromid](../../data/oledb/crowsetimpl-getcommandfromid.md) über einen upcasted-Zeiger aufgerufen werden.

## <a name="crowsetimplgetcolumninfo"></a><a name="getcolumninfo"></a>Crowctimpl:: GetColumnInfo

Ruft Spalten Informationen für eine bestimmte Client Anforderung ab.

### <a name="syntax"></a>Syntax

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>Parameter

*teuren*<br/>
in Ein Zeiger auf die `CRowsetImpl` abgeleitete Klasse des Benutzers.

*pcCols*<br/>
in Ein Zeiger (Ausgabe) auf die Anzahl der zurückgegebenen Spalten.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine statische- `ATLCOLUMNINFO` Struktur.

### <a name="remarks"></a>Bemerkungen

Diese Methode ist eine erweiterte außer Kraft Setzung.

Diese Methode wird von mehreren Basis Implementierungsklassen aufgerufen, um Spalten Informationen für eine bestimmte Client Anforderung abzurufen. Normalerweise würde diese Methode von aufgerufen werden `IColumnsInfoImpl` . Wenn Sie diese Methode überschreiben, müssen Sie eine Version der-Methode in der von `CRowsetImpl` abgeleiteten Klasse platzieren. Da die-Methode in einer nicht-Vorlagen Klasse platziert werden kann, müssen Sie die *PV* in die entsprechende von `CRowsetImpl` abgeleitete Klasse ändern.

Im folgenden Beispiel wird die Verwendung von veranschaulicht `GetColumnInfo` . In diesem Beispiel `CMyRowset` ist eine von `CRowsetImpl` abgeleitete Klasse. Um `GetColumnInfo` für alle Instanzen dieser Klasse zu überschreiben, platzieren Sie die folgende Methode in der `CMyRowset` Klassendefinition:

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="crowsetimplgetcommandfromid"></a><a name="getcommandfromid"></a>Crowctimpl:: getcommandfromid

Prüft, ob einer oder beide Parameter Zeichen folgen Werte enthalten. wenn dies der Fall ist, werden die Zeichen folgen Werte in die Datenelemente [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) und [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)kopiert.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parameter

*pTableID*<br/>
in Ein Zeiger auf den, der `DBID` die Tabellen-ID darstellt.

*pIndexID*<br/>
in Ein Zeiger auf den, der `DBID` die Index-ID darstellt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird durch einen statischen umgewandelt von aufgerufen `CRowsetImpl` , um die Datenmember [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) und [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)aufzufüllen. Standardmäßig prüft diese Methode, ob einer oder beide Parameter Zeichen folgen Werte enthalten. Wenn Sie Zeichen folgen Werte enthalten, kopiert diese Methode die Zeichen folgen Werte in die Datenmember. Wenn Sie in der von abgeleiteten Klasse eine Methode mit dieser Signatur platzieren `CRowsetImpl` , wird die-Methode anstelle der Basis Implementierung aufgerufen.

## <a name="crowsetimplvalidatecommandid"></a><a name="validatecommandid"></a>Crowabtimpl:: ValidateCommandID

Prüft, ob eine oder beide `DBID` s Zeichen folgen Werte enthalten. wenn dies der Fall ist, werden Sie in die Datenmember [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) und [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)kopiert.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parameter

*pTableID*<br/>
in Ein Zeiger auf den, der `DBID` die Tabellen-ID darstellt.

*pIndexID*<br/>
in Ein Zeiger auf den, der `DBID` die Index-ID darstellt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird durch einen statischen umgewandelt von aufgerufen `CRowsetImpl` , um die Datenmember [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) und [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)aufzufüllen. Standardmäßig prüft diese Methode, ob eine oder beide `DBID` s Zeichen folgen Werte enthalten. wenn dies der Fall ist, werden Sie in die Datenmember kopiert. Wenn Sie in der von abgeleiteten Klasse eine Methode mit dieser Signatur platzieren `CRowsetImpl` , wird die-Methode anstelle der Basis Implementierung aufgerufen.

## <a name="crowsetimplm_rgrowdata"></a><a name="rgrowdata"></a>Crow-timpl:: m_rgRowData

Standardmäßig eine, `CAtlArray` die eine Vorlage für das Benutzerdaten Satz-Vorlagen Argument für vorweist `CRowsetImpl` .

### <a name="syntax"></a>Syntax

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>Bemerkungen

*ArrayType* ist ein Vorlagen Parameter für `CRowsetImpl` .

## <a name="crowsetimplm_strcommandtext"></a><a name="strcommandtext"></a>Crow-timpl:: m_strCommandText

Enthält den anfänglichen Befehl des Rowsets.

### <a name="syntax"></a>Syntax

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="crowsetimplm_strindextext"></a><a name="strindextext"></a>Crow-timpl:: m_strIndexText

Enthält den Anfangs Index des Rowsets.

### <a name="syntax"></a>Syntax

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```
