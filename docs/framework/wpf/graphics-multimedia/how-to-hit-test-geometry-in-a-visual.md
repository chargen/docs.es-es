---
title: 'Cómo: Geometría de una prueba de seguimiento en un objeto visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 26e0119ee82646f466c3567881bf33350fe59d17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Cómo: Geometría de una prueba de seguimiento en un objeto visual
Este ejemplo muestra cómo realizar una prueba de posicionamiento en un objeto visual que se compone de uno o varios <xref:System.Windows.Media.Geometry> objetos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar el <xref:System.Windows.Media.DrawingGroup> desde un objeto visual que usa el <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> método. A continuación, se realiza una prueba de posicionamiento en el contenido representado de cada dibujo el <xref:System.Windows.Media.DrawingGroup> para determinar qué geometría se obtuvo acceso.  
  
> [!NOTE]
>  En la mayoría de los casos, se utilizaría la <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método para determinar si un punto forma una intersección con el contenido representado de un objeto visual.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 El <xref:System.Windows.Media.Geometry.FillContains%2A> método es un método sobrecargado que permite realizar pruebas de posicionamiento mediante el uso de un determinado <xref:System.Windows.Point> o <xref:System.Windows.Media.Geometry>. Si se traza una geometría, el trazo puede extenderse fuera del límite del relleno. En este caso, puede que desee llamar a <xref:System.Windows.Media.Geometry.StrokeContains%2A> además <xref:System.Windows.Media.Geometry.FillContains%2A>.  
  
 También puede proporcionar un <xref:System.Windows.Media.ToleranceType> que se usa para los propósitos de reducción de Bézier.  
  
> [!NOTE]
>  Esta muestra no tiene en cuenta ninguna transformación o recorte que pueda aplicarse a la geometría. Además, este ejemplo no funcionará con un control con estilo, puesto que no tiene los dibujos asociados a él.  
  
## <a name="see-also"></a>Vea también  
 [Realizar pruebas de posicionamiento en la capa visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Realizar una prueba de posicionamiento usando Geometry como parámetro](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
