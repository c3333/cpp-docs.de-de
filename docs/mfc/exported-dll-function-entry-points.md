---
title: Einstiegspunkte für exportierte DLL-Funktionen
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
ms.openlocfilehash: c521cad666864c728fd871b460cf0c92b815e414
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622644"
---
# <a name="exported-dll-function-entry-points"></a>Einstiegspunkte für exportierte DLL-Funktionen

Verwenden Sie für exportierte Funktionen einer DLL das [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) -Makro, um den richtigen globalen Zustand beizubehalten, wenn Sie vom dll-Modul zur dll der aufrufenden Anwendung wechseln.

Beim Aufruf wird dieses Makro `pModuleState` , ein Zeiger auf eine- `AFX_MODULE_STATE` Struktur, die globale Daten für das Modul enthält, als effektiver Modul Zustand für den Rest des enthaltenden Bereichs der Funktion festgelegt. Wenn Sie den Bereich, der das Makro enthält, verlassen, wird der vorherige effektive Modul Zustand automatisch wieder hergestellt.

Dieser Wechsel wird durch das Erstellen einer Instanz einer- `AFX_MODULE_STATE` Klasse im Stapel erreicht. In seinem Konstruktor erhält diese Klasse einen Zeiger auf den aktuellen Modul Zustand und speichert Sie in einer Element Variablen und legt dann `pModuleState` als neuen effektiven Modul Zustand fest. In seinem destrukturtor stellt diese Klasse den in der Member-Variable gespeicherten Zeiger als effektiven Modul Zustand wieder her.

Wenn Sie über eine exportierte Funktion verfügen, z. b. eine, die ein Dialogfeld in der dll startet, müssen Sie am Anfang der Funktion den folgenden Code hinzufügen:

[!code-cpp[NVC_MFCConnectionPoints#6](codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

Dadurch wird der aktuelle Modul Zustand mit dem von [afxgetstaticmodulestate](reference/extension-dll-macros.md#afxgetstaticmodulestate) zurückgegebenen Zustand bis zum Ende des aktuellen Bereichs vertauscht.

Probleme mit Ressourcen in DLLs treten auf, wenn das `AFX_MANAGE_STATE` Makro nicht verwendet wird. Standardmäßig verwendet MFC das Ressourcen Handle der Hauptanwendung, um die Ressourcen Vorlage zu laden. Diese Vorlage wird tatsächlich in der dll gespeichert. Die Ursache hierfür ist, dass die Modul Zustandsinformationen von MFC nicht durch das Makro gewechselt wurden `AFX_MANAGE_STATE` . Das Ressourcen Handle wird aus dem Modul Zustand von MFC wieder hergestellt. Wenn Sie den Modulstatus nicht wechseln, wird das falsche Ressourcen Handle verwendet.

`AFX_MANAGE_STATE`muss nicht in jede Funktion in der DLL eingefügt werden. Beispielsweise `InitInstance` kann vom MFC-Code in der Anwendung aufgerufen werden, ohne dass `AFX_MANAGE_STATE` MFC den Modul Zustand automatisch vor verschiebt `InitInstance` und dann nach der Rückgabe von zurück wechselt `InitInstance` . Das gleiche gilt für alle Meldungs Zuordnungs Handler. Reguläre MFC-DLLs verfügen tatsächlich über eine spezielle Master Fenster Prozedur, mit der der Modul Zustand vor dem Weiterleiten von Nachrichten automatisch gewechselt wird.

## <a name="see-also"></a>Siehe auch

[Verwalten der Statusdaten von MFC-Modulen](managing-the-state-data-of-mfc-modules.md)
