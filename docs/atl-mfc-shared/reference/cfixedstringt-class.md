---
title: CFixedStringT-Klasse
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: fe096185f6f0b71ad45757cd0b75ab13c41e5f5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317826"
---
# <a name="cfixedstringt-class"></a>CFixedStringT-Klasse

Diese Klasse stellt ein Zeichenfolgenobjekt mit einem festen Zeichenpuffer dar.

## <a name="syntax"></a>Syntax

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Parameter

*StringType*<br/>
Wird als Basisklasse für das feste Zeichenfolgenobjekt verwendet und kann ein beliebiger `CStringT`-basierter Typ sein. Einige Beispiele `CString` `CStringA`sind `CStringW`, und .

*t_nChars*<br/>
Die Anzahl der im Puffer gespeicherten Zeichen.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFixedStringT::CFixedStringT](#cfixedstringt)|Der Konstruktor für das Zeichenfolgenobjekt.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFixedStringT::operator =](#operator_eq)|Weist einem `CFixedStringT` Objekt einen neuen Wert zu.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse ist ein Beispiel für `CStringT`eine benutzerdefinierte Zeichenfolgenklasse, die auf basiert. Obwohl sie sich ähneln, unterscheiden sich die beiden Klassen in der Implementierung. Die hauptwichtigsten `CFixedStringT` `CStringT` Unterschiede zwischen und sind:

- Der anfängliche Zeichenpuffer wird als Teil des Objekts zugewiesen und hat die Größe *t_nChars*. Dadurch kann `CFixedString` das Objekt einen zusammenhängenden Speicherblock für Leistungszwecke belegen. Wenn der Inhalt eines `CFixedStringT` Objekts jedoch über *t_nChars*hinaus wächst, wird der Puffer dynamisch zugewiesen.

- Der Zeichenpuffer `CFixedStringT` für ein Objekt hat immer die gleiche Länge ( *t_nChars*). Es gibt keine Beschränkung `CStringT` der Puffergröße für Objekte.

- Der Speicher-Manager für `CFixedStringT` ist so angepasst, dass die Freigabe eines [CStringData-Objekts](../../atl-mfc-shared/reference/cstringdata-class.md) zwischen zwei oder mehr `CFixedStringT` Objekten nicht zulässig ist. `CStringT`Objekte haben diese Einschränkung nicht.

Weitere Informationen zur Anpassung `CFixedStringT` und Speicherverwaltung für Zeichenfolgenobjekte im Allgemeinen finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** cstringt.h

## <a name="cfixedstringtcfixedstringt"></a><a name="cfixedstringt"></a>CFixedStringT::CFixedStringT

Erstellt ein `CFixedStringT`-Objekt.

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>Parameter

*pszSrc*<br/>
Eine null-terminierte Zeichenfolge, die `CFixedStringT` in dieses Objekt kopiert werden soll.

*strSrc*<br/>
Ein `CFixedStringT` vorhandenes Objekt, `CFixedStringT` das in dieses Objekt kopiert werden soll.

*pStringMgr*<br/>
Ein Zeiger auf den Speicher-Manager des `CFixedStringT` Objekts. Weitere Informationen `IAtlStringMgr` zu und `CFixedStringT`Speicherverwaltung für finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Bemerkungen

Da die Konstruktoren die Eingabedaten in neuen zugewiesenen Speicher kopieren, sollten Sie sich bewusst sein, dass Speicherausnahmen auftreten können. Einige dieser Konstruktoren fungieren als Konvertierungsfunktionen.

## <a name="cfixedstringtoperator-"></a><a name="operator_eq"></a>CFixedStringT::operator =

Initialisiert ein vorhandenes `CFixedStringT` Objekt mit neuen Daten erneut.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>Parameter

*pszSrc*<br/>
Eine null-terminierte Zeichenfolge, die `CFixedStringT` in dieses Objekt kopiert werden soll.

*strSrc*<br/>
Eine `CFixedStringT` vorhandene, die `CFixedStringT` in dieses Objekt kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Sie sollten sich bewusst sein, dass Speicherausnahmen auftreten können, wenn Sie den `CFixedStringT` Zuweisungsoperator verwenden, da häufig neuer Speicher für das resultierende Objekt reserviert wird.

## <a name="see-also"></a>Siehe auch

[CStringT-Klasse](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
