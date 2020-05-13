---
title: Speicherklassenspezifizierer "register"
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 0fac6db2254a909d0ec558a7e76f7ccf32aa7ac3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325246"
---
# <a name="register-storage-class-specifier"></a>Speicherklassenspezifizierer "register"

**Microsoft-spezifisch**

Der Microsoft C/C++-Compiler berücksichtigt keine Benutzeranforderungen für Registervariablen. Aus Gründen der Portabilität wird jedoch jede andere Semantik, die dem **register**-Schlüsselwort zugeordnet ist, vom Compiler berücksichtigt. Sie können z.B. weder den unären Operator „address-of“ ( **&** ) auf ein register-Objekt anwenden, noch kann das **register**-Schlüsselwort für Arrays verwendet werden.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Speicherklassenspezifizierer für Deklarationen der internen Ebene](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
