---
title: AFX_GLOBAL_DATA-Struktur
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::InitD2D
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: 0361d535a31526c5f7b79fdd4eab046dad0435cc
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752871"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA-Struktur

Die `AFX_GLOBAL_DATA` -Struktur enthält Felder und Methoden, mit denen das Framework verwaltet oder die Darstellung und das Verhalten der Anwendung angepasst werden können.

## <a name="syntax"></a>Syntax

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Erstellt eine `AFX_GLOBAL_DATA` -Struktur.|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|Gibt Ressourcen frei, die vom Framework zugeordnet werden, z. B. Pinsel, Schriftarten und DLLs.|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Erstellt eine Drehtransformation, die sich in einem angegebenen Winkel um einen angegebenen Punkt dreht.|
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Zeichnet den Hintergrund des übergeordneten Elements eines Steuerelements im angegebenen Bereich.|
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Zeichnet den angegebenen Text im Stil des angegebenen Designs.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Entfernt das angegebenen XML-Tagpaar aus einem angegebenen Puffer.|
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Ruft die derzeitige Farbe eines angegebenen Benutzeroberflächen-Elements ab.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Gibt einen Zeiger auf die `ID2D1Factory` -Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Ruft den vordefinierten Cursor ab, der einer Hand ähnelt und dessen Bezeichner `IDC_HAND`lautet.|
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Erstellt und speichert in den globalen Daten einen Zeiger auf die ITaskBarList-Schnittstelle.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Erstellt und speichert in den globalen Daten einen Zeiger auf die ITaskBarList3-Schnittstelle.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Ruft die Metriken ab, die dem Nichtclientbereich von nicht minimierten Fenstern zugeordnet sind.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Bestimmt Positionen von Leisten zum automatischen Ausblenden einer Shell.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Ruft die Höhe von Textzeichen in der aktuellen Schriftart ab.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Gibt einen Zeiger auf die `IWICImagingFactory` -Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Gibt einen Zeiger auf die `IDWriteFactory` -Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.|
|[AFX_GLOBAL_DATA::InitD2D](#initd2d)|Initialisiert die Factorys `D2D`, `DirectWrite`und `WIC` . Rufen Sie diese Methode vor der Initialisierung des Hauptfensters auf.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Gibt an, ob vordefinierte 32-Bit-Symbole unterstützt werden.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Bestimmt, ob `D2D` initialisiert wurde.|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Stellt eine einfache Möglichkeit zum Aufrufen der [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) -Methode von Windows bereit.|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Gibt an, ob Bilder nur mit hohem Kontrast angezeigt werden.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Erkennt den aktuellen Zustand der Funktionen zum automatischen Ausblenden der Menüanimation und Taskleisten auf dem Desktop.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Registriert die angegebene MFC-Fensterklasse.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Gibt Schnittstellen frei, die durch die Methoden GetITaskbarList und GetITaskbarList3 ermittelt wurden.|
|[AFX_GLOBAL_DATA::Resume](#resume)|Initialisiert die internen Funktionszeiger für den Zugriff auf Methoden, die [Designs und visuelle Stile](/windows/win32/Controls/visual-styles-overview)in Windows unterstützen.|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Stellt eine einfache Möglichkeit zum Aufrufen der [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) -Methode von Windows bereit.|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Erstellt die angegebene logische Schriftart.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Erstellt und initialisiert ein Shellelementobjekt aus einem Analysenamen.|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Initialisiert die logischen Schriftarten erneut, die vom Framework verwendet werden.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Initialisiert die Farben, die Farbtiefe, die Stifte, die Pinsel und die Bilder, die vom Framework verwendet werden.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Aktiviert oder deaktiviert Microsoft Active Accessibility-Unterstützung. Active Accessibility stellt zuverlässige Methoden zum Anzeigen von Informationen über Benutzeroberflächenelemente bereit.|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Gibt an, ob Microsoft Active Accessibility-Unterstützung aktiviert ist.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Gibt an, ob das Betriebssystem überlappende Fenster unterstützt.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Gibt an, ob das aktuelle Betriebssystem Alphablending unterstützt.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Gibt an, ob die Anwendung unter dem Betriebssystem Windows 7 oder höher ausgeführt wird.|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Gibt den Farbverlauf der aktiven Beschriftung an. Wird im Allgemeinen für andockbare Bereiche verwendet.|
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Gibt den Farbverlauf der inaktiven Beschriftung an. Wird im Allgemeinen für andockbare Bereiche verwendet.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Gibt an, ob das Framework vordefinierte 32-Bit-Farbsymbole oder Symbole mit einer niedrigeren Auflösung verwendet.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Gibt an, ob eine Systemschriftart für Menüs, Symbolleisten und Menübänder verwendet wird.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Speichert das Handle für den Hand-Cursor.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Speichert das Handle für den horizontalen Streckungs-Cursor.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Speichert das Handle für den vertikalen Streckungs-Cursor.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Speichert das Handle für das Werkzeugsymbol.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Gibt den Offset von der äußersten linken Symbolleiste zum automatischen Ausblenden von der linken Seite der Andockleiste an.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Gibt die Lücke zwischen Symbolleisten zum automatischen Ausblenden an.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Gibt die Breite des Ziehrahmens an, mit dem der angedockten Zustand übermittelt wird.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Gibt die Breite des Ziehrahmens an, mit dem der unverankerte Zustand übermittelt wird.|

### <a name="remarks"></a>Bemerkungen

Die meisten Daten in der `AFX_GLOBAL_DATA` -Struktur werden beim Start der Anwendung initialisiert.

### <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxglobals.h

## <a name="afx_global_databisosalphablendingsupport"></a><a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport

Gibt an, ob das Betriebssystem Alpha-Überblendungen unterstützt.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass Alpha-Überblendungen unterstützt werden. andernfalls FALSE.

## <a name="afx_global_datacleanup"></a><a name="cleanup"></a>AFX_GLOBAL_DATA::CleanUp

Gibt Ressourcen frei, die vom Framework zugeordnet werden, z. B. Pinsel, Schriftarten und DLLs.

```cpp
void CleanUp();
```

## <a name="afx_global_datad2d1makerotatematrix"></a><a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D2D1MakeRotateMatrix

Erstellt eine Drehtransformation, die sich in einem angegebenen Winkel um einen angegebenen Punkt dreht.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Parameter

*angle*<br/>
Der Winkel der Drehung im Uhrzeigersinn in Grad.

*Center*<br/>
Der Punkt, um den gedreht werden soll.

*Matrix*<br/>
Wenn diese Methode zurückgegeben wird, enthält die neue Rotationstransformation. Sie müssen Speicher für diesen Parameter zuweisen.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK, wenn erfolgreich, oder einen anderen Fehlerwert zurück.

## <a name="afx_global_datadrawparentbackground"></a><a name="drawparentbackground"></a>AFX_GLOBAL_DATA::DrawParentBackground

Zeichnet den Hintergrund des übergeordneten Elements eines Steuerelements im angegebenen Bereich.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
[in] Zeiger auf das Fenster eines Steuerelements.

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext.

*lpRect*<br/>
[in] Zeigen Sie auf ein Rechteck, das den zu zeichnenden Bereich begrenzt. Der Standardwert ist NULL.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

## <a name="afx_global_datadrawtextonglass"></a><a name="drawtextonglass"></a>AFX_GLOBAL_DATA::DrawTextOnGlass

Zeichnet den angegebenen Text im Stil des angegebenen Designs.

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>Parameter

*hThema*<br/>
[in] Behandeln Sie die Designdaten eines Fensters oder NULL. Das Framework verwendet das angegebene Design, um den Text zu zeichnen, wenn dieser Parameter nicht NULL ist und Designs unterstützt werden. Andernfalls verwendet das Framework kein Design zum Zeichnen des Texts.

Verwenden Sie die [OpenThemeData-Methode,](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) um ein HTHEME zu erstellen.

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext.

*iPartId*<br/>
[in] Der Kontrollteil mit der gewünschten Textdarstellung. Weitere Informationen finden Sie im Artikel [Parts and States](/windows/win32/controls/parts-and-states)(Teile und Zustände) in der Tabellenspalte „Part“ (Teil). Wenn der Wert 0 lautet, wird der Text in der Standardschriftart oder in einer im Gerätekontext ausgewählten Schriftart gezeichnet.

*iStateId*<br/>
[in] Der Steuerelementstatus, der die gewünschte Textdarstellung hat. Weitere Informationen finden Sie im Artikel [Parts and States](/windows/win32/controls/parts-and-states)(Teile und Zustände) in der Tabellenspalte „States“ (Zustände).

*strText*<br/>
[in] Der zu zeichnende Text.

*Rect*<br/>
[in] Die Grenze des Bereichs, in dem der angegebene Text gezeichnet wird.

*dwFlags*<br/>
[in] Eine bitweise Kombination (OR) von Flags, die angeben, wie der angegebene Text gezeichnet wird.

Wenn der *hTheme-Parameter* unterstützt `NULL` und aktiviert ist, beschreibt der *nFormat-Parameter* der [CDC::DrawText-Methode](../../mfc/reference/cdc-class.md#drawtext) die gültigen Flags. Wenn Designs unterstützt werden, beschreibt der *dwFlags-Parameter* der [DrawThemeTextEx-Methode](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) die gültigen Flags.

*nGlowSize*<br/>
[in] Die Größe eines Glüheffekts, der vor dem Zeichnen des angegebenen Textes auf dem Hintergrund gezeichnet wird. Der Standardwert ist 0.

*clrText*<br/>
[in] Die Farbe, in der der angegebene Text gezeichnet wird. Der Standardwert ist die Standardfarbe.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein Design zum Zeichnen des angegebenen Textes verwendet wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Ein Design definiert den visuellen Stil einer Anwendung. Ein Design wird nicht verwendet, um den Text zu zeichnen, wenn der *hTheme-Parameter* NULL ist oder wenn die [DrawThemeTextEx-Methode](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) nicht unterstützt wird oder wenn die DWM-Komposition [(Desktop Window Manager)](/windows/win32/dwm/dwm-overview) deaktiviert ist.

## <a name="afx_global_dataenableaccessibilitysupport"></a><a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySupport

Aktiviert oder deaktiviert Microsoft Active Accessibility-Unterstützung.

```cpp
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um die Unterstützung für Barrierefreiheit zu aktivieren; FALSE, um die Barrierefreiheitsunterstützung zu deaktivieren. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Active Accessibility ist eine COM-basierte Technologie, die die Zusammenarbeit von Programmen und dem Windows-Betriebssystem mit unterstützenden Technologieprodukten verbessert. Es bietet zuverlässige Methoden zum Offenlegen von Informationen über Benutzeroberflächenelemente. Ein neueres Eingabehilfenmodell namens Microsoft UI Automation ist jetzt jedoch verfügbar. Einen Vergleich der beiden Technologien finden Sie unter [UI Automation und Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Verwenden Sie die [AFX_GLOBAL_DATA::IsAccessibilitySupport-Methode,](#isaccessibilitysupport) um zu bestimmen, ob die Microsoft Active Accessibility-Unterstützung aktiviert ist.

## <a name="afx_global_dataexcludetag"></a><a name="excludetag"></a>AFX_GLOBAL_DATA::ExcludeTag

Entfernt das angegebenen XML-Tagpaar aus einem angegebenen Puffer.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Parameter

*strBuffer*<br/>
[in] Ein Textpuffer.

*lpszTag*<br/>
[in] Der Name eines Paares von öffnenden und schließenden XML-Tags.

*strTag*<br/>
[out] Wenn diese Methode zurückgegeben wird, enthält der *strTag-Parameter* den Text zwischen dem öffnenden und schließenden XML-Tag, der vom Parameter *lpszTag* benannt wird. Alle führenden oder nachfolgenden Leerzeichen werden aus dem Ergebnis getrimmt.

*bIsCharsList*<br/>
[in] TRUE, um Symbole für Escapezeichen im *strTag-Parameter* in tatsächliche Escape-Zeichen zu konvertieren; FALSE, um die Konvertierung nicht durchzuführen. Der Standardwert ist FALSE. Weitere Informationen finden Sie in den Hinweisen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Ein XML-Tag-Paar besteht aus benannten öffnenden und schließenden Tags, die den Anfang und das Ende einer Textausführung im angegebenen Puffer angeben. Der *Parameter strBuffer* gibt den Puffer an, und der *Parameter lpszTag* gibt den Namen der XML-Tags an.

Verwenden Sie die Symbole in der folgenden Tabelle, um einen Satz von Escapezeichen im angegebenen Puffer zu codieren. Geben Sie TRUE für den Parameter *bIsCharsList* an, um die Symbole im *strTag-Parameter* in tatsächliche Escapezeichen zu konvertieren. In der folgenden Tabelle wird das Makro [_T()](../../c-runtime-library/data-type-mappings.md) verwendet, um das Symbol und die Escapezeichenzeichenfolgen anzugeben.

|Symbol|Escapezeichen|
|------------|----------------------|
|_T("\\|_T("t")|
|_T("\\n")|_T("n")|
|_T("\\ér))|_T("r")|
|_T("\\b))|_T("-b")|
|_T("LT")|_T("\<")|
|_T("GT")|_T(">")|
|_T("AMP")|_T("&")|

## <a name="afx_global_datagetcolor"></a><a name="getcolor"></a>AFX_GLOBAL_DATA::GetColor

Ruft die derzeitige Farbe eines angegebenen Benutzeroberflächen-Elements ab.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Parameter

*nColor*<br/>
[in] Ein Wert, der ein Benutzeroberflächenelement angibt, dessen Farbe abgerufen wird. Eine Liste gültiger Werte finden Sie im *nIndex-Parameter* der [GetSysColor-Methode.](/windows/win32/api/winuser/nf-winuser-getsyscolor)

### <a name="return-value"></a>Rückgabewert

Der RGB-Farbwert des angegebenen Benutzeroberflächenelements. Weitere Informationen finden Sie in den Hinweisen.

### <a name="remarks"></a>Bemerkungen

Wenn der *nColor-Parameter* aunter Bereich liegt, ist der Rückgabewert Null. Da Null auch ein gültiger RGB-Wert ist, können Sie diese Methode nicht verwenden, um zu bestimmen, ob eine Systemfarbe vom aktuellen Betriebssystem unterstützt wird. Verwenden Sie stattdessen die [GetSysColorBrush-Methode,](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) die NULL zurückgibt, wenn die Farbe nicht unterstützt wird.

## <a name="afx_global_datagetdirect2dfactory"></a><a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory

Gibt einen Zeiger auf die ID2D1Factory-Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die ID2D1Factory-Schnittstelle, wenn die Erstellung einer Factory erfolgreich ist, oder NULL, wenn die Erstellung fehlschlägt oder das aktuelle Betriebssystem keine D2D-Unterstützung hat.

## <a name="afx_global_datagethandcursor"></a><a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor

Ruft den vordefinierten Cursor ab, der einer Hand ähnelt und dessen Bezeichner IDC_HAND ist.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Rückgabewert

Der Griff des Handcursors.

## <a name="afx_global_datagetnonclientmetrics"></a><a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA::GetNonClientMetrics

Ruft die Metriken ab, die dem Nichtclientbereich von nicht minimierten Fenstern zugeordnet sind.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Parameter

*Informationen*<br/>
[in, out] Eine [NONCLIENTMETRICS-Struktur,](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) die die skalierbaren Metriken enthält, die dem Nichtclientbereich eines nicht minimierten Fensters zugeordnet sind.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

## <a name="afx_global_datagettextheight"></a><a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight

Ruft die Höhe von Textzeichen in der aktuellen Schriftart ab.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parameter

*bHorz*<br/>
[in] TRUE, um die Höhe von Zeichen abzurufen, wenn Text horizontal ausgeführt wird; FALSE, um die Höhe von Zeichen abzurufen, wenn Text vertikal ausgeführt wird. Der Standardwert ist TRUE.

### <a name="return-value"></a>Rückgabewert

Die Höhe der aktuellen Schriftart, die vom Aufsteiger bis zum Absteiger gemessen wird.

## <a name="afx_global_datagetwicfactory"></a><a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory

Gibt einen Zeiger auf die IWICImagingFactory-Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die IWICImagingFactory-Schnittstelle, wenn die Erstellung einer Factory erfolgreich ist, oder NULL, wenn die Erstellung fehlschlägt oder das aktuelle Betriebssystem keine WIC-Unterstützung hat.

## <a name="afx_global_datagetwritefactory"></a><a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory

Gibt einen Zeiger auf die IDWriteFactory-Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die IDWriteFactory-Schnittstelle, wenn die Erstellung einer Factory erfolgreich ist, oder NULL, wenn die Erstellung fehlschlägt oder das aktuelle Betriebssystem keine DirectWrite-Unterstützung hat.

## <a name="afx_global_datainitd2d"></a><a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D

Initialisiert D2D-, DirectWrite- und WIC-Fabriken. Rufen Sie diese Methode vor der Initialisierung des Hauptfensters auf.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parameter

*d2dFactoryType*<br/>
Das Threadingmodell der D2D-Fabrik und die ressourcen, die sie erstellt.

*writeFactoryType*<br/>
Ein Wert, der angibt, ob das Write Factory-Objekt freigegeben oder isoliert wird

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Fabriken intilalizrd, FALSE waren - sonst

## <a name="afx_global_datais32biticons"></a><a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons

Gibt an, ob vordefinierte 32-Bit-Symbole unterstützt werden.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn vordefinierte 32-Bit-Symbole unterstützt werden; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt TRUE zurück, wenn das Framework integrierte 32-Bit-Symbole unterstützt und wenn das Betriebssystem 16 Bit pro Pixel oder mehr unterstützt und Bilder nicht in hohem Kontrast angezeigt werden.

## <a name="afx_global_dataisaccessibilitysupport"></a><a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::IsAccessibilitySupport

Gibt an, ob Microsoft Active Accessibility-Unterstützung aktiviert ist.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Barrierefreiheitsunterstützung aktiviert ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Microsoft Active Accessibility war die frühere Lösung, um Anwendungen zugänglich zu machen. Microsoft UI Automation ist das neue Eingabehilfenmodell für Microsoft Windows und soll den Anforderungen von Hilfstechnologieprodukten und automatisierten Testtools gerecht werden.

Verwenden Sie die [AFX_GLOBAL_DATA::EnableAccessibilitySupport-Methode,](#enableaccessibilitysupport) um die Active Accessibility-Unterstützung zu aktivieren oder zu deaktivieren.

## <a name="afx_global_dataisd2dinitialized"></a><a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::IsD2DInitialisiert

Bestimmt, ob die D2D initialisiert wurde

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn D2D initialisiert wurde; andernfalls FALSE.

## <a name="afx_global_dataisdwmcompositionenabled"></a><a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled

Stellt eine einfache Möglichkeit zum Aufrufen der [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) -Methode von Windows bereit.

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn [die DWM-Komposition (Desktop Window Manager)](/windows/win32/dwm/dwm-overview) aktiviert ist; andernfalls FALSE.

## <a name="afx_global_dataishighcontrastmode"></a><a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode

Gibt an, ob Bilder nur mit hohem Kontrast angezeigt werden.

```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Bilder derzeit im Schwarz- oder Weißmodus mit hohem Kontrast angezeigt werden; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Im schwarzen Modus mit hohem Kontrast sind die Kanten, die dem Licht zugewandt sind, weiß und der Hintergrund schwarz. Im weißen Modus mit hohem Kontrast sind die Kanten, die dem Licht zugewandt sind, schwarz und der Hintergrund weiß.

## <a name="afx_global_dataiswindowslayersupportavailable"></a><a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA::IsWindowsLayerSupportVerfügbar

Gibt an, ob das Betriebssystem überlappende Fenster unterstützt.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn mehrschichtige Fenster unterstützt werden; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn mehrschichtige Fenster unterstützt werden, verwenden *intelligente Docking-Marker* mehrschichtige Fenster.

## <a name="afx_global_datam_busebuiltin32biticons"></a><a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons

Gibt an, ob das Framework vordefinierte 32-Bit-Farbsymbole oder Symbole mit einer niedrigeren Auflösung verwendet.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass das Framework 32-Bit-Farbsymbole verwendet. FALSE gibt Symbole mit niedrigerer Auflösung an. Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor initialisiert dieses Element in TRUE.

Dieser Member muss beim Starten der Anwendung festgelegt werden.

## <a name="afx_global_datam_busesystemfont"></a><a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont

Gibt an, ob eine Systemschriftart für Menüs, Symbolleisten und Menübänder verwendet wird.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, eine Systemschriftart zu verwenden. andernfalls FALSE. Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor initialisiert diesen Member in FALSE.

Das Testen dieses Members ist nicht die einzige Möglichkeit für das Framework, die zu verwendende Schriftart zu bestimmen. Die `AFX_GLOBAL_DATA::UpdateFonts` Methode testet auch Standard- und alternative Schriftarten, um zu bestimmen, welche visuellen Stile auf Menüs, Symbolleisten und Multifunktionsleisten angewendet werden können.

## <a name="afx_global_datam_hcurhand"></a><a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand

Speichert das Handle für den Hand-Cursor.

```
HCURSOR m_hcurHand;
```

## <a name="afx_global_datam_hcurstretch"></a><a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch

Speichert das Handle für den horizontalen Streckungs-Cursor.

```
HCURSOR m_hcurStretch;
```

## <a name="afx_global_datam_hcurstretchvert"></a><a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert

Speichert das Handle für den vertikalen Streckungs-Cursor.

```
HCURSOR m_hcurStretchVert;
```

## <a name="afx_global_datam_hicontool"></a><a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool

Speichert das Handle für das Werkzeugsymbol.

```
HICON m_hiconTool;
```

## <a name="afx_global_datam_nautohidetoolbarmargin"></a><a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin

Gibt den Versatz von der linken Autohide-Symbolleiste zur linken Seite der Dockleiste an.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Bemerkungen

Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor initialisiert dieses Element auf 4 Pixel.

## <a name="afx_global_datam_nautohidetoolbarspacing"></a><a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing

Gibt die Lücke zwischen Symbolleisten zum automatischen Ausblenden an.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Bemerkungen

Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor initialisiert dieses Element auf 14 Pixel.

## <a name="afx_global_datam_ndragframethicknessdock"></a><a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Gibt die Dicke des Ziehrahmens an, der verwendet wird, um den angedockten Zustand anzugeben.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Bemerkungen

Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor initialisiert dieses Element auf 3 Pixel.

## <a name="afx_global_datam_ndragframethicknessfloat"></a><a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat

Gibt die Dicke des Ziehrahmens an, der verwendet wird, um den Gleitzustand anzugeben.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Bemerkungen

Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor initialisiert dieses Element auf 4 Pixel.

## <a name="afx_global_dataonsettingchange"></a><a name="onsettingchange"></a>AFX_GLOBAL_DATA::OnSettingChange

Erkennt den aktuellen Zustand der Funktionen zum automatischen Ausblenden der Menüanimation und Taskleisten auf dem Desktop.

```cpp
void OnSettingChange();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode legt Frameworkvariablen auf den Status bestimmter Attribute des Desktops des Benutzers fest. Diese Methode erkennt den aktuellen Status der Menüanimation, menü fade und Task Bar Autohide-Features.

## <a name="afx_global_dataregisterwindowclass"></a><a name="registerwindowclass"></a>AFX_GLOBAL_DATA::RegisterWindowClass

Registriert die angegebene MFC-Fensterklasse.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Parameter

*lpszClassNamePrefix*<br/>
[in] Der Name der zu registrierenden Fensterklasse.

### <a name="return-value"></a>Rückgabewert

Der qualifizierte Name der registrierten Klasse, wenn diese Methode erfolgreich ist. Andernfalls eine [Ressourcenausnahme](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert ist eine durch Doppelpunkte getrennte Liste der Parameterzeichenfolge *lpszClassNamePrefix* und der hexadezimalen Textdarstellungen der Handles der aktuellen Anwendungsinstanz. der Anwendungscursor, d. d. pfeilcursor, dessen Bezeichner IDC_ARROW ist; und den Hintergrundpinsel. Weitere Informationen zum Registrieren von MFC-Fensterklassen finden Sie unter [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="afx_global_dataresume"></a><a name="resume"></a>AFX_GLOBAL_DATA::Resume

Initialisiert die internen Funktionszeiger für den Zugriff auf Methoden, die Designs und visuelle Stile in Windows unterstützen.

```
BOOL Resume();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE. Im Debugmodus wird diese Methode bestätigt, wenn diese Methode nicht erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn das Framework die [WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast) Nachricht empfängt.

## <a name="afx_global_datasetlayeredattrib"></a><a name="setlayeredattrib"></a>AFX_GLOBAL_DATA::SetLayeredAttrib

Stellt eine einfache Möglichkeit zum Aufrufen der [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) -Methode von Windows bereit.

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*Hwnd*<br/>
[in] Handle zum geschichteten Fenster.

*crKey*<br/>
[in] Der Transparenzfarbschlüssel, den der [Desktopfenster-Manager](/windows/win32/dwm/dwm-overview) zum Verfassen des mehrschichtigen Fensters verwendet.

*bAlpha*<br/>
[in] Der Alphawert, der verwendet wird, um die Deckkraft des ebenen Fensters zu beschreiben.

*dwFlags*<br/>
[in] Eine bitweise Kombination (OR) von Flags, die angeben, welche Methodenparameter verwendet werden sollen. Geben Sie LWA_COLORKEY an, der den *crKey-Parameter* als Transparenzfarbe verwenden soll. Geben Sie LWA_ALPHA an, der den *parameter bAlpha* verwenden soll, um die Deckkraft des layered-Fensters zu bestimmen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

## <a name="afx_global_datasetmenufont"></a><a name="setmenufont"></a>AFX_GLOBAL_DATA::SetMenuFont

Erstellt die angegebene logische Schriftart.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

*lpLogFont*<br/>
[in] Zeiger auf eine Struktur, die die Attribute einer Schriftart enthält.

*bHorz*<br/>
[in] TRUE, um anzugeben, dass der Text horizontal ausgeführt wird; FALSE, um anzugeben, dass der Text vertikal ausgeführt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE. Im Debugmodus wird diese Methode bestätigt, wenn diese Methode nicht erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt eine horizontale reguläre Schriftart, eine unterstrichene Schriftart und eine fett formatierte Schriftart, die in Standardmenüelementen verwendet wird. Diese Methode erstellt optional eine reguläre vertikale Schriftart. Weitere Informationen zu logischen Schriftarten finden Sie unter [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="afx_global_dataupdatefonts"></a><a name="updatefonts"></a>AFX_GLOBAL_DATA::UpdateFonts

Initialisiert die logischen Schriftarten erneut, die vom Framework verwendet werden.

```cpp
void UpdateFonts();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu logischen `CFont::CreateFontIndirect`Schriftarten finden Sie unter .

## <a name="afx_global_dataupdatesyscolors"></a><a name="updatesyscolors"></a>AFX_GLOBAL_DATA::UpdateSysColors

Initialisiert die Farben, die Farbtiefe, die Stifte, die Pinsel und die Bilder, die vom Framework verwendet werden.

```cpp
void UpdateSysColors();
```

## <a name="afx_global_databiswindows7"></a><a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7

Gibt an, ob die Anwendung unter Windows 7 oder höher ausgeführt wird.

```
BOOL bIsWindows7;
```

## <a name="afx_global_dataclractivecaptiongradient"></a><a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA::clrActiveCaptionGradient

Gibt die Farbverlaufsfarbe der aktiven Beschriftung an. Wird im Allgemeinen für andockbare Bereiche verwendet.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="afx_global_dataclrinactivecaptiongradient"></a><a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA::clrInactiveCaptionGradient

Gibt die Farbverlaufsfarbe der inaktiven Beschriftung an. Wird im Allgemeinen für andockbare Bereiche verwendet.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="afx_global_datagetitaskbarlist"></a><a name="getitaskbarlist"></a>AFX_GLOBAL_DATA::GetITaskbarList

Erstellt und speichert in den globalen `ITaskBarList` Daten einen Zeiger auf die Schnittstelle.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `ITaskbarList` die Schnittstelle, wenn die Erstellung eines Taskleistenlistenobjekts erfolgreich ist. NULL, wenn die Erstellung fehlschlägt oder wenn das aktuelle Betriebssystem kleiner als Windows 7 ist.

## <a name="afx_global_datagetitaskbarlist3"></a><a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA::GetITaskbarList3

Erstellt und speichert in den globalen `ITaskBarList3` Daten einen Zeiger auf die Schnittstelle.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `ITaskbarList3` die Schnittstelle, wenn die Erstellung eines Taskleistenlistenobjekts erfolgreich ist. NULL, wenn die Erstellung fehlschlägt oder wenn das aktuelle Betriebssystem kleiner als Windows 7 ist.

## <a name="afx_global_datagetshellautohidebars"></a><a name="getshellautohidebars"></a>AFX_GLOBAL_DATA::GetShellAutohideBars

Bestimmt Positionen von Leisten zum automatischen Ausblenden einer Shell.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Rückgabewert

Ein Ganzzahlwert mit codierten Flags, die Positionen von automatischen Ausblendbalken angeben. Es kann die folgenden Werte kombinieren: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="afx_global_datareleasetaskbarrefs"></a><a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs

Gibt Schnittstellen frei, `GetITaskbarList` `GetITaskbarList3` die über die und Methoden erhalten werden.

```cpp
void ReleaseTaskBarRefs();
```

## <a name="afx_global_datashellcreateitemfromparsingname"></a><a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA::ShellCreateItemFromParsingName

Erstellt und initialisiert ein Shellelementobjekt aus einem Analysenamen.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Parameter

*pszPath*<br/>
[in] Ein Zeiger auf einen Anzeigenamen.

*Pbc*<br/>
Ein Zeiger auf einen Bindungskontext, der den Analysevorgang steuert.

*riid*<br/>
Ein Verweis auf eine Schnittstellen-ID.

*Ppv*<br/>
[out] Wenn diese Funktion zurückkehrt, enthält der in *riid*angeforderte Schnittstellenzeiger . Dies wird `IShellItem` `IShellItem2`in der Regel oder sein.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn erfolgreich; andernfalls einen Fehlerwert.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../hierarchy-chart.md)<br/>
[Strukturen, Stile, Rückrufe und Meldungszuordnungen](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Parts and States](/windows/win32/controls/parts-and-states)<br/>
[CDC::DrawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Desktopfenster-Manager](/windows/win32/dwm/dwm-overview)<br/>
[Enable and Control DWM Composition (Aktivieren und Steuern der DWM-Komposition)](/windows/win32/dwm/composition-ovw)<br/>
[Benutzeroberflächenautomatisierung und Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor-Funktion](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[NONCLIENTMETRICS-Struktur](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
