---
title: 'Cómo: Asignar una matriz a otra (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Cómo: Asignar una matriz a otra (Visual Basic)
Dado que las matrices son objetos, se puede usar en instrucciones de asignación como otros tipos de objeto. Una variable de matriz contiene un puntero a los datos que constituyen los elementos de matriz y la información de rango y longitud, y una asignación de copia solo this (puntero).  
  
### <a name="to-assign-one-array-to-another-array"></a>Para asignar una matriz a otra  
  
1.  Asegúrese de que las dos matrices tienen el mismo rango (número de dimensiones) y tipos de datos de elementos compatibles.  
  
2.  Utilice una instrucción de asignación estándar para asignar la matriz de origen a la matriz de destino. No siga cualquier nombre de matriz con paréntesis.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Al asignar una matriz a otra, se aplican las reglas siguientes:  
  
-   **Rangos iguales.** El rango (número de dimensiones) de la matriz de destino debe ser el mismo que el de la matriz de origen.  
  
     Siempre que los rangos de las dos matrices son iguales, las dimensiones no es necesario que son iguales. Puede cambiar el número de elementos de una dimensión determinada durante la asignación.  
  
-   **Tipos de elemento.** Cualquier ambas matrices deben tener *tipo de referencia* elementos o ambas matrices deben tener *tipo de valor* elementos. Para obtener más información, consulte [tipos de valor y tipos de referencia](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Si ambas matrices tienen elementos de tipo de valor, los tipos de elemento de datos deben ser exactamente el mismo. La única excepción a esto es que puede asignar una matriz de `Enum` elementos en una matriz del tipo base del que `Enum`.  
  
    -   Si ambas matrices tienen referencia de elementos de tipo, el tipo de elemento de origen debe derivar del tipo de elemento de destino. Cuando esto ocurre, las dos matrices tienen la misma relación de herencia que sus elementos. Esto se denomina *covarianza de matrices*.  
  
 El compilador informa de un error si se infringen las reglas anteriores, por ejemplo, si los tipos de datos no son compatibles o si los rangos no son iguales. Puede agregar al código para asegurarse de que las matrices son compatibles antes de intentar realizar la asignación de control de errores. También puede usar el [TryCast (operador)](../../../../visual-basic/language-reference/operators/trycast-operator.md) palabra clave si desea evitar que se produzca una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Matrices](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Solución de problemas de matrices](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Enum (instrucción)](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Conversiones de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
