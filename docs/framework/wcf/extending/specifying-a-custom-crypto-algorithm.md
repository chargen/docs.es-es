---
title: Especificar un algoritmo criptográfico personalizado
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: d8fb22daac66c3ef80f148db03703fc5024d3438
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Especificar un algoritmo criptográfico personalizado
WCF permite especificar un algoritmo criptográfico personalizado para usarlo cuando se cifren datos o se calculen firmas digitales. Para ello, se siguen estos pasos:  
  
1.  Derivar una clase de la clase <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.  
  
2.  Registrar el algoritmo  
  
3.  Configurar el enlace con la clase derivada de la clase <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Derivar una clase de SecurityAlgorithmSuite  
 La clase <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> es una clase base abstracta derivada que permite especificar el algoritmo que se va a usar cuando se realicen distintas operaciones relacionadas con la seguridad. Por ejemplo, calcular un hash para una firma digital o cifrar un mensaje. En el código siguientes se muestra cómo derivar una clase de la clase <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a>Registrar el algoritmo personalizado  
 El registro se puede realizar en un archivo de configuración o en código imperativo. El registro de un algoritmo personalizado se lleva a cabo mediante la creación de una asignación entre una clase que implemente un proveedor de servicios criptográficos y un alias. A continuación, el alias se asigna a un URI que se usa cuando se especifica el algoritmo en el enlace del servicio WCF. En el siguiente fragmento de código de configuración se muestra cómo registrar un algoritmo personalizado en config:  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 La sección en la <`cryptoClasses`> elemento crea la asignación entre el SHA256CryptoServiceProvider y el alias "SHA256CSP". El <`nameEntry`> elemento crea la asignación entre el alias "SHA256CSP" y la dirección URL especificada (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).  
  
 Use el método <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> para registrar el algoritmo personalizado en código. Este método crea ambas asignaciones. En el ejemplo siguiente se muestra cómo llamar a este método:  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Configurar el enlace  
 Configure el enlace especificando la clase derivada de la clase <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> personalizada en la configuración del enlace como se muestra en el siguiente fragmento de código:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Para obtener un ejemplo de código completo, vea el [agilidad criptográfica en la seguridad de WCF](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [Protección de servicios y clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Seguridad de servicios](../../../../docs/framework/wcf/securing-services.md)  
 [Información general sobre seguridad](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Conceptos de seguridad](../../../../docs/framework/wcf/feature-details/security-concepts.md)
