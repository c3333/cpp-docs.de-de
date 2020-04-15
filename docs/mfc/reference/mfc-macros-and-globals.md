---
title: MFC-Makros, globale Funktionen und globale Variablen
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions [MFC]
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
ms.openlocfilehash: ed45fc7014bda18887be6dc8fbcdff8ba9a9c5f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373041"
---
# <a name="mfc-macros-and-globals"></a>MFC-Makros, globale Funktionen und globale Variablen

Die Microsoft Foundation Class-Bibliothek kann in zwei Hauptabschnitte unterteilt werden: (1) die MFC-Klassen und (2) Makros und Globals. Wenn eine Funktion oder eine Variable kein Member einer Klasse ist, ist es eine globale Funktion oder Variable.

Die MFC-Bibliothek und die ATL (Active Template Library) nutzen Makros für die Zeichenfolgenkonvertierung gemeinsam. Weitere Informationen finden Sie unter [String Conversion Macros](../../atl/reference/string-conversion-macros.md) in der ATL-Dokumentation.

Die MFC-Makros und -Globals bieten Funktionen in den folgenden Kategorien.

## <a name="general-mfc"></a>MFC allgemein

- [Datentypen](data-types-mfc.md)

- [Typumwandlung von MFC-Klassenobjekten](type-casting-of-mfc-class-objects.md)

- [Laufzeitobjektmodelldienste](run-time-object-model-services.md)

- [Diagnosedienste](diagnostic-services.md)

- [Ausnahmeverarbeitung](exception-processing.md)

- [CString-Formatierung und Meldungsbox-Anzeige](cstring-formatting-and-message-box-display.md)

- [Nachrichtenzuordnungen](message-map-macros-mfc.md)

- [Delegate- und Schnittstellenzuordnungen](delegate-and-interface-maps.md)

- [Module und DLLs](extension-dll-macros.md)

- [Anwendungsinformationen und Management](application-information-and-management.md)

- [Standardbefehls- und Fenster-IDs](standard-command-and-window-ids.md)

- [Sammlungsklassenhelfer](collection-class-helpers.md)

- [Graue und gezauderte Bitmap-Funktionen](gray-and-dithered-bitmap-functions.md)

- [Standardroutinen für den Dialogdatenaustausch (Dialog Data Exchange, DDX)](standard-dialog-data-exchange-routines.md)

- [Standardroutinen für die Dialogfelddatenvalidierung (Dialog Data Validation, DDV)](standard-dialog-data-validation-routines.md)

- [AFX-Meldungen](afx-messages.md)

- [Steuerelementstile für die Symbolleiste](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>Datenbank

- [Record Field Exchange (RFX)-Funktionen](record-field-exchange-functions.md) und [Bulk Record Field Exchange (Bulk RFX)-Funktionen](record-field-exchange-functions.md) für die MFC ODBC-Klassen

- [Datensatzfeldaustauschfunktionen (DFX)](record-field-exchange-functions.md) für die MFC DAO-Klassen

- [Dialogdatenaustauschfunktionen (DDX) für CRecordView und CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (MFC ODBC- und DAO-Klassen)

- [Funktionen für den Dialogdatenaustausch (DDX) für OLE-Steuerelemente](dialog-data-exchange-functions-for-ole-controls.md)

- [Makros und Globals, die das direkte Aufrufen von Open Database Connectivity(ODBC)-API-Funktionen unterstützen](database-macros-and-globals.md)

- [Initialisierung und Beendigung der DAO-Datenbank-Engine](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [Internet-URL-Analyse globaler Daten](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>DHTML-/DHTML-Ereigniszuordnungen

- [Hilfsmakros für den DHTML-Dialogdatenaustausch (DDX)](ddx-dhtml-helper-macros.md)

- [DHTML-Ereigniszuordnungen](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [OLE-Initialisierung](ole-initialization.md)

- [Anwendungssteuerung](application-control.md)

- [Dispatch-Karten](dispatch-maps.md)

Darüber hinaus bietet MFC eine Funktion namens [AfxEnableControlContainer,](ole-initialization.md#afxenablecontrolcontainer) mit der alle mit MFC 4.0 entwickelten OLE-Container eingebettete OLE-Steuerelemente vollständig unterstützen können.

## <a name="ole-controls"></a>OLE-Steuerelemente

- [Variantenparametertypkonstanten](variant-parameter-type-constants.md)

- [Typbibliothekszugriff](type-library-access.md)

- [Eigenschaftenseiten](property-pages-mfc.md)

- [Ereigniskarten](event-maps.md)

- [Ereignissenkenkarten](event-sink-maps.md)

- [Verbindungskarten](connection-maps.md)

- [Registrieren von OLE-Steuerelementen](registering-ole-controls.md)

- [Klassenfabriken und Lizenzierung](class-factories-and-licensing.md)

- [Persistenz von OLE-Steuerelementen](persistence-of-ole-controls.md)

Im ersten Teil dieses Abschnitts wird kurz auf die einzelnen der oben genannten Kategorien eingegangen. Darüber hinaus werden die Globals und Makros in der Kategorie zusammen mit einer kurzen Beschreibung der Funktionen aufgeführt. Anschließend folgt eine Beschreibung der globalen Funktionen, der globalen Variablen und der Makros in der MFC-Bibliothek.

> [!NOTE]
> Viele globale Funktionen beginnen mit dem Präfix "Afx". Einige Funktionen, beispielsweise die Funktionen für den Dialogdatenaustausch (DDX) sowie viele Datenbankfunktionen, entsprechen dieser Konvention jedoch nicht. Alle globalen Variablen beginnen mit "afx" als Präfix. Makros beginnen nicht mit einem bestimmten Präfix, werden aber in Großbuchstaben geschrieben.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../mfc/class-library-overview.md)
