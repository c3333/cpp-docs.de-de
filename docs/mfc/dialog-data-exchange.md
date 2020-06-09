---
title: Dialogdatenaustausch
ms.date: 11/19/2018
helpviewer_keywords:
- initializing dialog boxes
- canceling data exchange
- dialog box data, retrieving
- DDX (dialog data exchange), data exchange mechanism
- dialog boxes [MFC], initializing
- dialog boxes [MFC], retrieving user input using DDX
- dialog box data
- dialog boxes [MFC], data exchange
- CDataExchange class [MFC], using DDX
- DoDataExchange method [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- transferring dialog box data
- DDX (dialog data exchange), canceling
- UpdateData method [MFC]
- retrieving dialog box data [MFC]
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
ms.openlocfilehash: c12953ab0b9922788747246a97115188b2f686ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616831"
---
# <a name="dialog-data-exchange"></a>Dialogdatenaustausch

Wenn Sie den DDX-Mechanismus verwenden, legen Sie die Anfangswerte der Element Variablen des Dialog Objekts fest, in der Regel in Ihrem `OnInitDialog` Handler oder im Dialog-Konstruktor. Unmittelbar bevor das Dialogfeld angezeigt wird, überträgt der DDX-Mechanismus des Frameworks die Werte der Element Variablen an die Steuerelemente im Dialogfeld, wo Sie angezeigt werden, wenn das Dialogfeld selbst als Antwort auf oder angezeigt wird `DoModal` `Create` . Die Standard Implementierung von `OnInitDialog` in `CDialog` Ruft die `UpdateData` Member-Funktion der-Klasse `CWnd` auf, um die Steuerelemente im Dialogfeld zu initialisieren.

Derselbe Mechanismus überträgt Werte aus den Steuerelementen an die Element Variablen, wenn der Benutzer auf die Schaltfläche OK klickt (oder wenn Sie die `UpdateData` Member-Funktion mit dem Argument **true**aufrufen). Der Mechanismus für die Validierung von Dialog Daten überprüft alle Datenelemente, für die Sie Validierungsregeln angegeben haben.

In der folgenden Abbildung wird der Dialog Datenaustausch veranschaulicht.

![Dialogfeld-Datenaustausch](../mfc/media/vc379d1.gif "Dialogfeld-Datenaustausch") <br/>
Dialogdatenaustausch

`UpdateData`funktioniert in beide Richtungen, wie durch den **booleschen** Parameter angegeben, der an ihn übergeben wird. Um den Austausch auszuführen, `UpdateData` richtet ein- `CDataExchange` Objekt ein und ruft die Überschreibung der `CDialog` -Member-Funktion Ihrer Dialog Klasse auf `DoDataExchange` . `DoDataExchange`nimmt ein Argument vom Typ an `CDataExchange` . Das `CDataExchange` an übergebenen-Objekt `UpdateData` stellt den Kontext des Austauschs dar, wobei solche Informationen als Richtung des Austauschs definiert werden.

Wenn Sie (oder ein Code-Assistent) `DoDataExchange` überschreiben, geben Sie einen Rückruf für eine DDX-Funktion pro Datenmember (-Steuerelement) an. Jede DDX-Funktion weiß, wie Sie Daten in beiden Richtungen austauschen können, basierend auf dem Kontext, der durch das-Argument angegeben wird, das von `CDataExchange` an übergeben `DoDataExchange` wird `UpdateData`

MFC bietet viele DDX-Funktionen für verschiedene Arten von Exchange. Das folgende Beispiel zeigt eine `DoDataExchange` außer Kraft setzung, bei der zwei DDX-Funktionen und eine DDV-Funktion aufgerufen werden:

[!code-cpp[NVC_MFCControlLadenDialog#49](codesnippet/cpp/dialog-data-exchange_1.cpp)]

Die `DDX_` `DDV_` Linien und sind eine Datenzuordnung. Die gezeigten DDX-und DDV-Beispiel Funktionen sind für ein Kontrollkästchen-Steuerelement und ein Bearbeitungsfeld-Steuerelement vorgesehen.

Wenn der Benutzer ein modales Dialogfeld abbricht, wird das `OnCancel` Dialogfeld von der Member-Funktion beendet, und `DoModal` der Wert " **IDCANCEL**" wird zurückgegeben. In diesem Fall werden keine Daten zwischen dem Dialogfeld und dem Dialogfeld Objekt ausgetauscht.

## <a name="see-also"></a>Siehe auch

[Dialogdatenaustausch und -validierung](dialog-data-exchange-and-validation.md)<br/>
[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)<br/>
[Validieren von Dialogfelddaten](dialog-data-validation.md)
