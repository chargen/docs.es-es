---
title: Funciones definidas por el usuario (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: a3c9cda162e77517d480d9e48eb80fa62dd1c161
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="user-defined-functions-entity-sql"></a>Funciones definidas por el usuario (Entity SQL)
Entity SQL admite llamadas a funciones definidas por el usuario en una consulta. Puede definir estas funciones alineadas con la consulta (vea [Cómo: llamar a una función definida por el usuario](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) o como parte del modelo conceptual (vea [Cómo: definir funciones personalizadas en el modelo Conceptual](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Funciones del modelo conceptual se definen como un comando de Entity SQL en el [DefiningExpression](http://msdn.microsoft.com/library/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) elemento de un [función](http://msdn.microsoft.com/library/dc3beca7-55cf-4977-8db0-5064cdbab134) elemento en el modelo conceptual.  
  
 Entity SQL le permite definir las funciones en el propio comando de consulta. El [función](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operador define las funciones inline. Puede definir varias funciones con el mismo nombre en un único comando, siempre que sus firmas sean únicas. Para obtener más información, consulta [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
