---
title: CMF ccmdusagecount-Klasse
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
ms.openlocfilehash: 95dca548856510cd8b06914932cc46435c28399d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834276"
---
# <a name="cmfccmdusagecount-class"></a>CMF ccmdusagecount-Klasse

Verfolgt die Verwendungs Anzahl von Windows-Meldungen, z. b. wenn der Benutzer ein Element aus einem Menü auswählt.

## <a name="syntax"></a>Syntax

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Standardkonstruktor|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[CMF ccmdusagecount:: addcmd](#addcmd)|Inkremente um einen der mit dem angegebenen Befehl verknüpften Zählers.|
|[CMF ccmdusagecount:: GetCount](#getcount)|Ruft den Verwendungs Zähler ab, der der angegebenen Befehls-ID zugeordnet ist.|
|[CMF ccmdusagecount:: hasenoughinformation](#hasenoughinformation)|Bestimmt, ob dieses-Objekt die minimale Menge an Überwachungsdaten erfasst hat.|
|[CMF ccmdusagecount:: isfreqeuntlyusedcmd](#isfreqeuntlyusedcmd)|Bestimmt, ob der angegebene Befehl häufig verwendet wird.|
|[CMF ccmdusagecount:: Reset](#reset)|Löscht den Verwendungs Zähler aller Befehle.|
|[CMF ccmdusagecount:: Serialize](#serialize)|Liest dieses Objekt aus einem Archiv oder schreibt es in ein Archiv. (Überschreibt [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CMF ccmdusagecount::-toptions](#setoptions)|Legt die Werte von freigegebenen `CMFCCmdUsageCount` klassendatenmembern fest.|

### <a name="data-members"></a>Datenelemente

|Name|Beschreibung|
|-|-|
|`m_CmdUsage`|Ein- `CMap` Objekt, das Befehle Ihren Verwendungs Anzahlen zuordnet.|
|`m_nMinUsagePercentage`|Der minimale Verwendungs Prozentsatz für einen Befehl, der häufig verwendet wird.|
|`m_nStartCount`|Der Start-Counter, der verwendet wird, um zu bestimmen, ob dieses Objekt die minimale Menge an Überwachungsdaten erfasst hat.|
|`m_nTotalUsage`|Gibt die Anzahl aller nach verfolgten Befehle an.|

### <a name="remarks"></a>Bemerkungen

Die- `CMFCCmdUsageCount` Klasse ordnet jeden numerischen Windows-Nachrichten Bezeichner einer 32-Bit-Ganzzahl ohne Vorzeichen zu. `CMFCToolBar` verwendet diese Klasse, um häufig verwendete Symbolleisten Elemente anzuzeigen. Weitere Informationen zu `CMFCToolBar` finden Sie unter [cmfctoolbar-Klasse](../../mfc/reference/cmfctoolbar-class.md).

Sie können `CMFCCmdUsageCount` Klassen Daten zwischen den Ausführungen des Programms beibehalten. Verwenden Sie die [cmfccmdusagecount:: Serialisieren](#serialize) -Methode, um Klassenmember-Daten zu serialisieren, und die [cmfccmdusagecount:: SetOptions](#setoptions) -Methode, um freigegebene Elementdaten festzulegen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmdusagecount. h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a> CMF ccmdusagecount:: addcmd

Inkremente um einen der mit dem angegebenen Befehl verknüpften Zählers.

```cpp
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parameter

*uicmd*\
in Gibt den zu Inkrement des Befehls Zählers an.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt der Karten Struktur der Befehls Anzahl einen neuen Eintrag hinzu, `m_CmdUsage` , wenn der Eintrag nicht bereits vorhanden ist.

Diese Methode führt in den folgenden Fällen keine Aktion aus:

- Das Symbolleisten Framework befindet sich im Anpassungsmodus (die [cmfctoolbar:: iscustomizemode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) -Methode gibt einen Wert ungleich 0 (null) zurück).

- Der Befehl verweist auf ein Untermenü oder ein Menü Trennzeichen ( *uicmd* ist 0 oder-1).

- *uicmd* verweist auf einen Standardbefehl (die globale `IsStandardCommand` Funktion gibt einen Wert ungleich 0 (null) zurück).

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a> CMF ccmdusagecount:: GetCount

Ruft den Verwendungs Zähler ab, der der angegebenen Befehls-ID zugeordnet ist.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>Parameter

*uicmd*\
in Die ID des abzurufenden Befehls Zählers.

### <a name="return-value"></a>Rückgabewert

Der Verwendungs Zähler, der der angegebenen Befehls-ID zugeordnet ist.

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a> CMF ccmdusagecount:: hasenoughinformation

Bestimmt, ob dieses-Objekt die minimale Menge an Überwachungsdaten empfangen hat.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn dieses Objekt die minimale Menge an Überwachungsdaten empfangen hat. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt einen Wert ungleich 0 (null) zurück, wenn die Gesamtzahl `m_nTotalUsage` aller nach verfolgten Befehle gleich oder größer als die anfängliche Anzahl ist `m_nStartCount` . Standardmäßig legt das Framework die anfängliche Anzahl 0 fest. Sie können diesen Wert überschreiben, indem Sie die [CMF ccmdusagecount:: endtions](#setoptions) -Methode verwenden.

Diese Methode wird von [cmfcmenubar:: isshowallcommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) verwendet, um zu bestimmen, ob alle verfügbaren Menübefehle angezeigt werden sollen.

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a> CMF ccmdusagecount:: isfreqeuntlyusedcmd

Bestimmt, ob der angegebene Befehl häufig verwendet wird.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>Parameter

*uicmd*\
in Gibt den zu überprüfen Befehl an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Befehl häufig verwendet wird. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt 0 zurück, wenn die gesamte Befehls Verwendung, `m_nTotalUsage` , 0 ist. Andernfalls gibt diese Methode einen Wert ungleich 0 (null) zurück, wenn der Prozentsatz, mit dem der angegebene Befehl verwendet wird, größer als der minimale Prozentsatz ist `m_nMinUsagePercentage` . Standardmäßig legt das Framework den minimalen Prozentsatz auf 5 fest. Sie können diesen Wert überschreiben, indem Sie die [CMF ccmdusagecount:: endtions](#setoptions) -Methode verwenden. Wenn der minimale Prozentsatz 0 beträgt, gibt diese Methode einen Wert ungleich 0 (null) zurück, wenn die angegebene Befehls Anzahl größer als 0 ist.

[Cmfctoolbar:: iscommandrarelyused](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) verwendet diese Methode, um zu bestimmen, ob ein Befehl selten verwendet wird.

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a> CMF ccmdusagecount:: Reset

Löscht den Verwendungs Zähler aller Befehle.

```cpp
void Reset();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Methode aufrufen, löschen Sie alle Einträge aus der Zuordnungs Struktur der Befehls Anzahl, `m_CmdUsage` , und setzen Sie den Zähler für die gesamte Befehls Verwendung () `m_nTotalUsage` auf 0.

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a> CMF ccmdusagecount:: Serialize

Liest dieses Objekt aus einem Archiv oder schreibt es in ein Archiv.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*Tempel*\
in Ein- `CArchive` Objekt, aus dem oder in das serialisiert werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode serialisiert die Zuordnungs Struktur der Befehls Anzahl, `m_CmdUsage` und den gesamten Befehls Verwendungs-,-und- `m_nTotalUsage` Zähler aus oder in das angegebene Archiv.

Beispiele für die Serialisierung finden Sie unter [Serialisierung: Serialisieren eines Objekts](../../mfc/serialization-serializing-an-object.md).

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a> CMF ccmdusagecount::-toptions

Legt die Werte von freigegebenen `CMFCCmdUsageCount` klassendatenmembern fest.

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>Parameter

*nstartcount*\
in Die neue anfängliche Anzahl aller nach verfolgten Befehle.

*nminusageprozent*\
in Der neue minimale Verwendungs Prozentsatz.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist, false, wenn der *nminusageprozent* -Parameter größer oder gleich 100 ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode legt die Datenelemente der freigegebenen `CMFCCmdUsageCount` Klasse `m_nStartCount` und `m_nMinUsagePercentage` auf *nstartcount* bzw. *nminusageprozent*fest. `m_nStartCount` wird von der [cmfccmdusagecount:: hasenoughinformation](#hasenoughinformation) -Methode verwendet, um zu bestimmen, ob dieses Objekt die minimale Menge an Überwachungsdaten erfasst hat. `m_nMinUsagePercentage` wird von der [cmfccmdusagecount:: isfreqeuntlyusedcmd](#isfreqeuntlyusedcmd) -Methode verwendet, um zu bestimmen, ob ein bestimmter Befehl häufig verwendet wird.

In Debugbuilds generiert diese Methode einen Fehler bei der Übersetzung, wenn der *nminusageprozent* -Parameter größer oder gleich 100 ist.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cmfctoolbar-Klasse](../../mfc/reference/cmfctoolbar-class.md)
