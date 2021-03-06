---
title: 'Cómo: Transformar la escala de un modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 3cca1a210a7dbe410ebaacaaf89c08de8c31c40e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a>Cómo: Transformar la escala de un modelo 3D
Este ejemplo muestra cómo escalar un objeto 3D. Para escalar un objeto 3D, use un <xref:System.Windows.Media.Media3D.ScaleTransform3D>. El <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, y <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> propiedades cambiar tamaño del elemento según el factor especificado. Por ejemplo, un <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> valor de 1,5 expande un objeto al 150 por ciento de su ancho original. Un <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> valor de 0,5 reduce el alto de un objeto a 50 por ciento. El código siguiente muestra cómo utilizar un <xref:System.Windows.Media.Media3D.ScaleTransform3D> como la transformación de un <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra el ejemplo completo.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Vea también  
 [Animar traslaciones 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)  
 [Crear una escena 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Información general sobre gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
