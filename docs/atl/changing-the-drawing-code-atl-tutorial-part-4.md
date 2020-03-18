---
title: Ändern des Zeichencodes (ATL-Lernprogramm, Teil 4)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: 4244dae532f467f28a5ca53e15ee601344999233
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509375"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Ändern des Zeichencodes (ATL-Lernprogramm, Teil 4)

Standardmäßig zeigt der Zeichnungs Code des Steuer Elements ein quadratisches und den Text **PolyCtl**an. In diesem Schritt ändern Sie den Code, um etwas interessanteres anzuzeigen. Die folgenden Aufgaben sind beteiligt:

- Ändern der Header Datei

- Ändern der `OnDraw`-Funktion

- Hinzufügen einer Methode zum Berechnen der Polygon Punkte

- Initialisieren der Füllfarbe

## <a name="modifying-the-header-file"></a>Ändern der Header Datei

Beginnen Sie mit dem Hinzufügen von Unterstützung für die mathematischen Funktionen `sin` und `cos`, die verwendet werden, um die Polygon Punkte zu berechnen, und durch Erstellen eines Arrays zum Speichern von Positionen.

### <a name="to-modify-the-header-file"></a>So ändern Sie die Header Datei

1. Fügen Sie die Zeile `#include <math.h>` oben in PolyCtl. h hinzu. Der Anfang der Datei sollte wie folgt aussehen:

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. Implementieren Sie die `IProvideClassInfo`-Schnittstelle zum Bereitstellen von Methoden Informationen für das-Steuerelement, indem Sie den folgenden Code zu PolyCtl. h hinzufügen. Ersetzen Sie in der `CPolyCtl`-Klasse die folgende Zeile:

    ```cpp
    public CComControl<CPolyCtl>
    ```

    durch

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    Fügen Sie in `BEGIN_COM_MAP(CPolyCtl)`die folgenden Zeilen hinzu:

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. Nachdem die Polygon Punkte berechnet wurden, werden Sie in einem Array vom Typ `POINT`gespeichert. Fügen Sie daher das Array nach der Definitions Anweisung `short m_nSides;` in PolyCtl. h hinzu:

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>Ändern der OnDraw-Methode

Nun sollten Sie die `OnDraw`-Methode in PolyCtl. h ändern. Der Code, den Sie hinzufügen, erstellt einen neuen Stift und Pinsel, mit dem das Polygon gezeichnet werden soll, und ruft dann die `Ellipse`-und `Polygon` Win32-API-Funktionen auf, um die eigentliche Zeichnung auszuführen.

### <a name="to-modify-the-ondraw-function"></a>So ändern Sie die OnDraw-Funktion

1. Ersetzen Sie die vorhandene `OnDraw`-Methode in PolyCtl. h durch den folgenden Code:

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Hinzufügen einer Methode zum Berechnen der Polygon Punkte

Fügen Sie eine Methode namens "`CalcPoints`" hinzu, mit der die Koordinaten der Punkte berechnet werden, die den Umkreis des Polygons bilden. Diese Berechnungen basieren auf der Rect-Variablen, die an die Funktion weitergeleitet wird.

### <a name="to-add-the-calcpoints-method"></a>So fügen Sie die CalcPoints-Methode hinzu

1. Fügen Sie die Deklaration von `CalcPoints` dem `IPolyCtl` Public-Abschnitt der `CPolyCtl`-Klasse in PolyCtl. h hinzu:

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    Der letzte Teil des öffentlichen Abschnitts der `CPolyCtl`-Klasse sieht wie folgt aus:

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. Fügen Sie diese Implementierung der `CalcPoints` Funktion am Ende von PolyCtl. cpp hinzu:

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>Initialisieren der Füllfarbe

Initialisieren Sie `m_clrFillColor` mit einer Standardfarbe.

### <a name="to-initialize-the-fill-color"></a>So initialisieren Sie die Füllfarbe

1. Verwenden Sie grün als Standardfarbe, indem Sie diese Zeile zum `CPolyCtl`-Konstruktor in PolyCtl. h hinzufügen:

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

Der Konstruktor sieht nun wie folgt aus:

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>Erstellen und Testen des Steuerelements

Erstellen Sie das Steuerelement neu. Stellen Sie sicher, dass die Datei "PolyCtl. htm" geschlossen ist, wenn Sie noch geöffnet ist, und klicken Sie dann im Menü " **Build** " auf **Polygon erstellen** . Sie können das Steuerelement erneut auf der Seite PolyCtl. htm anzeigen, aber diesmal den Test Container des ActiveX-Steuer Elements verwenden.

### <a name="to-use-the-activex-control-test-container"></a>So verwenden Sie den Test Container des ActiveX-Steuer Elements

1. Erstellen und starten Sie den Test Container des ActiveX-Steuer Elements. Das [TSTCON-Beispiel für den Test Container für ActiveX-Steuer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon) Elemente finden Sie auf GitHub.

    > [!NOTE]
    > Ersetzen Sie bei Fehlern im Zusammenhang mit `ATL::CW2AEX`in Skript. cpp den Zeilen `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` durch `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`und Line `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` durch `TRACE( "Source Text: %s\n", bstrSourceLineText );`.<br/>
    > Öffnen Sie "stdafx. h" im `TCProps` Projekt, und ersetzen Sie Folgendes, um `HMONITOR`Fehler zu erhalten:
    >
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    >
    > durch
    >
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. Klicken Sie im **Test Container**im Menü **Bearbeiten** auf **neues Steuerelement einfügen**.

1. Suchen Sie das Steuerelement, das als `PolyCtl class`bezeichnet wird, und klicken Sie auf **OK**. Es wird ein grünes Dreieck innerhalb eines Kreises angezeigt.

Versuchen Sie, die Anzahl der Seiten zu ändern, indem Sie das nächste Verfahren befolgen. Verwenden Sie zum Ändern der Eigenschaften für eine duale Schnittstelle aus dem **Test Container** **Methoden zum Aufrufen**.

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>So ändern Sie die-Eigenschaft eines Steuer Elements aus dem Test Container

1. Klicken Sie im **Test Container**im Menü **Steuer** Element auf **Methoden aufrufen** .

    Das Dialogfeld **Methode aufrufen** wird angezeigt.

1. Wählen Sie im Dropdown-Listenfeld **Methoden Name** die **PROPPUT** -Version der Eigenschaft **Seiten** aus.

1. Geben Sie im Feld **Parameter Wert** `5` ein, klicken Sie auf **Wert festlegen**, und klicken Sie dann auf **aufrufen**.

Beachten Sie, dass sich das Steuerelement nicht ändert. Obwohl Sie die Anzahl der Seiten intern geändert haben, indem Sie die `m_nSides` Variable festgelegt haben, hat dies nicht bewirkt, dass das Steuerelement neu gezeichnet wird. Wenn Sie zu einer anderen Anwendung wechseln und dann wieder zum **Test Container**wechseln, werden Sie feststellen, dass das Steuerelement neu gezeichnet wurde und über die richtige Anzahl von Seiten verfügt.

Um dieses Problem zu beheben, fügen Sie nach dem Festlegen der Anzahl der Seiten einen aufzurufenden `FireViewChange` Funktion hinzu, der in `IViewObjectExImpl`definiert ist. Wenn das Steuerelement in einem eigenen Fenster ausgeführt wird, wird `FireViewChange` die `InvalidateRect` Methode direkt aufzurufen. Wenn das Steuerelement unter Windows less ausgeführt wird, wird die `InvalidateRect`-Methode auf der Website Schnittstelle des Containers aufgerufen. Dadurch wird das Steuerelement gezwungen, sich selbst neu zu zeichnen.

### <a name="to-add-a-call-to-fireviewchange"></a>So fügen Sie FireViewChange einen Befehl hinzu

1. Aktualisieren Sie PolyCtl. cpp durch Hinzufügen des Aufrufes `FireViewChange` zur `put_Sides`-Methode. Wenn Sie fertig sind, sollte die `put_Sides`-Methode wie folgt aussehen:

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

Nachdem Sie `FireViewChange`hinzugefügt haben, erstellen Sie das Steuerelement erneut, und wiederholen Sie es im Test Container des ActiveX Wenn Sie die Anzahl der Seiten ändern und auf `Invoke`klicken, sollte das Steuerelement sofort angezeigt werden.

Im nächsten Schritt fügen Sie ein Ereignis hinzu.

[Zurück zu Schritt 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [auf Schritt 5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>Weitere Informationen

[Tutorial](../atl/active-template-library-atl-tutorial.md)<br/>
[Testen der Eigenschaften und Ereignisse mit Test Container](../mfc/testing-properties-and-events-with-test-container.md)
