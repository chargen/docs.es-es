---
title: Cómo deshabilitar el cifrado de firmas digitales
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 074a32f6a69f8353568e76c99f4b65aece813f55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Cómo deshabilitar el cifrado de firmas digitales
De forma predeterminada, un mensaje se firma y la firma se cifra digitalmente. Esto se controla mediante la creación de un enlace personalizado con una instancia de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> o el <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, y estableciendo la propiedad `MessageProtectionOrder` de cualquier clase en un valor de enumeración <xref:System.ServiceModel.Security.MessageProtectionOrder>. De manera predeterminada, es <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Este proceso utiliza hasta un 30 por ciento más de tiempo que si, simplemente, se firma y cifra el mensaje en base a su tamaño total (cuanto más pequeño es el mensaje, mayor es el impacto en el rendimiento). No obstante, deshabilitar el cifrado de la firma puede permitir a un atacante suponer el contenido del mensaje. Esto es posible porque el elemento de firma contiene el código hash del texto sin formato de cada parte del mensaje firmada. Por ejemplo, aunque el cuerpo del mensaje se cifra de forma predeterminada, la firma no cifrada contiene el código hash del cuerpo del mensaje antes del cifrado. Si el conjunto de valores posibles para la parte firmada y cifrada es pequeño, un atacante podría ser capaz de deducir el contenido examinando el valor hash. El cifrado de la firma mitiga este vector de ataque.  
  
 Por lo tanto, deshabilite el cifrado de la firma solo cuando el valor del contenido es bajo, o el conjunto de posibles valores de contenido es grande y no determinista, y el beneficio para el rendimiento es más importante que mitigar el ataque descrito anteriormente.  
  
> [!NOTE]
>  Si no hay nada cifrado en el mensaje, el elemento de firma no se cifra, incluso si la propiedad <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> está establecida en <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Este comportamiento se produce incluso con enlaces proporcionados por el sistema; todos los enlaces proporcionados por el sistema tienen el orden de protección de mensaje establecido en `SignBeforeEncryptAndEncryptSignature`. Sin embargo, el lenguaje de descripción de Web servicios WCF (WSDL) genera, seguirá conteniendo el `<sp:EncryptSignature>` aserción.  
  
### <a name="to-disable-digital-signing"></a>Para deshabilitar la firma digital  
  
1.  Creará un control <xref:System.ServiceModel.Channels.CustomBinding>. Para obtener más información, consulte [Cómo: crear un personalizado de enlace con SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Agregue <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a la colección de enlaces.  
  
3.  Establezca la propiedad <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> en <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> o establezca la propiedad <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> en <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Vea también  
 [Funcionalidades de seguridad con enlaces personalizados](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
