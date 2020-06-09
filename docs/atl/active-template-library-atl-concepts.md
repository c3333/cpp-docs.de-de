---
title: ATL-Konzepte (Active Template Library)
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: cc96b5ed931713ca64a0582ca1cc18a8526ea8af
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616682"
---
# <a name="active-template-library-atl-concepts"></a>ATL-Konzepte (Active Template Library)

Die Active Template Library (ATL) ist ein Satz vorlagenbasierter C++-Klassen, mit deren Hilfe Sie kleine, schnell ausführbare COM-Objekte (Component Object Model) erstellen können. Sie bietet besondere Unterstützung für wichtige COM-Features, einschließlich Bestandsimplementierungen, dualen Schnittstellen, COM-Enumerator-Standardschnittstellen, Verbindungspunkten, abtrennbaren Schnittstellen und ActiveX-Steuerelementen.

Wenn Sie sich viel mit ATL-Programmierung befassen, möchten Sie sicherlich mehr über COM- und .NET-Attribute erfahren, die dafür ausgelegt sind, die COM-Programmierung zu vereinfachen. Weitere Informationen finden Sie unter [Attributiertes Programmieren](../windows/attributed-programming-concepts.md). (COM- und .NET-Attribute dürfen nicht mit dem Feature \[\[attribute]] im C++-Standard verwechselt werden.)

## <a name="in-this-section"></a>In diesem Abschnitt

[Einführung in COM und ATL](introduction-to-com-and-atl.md)<br/>
Stellt die wichtigsten Konzepte hinter dem Component Object Model (COM) vor. Dieser Artikel erläutert außerdem kurz, was ATL ist und wann Sie sie verwenden sollten.

[Grundlagen von ATL-COM-Objekten](fundamentals-of-atl-com-objects.md)<br/>
Erörtert die Beziehung zwischen verschiedenen ATL-Klassen und deren Implementierung.

[Duale Schnittstellen und ATL](dual-interfaces-and-atl.md)<br/>
Beschreibt duale Schnittstellen aus der ATL-Perspektive.

[ATL-Auflistungen und-Enumeratoren](atl-collections-and-enumerators.md)<br/>
Beschreibt die Implementierung und Erstellung von Auflistungen und Enumeratoren in ATL.

[Grundlagen von zusammengesetzten Steuerelementen](atl-composite-control-fundamentals.md)<br/>
Bietet Schrittanleitungen zum Erstellen eines zusammengesetzten Steuerelements. Ein zusammengesetztes Steuerelement ist ein Typ von ActiveX-Steuerelement, der andere ActiveX-Steuerelemente oder Windows-Steuerelemente enthalten kann.

[Fragen und Antworten zur ATL-Steuerelementkapselung](atl-control-containment-faq.md)<br/>
Behandelt die grundlegenden Fragen zum Hosten von Steuerelementen in ATL.

[ATL-COM-Eigenschaften Seiten](atl-com-property-pages.md)<br/>
Veranschaulicht das Angeben und Implementieren von COM-Eigenschaftenseiten.

[ATL-Unterstützung für DHTML-Steuerelemente](atl-support-for-dhtml-controls.md)<br/>
Bietet Schrittanleitungen zum Erstellen eines DHTML-Steuerelements.

[ATL-Verbindungspunkte](atl-connection-points.md)<br/>
Erläutert, was Verbindungspunkte sind und wie sie von ATL implementiert werden.

[Ereignisbehandlung und ATL](event-handling-and-atl.md)<br/>
Beschreibt die Schritte, die Sie zur Behandlung von COM-Ereignissen mithilfe der Klassen [IDispEventImpl](reference/idispeventimpl-class.md) und [IDispEventSimpleImpl](reference/idispeventsimpleimpl-class.md) der ATL ausführen müssen.

[ATL und der freethreaded Marshaller](atl-and-the-free-threaded-marshaler.md)<br/>
Bietet Details zur Option des ATL-Assistenten für einfache Objekte, die es Ihrer Klasse ermöglicht, den Freethreaded Marshaller (FTM) zu aggregieren.

[Angeben des Threadingmodells für ein Projekt](specifying-the-threading-model-for-a-project-atl.md)<br/>
Beschreibt die Makros, die zur Steuerung der Leistung zur Laufzeit im Zusammenhang mit dem Threading in Ihrem Projekt zur Verfügung stehen.

[ATL-Modulklassen](atl-module-classes.md)<br/>
Beschreibt die neuen Modulklassen in ATL 7.0. Modulklassen implementieren die grundlegende Funktionalität, die für ATL erforderlich ist.

[ATL-Dienste](atl-services.md)<br/>
Behandelt die Abfolge von Ereignissen, die bei der Implementierung eines Diensts eintreten. Erörtert darüber hinaus einige der Konzepte im Zusammenhang mit der Entwicklung von Diensten.

[ATL-Fenster Klassen](atl-window-classes.md)<br/>
Beschreibt, wie in ATL Fenster erstellt und als übergeordnete oder untergeordnete Klasse festgelegt werden. Bei ATL-Fensterklassen handelt es sich nicht um COM-Klassen.

[ATL-Auflistungs Klassen](atl-collection-classes.md)<br/>
Beschreibt die Verwendung von Arrays und Zuordnungen in ATL.

[ATL-Registrierungskomponente (Registrar)](atl-registry-component-registrar.md)<br/>
Erörtert Syntax und ersetzbare Parameter bei der ATL-Skripterstellung. Außerdem wird das Einrichten eines statischen Links zur Registrierungskomponente erläutert.

[Programmieren mit ATL- und C-Laufzeitcode](programming-with-atl-and-c-run-time-code.md)<br/>
Erörtert die Vorteile des statischen oder dynamischen Linkens zur C-Laufzeitbibliothek (CRT).

[Programmieren mit CComBSTR](programming-with-ccombstr-atl.md)<br/>
Erörtert verschiedene Situationen beim Programmieren mit `CComBSTR`, in denen Vorsicht angebracht ist.

[Codierungsreferenz](atl-encoding-reference.md)<br/>
Bietet Funktionen und Makros, die das Codieren in einer Bandbreite von Internetstandards unterstützen, darunter uuencode, hexadezimal und UTF8 in atlenc.h.

[Hilfsprogrammreferenz](atl-utilities-reference.md)<br/>
Stellt Code für das Bearbeiten von Pfaden und URLs in Form von [CPathT](reference/cpatht-class.md) und [CUrl](reference/curl-class.md) bereit. In Ihren eigenen Anwendungen kann ein Threadpool, [CThreadPool](reference/cthreadpool-class.md), verwendet werden. Diesen Code finden Sie in „atlpath.h“ und „atlutil.h“.

## <a name="related-sections"></a>Verwandte Abschnitte

[ATL-Tutorial](active-template-library-atl-tutorial.md)<br/>
Führt Sie durch die Erstellung eines Steuerelements und veranschaulicht dabei einige ATL-Grundlagen.

[ATL-Beispiele](../overview/visual-cpp-samples.md)<br/>
Enthält Beschreibungen und Links zu den ATL-Beispielprogrammen.

[Erstellen eines ATL-Projekts](reference/creating-an-atl-project.md)<br/>
Enthält Informationen zum ATL-Projekt-Assistenten.

[ATL-Steuerelement-Assistent](reference/atl-control-wizard.md)<br/>
Erläutert das Hinzufügen von Klassen.

[Attributiertes Programmieren](../windows/attributed-programming-concepts.md)<br/>
Ein Überblick zur Verwendung von Attributen, um die COM-Programmierung zu vereinfachen, mit einer Linkliste zu detaillierteren Themen.

[ATL-Klassen Übersicht](atl-class-overview.md)<br/>
Referenzinformationen und Links zu den ATL-Klassen.
