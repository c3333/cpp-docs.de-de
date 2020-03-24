---
title: 'Ressourcencompiler: Fehler RC2001'
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: 35042687b798b53857becdedba57861bd4f41a05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191721"
---
# <a name="resource-compiler-error-rc2001"></a>Ressourcencompiler: Fehler RC2001

Zeilen-Zeilen Ausdruck in konstanter Konstante

Eine Zeichen folgen Konstante wurde in einer zweiten Zeile ohne einen umgekehrten Schrägstrich ( **\\** ) oder schließende und öffnende doppelte Anführungszeichen ( **"** ) fortgesetzt.

Führen Sie einen der folgenden Schritte aus, um eine Zeichen folgen Konstante, die sich in zwei Zeilen in der Quelldatei befindet, zu unterbrechen:

- Beenden Sie die erste Zeile mit dem Zeilen Fortsetzungs Zeichen, einem umgekehrten Schrägstrich.

- Schließen Sie die Zeichenfolge in der ersten Zeile mit einem doppelten Anführungszeichen, und öffnen Sie die Zeichenfolge in der nächsten Zeile mit einem weiteren Anführungszeichen.

Das Beenden der ersten Zeile mit \n, der Escapesequenz zum Einbetten eines Zeilen Vorzeichens in eine Zeichen folgen Konstante ist nicht ausreichend.
