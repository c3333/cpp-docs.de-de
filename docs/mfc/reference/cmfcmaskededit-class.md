---
title: CMFCMaskedEdit-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
ms.openlocfilehash: 26617f10605fe2a8a94adcc477cccab7e2ba4919
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754220"
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit-Klasse

Die `CMFCMaskedEdit` Klasse unterstützt ein maskiertes Bearbeitungssteuerelement, das Benutzereingaben anhand einer Maske überprüft und die validierten Ergebnisse gemäß einer Vorlage anzeigt.

## <a name="syntax"></a>Syntax

```
class CMFCMaskedEdit : public CEdit
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCMaskedEdit::CMFCMaskedEdit`|Der Standardkonstruktor.|
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCMaskedBearbeiten::DIsableMask](#disablemask)|Deaktiviert die Überprüfung von Benutzereingaben.|
|[CMFCMaskedBearbeiten::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Gibt an, `GetWindowText` ob die Methode nur maskierte Zeichen abruft.|
|[CMFCMaskedBearbeiten::EnableMask](#enablemask)|Initialisiert das maskierte Bearbeitungssteuerelement.|
|[CMFCMaskedBearbeiten::EnableSelectByGroup](#enableselectbygroup)|Gibt an, ob das maskierte Bearbeitungssteuerelement bestimmte Gruppen von Benutzereingaben oder alle Benutzereingaben auswählt.|
|[CMFCMaskedBearbeiten::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Gibt an, ob der Text nur anhand maskierter Zeichen oder für die gesamte Maske überprüft wird.|
|`CMFCMaskedEdit::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Ruft validierten Text aus dem maskierten Bearbeitungssteuerelement ab.|
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Gibt eine Zeichenfolge mit gültigen Zeichen an, die der Benutzer eingeben kann.|
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Zeigt eine Eingabeaufforderung im maskierten Bearbeitungssteuerelement an.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCMaskedBearbeiten::IsMaskedChar](#ismaskedchar)|Wird vom Framework aufgerufen, um das angegebene Zeichen anhand des entsprechenden Maskenzeichens zu überprüfen.|

## <a name="remarks"></a>Bemerkungen

Führen Sie die folgenden `CMFCMaskedEdit` Schritte aus, um das Steuerelement in Ihrer Anwendung zu verwenden:

1. Betten Sie `CMFCMaskedEdit` ein Objekt in Ihre Fensterklasse ein.

2. Rufen Sie die [CMFCMaskedEdit::EnableMask-Methode](#enablemask) auf, um die Maske anzugeben.

3. Rufen Sie die [CMFCMaskedEdit::SetValidChars-Methode](#setvalidchars) auf, um die Liste der gültigen Zeichen anzugeben.

4. Rufen Sie die [CMFCMaskedEdit::SetWindowText-Methode](#setwindowtext) auf, um den Standardtext für das maskierte Bearbeitungssteuerelement anzugeben.

5. Rufen Sie die [CMFCMaskedEdit::GetWindowText-Methode](#getwindowtext) auf, um den validierten Text abzurufen.

Wenn Sie nicht eine oder mehrere Methoden aufrufen, um die Maske, gültige Zeichen und Standardtext zu initialisieren, verhält sich das maskierte Bearbeitungssteuerelement genauso wie das Standardbearbeitungssteuerelement.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie eine Maske (z. B. eine Telefonnummer) einrichten, indem Sie die `EnableMask` Methode zum Erstellen der Maske für das maskierte Bearbeitungssteuerelement, die `SetValidChars` Methode zum Angeben einer Zeichenfolge mit gültigen Zeichen, die der Benutzer eingeben kann, und `SetWindowText` die Methode zum Anzeigen einer Eingabeaufforderung im maskierten Bearbeitungssteuerelement verwenden. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxmaskededit.h

## <a name="cmfcmaskededitdisablemask"></a><a name="disablemask"></a>CMFCMaskedBearbeiten::DIsableMask

Deaktiviert die Überprüfung von Benutzereingaben.

```cpp
void DisableMask();
```

### <a name="remarks"></a>Bemerkungen

Wenn die Benutzereingabeüberprüfung deaktiviert ist, verhält sich das maskierte Bearbeitungssteuerelement wie das Standard-Bearbeitungssteuerelement.

## <a name="cmfcmaskededitenablegetmaskedcharsonly"></a><a name="enablegetmaskedcharsonly"></a>CMFCMaskedBearbeiten::EnableGetMaskedCharsOnly

Gibt an, `GetWindowText` ob die Methode nur maskierte Zeichen abruft.

```cpp
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um anzugeben, dass die [CMFCMaskedEdit::GetWindowText-Methode](#getwindowtext) nur maskierte Zeichen abruft. FALSE, um anzugeben, dass die Methode den gesamten Text abruft. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um das Abrufen maskierter Zeichen zu aktivieren. Erstellen Sie dann ein maskiertes Bearbeitungssteuerelement, das der Telefonnummer entspricht, z. B. (425) 555-0187. Wenn Sie `GetWindowText` die Methode aufrufen, wird "4255550187" zurückgegeben. Wenn Sie das Abrufen maskierter `GetWindowText` Zeichen deaktivieren, gibt die Methode den Text zurück, der im Bearbeitungssteuerelement angezeigt wird, z. B. "(425) 555-0187".

## <a name="cmfcmaskededitenablemask"></a><a name="enablemask"></a>CMFCMaskedBearbeiten::EnableMask

Initialisiert das maskierte Bearbeitungssteuerelement.

```cpp
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parameter

*lpszMaske*<br/>
[in] Eine Maskenzeichenfolge, die den Zeichentyp angibt, der an jeder Position in der Benutzereingabe angezeigt werden kann. Die Länge der *Parameterzeichenfolgen lpszInputTemplate* und *lpszMask* muss identisch sein. Weitere Informationen zu Maskenzeichen finden Sie im Abschnitt "Bemerkungen".

*lpszInputTemplate*<br/>
[in] Eine Maskenvorlagenzeichenfolge, die die Literalzeichen angibt, die an jeder Position in der Benutzereingabe angezeigt werden können. Verwenden Sie das Unterstrichzeichen ('_') als Platzhalter des Zeichens. Die Länge der *Parameterzeichenfolgen lpszInputTemplate* und *lpszMask* muss identisch sein.

*chMaskInputTemplate*<br/>
[in] Ein Standardzeichen, das das Framework für jedes ungültige Zeichen in der Benutzereingabe ersetzt. Der Standardwert dieses Parameters ist Unterstrich ('_').

*lpszValid*<br/>
[in] Eine Zeichenfolge, die einen Satz gültiger Zeichen enthält. NULL gibt an, dass alle Zeichen gültig sind. Der Standardwert dieses Parameters ist NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Maske für das maskierte Bearbeitungssteuerelement zu erstellen. Leiten Sie eine `CMFCMaskedEdit` Klasse von der Klasse ab, und überschreiben Sie die [CMFCMaskedEdit::IsMaskedChar-Methode,](#ismaskedchar) um Ihren eigenen Code für die benutzerdefinierte Maskenverarbeitung zu verwenden.

In der folgenden Tabelle sind die Standardmaskenzeichen aufgeführt:

|Maskenzeichen|Definition|
|--------------------|----------------|
|D|Ziffer.|
|d|Ziffer oder Raum.|
|+|Plus ('+'), Minus ('-') oder Leerzeichen.|
|C|Alphabetischer Charakter.|
|c|Alphabetischer Charakter oder Leerzeichen.|
|Ein|Alphanumerisches Zeichen.|
|a|Alphanumerisches Zeichen oder Leerzeichen.|
|*|Ein druckbares Zeichen.|

## <a name="cmfcmaskededitenableselectbygroup"></a><a name="enableselectbygroup"></a>CMFCMaskedBearbeiten::EnableSelectByGroup

Gibt an, ob das maskierte Bearbeitungssteuerelement es dem Benutzer ermöglicht, bestimmte Gruppeneingaben oder alle Eingaben auszuwählen.

```cpp
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um nur Gruppen auszuwählen; FALSE, um den gesamten Text auszuwählen. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um anzugeben, ob das maskierte Bearbeitungssteuerelement es einem Benutzer ermöglicht, nach Gruppe oder dem gesamten Text auszuwählen.

Standardmäßig ist die Auswahl nach Gruppe aktiviert. In diesem Fall kann der Benutzer nur fortlaufende Gruppen gültiger Zeichen auswählen.

Sie können z. B. das folgende maskierte Bearbeitungssteuerelement verwenden, um eine Telefonnummer zu überprüfen:

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

Wenn die Auswahl nach Gruppe aktiviert ist, kann der Benutzer nur die Zeichenfolgengruppen "425", "555" oder "0187" abrufen. Wenn die Gruppenauswahl deaktiviert ist, kann der Benutzer den gesamten Text der Telefonnummer abrufen: "(425) 555-0187".

## <a name="cmfcmaskededitenablesetmaskedcharsonly"></a><a name="enablesetmaskedcharsonly"></a>CMFCMaskedBearbeiten::EnableSetMaskedCharsOnly

Gibt an, ob der Text nur anhand der maskierten Zeichen oder der gesamten Maske überprüft wird.

```cpp
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um die Benutzereingabe nur anhand maskierter Zeichen zu überprüfen; FALSE, um die gesamte Maske zu validieren. Der Standardwert ist TRUE.

## <a name="cmfcmaskededitgetwindowtext"></a><a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText

Ruft validierten Text aus dem maskierten Bearbeitungssteuerelement ab.

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>Parameter

*lpszStringBuf*<br/>
[out] Ein Zeiger auf einen Puffer, der den Text vom Bearbeitungssteuerelement empfängt.

*nMaxCount*<br/>
[in] Die maximale Anzahl der zu empfangenden Zeichen.

*rstrString*<br/>
[out] Ein Verweis auf das Zeichenfolgenobjekt, das den Text vom Bearbeitungssteuerelement empfängt.

### <a name="return-value"></a>Rückgabewert

Die erste Methodenüberladung gibt die Anzahl der Bytes der Zeichenfolge zurück, die in den Parameterpuffer *lpszStringBuf* kopiert wird. 0, wenn das maskierte Bearbeitungssteuerelement keinen Text enthält.

### <a name="remarks"></a>Bemerkungen

Diese Methode kopiert den Text aus dem maskierten Bearbeitungssteuerelement in den *puffer lpszStringBuf* oder die *rstrString-Zeichenfolge.*

Diese Methode definiert [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext)neu.

## <a name="cmfcmaskededitismaskedchar"></a><a name="ismaskedchar"></a>CMFCMaskedBearbeiten::IsMaskedChar

Wird vom Framework aufgerufen, um das angegebene Zeichen anhand des entsprechenden Maskenzeichens zu überprüfen.

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>Parameter

*chChar*<br/>
[in] Das zu validierende Zeichen.

*chMaskChar*<br/>
[in] Das entsprechende Zeichen aus der Maskenzeichenfolge.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der *chChar-Parameter* der Typ des Zeichens ist, der durch den *chMaskChar-Parameter* zulässig ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um Eingabezeichen selbst zu überprüfen. Weitere Informationen zu Maskenzeichen finden Sie in der [CMFCMaskedEdit::EnableMask-Methode.](#enablemask)

## <a name="cmfcmaskededitsetvalidchars"></a><a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars

Gibt eine Zeichenfolge mit gültigen Zeichen an, die der Benutzer eingeben kann.

```cpp
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parameter

*lpszValid*<br/>
[in] Eine Zeichenfolge, die den Satz gültiger Eingabezeichen enthält. NULL bedeutet, dass alle Zeichen gültig sind. Der Standardwert dieses Parameters ist NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um eine Liste gültiger Zeichen zu definieren. Wenn ein Eingabezeichen nicht in dieser Liste enthalten ist, wird es von maskiertem Bearbeitungssteuerelement nicht akzeptiert.

Im folgenden Codebeispiel werden nur hexadezimale Zahlen akzeptiert.

```cpp
//Mask: 0xFFFF
m_wndMaskEdit.EnableMask(
    _T(" AAAA"),                // The mask string.
    _T("0x____"),               // The literal template string.
    _T('_'));                   // The default character that
                                // replaces the backspace character.
// Valid string characters
m_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));
```

## <a name="cmfcmaskededitsetwindowtext"></a><a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText

Zeigt eine Eingabeaufforderung im maskierten Bearbeitungssteuerelement an.

```cpp
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parameter

*lpszString*<br/>
[in] Verweist auf eine null-terminierte Zeichenfolge, die als Eingabeaufforderung verwendet wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode legt den Steuertext fest.

Diese Methode definiert [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)neu.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)
