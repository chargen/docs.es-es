---
title: '&lt;typeparamref&gt; (Guía de programación de C#)'
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 36e5a8998018839214da00287a2bf8dc2c5925a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="lttypeparamrefgt-c-programming-guide"></a>&lt;typeparamref&gt; (Guía de programación de C#)
## <a name="syntax"></a>Sintaxis  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `name`  
 El nombre del parámetro de tipo. Ponga el nombre entre comillas dobles (" ").  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre los parámetros de tipo en métodos y tipos genéricos, vea [Genéricos](../../../csharp/programming-guide/generics/index.md).  
  
 Use esta etiqueta para permitir que los consumidores del archivo de documentación den formato a la palabra de alguna manera distinta, por ejemplo en cursiva.  
  
 Compile con [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para procesar los comentarios de documentación a un archivo.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
 [Etiquetas recomendadas para los comentarios de documentación](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
