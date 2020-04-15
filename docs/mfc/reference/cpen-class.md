---
title: CPen-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
ms.openlocfilehash: e15dc53fafa0d80f1b52b3fe77f3635c592a4346
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364072"
---
# <a name="cpen-class"></a>CPen-Klasse

Kapselt einen Stift der Windows GDI (Graphics Device Interface).

## <a name="syntax"></a>Syntax

```
class CPen : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPen::CPen](#cpen)|Erstellt ein `CPen`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPen::CreatePen](#createpen)|Erstellt einen logischen kosmetischen oder geometrischen Stift mit den angegebenen Stil-, Breiten- und Pinselattributen und fügt ihn an das `CPen` Objekt an.|
|[CPen::CreatePenIndirect](#createpenindirect)|Erstellt einen Stift mit dem Stil, der Breite und der Farbe, `CPen` die in einer [LOGPEN-Struktur](/windows/win32/api/wingdi/ns-wingdi-logpen) angegeben sind, und fügt ihn an das Objekt an.|
|[CPen::FromHandle](#fromhandle)|Gibt einen Zeiger `CPen` auf ein Objekt zurück, wenn ein Windows HPEN angegeben wird.|
|[CPen::GetExtLogPen](#getextlogpen)|Ruft eine [EXTLOGPEN-Basisstruktur](/windows/win32/api/wingdi/ns-wingdi-extlogpen) ab.|
|[CPen::GetLogPen](#getlogpen)|Ruft eine zugrunde liegende [LOGPEN-Struktur ab.](/windows/win32/api/wingdi/ns-wingdi-logpen)|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPen::operator HPEN](#operator_hpen)|Gibt das Windows-Handle `CPen` zurück, das an das Objekt angefügt ist.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zur `CPen`Verwendung finden Sie unter [Grafikobjekte](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cpencpen"></a><a name="cpen"></a>CPen::CPen

Erstellt ein `CPen`-Objekt.

```
CPen();

CPen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

CPen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>Parameter

*nPenStyle*<br/>
Gibt den Stiftstil an. Dieser Parameter in der ersten Version des Konstruktors kann einer der folgenden Werte sein:

- PS_SOLID Erstellt einen festen Stift.

- PS_DASH Erstellt einen gestrichelten Stift. Gültig nur bei einer Stiftbreite von 1 oder weniger in Geräteeinheiten.

- PS_DOT Erstellt einen gepunkteten Stift. Gültig nur bei einer Stiftbreite von 1 oder weniger in Geräteeinheiten.

- PS_DASHDOT Erstellt einen Stift mit abwechselnden Strichen und Punkten. Gültig nur bei einer Stiftbreite von 1 oder weniger in Geräteeinheiten.

- PS_DASHDOTDOT Erstellt einen Stift mit abwechselnden Strichen und doppelten Punkten. Gültig nur bei einer Stiftbreite von 1 oder weniger in Geräteeinheiten.

- PS_NULL Erstellt einen Nullstift.

- PS_INSIDEFRAME Erstellt einen Stift, der eine Linie innerhalb des Rahmens geschlossener Formen zeichnet, die von `Ellipse` `Rectangle`den `RoundRect` `Pie`Windows GDI-Ausgabefunktionen erzeugt werden, die ein umgebendes Rechteck angeben (z. B. die Funktionen , , , und `Chord` Member). Wenn dieser Stil mit Windows GDI-Ausgabefunktionen verwendet wird, die kein `LineTo` umgebendes Rechteck angeben (z. B. die Memberfunktion), wird der Zeichenbereich des Stifts nicht durch einen Rahmen begrenzt.

Die zweite Version `CPen` des Konstruktors gibt eine Kombination aus Typ-, Stil-, Endkappes- und Joinattributen an. Die Werte aus jeder Kategorie sollten mithilfe des bitweisen ODER-Operators (&#124;) kombiniert werden. Der Stifttyp kann einer der folgenden Werte sein:

- PS_GEOMETRIC Erstellt einen geometrischen Stift.

- PS_COSMETIC Erstellt einen Kosmetikstift.

   Die zweite Version `CPen` des Konstruktors fügt die folgenden Stiftstile für *nPenStyle*hinzu:

- PS_ALTERNATE Erstellt einen Stift, der jedes andere Pixel festlegt. (Dieser Stil gilt nur für kosmetische Stifte.)

- PS_USERSTYLE Erstellt einen Stift, der ein vom Benutzer bereitgestelltes Styling-Array verwendet.

   Die Endkappe kann einer der folgenden Werte sein:

- PS_ENDCAP_ROUND Endkappen sind rund.

- PS_ENDCAP_SQUARE Endkappen sind quadratisch.

- PS_ENDCAP_FLAT Endkappen sind flach.

   Die Verknüpfung kann einer der folgenden Werte sein:

- PS_JOIN_BEVEL Verknüpfungen werden abgeschrägt.

- PS_JOIN_MITER Verknüpfungen werden gemildert, wenn sie innerhalb des aktuellen Grenzwerts liegen, der von der [SetMiterLimit-Funktion](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) festgelegt wurde. Wenn die Verknüpfung diesen Grenzwert überschreitet, wird sie abgeschrägt.

- PS_JOIN_ROUND Joins sind rund.

*nWidth*<br/>
Gibt die Breite des Stifts an.

- Bei der ersten Version des Konstruktors beträgt die Breite in Geräteeinheiten unabhängig vom Zuordnungsmodus immer 1 Pixel, wenn dieser Wert 0 ist.

- Für die zweite Version des Konstruktors wird die Breite in logischen Einheiten angegeben, wenn *nPenStyle* PS_GEOMETRIC ist. Wenn *nPenStyle* PS_COSMETIC ist, muss die Breite auf 1 gesetzt werden.

*crColor*<br/>
Enthält eine RGB-Farbe für den Stift.

*pLogBrush*<br/>
Zeigt auf `LOGBRUSH` eine Struktur. Wenn *nPenStyle* PS_COSMETIC ist, gibt `LOGBRUSH` das *lbColor-Member* der Struktur die Farbe `LOGBRUSH` des Stifts an, und das *lbStyle-Member* der Struktur muss auf BS_SOLID festgelegt werden. Wenn *nPenStyle* PS_GEOMETRIC ist, müssen alle Member verwendet werden, um die Pinselattribute des Stifts anzugeben.

*nStyleCount*<br/>
Gibt die Länge des *lpStyle-Arrays* in Doppelworteinheiten an. Dieser Wert muss Null sein, wenn *nPenStyle* nicht PS_USERSTYLE ist.

*lpStyle*<br/>
Zeigt auf ein Array von Doubleword-Werten. Der erste Wert gibt die Länge des ersten Bindestrichs in einem benutzerdefinierten Stil an, der zweite Wert gibt die Länge des ersten Raums usw. an. Dieser Zeiger muss NULL sein, wenn *nPenStyle* nicht PS_USERSTYLE ist.

### <a name="remarks"></a>Bemerkungen

Wenn Sie den Konstruktor ohne Argumente verwenden, `CPen` müssen Sie `CreatePen` `CreatePenIndirect`das `CreateStockObject` resultierende Objekt mit den Funktionen , oder Member initialisieren.

Wenn Sie den Konstruktor verwenden, der Argumente verwendet, ist keine weitere Initialisierung erforderlich. Der Konstruktor mit Argumenten kann eine Ausnahme auslösen, wenn Fehler auftreten, während der Konstruktor ohne Argumente immer erfolgreich ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

## <a name="cpencreatepen"></a><a name="createpen"></a>CPen::CreatePen

Erstellt einen logischen kosmetischen oder geometrischen Stift mit den angegebenen Stil-, Breiten- und Pinselattributen und fügt ihn an das `CPen` Objekt an.

```
BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>Parameter

*nPenStyle*<br/>
Gibt den Stil für den Stift an. Eine Liste möglicher Werte finden Sie im *Parameter nPenStyle* im [CPen-Konstruktor.](#cpen)

*nWidth*<br/>
Gibt die Breite des Stifts an.

- Bei der ersten `CreatePen`Version von , wenn dieser Wert 0 ist, beträgt die Breite in Geräteeinheiten immer 1 Pixel, unabhängig vom Zuordnungsmodus.

- Für die zweite `CreatePen`Version von , wenn *nPenStyle* PS_GEOMETRIC ist, wird die Breite in logischen Einheiten angegeben. Wenn *nPenStyle* PS_COSMETIC ist, muss die Breite auf 1 gesetzt werden.

*crColor*<br/>
Enthält eine RGB-Farbe für den Stift.

*pLogBrush*<br/>
Zeigt auf eine [LOGBRUSH-Struktur.](/windows/win32/api/wingdi/ns-wingdi-logbrush) Wenn *nPenStyle* PS_COSMETIC `lbColor` ist, `LOGBRUSH` gibt das Element der Struktur die Farbe des `LOGBRUSH` Stifts an, und das *lbStyle-Member* der Struktur muss auf BS_SOLID festgelegt werden. Wenn nPenStyle PS_GEOMETRIC ist, müssen alle Member verwendet werden, um die Pinselattribute des Stifts anzugeben.

*nStyleCount*<br/>
Gibt die Länge des *lpStyle-Arrays* in Doppelworteinheiten an. Dieser Wert muss Null sein, wenn *nPenStyle* nicht PS_USERSTYLE ist.

*lpStyle*<br/>
Zeigt auf ein Array von Doubleword-Werten. Der erste Wert gibt die Länge des ersten Bindestrichs in einem benutzerdefinierten Stil an, der zweite Wert gibt die Länge des ersten Raums usw. an. Dieser Zeiger muss NULL sein, wenn *nPenStyle* nicht PS_USERSTYLE ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn erfolgreich, oder Null, wenn die Methode fehlschlägt.

### <a name="remarks"></a>Bemerkungen

Die erste `CreatePen` Version von initialisiert einen Stift mit dem angegebenen Stil, der angegebenen Breite und Farbe. Der Stift kann anschließend als aktueller Stift für jeden Gerätekontext ausgewählt werden.

Stifte mit einer Breite von mehr als 1 Pixel sollten immer entweder den PS_NULL-, PS_SOLID- oder PS_INSIDEFRAME-Stil aufweisen.

Wenn ein Stift den PS_INSIDEFRAME Stil und eine Farbe hat, die nicht mit einer Farbe in der logischen Farbtabelle übereinstimmt, wird der Stift mit einer gezauderten Farbe gezeichnet. Der PS_SOLID Stiftstil kann nicht verwendet werden, um einen Stift mit einer gezauderten Farbe zu erstellen. Der Stil PS_INSIDEFRAME ist identisch mit PS_SOLID wenn die Stiftbreite kleiner oder gleich 1 ist.

Die zweite `CreatePen` Version von initialisiert einen logischen kosmetischen oder geometrischen Stift mit den angegebenen Stil-, Breiten- und Pinselattributen. Die Breite eines kosmetischen Stifts ist immer 1; Die Breite eines geometrischen Stifts wird immer in Welteinheiten angegeben. Nachdem eine Anwendung einen logischen Stift erstellt hat, kann sie diesen Stift in einen Gerätekontext auswählen, indem sie die [CDC::SelectObject-Funktion](../../mfc/reference/cdc-class.md#selectobject) aufruft. Nachdem ein Stift in einem Gerätekontext ausgewählt wurde, kann er zum Zeichnen von Linien und Kurven verwendet werden.

- Wenn *nPenStyle* PS_COSMETIC und PS_USERSTYLE ist, geben die Einträge im *lpStyle-Array* Längen von Bindestrichen und Leerzeichen in Stileinheiten an. Eine Stileinheit wird durch das Gerät definiert, in dem der Stift zum Zeichnen einer Linie verwendet wird.

- Wenn *nPenStyle* PS_GEOMETRIC und PS_USERSTYLE ist, geben die Einträge im *lpStyle-Array* Längen von Bindestrichen und Leerzeichen in logischen Einheiten an.

- Wenn *nPenStyle* PS_ALTERNATE ist, wird die Stileinheit ignoriert und jedes andere Pixel gesetzt.

Wenn eine Anwendung keinen bestimmten Stift mehr benötigt, sollte sie die [Memberfunktion CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) aufrufen oder das `CPen` Objekt zerstören, damit die Ressource nicht mehr verwendet wird. Eine Anwendung sollte keinen Stift löschen, wenn der Stift in einem Gerätekontext ausgewählt ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

## <a name="cpencreatepenindirect"></a><a name="createpenindirect"></a>CPen::CreatePenIndirect

Initialisiert einen Stift mit dem Stil, der Breite und der Farbe, die in der Struktur angegeben sind, auf die *lpLogPen*zeigt.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Parameter

*lpLogPen*<br/>
Verweist auf die Windows [LOGPEN-Struktur,](/windows/win32/api/Wingdi/ns-wingdi-logpen) die Informationen über den Stift enthält.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Stifte mit einer Breite von mehr als 1 Pixel sollten immer entweder den PS_NULL-, PS_SOLID- oder PS_INSIDEFRAME-Stil aufweisen.

Wenn ein Stift den PS_INSIDEFRAME Stil und eine Farbe hat, die nicht mit einer Farbe in der logischen Farbtabelle übereinstimmt, wird der Stift mit einer gezauderten Farbe gezeichnet. Der PS_INSIDEFRAME-Stil ist identisch mit PS_SOLID, wenn die Stiftbreite kleiner oder gleich 1 ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

## <a name="cpenfromhandle"></a><a name="fromhandle"></a>CPen::FromHandle

Gibt einen Zeiger `CPen` auf ein Objekt zurück, das einem Windows GDI-Stiftobjekt ein Handle gegeben hat.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Parameter

*hPen*<br/>
`HPEN`Handle auf Windows GDI-Stift.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CPen` ein Objekt, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn ein `CPen`-Objekt nicht an das Handle angefügt ist, wird ein temporäres `CPen`-Objekt erstellt und angefügt. Dieses `CPen` temporäre Objekt ist nur gültig, bis die Anwendung das nächste Mal Leerlaufzeit in ihrer Ereignisschleife hat, zu diesem Zeitpunkt alle temporären Grafikobjekte gelöscht werden. Mit anderen Worten, das temporäre Objekt ist nur während der Verarbeitung einer Fensternachricht gültig.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

## <a name="cpengetextlogpen"></a><a name="getextlogpen"></a>CPen::GetExtLogPen

Ruft `EXTLOGPEN` eine zugrunde liegende Struktur ab.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Parameter

*pLogPen*<br/>
Verweist auf eine [EXTLOGPEN-Struktur,](/windows/win32/api/wingdi/ns-wingdi-extlogpen) die Informationen über den Stift enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die `EXTLOGPEN` Struktur definiert die Stil-, Breiten- und Pinselattribute eines Stifts. Rufen Sie `GetExtLogPen` z. B. an, um dem jeweiligen Stil eines Stifts zu entsprechen.

Informationen zu Stiftattributen finden Sie in den folgenden Themen im Windows SDK:

- [Getobject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel `GetExtLogPen` wird das Aufrufen zum Abrufen der Attribute eines Stifts veranschaulicht, und dann ein neuer, kosmetischer Stift mit derselben Farbe erstellt.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

## <a name="cpengetlogpen"></a><a name="getlogpen"></a>CPen::GetLogPen

Ruft `LOGPEN` eine zugrunde liegende Struktur ab.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Parameter

*pLogPen*<br/>
Verweist auf eine [LOGPEN-Struktur,](/windows/win32/api/wingdi/ns-wingdi-logpen) die Informationen über den Stift enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die `LOGPEN` Struktur definiert den Stil, die Farbe und das Muster eines Stifts.

Rufen Sie `GetLogPen` z. B. an, um dem jeweiligen Stiftstil zu entsprechen.

Informationen zu Stiftattributen finden Sie in den folgenden Themen im Windows SDK:

- [Getobject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel `GetLogPen` wird das Aufrufen zum Abrufen eines Stiftzeichens veranschaulicht, und dann ein neuer, durchgezogener Stift mit derselben Farbe erstellt.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

## <a name="cpenoperator-hpen"></a><a name="operator_hpen"></a>CPen::operator HPEN

Ruft das angefügte Windows `CPen` GDI-Handle des Objekts ab.

```
operator HPEN() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Handle für das Windows `CPen` GDI-Objekt, das durch das Objekt dargestellt wird; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Dieser Operator ist ein Gießoperator, der die direkte Verwendung eines HPEN Objekts unterstützt.

Weitere Informationen zur Verwendung von Grafikobjekten finden Sie im Artikel [Grafikobjekte](/windows/win32/gdi/graphic-objects) in Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Siehe auch

[CGdiObject-Klasse](../../mfc/reference/cgdiobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CBrush-Klasse](../../mfc/reference/cbrush-class.md)
