---
title: Speicherklassenspezifizierer "register"
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 513213222ee2c598455709a0891977a0949c8555
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229557"
---
# <a name="register-storage-class-specifier"></a>Speicherklassenspezifizierer "register"

**Microsoft-spezifisch**

Der Microsoft C/C++-Compiler berücksichtigt keine Benutzeranforderungen für Registervariablen. Aus Gründen der Portabilität wird jedoch jede andere Semantik, die dem **`register`** -Schlüsselwort zugeordnet ist, vom Compiler berücksichtigt. Sie können z. B. weder den unären address-of-Operator ( **&** ) auf ein register-Objekt anwenden noch das **`register`** -Schlüsselwort für Arrays verwenden.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Speicherklassenspezifizierer für Deklarationen der internen Ebene](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
