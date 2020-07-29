---
title: Compilerfehler C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: c92a95b97cb4c57d3ad5cfbf8fe1d9980d5362cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221210"
---
# <a name="compiler-error-c2338"></a>Compilerfehler C2338

> *Fehlermeldung*

Dieser Fehler kann durch einen **`static_assert`** Fehler bei der Kompilierung verursacht werden. Die Meldung wird von den **`static_assert`** Parametern bereitgestellt.

Diese Fehlermeldung kann auch von externen Anbietern an den Compiler generiert werden. In den meisten Fällen werden diese Fehler von einer Attribut Anbieter-DLL (z. b. atlprov) gemeldet. Zu den allgemeinen Formen dieser Nachricht gehören:

- '*Attribut*' ATL-Attribut Anbieter: Fehler *Meldung* ATL-*Nummer*

- Falsche Verwendung des Attributs "*Attribute*".

- "*Usage*": falsches Format für das Attribut "Usage"

Diese Fehler sind oft nicht wiederherstellbar, und es folgt ein schwerwiegender Compilerfehler.

Korrigieren Sie die Attribut Verwendung, um diese Probleme zu beheben. In einigen Fällen müssen Attribut Parameter beispielsweise deklariert werden, bevor Sie verwendet werden können. Wenn eine ATL-Fehlernummer angegeben wird, finden Sie in der Dokumentation zu diesem Fehler Weitere Informationen.
