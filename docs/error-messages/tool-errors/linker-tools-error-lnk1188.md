---
title: Linkertoolfehler LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: b18a93c7434ee3d66f42829f373bd916a65369bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195174"
---
# <a name="linker-tools-error-lnk1188"></a>Linkertoolfehler LNK1188

Badfixupsection:: Ungültiges fixupziel ' Symbol '; möglicher Abschnitt mit einer Länge von NULL

Bei einem VxD-Link hat das Ziel einer Verlagerung keinen Abschnitt. Mit LINK386 (eine ältere Version) kann ein OMF-Gruppendaten Satz (generiert durch eine MASM-Gruppen Direktive) verwendet werden, um den Abschnitt mit der Länge 0 (null) mit einem anderen Abschnitt ungleich 0 (null) zu kombinieren. Das COFF-Format unterstützt die Gruppen Direktive und die Abschnitte mit der Länge Null nicht. Wenn der Link diesen Typ von OMF-Objekten automatisch in COFF konvertiert, kann dieser Fehler auftreten.
