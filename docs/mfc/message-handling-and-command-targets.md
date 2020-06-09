---
title: Meldungsbehandlung und Befehlsziele
ms.date: 11/04/2016
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
ms.openlocfilehash: cbcbce1e476fef0d076f9c25b46b3166c1eb5935
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624349"
---
# <a name="message-handling-and-command-targets"></a>Meldungsbehandlung und Befehlsziele

Die Befehls Dispatchschnittstelle `IOleCommandTarget` definiert einen einfachen und erweiterbaren Mechanismus zum Abfragen und Ausführen von Befehlen. Dieser Mechanismus ist einfacher als die Automatisierung `IDispatch` , da er vollständig auf einem Standardsatz von Befehlen basiert, Befehle nur selten Argumente haben und keine Typinformationen beteiligt sind (die Typsicherheit wird auch für Befehlsargumente verringert).

Im Entwurfs Schnittstellendesign der Befehls Verteilung gehört jeder Befehl zu einer Befehlsgruppe, die selbst durch eine **GUID**identifiziert wird. Daher kann jeder Benutzer eine neue Gruppe definieren und alle Befehle innerhalb dieser Gruppe definieren, ohne sich mit Microsoft oder einem anderen Hersteller koordinieren zu müssen. (Dies ist im Wesentlichen die gleiche Definition wie eine **dispinterface** Plus **DispIds** in Automation. Hier gibt es eine Überschneidung, obwohl dieser Befehls Routing Mechanismus nur für Befehls Routing und nicht für die Skript-/Programmierbarkeits-in großem Umfang als Automatisierungs Handles gilt.)

`IOleCommandTarget`behandelt die folgenden Szenarien:

- Wenn ein Objekt direkt aktiviert ist, werden in der Regel nur die Symbolleisten des-Objekts angezeigt, und die Symbolleisten des-Objekts verfügen möglicherweise über Schaltflächen für einige der Container Befehle wie " **Print**", " **Print Preview**", " **Save**", " **New**", " **Zoom**" und andere. (Bei direkten Aktivierungs Standards wird empfohlen, dass Objekte solche Schaltflächen aus ihren Symbolleisten entfernen oder zumindest deaktivieren. Dieser Entwurf ermöglicht es, dass diese Befehle aktiviert und dennoch an den richtigen Handler weitergeleitet werden.) Zurzeit gibt es keinen Mechanismus, mit dem das-Objekt diese Befehle an den Container verteilen kann.

- Wenn ein aktives Dokument in einen aktiven Dokument Container (z. b. Office-Binder) eingebettet ist, muss der Container möglicherweise Befehle wie **Print**, **Page Setup**, **Properties**und andere an das enthaltene aktive Dokument senden.

Dieses einfache Befehls Routing kann durch vorhandene Automatisierungs Standards und behandelt werden `IDispatch` . Der Aufwand, der mit verbunden ist `IDispatch` , ist jedoch mehr als erforderlich. es `IOleCommandTarget` bietet daher eine einfachere Möglichkeit, dieselben enden zu erreichen:

```
interface IOleCommandTarget : IUnknown
    {
    HRESULT QueryStatus(
        [in] GUID *pguidCmdGroup,
        [in] ULONG cCmds,
        [in,out][size_is(cCmds)] OLECMD *prgCmds,
        [in,out] OLECMDTEXT *pCmdText);
    HRESULT Exec(
        [in] GUID *pguidCmdGroup,
        [in] DWORD nCmdID,
        [in] DWORD nCmdExecOpt,
        [in] VARIANTARG *pvaIn,
        [in,out] VARIANTARG *pvaOut);
    }
```

Die- `QueryStatus` Methode testet hier, ob eine bestimmte Gruppe von Befehlen, die mit einer **GUID**identifizierte Menge, unterstützt wird. Dieser Befehl füllt ein Array von **olecmd** -Werten (Strukturen) mit der unterstützten Liste der Befehle sowie der Rückgabe von Text auf, der den Namen eines Befehls und/oder Statusinformationen beschreibt. Wenn der Aufrufer einen Befehl aufrufen möchte, kann er den Befehl (und die Set- **GUID**) `Exec` zusammen mit Optionen und Argumenten an übergeben und einen Rückgabewert zurückerhalten.

## <a name="see-also"></a>Siehe auch

[Aktive Dokumente-Container](active-document-containers.md)
