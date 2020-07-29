---
title: 'TN016: Verwenden von C++-Mehrfachvererbung mit MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.inheritance
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
ms.openlocfilehash: c44639e713f6d0b26d5b74e9f645f60c8627e0c8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231766"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016: Verwenden von C++-Mehrfachvererbung mit MFC

In diesem Hinweis wird beschrieben, wie Sie mit der Microsoft Foundation Classes mehrere Vererbung (Mi) verwenden. Die Verwendung von Mi ist für MFC nicht erforderlich. Mi wird nicht in MFC-Klassen verwendet und ist nicht erforderlich, um eine Klassenbibliothek zu schreiben.

In den folgenden Unterthemen wird beschrieben, wie sich Mi auf die Verwendung allgemeiner MFC-Ausdrücke auswirkt und einige der Einschränkungen von Mi behandelt. Einige dieser Einschränkungen sind allgemeine C++-Einschränkungen. Andere werden von der MFC-Architektur festgelegt.

Am Ende dieses technischen Hinweises finden Sie eine komplette MFC-Anwendung, die Mi verwendet.

## <a name="cruntimeclass"></a>CRuntimeClass

Die persistenzerstellungs-Mechanismen für Persistenz und dynamische Objekte von MFC verwenden die [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) -Datenstruktur zur eindeutigen Identifizierung von Klassen MFC ordnet eine dieser Strukturen jeder dynamischen und/oder serialisierbaren Klasse in Ihrer Anwendung zu. Diese Strukturen werden initialisiert, wenn die Anwendung mithilfe eines speziellen statischen Objekts vom Typ gestartet wird `AFX_CLASSINIT` .

Die aktuelle Implementierung von `CRuntimeClass` unterstützt keine Informationen zum Mi-Lauf Zeittyp. Dies bedeutet nicht, dass Sie Mi nicht in ihrer MFC-Anwendung verwenden können. Bei der Arbeit mit Objekten mit mehr als einer Basisklasse werden Sie jedoch bestimmte Zuständigkeiten haben.

Die [CObject:: IsKindOf](../mfc/reference/cobject-class.md#iskindof) -Methode bestimmt den Typ eines Objekts nicht ordnungsgemäß, wenn Sie über mehrere Basisklassen verfügt. Daher können Sie [CObject](../mfc/reference/cobject-class.md) nicht als virtuelle Basisklasse verwenden, und alle Aufrufe an `CObject` Member-Funktionen, wie z. b. " [CObject:: Serialize](../mfc/reference/cobject-class.md#serialize) " und " [CObject:: Operator new](../mfc/reference/cobject-class.md#operator_new) ", müssen über Bereichs Qualifizierer verfügen, damit C++ den passenden Funktionsaufruf unterscheiden kann. Wenn ein Programm Mi innerhalb von MFC verwendet, muss die Klasse, die die `CObject` Basisklasse enthält, die linke Klasse in der Liste der Basisklassen sein.

Eine Alternative ist die Verwendung des- **`dynamic_cast`** Operators. Wenn Sie ein Objekt mit Mi in eine der Basisklassen umwandeln, wird der Compiler gezwungen, die Funktionen in der angegebenen Basisklasse zu verwenden. Weitere Informationen finden Sie unter [dynamic_cast-Operator](../cpp/dynamic-cast-operator.md).

## <a name="cobject---the-root-of-all-classes"></a>CObject-der Stamm aller Klassen

Alle wichtigen Klassen werden direkt oder indirekt von der Klasse abgeleitet `CObject` . `CObject`verfügt über keine Elementdaten, verfügt jedoch über einige Standardfunktionen. Wenn Sie Mi verwenden, erben Sie in der Regel von zwei oder mehr von `CObject` abgeleiteten Klassen. Im folgenden Beispiel wird veranschaulicht, wie eine Klasse von einem [CFrameWnd](../mfc/reference/cframewnd-class.md) und einem [CObList](../mfc/reference/coblist-class.md)erben kann:

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

In diesem Fall `CObject` ist zweimal enthalten. Dies bedeutet, dass Sie eine Möglichkeit benötigen, um einen Verweis auf `CObject` Methoden oder Operatoren eindeutig zu machen. Der **Operator new** und der [Operator Delete](../mfc/reference/cobject-class.md#operator_delete) sind zwei Operatoren, die eindeutig sein müssen. Ein weiteres Beispiel: der folgende Code verursacht einen Fehler zur Kompilierzeit:

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>Reimplementierung von CObject-Methoden

Wenn Sie eine neue Klasse erstellen, die über mindestens zwei `CObject` abgeleitete Basisklassen verfügt, sollten Sie die Methoden, die von anderen Benutzern verwendet werden sollen, neu implementieren `CObject` . Operatoren **`new`** und **`delete`** sind obligatorisch, und [Dump](../mfc/reference/cobject-class.md#dump) wird empfohlen. Im folgenden Beispiel werden die **`new`** **`delete`** Operatoren und und die- `Dump` Methode neu implementiert:

```cpp
class CListWnd : public CFrameWnd, public CObList
{
public:
    void* operator new(size_t nSize)
    {
        return CFrameWnd:: operator new(nSize);
    }
    void operator delete(void* p)
    {
        CFrameWnd:: operator delete(p);
    }
    void Dump(CDumpContent& dc)
    {
        CFrameWnd::Dump(dc);
        CObList::Dump(dc);
    }
    // ...
};
```

## <a name="virtual-inheritance-of-cobject"></a>Virtuelle Vererbung von CObject

Es könnte so erscheinen, als ob praktisch Vererbung `CObject` das Problem der Funktions Mehrdeutigkeit lösen würde, aber das ist nicht der Fall. Da keine Elementdaten in vorhanden sind `CObject` , benötigen Sie keine virtuelle Vererbung, um mehrere Kopien eines Basisklassenmember-Daten zu verhindern. Im ersten zuvor gezeigten Beispiel `Dump` ist die virtuelle Methode immer noch mehrdeutig, da Sie in und unterschiedlich implementiert `CFrameWnd` wird `CObList` . Die beste Möglichkeit, um Mehrdeutigkeit aufzuheben, besteht darin, die im vorherigen Abschnitt vorgestellten Empfehlungen einzuhalten.

## <a name="cobjectiskindof-and-run-time-typing"></a>CObject:: IsKindOf und Lauf Zeiteingabe

Der von MFC in unterstützte Lauf Zeiteingabe Mechanismus `CObject` verwendet die Makros DECLARE_DYNAMIC, IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE, IMPLEMENT_DYNCREATE, DECLARE_SERIAL und IMPLEMENT_SERIAL. Diese Makros können eine Lauf Zeittyp Überprüfung durchführen, um sichere downcasts zu gewährleisten.

Diese Makros unterstützen nur eine einzelne Basisklasse und funktionieren in einer begrenzten Weise für mehrfach geerbte Klassen. Die Basisklasse, die Sie in IMPLEMENT_DYNAMIC oder IMPLEMENT_SERIAL angeben, sollte die erste (oder linke) Basisklasse sein. Diese Platzierung ermöglicht es Ihnen, die Typüberprüfung nur für die linke Basisklasse durchzuführen. Das Lauf Zeittyp System weiß nichts über zusätzliche Basisklassen. Im folgenden Beispiel führen die Laufzeitsysteme eine Typüberprüfung für aus `CFrameWnd` , wissen aber nicht `CObList` .

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd und Meldungs Zuordnungen

Damit das MFC-Nachrichten Zuordnungs System ordnungsgemäß funktioniert, müssen zwei zusätzliche Anforderungen erfüllt werden:

- Es darf nur eine von `CWnd` abgeleitete Basisklasse vorhanden sein.

- Die von `CWnd` abgeleitete Basisklasse muss die erste (oder linke) Basisklasse sein.

Im folgenden finden Sie einige Beispiele, die nicht funktionieren:

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>Ein Beispielprogramm mit Mi

Das folgende Beispiel ist eine eigenständige Anwendung, die aus einer Klasse besteht, die von `CFrameWnd` und [CWinApp](../mfc/reference/cwinapp-class.md)abgeleitet ist. Es wird nicht empfohlen, dass Sie eine Anwendung auf diese Weise strukturieren, aber dies ist ein Beispiel für die kleinste MFC-Anwendung, die über eine Klasse verfügt.

```cpp
#include <afxwin.h>

class CHelloAppAndFrame : public CFrameWnd, public CWinApp
{
public:
    CHelloAppAndFrame() {}

    // Necessary because of MI disambiguity
    void* operator new(size_t nSize)
        { return CFrameWnd::operator new(nSize); }
    void operator delete(void* p)
        { CFrameWnd::operator delete(p); }

    // Implementation
    // CWinApp overrides
    virtual BOOL InitInstance();
    // CFrameWnd overrides
    virtual void PostNcDestroy();
    afx_msg void OnPaint();

    DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)
    ON_WM_PAINT()
END_MESSAGE_MAP()

// because the frame window is not allocated on the heap, we must
// override PostNCDestroy not to delete the frame object
void CHelloAppAndFrame::PostNcDestroy()
{
    // do nothing (do not call base class)
}

void CHelloAppAndFrame::OnPaint()
{
    CPaintDC dc(this);
    CRect rect;
    GetClientRect(rect);

    CString s = "Hello, Windows!";
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));
    dc.SetBkMode(TRANSPARENT);
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);
}

// Application initialization
BOOL CHelloAppAndFrame::InitInstance()
{
    // first create the main frame
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",
        WS_OVERLAPPEDWINDOW, rectDefault))
        return FALSE;

    // the application object is also a frame window
    m_pMainWnd = this;
    ShowWindow(m_nCmdShow);
    return TRUE;
}

CHelloAppAndFrame theHelloAppAndFrame;
```

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise nach Zahl](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise nach Kategorie](../mfc/technical-notes-by-category.md)
