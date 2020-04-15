---
title: 'MFC-ActiveX-Steuerelemente: Serialisierung'
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
ms.openlocfilehash: d804486b612906f537b6ed1665dfc0cec5149826
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364548"
---
# <a name="mfc-activex-controls-serializing"></a>MFC-ActiveX-Steuerelemente: Serialisierung

In diesem Artikel wird erläutert, wie ein ActiveX-Steuerelement serialisiert wird. Serialisierung ist der Prozess des Lesens oder Schreibens von einem persistenten Speichermedium, z. B. einer Datenträgerdatei. Die Microsoft Foundation Class (MFC)-Bibliothek bietet integrierte `CObject`Unterstützung für die Serialisierung in der Klasse . `COleControl`erweitert diese Unterstützung auf ActiveX-Steuerelemente durch die Verwendung eines Eigenschaftenaustauschmechanismus.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

Die Serialisierung für ActiveX-Steuerelemente wird durch Überschreiben von [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)implementiert. Diese Funktion, die beim Laden und Speichern des Steuerelementobjekts aufgerufen wird, speichert alle Eigenschaften, die mit einer Membervariablen oder einer Membervariablen mit Änderungsbenachrichtigung implementiert sind.

In den folgenden Themen werden die wichtigsten Probleme im Zusammenhang mit der Serialisierung eines ActiveX-Steuerelements behandelt:

- Implementieren `DoPropExchange` der Funktion zur Serialisierung des Steuerobjekts

- [Anpassen des Serialisierungsprozesses](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implementieren der Versionsunterstützung](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>Implementieren der DoPropExchange-Funktion

Wenn Sie den ActiveX Control-Assistenten zum Generieren des Steuerelementprojekts verwenden, werden der Steuerelementklasse automatisch mehrere Standardhandlerfunktionen hinzugefügt, einschließlich der Standardimplementierung von [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Das folgende Beispiel zeigt den Code, der Klassen hinzugefügt wurde, die mit dem ActiveX Control Wizard erstellt wurden:

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Wenn Sie eine Eigenschaft persistent `DoPropExchange` machen möchten, ändern Sie dies, indem Sie der Eigenschaftsaustauschfunktion einen Aufruf hinzufügen. Das folgende Beispiel veranschaulicht die Serialisierung einer benutzerdefinierten Boolean CircleShape-Eigenschaft, bei der die CircleShape-Eigenschaft den Standardwert **TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

In der folgenden Tabelle sind die möglichen Eigenschaftenaustauschfunktionen aufgeführt, mit denen Sie die Eigenschaften des Steuerelements serialisieren können:

|Eigenschaftenaustauschfunktionen|Zweck|
|---------------------------------|-------------|
|**PX_Blob( )**|Serialisiert eine BLOB-Dateneigenschaft (Binary Large Object) vom Typ.|
|**PX_Bool( )**|Serialisiert eine boolesche Eigenschaft vom Typ.|
|**PX_Color( )**|Serialisiert eine Typfarbeigenschaft.|
|**PX_Currency( )**|Serialisiert eine **CY-Eigenschaft** (Währung).|
|**PX_Double( )**|Serialisiert eine **Typ-Double-Eigenschaft.**|
|**PX_Font( )**|Serialisiert eine Font-Typeigenschaft.|
|**PX_Float( )**|Serialisiert eine **float** typ float-Eigenschaft.|
|**PX_IUnknown( )**|Serialisiert eine Eigenschaft `LPUNKNOWN`vom Typ .|
|**PX_Long( )**|Serialisiert eine **long** type long-Eigenschaft.|
|**PX_Picture( )**|Serialisiert eine Picture-Eigenschaft vom Typ.|
|**PX_Short( )**|Serialisiert eine **short** type short-Eigenschaft.|
|**PXstring( )**|Serialisiert eine `CString` Typeigenschaft.|
|**PX_ULong( )**|Serialisiert eine **ULONG-Eigenschaft** vom Typ.|
|**PX_UShort( )**|Serialisiert eine **USHORT-Eigenschaft** vom Typ.|

Weitere Informationen zu diesen Eigenschaftenaustauschfunktionen finden Sie unter [Persistenz von OLE-Steuerelementen](../mfc/reference/persistence-of-ole-controls.md) in der *MFC-Referenz*.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>Anpassen des Standardverhaltens von DoPropExchange

Die Standardimplementierung `DoPropertyExchange` von (wie im vorherigen Thema gezeigt) `COleControl`ruft die Basisklasse auf. Dadurch wird der Satz von Eigenschaften `COleControl`serialisiert, die automatisch von unterstützt werden, der mehr Speicherplatz verbraucht, als nur die benutzerdefinierten Eigenschaften des Steuerelements zu serialisieren. Durch das Entfernen dieses Aufrufs kann das Objekt nur die Eigenschaften serialisieren, die Sie für wichtig erachten. Alle Bestandseigenschaften, die das Steuerelement implementiert hat, werden beim Speichern oder Laden des Steuerelementobjekts nicht serialisiert, es sei denn, Sie fügen **explizit PX_** Aufrufe für sie hinzu.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>Implementieren der Versionsunterstützung

Die Versionsunterstützung ermöglicht es einem überarbeiteten ActiveX-Steuerelement, neue persistente Eigenschaften hinzuzufügen und dennoch den persistenten Zustand zu erkennen und zu laden, der von einer früheren Version des Steuerelements erstellt wurde. Um die Version eines Steuerelements als Teil seiner persistenten Daten verfügbar zu machen, `DoPropExchange` rufen Sie [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) in der Funktion des Steuerelements auf. Dieser Aufruf wird automatisch eingefügt, wenn das ActiveX-Steuerelement mit dem ActiveX Control Wizard erstellt wurde. Sie kann entfernt werden, wenn keine Versionsunterstützung erforderlich ist. Die Kosten in der Kontrollgröße sind jedoch sehr gering (4 Byte) für die zusätzliche Flexibilität, die die Versionsunterstützung bietet.

Wenn das Steuerelement nicht mit dem ActiveX Control `COleControl::ExchangeVersion` Wizard erstellt wurde, fügen Sie `DoPropExchange` einen Aufruf hinzu, `COleControl::DoPropExchange`indem Sie die folgende Zeile am Anfang Ihrer Funktion einfügen (vor dem Aufruf von):

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Sie können jedes **DWORD** als Versionsnummer verwenden. Für Projekte, die vom `_wVerMinor` ActiveX Control Wizard generiert werden, werden sie `_wVerMajor` als Standard verwendet. Dabei handelt es sich um globale Konstanten, die in der Implementierungsdatei der ActiveX-Steuerelementklasse des Projekts definiert sind. Innerhalb des Rests `DoPropExchange` Ihrer Funktion können Sie [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion) jederzeit aufrufen, um die Version abzurufen, die Sie speichern oder abrufen.

Im folgenden Beispiel verfügt Version 1 dieses Beispielsteuerelements nur über eine "ReleaseDate"-Eigenschaft. Version 2 fügt eine "OriginalDate"-Eigenschaft hinzu. Wenn das Steuerelement angewiesen wird, den persistenten Zustand aus der alten Version zu laden, initialisiert es die Membervariable für die neue Eigenschaft auf einen Standardwert.

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Standardmäßig "konvertiert" ein Steuerelement alte Daten in das neueste Format. Wenn beispielsweise Version 2 eines Steuerelements Daten lädt, die in Version 1 gespeichert wurden, wird das Format version 2 geschrieben, wenn es erneut gespeichert wird. Wenn das Steuerelement Daten im zuletzt gelesenen **FALSE** Format speichern soll, `ExchangeVersion`übergeben Sie FALSE beim Aufruf als dritten Parameter. Dieser dritte Parameter ist optional und standardmäßig **TRUE.**

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)
