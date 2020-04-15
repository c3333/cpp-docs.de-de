---
title: Fragen und Antworten zur ATL-Steuerelementkapselung
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: 36ff3381447b46b28908522d65be9f34fe23addf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317398"
---
# <a name="atl-control-containment-faq"></a>Fragen und Antworten zur ATL-Steuerelementkapselung

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Welche ATL-Klassen machen die Kapselung von ActiveX-Steuerelementen verfügbar?

Der Kontrollhostingcode von ATL erfordert nicht, dass Sie ATL-Klassen verwenden. Sie können einfach ein **"AtlAxWin80"-Fenster** erstellen und bei Bedarf die Control-Hosting-API verwenden (weitere Informationen finden Sie unter **Was ist die ATL Control-Hosting API**. Die folgenden Klassen erleichtern jedoch die Verwendung der Containment-Features.

|Klasse|BESCHREIBUNG|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|Umschließt ein **"AtlAxWin80"-Fenster,** stellt Methoden zum Erstellen des Fensters, erstellen eines Steuerelements und/oder Anfügen eines Steuerelements an das Fenster und Abrufen von Schnittstellenzeigern auf dem Hostobjekt bereit.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Umschließt ein **"AtlAxWinLic80"-Fenster,** stellt Methoden zum Erstellen des Fensters, zum Erstellen eines Steuerelements und/oder zum Anfügen eines lizenzierten Steuerelements an das Fenster und zum Abrufen von Schnittstellenzeigern auf dem Hostobjekt bereit.|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Fungiert als Basisklasse für ActiveX-Steuerelementklassen basierend auf einer Dialogressource. Solche Steuerelemente können andere ActiveX-Steuerelemente enthalten.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Fungiert als Basisklasse für Dialogklassen, die auf einer Dialogressource basieren. Solche Dialogfelder können ActiveX-Steuerelemente enthalten.|
|[CWindow](../atl/reference/cwindow-class.md)|Stellt eine Methode bereit, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), die einen Schnittstellenzeiger für ein Steuerelement zurückgibt, wenn die ID des Hostfensters angegeben wird. Darüber hinaus erleichtern die Windows-API-Wrapper die Fensterverwaltung `CWindow` im Allgemeinen.|

## <a name="what-is-the-atl-control-hosting-api"></a>Was ist die API des ATL-Steuerelementhostings?

Die Control-Hosting-API von ATL ist der Satz von Funktionen, mit denen jedes Fenster als ActiveX-Steuerelementcontainer fungieren kann. Diese Funktionen können statisch oder dynamisch mit Ihrem Projekt verknüpft werden, da sie als Quellcode verfügbar sind und von ATL90.dll verfügbar gemacht werden. Die Steuerungshostingfunktionen sind in der folgenden Tabelle aufgeführt.

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Erstellt ein Hostobjekt, verbindet es mit dem angegebenen Fenster und fügt dann ein vorhandenes Steuerelement an.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Erstellt ein Hostobjekt, verbindet es mit dem bereitgestellten Fenster und lädt dann ein Steuerelement.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Erstellt ein Hostobjekt, verbindet es mit dem angegebenen Fenster und lädt dann ein Steuerelement (außerdem können Ereignissenken eingerichtet werden).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Erstellt ein modusloses Dialogfeld aus einer Dialogressource und gibt das Fensterhandle zurück.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Erstellt ein modales Dialogfeld aus einer Dialogressource.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Gibt den **IUnknown-Schnittstellenzeiger** des in einem Fenster gehosteten Steuerelements zurück.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Gibt den **IUnknown-Schnittstellenzeiger** des Hostobjekts zurück, das mit einem Fenster verbunden ist.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Initialisiert den Steuerelementhostingcode.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Der Code für das Steuerelementhosting wird nicht initialisiert.|

Die `HWND` Parameter in den ersten drei Funktionen müssen ein vorhandenes Fenster (fast) jedes Typs sein. Wenn Sie eine dieser drei Funktionen explizit aufrufen (in der Regel müssen Sie es nicht), übergeben Sie kein Handle an ein Fenster, das bereits als Host fungiert (wenn Sie dies tun, wird das vorhandene Hostobjekt nicht freigegeben).

Die ersten sieben Funktionen rufen [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implizit auf.

> [!NOTE]
> Die Control-Hosting-API bildet die Grundlage für die Unterstützung von ATL für Die ActiveX-Steuerelementbeschränkung. In der Regel ist es jedoch wenig notwendig, diese Funktionen direkt aufzurufen, wenn Sie die Wrapperklassen von ATL nutzen oder voll ausnutzen. Weitere Informationen finden Sie unter [Welche ATL-Klassen ActiveX Control Containment erleichtern.](which-atl-classes-facilitate-activex-control-containment-q.md)

## <a name="what-is-atlaxwin100"></a>Was ist AtlAxWin100?

`AtlAxWin100`ist der Name einer Fensterklasse, die die Steuerungshostingfunktionalität von ATL bereitstellt. Wenn Sie eine Instanz dieser Klasse erstellen, verwendet die Fensterprozedur automatisch die Steuerelementhosting-API, um ein Hostobjekt zu erstellen, das dem Fenster zugeordnet ist, und es mit dem Steuerelement zu laden, das Sie als Titel des Fensters angeben.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Wann muss ich AtlAxWinInit aufrufen?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) registriert die Fensterklasse **"AtlAxWin80"** (plus ein paar benutzerdefinierte Fenstermeldungen), daher muss diese Funktion aufgerufen werden, bevor Sie versuchen, ein Hostfenster zu erstellen. Sie müssen diese Funktion jedoch nicht immer explizit aufrufen, da die Hosting-APIs (und die Klassen, die sie verwenden) diese Funktion häufig für Sie aufrufen. Es schadet nicht, diese Funktion mehr als einmal aufzurufen.

## <a name="what-is-a-host-object"></a>Was ist ein Hostobjekt?

Ein Hostobjekt ist ein COM-Objekt, das den ActiveX-Steuerelementcontainer darstellt, der von ATL für ein bestimmtes Fenster bereitgestellt wird. Das Hostobjekt unterklassen das Containerfenster, sodass es Nachrichten an das Steuerelement reflektieren kann, stellt die erforderlichen Containerschnittstellen bereit, die vom Steuerelement verwendet werden sollen, und es macht die [Schnittstellen IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) und [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) verfügbar, damit Sie die Umgebung des Steuerelements konfigurieren können.

Sie können das Hostobjekt verwenden, um die Umgebungseigenschaften des Containers festzulegen.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Kann ich in einem Fenster mehrere Steuerelemente hosten?

Es ist nicht möglich, mehr als ein Steuerelement in einem einzelnen ATL-Hostfenster zu hosten. Jedes Hostfenster ist so konzipiert, dass es jeweils genau ein Steuerelement enthält (dies ermöglicht einen einfachen Mechanismus für die Verarbeitung von Nachrichtenreflexion und Umgebungseigenschaften pro Steuerung). Wenn Sie jedoch mehrere Steuerelemente in einem einzigen Fenster anzeigen müssen, ist es einfach, mehrere Hostfenster als untergeordnete Elemente dieses Fensters zu erstellen.

## <a name="can-i-reuse-a-host-window"></a>Kann ich ein Hostfenster wiederverwenden?

Es wird nicht empfohlen, Hostfenster wiederzuverwenden. Um die Robustheit des Codes zu gewährleisten, sollten Sie die Lebensdauer des Hostfensters an die Lebensdauer eines einzelnen Steuerelements binden.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Wann muss ich AtlAxWinInit aufrufen?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) entregistriert die Fensterklasse **"AtlAxWin80".** Sie sollten diese Funktion aufrufen (wenn Sie keine Hostfenster mehr erstellen müssen), nachdem alle vorhandenen Hostfenster zerstört wurden. Wenn Sie diese Funktion nicht aufrufen, wird die Registrierung der Fensterklasse automatisch aufgehoben, wenn der Prozess beendet wird.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hosten eines ActiveX-Steuerelement mit ATL-XHost

Das Beispiel in diesem Abschnitt zeigt, wie AXHost erstellt wird und wie ein ActiveX-Steuerelement mit verschiedenen ATL-Funktionen hosten wird. Außerdem wird gezeigt, wie Sie über das gehostete Steuerelement auf die Steuerelement- und Senkenereignisse (mit [IDispEventImpl)](../atl/reference/idispeventimpl-class.md)zugreifen können. Das Beispiel hostet das Kalendersteuerelement in einem Hauptfenster oder in einem untergeordneten Fenster.

Beachten Sie die `USE_METHOD` Definition des Symbols. Sie können den Wert dieses Symbols so ändern, dass er zwischen 1 und 8 variiert. Der Wert des Symbols bestimmt, wie das Steuerelement erstellt wird:

- Für gerade Nummerierte `USE_METHOD`Werte von wird der Aufruf zum Erstellen der Hostunterklassen ein Fenster erstellt und in einen Steuerelementhost konvertiert. Bei ungeraden Werten erstellt der Code ein untergeordnetes Fenster, das als Host fungiert.

- Bei Werten `USE_METHOD` zwischen 1 und 4 wird der Zugriff auf die Steuerung und das Senken von Ereignissen in dem Aufruf ausgeführt, der auch den Host erstellt. Werte zwischen 5 und 8 abfragen den Host nach Schnittstellen und hooken die Senke.

Hier finden Sie eine Zusammenfassung:

|USE_METHOD|Host|Steuerung des Zugriffs und Fallen von Ereignis|Funktion demonstriert|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Kinderfenster|Ein Schritt|CreateControlLicEx|
|2|Hauptfenster|Ein Schritt|AtlAxCreateControlLicEx|
|3|Kinderfenster|Ein Schritt|CreateControlEx|
|4|Hauptfenster|Ein Schritt|AtlAxCreateControlEx|
|5|Kinderfenster|Mehrere Schritte|CreateControlLic|
|6|Hauptfenster|Mehrere Schritte|AtlAxCreateControlLic|
|7|Kinderfenster|Mehrere Schritte|CreateControl|
|8|Hauptfenster|Mehrere Schritte|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Siehe auch

[Fragen und Antworten zur Steuerelementkapselung](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[CAxWindow2T-Klasse](../atl/reference/caxwindow2t-class.md)<br/>
[IAxWinHostWindowlic-Schnittstelle](../atl/reference/iaxwinhostwindowlic-interface.md)
