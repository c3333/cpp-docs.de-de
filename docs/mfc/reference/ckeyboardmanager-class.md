---
title: CKeyboardManager-Klasse
ms.date: 11/04/2016
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
ms.openlocfilehash: 5d0f544943cc8584960bb2668ee7ce326547e2fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372314"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager-Klasse

Verwaltet Tastenkombinationstabellen für das Hauptrahmenfenster und die untergeordneten Rahmenfenster.

## <a name="syntax"></a>Syntax

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Erstellt ein `CKeyboardManager`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CKeyboardManager::Bereinigung](#cleanup)|Löscht die Tastenkombinationstabellen.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Ruft die Standardverknüpfungstaste für den angegebenen Befehl und das angegebene Fenster ab.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Bestimmt, ob ein Schlüssel von der Beschleunigertabelle behandelt wird.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Gibt an, ob ein Zeichen druckbar ist.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Gibt an, ob in Menüs alle Tastenkombinationen für einen Befehl oder nur die Standard-Tastenkombination angezeigt werden.|
|[CKeyboardManager::LoadState](#loadstate)|Lädt die Tastenkombinationstabellen aus der Windows-Registrierung.|
|[CKeyboardManager::ResetAlle](#resetall)|Lädt die Tastenkombinationstabellen aus der Anwendungsressource neu.|
|[CKeyboardManager::SaveState](#savestate)|Speichert die Tastenkombinationstabellen in der Windows-Registrierung.|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Gibt an, ob das Framework alle Tastenkombinationen für alle Befehle oder eine einzelne Tastenkombination für jeden Befehl anzeigt. Diese Methode wirkt sich nicht auf Befehle aus, denen nur eine Tastenkombination zugeordnet ist.|
|[CKeyboardManager::TranslateCharToupper](#translatechartoupper)|Konvertiert ein Zeichen in sein oberes Register.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Aktualisiert eine Tastenkombinationstabelle mit einer neuen Verknüpfungsschlüsseltabelle.|

## <a name="remarks"></a>Bemerkungen

Mit den Membern dieser Klasse können Sie Tastenkombinationstabellen in der Windows-Registrierung speichern und laden, eine Vorlage verwenden, um die Kurzschnittschlüsseltabellen zu aktualisieren, und die Standardschlüsselkombination für einen Befehl in einem Rahmenfenster finden. Darüber hinaus `CKeyboardManager` können Sie mit dem Objekt steuern, wie dem Benutzer Tastenkombinationen angezeigt werden.

Sie sollten ein `CKeyboardManager` Objekt nicht manuell erstellen. Sie wird automatisch durch das Framework Ihrer Anwendung erstellt. Sie sollten jedoch [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) während des Initialisierungsprozesses Ihrer Anwendung aufrufen. Um einen Zeiger auf den Tastaturmanager für Ihre Anwendung zu erhalten, rufen Sie [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)an.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie `CKeyboardManager` Sie `CWinAppEx` einen Zeiger auf ein Objekt aus einer Klasse abrufen und alle Tastenkombinationen anzeigen, die Menübefehlen zugeordnet sind. Dieser Codeausschnitt ist Teil des [Beispiels für benutzerdefinierte Seiten](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxkeyboardmanager.h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a>CKeyboardManager::CKeyboardManager

Erstellt ein `CKeyboardManager`-Objekt.

```
CKeyboardManager();
```

### <a name="remarks"></a>Bemerkungen

In den meisten Fällen müssen Sie `CKeyboardManager` keine direkt erstellen. Standardmäßig erstellt das Framework eine für Sie. Um einen Zeiger auf `CKeyboardManager`die zu erhalten, rufen Sie [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)an. Wenn Sie eine manuell erstellen, müssen Sie sie mit der Methode [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)initialisieren.

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a>CKeyboardManager::Bereinigung

Gibt die `CKeyboardManager` Ressourcen frei und löscht alle Verknüpfungsschlüsselzuordnungen.

```
static void CleanUp();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu Tastenkombinationen finden Sie unter [Tastatur- und Mausanpassung](../../mfc/keyboard-and-mouse-customization.md).

Sie müssen diese Funktion nicht aufrufen, wenn ihre Anwendung beendet wird, da das Framework sie während des Anwendungs-Exits automatisch aufruft.

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a>CKeyboardManager::FindDefaultAccelerator

Ruft die Standardverknüpfungstaste für den angegebenen Befehl und das angegebene Fenster ab.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID.

*Str*<br/>
[out] Ein Verweis `CString` auf ein Objekt.

*pWndFrame*<br/>
[in] Ein Zeiger auf ein Rahmenfenster.

*bIsDefaultFrame*<br/>
[in] Gibt an, ob das Rahmenfenster das Standardrahmenfenster ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Verknüpfung gefunden wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode sucht den von *uiCmd* angegebenen Befehl und ruft die Standard-Tastenkombination ab. Anschließend nimmt die Methode die Zeichenfolge, die dieser Tastenkombination zugeordnet ist, und schreibt den Wert in den Parameter *str.*

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a>CKeyboardManager::IsKeyHandled

Bestimmt, ob der angegebene Schlüssel von der [CKeyboardManager-Klasse](../../mfc/reference/ckeyboardmanager-class.md)behandelt wird.

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*nKey*|[in] Der zu überprüfende Schlüssel.|
|*fVirt*|[in] Gibt das Verhalten der Tastenkombination an. Eine Liste möglicher Werte finden Sie unter [ACCEL Structure](/windows/win32/api/winuser/ns-winuser-accel).|
|*pWndFrame*|[in] Ein Rahmenfenster. Diese Methode bestimmt, ob eine Tastenkombination in diesem Frame behandelt wird.|
|*bIsDefaultFrame*|[in] Ein boolescher Parameter, der angibt, ob *pWndFrame* das Standardrahmenfenster ist.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Tastenkombination behandelt wird. FALSE, wenn der Schlüssel nicht behandelt wird oder *wenn pWndFrame* NULL ist.

### <a name="remarks"></a>Bemerkungen

Die Eingabeparameter müssen mit dem Eintrag in der Beschleunigertabelle übereinstimmen, sowohl für *nKey* als auch für *fVirt,* um zu bestimmen, ob eine Tastenkombination in *pWndFrame*behandelt wird.

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a>CKeyboardManager::IsKeyPrintable

Gibt an, ob ein Zeichen druckbar ist.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*Nchar*|[in] Das Zeichen, das diese Methode überprüft.|

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Zeichen druckbar ist, Null, wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt fehl, wenn ein Aufruf von [GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) fehlschlägt.

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a>CKeyboardManager::IsShowAllAccelerators

Gibt an, ob in Menüs alle Tastenkombinationen angezeigt werden, die Menübefehlen zugeordnet sind, oder nur die Standardtasten.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Anwendung alle Tastenkombinationen für Menübefehle auflistet; 0, wenn die Anwendung nur Standard-Tastenkombinationen anzeigt.

### <a name="remarks"></a>Bemerkungen

Die Anwendung listet die Tastenkombinationen für Menübefehle in der Menüleiste auf. Verwenden Sie die Funktion [CKeyboardManager::ShowAllAccelerators,](#showallaccelerators) um zu steuern, ob die Anwendung alle Tastenkombinationen oder nur die Standard-Tastenkombinationen auflistet.

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a>CKeyboardManager::LoadState

Lädt die Tastenkombinationstabellen aus der Windows-Registrierung.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Der Registrierungspfad, in dem `CKeyboardManager` Daten gespeichert werden.

*pDefaultFrame*<br/>
[in] Ein Zeiger auf ein Rahmenfenster, das als Standardfenster verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Status erfolgreich geladen wurde, oder 0 andernfalls.

### <a name="remarks"></a>Bemerkungen

Wenn der Parameter *lpszProfileName* NULL ist, überprüft `CKeyboardManager` diese Methode den Standardregistrierungsspeicherort für Daten. Der Standardregistrierungsspeicherort wird von der [CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)angegeben. Die Daten müssen zuvor mit der Methode [CKeyboardManager::SaveState](#savestate)geschrieben werden.

Wenn Sie kein Standardfenster angeben, wird das Hauptrahmenfenster Ihrer Anwendung verwendet.

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a>CKeyboardManager::ResetAlle

Lädt die Tastenkombinationstabellen aus der Anwendungsressource neu.

```
void ResetAll();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion löscht die in `CKeyboardManager` der Instanz gespeicherten Verknüpfungen. Anschließend wird der Status des Tastatur-Managers aus der Anwendungsressource neu geladen.

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a>CKeyboardManager::SaveState

Speichert die Tastenkombinationstabellen in der Windows-Registrierung.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Der Registrierungspfad zum `CKeyboardManager` Speichern des Status.

*pDefaultFrame*<br/>
[in] Ein Zeiger auf ein Rahmenfenster, das zum Standardfenster wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Tastatur-Managerstatus erfolgreich gespeichert wurde, oder 0 andernfalls.

### <a name="remarks"></a>Bemerkungen

Wenn der Parameter *lpszProfileName* NULL ist, `CKeyboardManager` schreibt diese Methode den Status in den Standardspeicherort, der von der [CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)angegeben wird. Wenn Sie einen Speicherort angeben, können Sie die Daten später mit der Methode [CKeyboardManager::LoadState](#loadstate)laden.

Wenn Sie kein Standardfenster angeben, wird das Hauptrahmenfenster als Standardfenster verwendet.

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a>CKeyboardManager::ShowAllAccelerators

Zeigt alle Tastenkombinationen an, die Menübefehlen zugeordnet sind.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parameter

*bShowAll*<br/>
[in] Wenn TRUE, werden alle Tastenkombinationen angezeigt. Wenn FALSE, wird nur die erste Tastenkombination angezeigt.

*lpszDelimiter*<br/>
[in] Eine Zeichenfolge, die zwischen Tastenkombinationen eingefügt werden soll. Dieses Trennzeichen hat keine Auswirkungen, wenn nur eine Tastenkombination angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Wenn einem Befehl mehr als eine Tastenkombination zugeordnet ist, wird standardmäßig nur die erste Tastenkombination angezeigt. Mit dieser Funktion können Sie alle Tastenkombinationen auflisten, die allen Befehlen zugeordnet sind.

Die Tastenkombinationen werden neben dem Befehl in der Menüleiste aufgelistet. Wenn alle Tastenkombinationen angezeigt werden, trennt die von *lpszDelimiter* bereitgestellte Zeichenfolge einzelne Tastenkombinationen.

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a>CKeyboardManager::TranslateCharToupper

Konvertiert ein Zeichen in sein oberes Register.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parameter

*Nchar*<br/>
[in] Das zu konvertierende Zeichen.

### <a name="return-value"></a>Rückgabewert

Das Zeichen, das das obere Register des Eingabeparameters ist.

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a>CKeyboardManager::UpdateAccelTable

Aktualisiert eine Tastenkombinationstabelle mit einer neuen Verknüpfungsschlüsseltabelle.

```
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    LPACCEL lpAccel,
    int nSize,
    CFrameWnd* pDefaultFrame = NULL);

BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    HACCEL hAccelNew,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parameter

*pTemplate*<br/>
[in] Ein Zeiger auf eine Dokumentvorlage.

*lpAccel*<br/>
[in] Ein Zeiger auf die neue Tastenkombination.

*nGröße*<br/>
[in] Die Größe der neuen Verknüpfungstabelle.

*pDefaultFrame*<br/>
[in] Ein Zeiger auf das Standardrahmenfenster.

*hAccelNeu*<br/>
[in] Ein Handle für die neue Verknüpfungstabelle.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um die vorhandene Verknüpfungstabelle durch neue Tastenkombinationen für mehrere Framefensterobjekte zu ersetzen. Die Funktion erhält eine Dokumentvorlage als Parameter, um Zugriff auf alle Framefensterobjekte zu erhalten, die mit der angegebenen Dokumentvorlage verbunden sind.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Tastatur- und Mausanpassung](../../mfc/keyboard-and-mouse-customization.md)
