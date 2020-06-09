---
title: Automation
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
ms.openlocfilehash: e5790be14f26f59c2b51b339c8bee7c5eca7d692
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616513"
---
# <a name="automation"></a>Automation

Automation (früher: OLE-Automatisierung) ermöglicht es einer Anwendung, die in einer anderen Anwendung implementierten Objekte zu bearbeiten oder Objekte verfügbar zu machen, damit sie bearbeitet werden können.

Ein [Automatisierungsserver](automation-servers.md) ist eine Anwendung (ein COM-Servertyp), die seine Funktionalität über COM-Schnittstellen für andere Anwendungen, sogenannte [Automatisierungsclients](automation-clients.md), zur Verfügung stellt. Dank der Verfügbarkeit können Automatisierungsclients bestimmte Funktionen automatisieren, indem direkt auf Objekte zugegriffen und die angebotenen Dienste verwendet werden.

Automatisierungsserver und -clients verwenden COM-Schnittstellen, die immer von `IDispatch` abgeleitet sind und einen bestimmten Satz von Datentypen, genannt Automatisierungstypen, akzeptieren und zurückgeben. Sie können jedes Objekt automatisieren, das eine Automatisierungsschnittstelle verfügbar macht, die Methoden und Eigenschaften bereitstellt, auf die Sie von anderen Programmen zugreifen können. Automation ist für OLE und COM-Objekte verfügbar. Das automatisierte Objekt kann lokal oder remote (sprich, auf einem anderen Computer, auf den Sie über ein Netzwerk zugreifen können) sein. Es gibt somit zwei Kategorien der Automatisierung:

- Automatisierung (lokal).

- Remoteautomatisierung (über ein Netzwerk mithilfe von Distributed COM, oder DCOM).

Das Verfügbarmachen von Objekten ist nützlich, wenn Anwendungen Funktionen bereitstellen, die hilfreich für andere Anwendungen sind. Ein ActiveX-Steuerelement ist beispielsweise ein Automatisierungsservertyp; die Anwendung, in der das ActiveX-Steuerelement gehostet wird, ist der Automatisierungsclient dieses Steuerelements.

Ein weiteres Beispiel ist ein Textverarbeitungsprogramm, das seine Funktion zur Rechtschreibprüfung für andere Programme zur Verfügung stellt. Das Verfügbarmachen von Objekten ermöglicht es den Herstellern, ihre Anwendungen zu verbessern, indem sie die vordefinierten Funktionen von anderen Anwendungen nutzen. Auf diese Weise wendet Automation einige der Prinzipien der objektorientierten Programmierung an, z. B. Wiederverwendung und Kapselung auf der Anwendungsebene selbst.

Wichtiger ist die Unterstützung, die Automation Benutzern und Lösungsanbietern bietet. Durch das Verfügbarmachen von Anwendungsfunktionen über eine gemeinsame, klar definierte Schnittstelle ermöglicht Automation die Erstellung von umfassenden Lösungen in einer einzelnen allgemeinen Programmiersprache, z. B. Microsoft Visual Basic, statt in verschiedenen anwendungsspezifischen Makrosprachen.

Viele kommerzielle Anwendungen, wie Microsoft Excel und Microsoft Visual C++, ermöglichen es Ihnen, viele ihrer Funktionen zu automatisieren. In Visual C++ können Sie beispielsweise VBScript -Makros schreiben, um Builds, Aspekte der Codebearbeitung oder von Debuggingaufgaben zu automatisieren.

## <a name="passing-parameters-in-automation"></a><a name="_core_passing_parameters_in_automation"></a> Übergeben von Parametern in Automation

Eine Schwierigkeit bei der Erstellung von Automatisierungsmethoden besteht darin, einen einheitlichen „sicheren“ Mechanismus zum Übergeben von Daten zwischen Automatisierungsservern und -clients bereitzustellen. Automation verwendet den **VARIANT** -Typ, um Daten zu übergeben. Der **VARIANT** -Typ ist eine Union mit Tags. Sie verfügt über ein Datenelement für den Wert (wobei es sich um eine anonyme C++-Union handelt) und ein Datenelement, das den in der Union gespeicherten Informationstyp angibt. Der **VARIANT** -Typ unterstützt eine Reihe von Standarddatentypen: 2- und 4-Byte-Ganzzahlen, 4 und 8-Byte-Gleitkommazahlen, Zeichenfolgen und boolesche Werte. Außerdem werden die **HRESULT** -(OLE-Fehlercodes), **Currency** -(ein numerischer festgelegter Typ) und **Datums** -(absolute Datums-und Uhrzeittyp) sowie Zeiger auf `IUnknown` -und- `IDispatch` Schnittstellen unterstützt.

Der **VARIANT** -Typ ist in der [COleVariant](reference/colevariant-class.md) -Klasse gekapselt. Die unterstützenden **CURRENCY** - und **DATE** -Klassen sind in den [COleCurrency](reference/colecurrency-class.md) - und [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) -Klassen gekapselt.

## <a name="automation-samples"></a>Automatisierungsbeispiele

- [AUTOCLIK](../overview/visual-cpp-samples.md) Verwenden Sie dieses Beispiel, um mehr über Automatisierungsverfahren zu lernen und als Grundlage für weitere Informationen zur Remoteautomatisierung.

- [ACDUAL](../overview/visual-cpp-samples.md) Fügt einer Automatisierungsserveranwendung duale Schnittstellen hinzu.

- [CALCDRIV](../overview/visual-cpp-samples.md) Automatisierungsclientanwendung mit MFCCALC.

- [INPROC](../overview/visual-cpp-samples.md) Demonstration einer prozessinternen Automatisierungsserveranwendung.

- [IPDRIVE](../overview/visual-cpp-samples.md) Automatisierungsclientanwendung mit INPROC.

- [MFCCALC](../overview/visual-cpp-samples.md) Demonstration einer Automatisierungsclientanwendung.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Automatisierungsclients](automation-clients.md)

- [Automatisierungsserver](automation-servers.md)

- [OLE](ole-in-mfc.md)

- [Active Technology](mfc-com.md)

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Hinzufügen einer Automatisierungsklasse](automation-servers.md)

- [Verwenden von Typbibliotheken](automation-clients-using-type-libraries.md)

- [Zugreifen auf Automatisierungsserver](automation-servers.md)

- [Schreiben von Automatisierungsclients in C++](automation-clients.md)

## <a name="see-also"></a>Siehe auch

[MFC COM](mfc-com.md)
