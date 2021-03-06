---
title: Elemento &lt;security&gt; de &lt;netTcpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f58dd0ee1b00785e82628e5442c736866ffe7db5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a>Elemento &lt;security&gt; de &lt;netTcpBinding&gt;
Define la configuración de seguridad de un enlace.  
  
 \<system.ServiceModel>  
\<enlaces >  
\<netTcpBinding >  
\<enlace >  
\<seguridad >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|modo|Opcional. Especifica el tipo de seguridad que se aplica. Se muestran los valores válidos a continuación. El valor predeterminado es `Transport`.<br /><br /> Este atributo es del tipo <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Atributo de modo  
  
|Valor|Descripción|  
|-----------|-----------------|  
|Ninguna|La seguridad está deshabilitada.|  
|Transporte|La seguridad de transporte se proporciona utilizando TLS sobre TCP o SPNego. El servicio puede necesitar ser configurado con certificados SSL. Es posible controlar el nivel de protección con este modo.|  
|Mensaje|La seguridad se proporciona mediante la seguridad del mensaje SOAP. De forma predeterminada, el cuerpo SOAP se cifra y firma. Este modo proporciona una variedad de características, como si las credenciales del servicio están disponibles para el cliente fuera de la banda, el conjunto de algoritmos que se utiliza y qué nivel de protección se aplica al cuerpo del mensaje. Se realiza la autenticación del cliente una vez por sesión y los resultados de autenticación están almacenados en memoria caché durante la duración de la sesión.|  
|TransportWithMessageCredential|La seguridad de transporte va unida a la seguridad del mensaje. TLS proporciona la seguridad de transporte sobre TCP o SPNego y asegura la integridad, confidencialidad y autenticación de servidor. La seguridad del mensaje SOAP proporciona la autenticación del cliente. De manera predeterminada, se realiza la autenticación del cliente una vez por sesión y los resultados de autenticación están almacenados en la memoria caché durante la duración de la sesión.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|Define la configuración de seguridad para el transporte. Este elemento es del tipo <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<mensaje >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|Define la configuración de seguridad del mensaje. Este elemento es del tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|enlace|El elemento de enlace de la [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Comentarios  
 Cada uno de los enlaces estándar proporciona los parámetros para controlar los requisitos de seguridad de la transferencia. Estos parámetros incluyen normalmente el modo de seguridad que especificó si se usó la seguridad del nivel de mensaje o del nivel de transporte y la elección del tipo de credencial del cliente. Basada en la elección de opciones que estos parámetros presentan, se construirá una pila de canal con la seguridad adecuada.  
  
 Los enlaces proporcionados por el sistema suministrados por Windows Communication Foundation (WCF) son un conjunto diseñado para cumplir algunos de los requisitos de escenario más comunes. Cada uno de estos enlaces permite la especificación de requisitos de seguridad para algunos escenarios concretos.  
  
 Este elemento de configuración proporciona especificaciones de seguridad para `netTcpBinding`. Se trata de un enlace seguro, confiable y optimizado adecuado para la comunicación entre equipos. De forma predeterminada, genera una pila de comunicación en tiempo de ejecución que admite TCP para la entrega del mensaje y Seguridad de Windows para la seguridad y autenticación del mensaje, WS-ReliableMessaging para la confiabilidad, y la codificación binaria del mensaje.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Protección de servicios y clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Enlaces](../../../../../docs/framework/wcf/bindings.md)  
 [Configuración de enlaces proporcionados por el sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilización de enlaces para configurar los clientes y servicios de Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<enlace >](../../../../../docs/framework/misc/binding.md)
