---
title: CMFCCmdUsageCount-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
ms.openlocfilehash: 1c03f0c62e508f9d00a352b71c8f3a18604e36c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367741"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount-Klasse

Verfolgt die Verwendungsanzahl von Windows-Nachrichten, z. B. wenn der Benutzer ein Element aus einem Menü auswählt.

## <a name="syntax"></a>Syntax

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Der Standardkonstruktor.|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Erhöht um eins den Zähler, der dem angegebenen Befehl zugeordnet ist.|
|[CMFCCmdUsageCount::GetCount](#getcount)|Ruft die Verwendungsanzahl ab, die der angegebenen Befehls-ID zugeordnet ist.|
|[CMFCCmdUsageCount::HasEnoughInformationen](#hasenoughinformation)|Bestimmt, ob dieses Objekt die minimale Menge an Nachverfolgungsdaten erfasst hat.|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Bestimmt, ob der angegebene Befehl häufig verwendet wird.|
|[CMFCCmdUsageCount::Reset](#reset)|Löscht die Verwendungsanzahl aller Befehle.|
|[CMFCCmdUsageCount::Serialisieren](#serialize)|Liest dieses Objekt aus einem Archiv oder schreibt es in ein Archiv. (Überschreibt [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CMFCCmdUsageCount::SetOptionen](#setoptions)|Legt die Werte `CMFCCmdUsageCount` von freigegebenen Klassendatenmembern fest.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|Name|BESCHREIBUNG|
|`m_CmdUsage`|Ein `CMap` Objekt, das Befehle ihrer Verwendungsanzahl zuordnet.|
|`m_nMinUsagePercentage`|Der minimale Nutzungsprozentsatz für einen Häufig verwendeten Befehl.|
|`m_nStartCount`|Der Startzähler, der verwendet wird, um zu bestimmen, ob dieses Objekt die minimale Menge an Nachverfolgungsdaten erfasst hat.|
|`m_nTotalUsage`|Die Anzahl aller nachverfolgten Befehle.|

### <a name="remarks"></a>Bemerkungen

Die `CMFCCmdUsageCount` Klasse ordnet jeden numerischen Windows-Nachrichtenbezeichner einem 32-Bit-Ganzzahlzähler ohne Vorzeichen zu. `CMFCToolBar`verwendet diese Klasse, um häufig verwendete Symbolleistenelemente anzuzeigen. Weitere Informationen `CMFCToolBar`zu finden Sie unter [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md).

Sie können `CMFCCmdUsageCount` Klassendaten zwischen den Ausführungen des Programms beibehalten. Verwenden Sie die [CMFCCmdUsageCount::Serialize-Methode](#serialize) zum Serialisieren von Klassenmemberdaten und die [CMFCCmdUsageCount::SetOptions-Methode](#setoptions) zum Festlegen freigegebener Memberdaten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxcmdusagecount.h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a>CMFCCmdUsageCount::AddCmd

Erhöht um eins den Zähler, der dem angegebenen Befehl zugeordnet ist.

```
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*uiCmd*|[in] Gibt den Befehlszähler an, der inkrementiert werden soll.|

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt der Kartenstruktur der Befehlsanzahl einen neuen Eintrag hinzu, `m_CmdUsage`wenn der Eintrag noch nicht vorhanden ist.

Diese Methode bewirkt in den folgenden Fällen nichts:

- Das Symbolleistenframework befindet sich im Anpassungsmodus (die [CMFCToolBar::IsCustomizeMode-Methode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) gibt einen Wert ungleich Null zurück).

- Der Befehl bezieht sich auf ein Untermenü oder Menütrennzeichen *(uiCmd* entspricht 0 oder -1).

- *uiCmd* bezieht sich auf einen `IsStandardCommand` Standardbefehl (die globale Funktion gibt einen Wert ungleich Null zurück).

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a>CMFCCmdUsageCount::GetCount

Ruft die Verwendungsanzahl ab, die der angegebenen Befehls-ID zugeordnet ist.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*uiCmd*|[in] Die ID des abzurufenden Befehlszählers.|

### <a name="return-value"></a>Rückgabewert

Die Verwendungsanzahl, die der angegebenen Befehls-ID zugeordnet ist.

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformationen

Bestimmt, ob dieses Objekt die Minimale Menge an Nachverfolgungsdaten empfangen hat.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn dieses Objekt die Mindestmenge an Nachverfolgungsdaten erhalten hat; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt einen Wert ungleich `m_nTotalUsage`Null zurück, wenn die Gesamtanzahl aller nachverfolgten Befehle gleich oder größer als die anfängliche Anzahl `m_nStartCount`ist. Standardmäßig legt das Framework die anfängliche Anzahl 0 fest. Sie können diesen Wert überschreiben, indem Sie die [CMFCCmdUsageCount::SetOptions-Methode](#setoptions) verwenden.

Diese Methode wird von [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) verwendet, um zu bestimmen, ob alle verfügbaren Menübefehle angezeigt werden sollen.

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

Bestimmt, ob der angegebene Befehl häufig verwendet wird.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*uiCmd*|[in] Gibt den zu überprüfenden Befehl an.|

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Befehl häufig verwendet wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt 0 zurück, `m_nTotalUsage`wenn die Gesamtbefehlsverwendung 0 ist. Andernfalls gibt diese Methode einen Wert ungleich Null zurück, wenn der `m_nMinUsagePercentage`Prozentsatz, für den der angegebene Befehl verwendet wird, größer als der Mindestprozentsatz ist. Standardmäßig legt das Framework den Mindestprozentsatz auf 5 fest. Sie können diesen Wert überschreiben, indem Sie die [CMFCCmdUsageCount::SetOptions-Methode](#setoptions) verwenden. Wenn der Mindestprozentsatz 0 ist, gibt diese Methode einen Wert ungleich Null zurück, wenn die angegebene Befehlsanzahl größer als 0 ist.

[CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) verwendet diese Methode, um zu bestimmen, ob ein Befehl selten verwendet wird.

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a>CMFCCmdUsageCount::Reset

Löscht die Verwendungsanzahl aller Befehle.

```
void Reset();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um alle `m_CmdUsage`Einträge aus der Kartenstruktur `m_nTotalUsage`der Befehlsanzahl , zu löschen und die Gesamtbefehlsverwendung, , Zähler auf 0 zurückzusetzen.

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a>CMFCCmdUsageCount::Serialisieren

Liest dieses Objekt aus einem Archiv oder schreibt es in ein Archiv.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*ar*|[in] Ein `CArchive` Objekt, von dem serialisiert werden soll, oder an.|

### <a name="remarks"></a>Bemerkungen

Diese Methode serialisiert die Kartenstruktur `m_CmdUsage`der Befehlsanzahlen `m_nTotalUsage`, und die gesamte Befehlsverwendung, , Zähler aus oder zum angegebenen Archiv.

Beispiele für Serialisierung finden Sie unter [Serialisierung: Serialisieren eines Objekts](../../mfc/serialization-serializing-an-object.md).

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a>CMFCCmdUsageCount::SetOptionen

Legt die Werte `CMFCCmdUsageCount` von freigegebenen Klassendatenmembern fest.

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*nStartCount*|[in] Die neue anfängliche Anzahl aller nachverfolgten Befehle.|
|*nMinUsageProzentsatz*|[in] Der neue Mindestnutzungsprozentsatz.|

### <a name="return-value"></a>Rückgabewert

TRUE wenn die Methode erfolgreich ist, FALSE, wenn der Parameter *nMinUsagePercentage* größer oder gleich 100 ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode legt `CMFCCmdUsageCount` die `m_nStartCount` shared `m_nMinUsagePercentage` class data members bzw. auf *nStartCount* bzw. *nMinUsagePercentage*fest. `m_nStartCount`wird von der [CMFCCmdUsageCount::HasEnoughInformation-Methode](#hasenoughinformation) verwendet, um zu bestimmen, ob dieses Objekt die minimale Menge an Nachverfolgungsdaten gesammelt hat. `m_nMinUsagePercentage`wird von der [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd-Methode](#isfreqeuntlyusedcmd) verwendet, um zu bestimmen, ob ein gegebener Befehl häufig verwendet wird.

In Debug-Builds generiert diese Methode einen Assertionsfehler, wenn der Parameter *nMinUsagePercentage* größer oder gleich 100 ist.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)
