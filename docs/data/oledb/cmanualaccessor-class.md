---
title: CManualAccessor-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
ms.openlocfilehash: 32ab31734b8c6e3f72053e1e4f2a8a9233b73995
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838099"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor-Klasse

Stellt einen Accessortyp dar, der für die Erweiterte Verwendung entworfen wurde.

## <a name="syntax"></a>Syntax

```cpp
class CManualAccessor : public CAccessorBase
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[AddBindEntry](#addbindentry)|Fügt den Ausgabespalten einen Bindungs Eintrag hinzu.|
|[AddParameterEntry](#addparameterentry)|Fügt dem Parameter Accessor einen Parameter Eintrag hinzu.|
|[CreateAccessor](#createaccessor)|Weist Speicher für die Spalten Bindungs Strukturen zu und initialisiert die Spalten Datenmember.|
|[CreateParameterAccessor](#createparameteraccessor)|Weist Speicher für die Parameter Bindungs Strukturen zu und initialisiert die Parameter Datenmember.|

## <a name="remarks"></a>Bemerkungen

Mithilfe `CManualAccessor` von können Sie die Parameter-und Ausgabespalten Bindung mithilfe von Lauf Zeit Funktionsaufrufen angeben.

## <a name="cmanualaccessoraddbindentry"></a><a name="addbindentry"></a> CManualAccessor:: AddBindEntry

Fügt den Ausgabespalten einen Bindungs Eintrag hinzu.

### <a name="syntax"></a>Syntax

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer.

*wType*<br/>
in Datentyp.

*ncolumnsize*<br/>
in Spaltengröße in Byte.

*pData*<br/>
in Ein Zeiger auf die Spaltendaten, die im Puffer gespeichert werden.

*pLength*<br/>
in Ein Zeiger auf die Feldlänge, falls erforderlich.

*pstatus*<br/>
in Ein Zeiger auf die Variable, die an den Spalten Status gebunden werden soll, falls erforderlich.

### <a name="remarks"></a>Bemerkungen

Um diese Funktion verwenden zu können, müssen Sie zuerst "up- [Accessor](../../data/oledb/cmanualaccessor-createaccessor.md)" aufrufen. Sie können keine weiteren Einträge hinzufügen, als die Anzahl der in angegebenen Spalten `CreateAccessor` .

## <a name="cmanualaccessoraddparameterentry"></a><a name="addparameterentry"></a> CManualAccessor:: AddParameterEntry

Fügt den Parameter Eintrags Strukturen einen Parameter Eintrag hinzu.

### <a name="syntax"></a>Syntax

```cpp
void AddParameterEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL,
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Parameter Nummer.

*wType*<br/>
in Datentyp.

*ncolumnsize*<br/>
in Spaltengröße in Byte.

*pData*<br/>
in Ein Zeiger auf die Spaltendaten, die im Puffer gespeichert werden.

*pLength*<br/>
in Ein Zeiger auf die Feldlänge, falls erforderlich.

*pstatus*<br/>
in Ein Zeiger auf die Variable, die an den Spalten Status gebunden werden soll, falls erforderlich.

*eParamIO*<br/>
in Gibt an, ob der Parameter, mit dem die Bindung verknüpft ist, ein Eingabe-, Eingabe-/Ausgabe-oder Ausgabeparameter ist.

### <a name="remarks"></a>Bemerkungen

Um diese Funktion verwenden zu können, müssen Sie zuerst den Befehl "" für "" als " [" aufrufen.](../../data/oledb/cmanualaccessor-createparameteraccessor.md)

## <a name="cmanualaccessorcreateaccessor"></a><a name="createaccessor"></a> CManualAccessor:: erkreateaccessor

Weist Speicher für die Spalten Bindungs Strukturen zu und initialisiert die Spalten Datenmember.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Parameter

*nbindentries*<br/>
in Anzahl der Spalten. Diese Zahl sollte mit der Anzahl der Aufrufe der [CManualAccessor:: AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) -Funktion identisch sein.

*pBuffer*<br/>
in Ein Zeiger auf den Puffer, in dem die Ausgabespalten gespeichert werden.

*nbuffersize*<br/>
in Die Größe des Puffers in Bytes.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, bevor die-Funktion aufgerufen wird `CManualAccessor::AddBindEntry` .

## <a name="cmanualaccessorcreateparameteraccessor"></a><a name="createparameteraccessor"></a> CManualAccessor:: up Parameteraccessor

Weist Speicher für die Parameter Bindungs Strukturen zu und initialisiert die Parameter Datenmember.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Parameter

*nbindentries*<br/>
in Anzahl der Spalten.

*pBuffer*<br/>
in Ein Zeiger auf den Puffer, in dem die Eingabe Spalten gespeichert werden.

*nbuffersize*<br/>
in Die Größe des Puffers in Bytes.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Funktion aufrufen, bevor Sie [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)aufrufen.

## <a name="see-also"></a>Weitere Informationen

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor-Klasse](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor-Klasse](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor-Klasse](../../data/oledb/cdynamicparameteraccessor-class.md)
