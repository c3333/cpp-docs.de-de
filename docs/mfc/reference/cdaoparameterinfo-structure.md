---
title: CDaoParameterInfo-Struktur
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 6d594bbeec34e400eb074c136e3467e78b35c4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368981"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo-Struktur

Die `CDaoParameterInfo` Struktur enthält Informationen zu einem Parameterobjekt, das für Datenzugriffsobjekte (DAO) definiert ist. DAO 3.6 ist die endgültige Version und gilt als veraltet.

## <a name="syntax"></a>Syntax

```
struct CDaoParameterInfo
{
    CString m_strName;       // Primary
    short m_nType;           // Primary
    ColeVariant m_varValue;  // Secondary
};
```

#### <a name="parameters"></a>Parameter

*m_strName*<br/>
Benennt das Parameterobjekt eindeutig. Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe.

*m_nType*<br/>
Ein Wert, der den Datentyp eines Parameterobjekts angibt. Eine Liste der möglichen Werte finden Sie im *m_nType-Member* der [CDaoFieldInfo-Struktur.](../../mfc/reference/cdaofieldinfo-structure.md) Weitere Informationen finden Sie im Thema "Typeigenschaft" in der DAO-Hilfe.

*m_varValue*<br/>
Der Wert des Parameters, der in einem [COleVariant-Objekt](../../mfc/reference/colevariant-class.md) gespeichert ist.

## <a name="remarks"></a>Bemerkungen

Die obigen Verweise auf Primär und Sekundär geben an, wie `CDaoQueryDef`die Informationen von der [GetParameterInfo-Memberfunktion](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) in der Klasse zurückgegeben werden.

MFC kapselt KEINE DAO-Parameterobjekte in einer Klasse. DAO querydef-Objekte, `CDaoQueryDef` die MFC-Objekten zugrunde liegen, speichern Parameter in ihren Parameters-Auflistungen. Um auf die Parameterobjekte in einem [CDaoQueryDef-Objekt](../../mfc/reference/cdaoquerydef-class.md) `GetParameterInfo` zuzugreifen, rufen Sie die Memberfunktion des querydef-Objekts für einen bestimmten Parameternamen oder einen Index in die Parameters-Auflistung auf. Sie können die [Memberfunktion CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) in Verbindung mit `GetParameterInfo` dem Durchlaufen der Parameters-Auflistung verwenden.

Die von der [Memberfunktion CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) `CDaoParameterInfo` abgerufenen Informationen werden in einer Struktur gespeichert. Rufen `GetParameterInfo` Sie das querydef-Objekt auf, in dessen Parameters-Auflistung das Parameterobjekt gespeichert ist.

> [!NOTE]
> Wenn Sie nur den Wert eines Parameters abrufen oder festlegen möchten, verwenden Sie die `CDaoRecordset`Elementfunktionen [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) und [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) der Klasse .

`CDaoParameterInfo`definiert auch `Dump` eine Memberfunktion in Debugbuilds. Sie können `Dump` den Inhalt eines `CDaoParameterInfo` Objekts absetzen.

## <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="see-also"></a>Siehe auch

[Strukturen, Stile, Rückrufe und Meldungszuordnungen](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef-Klasse](../../mfc/reference/cdaoquerydef-class.md)
