---
title: Información general sobre ContextMenu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: e862f02e736cb8507dde5036700d751f8af0a226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="contextmenu-overview"></a>Información general sobre ContextMenu
El <xref:System.Windows.Controls.ContextMenu> clase representa el elemento que expone la funcionalidad mediante el uso de un determinado contexto <xref:System.Windows.Controls.Menu>. Normalmente, un usuario expone el <xref:System.Windows.Controls.ContextMenu> en el [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] haciendo clic en el botón del mouse. Este tema se presentan los <xref:System.Windows.Controls.ContextMenu> elemento y proporciona ejemplos de cómo se usa en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] y el código.  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>Control ContextMenu  
 Un <xref:System.Windows.Controls.ContextMenu> se adjunta a un control específico. El <xref:System.Windows.Controls.ContextMenu> elemento le permite presentar a los usuarios con una lista de elementos que especifican comandos u opciones que están asociados a un control determinado, por ejemplo, un <xref:System.Windows.Controls.Button>. Los usuarios hacen clic con el botón derecho en el control para que aparezca el menú. Normalmente, al hacer clic en un <xref:System.Windows.Controls.MenuItem> abre un submenú o hace que una aplicación para llevar a cabo un comando.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Creación de elementos ContextMenu  
 Los ejemplos siguientes muestran cómo crear un <xref:System.Windows.Controls.ContextMenu> con submenús. El <xref:System.Windows.Controls.ContextMenu> controles están asociados a los controles de botón.  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Aplicación de estilos a un control ContextMenu  
 Mediante el uso de un control <xref:System.Windows.Style>, puede cambiar considerablemente la apariencia y el comportamiento de un <xref:System.Windows.Controls.ContextMenu> sin necesidad de escribir un control personalizado. Además de establecer propiedades visuales, también puede aplicar estilos a las partes de un control. Por ejemplo, puede cambiar el comportamiento de los elementos del control mediante propiedades, o puede agregar partes a, o cambiar el diseño de, un <xref:System.Windows.Controls.ContextMenu>. Los ejemplos siguientes muestran varias maneras de agregar estilos para <xref:System.Windows.Controls.ContextMenu> controles.  
  
 En el primer ejemplo se define un estilo denominado `SimpleSysResources`, que muestra cómo usar la configuración actual del sistema en el estilo. El ejemplo se asigna <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> como el <xref:System.Windows.Controls.Control.Background%2A> color y <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> como el <xref:System.Windows.Controls.Control.Foreground%2A> color de la <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 En el ejemplo siguiente se usa el <xref:System.Windows.Trigger> elemento que se va a cambiar la apariencia de un <xref:System.Windows.Controls.Menu> en respuesta a eventos que se producen en el <xref:System.Windows.Controls.ContextMenu>. Cuando un usuario mueve el mouse sobre el menú, el aspecto de los <xref:System.Windows.Controls.ContextMenu> cambios de elementos.  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [ContextMenu Styles and Templates](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md) (Estilos y plantillas de ContextMenu)  
 [WPF Controls Gallery Sample](http://go.microsoft.com/fwlink/?LinkID=160053) (Ejemplo de galería de controles de WPF)
