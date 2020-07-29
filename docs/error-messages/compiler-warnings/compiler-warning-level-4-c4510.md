---
title: Compilerwarnung (Stufe 4) C4510
description: Compilerwarnung C4510 Beschreibung und Projekt Mappe.
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: e4bb688266d9fe638978d2d3fa2666b83b3e6cc9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225253"
---
# <a name="compiler-warning-level-4-c4510"></a>Compilerwarnung (Stufe 4) C4510

> "*Klasse*": Standardkonstruktor konnte nicht generiert werden.

Der Compiler kann keinen Standardkonstruktor für die angegebene Klasse generieren, die über keine benutzerdefinierten Konstruktoren verfügt. Objekte dieses Typs können nicht erstellt werden.

Es gibt mehrere Situationen, in denen verhindert wird, dass der Compiler einen Standardkonstruktor erzeugt, einschließlich:

- Ein **`const`** Datenmember.

- Ein Datenmember, der ein Verweis ist.

Um dieses Problem zu beheben, erstellen Sie einen benutzerdefinierten Standardkonstruktor für die Klasse, die diese Member initialisiert.
