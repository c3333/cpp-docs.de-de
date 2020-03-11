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
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
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
ms.openlocfilehash: dda3056cbed18ef93e09b52cd9d0a6b00e1db177
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78869915"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA-Struktur

Die `AFX_GLOBAL_DATA` -Struktur enthält Felder und Methoden, mit denen das Framework verwaltet oder die Darstellung und das Verhalten der Anwendung angepasst werden können.

## <a name="syntax"></a>Syntax

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Erstellt eine `AFX_GLOBAL_DATA` -Struktur.|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[AFX_GLOBAL_DATA:: Cleanup](#cleanup)|Gibt Ressourcen frei, die vom Framework zugeordnet werden, z. B. Pinsel, Schriftarten und DLLs.|
|[AFX_GLOBAL_DATA::D 2d1makerotatematrix](#d2d1makerotatematrix)|Erstellt eine Drehtransformation, die sich in einem angegebenen Winkel um einen angegebenen Punkt dreht.|
|[AFX_GLOBAL_DATA::D rawpartbackground](#drawparentbackground)|Zeichnet den Hintergrund des übergeordneten Elements eines Steuerelements im angegebenen Bereich.|
|[AFX_GLOBAL_DATA::D rawtextonglass](#drawtextonglass)|Zeichnet den angegebenen Text im Stil des angegebenen Designs.|
|[AFX_GLOBAL_DATA:: excluenttag](#excludetag)|Entfernt das angegebenen XML-Tagpaar aus einem angegebenen Puffer.|
|[AFX_GLOBAL_DATA:: GetColor](#getcolor)|Ruft die derzeitige Farbe eines angegebenen Benutzeroberflächen-Elements ab.|
|[AFX_GLOBAL_DATA:: GetDirect2dFactory](#getdirect2dfactory)|Gibt einen Zeiger auf die `ID2D1Factory` -Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.|
|[AFX_GLOBAL_DATA:: gethandcursor](#gethandcursor)|Ruft den vordefinierten Cursor ab, der einer Hand ähnelt und dessen Bezeichner `IDC_HAND`lautet.|
|[AFX_GLOBAL_DATA:: getitaskbarlist](#getitaskbarlist)|Erstellt und speichert in den globalen Daten einen Zeiger auf die ITaskBarList-Schnittstelle.|
|[AFX_GLOBAL_DATA:: getitaskbarlist3 ermittelt wurden](#getitaskbarlist3)|Erstellt und speichert in den globalen Daten einen Zeiger auf die ITaskBarList3-Schnittstelle.|
|[AFX_GLOBAL_DATA:: getnonclientmetrics](#getnonclientmetrics)|Ruft die Metriken ab, die dem Nichtclientbereich von nicht minimierten Fenstern zugeordnet sind.|
|[AFX_GLOBAL_DATA:: getshellautohidebars](#getshellautohidebars)|Bestimmt Positionen von Leisten zum automatischen Ausblenden einer Shell.|
|[AFX_GLOBAL_DATA:: gettextheight](#gettextheight)|Ruft die Höhe von Textzeichen in der aktuellen Schriftart ab.|
|[AFX_GLOBAL_DATA:: getwicfactory](#getwicfactory)|Gibt einen Zeiger auf die `IWICImagingFactory` -Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.|
|[AFX_GLOBAL_DATA:: getschreitefactory](#getwritefactory)|Gibt einen Zeiger auf die `IDWriteFactory` -Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.|
|[AFX_GLOBAL_DATA:: IsD2DInitialized](#isd2dinitialized)|Initialisiert die Factorys `D2D`, `DirectWrite`und `WIC` . Rufen Sie diese Methode vor der Initialisierung des Hauptfensters auf.|
|[AFX_GLOBAL_DATA:: Is32BitIcons](#is32biticons)|Gibt an, ob vordefinierte 32-Bit-Symbole unterstützt werden.|
|[AFX_GLOBAL_DATA:: IsD2DInitialized](#isd2dinitialized)|Bestimmt, ob `D2D` initialisiert wurde.|
|[AFX_GLOBAL_DATA:: isdwmcompositionaktivierte](#isdwmcompositionenabled)|Stellt eine einfache Möglichkeit zum Aufrufen der [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) -Methode von Windows bereit.|
|[AFX_GLOBAL_DATA:: ishighcontrastmode](#ishighcontrastmode)|Gibt an, ob Bilder nur mit hohem Kontrast angezeigt werden.|
|[AFX_GLOBAL_DATA:: onsettingchange](#onsettingchange)|Erkennt den aktuellen Zustand der Funktionen zum automatischen Ausblenden der Menüanimation und Taskleisten auf dem Desktop.|
|[AFX_GLOBAL_DATA:: registerwindowclass](#registerwindowclass)|Registriert die angegebene MFC-Fensterklasse.|
|[AFX_GLOBAL_DATA:: releasetaskbarrefs](#releasetaskbarrefs)|Gibt Schnittstellen frei, die durch die Methoden GetITaskbarList und GetITaskbarList3 ermittelt wurden.|
|[AFX_GLOBAL_DATA:: Resume](#resume)|Initialisiert die internen Funktionszeiger für den Zugriff auf Methoden, die [Designs und visuelle Stile](/windows/win32/Controls/visual-styles-overview)in Windows unterstützen.|
|[AFX_GLOBAL_DATA:: setlayeredatdib](#setlayeredattrib)|Stellt eine einfache Möglichkeit zum Aufrufen der [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) -Methode von Windows bereit.|
|[AFX_GLOBAL_DATA:: setmenufont](#setmenufont)|Erstellt die angegebene logische Schriftart.|
|[AFX_GLOBAL_DATA:: shellkreateitemfromparser Name](#shellcreateitemfromparsingname)|Erstellt und initialisiert ein Shellelementobjekt aus einem Analysenamen.|
|[AFX_GLOBAL_DATA:: updatefonts](#updatefonts)|Initialisiert die logischen Schriftarten erneut, die vom Framework verwendet werden.|
|[AFX_GLOBAL_DATA:: updatesyscolors](#updatesyscolors)|Initialisiert die Farben, die Farbtiefe, die Stifte, die Pinsel und die Bilder, die vom Framework verwendet werden.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[AFX_GLOBAL_DATA:: enableaccessibilitysupport](#enableaccessibilitysupport)|Aktiviert oder deaktiviert Microsoft Active Accessibility-Unterstützung. Active Accessibility stellt zuverlässige Methoden zum Anzeigen von Informationen über Benutzeroberflächenelemente bereit.|
|[AFX_GLOBAL_DATA:: isaccessibilitysupport](#isaccessibilitysupport)|Gibt an, ob Microsoft Active Accessibility-Unterstützung aktiviert ist.|
|[AFX_GLOBAL_DATA:: iswindowslayersupportavailable](#iswindowslayersupportavailable)|Gibt an, ob das Betriebssystem überlappende Fenster unterstützt.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[AFX_GLOBAL_DATA:: bisosalphablendingsupport](#bisosalphablendingsupport)|Gibt an, ob das aktuelle Betriebssystem Alphablending unterstützt.|
|[AFX_GLOBAL_DATA:: bIsWindows7](#biswindows7)|Gibt an, ob die Anwendung unter dem Betriebssystem Windows 7 oder höher ausgeführt wird.|
|[AFX_GLOBAL_DATA:: clractivecaptiongradient](#clractivecaptiongradient)|Gibt den Farbverlauf der aktiven Beschriftung an. Wird im Allgemeinen für andockbare Bereiche verwendet.|
|[AFX_GLOBAL_DATA:: clrinactivecaptiongradient](#clrinactivecaptiongradient)|Gibt den Farbverlauf der inaktiven Beschriftung an. Wird im Allgemeinen für andockbare Bereiche verwendet.|
|[AFX_GLOBAL_DATA:: m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Gibt an, ob das Framework vordefinierte 32-Bit-Farbsymbole oder Symbole mit einer niedrigeren Auflösung verwendet.|
|[AFX_GLOBAL_DATA:: m_bUseSystemFont](#m_busesystemfont)|Gibt an, ob eine Systemschriftart für Menüs, Symbolleisten und Menübänder verwendet wird.|
|[AFX_GLOBAL_DATA:: m_hcurHand](#m_hcurhand)|Speichert das Handle für den Hand-Cursor.|
|[AFX_GLOBAL_DATA:: m_hcurStretch](#m_hcurstretch)|Speichert das Handle für den horizontalen Streckungs-Cursor.|
|[AFX_GLOBAL_DATA:: m_hcurStretchVert](#m_hcurstretchvert)|Speichert das Handle für den vertikalen Streckungs-Cursor.|
|[AFX_GLOBAL_DATA:: m_hiconTool](#m_hicontool)|Speichert das Handle für das Werkzeugsymbol.|
|[AFX_GLOBAL_DATA:: m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Gibt den Offset von der äußersten linken Symbolleiste zum automatischen Ausblenden von der linken Seite der Andockleiste an.|
|[AFX_GLOBAL_DATA:: m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Gibt die Lücke zwischen Symbolleisten zum automatischen Ausblenden an.|
|[AFX_GLOBAL_DATA:: m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Gibt die Breite des Ziehrahmens an, mit dem der angedockten Zustand übermittelt wird.|
|[AFX_GLOBAL_DATA:: m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Gibt die Breite des Ziehrahmens an, mit dem der unverankerte Zustand übermittelt wird.|

### <a name="remarks"></a>Bemerkungen

Die meisten Daten in der `AFX_GLOBAL_DATA` -Struktur werden beim Start der Anwendung initialisiert.

### <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxglobals.h

## <a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA:: bisosalphablendingsupport

Gibt an, ob das Betriebssystem Alpha Blending unterstützt.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass Alpha Blending unterstützt wird. andernfalls false.

## <a name="cleanup"></a>AFX_GLOBAL_DATA:: Cleanup

Gibt Ressourcen frei, die vom Framework zugeordnet werden, z. B. Pinsel, Schriftarten und DLLs.

```
void CleanUp();
```

## <a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D 2d1makerotatematrix

Erstellt eine Drehtransformation, die sich in einem angegebenen Winkel um einen angegebenen Punkt dreht.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Parameter

*Ultra*<br/>
Der Winkel der Drehung im Uhrzeigersinn in Grad.

*Tagesstätte*<br/>
Der Punkt, um den die Drehung erfolgen soll.

*Ko*<br/>
Wenn diese Methode zurückgegeben wird, enthält Sie die neue Rotations Transformation. Sie müssen Speicher für diesen Parameter zuweisen.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn erfolgreich, oder andernfalls einen Fehlerwert.

## <a name="drawparentbackground"></a>AFX_GLOBAL_DATA::D rawpartbackground

Zeichnet den Hintergrund des übergeordneten Elements eines Steuerelements im angegebenen Bereich.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
in Zeiger auf das Fenster eines Steuer Elements.

*pDC*<br/>
in Zeiger auf einen Gerätekontext.

*lprect*<br/>
in Zeiger auf ein Rechteck, das den zu zeichnenden Bereich umschließt. Der Standardwert ist NULL.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

## <a name="drawtextonglass"></a>AFX_GLOBAL_DATA::D rawtextonglass

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

*htheme*<br/>
in Handle zu den Designdaten eines Fensters oder NULL. Das Framework verwendet das angegebene Design, um den Text zu zeichnen, wenn dieser Parameter nicht NULL ist und Designs unterstützt werden. Andernfalls verwendet das Framework kein Design zum Zeichnen des Texts.

Verwenden Sie die [openfomedata](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) -Methode, um ein HTHEME zu erstellen.

*pDC*<br/>
in Zeiger auf einen Gerätekontext.

*ipartid*<br/>
in Der Steuerelement Teil, der über die gewünschte Textdarstellung verfügt. Weitere Informationen finden Sie im Artikel [Parts and States](/windows/win32/controls/parts-and-states)(Teile und Zustände) in der Tabellenspalte „Part“ (Teil). Wenn der Wert 0 lautet, wird der Text in der Standardschriftart oder in einer im Gerätekontext ausgewählten Schriftart gezeichnet.

*istatus Eid*<br/>
in Der Steuerelement Zustand, der die gewünschte Textdarstellung aufweist. Weitere Informationen finden Sie im Artikel [Parts and States](/windows/win32/controls/parts-and-states)(Teile und Zustände) in der Tabellenspalte „States“ (Zustände).

*Text*<br/>
in Der zu zeichnende Text.

*Rect*<br/>
in Die Grenze des Bereichs, in dem der angegebene Text gezeichnet wird.

*dwFlags*<br/>
in Eine bitweise Kombination (or) von Flags, die angeben, wie der angegebene Text gezeichnet wird.

Wenn der *htheme* -Parameter `NULL` ist oder wenn Designs nicht unterstützt und aktiviert werden, beschreibt der *nformat* -Parameter der [CDC::D rawtext](../../mfc/reference/cdc-class.md#drawtext) -Methode die gültigen Flags. Wenn Designs unterstützt werden, beschreibt der *dwFlags* -Parameter der [drawdermetextex](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) -Methode die gültigen Flags.

*nglowsize*<br/>
in Die Größe eines Glanz Effekts, der auf dem Hintergrund gezeichnet wird, bevor der angegebene Text gezeichnet wird. Der Standardwert ist 0.

*clrtext*<br/>
in Die Farbe, in der der angegebene Text gezeichnet wird. Der Standardwert ist die Standardfarbe.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn zum Zeichnen des angegebenen Texts ein Design verwendet wird. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Ein Design definiert den visuellen Stil einer Anwendung. Ein Design wird nicht verwendet, um den Text zu zeichnen, wenn der *htheme* -Parameter NULL ist, oder wenn die [drawdermetextex](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) -Methode nicht unterstützt wird oder wenn [Desktopfenster-Manager](/windows/win32/dwm/dwm-overview) (DWM)-Komposition deaktiviert ist.

## <a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA:: enableaccessibilitysupport

Aktiviert oder deaktiviert Microsoft Active Accessibility-Unterstützung.

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*benabel*<br/>
in TRUE, um die Barrierefreiheits Unterstützung zu aktivieren; FALSE zum Deaktivieren der Barrierefreiheits Unterstützung. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Active Accessibility ist eine COM-basierte Technologie, die die Zusammenarbeit von Programmen und Windows-Betriebssystemen mit Hilfstechnologieprodukten verbessert. Es stellt zuverlässige Methoden zum verfügbar machen von Informationen über Benutzeroberflächen Elemente bereit. Ein neueres Barrierefreiheits Modell namens Microsoft UI Automation ist nun jedoch verfügbar. Einen Vergleich der beiden Technologien finden Sie unter [UI Automation and Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Verwenden Sie die [AFX_GLOBAL_DATA:: isaccessibilitysupport](#isaccessibilitysupport) -Methode, um zu bestimmen, ob die Unterstützung von Microsoft Active Accessibility aktiviert ist.

## <a name="excludetag"></a>AFX_GLOBAL_DATA:: excluenttag

Entfernt das angegebenen XML-Tagpaar aus einem angegebenen Puffer.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Parameter

*"strinbuffer"*<br/>
in Ein Text Puffer.

*lpsztag*<br/>
in Der Name eines Paares von öffnenden und schließenden XML-Tags.

*-Tag*<br/>
vorgenommen Wenn diese Methode zurückgegeben wird, enthält der Parameter " *strintag* " den Text zwischen den öffnenden und schließenden XML-Tags, die durch den *lpsztag* -Parameter benannt werden. Alle führenden oder nachfolgenden Leerzeichen werden aus dem Ergebnis abgeschnitten.

*bischarslist*<br/>
in TRUE, wenn Symbole für Escapezeichen im Parameter " *strintag* " in tatsächliche Escapezeichen konvertiert werden sollen. FALSE: die Konvertierung wird nicht durchgeführt. Der Standardwert ist false. Weitere Informationen finden Sie in den Hinweisen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Ein XML-Tagpaar besteht aus benannten öffnenden und schließenden Tags, die den Anfang und das Ende einer Textlauf im angegebenen Puffer angeben. Der Parameter " *strinbuffer* " gibt den Puffer an, und der *lpsztag* -Parameter gibt den Namen der XML-Tags an.

Verwenden Sie die Symbole in der folgenden Tabelle, um einen Satz von Escapezeichen im angegebenen Puffer zu codieren. Geben Sie true für den *bischarslist* -Parameter an, um die Symbole im " *strintag* "-Parameter in tatsächliche Escapezeichen zu konvertieren. In der folgenden Tabelle wird das [_T ()](../../c-runtime-library/data-type-mappings.md) -Makro verwendet, um das Symbol und die Escapezeichenfolgen anzugeben.

|Symbol|Escapezeichen|
|------------|----------------------|
|_T ("\\\t")|_T ("\t")|
|_T ("\\\n")|_T ("\n")|
|_T ("\\\r")|_T ("\r")|
|_T ("\\\b")|_T("\b")|
|_T ("lt")|_T ("\<")|
|_T("GT")|_T (">")|
|_T ("amp")|_T ("&")|

## <a name="getcolor"></a>AFX_GLOBAL_DATA:: GetColor

Ruft die derzeitige Farbe eines angegebenen Benutzeroberflächen-Elements ab.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Parameter

*ncolor*<br/>
in Ein-Wert, der ein Benutzeroberflächen Element angibt, dessen Farbe abgerufen wird. Eine Liste gültiger Werte finden Sie unter dem *nIndex* -Parameter der [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) -Methode.

### <a name="return-value"></a>Rückgabewert

Der RGB-Farbwert des angegebenen Benutzeroberflächen Elements. Weitere Informationen finden Sie in den Hinweisen.

### <a name="remarks"></a>Bemerkungen

Wenn der *ncolor* -Parameter außerhalb des gültigen Bereichs liegt, ist der Rückgabewert 0 (null). Da NULL auch ein gültiger RGB-Wert ist, können Sie diese Methode nicht verwenden, um zu bestimmen, ob eine System Farbe vom aktuellen Betriebssystem unterstützt wird. Verwenden Sie stattdessen die [getsyscolorbrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) -Methode, die NULL zurückgibt, wenn die Farbe nicht unterstützt wird.

## <a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA:: GetDirect2dFactory

Gibt einen Zeiger auf die ID2D1Factory-Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die ID2D1Factory-Schnittstelle, wenn die Erstellung einer Factory erfolgreich ist, oder NULL, wenn die Erstellung fehlschlägt oder das aktuelle Betriebs System keine D2D-Unterstützung

## <a name="gethandcursor"></a>AFX_GLOBAL_DATA:: gethandcursor

Ruft den vordefinierten Cursor ab, der einer Hand ähnelt und dessen Bezeichner IDC_HAND ist.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Rückgabewert

Das Handle des Hand Cursors.

## <a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA:: getnonclientmetrics

Ruft die Metriken ab, die dem Nichtclientbereich von nicht minimierten Fenstern zugeordnet sind.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Parameter

*info*<br/>
[in, out] Eine [nonclientmetrics](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) -Struktur, die die skalierbaren Metriken enthält, die dem nicht-Client Bereich eines nicht minimierten Fensters zugeordnet sind.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

## <a name="gettextheight"></a>AFX_GLOBAL_DATA:: gettextheight

Ruft die Höhe von Textzeichen in der aktuellen Schriftart ab.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parameter

*bhorz*<br/>
in TRUE, wenn die Höhe von Zeichen beim horizontalen Ausführen von Text abgerufen werden soll. FALSE zum Abrufen der Höhe von Zeichen, wenn der Text vertikal ausgeführt wird. Der Standardwert ist TRUE.

### <a name="return-value"></a>Rückgabewert

Die Höhe der aktuellen Schriftart, die von seinem Vorgänger auf seinen descender-Wert gemessen wird.

## <a name="getwicfactory"></a>AFX_GLOBAL_DATA:: getwicfactory

Gibt einen Zeiger auf die IWICImagingFactory-Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die IWICImagingFactory-Schnittstelle, wenn die Erstellung einer Factory erfolgreich ist, oder NULL, wenn die Erstellung fehlschlägt oder das aktuelle Betriebs System keine WIC-Unterstützung hat.

## <a name="getwritefactory"></a>AFX_GLOBAL_DATA:: getschreitefactory

Gibt einen Zeiger auf die idschreitefactory-Schnittstelle zurück, die in den globalen Daten gespeichert ist. Wenn die Schnittstelle nicht initialisiert wurde, wird sie mit den Standardparametern erstellt.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die idschreitefactory-Schnittstelle, wenn die Erstellung einer Factory erfolgreich ist, oder NULL, wenn die Erstellung fehlschlägt oder das aktuelle Betriebs System keine DirectWrite-Unterstützung hat

## <a name="initd2d"></a>AFX_GLOBAL_DATA:: InitD2D

Initialisiert D2D-, DirectWrite-und WIC-Factorys. Rufen Sie diese Methode vor der Initialisierung des Hauptfensters auf.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parameter

*d2dFactoryType*<br/>
Das Threading Modell der D2D Factory und der von ihr erstellten Ressourcen.

*"Write"-Typ*<br/>
Ein-Wert, der angibt, ob das Write Factory-Objekt freigegeben oder isoliert wird.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Factorys intilalizrd sind, andernfalls false.

## <a name="is32biticons"></a>AFX_GLOBAL_DATA:: Is32BitIcons

Gibt an, ob vordefinierte 32-Bit-Symbole unterstützt werden.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn vordefinierte 32-Bit-Symbole unterstützt werden. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt "true" zurück, wenn das Framework integrierte 32-Bit-Symbole unterstützt, und wenn das Betriebssystem 16 Bits pro Pixel oder mehr unterstützt, und wenn Bilder im hohen Kontrast nicht angezeigt werden.

## <a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA:: isaccessibilitysupport

Gibt an, ob Microsoft Active Accessibility-Unterstützung aktiviert ist.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Barrierefreiheits Unterstützung aktiviert ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Microsoft Active Accessibility war die frühere Lösung, mit der Anwendungen zugänglich gemacht werden konnten. Microsoft UI Automation ist das neue Barrierefreiheits Modell für Microsoft Windows und soll den Anforderungen von Hilfstechnologieprodukten und automatisierten Testtools gerecht werden.

Verwenden Sie die [AFX_GLOBAL_DATA:: enableaccessibilitysupport](#enableaccessibilitysupport) -Methode, um Active Accessibility-Unterstützung zu aktivieren oder zu deaktivieren.

## <a name="isd2dinitialized"></a>AFX_GLOBAL_DATA:: IsD2DInitialized

Bestimmt, ob D2D initialisiert wurde.

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn D2D initialisiert wurde. andernfalls false.

## <a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA:: isdwmcompositionaktivierte

Stellt eine einfache Möglichkeit zum Aufrufen der [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) -Methode von Windows bereit.

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Komposition von [Desktopfenster-Manager](/windows/win32/dwm/dwm-overview) (DWM) aktiviert ist. andernfalls false.

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA:: ishighcontrastmode

Gibt an, ob Bilder nur mit hohem Kontrast angezeigt werden.
```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn derzeit Bilder im Schwarzen oder weißen Modus mit hohem Kontrast angezeigt werden. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Im schwarz-Modus mit hohem Kontrast sind Kanten mit dem Licht weiß, und der Hintergrund ist schwarz. Im Modus für weiße hohe Kontraste sind Kanten mit dem Licht schwarz, und der Hintergrund ist weiß.

## <a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA:: iswindowslayersupportavailable

Gibt an, ob das Betriebssystem überlappende Fenster unterstützt.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn überlappende Fenster unterstützt werden. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn überlappende Fenster unterstützt werden, verwenden *smardockmarker* überlappende Fenster.

## <a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA:: m_bUseBuiltIn32BitIcons

Gibt an, ob das Framework vordefinierte 32-Bit-Farbsymbole oder Symbole mit einer niedrigeren Auflösung verwendet.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass das Framework 32-Bit-Farbsymbole verwendet. FALSE gibt Symbole mit niedrigerer Auflösung an. Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`-Konstruktor initialisiert diesen Member mit true.

Dieser Member muss beim Anwendungsstart festgelegt werden.

## <a name="m_busesystemfont"></a>AFX_GLOBAL_DATA:: m_bUseSystemFont

Gibt an, ob eine Systemschriftart für Menüs, Symbolleisten und Menübänder verwendet wird.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass eine System Schriftart verwendet werden soll. andernfalls false. Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`-Konstruktor initialisiert diesen Member mit false.

Das Testen dieses Members ist nicht die einzige Möglichkeit für das Framework, die zu verwendende Schriftart zu bestimmen. Die `AFX_GLOBAL_DATA::UpdateFonts`-Methode testet auch Standard-und alternative Schriftarten, um zu bestimmen, welche visuellen Stile für Menüs, Symbolleisten und Menü Bänder verfügbar sind.

## <a name="m_hcurhand"></a>AFX_GLOBAL_DATA:: m_hcurHand

Speichert das Handle für den Hand-Cursor.

```
HCURSOR m_hcurHand;
```

## <a name="m_hcurstretch"></a>AFX_GLOBAL_DATA:: m_hcurStretch

Speichert das Handle für den horizontalen Streckungs-Cursor.

```
HCURSOR m_hcurStretch;
```

## <a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA:: m_hcurStretchVert

Speichert das Handle für den vertikalen Streckungs-Cursor.

```
HCURSOR m_hcurStretchVert;
```

## <a name="m_hicontool"></a>AFX_GLOBAL_DATA:: m_hiconTool

Speichert das Handle für das Werkzeugsymbol.

```
HICON m_hiconTool;
```

## <a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA:: m_nAutoHideToolBarMargin

Gibt den Offset von der äußersten linken Symbolleiste zum automatischen Ausblenden auf der linken Seite der Andock Leiste an.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Bemerkungen

Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`-Konstruktor initialisiert diesen Member auf 4 Pixel.

## <a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA:: m_nAutoHideToolBarSpacing

Gibt die Lücke zwischen Symbolleisten zum automatischen Ausblenden an.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Bemerkungen

Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`-Konstruktor initialisiert diesen Member mit 14 Pixeln.

## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA:: m_nDragFrameThicknessDock

Gibt die Stärke des ziehrahmens an, der verwendet wird, um den angedockten Zustand anzugeben.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Bemerkungen

Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`-Konstruktor initialisiert diesen Member auf 3 Pixel.

## <a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA:: m_nDragFrameThicknessFloat

Gibt die Stärke des ziehrahmens an, der verwendet wird, um den Gleit Komma Zustand anzugeben.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Bemerkungen

Der `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`-Konstruktor initialisiert diesen Member auf 4 Pixel.

## <a name="onsettingchange"></a>AFX_GLOBAL_DATA:: onsettingchange

Erkennt den aktuellen Zustand der Funktionen zum automatischen Ausblenden der Menüanimation und Taskleisten auf dem Desktop.

```
void OnSettingChange();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode legt frameworkvariablen auf den Zustand bestimmter Attribute des Benutzer Desktops fest. Diese Methode erkennt den aktuellen Zustand der Features Menü Animation, Menü ausblenden und Aufgaben Leiste automatisch ausblenden.

## <a name="registerwindowclass"></a>AFX_GLOBAL_DATA:: registerwindowclass

Registriert die angegebene MFC-Fensterklasse.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Parameter

*lpszclassnameprefix*<br/>
in Der Name der Fenster Klasse, die registriert werden soll.

### <a name="return-value"></a>Rückgabewert

Der qualifizierte Name der registrierten Klasse, wenn diese Methode erfolgreich ist. andernfalls eine [Ressourcen Ausnahme](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert ist eine durch Doppelpunkte getrennte Liste der *lpszclassnameprefix* -Parameter Zeichenfolge und der hexadezimalen Textdarstellungen der Handles der aktuellen Anwendungs Instanz. der Anwendungs Cursor, bei dem es sich um den Pfeilcursor handelt, dessen Bezeichner IDC_ARROW ist. und den Hintergrund Pinsel. Weitere Informationen zum Registrieren von MFC-Fenster Klassen finden Sie unter [afxregisterclass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="resume"></a>AFX_GLOBAL_DATA:: Resume

Initialisiert die internen Funktionszeiger für den Zugriff auf Methoden, die Designs und visuelle Stile in Windows unterstützen.

```
BOOL Resume();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false. Im Debugmodus bestätigt diese Methode, wenn diese Methode nicht erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn das Framework die [WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast) Nachricht empfängt.

## <a name="setlayeredattrib"></a>AFX_GLOBAL_DATA:: setlayeredatdib

Stellt eine einfache Möglichkeit zum Aufrufen der [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) -Methode von Windows bereit.

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*HWND*<br/>
in Handle für das geschichtete Fenster.

*crkey*<br/>
in Der Transparenz Farbschlüssel, den der [Desktopfenster-Manager](/windows/win32/dwm/dwm-overview) verwendet, um das überlappende Fenster zu verfassen.

*bAlpha*<br/>
in Der Alpha-Wert, der verwendet wird, um die Deckkraft des geschichteten Fensters zu beschreiben.

*dwFlags*<br/>
in Eine bitweise Kombination (or) von Flags, die angeben, welche Methoden Parameter verwendet werden sollen. Geben Sie LWA_COLORKEY an, dass der *crkey* -Parameter als Transparenz Farbe verwendet werden soll. Geben Sie LWA_ALPHA an, um den *bAlpha* -Parameter zu verwenden, um die Deckkraft des geschichteten Fensters zu bestimmen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

## <a name="setmenufont"></a>AFX_GLOBAL_DATA:: setmenufont

Erstellt die angegebene logische Schriftart.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

*lplogfont*<br/>
in Ein Zeiger auf eine-Struktur, die die Attribute einer Schriftart enthält.

*bhorz*<br/>
in TRUE, um anzugeben, dass der Text horizontal ausgeführt wird. FALSE, um anzugeben, dass der Text vertikal ausgeführt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false. Im Debugmodus bestätigt diese Methode, wenn diese Methode nicht erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt eine horizontale reguläre Schriftart, eine unterstrichene Schriftart und eine Fett formatierte Schriftart, die in Standardmenü Elementen verwendet wird. Diese Methode erstellt optional eine reguläre vertikale Schriftart. Weitere Informationen zu logischen Schriftarten finden Sie unter [CFont:: kreatefontindirekt](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="updatefonts"></a>AFX_GLOBAL_DATA:: updatefonts

Initialisiert die logischen Schriftarten erneut, die vom Framework verwendet werden.

```
void UpdateFonts();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu logischen Schriftarten finden Sie unter `CFont::CreateFontIndirect`.

## <a name="updatesyscolors"></a>AFX_GLOBAL_DATA:: updatesyscolors

Initialisiert die Farben, die Farbtiefe, die Stifte, die Pinsel und die Bilder, die vom Framework verwendet werden.

```
void UpdateSysColors();
```

## <a name="biswindows7"></a>AFX_GLOBAL_DATA:: bIsWindows7

Gibt an, ob die Anwendung unter Windows 7 oder höher ausgeführt wird.

```
BOOL bIsWindows7;
```

## <a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA:: clractivecaptiongradient

Gibt die Farbverlaufs Farbe der aktiven Beschriftung an. Wird im Allgemeinen für andockbare Bereiche verwendet.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA:: clrinactivecaptiongradient

Gibt die Farbverlaufs Farbe der inaktiven Beschriftung an. Wird im Allgemeinen für andockbare Bereiche verwendet.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="getitaskbarlist"></a>AFX_GLOBAL_DATA:: getitaskbarlist

Erstellt und speichert in den globalen Daten einen Zeiger auf die `ITaskBarList`-Schnittstelle.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die `ITaskbarList`-Schnittstelle, wenn die Erstellung eines Aufgaben leisten Listen Objekts erfolgreich ist. NULL, wenn die Erstellung fehlschlägt oder wenn das aktuelle Betriebs System kleiner als Windows 7 ist.

## <a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA:: getitaskbarlist3 ermittelt wurden

Erstellt und speichert in den globalen Daten einen Zeiger auf die `ITaskBarList3`-Schnittstelle.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die `ITaskbarList3`-Schnittstelle, wenn die Erstellung eines Aufgaben leisten Listen Objekts erfolgreich ist. NULL, wenn die Erstellung fehlschlägt oder wenn das aktuelle Betriebs System kleiner als Windows 7 ist.

## <a name="getshellautohidebars"></a>AFX_GLOBAL_DATA:: getshellautohidebars

Bestimmt Positionen von Leisten zum automatischen Ausblenden einer Shell.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Rückgabewert

Ein ganzzahliger Wert mit codierten Flags, die Positionen von automatisch Ausblend enden leisten angeben. Sie kann die folgenden Werte kombinieren: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA:: releasetaskbarrefs

Gibt Schnittstellen frei, die durch die Methoden `GetITaskbarList` und `GetITaskbarList3` abgerufen werden.

```
void ReleaseTaskBarRefs();
```

## <a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA:: shellkreateitemfromparser Name

Erstellt und initialisiert ein Shellelementobjekt aus einem Analysenamen.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Parameter

*pszpath*<br/>
in Ein Zeiger auf einen anzeigen Amen.

*PBC*<br/>
Ein Zeiger auf einen Bindungs Kontext, der den Verarbeitungsvorgang steuert.

*riid*<br/>
Ein Verweis auf eine Schnittstellen-ID.

*PPV*<br/>
vorgenommen Wenn diese Funktion zurückgegeben wird, enthält Sie den in *riid*angeforderten Schnittstellen Zeiger. Dabei handelt es sich in der Regel um `IShellItem` oder `IShellItem2`.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn erfolgreich; andernfalls ein Fehlerwert.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../hierarchy-chart.md)<br/>
[Strukturen, Stile, Rückrufe und Meldungszuordnungen](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Teile und Zustände](/windows/win32/controls/parts-and-states)<br/>
[CDC::D rawtext](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Desktopfenster-Manager](/windows/win32/dwm/dwm-overview)<br/>
[Aktivieren und Steuern der DWM-Komposition](/windows/win32/dwm/composition-ovw)<br/>
[Benutzeroberflächenautomatisierung und Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor-Funktion](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[Getsyscolorbrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[Nonclientmetrics-Struktur](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[Afxregisterclass](application-information-and-management.md#afxregisterclass)<br/>
[Afxthrowresourceexception](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
