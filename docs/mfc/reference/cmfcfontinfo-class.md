---
title: CMFCFontInfo-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: 6e87971e2afefc9cf1574abe951920c254dcd2ae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367486"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo-Klasse

Die `CMFCFontInfo` Klasse beschreibt den Namen und andere Attribute einer Schriftart.

## <a name="syntax"></a>Syntax

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCFontInfo`|Erstellt ein `CMFCFontInfo`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|Ruft die verketteten Namen einer Schriftart und deren Zeichensatz (Skript) ab.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Ein Wert, der den Zeichensatz (Skript) angibt, der der Schriftart zugeordnet ist.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Ein Wert, der die Tonhöhe und die Familie der Schriftart angibt.|
|[CMFCFontInfo::m_nType](#m_ntype)|Ein Wert, der den Typ der Schriftart angibt.|
|[CMFCFontInfo::m_strName](#m_strname)|Der Name der Schriftart; z. B. **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|Der Name eines Zeichensatzes (Skripts), der der Schriftart zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

Sie können `CMFCFontInfo` ein Objekt an ein Element der [CMFCToolBarFontComboBox-Klassenklasse](../../mfc/reference/cmfctoolbarfontcombobox-class.md) anfügen. Rufen Sie die [CMFCToolBarFontComboBox::GetFontDesc-Methode](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) auf, um einen Zeiger auf ein `CMFCFontInfo` Objekt abzurufen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCFontInfo` wie verschiedene Member der Klasse verwendet werden. Im Beispiel wird veranschaulicht, wie ein `CMFCFontInfo` Objekt von einem `CMFCRibbonFontComboBox`abgreift und wie auf seine lokalen Variablen zugreift. Dieses Beispiel ist Teil des [MSOffice 2007-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxtoolbarfontcombobox.h

## <a name="cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo

Erstellt ein `CMFCFontInfo`-Objekt.

```
CMFCFontInfo(
    LPCTSTR lpszName,
    LPCTSTR lpszScript,
    BYTE nCharSet,
    BYTE nPitchAndFamily,
    int nType);

CMFCFontInfo(const CMFCFontInfo& src);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
[in] Der Name der Schriftart. Weitere Informationen finden `lfFaceName` Sie im Member der [LOGFONT-Struktur.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*lpszScript*<br/>
[in] Der Name des Skripts (Zeichensatz) der Schriftart.

*nCharSet*<br/>
[in] Ein Wert, der den Zeichensatz (Skript) der Schriftart angibt. Weitere Informationen finden `lfCharSet` Sie im Member der [LOGFONT-Struktur.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*nPitchAndFamilie*<br/>
[in] Ein Wert, der die Tonhöhe und die Familie der Schriftart angibt. Weitere Informationen finden `lfPitchAndFamily` Sie im Member der [LOGFONT-Struktur.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*nType*<br/>
[in] Ein Wert, der den Schrifttyp angibt. Dieser Parameter kann eine bitweise Kombination (OR) von DEVICE_FONTTYPE, RASTER_FONTTYPE und TRUETYPE_FONTTYPE sein.

*src*<br/>
[in] Ein `CMFCFontInfo` vorhandenes Objekt, dessen `CMFCFontInfo` Member zum Erstellen dieses Objekts verwendet werden.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

In dieser Dokumentation werden die Begriffe *Zeichensatz* und *Skript* austauschbar verwendet. Ein *Skript*, das auch als Schreibsystem bezeichnet wird, ist eine Sammlung von Zeichen und Regeln zum Schreiben dieser Zeichen in einer oder mehreren Sprachen. Die Sammlung von Zeichen enthält das Alphabet und die Interpunktion, die in diesem Skript verwendet werden. Beispielsweise wird die lateinische Schrift für Englisch verwendet, wie sie in den Vereinigten Staaten gesprochen wird, und das Alphabet enthält die Zeichen von A bis Z. Das `lfCharSet` Element der [LOGFONT-Struktur](/windows/win32/api/wingdi/ns-wingdi-logfontw) gibt einen Zeichensatz an. Der Wert ANSI_CHARSET gibt z. B. den ANSI-Zeichensatz an, der das Alphabet der lateinischen Schrift enthält.

## <a name="cmfcfontinfogetfullname"></a><a name="getfullname"></a>CMFCFontInfo::GetFullName

Ruft die verketteten Namen einer Schriftart und deren Zeichensatz (Skript) ab.

```
CString GetFullName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die den Schriftnamen und das Skript enthält.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um den vollständigen Namen der Schriftart abzuerhalten. Wenn der Schriftartname beispielsweise **Arial** und das Schriftskript **kyrillisch**ist, gibt diese Methode "Arial (Kyrillisch)" zurück.

## <a name="cmfcfontinfom_ncharset"></a><a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet

Ein Wert, der den Zeichensatz (Skript) angibt, der der Schriftart zugeordnet ist.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im *nCharSet-Parameter* des [Konstruktors CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_npitchandfamily"></a><a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily

Ein Wert, der die Tonhöhe (Punktgröße) und die Familie (z. B. Serif, Sans-Serif und Monospace) der Schriftart angibt.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im *NPitchAndFamily-Parameter* des [CMFCFontInfo::CMFCFontInfo-Konstruktors.](#cmfcfontinfo)

## <a name="cmfcfontinfom_ntype"></a><a name="m_ntype"></a>CMFCFontInfo::m_nType

Ein Wert, der den Typ der Schriftart angibt.

```
const int m_nType;
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im *nType-Parameter* des [Konstruktors CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_strname"></a><a name="m_strname"></a>CMFCFontInfo::m_strName

Der Name der Schriftart: z. B. **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im *lpszName-Parameter* des [Konstruktors CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="cmfcfontinfom_strscript"></a><a name="m_strscript"></a>CMFCFontInfo::m_strScript

Der Name eines Zeichensatzes (Skripts), der der Schriftart zugeordnet ist.

```
const CString m_strScript;
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im *lpszScript-Parameter* des [Konstruktors CMFCFontInfo::CMFCFontInfo.](#cmfcfontinfo)

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox-Klasse](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox-Klasse](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
