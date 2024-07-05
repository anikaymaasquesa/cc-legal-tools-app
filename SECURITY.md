# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

## Reporting a Vulnerability

Use this section to tell people how to report a vulnerability.

Tell them where to go, how often they can expect to get an update on a
reported vulnerability, what to expect if the vulnerability is accepted or
declined, etc.






Grupo de trabajo de ingeniería de Internet (IETF) K. Moriarty, Ed.
Solicitud de comentarios: 8017 EMC Corporation
Obsoletos: 3447 B. Kaliski
Categoría: Informativo Verisign
ISSN: 2070-1721 J. Jonsson
                                                               Subconjunto AB
                                                                A. Rusch
                                                                     Sociedad Anónima
                                                           Noviembre de 2016


          PKCS #1: Especificaciones de criptografía RSA versión 2.2

Abstracto

   Este documento proporciona recomendaciones para la implementación de
   criptografía de clave pública basada en el algoritmo RSA, que abarca
   primitivas criptográficas, esquemas de cifrado, esquemas de firma con
   apéndice y sintaxis ASN.1 para representar claves y para identificar
   los esquemas.

   Este documento representa una republicación de PKCS #1 v2.2 de RSA
   Serie de estándares de criptografía de clave pública (PKCS) de los laboratorios.
   Al publicar este RFC, el control de cambios se transfiere al IETF.

   Este documento también deja obsoleto el RFC 3447.

Estado de este memorando

   Este documento no es una especificación de Internet Standards Track; es
   publicado con fines informativos.

   Este documento es un producto del Grupo de trabajo de ingeniería de Internet
   (IETF). Representa el consenso de la comunidad IETF. Tiene
   recibió revisión pública y ha sido aprobado para su publicación por la
   Grupo de dirección de ingeniería de Internet (IESG). No todos los documentos
   aprobados por el IESG son candidatos para cualquier nivel de Internet
   Estándar; consulte la Sección 2 del RFC 7841.

   Información sobre el estado actual de este documento, cualquier errata,
   y cómo proporcionar retroalimentación al respecto se puede obtener en
   http://www.rfc-editor.org/info/rfc8017.









Moriarty, et al. Informativo [Página 1]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


Aviso de copyright

   Copyright (c) 2016 IETF Trust y las personas identificadas como
   Autores del documento. Todos los derechos reservados.

   Este documento está sujeto a BCP 78 y al Fideicomiso Legal de IETF.
   Disposiciones relativas a los documentos del IETF
   (http://trustee.ietf.org/license-info) vigente en la fecha de
   publicación de este documento. Por favor revise estos documentos
   con cuidado, ya que describen sus derechos y restricciones con respecto
   a este documento. Los componentes de código extraídos de este documento deben
   incluir el texto de la Licencia BSD Simplificada como se describe en la Sección 4.e de
   las Disposiciones Legales del Fideicomiso y se proporcionan sin garantía como
   descrito en la Licencia BSD Simplificada.





































Moriarty, et al. Informativo [Página 2]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


Tabla de contenido

   1. Introducción . ...
     1.1. Requisitos Idioma . ...
   2. Notación . ...
   3. Tipos de claves . ...
     3.1. Clave pública RSA . ...
     3.2. Clave privada RSA . . . . . . . . . . . . . . . . . . . . . . . 9
   4. Primitivas de conversión de datos . . . . . . . . . . . . . . . . . 11
     4.1. Sistema operativo: OSP. . . . . . . . . . . . . . . . . . . . . . . . . . 11
     4.2. OS2IP . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 12
   5. Primitivas criptográficas . . . . . . . . . . . . . . . . . . 12
     5.1. Primitivas de cifrado y descifrado . . . . . . . . . . 12
       5.1.1. RSAEP . ...
       5.1.2. RSADP . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13
     5.2. Primitivas de firma y verificación . . . . . . . . . . 15
       5.2.1. RSASP1 . . . . . . . . . . . . . . . . . . . . . . . 15
       5.2.2. RSAVP1 . . . . . . . . . . . . . . . . . . . . . . . . . 16
   6. Descripción general de los esquemas . . . . . . . . . . . . . . . . . . . . . . . 17
   7. Esquemas de cifrado . . . . . . . . . . . . . . . . . . . . . . 18
     7.1. RSAES-OAEP . ...
       7.1.1. Operación de cifrado . . . . . . . . . . . . . . . . . 22
       7.1.2. Operación de descifrado . . . . . . . . . . . . . . . . 25
     7.2. RSAES-PKCS1-v1_5 . . . . . . . . . . . . . . . . . . . . . . 27
       7.2.1. Operación de cifrado . . . . . . . . . . . . . . . . . 28
       7.2.2. Operación de descifrado . . . . . . . . . . . . . . . . 29
   8. Esquema de firma con apéndice . . . . . . . . . . . . . . . . 31
     8.1. RSASSA-PSS . ...
       8.1.1. Operación de generación de firma . . . . . . . . . . . 33
       8.1.2. Operación de verificación de firma . . . . . . . . . . 34
     8.2. Código RSASSA-PKCS1-v1_5 . . . . . . . . . . . . . . . . . . . . 35
       8.2.1. Operación de generación de firma . . . . . . . . . . . 36
       8.2.2. Operación de verificación de firma . . . . . . . . . . 37
   9. Métodos de codificación para firmas con apéndice . . . . . . . . 39
     9.1. AESM-PSS . ...
       9.1.1. Operación de codificación . . . . . . . . . . . . . . . . . . . 42
       9.1.2. Operación de verificación . . . . . . . . . . . . . . . . 44
     9.2. EMSA-PKCS1-v1_5 . ...
   10. Consideraciones de seguridad . ...
   11. Referencias . ...
     11.1 Referencias normativas . ...
     11.2. Referencias informativas . ...









Moriarty, et al. Informativo [Página 3]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Apéndice A. Sintaxis ASN.1 . ...
     A.1. Representación de claves RSA . . . . . . . . . . . . . . . . . . 54
       A.1.1. Sintaxis de clave pública RSA . . . . . . . . . . . . . . . . . 54
       A.1.2. Sintaxis de clave privada RSA . . . . . . . . . . . . . . . . 55
     A.2. Identificación del esquema . ...
       A.2.1. RSAES-OAEP . . . . . . . . . . . . . . . . . . . . . . . . 57
       A.2.2. RSAES-PKCS-v1_5 . ...
       A.2.3. RSASSA-PSS . ...
       A.2.4. RSASSA-PKCS-v1_5 . . . . . . . . . . . . . . . . . . . . . 62
   Apéndice B. Técnicas de apoyo . . . . . . . . . . . . . . . 63
     B.1. Funciones hash . . . . . . . . . . . . . . . . . . . . . . . 63
     B.2. Funciones de generación de máscaras . . . . . . . . . . . . . . . . . 66
       B.2.1. MGF1 . ...
   Apéndice C. Módulo ASN.1 . ...
   Apéndice D. Historial de revisiones de PKCS #1 . . . . . . . . . . . . . 76
   Apéndice E. Acerca de PKCS . ...
   Agradecimientos . ...
   Direcciones de los autores . ...

1. Introducción

   Este documento proporciona recomendaciones para la implementación de
   criptografía de clave pública basada en el algoritmo RSA [RSA], que abarca
   los siguientes aspectos:

   o Primitivas criptográficas

   o Esquemas de cifrado

   o Esquemas de firma con apéndice

   o Sintaxis ASN.1 para representar claves y para identificar los esquemas

   Las recomendaciones están destinadas a una aplicación general dentro de
   sistemas informáticos y de comunicaciones y, como tales, incluyen una buena cantidad
   de flexibilidad. Se espera que los estándares de aplicación basados ​​en
   Estas especificaciones pueden incluir restricciones adicionales.
   Las recomendaciones están pensadas para ser compatibles con los estándares IEEE.
   1363 [IEEE1363], IEEE 1363a [IEEE1363A] y ANSI X9.44 [ANSIX944].

   Este documento reemplaza a PKCS #1 versión 2.1 [RFC3447] pero incluye
   Técnicas compatibles.

   La organización de este documento es la siguiente:

   o La sección 1 es una introducción.

   o La Sección 2 define algunas notaciones utilizadas en este documento.



Moriarty, et al. Informativo [Página 4]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   o La sección 3 define los tipos de claves públicas y privadas RSA.

   o Las secciones 4 y 5 definen varias primitivas o ecuaciones matemáticas básicas.
      operaciones. Las primitivas de conversión de datos se encuentran en la Sección 4 y
      primitivas criptográficas (cifrado-descifrado y firma-
      verificación) se encuentran en la Sección 5.

   o Las secciones 6, 7 y 8 tratan del cifrado y la firma.
      esquemas en este documento. La sección 6 ofrece una descripción general.
      con los métodos que se encuentran en PKCS #1 v1.5, la Sección 7 define un
      Esquema de cifrado basado en relleno de cifrado asimétrico óptimo
      (OAEP) [OAEP], y la Sección 8 define un esquema de firma con
      Apéndice basado en el Esquema de Firma Probabilística (PSS)
      [RSARABINA] [PSS].

   o La sección 9 define los métodos de codificación para los esquemas de firma.
      en la Sección 8.

   o El Apéndice A define la sintaxis ASN.1 para las claves definidas en
      Sección 3 y los esquemas de las Secciones 7 y 8.

   o El Apéndice B define las funciones hash y la generación de máscaras.
      función (MGF) utilizada en este documento, incluida la sintaxis ASN.1 para
      Las técnicas.

   o El Apéndice C proporciona un módulo ASN.1.

   o Los apéndices D y E describen el historial de revisión de PKCS #1 y
      Proporcionar información general sobre la criptografía de clave pública.
      Normas.

   Este documento representa una republicación de PKCS #1 v2.2 [PKCS1_22]
   de los estándares de criptografía de clave pública (PKCS) de RSA Laboratories
   serie.

1.1 Requisitos Idioma

   Las palabras clave "DEBE", "NO DEBE", "REQUERIDO", "DEBERÁ", "NO DEBERÁ",
   "DEBERÍA", "NO DEBERÍA", "RECOMENDADO", "PUEDE" y "OPCIONAL" en este
   Los documentos deben interpretarse como se describe en [RFC2119].











Moriarty, et al. Informativo [Página 5]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


2. Notación

   La notación en este documento incluye:

      c representante del texto cifrado, un número entero entre 0 y
                     número uno

      Texto cifrado C, una cadena de octetos

      d exponente privado RSA

      d_i factor adicional exponente CRT de r_i,
                     un entero positivo tal que

                       e * d_i == 1 (mod (r_i-1)), i = 3, ..., u

      dP exponente CRT de p, un entero positivo tal que

                       e * dP == 1 (mód (p-1))

      dQ exponente CRT de q, un entero positivo tal que

                       e * dQ == 1 (mód (q-1))

      y exponente público de RSA

      Mensaje codificado EM, una cadena de octetos

      emBits (previsto) longitud en bits de un mensaje codificado EM

      emLen (prevista) longitud en octetos de un mensaje codificado
                     En

      MCD(. , .) máximo común divisor de dos números enteros no negativos

      Función hash

      hLen longitud de salida en octetos de la función hash Hash

      k longitud en octetos del módulo RSA n

      Clave privada K RSA

      L etiqueta RSAES-OAEP opcional, una cadena de octetos

      MCM(., ..., .) mínimo común múltiplo de una lista de números no negativos
                     números enteros




Moriarty, et al. Informativo [Página 6]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      m representante del mensaje, un número entero entre 0 y
                     número uno

      Mensaje M, una cadena de octetos

      máscara de salida MGF, una cadena de octetos

      maskLen (prevista) longitud de la máscara de cadena de octetos

      Función de generación de máscara MGF

      mgfSeed semilla a partir de la cual se genera la máscara, una cadena de octetos

      mLen longitud en octetos de un mensaje M

      n módulo RSA, n = r_1 * r_2 * ... * r_u , u >= 2

      (n, e) Clave pública RSA

      p, q primeros dos factores primos del módulo RSA n

      qInv Coeficiente CRT, un entero positivo menor que
                     p tal que q * qInv == 1 (mod p)

      r_i factores primos del módulo RSA n, incluyendo
                     r_1 = p, r_2 = q y factores adicionales si los hay

      s representante de la firma, un número entero entre 0 y
                     número uno

      Firma S, una cadena de octetos

      Longitud sLen en octetos de la sal EMSA-PSS

      t_i factor primo adicional coeficiente CRT de r_i, a
                     entero positivo menor que r_i tal que

                       r_1 * r_2 * ... * r_(i-1) * t_i == 1 (mod r_i) ,

                     yo = 3, ... , u

      u número de factores primos del módulo RSA, u >= 2

      xa entero no negativo

      X una cadena de octetos correspondiente a x

      xLen (longitud prevista) de la cadena de octetos X



Moriarty, et al. Informativo [Página 7]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      Indicador 0x de representación hexadecimal de un octeto
                     o una cadena de octetos: "0x48" denota el octeto con
                     valor hexadecimal 48; "(0x)48 09 0e" denota el
                     cadena de tres octetos consecutivos con hexadecimal
                     valores 48, 09 y 0e, respectivamente

      \lambda(n) MCM(r_1-1, r_2-1, ... , r_u-1)

      \xor operación exclusiva-or bit a bit de dos cadenas de octetos

      Función techo \ceil(.); \ceil(x) es el entero más pequeño
                     mayor o igual que el número real x

      || operador de concatenación

      == símbolo de congruencia; a == b (mod n) significa que el
                     El entero n divide al entero a - b

   Nota: El teorema del resto chino (TRC) se puede aplicar en un sistema no
   recursiva y también de forma recursiva. En este documento, se presenta una forma recursiva.
   Se utiliza el método que sigue el algoritmo de Garner [GARNER]. Véase también
   Nota 1 en la Sección 3.2.

3. Tipos de claves

   Se emplean dos tipos de claves en los primitivos y esquemas definidos en
   Este documento: clave pública RSA y clave privada RSA. Juntas, una clave RSA
   Una clave pública y una clave privada RSA forman un par de claves RSA.

   Esta especificación admite el denominado RSA "multiprime", en el que
   El módulo puede tener más de dos factores primos. El beneficio de los factores múltiples
   RSA principal tiene un menor costo computacional para el descifrado y
   primitivas de firma, siempre que se utilice el CRT. Mejor
   El rendimiento se puede lograr en plataformas de un solo procesador, pero hasta cierto punto.
   mayor medida en plataformas multiprocesador, donde el sistema modular
   Las exponenciaciones involucradas se pueden realizar en paralelo.

   Para una discusión sobre cómo el multi-prime afecta la seguridad del RSA
   criptosistema, el lector puede consultar [SILVERMAN].

3.1 Clave pública RSA

   Para los fines de este documento, una clave pública RSA consta de dos
   Componentes:

         n el módulo RSA, un entero positivo
         e el exponente público RSA, un entero positivo




Moriarty, et al. Informativo [Página 8]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   En una clave pública RSA válida, el módulo RSA n es un producto de u
   primos impares distintos r_i, i = 1, 2, ..., u, donde u >= 2, y el RSA
   El exponente público e es un número entero entre 3 y n - 1 que satisface
   MCD(e,\lambda(n)) = 1, donde \lambda(n) = MCM(r_1 - 1, ..., r_u - 1).
   Por convención, los dos primeros primos r_1 y r_2 también pueden denotarse p
   y q, respectivamente.

   Una sintaxis recomendada para intercambiar claves públicas RSA entre
   Las implementaciones se dan en el Apéndice A.1.1; una implementación
   La representación interna puede diferir.

3.2 Clave privada RSA

   Para los fines de este documento, una clave privada RSA puede tener:
   de dos representaciones.

   1. La primera representación consiste en el par (n, d), donde
       Los componentes tienen los siguientes significados:

            n el módulo RSA, un entero positivo
            d el exponente privado RSA, un entero positivo

   2. La segunda representación consiste en un quíntuple (p, q, dP, dQ,
       qInv) y una secuencia (posiblemente vacía) de tripletes (r_i, d_i,
       t_i), i = 3, ..., u, uno por cada primo que no esté en el quíntuple,
       donde los componentes tienen los siguientes significados:

            p el primer factor, un entero positivo
            q el segundo factor, un entero positivo
            dP el exponente CRT del primer factor, un entero positivo
            dQ el exponente CRT del segundo factor, un entero positivo
            qInv el (primer) coeficiente CRT, un entero positivo
            r_i el i-ésimo factor, un entero positivo
            d_i el exponente CRT del factor i, un entero positivo
            t_i el coeficiente CRT del factor i-ésimo, un entero positivo

   En una clave privada RSA válida con la primera representación, el RSA
   El módulo n es el mismo que en la clave pública RSA correspondiente y es
   el producto de u primos impares distintos r_i, i = 1, 2, ..., u, donde u
   >= 2. El exponente privado RSA d es un entero positivo menor que n
   satisfactorio

      e * d == 1 (mód \lambda(n)),

   donde e es el exponente público RSA correspondiente y \lambda(n) es
   definido como en la Sección 3.1.





Moriarty, et al. Informativo [Página 9]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   En una clave privada RSA válida con la segunda representación, los dos
   Los factores p y q son los dos primeros factores primos del módulo RSA n
   (es decir, r_1 y r_2); los exponentes CRT dP y dQ son positivos
   números enteros menores que p y q, respectivamente, que satisfacen

      e * dP == 1 (mód (p-1))

      e * dQ == 1 (mod (q-1)) ,

   y el coeficiente CRT qInv es un entero positivo menor que p
   satisfactorio

      q * qInv == 1 (mod p).

   Si u > 2, la representación incluirá uno o más tripletes (r_i,
   d_i, t_i), i = 3, ..., u. Los factores r_i son los primos adicionales
   Factores del módulo RSA n. Cada exponente CRT d_i (i = 3, ..., u)
   satisface

      y * d_i == 1 (mod (r_i - 1)).

   Cada coeficiente CRT t_i (i = 3, ..., u) es un entero positivo menor
   que r_i satisfactorio

      R_i * t_i == 1 (mod r_i) ,

   donde R_i = r_1 * r_2 * ... * r_(i-1).

   Una sintaxis recomendada para intercambiar claves privadas RSA entre
   implementaciones, que incluyen componentes de ambas representaciones,
   se da en el Apéndice A.1.2; una implementación interna
   La representación puede diferir.

   Notas:

   1. La definición de los coeficientes CRT aquí y las fórmulas que
       Úsalos en los primitivos de la Sección 5, generalmente siguiendo el método de Garner.
       algoritmo [GARNER] (véase también Algoritmo 14.71 en [MANUAL]).
       Sin embargo, para compatibilidad con las representaciones de RSA
       claves privadas en PKCS #1 v2.0 y versiones anteriores, los roles de
       p y q están invertidos en comparación con el resto de los primos. Por lo tanto,
       El primer coeficiente CRT, qInv, se define como el inverso de q
       mod p, en lugar de como el inverso de R_1 mod r_2, es decir, de
       p módulo q.

   2. Quisquater y Couvreur [FASTDEC] observaron el beneficio de
       aplicando el CRT a las operaciones de RSA.




Moriarty, et al. Informativo [Página 10]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


4. Primitivas de conversión de datos

   En los esquemas definidos en se emplean dos primitivas de conversión de datos
   este documento:

   o I2OSP: primitiva de conversión de enteros a cadenas de octetos

   o OS2IP: primitiva de cadena de octetos a entero

   Para los fines de este documento, y de acuerdo con la sintaxis ASN.1,
   Una cadena de octetos es una secuencia ordenada de octetos (bytes de ocho bits).
   La secuencia está indexada desde el primero (convencionalmente, más a la izquierda) hasta el último.
   (extremo derecho). Para fines de conversión a y desde números enteros, el
   El primer octeto se considera el más significativo en los siguientes
   primitivas de conversión.

4.1. I2OSP

   I2OSP convierte un entero no negativo en una cadena de octetos de un
   longitud especificada.

   I2OSP (x, xLen)

   Aporte:

      x entero no negativo a convertir

      xLen longitud prevista de la cadena de octetos resultante

   Producción:

         X cadena de octetos correspondiente de longitud xLen

   Error: "número entero demasiado grande"

   Pasos:

      1. Si x >= 256^xLen, muestra "entero demasiado grande" y se detiene.

      2. Escribe el entero x en su representación única de xLen dígitos en
          base 256:

             x = x_(xLen-1) 256^(xLen-1) + x_(xLen-2) 256^(xLen-2) + ...
             + x_1 256 + x_0,

          donde 0 <= x_i < 256 (tenga en cuenta que uno o más dígitos iniciales
          será cero si x es menor que 256^(xLen-1)).




Moriarty, et al. Informativo [Página 11]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      3. Sea el octeto X_i el valor entero x_(xLen-i) para 1 <= i
          <= xLen. Salida de la cadena de octetos

             X = X_1 X_2 ... X_xLen.

4.2. OS2IP

   OS2IP convierte una cadena de octetos en un entero no negativo.

   OS2IP (X)

   Entrada: cadena de X octetos a convertir

   Salida: x entero no negativo correspondiente

   Pasos:

      1. Sean X_1 X_2 ... X_xLen los octetos de X del primero al último,
          y sea x_(xLen-i) el valor entero del octeto X_i para 1
          <= yo <= xLen.

      2. Sea x = x_(xLen-1) 256^(xLen-1) + x_(xLen-2) 256^(xLen-2) +
          ... + x_1 256 + x_0.

      3. Salida x.

5. Primitivas criptográficas

   Los primitivos criptográficos son operaciones matemáticas básicas sobre las que
   Se pueden construir esquemas criptográficos. Están pensados ​​para
   implementación en hardware o como módulos de software y no son
   destinado a proporcionar seguridad al margen de un esquema.

   En este documento se especifican cuatro tipos de primitivos, organizados en
   pares: cifrado y descifrado; y firma y verificación.

   Las especificaciones de los primitivos suponen que se cumplen ciertas condiciones
   se cumplen con las entradas, en particular las claves públicas y privadas RSA
   son validos.

5.1. Primitivas de cifrado y descifrado

   Un primitivo de cifrado produce un texto cifrado representativo de un
   representante del mensaje bajo el control de una clave pública, y un
   El primitivo de descifrado recupera el mensaje representativo del
   representante del texto cifrado bajo el control del correspondiente
   llave privada.




Moriarty, et al. Informativo [Página 12]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   En el sistema se emplea un par de primitivas de cifrado y descifrado.
   esquemas de cifrado definidos en este documento y se especifican aquí:
   Primitivo de cifrado RSA (RSAEP) / Primitivo de descifrado RSA (RSADP).
   RSAEP y RSADP implican la misma operación matemática, con
   Diferentes claves como entrada. Las primitivas definidas aquí son las mismas que
   Cifrado primitivo de factorización de enteros mediante RSA (IFEP-RSA) /
   Primitiva de descifrado de factorización de enteros mediante RSA (IFDP-RSA) en
   IEEE 1363 [IEEE1363] (excepto que se ha incorporado soporte para RSA multiprime)
   se han agregado) y son compatibles con PKCS #1 v1.5.

   La operación matemática principal en cada primitiva es la exponenciación.

5.1.1. RSAEP

   RSAEP ((nombre, apellido), m)

   Aporte:

         (n, e) Clave pública RSA

         m representante del mensaje, un número entero entre 0 y n - 1

   Salida: c representativo del texto cifrado, un número entero entre 0 y n - 1

   Error: "Representante del mensaje fuera de rango"

   Suposición: la clave pública RSA (n, e) es válida

   Pasos:

      1. Si el representante del mensaje m no está entre 0 y n - 1,
          salida "mensaje representativo fuera de rango" y se detiene.

      2. Sea c = m^e mod n.

      3. Salida c.

5.1.2. RSADP

   RSADP (K, c)

   Aporte:

         K Clave privada RSA, donde K tiene una de las siguientes formas:

         + un par (n, d)





Moriarty, et al. Informativo [Página 13]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


         + un quíntuple (p, q, dP, dQ, qInv) y un posible vacío
            secuencia de tripletes (r_i, d_i, t_i), i = 3, ..., u

         c representante del texto cifrado, un número entero entre 0 y n - 1

   Salida: m mensaje representativo, un entero entre 0 y n - 1

   Error: "representante de texto cifrado fuera de rango"

   Suposición: la clave privada RSA K es válida

   Pasos:

      1. Si el representante del texto cifrado c no está entre 0 y n - 1,
          salida "representante de texto cifrado fuera de rango" y se detiene.

      2. El representante del mensaje m se calcula de la siguiente manera.

          a. Si se utiliza la primera forma (n, d) de K, sea m = c^d mod n.

          b. Si la segunda forma (p, q, dP, dQ, qInv) y (r_i, d_i,
              Si se utiliza t_i) de K, se procede de la siguiente manera:

              i. Sea m_1 = c^dP mod p y m_2 = c^dQ mod q.

              ii. Si u > 2, sea m_i = c^(d_i) mod r_i, i = 3, ..., u.

              iii. Sea h = (m_1 - m_2) * qInv mod p.

              iv. Sea m = m_2 + q * h.

              v. Si u > 2, sea R = r_1 y para i = 3 a u hacemos

                   1. Sea R = R * r_(i-1).

                   2. Sea h = (m_i - m) * t_i mod r_i.

                   3. Sea m = m + R * h.

      3. Salida m.

   Nota: El paso 2.b se puede reescribir como un solo bucle, siempre que uno
   invierte el orden de p y q. Para mantener la coherencia con PKCS #1 v2.0,
   Sin embargo, los dos primeros primos p y q se tratan por separado.
   primos adicionales






Moriarty, et al. Informativo [Página 14]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


5.2 Primitivas de firma y verificación

   Una primitiva de firma produce un representante de firma a partir de una
   representante del mensaje bajo el control de una clave privada y una
   La primitiva de verificación recupera el mensaje representativo del
   representante de firma bajo el control del correspondiente
   clave pública. Un par de primitivas de firma y verificación es
   empleado en los esquemas de firma definidos en este documento y es
   especificado aquí: RSA Signature Primitive, versión 1 (RSASP1) / RSA
   Primitiva de verificación, versión 1 (RSAVP1).

   Los primitivos definidos aquí son los mismos que los de la factorización de enteros.
   Primitiva de firma que utiliza RSA, versión 1 (IFSP-RSA1) / Entero
   Primitiva de verificación de factorización mediante RSA, versión 1 (IFVP-RSA1)
   en IEEE 1363 [IEEE1363] (excepto que se ha incorporado soporte para RSA multiprime)
   se han agregado) y son compatibles con PKCS #1 v1.5.

   La operación matemática principal en cada primitiva es la exponenciación,
   como en los primitivos de cifrado y descifrado de la Sección 5.1.
   RSASP1 y RSAVP1 son iguales que RSADP y RSAEP excepto por la
   nombres de sus argumentos de entrada y salida; se distinguen como
   Están destinados a diferentes propósitos.

5.2.1.RSASP1

   RSASP1 (K, m)

   Aporte:

      K Clave privada RSA, donde K tiene una de las siguientes formas:
               - un par (n, d)
               - un quíntuple (p, q, dP, dQ, qInv) y un (posiblemente vacío)
                 secuencia de tripletes (r_i, d_i, t_i), i = 3, ..., u
      m representante del mensaje, un número entero entre 0 y n - 1


   Producción:

      s representante de la firma, un número entero entre 0 y n - 1

   Error: "Representante del mensaje fuera de rango"

   Suposición: la clave privada RSA K es válida








Moriarty, et al. Informativo [Página 15]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Pasos:

      1. Si el representante del mensaje m no está entre 0 y n - 1,
          salida "mensaje representativo fuera de rango" y se detiene.

      2. La firma representativa s se calcula de la siguiente manera.

          a. Si se utiliza la primera forma (n, d) de K, sea s = m^d mod n.

          b. Si la segunda forma (p, q, dP, dQ, qInv) y (r_i, d_i,
              Si se utiliza t_i) de K, se procede de la siguiente manera:

              1. Sea s_1 = m^dP mod p y s_2 = m^dQ mod q.

              2. Si u > 2, sea s_i = m^(d_i) mod r_i, i = 3, ..., u.

              3. Sea h = (s_1 - s_2) * qInv mod p.

              4. Sea s = s_2 + q * h.

              5. Si u > 2, sea R = r_1 y para i = 3 a u hagamos

                  a. Sea R = R * r_(i-1).

                  b. Sea h = (s_i - s) * t_i mod r_i.

                  c. Sea s = s + R * h.

      3. Salida s.

   Nota: El paso 2.b se puede reescribir como un solo bucle, siempre que uno
   invierte el orden de p y q. Para mantener la coherencia con PKCS #1 v2.0,
   Sin embargo, los dos primeros primos p y q se tratan por separado.
   primos adicionales

5.2.2.RSAVP1

   RSAVP1 ((nombre, apellido), apellido(s))

   Aporte:

         (n, e) Clave pública RSA

         s representante de la firma, un número entero entre 0 y n - 1







Moriarty, et al. Informativo [Página 16]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Producción:

         m representante del mensaje, un número entero entre 0 y n - 1

   Error: "representante de firma fuera de rango"

   Suposición: la clave pública RSA (n, e) es válida

   Pasos:

      1. Si el representante de la firma s no está entre 0 y n - 1,
          salida "representante de firma fuera de rango" y se detiene.

      2. Sea m = s^e mod n.

      3. Salida m.

6. Descripción general de los esquemas

   Un esquema combina primitivas criptográficas y otras técnicas para
   lograr un objetivo de seguridad particular. Hay dos tipos de esquemas:
   especificado en este documento: esquemas de cifrado y esquemas de firma
   con apéndice.

   Los esquemas especificados en este documento tienen un alcance limitado en el sentido de que
   Sus operaciones consisten únicamente en pasos para procesar datos con un RSA.
   clave pública o privada, y no incluyen pasos para obtenerla o
   validando la clave. Por lo tanto, además de las operaciones del esquema, una
   La aplicación normalmente incluirá operaciones de gestión de claves mediante las cuales
   Las partes pueden seleccionar claves públicas y privadas RSA para un plan
   operación. Las operaciones adicionales específicas y otros detalles se encuentran
   fuera del alcance de este documento.

   Como fue el caso de los primitivos criptográficos (Sección 5), la
   Las especificaciones de las operaciones del esquema suponen que se cumplen ciertas condiciones
   se cumplen con las entradas, en particular las claves públicas y privadas RSA
   son válidos. Por lo tanto, el comportamiento de una implementación no está especificado.
   Cuando una clave no es válida. El impacto de este comportamiento no especificado
   Depende de la aplicación. Posibles medios para direccionar claves
   La validación incluye la validación explícita de la clave por parte de la aplicación; clave
   validación dentro de la infraestructura de clave pública; y asignación de
   responsabilidad por operaciones realizadas con una clave no válida para la parte
   ¿Quién generó la clave?

   Una práctica criptográfica generalmente buena es emplear una clave RSA determinada
   par en un solo esquema. Esto evita el riesgo de vulnerabilidad en
   Un esquema puede comprometer la seguridad del otro y puede ser
   Es esencial mantener una seguridad demostrable. Mientras que RSAES-PKCS1-v1_5



Moriarty, et al. Informativo [Página 17]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   (Sección 7.2) y RSASSA-PKCS1-v1_5 (Sección 8.2) tradicionalmente han
   Se han empleado juntos sin ninguna interacción negativa conocida (de hecho,
   Este es el modelo introducido por PKCS #1 v1.5), tal uso combinado de
   NO SE RECOMIENDA un par de claves RSA para aplicaciones nuevas.

   Para ilustrar los riesgos relacionados con el empleo de un par de claves RSA
   En más de un esquema, supongamos que se emplea un par de claves RSA en ambos
   RSAES-OAEP (Sección 7.1) y RSAES-PKCS1-v1_5. Aunque RSAES-OAEP
   por sí solo resistiría el ataque, un oponente podría ser capaz de explotar una
   Debilidad en la implementación de RSAES-PKCS1-v1_5 para recuperar
   mensajes cifrados con cualquiera de los dos esquemas. Como otro ejemplo, supongamos
   Se utiliza un par de claves RSA tanto en RSASSA-PSS (Sección 8.1) como
   RSASSA-PKCS1-v1_5. Entonces, la prueba de seguridad para RSASSA-PSS no sería válida.
   ya no sería suficiente ya que la prueba no explica la
   posibilidad de que se puedan generar firmas con un segundo esquema.
   Se pueden aplicar consideraciones similares si se utiliza un par de claves RSA en
   uno de los esquemas definidos aquí y en una variante definida en otro lugar.

7. Esquemas de cifrado

   A los efectos de este documento, un esquema de cifrado consiste en
   una operación de cifrado y una operación de descifrado, donde
   La operación de cifrado produce un texto cifrado a partir de un mensaje con una
   la clave pública RSA del destinatario y la operación de descifrado recupera la
   mensaje del texto cifrado con el RSA correspondiente del destinatario
   llave privada.

   Un esquema de cifrado se puede emplear en una variedad de aplicaciones.
   Una aplicación típica es un protocolo de establecimiento de clave, donde
   El mensaje contiene material clave que debe entregarse de forma confidencial desde uno
   parte a otra. Por ejemplo, PKCS #7 [RFC2315] emplea un método similar.
   Protocolo para enviar una clave de cifrado de contenido de un remitente a un
   destinatario; los esquemas de cifrado definidos aquí serían clave adecuados
   algoritmos de cifrado en ese contexto.

   En este documento se especifican dos esquemas de cifrado: RSAES-OAEP y
   RSAES-PKCS1-v1_5. Se REQUIERE que RSAES-OAEP sea compatible con los nuevos
   aplicaciones; RSAES-PKCS1-v1_5 se incluye solo por compatibilidad
   con aplicaciones existentes.

   Los esquemas de cifrado que se dan aquí siguen un modelo general similar a
   que se emplea en IEEE 1363 [IEEE1363], que combina el cifrado y
   primitivas de descifrado con un método de codificación para el cifrado.
   Las operaciones de cifrado aplican una operación de codificación de mensajes a un mensaje.
   para producir un mensaje codificado, que luego se convierte en un número entero
   representante del mensaje. Se aplica una primitiva de cifrado al
   representante del mensaje para producir el texto cifrado. Al invertir esto,
   Las operaciones de descifrado aplican un primitivo de descifrado al



Moriarty, et al. Informativo [Página 18]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   texto cifrado para recuperar un representante del mensaje, que luego es
   convertido en un mensaje codificado en cadena de octetos. Un mensaje de decodificación
   Se aplica la operación al mensaje codificado para recuperar el mensaje.
   y verificar la exactitud del descifrado.

   Para evitar debilidades de implementación relacionadas con la forma en que se registran los errores
   manejado dentro de la operación de decodificación (ver [BLEICHENBACHER] y
   [MANGER]), las operaciones de codificación y decodificación para RSAES-OAEP y
   RSAES-PKCS1-v1_5 están integrados en las especificaciones de los respectivos
   esquemas de cifrado en lugar de definirse en especificaciones separadas.
   Ambos esquemas de cifrado son compatibles con los esquemas correspondientes.
   en PKCS #1 v2.1.

7.1. RSAES-OAEP

   RSAES-OAEP combina las primitivas RSAEP y RSADP (Secciones 5.1.1
   y 5.1.2) con el método de codificación EME-OAEP (Paso 2 en
   Sección 7.1.1 y Paso 3 en la Sección 7.1.2). EME-OAEP se basa en
   Esquema de cifrado asimétrico óptimo de Bellare y Rogaway [OAEP].
   Es compatible con el esquema de cifrado de factorización de enteros.
   (IFES) definido en IEEE 1363 [IEEE1363], donde el cifrado y
   Los primitivos de descifrado son IFEP-RSA e IFDP-RSA y el mensaje
   El método de codificación es EME-OAEP. RSAES-OAEP puede operar en mensajes de
   longitud hasta k - 2hLen -2 octetos, donde hLen es la longitud de la
   salida de la función hash subyacente y k es la longitud en
   octetos del módulo RSA del destinatario.

   Suponiendo que calcular las raíces e-ésimas módulo n no es factible y que
   La función de generación de máscara en RSAES-OAEP tiene propiedades apropiadas,
   RSAES-OAEP es semánticamente seguro contra texto cifrado seleccionado adaptativo
   ataques. Esta seguridad es demostrable en el sentido de que la dificultad
   La dificultad de romper el RSAES-OAEP puede estar directamente relacionada con la dificultad de
   invirtiendo la función RSA, siempre que la generación de máscara
   La función se considera como una caja negra o un oráculo aleatorio; consulte [FOPS] y
   La nota a continuación para mayor discusión.

   Tanto las operaciones de cifrado como las de descifrado de RSAES-OAEP requieren
   el valor de una etiqueta L como entrada. En esta versión de PKCS #1, L es
   la cadena vacía; otros usos de la etiqueta están fuera del alcance de
   Este documento. Consulte el Apéndice A.2.1 para conocer la sintaxis ASN.1 pertinente.

   RSAES-OAEP está parametrizado por la elección de la función hash y la máscara
   Función de generación. Esta opción debe ser fija para un RSA determinado.
   clave. Las funciones de generación de hash y máscara sugeridas se dan en
   Apéndice B.






Moriarty, et al. Informativo [Página 19]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Nota: Los resultados anteriores han aclarado de manera útil las propiedades de seguridad.
   del método de codificación OAEP [OAEP] (aproximadamente el procedimiento descrito
   en el Paso 2 de la Sección 7.1.1). Los antecedentes son los siguientes. En 1994,
   Bellare y Rogaway [OAEP] introdujeron un concepto de seguridad que...
   denotó conciencia de texto simple (PA94). Demostraron que si un
   El cifrado de clave pública determinista primitivo (por ejemplo, RSAEP) es difícil
   Para invertir sin la clave privada, entonces la correspondiente basada en OAEP
   El esquema de cifrado reconoce texto simple (en el modelo de oráculo aleatorio).
   Significa aproximadamente que un adversario no puede producir un texto cifrado válido.
   Sin "conocer" realmente el texto sin formato subyacente. Texto sin formato
   El conocimiento de un esquema de cifrado está estrechamente relacionado con la
   resistencia del esquema contra ataques de texto cifrado seleccionado. En tal
   ataques, a un adversario se le da la oportunidad de enviar consultas a un
   Oracle simula el primitivo de descifrado. Utilizando los resultados de
   Estas consultas, el adversario intenta descifrar un desafío.
   texto cifrado.

   Sin embargo, hay dos tipos de ataques de texto cifrado elegido y PA94
   implica seguridad contra sólo uno de ellos. La diferencia se basa en
   Lo que se le permite hacer al adversario después de que se le presenta el desafío.
   Texto cifrado. El escenario de ataque indiferente (denominado CCA1) no
   admitir cualquier consulta al oráculo de descifrado después de que el adversario esté
   Dado el desafío del texto cifrado, mientras que el escenario adaptativo
   (denominado CCA2) lo hace (excepto que el oráculo de descifrado se niega a hacerlo).
   descifrar el texto cifrado del desafío una vez que se publique). En 1998,
   Bellare y Rogaway, junto con Desai y Pointcheval [PA98], llegaron
   con una noción nueva y más fuerte de conciencia de texto simple (PA98) que
   implica seguridad contra CCA2.

   En resumen, ha habido dos fuentes potenciales para
   idea errónea: que PA94 y PA98 son conceptos equivalentes, o que
   CCA1 y CCA2 son conceptos equivalentes. Cualquier suposición conduce a
   La conclusión de que el documento de Bellare-Rogaway implica seguridad de
   OAEP contra CCA2, lo cual no hace.

   (Nota al pie: Tal vez sea justo mencionar que PKCS #1 v2.0 cita [OAEP]
   y afirma que "un ataque de texto cifrado elegido es ineficaz contra un
   esquema de cifrado que reconoce texto simple como RSAES-OAEP" sin
   especificando el tipo de reconocimiento de texto simple o texto cifrado elegido
   (Ataque considerado.)

   Nunca se ha demostrado que OAEP sea seguro contra CCA2; de hecho, Victor Shoup
   [SHOUP] ha demostrado que tal prueba no existe en el
   Caso general. En pocas palabras, Shoup demostró que un adversario en el
   Escenario CCA2 ¿Quién sabe cómo invertir parcialmente el cifrado?
   primitivo pero no sabe cómo invertirlo completamente bien puede ser
   capaz de romper el esquema. Por ejemplo, uno puede imaginar un atacante
   ¿Quién es capaz de romper el RSAES-OAEP si sabe cómo recuperar todo menos



Moriarty, et al. Informativo [Página 20]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   los primeros 20 bytes de un entero aleatorio cifrado con RSAEP.
   El atacante no necesita poder invertir completamente RSAEP, porque
   no utiliza los primeros 20 octetos en su ataque.

   Aun así, RSAES-OAEP es seguro contra CCA2, lo que fue demostrado por
   Fujisaki, Okamoto, Pointcheval y Stern [FOPS] poco después de la
   Anuncio del resultado de Shoup. Utilizando una inteligente reducción de red
   técnicas, lograron demostrar cómo invertir completamente el RSAEP dado
   una parte suficientemente grande de la preimagen. Esta observación,
   combinado con una prueba de que OAEP es seguro contra CCA2 si el
   El primitivo de cifrado subyacente es difícil de invertir parcialmente y se llena
   la brecha entre lo que Bellare y Rogaway demostraron sobre RSAES-OAEP y
   lo que algunos pueden haber creído que probaron. Un poco
   Paradójicamente, nos salvamos gracias a una aparente debilidad en la RSAEP.
   (es decir, toda la inversa puede deducirse de partes de ella).

   Desafortunadamente, sin embargo, la reducción de seguridad no es eficiente para
   parámetros concretos. Si bien la prueba relaciona con éxito un
   adversario A contra la seguridad CCA2 de RSAES-OAEP a un algoritmo I
   invirtiendo RSA, la probabilidad de éxito para I es solo aproximadamente
   \epsilon^2 / 2^18, donde \epsilon es la probabilidad de éxito para
   A.

   (Nota al pie: En [FOPS], la probabilidad de éxito del inversor era
   \epsilon^2 / 4. El factor adicional 1 / 2^16 se debe a los ocho
   bits cero fijos al comienzo del mensaje codificado EM, que son
   no presente en la variante de OAEP considerada en [FOPS]. (A debe ser
   Se aplica dos veces para invertir RSA, y cada aplicación corresponde a una
   factor 1 / 2^8.))

   Además, el tiempo de ejecución para I es aproximadamente t^2, donde t es
   el tiempo de ejecución del adversario. La consecuencia es que no podemos
   excluir la posibilidad de que atacar RSAES-OAEP sea considerablemente
   más fácil que invertir el RSA para parámetros concretos. Aún así, el
   La existencia de una prueba de seguridad proporciona cierta seguridad de que
   La construcción RSAES-OAEP es más sólida que las construcciones ad hoc como
   Código RSAES-PKCS1-v1_5.

   Esquemas de cifrado híbrido basados ​​en la encapsulación de clave RSA
   El paradigma del mecanismo (RSA-KEM) ofrece pruebas estrictas de seguridad directamente
   aplicable a parámetros concretos; véase [ISO18033] para más información.
   Las futuras versiones de PKCS #1 pueden especificar esquemas basados ​​en esto
   paradigma.








Moriarty, et al. Informativo [Página 21]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


7.1.1. Operación de cifrado

   RSAES-OAEP-ENCRYPT ((n, e), M, L)

   Opciones:

      Función hash (hLen denota la longitud en octetos de
               la salida de la función hash)
      Función de generación de máscara MGF

   Aporte:

      (n, e) clave pública RSA del destinatario (k denota la longitud en
               octetos del módulo RSA n)
      Mensaje M a cifrar, una cadena de octetos de longitud mLen,
               donde mLen <= k - 2hLen - 2
      L etiqueta opcional que se asociará con el mensaje;
               Valor predeterminado para L, si no se proporciona L, está vacío.
               cadena

   Producción:

      Texto cifrado C, una cadena de octetos de longitud k

   Errores: "mensaje demasiado largo"; "etiqueta demasiado larga"

   Suposición: la clave pública RSA (n, e) es válida

   Pasos:

      1. Comprobación de longitud:

          a. Si la longitud de L es mayor que la limitación de entrada
              para la función hash (2^61 - 1 octetos para SHA-1), salida
              "Etiqueta demasiado larga" y parar.

          b. Si mLen > k - 2hLen - 2, muestra "mensaje demasiado largo" y
              detener.

      2. Codificación EME-OAEP (ver Figura 1 a continuación):

          a. Si no se proporciona la etiqueta L, sea L la cadena vacía.
              Sea lHash = Hash(L), una cadena de octetos de longitud hLen (ver
              (la nota de abajo).

          b. Genere una cadena de relleno PS que consta de k - mLen -
              2hLen: 2 octetos cero. La longitud de PS puede ser cero.




Moriarty, et al. Informativo [Página 22]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


          c. Concatenar lHash, PS, un solo octeto con hexadecimal
              valor 0x01, y el mensaje M para formar un bloque de datos DB de
              longitud k - hLen - 1 octetos como

                 BD = lHash || PS || 0x01 || M.

          d. Genere una semilla de cadena de octetos aleatoria de longitud hLen.

          e. Sea dbMask = MGF(semilla, k - hLen - 1).

          f. Sea maskedDB = DB \xor dbMask.

          g. Sea seedMask = MGF(maskedDB, hLen).

          h. Sea maskedSeed = semilla \xor seedMask.

          i. Concatenar un único octeto con valor hexadecimal 0x00,
              maskedSeed y maskedDB para formar un mensaje codificado EM de
              longitud k octetos como

                 EM = 0x00 || SemillaEnmascarada || BaseDeDatosEnmascarada.

      3. Cifrado RSA:

          a. Convertir el mensaje codificado EM en un mensaje entero
              representante m (ver Sección 4.2):

                 m = OS2IP (EM).

          b. Aplique la primitiva de cifrado RSAEP (Sección 5.1.1) a
              la clave pública RSA (n, e) y el representante del mensaje m
              Para producir un texto cifrado entero representativo c:

                 c = RSAEP ((n, e), m).

          c. Convertir el texto cifrado representativo c en un texto cifrado C
              de longitud k octetos (ver Sección 4.1):

                 C = I2OSP(c, k).












Moriarty, et al. Informativo [Página 23]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      4. Imprima el texto cifrado C.

      _________________________________________________________________

                                +----------+------+--+-------+
                           BD = | lHash | PS | 01 | M |
                                +----------+------+--+-------+
                                               |
                     +----------+ |
                     | semilla | |
                     +----------+ |
                           | |
                           |-------> MGF ---> xor
                           | |
                  +--+ V |
                  |00| xor <-----MGF <-----|
                  +--+ | |
                    | | |
                    VVV
                  +--+----------+----------------------------+
            EM = |00|semilla enmascarada| base de datos enmascarada |
                  +--+----------+----------------------------+
      _________________________________________________________________

                   Figura 1: Operación de codificación EME-OAEP

   Notas:

   - lHash es el hash de la etiqueta opcional L.

   - La operación de decodificación sigue los pasos inversos para recuperar M y
      verificar lHash y PS.

   - Si L es la cadena vacía, el valor hash correspondiente lHash tiene
      la siguiente representación hexadecimal para diferentes opciones de
      Picadillo:

      SHA-1: (0x)da39a3ee 5e6b4b0d 3255bfef 95601890 afd80709
      SHA-256: (0x)e3b0c442 98fc1c14 9afbf4c8 996fb924 27ae41e4 649b934c
                   a495991b 7852b855
      SHA-384: (0x)38b060a7 51ac9638 4cd9327e b1b1e36a 21fdb711 14be0743
                   4c0cc7bf 63f6e1da 274edebf e76f65fb d51ad2f1 4898b95b
      SHA-512: (0x)cf83e135 7eefb8bd f1542850 d66d8007 d620e405 0b5715dc
                   83f4a921 d36ce9ce 47d0d13c 5d85f2b0 ff8318d2 877eec2f
                   63b931bd 47417a81 a538327a f927da3e






Moriarty, et al. Informativo [Página 24]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


7.1.2. Operación de descifrado

   RSAES-OAEP-DESCIFRADO (K, C, L)

   Opciones:

      Función hash (hLen denota la longitud en octetos de
               la salida de la función hash)
      Función de generación de máscara MGF

   Aporte:

      Clave privada RSA del destinatario K (k indica la longitud en
               octetos del módulo RSA n), donde k >= 2hLen + 2
      Texto cifrado C a descifrar, una cadena de octetos de longitud k
      L etiqueta opcional cuya asociación con el mensaje es
               ser verificado; el valor predeterminado para L, si L no es
               siempre que sea una cadena vacía

   Producción:

      Mensaje M, una cadena de octetos de longitud mLen, donde
               mLen <= k - 2hLen - 2

   Error: "error de descifrado"

   Pasos:

      1. Comprobación de longitud:

          a. Si la longitud de L es mayor que la limitación de entrada
              para la función hash (2^61 - 1 octetos para SHA-1), salida
              "error de descifrado" y se detiene.

          b. Si la longitud del texto cifrado C no es de k octetos, salida
              "error de descifrado" y se detiene.

          c. Si k < 2hLen + 2, muestra "error de descifrado" y se detiene.

      2. Descifrado RSA:

          a. Convertir el texto cifrado C en un texto cifrado entero
              representante c (véase la sección 4.2):

                 c = OS2IP (C).






Moriarty, et al. Informativo [Página 25]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


          b. Aplique la primitiva de descifrado RSADP (Sección 5.1.2) a
              la clave privada RSA K y el texto cifrado representativo c
              Para producir un mensaje entero representativo m:

                 m = RSADP (K, c).

              Si RSADP muestra "representante de texto cifrado fuera de rango"
              (lo que significa que c >= n), muestra "error de descifrado" y se detiene.

          c. Convertir el representante del mensaje m en un mensaje codificado
              EM de longitud k octetos (ver Sección 4.1):

                 EM = I2OSP(m,k).

      3. Decodificación EME-OAEP:

          a. Si no se proporciona la etiqueta L, sea L la cadena vacía.
              Sea lHash = Hash(L), una cadena de octetos de longitud hLen (ver
              la nota en la Sección 7.1.1).

          b. Separar el mensaje codificado EM en un solo octeto Y, un
              cadena de octetos maskedSeed de longitud hLen y un octeto
              cadena maskedDB de longitud k - hLen - 1 como

                 EM = Y || semilla enmascarada || base de datos enmascarada.

          c. Sea seedMask = MGF(maskedDB, hLen).

          d. Sea semilla = maskedSeed \xor seedMask.

          e. Sea dbMask = MGF(semilla, k - hLen - 1).

          f. Sea DB = maskedDB \xor dbMask.

          g. Separe la base de datos en una cadena de octetos lHash' de longitud hLen, a
              Cadena de relleno (posiblemente vacía) PS que consta de octetos
              con valor hexadecimal 0x00, y un mensaje M como

                 BD = lHash' || PS || 0x01 || M.

              Si no hay ningún octeto con valor hexadecimal 0x01 a
              separar PS de M, si lHash no es igual a lHash', o si
              Y es distinto de cero, muestra "error de descifrado" y se detiene. (Ver
              (la nota a continuación.)







Moriarty, et al. Informativo [Página 26]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      4. Imprima el mensaje M.

      Nota: Se debe tener cuidado para garantizar que un oponente no pueda
      Distinguir las diferentes condiciones de error en el Paso 3.g, ya sea por
      mensaje de error o de sincronización y, de manera más general, que un oponente
      No se puede obtener información parcial sobre el mensaje codificado EM.
      De lo contrario, un oponente podría obtener información útil.
      sobre el descifrado del texto cifrado C, lo que conduce a un resultado elegido.
      ataque de texto cifrado como el observado por Manger [MANGER].

7.2.RSAES-PKCS1-v1_5

   RSAES-PKCS1-v1_5 combina las primitivas RSAEP y RSADP (Secciones
   5.1.1 y 5.1.2) con el método de codificación EME-PKCS1-v1_5 (Paso 2 en
   Sección 7.2.1 y Paso 3 en la Sección 7.2.2). Es matemáticamente
   equivalente al esquema de cifrado en PKCS #1 v1.5.
   RSAES-PKCS1-v1_5 puede operar en mensajes de longitud hasta k - 11
   octetos (k es la longitud del octeto del módulo RSA), aunque tenga cuidado
   Se deben tomar medidas para evitar ciertos ataques al RSA de bajo exponente debido a
   Coppersmith, Franklin, Patarin y Reiter cuando se trata de mensajes largos.
   cifrado (ver la tercera viñeta en las notas a continuación y [LOWEXP];
   [NEWATTACK] contiene un ataque mejorado). Como regla general, el uso
   de este esquema para cifrar un mensaje arbitrario, a diferencia de un
   Clave generada aleatoriamente, NO SE RECOMIENDA.

   Es posible generar textos cifrados RSAES-PKCS1-v1_5 válidos sin
   conociendo los textos claros correspondientes, con una probabilidad razonable
   de éxito. Esta capacidad puede aprovecharse en un texto cifrado seleccionado
   ataque como se muestra en [BLEICHENBACHER]. Por lo tanto, si RSAES-PKCS1-v1_5
   Si se va a utilizar, se deben adoptar ciertas contramedidas de fácil implementación.
   tomadas para frustrar el ataque encontrado en [BLEICHENBACHER]. Típico
   Los ejemplos incluyen la adición de estructura a los datos que se van a codificar,
   Comprobación rigurosa de la conformidad con PKCS #1 v1.5 (y otras redundancias)
   en mensajes descifrados y la consolidación de mensajes de error en un
   Protocolo cliente-servidor basado en PKCS #1 v1.5. Todos estos pueden ser
   contramedidas eficaces y que no impliquen cambios en un protocolo
   Basado en PKCS #1 v1.5. Consulte [BKS] para obtener más información sobre estos
   y otras contramedidas. Recientemente se ha demostrado que la
   seguridad del protocolo de enlace SSL/TLS [RFC5246], que utiliza
   RSAES-PKCS1-v1_5 y ciertas contramedidas pueden estar relacionadas con un
   variante del problema RSA; véase [RSATLS] para discusión.

   Nota: Los siguientes pasajes describen algunas recomendaciones de seguridad.
   Recomendaciones de PKCS sobre el uso de RSAES-PKCS1-v1_5
   Se incluyen las versiones 1.5 y n.° 1, así como nuevas recomendaciones motivadas por
   avances criptoanalíticos logrados en los años intermedios.





Moriarty, et al. Informativo [Página 27]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   o Se RECOMIENDA que los octetos pseudoaleatorios del Paso 2 en
      La sección 7.2.1 se generará de forma independiente para cada cifrado.
      proceso, especialmente si los mismos datos se introducen en más de un proceso.
      proceso de cifrado. Los resultados de Haastad [HAASTAD] son ​​uno
      Motivación para esta recomendación.

   o La cadena de relleno PS en el Paso 2 de la Sección 7.2.1 es al menos ocho
      octetos de longitud, lo cual es una condición de seguridad para la clave pública
      Operaciones que dificultan que un atacante recupere datos.
      probando todos los bloques de cifrado posibles.

   o Los octetos pseudoaleatorios también pueden ayudar a frustrar un ataque debido a
      Coppersmith et al. [LOWEXP] (ver [NEWATTACK] para una mejora)
      del ataque) cuando el tamaño del mensaje a cifrar es
      Se mantiene pequeño. El ataque funciona en RSA de bajo exponente cuando son similares.
      Los mensajes se cifran con la misma clave pública RSA. Más
      En concreto, en un tipo de ataque, cuando dos entradas a
      RSAEP acuerda una gran fracción de bits (8/9) y RSA de bajo exponente
      (e = 3) se utiliza para cifrarlos a ambos, es posible que sea posible
      Recuperar ambas entradas con el ataque. Otro sabor del ataque.
      tiene éxito en descifrar un solo texto cifrado cuando un gran
      La fracción (2/3) de la entrada a RSAEP ya se conoce.
      En aplicaciones típicas, el mensaje a cifrar es corto (por ejemplo,
      una clave simétrica de 128 bits), por lo que no se conocerá suficiente información
      o común entre dos mensajes para permitir el ataque. Sin embargo, si
      un mensaje largo está encriptado, o si se conoce parte de un mensaje,
      Entonces el ataque puede ser un problema. En cualquier caso, el RSAES-OAEP
      El plan supera el ataque.

7.2.1. Operación de cifrado

   RSAES-PKCS1-V1_5-ENCRYPT ((n, e), M)

   Aporte:

      (n, e) clave pública RSA del destinatario (k denota la longitud en
               octetos del módulo n)
      Mensaje M a cifrar, cadena de octetos de longitud
               mLen, donde mLen <= k - 11

   Producción:

      Texto cifrado C, una cadena de octetos de longitud k

   Error: "mensaje demasiado largo"






Moriarty, et al. Informativo [Página 28]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Pasos:

      1. Comprobación de longitud: si mLen > k - 11, muestra "mensaje demasiado largo"
          y pare.

      2. Codificación EME-PKCS1-v1_5:

          a. Generar una cadena de octetos PS de longitud k - mLen - 3
              que consiste en octetos distintos de cero generados de forma pseudoaleatoria.
              La longitud de PS será de al menos ocho octetos.

          b. Concatenar PS, el mensaje M y otros rellenos para formar
              un mensaje codificado EM de longitud k octetos como

                 EM = 0x00 || 0x02 || PS || 0x00 || METRO.

      3. Cifrado RSA:

          a. Convertir el mensaje codificado EM en un mensaje entero
              representante m (ver Sección 4.2):

                 m = OS2IP (EM).

          b. Aplique la primitiva de cifrado RSAEP (Sección 5.1.1) a
              la clave pública RSA (n, e) y el representante del mensaje m
              Para producir un texto cifrado entero representativo c:

                 c = RSAEP ((n, e), m).

          c. Convertir el texto cifrado representativo c en un texto cifrado C
              de longitud k octetos (ver Sección 4.1):

                 C = I2OSP(c, k).

      4. Imprima el texto cifrado C.

7.2.2. Operación de descifrado

   RSAES-PKCS1-V1_5-DECRYPT (K, C)

   Aporte:

      Clave privada RSA del destinatario K
      Texto cifrado C a descifrar, una cadena de octetos de longitud k,
               donde k es la longitud en octetos del módulo RSA n






Moriarty, et al. Informativo [Página 29]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Producción:

      Mensaje M, una cadena de octetos con una longitud máxima de k - 11

   Error: "error de descifrado"

   Pasos:

      1. Comprobación de longitud: si la longitud del texto cifrado C no es k
          octetos (o si k < 11), salida "error de descifrado" y parada.

      2. Descifrado RSA:

          a. Convertir el texto cifrado C en un texto cifrado entero
              representante c (véase la sección 4.2):

                 c = OS2IP (C).

          b. Aplique la primitiva de descifrado RSADP (Sección 5.1.2) a
              La clave privada RSA (n, d) y el texto cifrado
              representante c para producir un mensaje entero
              representante m:

                 m = RSADP ((n, d), c).

              Si RSADP muestra "representante de texto cifrado fuera de rango"
              (lo que significa que c >= n), muestra "error de descifrado" y se detiene.

          c. Convertir el representante del mensaje m en un mensaje codificado
              EM de longitud k octetos (ver Sección 4.1):

                 EM = I2OSP(m,k).

      3. Decodificación EME-PKCS1-v1_5: Separa el mensaje codificado EM en
          una cadena de octetos PS que consta de octetos distintos de cero y un mensaje
          M como

             EM = 0x00 || 0x02 || PS || 0x00 || METRO.

          Si el primer octeto de EM no tiene el valor hexadecimal 0x00,
          Si el segundo octeto de EM no tiene valor hexadecimal
          0x02, si no hay ningún octeto con valor hexadecimal 0x00 a
          separar PS de M, o si la longitud de PS es menor a 8
          octetos, salida "error de descifrado" y parada. (Ver la nota
          abajo.)

      4. Salida M.




Moriarty, et al. Informativo [Página 30]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      Nota: Se debe tener cuidado para garantizar que un oponente no pueda
      Distinguir las diferentes condiciones de error en el Paso 3, ya sea por
      mensaje de error o tiempo. De lo contrario, un oponente podría ser capaz de
      Obtenga información útil sobre el descifrado del texto cifrado
      C, lo que lleva a una versión reforzada del ataque de Bleichenbacher.
      [BLEICHENBACHER]; comparar con el ataque de Manger [MANGER].

8. Esquema de firma con apéndice

   A los efectos de este documento se entenderá por esquema de firma con apéndice
   consiste en una operación de generación de firma y una firma
   operación de verificación, donde la operación de generación de firma
   produce una firma a partir de un mensaje con la clave privada RSA de un firmante,
   y la operación de verificación de firma verifica la firma en
   el mensaje con la clave pública RSA correspondiente del firmante.
   verificar una firma construida con este tipo de esquema, es
   necesario tener el mensaje en sí. De esta manera, los esquemas de firma
   con apéndice se distinguen de los esquemas de firma con mensaje
   recuperación, que no están soportadas en este documento.

   Un esquema de firma con apéndice se puede emplear en una variedad de
   aplicaciones. Por ejemplo, los esquemas de firma con apéndice
   Los algoritmos de firma definidos aquí serían adecuados para X.509
   certificados [ISO9594]. Se podrían emplear esquemas de firma relacionados
   en PKCS #7 [RFC2315], aunque por razones técnicas la norma actual
   La versión n.° 7 de PKCS separa una función hash de un esquema de firma,
   que es diferente a lo que se hace aquí; ver la nota en
   Apéndice A.2.3 para mayor discusión.

   En este documento se especifican dos esquemas de firma con apéndice:
   RSASSA-PSS y RSASSA-PKCS1-v1_5. Aunque no se conocen ataques
   contra RSASSA-PKCS1-v1_5, en aras de una mayor robustez,
   RSASSA-PSS es REQUERIDO en aplicaciones nuevas. RSASSA-PKCS1-v1_5 es
   Incluido sólo para compatibilidad con aplicaciones existentes.

   Los esquemas de firma con apéndice que se presentan aquí siguen un modelo general
   similar al empleado en IEEE 1363 [IEEE1363], combinando la firma
   y primitivas de verificación con un método de codificación para firmas.
   Las operaciones de generación de firma aplican una codificación de mensajes.
   operación a un mensaje para producir un mensaje codificado, que luego es
   convertido en un mensaje entero representativo. Una firma
   El primitivo se aplica al representante del mensaje para producir el
   firma. Al revertir esto, las operaciones de verificación de firma
   aplicar una primitiva de verificación de firma a la firma a recuperar
   un representante del mensaje, que luego se convierte en una cadena de octetos.
   Mensaje codificado. Se aplica una operación de verificación al mensaje.
   y el mensaje codificado para determinar si son consistentes.




Moriarty, et al. Informativo [Página 31]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Si el método de codificación es determinista (por ejemplo, EMSA-PKCS1-v1_5),
   La operación de verificación puede aplicar la operación de codificación del mensaje a
   el mensaje y comparar el mensaje codificado resultante con el
   mensaje codificado derivado previamente. Si hay una coincidencia, el
   La firma se considera válida. Si el método es aleatorio (por ejemplo,
   EMSA-PSS), la operación de verificación suele ser más complicada.
   Por ejemplo, la operación de verificación en EMSA-PSS extrae la
   Sal aleatoria y una salida hash del mensaje codificado y comprobaciones
   si la salida del hash, la sal y el mensaje son consistentes;
   La salida hash es una función determinista en términos del mensaje.
   y la sal. Para ambos esquemas de firma con apéndice definido en
   Este documento, la generación de firma y la verificación de firma.
   Las operaciones se implementan fácilmente como operaciones de "una sola pasada" si
   La firma se coloca después del mensaje. Consulte PKCS #7 [RFC2315] para obtener más información.
   formato de ejemplo en el caso de RSASSA-PKCS1-v1_5.

8.1. RSASSA-PSS

   RSASSA-PSS combina las primitivas RSASP1 y RSAVP1 con la
   Método de codificación EMSA-PSS. Es compatible con el sistema de codificación de números enteros.
   Esquema de Firma de Factorización con Apéndice (IFSSA) modificado en
   IEEE 1363a [IEEE1363A], donde se incluye la firma y la verificación
   Los primitivos son IFSP-RSA1 e IFVP-RSA1 como se define en IEEE 1363
   [IEEE1363], y el método de codificación del mensaje es EMSA4. EMSA4 es
   Un poco más general que EMSA-PSS, ya que actúa sobre cadenas de bits en lugar de
   que en cadenas de octetos. EMSA-PSS es equivalente a EMSA4 restringido a
   el caso en que los operandos así como los valores hash y salt son
   cadenas de octetos.

   La longitud de los mensajes en los que puede operar RSASSA-PSS es
   sin restricciones o limitadas por un número muy grande, dependiendo de la
   función hash subyacente al método de codificación EMSA-PSS.

   Suponiendo que calcular las raíces e-ésimas módulo n no es factible y que
   Las funciones de generación de hash y máscara en EMSA-PSS tienen las características adecuadas
   propiedades, RSASSA-PSS proporciona firmas seguras. Esta garantía es
   demostrable en el sentido de que la dificultad de falsificar firmas puede
   estar directamente relacionado con la dificultad de invertir la función RSA,
   siempre que las funciones de generación de hash y máscara se consideren como
   Cajas negras u oráculos aleatorios. Los límites de la prueba de seguridad son
   Esencialmente "ajustado", lo que significa que la probabilidad de éxito y la ejecución
   El momento del mejor falsificador contra RSASSA-PSS está muy cerca.
   parámetros correspondientes para el mejor algoritmo de inversión RSA; ver
   [RSARABIN] [PSSPROOF] [JONSSON] para mayor discusión.

   A diferencia del esquema de firma RSASSA-PKCS1-v1_5, un hash
   El identificador de función no está integrado en el mensaje codificado EMSA-PSS.
   Así que, en teoría, es posible que un adversario sustituya un



Moriarty, et al. Informativo [Página 32]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   función hash diferente (y potencialmente más débil) que la
   seleccionada por el firmante. Por lo tanto, se RECOMIENDA que el
   La función de generación de máscara EMSA-PSS se basará en la misma función hash.
   De esta manera, todo el mensaje codificado dependerá de la
   función hash, y será difícil para un oponente sustituirla
   una función hash diferente a la prevista por el firmante. Esta
   La coincidencia de funciones hash tiene como único fin evitar el hash.
   sustitución de función y no es necesaria si la función hash
   La sustitución se aborda por otros medios (por ejemplo, el verificador acepta
   sólo una función hash designada). Ver [HASHID] para más información
   Discusión de estos puntos. La seguridad demostrable de RSASSA-PSS no
   no confíe en la función hash en la función de generación de máscara.
   Lo mismo que la función hash aplicada al mensaje.

   RSASSA-PSS es diferente de otros esquemas de firma basados ​​en RSA en
   que es probabilístico en lugar de determinista, incorporando una
   Valor de sal generado aleatoriamente. El valor de sal mejora la seguridad.
   del plan al proporcionar una prueba de seguridad "más estricta" que
   alternativas deterministas como Full Domain Hashing (FDH); ver
   [RSARABIN] para discusión. Sin embargo, la aleatoriedad no es crítica.
   para la seguridad. En situaciones en las que no es posible la generación aleatoria,
   Se podría emplear en su lugar un valor fijo o un número de secuencia, con
   La seguridad demostrable resultante es similar a la de FDH [FDH].

8.1.1. Operación de generación de firma

   SIGNO RSASSA-PSS (K, M)

   Aporte:

      Clave privada RSA del firmante K
      M mensaje a firmar, una cadena de octetos

   Producción:

      Firma S, una cadena de octetos de longitud k, donde k es la
               longitud en octetos del módulo RSA n

   Errores: "mensaje demasiado largo"; "error de codificación"

   Pasos:

      1. Codificación EMSA-PSS: Aplicar la operación de codificación EMSA-PSS
          (Sección 9.1.1) al mensaje M para producir un mensaje codificado
          EM de longitud \ceil ((modBits - 1)/8) octetos tal que el bit
          La longitud del entero OS2IP (EM) (ver Sección 4.2) es como máximo
          modBits - 1, donde modBits es la longitud en bits del RSA
          módulo n:



Moriarty, et al. Informativo [Página 33]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


             EM = EMSA-PSS-CODIFICACIÓN (M, modBits - 1).

          Tenga en cuenta que la longitud del octeto de EM será uno menos que k si
          modBits - 1 es divisible por 8 y es igual a k en caso contrario. Si
          La operación de codificación genera "mensaje demasiado largo".
          "mensaje demasiado largo" y se detiene. Si la operación de codificación
          emite "error de codificación", emite "error de codificación" y se detiene.

      2. Firma RSA:

          a. Convertir el mensaje codificado EM en un mensaje entero
              representante m (ver Sección 4.2):

                 m = OS2IP (EM).

          b. Aplique la primitiva de firma RSASP1 (Sección 5.2.1) a
              la clave privada RSA K y el representante del mensaje m a
              Producir un representante de firma entera s:

                 s = RSASP1 (K, m).

          c. Convertir el representante de firma s en una firma S de
              longitud k octetos (ver Sección 4.1):

                 S = I2OSP(s, k).

      3. Imprima la firma S.

8.1.2. Operación de verificación de firma

   RSASSA-PSS-VERIFICAR ((n, e), M, S)

   Aporte:

      (n, e) clave pública RSA del firmante
      M mensaje cuya firma se va a verificar, una cadena de octetos
      Firma S a verificar, una cadena de octetos de longitud k,
              donde k es la longitud en octetos del módulo RSA n

   Salida: "firma válida" o "firma no válida"

   Pasos:

      1. Comprobación de longitud: Si la longitud de la firma S no es k
          octetos, salida "firma inválida" y parada.






Moriarty, et al. Informativo [Página 34]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      2. Verificación RSA:

          a. Convertir la firma S en una firma entera
              Representantes (véase la sección 4.2):

                 s = OS2IP (S).

          b. Aplique la primitiva de verificación RSAVP1 (Sección 5.2.2) a
              la clave pública RSA (n, e) y el representante de la firma
              s para producir un mensaje entero representativo m:

                 m = RSAVP1 ((n, e), s).

              Si la salida RSAVP1 indica "representante de firma fuera de rango",
              salida "firma inválida" y se detiene.

          c. Convertir el representante del mensaje m en un mensaje codificado
              EM de longitud emLen = \ceil ((modBits - 1)/8) octetos, donde
              modBits es la longitud en bits del módulo RSA n (ver
              Sección 4.1):

                 EM = I2OSP (m, emLen).

              Tenga en cuenta que emLen será uno menos que k si modBits - 1 es
              divisible por 8 e igual a k en caso contrario. Si I2OSP genera
              "entero demasiado grande", salida "firma no válida" y se detiene.

      3. Verificación EMSA-PSS: Aplicar la verificación EMSA-PSS
          operación (Sección 9.1.2) al mensaje M y al codificado
          mensaje EM para determinar si son consistentes:

             Resultado = EMSA-PSS-VERIFY (M, EM, modBits - 1).

      4. Si Resultado = "consistente", salida "firma válida".
          De lo contrario, muestra "firma no válida".

8.2.RSASSA-PKCS1-v1_5

   RSASSA-PKCS1-v1_5 combina las primitivas RSASP1 y RSAVP1 con la
   Método de codificación EMSA-PKCS1-v1_5. Es compatible con el estándar IFSSA.
   esquema definido en IEEE 1363 [IEEE1363], donde la firma y
   Las primitivas de verificación son IFSP-RSA1 e IFVP-RSA1, y el mensaje
   El método de codificación es EMSA-PKCS1-v1_5 (que no está definido en IEEE 1363)
   pero está en IEEE 1363a [IEEE1363A]).

   La longitud de los mensajes en los que puede operar RSASSA-PKCS1-v1_5 es
   ya sea sin restricciones o restringidas por un número muy grande, dependiendo
   sobre la función hash subyacente al método EMSA-PKCS1-v1_5.



Moriarty, et al. Informativo [Página 35]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Suponiendo que calcular las raíces e-ésimas módulo n no es factible y que
   La función hash en EMSA-PKCS1-v1_5 tiene propiedades apropiadas,
   Se supone que RSASSA-PKCS1-v1_5 proporciona firmas seguras. Más
   Precisamente, falsificar firmas sin conocer la clave privada RSA es
   Se conjetura que es computacionalmente inviable. Además, en la codificación
   método EMSA-PKCS1-v1_5, se incorpora un identificador de función hash en el
   codificación. Debido a esta característica, un adversario que intente encontrar una
   El mensaje con la misma firma que un mensaje firmado previamente debe
   encontrar colisiones de la función hash particular que se esté utilizando; atacar
   una función hash diferente a la seleccionada por el firmante no es
   útil para el adversario. Véase [HASHID] para más información.

   Nota: Como se indica en PKCS #1 v1.5, el método de codificación EMSA-PKCS1-v1_5
   tiene la propiedad de que el mensaje codificado, convertido a un entero
   Se garantiza que el representante del mensaje sea grande y al menos
   algo "aleatorio". Esto evita ataques del tipo propuesto por
   Desmedt y Odlyzko [ELEGIDO] donde las relaciones multiplicativas
   entre los representantes de mensajes se desarrollan factorizando la
   representantes de mensajes en un conjunto de valores pequeños (por ejemplo, un conjunto de
   primos pequeños). Coron, Naccache y Stern [PADDING] demostraron que un
   Una forma más fuerte de este tipo de ataque podría ser bastante efectiva contra
   Algunos ejemplos del esquema de firma ISO/IEC 9796-2. También
   analizó la complejidad de este tipo de ataques contra el
   Método de codificación EMSA-PKCS1-v1_5 y concluyó que un ataque sería
   poco práctico, ya que requiere más operaciones que una búsqueda de colisión en el
   función hash subyacente (es decir, más de 2^80 operaciones).
   Posteriormente, Coppersmith, Halevi y Jutla [FALSIFICACIÓN] ampliaron Coron
   El ataque de et al. para romper el esquema de firma ISO/IEC 9796-1 con
   recuperación de mensajes. Los diversos ataques ilustran la importancia de
   construyendo cuidadosamente la entrada a la primitiva de firma RSA,
   particularmente en un esquema de firma con recuperación de mensajes.
   En consecuencia, el método de codificación EMSA-PKCS-v1_5 incluye explícitamente una
   operación hash y no está pensada para esquemas de firma con mensaje
   recuperación. Además, aunque no se conoce ningún ataque contra el
   Método de codificación EMSA-PKCS-v1_5, una transición gradual a EMSA-PSS es
   Recomendado como medida de precaución ante futuros desarrollos.

8.2.1. Operación de generación de firma

   RSASSA-PKCS1-V1_5-SIGNO (K, M)

   Aporte:

      Clave privada RSA del firmante K
      M mensaje a firmar, una cadena de octetos






Moriarty, et al. Informativo [Página 36]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Producción:

      Firma S, una cadena de octetos de longitud k, donde k es la
               longitud en octetos del módulo RSA n

   Errores: "mensaje demasiado largo"; "módulo RSA demasiado corto"

   Pasos:

      1. Codificación EMSA-PKCS1-v1_5: aplique la codificación EMSA-PKCS1-v1_5
          operación (Sección 9.2) al mensaje M para producir un código
          mensaje EM de longitud k octetos:

             EM = EMSA-PKCS1-V1_5-CODIFICAR (M, k).

          Si la operación de codificación genera "mensaje demasiado largo", salida
          "mensaje demasiado largo" y se detiene. Si la operación de codificación
          salidas "longitud del mensaje codificado previsto demasiado corta", salida
          "Módulo RSA demasiado corto" y se detiene.

      2. Firma RSA:

          a. Convertir el mensaje codificado EM en un mensaje entero
              representante m (ver Sección 4.2):

                 m = OS2IP (EM).

          b. Aplique la primitiva de firma RSASP1 (Sección 5.2.1) a
              la clave privada RSA K y el representante del mensaje m a
              Producir un representante de firma entera s:

                 s = RSASP1 (K, m).

          c. Convertir el representante de firma s en una firma S de
              longitud k octetos (ver Sección 4.1):

                 S = I2OSP(s, k).

      3. Imprima la firma S.

8.2.2. Operación de verificación de firma

   RSASSA-PKCS1-V1_5-VERIFICAR ((n, e), M, S)

   Aporte:

      (n, e) clave pública RSA del firmante
      M mensaje cuya firma se va a verificar, una cadena de octetos



Moriarty, et al. Informativo [Página 37]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      Firma S a verificar, una cadena de octetos de longitud k,
              donde k es la longitud en octetos del módulo RSA n

   Salida "firma válida" o "firma no válida"

   Errores: "mensaje demasiado largo"; "módulo RSA demasiado corto"

   Pasos:

      1. Comprobación de longitud: Si la longitud de la firma S no es k
          octetos, salida "firma inválida" y parada.

      2. Verificación RSA:

          a. Convertir la firma S en una firma entera
              Representantes (véase la sección 4.2):

                 s = OS2IP (S).

          b. Aplique la primitiva de verificación RSAVP1 (Sección 5.2.2) a
              la clave pública RSA (n, e) y el representante de la firma
              s para producir un mensaje entero representativo m:

                 m = RSAVP1 ((n, e), s).

              Si RSAVP1 genera el mensaje "representante de firma fuera de rango",
              salida "firma inválida" y se detiene.

          c. Convertir el representante del mensaje m en un mensaje codificado
              EM de longitud k octetos (ver Sección 4.1):

                 EM = I2OSP(m,k).

              Si I2OSP genera "entero demasiado grande", genera "número inválido"
              firma" y parar.

      3. Codificación EMSA-PKCS1-v1_5: aplique la codificación EMSA-PKCS1-v1_5
          operación (Sección 9.2) al mensaje M para producir un segundo
          mensaje codificado EM' de longitud k octetos:

             EM' = EMSA-PKCS1-V1_5-CODIFICAR (M, k).

          Si la operación de codificación genera "mensaje demasiado largo", salida
          "mensaje demasiado largo" y se detiene. Si la operación de codificación
          salidas "longitud del mensaje codificado previsto demasiado corta", salida
          "Módulo RSA demasiado corto" y se detiene.





Moriarty, et al. Informativo [Página 38]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      4. Compare el mensaje codificado EM y el segundo mensaje codificado
          EM'. Si son iguales, muestra "firma válida";
          De lo contrario, mostrará "firma inválida".

      Nota: Otra forma de implementar la verificación de firma
      La operación consiste en aplicar una operación de "decodificación" (no especificada en
      este documento) al mensaje codificado para recuperar el subyacente
      valor hash y luego compararlo con un valor hash recién calculado.
      Esto tiene la ventaja de que requiere menos almacenamiento intermedio.
      (dos valores hash en lugar de dos mensajes codificados), pero el
      desventaja que requiere código adicional.

9. Métodos de codificación para firmas con apéndice

   Los métodos de codificación consisten en operaciones que se asignan entre cadenas de octetos.
   mensajes y mensajes codificados en cadenas de octetos, que se convierten a
   y de representantes de mensajes enteros en los esquemas. El entero
   Los representantes de mensajes se procesan a través de los primitivos.
   Los métodos de codificación proporcionan así la conexión entre los esquemas,
   que procesan los mensajes y los primitivos.

   Un método de codificación para firmas con apéndice, a los efectos de
   Este documento consta de una operación de codificación y opcionalmente una
   operación de verificación. Una operación de codificación asigna un mensaje M a un
   mensaje codificado EM de una longitud especificada. Una operación de verificación
   determina si un mensaje M y un mensaje codificado EM son
   consistente, es decir, si el mensaje codificado EM es una codificación válida
   del mensaje M.

   La operación de codificación puede introducir cierta aleatoriedad, de modo que
   Diferentes aplicaciones de la operación de codificación para el mismo mensaje
   producirá diferentes mensajes codificados, lo que tiene beneficios para
   seguridad demostrable. Para un método de codificación de este tipo, tanto una codificación como
   Se necesita una operación de verificación a menos que el verificador pueda reproducir
   la aleatoriedad (por ejemplo, obteniendo el valor de sal del firmante).
   Para un método de codificación determinista, solo se realiza una operación de codificación.
   necesario.

   En el presente documento se emplean dos métodos de codificación para firmas con apéndice.
   Los esquemas de firma se especifican aquí: EMSA-PSS y
   EMSA-PKCS1-v1_5.










Moriarty, et al. Informativo [Página 39]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


9.1. Sistema de alerta temprana de emergencia (PSS)

   Este método de codificación está parametrizado por la elección de la función hash,
   Función de generación de máscara y longitud de sal. Estas opciones deberían ser
   fijo para una clave RSA dada, excepto que la longitud de la sal puede ser
   variable (ver [JONSSON] para más información). Hash y máscara sugeridos
   Las funciones de generación se dan en el Apéndice B. El método de codificación es
   Basado en el esquema de firma probabilística (PSS) de Bellare y Rogaway
   [RSARABIN][PSS]. Es aleatorio y tiene una operación de codificación y
   una operación de verificación.

   La figura 2 ilustra la operación de codificación.

      __________________________________________________________________

                                     +----------+
                                     |YO|
                                     +----------+
                                           |
                                           V
                                         Picadillo
                                           |
                                           V
                             +--------+----------+----------+
                        M' = |Padding1| mHash | sal |
                             +--------+----------+----------+
                                            |
                  +--------+----------+ V
            DB = |Padding2| sal | Hash
                  +--------+----------+ |
                            | |
                            V |
                           xor <---MGF <---|
                            | |
                            | |
                            VV
                  +-------------------+----------+--+
            EM = | enmascaradoDB | H |bc|
                  +-------------------+----------+--+
      __________________________________________________________________

   Figura 2: Operación de codificación EMSA-PSS

   Tenga en cuenta que la operación de verificación sigue pasos inversos para recuperarse.
   sal y luego avanza pasos para recalcular y comparar H.






Moriarty, et al. Informativo [Página 40]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Notas:

   1. El método de codificación definido aquí difiere del de Bellare.
       y la presentación de Rogaway a IEEE 1363a [PSS] en tres aspectos:

       * Aplica una función hash en lugar de una generación de máscara.
          función al mensaje. Aunque la generación de máscara
          La función se basa en una función hash, parece más natural
          aplicar una función hash directamente.

       * El valor que se combina con el valor de sal es el
          cadena (0x)00 00 00 00 00 00 00 00 || mHash en lugar de
          mensaje M en sí. Aquí, mHash es el hash de M. Tenga en cuenta que
          La función hash es la misma en ambos pasos. Véase la nota 3 a continuación.
          para mayor discusión. (Además, se utiliza el nombre "sal"
          en lugar de "semilla", ya que refleja mejor el valor
          role.)

       * El mensaje codificado en EMSA-PSS tiene nueve bits fijos; el primero
          El bit es 0 y los últimos ocho bits forman un "campo final", el
          Octeto 0xbc. En el esquema original, solo el primer bit es
          arreglado. La razón para el campo del tráiler es
          compatibilidad con la firma de factorización entera
          Primitivo que utiliza Rabin-Williams (IFSP-RW) en IEEE 1363
          [IEEE1363] y la primitiva correspondiente en ISO/IEC
          Norma ISO 9796-2:2010.

   2. Suponiendo que la función de generación de máscara se basa en un hash
       función, se RECOMIENDA que la función hash sea la misma que
       el que se aplica al mensaje; consulte la Sección 8.1 para
       más discusión.

   3. Sin comprometer la prueba de seguridad de RSASSA-PSS, uno puede
       Realice los pasos 1 y 2 de EMSA-PSS-ENCODE y EMSA-PSS-VERIFY (el
       aplicación de la función hash al mensaje) fuera de la
       módulo que calcula el resto de la operación de firma, de modo que
       Se ingresa al módulo mHash en lugar del mensaje M en sí.
       En otras palabras, la prueba de seguridad de RSASSA-PSS aún se mantiene.
       Incluso si un oponente puede controlar el valor de mHash, esto es
       Es conveniente si el módulo tiene un ancho de banda de E/S limitado, por ejemplo, un módulo inteligente.
       Tarjeta. Tenga en cuenta que las versiones anteriores de PSS [RSARABIN][PSS] no
       tienen esta propiedad. Por supuesto, puede ser deseable para otros
       razones de seguridad para que el módulo procese el mensaje completo.
       Por ejemplo, el módulo puede necesitar "ver" lo que está firmando si
       No confía en el componente que calcula el valor hash.






Moriarty, et al. Informativo [Página 41]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   4. Las longitudes de sal típicas en octetos son hLen (la longitud de la salida)
       de la función hash Hash) y 0. En ambos casos, la seguridad de
       RSASSA-PSS puede estar estrechamente relacionado con la dureza de la inversión
       RSAVP1. Bellare y Rogaway [RSARABIN] dan un límite inferior estricto
       para la seguridad del esquema RSA-PSS original, que
       corresponde aproximadamente al caso anterior, mientras que Coron [FDH] da una
       límite inferior para el esquema de hash de dominio completo relacionado, que
       corresponde aproximadamente al último caso. En [PSSPROOF], Coron
       Proporciona un tratamiento general con varias longitudes de sal que varían
       de 0 a hLen; consulte [IEEE1363A] para obtener más información. Consulte también
       [JONSSON], que adapta las pruebas de seguridad en [RSARABIN]
       [PSSPROOF] para abordar las diferencias entre el original y
       la versión actual de RSA-PSS tal como se indica en la Nota 1 anterior.

   5. Como se señala en IEEE 1363a [IEEE1363A], el uso de aleatorización en
       Los esquemas de firma, como el valor de sal en EMSA-PSS, pueden
       proporcionar un "canal encubierto" para transmitir información a otros
       que el mensaje que se está firmando. Para obtener más información sobre los canales encubiertos, consulte
       [SIMMONS].

9.1.1. Operación de codificación

   EMSA-PSS-CODIFICACIÓN (M, emBits)

   Opciones:

      Función hash (hLen denota la longitud en octetos de
               la salida de la función hash)
      Función de generación de máscara MGF
      sLen longitud prevista en octetos de la sal

   Aporte:

      Mensaje M a codificar, cadena de octetos
      emBits longitud máxima en bits del entero OS2IP (EM) (ver Sección
               4.2), al menos 8hLen + 8sLen + 9

   Producción:

      Mensaje codificado EM, una cadena de octetos de longitud emLen = \ceil
               (bits/8)

   Errores: "Error de codificación"; "mensaje demasiado largo"








Moriarty, et al. Informativo [Página 42]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Pasos:

      1. Si la longitud de M es mayor que la limitación de entrada para
           la función hash (2^61 - 1 octetos para SHA-1), salida
           "Mensaje demasiado largo" y parar.

      2. Sea mHash = Hash(M), una cadena de octetos de longitud hLen.

      3. Si emLen < hLen + sLen + 2, muestra "error de codificación" y se detiene.

      4. Genere una sal de cadena de octetos aleatoria de longitud sLen; si sLen =
           0, entonces la sal es la cadena vacía.

      5. Dejar

              M' = (0x)00 00 00 00 00 00 00 00 || mHash || sal;

           M' es una cadena de octetos de longitud 8 + hLen + sLen con ocho
           octetos cero iniciales.

      6. Sea H = Hash(M'), una cadena de octetos de longitud hLen.

      7. Genere una cadena de octetos PS que consta de emLen - sLen - hLen
           - 2 octetos cero. La longitud de PS puede ser 0.

      8. Sea DB = PS || 0x01 || sal; DB es una cadena de octetos de longitud
           emLen-hLen-1.

      9. Sea dbMask = MGF(H, emLen - hLen - 1).

      10. Sea maskedDB = DB \xor dbMask.

      11. Establezca los bits 8emLen - emBits más a la izquierda del octeto más a la izquierda
           en maskedDB a cero.

      12. Sea EM = maskedDB || H || 0xbc.

      13. Salida EM.













Moriarty, et al. Informativo [Página 43]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


9.1.2. Operación de verificación

   EMSA-PSS-VERIFICAR (M, EM, emBits)

   Opciones:

      Función hash (hLen denota la longitud en octetos de
               la salida de la función hash)
      Función de generación de máscara MGF
      sLen longitud prevista en octetos de la sal

   Aporte:

      Mensaje M a verificar, una cadena de octetos
      Mensaje codificado EM, una cadena de octetos de longitud emLen = \ceil
               (bits/8)
      emBits longitud máxima en bits del entero OS2IP (EM) (ver Sección
               4.2), al menos 8hLen + 8sLen + 9

   Salida: "consistente" o "inconsistente"

   Pasos:

      1. Si la longitud de M es mayor que la limitación de entrada para
           la función hash (2^61 - 1 octetos para SHA-1), salida
           "inconsistente" y parar.

      2. Sea mHash = Hash(M), una cadena de octetos de longitud hLen.

      3. Si emLen < hLen + sLen + 2, muestra "inconsistente" y se detiene.

      4. Si el octeto más a la derecha de EM no tiene valor hexadecimal
           0xbc, salida "inconsistente" y se detiene.

      5. Sea maskedDB el octeto emLen - hLen - 1 más a la izquierda de EM,
           y sean H los siguientes hLen octetos.

      6. Si los bits 8emLen - emBits más a la izquierda del octeto más a la izquierda en
           maskedDB no son todos iguales a cero, salida "inconsistente" y
           detener.

      7. Sea dbMask = MGF(H, emLen - hLen - 1).

      8. Sea DB = maskedDB \xor dbMask.

      9. Establezca los bits 8emLen - emBits más a la izquierda del octeto más a la izquierda
           en DB a cero.




Moriarty, et al. Informativo [Página 44]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


      10. Si los octetos más a la izquierda emLen - hLen - sLen - 2 de DB no son
           cero o si el octeto en la posición emLen - hLen - sLen - 1 (el
           La posición más a la izquierda es "posición 1") no tiene formato hexadecimal.
           valor 0x01, salida "inconsistente" y se detiene.

      11. Sea sal el último sLen octetos de DB.

      12. Dejar

              M' = (0x)00 00 00 00 00 00 00 00 || mHash || sal ;

           M' es una cadena de octetos de longitud 8 + hLen + sLen con ocho
           octetos cero iniciales.

      13. Sea H' = Hash(M'), una cadena de octetos de longitud hLen.

      14. Si H = H', salida "consistente". En caso contrario, salida
           "inconsistente".

9.2. EMSA-PKCS1-v1_5

   Este método de codificación es determinista y solo tiene una codificación
   operación.

   EMSA-PKCS1-v1_5-CODIFICACIÓN (M, longitud del em)

   Opción:

      Función hash (hLen denota la longitud en octetos de
               la salida de la función hash)

   Aporte:

      M mensaje a codificar
      emLen longitud prevista en octetos del mensaje codificado, en
               menos tLen + 11, donde tLen es la longitud del octeto
               Reglas de codificación distinguidas (DER) que codifican T de
               un cierto valor calculado durante la operación de codificación

   Producción:

      Mensaje codificado EM, una cadena de octetos de longitud emLen

   Errores: "mensaje demasiado largo"; "longitud del mensaje codificado previsto demasiado larga"
      corto"






Moriarty, et al. Informativo [Página 45]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Pasos:

      1. Aplique la función hash al mensaje M para producir un hash
          valor H:

             H = Hash(M).

          Si la función hash genera "mensaje demasiado largo", salida
          "Mensaje demasiado largo" y parar.

      2. Codifique el ID del algoritmo para la función hash y el hash
          valor en un valor ASN.1 de tipo DigestInfo (ver
          Apéndice A.2.4) con el DER, donde el tipo DigestInfo tiene
          La sintaxis

               DigestInfo::= SECUENCIA {
                   algoritmo de digestión algoritmo identificador,
                   Digerir CADENA DE OCTETOS
               }

          El primer campo identifica la función hash y el segundo
          contiene el valor hash. Sea T la codificación DER del
          Valor DigestInfo (ver las notas a continuación) y sea tLen el
          longitud en octetos de T.

      3. Si emLen < tLen + 11, salida "longitud de mensaje codificado deseada"
          demasiado corto" y parar.

      4. Genere una cadena de octetos PS que consta de emLen - tLen - 3
          octetos con valor hexadecimal 0xff. La longitud de PS será
          al menos 8 octetos.

      5. Concatene PS, la codificación DER T y otros rellenos para formar
          el mensaje codificado EM como

             EM = 0x00 || 0x01 || PS || 0x00 || T.

      6. Salida EM.













Moriarty, et al. Informativo [Página 46]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Notas:

   1. Para las nueve funciones hash mencionadas en el Apéndice B.1, el DER
       La codificación T del valor DigestInfo es igual a lo siguiente:

         MD2: (0x)30 20 30 0c 06 08 2a 86 48 86 f7 0d 02 02 05 00 04
                      10 || O.
         MD5: (0x)30 20 30 0c 06 08 2a 86 48 86 f7 0d 02 05 05 00 04
                      10 || O.
         SHA-1: (0x)30 21 30 09 06 05 2b 0e 03 02 1a 05 00 04 14 ||
         SHA-224: (0x)30 2d 30 0d 06 09 60 86 48 01 65 03 04 02 04
                      05 00 04 1c || H.
         SHA-256: (0x)30 31 30 0d 06 09 60 86 48 01 65 03 04 02 01 05 00
                      04 20 || H.
         SHA-384: (0x)30 41 30 0d 06 09 60 86 48 01 65 03 04 02 02 05 00
                      04 30 || H.
         SHA-512: (0x)30 51 30 0d 06 09 60 86 48 01 65 03 04 02 03 05 00
                      04 40 || H.
         SHA-512/224: (0x)30 2d 30 0d 06 09 60 86 48 01 65 03 04 02 05
                           05 00 04 1c || H.
         SHA-512/256: (0x)30 31 30 0d 06 09 60 86 48 01 65 03 04 02 06
                           05 00 04 20 || H.

   2. En la versión 1.5 de este documento, T se definió como la BER
       codificación, en lugar de la codificación DER, del valor DigestInfo.
       En particular, es posible, al menos en teoría, que la
       operación de verificación definida en este documento (así como en
       versión 2.0) rechaza una firma que es válida con respecto a
       la especificación dada en PKCS #1 v1.5. Esto ocurre si otros
       Se aplican reglas distintas a las de DER a DigestInfo (por ejemplo, un indefinido
       codificación de longitud del tipo de SECUENCIA subyacente). Si bien esto es
       Es poco probable que sea una preocupación en la práctica, pero un implementador cauteloso puede
       optar por emplear una operación de verificación basada en una decodificación BER
       operación como se especifica en PKCS #1 v1.5. De esta manera,
       compatibilidad con cualquier implementación válida basada en PKCS #1 v1.5
       Se obtiene dicha operación de verificación. Dicha operación de verificación debe indicar
       si la codificación BER subyacente es una codificación DER y, por lo tanto
       Si la firma es válida con respecto a la especificación
       dado en este documento.

10. Consideraciones de seguridad

   A lo largo de este memorando se analizan consideraciones de seguridad.








Moriarty, et al. Informativo [Página 47]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


11. Referencias

11.1 Referencias normativas

   [GARNER] Garner, H., "El sistema de numeración de residuos", IRE Transactions
              sobre Computadoras Electrónicas, Volumen EC-8, Número 2, págs.
              140-147, DOI 10.1109/TEC.1959.5219515, junio de 1959.

   [RFC2119] Bradner, S., "Palabras clave para usar en RFC para indicar
              Niveles de requisitos", BCP 14, RFC 2119,
              DOI 10.17487/RFC2119, marzo de 1997,
              <http://www.rfc-editor.org/info/rfc2119>.

   [RSA] Rivest, R., Shamir, A. y L. Adleman, "Un método para
              Obtención de firmas digitales y claves públicas
              Criptosistemas", Comunicaciones de la ACM, Volumen 21,
              Número 2, págs. 120-126, DOI 10.1145/359340.359342, febrero
              1978.

11.2. Referencias informativas

   [ANSIX944] ANSI, "Establecimiento de claves mediante factorización de enteros"
              Criptografía", ANSI X9.44-2007, agosto de 2007.

   [BKS] Bleichenbacher, D., Kaliski, B. y J. Staddon, "Reciente
              Resultados sobre PKCS #1: Estándar de cifrado RSA, RSA
              Laboratorios, Boletín No. 7, junio de 1998.

   [Bleichenbacher]
              Bleichenbacher, D., "Ataques de texto cifrado elegido contra
              Protocolos basados ​​en el estándar de cifrado RSA PKCS #1",
              Apuntes de clases sobre informática, volumen 1462, págs. 1-12,
              1998.

   [SELECCIONADO] Desmedt, Y. y A. Odlyzko, "Un ataque de texto elegido a la
              Criptosistema RSA y algunos esquemas de logaritmos discretos",
              Apuntes de clases de informática, volumen 218, pp.
              516-522, 1985.

   [COCHRAN] Cochran, M., "Notas sobre el ensayo SHA-1 de Wang et al. 2^63
              Archivo de ePrints de Criptología: Ruta diferencial
              2007/474, agosto de 2008, <http://eprint.iacr.org/2007/474>.

   [FASTDEC] Quisquater, J. y C. Couvreur, "Desciframiento rápido
              Algoritmo para el criptosistema de clave pública RSA", Electronic
              Cartas, Volumen 18, Número 21, págs. 905-907,
              DOI 10.1049/el:19820617, octubre de 1982.




Moriarty, et al. Informativo [Página 48]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   [FDH] Coron, J., "Sobre la seguridad exacta del hash de dominio completo",
              Apuntes de clases de informática, volumen 1880, pp.
              229-235, 2000.

   [FOPS] Fujisaki, E., Okamoto, T., Pointcheval, D. y J. Stern,
              "RSA-OAEP es seguro según el supuesto RSA", conferencia
              Notas de informática, volumen 2139, págs. 260-274,
              Agosto de 2001.

   [FALSIFICACIÓN] Coppersmith, D., Halevi, S. y C. Jutla, "ISO 9796-1 y
              La nueva estrategia de falsificación", sesión de fin de semana de Crypto, agosto
              1999.

   [HAASTAD] Haastad, J., "Resolución de ecuaciones modulares simultáneas de
              Grado bajo", Revista SIAM sobre Computación, Volumen 17,
              Número 2, págs. 336-341, DOI 10.1137/0217019, abril de 1988.

   [MANUAL] Menezes, A., van Oorschot, P. y S. Vanstone, "Manual
              de criptografía aplicada", CRC Press, ISBN: 0849385237,
              1996.

   [HASHID] Kaliski, B., "Sobre los firewalls de función hash en la firma
              Esquemas", Apuntes de clase en informática, Volumen 2271,
              págs. 1-16, DOI 10.1007/3-540-45760-7_1, febrero de 2002.

   [IEEE1363] IEEE, "Especificaciones estándar para claves públicas
              Criptografía", IEEE Std 1363-2000,
              DOI 10.1109/IEEESTD.2000.92292, agosto de 2000,
              <http://ieeexplore.ieee.org/document/891000/>.

   [IEEE1363A]
              IEEE, "Especificaciones estándar para criptografía de clave pública"
              - Enmienda 1: Técnicas adicionales", IEEE Std 1363a-
              2004, DOI 10.1109/IEEESTD.2004.94612, septiembre de 2004,
              <http://ieeexplore.ieee.org/document/1335427/>.

   [ISO18033] Organización Internacional de Normalización,
              "Tecnología de la información -- Técnicas de seguridad --
              Algoritmos de cifrado - Parte 2: Cifrados asimétricos", ISO/
              IEC 18033-2:2006, mayo de 2006.

   [ISO9594] Organización Internacional de Normalización,
              "Tecnología de la información - Interconexión de sistemas abiertos -
              El Directorio: Certificado de clave pública y de atributos
              marcos de referencia", ISO/IEC 9594-8:2008, diciembre de 2008.






Moriarty, et al. Informativo [Página 49]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   [ISO9796] Organización Internacional de Normalización,
              "Tecnologías de la información - Técnicas de seguridad - Digital
              Esquemas de firma que permiten la recuperación de mensajes - Parte 2:
              Mecanismos basados ​​en factorización de enteros",
              ISO/IEC 9796-2:2010, diciembre de 2010.

   [JONSSON] Jonsson, J., "Pruebas de seguridad para la firma RSA-PSS"
              Esquema y sus variantes", Criptología ePrint
              Archivo: Informe 2001/053, marzo de 2002,
              <http://eprint.iacr.org/2001/053>.

   [LOWEXP] Calderero, D., Franklin, M., Patarin, J. y M. Reiter,
              "RSA de bajo exponente con mensajes relacionados", notas de clase en
              Ciencias de la Computación, Volumen 1070, págs. 1-9, 1996.

   [MANGER] Manger, J., "Un ataque de texto cifrado elegido en RSA Optimal
              Relleno de cifrado asimétrico (OAEP) según lo estandarizado en
              PKCS #1 v2.0", Apuntes de clase sobre informática, volumen
              2139, págs. 230-238, DOI 10.1007/3-540-44647-8_14, 2001.

   [MD4] Dobbertin, H., "Criptoanálisis de MD4", Notas de clase en
              Ciencias de la Computación, Volumen 1039, págs. 53-69,
              DOI 10.1007/3-540-60865-6_43, 1996.

   [MD4FIRST] Dobbertin, H., "Las dos primeras rondas de MD4 no son únicas".
              Camino", Apuntes de clase en Ciencias de la Computación, Volumen 1372, págs.
              284-292, DOI 10.1007/3-540-69710-1_19, marzo de 1998.

   [MD4LAST] den Boer, B. y A. Bosselaers, "Un ataque a los dos últimos
              Rondas de MD4", Apuntes de clase en informática, volumen
              576, págs. 194-203, DOI 10.1007/3-540-46766-1_14, 1992.

   [NUEVO ATAQUE]
              Coron, J., Joye, M., Naccache, D. y P. Paillier, "Nuevo
              Ataques al cifrado PKCS #1 v1.5", Notas de clase en
              Ciencias de la Computación, Volumen 1807, págs. 369-381,
              DOI 10.1007/3-540-45539-6_25, mayo de 2000.

   [OAEP] Bellare, M. y P. Rogaway, "Cifrado asimétrico óptimo"
              - Cómo cifrar con RSA", Apuntes de clase en Informática
              Ciencia, Volumen 950, págs. 92-111, noviembre de 1995.

   [PA98] Bellare, M., Desai, A., Pointcheval, D. y P. Rogaway,
              "Relaciones entre nociones de seguridad para claves públicas
              Esquemas de cifrado", Apuntes de clase sobre informática
              Science, Volumen 1462, págs. 26-45, DOI 10.1007/BFb0055718,
              1998.




Moriarty, et al. Informativo [Página 50]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   [RELLENO] Coron, J., Naccache, D. y J. Stern, "Sobre la seguridad de
              Relleno RSA", Apuntes de clase en informática, volumen
              1666, págs. 1-18, DOI 10.1007/3-540-48405-1_1, diciembre
              1999.

   [PKCS1_22] RSA Laboratories, "PKCS #1: Estándar de criptografía RSA
              Versión 2.2", octubre de 2012.

   [PREFIX] Stevens, M., Lenstra, A. y B. de Weger, "Prefijo elegido"
              colisiones para MD5 y aplicaciones", Internacional
              Revista de criptografía aplicada, volumen 2, núm. 4, págs.
              322-359, julio de 2012.

   [PSS] Bellare, M. y P. Rogaway, "PSS: codificación demostrablemente segura
              Método para firmas digitales", Presentación a IEEE P1363a,
              Agosto de 1998, <http://grouper.ieee.org/groups/1363/
              P1363a/contribuciones/pss-submission.pdf>.

   [PSSPROOF] Coron, J., "Pruebas de seguridad óptimas para PSS y otros
              Esquemas de firma", apuntes de clase sobre informática
              Ciencia, Volumen 2332, págs. 272-287,
              DOI 10.1007/3-540-46035-7_18, 2002.

   [RFC1319] Kaliski, B., "El algoritmo de resumen de mensajes MD2", RFC 1319,
              DOI 10.17487/RFC1319, abril de 1992,
              <http://www.rfc-editor.org/info/rfc1319>.

   [RFC1321] Rivest, R., "El algoritmo de resumen de mensajes MD5", RFC 1321,
              DOI 10.17487/RFC1321, abril de 1992,
              <http://www.rfc-editor.org/info/rfc1321>.

   [RFC2313] Kaliski, B., "PKCS #1: Cifrado RSA versión 1.5",
              RFC 2313, DOI 10.17487/RFC2313, marzo de 1998,
              <http://www.rfc-editor.org/info/rfc2313>.

   [RFC2315] Kaliski, B., "PKCS #7: Sintaxis de mensajes criptográficos
              Versión 1.5", RFC 2315, DOI 10.17487/RFC2315, marzo de 1998,
              <http://www.rfc-editor.org/info/rfc2315>.

   [RFC2437] Kaliski, B. y J. Staddon, "PKCS #1: Criptografía RSA
              Especificaciones Versión 2.0", RFC 2437,
              DOI 10.17487/RFC2437, octubre de 1998,
              <http://www.rfc-editor.org/info/rfc2437>.

   [RFC3447] Jonsson, J. y B. Kaliski, "Criptografía de clave pública"
              Estándares (PKCS) n.° 1: Especificaciones de criptografía RSA
              Versión 2.1", RFC 3447, DOI 10.17487/RFC3447, febrero
              2003, <http://www.rfc-editor.org/info/rfc3447>.



Moriarty, et al. Informativo [Página 51]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   [RFC5246] Dierks, T. y E. Rescorla, "La seguridad de la capa de transporte
              (TLS) Versión 1.2 del protocolo", RFC 5246,
              DOI 10.17487/RFC5246, agosto de 2008,
              <http://www.rfc-editor.org/info/rfc5246>.

   [RFC5652] Housley, R., "Sintaxis de mensajes criptográficos (CMS)", STD 70,
              RFC 5652, DOI 10.17487/RFC5652, septiembre de 2009,
              <http://www.rfc-editor.org/info/rfc5652>.

   [RFC5958] Turner, S., "Paquetes de claves asimétricas", RFC 5958,
              DOI 10.17487/RFC5958, agosto de 2010,
              <http://www.rfc-editor.org/info/rfc5958>.

   [RFC6149] Turner, S. y L. Chen, "MD2 a estado histórico",
              RFC 6149, DOI 10.17487/RFC6149, marzo de 2011,
              <http://www.rfc-editor.org/info/rfc6149>.

   [RFC7292] Moriarty, K., Ed., Nystrom, M., Parkinson, S., Rusch, A.,
              y M. Scott, "PKCS #12: Intercambio de información personal
              Sintaxis v1.1", RFC 7292, DOI 10.17487/RFC7292, julio de 2014,
              <http://www.rfc-editor.org/info/rfc7292>.

   [RSARABIN] Bellare, M. y P. Rogaway, "La seguridad exacta de la información digital"
              Firmas - Cómo firmar con RSA y Rabin", Conferencia
              Notas de informática, volumen 1070, págs. 399-416,
              DOI 10.1007/3-540-68339-9_34, 1996.

   [RSATLS] Jonsson, J. y B. Kaliski, "Sobre la seguridad de RSA
              Cifrado en TLS", Apuntes de clase en Informática
              Ciencia, Volumen 2442, págs. 127-142,
              DOI 10.1007/3-540-45708-9_9, 2002.

   [Cifrado SHA1]
              Wang, X., Yao, A. y F. Yao, "Criptoanálisis en SHA-1",
              Apuntes de clases de informática, volumen 2442, pp.
              127-142, febrero de 2005,
              <http://csrc.nist.gov/groups/ST/hash/documents/
              Wang_SHA1-Nuevo-Resultado.pdf>.

   [SHOUP] Shoup, V., "OAEP reconsiderada (resumen ampliado)",
              Apuntes de clases de informática, volumen 2139, pp.
              239-259, DOI 10.1007/3-540-44647-8_15, 2001.

   [SHS] Instituto Nacional de Estándares y Tecnología, "Secure
              Estándar Hash (SHS)", FIPS PUB 180-4, agosto de 2015,
              <http://dx.doi.org/10.6028/NIST.FIPS.180-4>.





Moriarty, et al. Informativo [Página 52]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   [EL HOMBRE DE PLATA]
              Silverman, R., "Un análisis de seguridad basado en costos de
              Longitudes de clave simétricas y asimétricas, RSA
              Laboratorios, Boletín No. 13, 2000.

   [SIMMONS] Simmons, G., "La comunicación subliminal es fácil usando el
              DSA", Apuntes de clase en Ciencias de la Computación, Volumen 765, págs.
              218-232, DOI 10.1007/3-540-48285-7_18, 1994.











































Moriarty, et al. Informativo [Página 53]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


Apéndice A. Sintaxis ASN.1

A.1. Representación de claves RSA

   Esta sección define los identificadores de objetos ASN.1 para RSA públicos y
   claves privadas y define los tipos RSAPublicKey y RSAPrivateKey.
   La aplicación prevista de estas definiciones incluye X.509
   certificados, PKCS #8 [RFC5958] y PKCS #12 [RFC7292].

   El identificador de objeto rsaEncryption identifica RSA público y privado.
   claves como se definen en los Apéndices A.1.1 y A.1.2. El campo de parámetros
   se ha asociado con este OID en un valor de tipo AlgorithmIdentifier
   DEBE tener un valor de tipo NULL.

      rsaEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 1 }

   Las definiciones de esta sección se han ampliado para admitir múltiples
   Prime RSA, pero son compatibles con versiones anteriores.

A.1.1. Sintaxis de clave pública RSA

   Una clave pública RSA debe representarse con el tipo ASN.1
   Clave pública RSAP:

         RSAPublicKey ::= SECUENCIA {
             módulo ENTERO, -- n
             publicExponent ENTERO -- e
         }

   Los campos de tipo RSAPublicKey tienen los siguientes significados:

   El módulo o es el módulo RSA n.

   o publicExponent es el exponente público RSA e.

















Moriarty, et al. Informativo [Página 54]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


A.1.2. Sintaxis de clave privada RSA

   Una clave privada RSA debe representarse con el tipo ASN.1
   Clave privada RSAPrivate:

         RSAPrivateKey ::= SECUENCIA {
             versión Versión,
             módulo ENTERO, -- n
             publicExponent ENTERO, -- e
             Exponenteprivado ENTERO, -- d
             primo1 ENTERO, -- p
             prime2 ENTERO, -- q
             exponente1 ENTERO, -- d mod (p-1)
             exponente2 ENTERO, -- d mod (q-1)
             coeficiente ENTERO, -- (inverso de q) mod p
             otherPrimeInfos OtherPrimeInfos OPCIONAL
         }

   Los campos de tipo RSAPrivateKey tienen los siguientes significados:

   o version es el número de versión, para compatibilidad con futuras
      revisiones de este documento. DEBE ser 0 para esta versión del
      documento, a menos que se utilicen múltiples primes; en cuyo caso, SERÁ
      1.

            Versión::= ENTERO { dos primos(0), multi(1) }
               (LIMITADO POR
               {-- la versión debe ser múltiple si hay otras PrimeInfos presentes --})

   El módulo o es el módulo RSA n.

   o publicExponent es el exponente público RSA e.

   o privateExponent es el exponente privado RSA d.

   o prime1 es el factor primo p de n.

   o prime2 es el factor primo q de n.

   o exponente1 es d mod (p - 1).

   o exponente2 es d mod (q - 1).

   El coeficiente o es el coeficiente CRT q^(-1) mod p.







Moriarty, et al. Informativo [Página 55]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   o otherPrimeInfos contiene la información de los primos adicionales
      r_3, ..., r_u, en orden. DEBE omitirse si la versión es 0 y
      DEBE contener al menos una instancia de OtherPrimeInfo si la versión
      es 1.

            OtherPrimeInfos ::= TAMAÑO DE SECUENCIA(1..MÁXIMO) DE OtherPrimeInfo

            OtherPrimeInfo ::= SECUENCIA {
                entero primo, -- ri
                exponente ENTERO, -- di
                coeficiente ENTERO -- ti
            }

   Los campos de tipo OtherPrimeInfo tienen los siguientes significados:

   o primo es un factor primo r_i de n, donde i >= 3.

   El exponente es d_i = d mod (r_i - 1).

   o coeficiente es el coeficiente CRT t_i = (r_1 * r_2 * ... *
      r_(i-1))^(-1) módulo r_i.

   Nota: Es importante proteger la clave privada RSA contra ambos
   divulgación y modificación. Las técnicas para dicha protección son
   fuera del alcance de este documento. Métodos de almacenamiento y
   Se describe la distribución de claves privadas y otros datos criptográficos.
   en PKCS #12 y #15.
























Moriarty, et al. Informativo [Página 56]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


A.2. Identificación del esquema

   Esta sección define los identificadores de objetos para el cifrado y
   esquemas de firma. Los esquemas compatibles con PKCS #1 v1.5 tienen la
   Las mismas definiciones que en PKCS #1 v1.5. La aplicación prevista de
   Estas definiciones incluyen certificados X.509 y PKCS #7.

   A continuación se muestran las definiciones de identificadores de tipo para los OID PKCS n.° 1:

   Algoritmos PKCS1 IDENTIFICADOR DE ALGORITMO ::= {
       { OID rsaEncryption PARÁMETROS NULL } |
       { OID md2WithRSAEncryption PARÁMETROS NULL } |
       { OID md5WithRSAEncryption PARÁMETROS NULL } |
       { OID sha1WithRSAEncryption PARÁMETROS NULL } |
       { OID sha224WithRSAEncryption PARÁMETROS NULOS } |
       { OID sha256WithRSAEncryption PARÁMETROS NULOS } |
       { OID sha384WithRSAEncryption PARÁMETROS NULL } |
       { OID sha512WithRSAEncryption PARÁMETROS NULOS } |
       { OID sha512-224WithRSAEncryption PARÁMETROS NULL } |
       { OID sha512-256WithRSAEncryption PARÁMETROS NULOS } |
       { OID id-RSAES-OAEP PARÁMETROS RSAES-OAEP-params } |
       Algoritmos de origen PKCS1P |
       { OID id-RSASSA-PSS PARÁMETROS RSASSA-PSS-params },
       ... -- Permite expansión futura --
   }

A.2.1. RSAES-OAEP

   El identificador de objeto id-RSAES-OAEP identifica el RSAES-OAEP
   esquema de cifrado.

       id-RSAES-OAEP IDENTIFICADOR DE OBJETO ::= { pkcs-1 7 }

   El campo de parámetros asociado a este OID en un valor de tipo
   AlgorithmIdentifier DEBE tener un valor de tipo RSAES-OAEP-params:

   Parámetros RSAES-OAEP::= SECUENCIA {
       hashAlgorithm [0] HashAlgorithm PREDETERMINADO sha1,
       maskGenAlgorithm [1] MaskGenAlgorithm PREDETERMINADO mgf1SHA1,
       pSourceAlgorithm [2] PSourceAlgorithm PREDETERMINADO pSpecifiedEmpty
   }

   Los campos de tipo RSAES-OAEP-params tienen los siguientes significados:

   o hashAlgorithm identifica la función hash. DEBE ser una
      Identificador de algoritmo con un OID en el conjunto OAEP-PSSDigestAlgorithms. Para
      Para una discusión de las funciones hash admitidas, consulte el Apéndice B.1.




Moriarty, et al. Informativo [Página 57]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


       AlgoritmoHash::= IdentificadorAlgoritmo {
          {Algoritmos OAEP-PSSDigest}
       }

       OAEP-PSSDigestAlgorithms IDENTIFICADOR DE ALGORITMO ::= {
           { OID id-sha1 PARÁMETROS NULOS }|
           { OID id-sha224 PARÁMETROS NULOS }|
           { OID id-sha256 PARÁMETROS NULOS }|
           { OID id-sha384 PARÁMETROS NULOS }|
           { OID id-sha512 PARÁMETROS NULOS }|
           { OID id-sha512-224 PARÁMETROS NULOS }|
           { OID id-sha512-256 PARÁMETROS NULOS },
           ... -- Permite expansión futura --
       }

   La función hash predeterminada es SHA-1:

       Algoritmo hash sha1 ::= {
           algoritmo id-sha1,
           parámetros SHA1Parameters: NULL
       }

       Parámetros SHA1::= NULL

   o maskGenAlgorithm identifica la función de generación de máscara.
      DEBE ser un ID de algoritmo con un OID en el conjunto
      Algoritmos PKCS1MGFA, que para esta versión DEBERÁN consistir en
      id-mgf1, que identifica la función de generación de máscara MGF1 (ver
      Apéndice B.2.1). El campo de parámetros asociado con id-mgf1
      DEBE ser un ID de algoritmo con un OID en el conjunto
      OAEP-PSSDigestAlgorithms, que identifica la función hash en la que se basa
      Se basa en MGF1.

       MaskGenAlgorithm ::= Identificador de algoritmo { {PKCS1MGFAlgorithms} }

       PKCS1MGFAlgorithms IDENTIFICADOR DE ALGORITMO ::= {
           { OID id-mgf1 PARÁMETROS Algoritmo Hash },
           ... -- Permite expansión futura --
       }

   o La función de generación de máscara predeterminada es MGF1 con SHA-1:

       Algoritmo de generación de máscaras mgf1SHA1 ::= {
           algoritmo id-mgf1,
           parámetros Algoritmo hash: sha1
       }





Moriarty, et al. Informativo [Página 58]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   o pSourceAlgorithm identifica la fuente (y posiblemente el valor) de
      la etiqueta L. DEBE ser un ID de algoritmo con un OID en el conjunto
      PKCS1PSourceAlgorithms, que para esta versión DEBERÁN consistir en
      id-pSpecified, indica que la etiqueta se especifica explícitamente.
      El campo de parámetros asociado con id-pSpecified DEBE tener un
      valor de tipo OCTET STRING, que contiene la etiqueta. En el ejemplo anterior
      En las versiones de esta especificación, el término "parámetros de codificación" se utilizó
      se utiliza en lugar de "etiqueta", de ahí el nombre del tipo a continuación.

       AlgoritmoPSource ::= IdentificadorAlgoritmo {
          {Algoritmos de origen PKCS1}
       }

       PKCS1PSourceAlgorithms IDENTIFICADOR DE ALGORITMO ::= {
           { OID id-pEspecificado PARÁMETROS Parámetros de codificación },
           ... -- Permite expansión futura --
       }

       id-pSpecified IDENTIFICADOR DE OBJETO ::= { pkcs-1 9 }

       Parámetros de codificación::= OCTET STRING(SIZE(0..MAX))

   o La etiqueta predeterminada es una cadena vacía (para que lHash contenga
      el hash de la cadena vacía):

       pSpecifiedEmpty Algoritmo de origen P ::= {
           algoritmo id-pSpecified,
           parámetros EncodingParameters : cadena vacía
       }

       Parámetros de codificación de cadena vacía ::= ''H

   Si todos los valores predeterminados de los campos en RSAES-OAEP-params son
   utilizado, entonces el identificador del algoritmo tendrá el siguiente valor:

       Identificador predeterminado rSAES-OAEP Identificador de algoritmo RSAES ::= {
           algoritmo id-RSAES-OAEP,
           parámetros RSAES-OAEP-params : {
               algoritmo hash sha1,
               algoritmo maskGen mgf1SHA1,
               pSourceAlgorithm pSpecifiedEmpty
           }
       }

       Identificador de algoritmo RSAES ::= Identificador de algoritmo {
           {Algoritmos PKCS1}
       }




Moriarty, et al. Informativo [Página 59]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


A.2.2.RSAES-PKCS-v1_5

   El identificador de objeto rsaEncryption (ver Apéndice A.1) identifica el
   Esquema de cifrado RSAES-PKCS1-v1_5. El campo de parámetros asociado
   con este OID en un valor de tipo AlgorithmIdentifier DEBE tener un
   Valor de tipo NULL. Es lo mismo que en PKCS #1 v1.5.

       rsaEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 1 }

A.2.3. RSASSA-PSS

   El identificador de objeto id-RSASSA-PSS identifica el RSASSA-PSS
   esquema de cifrado.

       id-RSASSA-PSS IDENTIFICADOR DE OBJETO ::= { pkcs-1 10 }

   El campo de parámetros asociado a este OID en un valor de tipo
   AlgorithmIdentifier DEBE tener un valor de tipo RSASSA-PSS-params:

   Parámetros RSASSA-PSS::= SECUENCIA {
       hashAlgorithm [0] HashAlgorithm PREDETERMINADO sha1,
       maskGenAlgorithm [1] MaskGenAlgorithm PREDETERMINADO mgf1SHA1,
       saltLength [2] ENTERO PREDETERMINADO 20,
       trailerField [3] TrailerField PREDETERMINADO trailerFieldBC
   }

   Los campos de tipo RSASSA-PSS-params tienen los siguientes significados:

   o hashAlgorithm identifica la función hash. DEBE ser una
      ID de algoritmo con un OID en el conjunto OAEP-PSSDigestAlgorithms (ver
      Apéndice A.2.1). La función hash predeterminada es SHA-1.

   o maskGenAlgorithm identifica la función de generación de máscara.
      DEBE ser un identificador de algoritmo con un OID en el conjunto PKCS1MGFAlgorithms
      (ver Apéndice A.2.1). La función de generación de máscara predeterminada es
      MGF1 con SHA-1. Para MGF1 (y más generalmente, para otras máscaras)
      funciones de generación basadas en una función hash), se RECOMIENDA
      que la función hash subyacente sea la misma que la
      identificado por hashAlgorithm; consulte la Nota 2 en la Sección 9.1 para obtener más información.
      comentarios.

   o saltLength es la longitud del octeto de la sal. DEBE ser un
      entero. Para un algoritmo hash determinado, el valor predeterminado es
      saltLength es la longitud en octeto del valor hash. A diferencia de
      otros campos de tipo RSASSA-PSS-params, saltLength no necesita
      debe corregirse para un par de claves RSA determinado.





Moriarty, et al. Informativo [Página 60]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   o trailerField es el número del campo del tráiler, para compatibilidad con
      IEEE 1363a [IEEE1363A]. DEBE ser 1 para esta versión de la
      documento, que representa el campo del tráiler con formato hexadecimal
      valor 0xbc. Otros campos de tráiler (incluido el campo de tráiler)
      HashID || 0xcc en IEEE 1363a) no son compatibles con este documento.

       TrailerField ::= ENTERO { trailerFieldBC(1) }

   Si los valores predeterminados de hashAlgorithm, maskGenAlgorithm y
   Se utilizan los campos trailerField de RSASSA-PSS-params, luego el algoritmo
   El identificador tendrá el siguiente valor:

       Identificador predeterminado de rSASSA-PSS Identificador de algoritmo de RSASSA ::= {
           algoritmo id-RSASSA-PSS,
           parámetros RSASSA-PSS-params : {
               algoritmo hash sha1,
               algoritmo maskGen mgf1SHA1,
               salLongitud 20,
               trailerField trailerFieldBC
           }
       }

       Identificador de algoritmo RSASSA ::= Identificador de algoritmo {
           {Algoritmos PKCS1}
       }

   Nota: En algunas aplicaciones, la función hash subyacente a una firma
   El esquema se identifica por separado del resto de las operaciones en
   el esquema de firma. Por ejemplo, en PKCS #7 [RFC2315], un hash
   El identificador de función se coloca antes del mensaje y un "resumen"
   identificador del algoritmo de cifrado" (que indica el resto de la
   operaciones) se lleva con la firma. Para que PKCS #7
   Para soportar el esquema de firma RSASSA-PSS, un identificador de objeto sería
   Es necesario definirlo para las operaciones en RSASSA-PSS después del hash.
   función (análoga al OID RSAEncryption para el
   Esquema RSASSA-PKCS1-v1_5). Sintaxis de mensajes criptográficos S/MIME (CMS)
   [RFC5652] adopta un enfoque diferente. Aunque una función hash
   El identificador se coloca antes del mensaje, un identificador de algoritmo para
   El esquema de firma completo puede llevarse con una firma CMS (esta
   se realiza para firmas DSA). Siguiendo esta convención, el
   El OID id-RSASSA-PSS se puede utilizar para identificar firmas RSASSA-PSS en
   CMS. Dado que CMS se considera el sucesor de PKCS #7 y el nuevo
   Se realizarán avances como la incorporación de soporte para RSASSA-PSS.
   perseguido con respecto a CMS en lugar de PKCS #7, un OID para el "resto
   de" RSASSA-PSS no está definido en esta versión de PKCS #1.






Moriarty, et al. Informativo [Página 61]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


A.2.4.RSASSA-PKCS-v1_5

   El identificador de objeto para RSASSA-PKCS1-v1_5 DEBE ser uno de los
   Lo siguiente: La elección del OID depende de la elección del hash.
   algoritmo: MD2, MD5, SHA-1, SHA-224, SHA-256, SHA-384, SHA-512,
   SHA-512/224 o SHA-512/256. Tenga en cuenta que si se utiliza MD2 o MD5,
   Entonces el OID es igual que en PKCS #1 v1.5. Para cada OID, el
   campo de parámetros asociado con este OID en un valor de tipo
   AlgorithmIdentifier DEBE tener un valor de tipo NULL. El OID debe
   se elegirá de acuerdo con la siguiente tabla:

         OID del algoritmo hash
         ------------------------------------------------------------
         MD2 md2 con cifrado RSA ::= {pkcs-1 2}
         MD5 md5ConRSAEncryption ::= {pkcs-1 4}
         SHA-1 sha1 con cifrado RSA ::= {pkcs-1 5}
         SHA-256 sha224 con cifrado RSA ::= {pkcs-1 14}
         SHA-256 sha256ConCifradoRSA ::= {pkcs-1 11}
         SHA-384 sha384ConCifradoRSA ::= {pkcs-1 12}
         SHA-512 sha512ConCifradoRSA ::= {pkcs-1 13}
         SHA-512/224 sha512-224ConCifradoRSA ::= {pkcs-1 15}
         SHA-512/256 sha512-256ConCifradoRSA ::= {pkcs-1 16}

   El método de codificación EMSA-PKCS1-v1_5 incluye un valor ASN.1 de tipo
   DigestInfo, donde el tipo DigestInfo tiene la sintaxis

       DigestInfo::= SECUENCIA {
           Algoritmo de digestión Algoritmo de digestión,
           Digerir CADENA DE OCTETOS
       }

   digestAlgorithm identifica la función hash y DEBE ser un
   Identificador de algoritmo con un OID en el conjunto PKCS1-v1-5DigestAlgorithms. Para
   Para una discusión de las funciones hash admitidas, consulte el Apéndice B.1.

















Moriarty, et al. Informativo [Página 62]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


       AlgoritmoDigest ::= IdentificadorAlgoritmo {
          {Algoritmos de compendio PKCS1-v1-5}
       }

       Algoritmos de resumen PKCS1-v1-5 IDENTIFICADOR DE ALGORITMO ::= {
           { OID id-md2 PARÁMETROS NULOS }|
           { OID id-md5 PARÁMETROS NULOS }|
           { OID id-sha1 PARÁMETROS NULOS }|
           { OID id-sha224 PARÁMETROS NULOS }|
           { OID id-sha256 PARÁMETROS NULOS }|
           { OID id-sha384 PARÁMETROS NULOS }|
           { OID id-sha512 PARÁMETROS NULOS }|
           { OID id-sha512-224 PARÁMETROS NULOS }|
           { OID id-sha512-256 PARÁMETROS NULOS }
       }

Apéndice B. Técnicas de apoyo

   Esta sección ofrece varios ejemplos de funciones subyacentes.
   apoyando los esquemas de cifrado en la Sección 7 y la codificación
   métodos en la Sección 9. Aquí se ofrece una variedad de técnicas para permitir
   compatibilidad con aplicaciones existentes, así como migración a nuevas
   técnicas. Si bien estas técnicas de apoyo son apropiadas para
   aplicaciones para implementar, ninguna de ellas requiere ser
   Se espera que los perfiles para PKCS #1 v2.2 estén disponibles
   desarrollados que especifican técnicas de soporte particulares.

   Esta sección también proporciona identificadores de objetos para el soporte.
   Técnicas.

B.1. Funciones hash

   Las funciones hash se utilizan en las operaciones contenidas en las Secciones 7 y
   9. Las funciones hash son deterministas, lo que significa que la salida es
   completamente determinado por la entrada. Las funciones hash toman octeto
   cadenas de longitud variable y generar cadenas de octetos de longitud fija.
   Las funciones hash utilizadas en las operaciones contenidas en las Secciones 7 y
   9 debe ser, en general, resistente a colisiones. Esto significa que es
   No es factible encontrar dos entradas distintas a la función hash que
   produce el mismo resultado. Una función hash resistente a colisiones también
   tiene la propiedad deseable de ser unidireccional; esto significa que dado un
   salida, no es factible encontrar una entrada cuyo hash sea el especificado
   salida. Además de los requisitos, la función hash debe
   producir una función de generación de máscara (Apéndice B.2) con pseudoaleatorio
   producción.






Moriarty, et al. Informativo [Página 63]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Se dan nueve funciones hash como ejemplos de los métodos de codificación en
   Este documento: MD2 [RFC1319] (que fue retirado por [RFC6149]), MD5
   [RFC1321], SHA-1, SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224,
   y SHA-512/256 [SHS]. Para el esquema de cifrado RSAES-OAEP y
   Método de codificación EMSA-PSS, solo SHA-1, SHA-224, SHA-256, SHA-384, SHA-
   Se RECOMIENDAN 512, SHA-512/224 y SHA-512/256. Para la EMSA-
   Método de codificación PKCS1-v1_5, SHA-224, SHA-256, SHA-384, SHA-512, SHA-
   Se RECOMIENDAN 512/224 y SHA-512/256 para nuevas aplicaciones. MD2,
   MD5 y SHA-1 se recomiendan solo por compatibilidad con los existentes.
   aplicaciones basadas en PKCS #1 v1.5.

   Los identificadores de objeto id-md2, id-md5, id-sha1, id-sha224, id-sha256,
   id-sha384, id-sha512, id-sha512/224 e id-sha512/256 identifican el
   respectivas funciones hash:

       id-md2 IDENTIFICADOR DE OBJETO ::= {
           iso (1) organismo miembro (2) nosotros (840) rsadsi (113549)
           Algoritmo de digestión (2) 2
       }

       id-md5 IDENTIFICADOR DE OBJETO ::= {
           iso (1) organismo miembro (2) nosotros (840) rsadsi (113549)
           Algoritmo de digestión (2) 5
       }

       id-sha1 IDENTIFICADOR DE OBJETO ::= {
           iso(1) organización identificada(3) oiw(14) secsig(3)
            algoritmos(2) 26
       }

       id-sha224 IDENTIFICADOR DE OBJETO ::= {
           joint-iso-itu-t (2) país (16) eeuu (840) organización (1)
           gov (101) csor (3) algoritmo nistal (4) hashalgs (2) 4
       }

       id-sha256 IDENTIFICADOR DE OBJETO ::= {
           joint-iso-itu-t (2) país (16) eeuu (840) organización (1)
           gov (101) csor (3) algoritmo nistal (4) hashalgs (2) 1
       }

       id-sha384 IDENTIFICADOR DE OBJETO ::= {
           joint-iso-itu-t (2) país (16) eeuu (840) organización (1)
           gov (101) csor (3) algoritmo nistal (4) hashalgs (2) 2
       }







Moriarty, et al. Informativo [Página 64]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


       id-sha512 IDENTIFICADOR DE OBJETO ::= {
           joint-iso-itu-t (2) país (16) eeuu (840) organización (1)
           gov (101) csor (3) algoritmo nistal (4) hashalgs (2) 3
       }

       id-sha512-224 IDENTIFICADOR DE OBJETO ::= {
           joint-iso-itu-t (2) país (16) eeuu (840) organización (1)
           gov (101) csor (3) algoritmo nistal (4) hashalgs (2) 5
       }

       id-sha512-256 IDENTIFICADOR DE OBJETO ::= {
           joint-iso-itu-t (2) país (16) eeuu (840) organización (1)
           gov (101) csor (3) algoritmo nistal (4) hashalgs (2) 6
       }

   El campo de parámetros asociado a estos OID en un valor de tipo
   AlgorithmIdentifier DEBE tener un valor de tipo NULL.

   El campo de parámetros asociado con id-md2 e id-md5 en un valor de
   El tipo AlgorithmIdentifier debe tener un valor de tipo NULL.

   El campo de parámetros asociado con id-sha1, id-sha224, id-sha256,
   id-sha384, id-sha512, id-sha512/224 e id-sha512/256 deben
   Generalmente se omite, pero si está presente, tendrá un valor de tipo
   NULO.

   Esto es para alinearse con las definiciones promulgadas originalmente por el NIST.
   Para los algoritmos SHA, las implementaciones DEBEN aceptar
   Valores de AlgorithmIdentifier tanto sin parámetros como con NULL
   parámetros.

   Excepción: al formatear DigestInfoValue en EMSA-PKCS1-v1_5
   (ver Sección 9.2), el campo de parámetros asociado con id-sha1,
   id-sha224, id-sha256, id-sha384, id-sha512, id-sha512/224 y
   id-sha512/256 debe tener un valor de tipo NULL. Esto es para mantener
   compatibilidad con implementaciones existentes y con el sistema numérico
   valores de información ya publicados para EMSA-PKCS1-v1_5, que son
   También se refleja en IEEE 1363a [IEEE1363A].

   Nota: La versión 1.5 de PKCS #1 también permitía el uso de MD4 en
   esquemas de firma. El criptoanálisis de MD4 ha avanzado
   significativamente en los años intermedios. Por ejemplo, Dobbertin [MD4]
   demostró cómo encontrar colisiones para MD4 y que los dos primeros
   Las rondas de MD4 no son unidireccionales [MD4FIRST]. Debido a estos resultados
   y otros (por ejemplo, [MD4LAST]), MD4 NO SE RECOMIENDA.

   Se han logrado avances adicionales en el criptoanálisis de MD2 y MD5,
   especialmente después de los hallazgos de Stevens et al. [PREFIX] sobre los elegidos.



Moriarty, et al. Informativo [Página 65]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Colisiones de prefijos en MD5. Se deben tener en cuenta MD2 y MD5
   criptográficamente roto y eliminado de aplicaciones existentes.
   Esta versión del estándar admite MD2 y MD5 solo para versiones anteriores.
   razones de compatibilidad.

   También ha habido avances en el criptoanálisis de SHA-1.
   En particular, los resultados de Wang et al. [SHA1CRYPT] (que han
   sido verificado independientemente por M. Cochran en su análisis [COCHRAN])
   sobre el uso de una ruta diferencial para encontrar colisiones en SHA-1, que
   Concluimos que la fortaleza de seguridad del algoritmo hash SHA-1 es
   se redujo significativamente. Sin embargo, esta reducción no es significativa
   suficiente para justificar la eliminación de SHA-1 de las aplicaciones existentes,
   pero su uso solo se recomienda por compatibilidad con versiones anteriores
   razones.

   Para abordar estas inquietudes, solo SHA-224, SHA-256, SHA-384, SHA-512,
   Se RECOMIENDAN SHA-512/224 y SHA-512/256 para nuevas aplicaciones.
   A día de hoy, los ataques de colisión más conocidos contra estos hash
   Las funciones son ataques genéricos con complejidad 2L/2, donde L es el
   longitud en bits de la salida hash. Para los esquemas de firma en este
   Documento, un ataque de colisión se traduce fácilmente en una firma
   falsificación. Por lo tanto, el valor L/2 debe ser al menos igual al
   nivel de seguridad deseado en bits del esquema de firma (una seguridad
   El nivel de bits B significa que el mejor ataque tiene una complejidad 2B).
   La misma regla general se puede aplicar a RSAES-OAEP; se RECOMIENDA
   que la longitud de bits de la semilla (que es igual a la longitud de bits de
   la salida hash) sea el doble del nivel de seguridad deseado en bits.

B.2 Funciones de generación de máscaras

   Una función de generación de máscara toma una cadena de octetos de longitud variable
   y una longitud de salida deseada como entrada y genera una cadena de octetos de
   la longitud deseada. Puede haber restricciones en la longitud de la
   cadenas de octetos de entrada y salida, pero dichos límites son generalmente muy
   grande. Las funciones de generación de máscaras son deterministas; la cadena de octetos
   La salida está completamente determinada por la cadena de octetos de entrada.
   La salida de una función de generación de máscara debe ser pseudoaleatoria: Dado
   una parte de la salida pero no de la entrada, no debería ser factible
   predecir otra parte de la salida. La seguridad demostrable de
   RSAES-OAEP y RSASSA-PSS se basan en la naturaleza aleatoria de la salida.
   de la función de generación de máscara, que a su vez se basa en la aleatoriedad
   naturaleza del hash subyacente.

   Aquí se proporciona una función de generación de máscara: MGF1, que se basa en una
   Función hash. MGF1 coincide con las funciones de generación de máscaras.
   definido en IEEE 1363 [IEEE1363] y ANSI X9.44 [ANSIX944]. Futuro
   Las versiones de este documento pueden definir otras funciones de generación de máscaras.




Moriarty, et al. Informativo [Página 66]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


B.2.1.MGF1

   MGF1 es una función de generación de máscara basada en una función hash.

   MGF1 (mgfSeed, longitud de máscara)

   Opciones:

      Función hash (hLen denota la longitud en octetos de
               la salida de la función hash)

   Aporte:

      mgfSeed semilla a partir de la cual se genera la máscara, una cadena de octetos
      maskLen longitud prevista en octetos de la máscara, como máximo 2^32 hLen

   Producción:

      máscara máscara, una cadena de octetos de longitud maskLen

   Error: "máscara demasiado larga"

   Pasos:

   1. Si maskLen > 2^32 hLen, muestra "máscara demasiado larga" y se detiene.

   2. Sea T la cadena de octetos vacía.

   3. Para el contador de 0 a \ceil (maskLen / hLen) - 1, haga lo siguiente:
       siguiente:

       A. Convierte el contador en una cadena de octetos C de longitud 4 octetos (ver
           Sección 4.1):

              C = I2OSP (contador, 4).

       B. Concatenar el hash de la semilla mgfSeed y C al octeto
           cadena T:

              T = T || Hash(mgfSeed || C) .

   4. Imprima los octetos maskLen iniciales de T como la máscara de cadena de octetos.

   El identificador de objeto id-mgf1 identifica la generación de máscara MGF1
   función:

      id-mgf1 IDENTIFICADOR DE OBJETO ::= { pkcs-1 8 }




Moriarty, et al. Informativo [Página 67]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   El campo de parámetros asociado a este OID en un valor de tipo
   AlgorithmIdentifier deberá tener un valor de tipo hashAlgorithm,
   identificando la función hash en la que se basa MGF1.

Apéndice C. Módulo ASN.1

   -- Módulo PKCS #1 v2.2 ASN.1
   -- Revisado el 27 de octubre de 2012

   -- Se ha comprobado que este módulo cumple con las normas
   -- Estándar ASN.1 de OSS Herramientas ASN.1

   PKCS-1 {
       iso(1) cuerpo-miembro(2) us(840) rsadsi(113549) pkcs(1) pkcs-1(1)
       módulos(0) pkcs-1(1)
   }

   DEFINICIONES ETIQUETAS EXPLICITAS ::=

   COMENZAR

   --EXPORTACIONES TODO
   -- Todos los tipos y valores definidos en este módulo se exportan para su uso.
   -- en otros módulos ASN.1.

   IMPORTACIONES

   id-sha224, id-sha256, id-sha384, id-sha512, id-sha512-224,
   id-sha512-256
       DESDE NIST-SHA2 {
           joint-iso-itu-t(2) país(16) nosotros(840) organización(1)
           gov(101) csor(3) nistalgorithm(4) hashAlgs(2)
       };

   -- ============================
   -- Identificadores de objetos básicos
   -- ============================

   --La ​​codificación DER de esto en hexadecimal es:
   -- (0x)06 08
   -- 2A 86 48 86 F7 0D 01 01
   --
   pkcs-1 IDENTIFICADOR DE OBJETO ::= {
       iso(1) cuerpo-miembro(2) us(840) rsadsi(113549) pkcs(1) 1
   }

   --
   -- Cuando se utiliza rsaEncryption en un AlgorithmIdentifier,



Moriarty, et al. Informativo [Página 68]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   -- los parámetros DEBEN estar presentes y DEBEN ser NULOS.
   --
   rsaEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 1 }

   --
   -- Cuando se utiliza id-RSAES-OAEP en un AlgorithmIdentifier, el
   -- los parámetros DEBEN estar presentes y DEBEN ser RSAES-OAEP-params.
   --
   id-RSAES-OAEP IDENTIFICADOR DE OBJETO ::= { pkcs-1 7 }

   --
   -- Cuando se utiliza id-pSpecified en un AlgorithmIdentifier, el
   -- los parámetros DEBEN ser una CADENA DE OCTETOS.
   --
   id-pSpecified IDENTIFICADOR DE OBJETO ::= { pkcs-1 9 }

   --
   -- Cuando se utiliza id-RSASSA-PSS en un AlgorithmIdentifier, el
   -- los parámetros DEBEN estar presentes y DEBEN ser RSASSA-PSS-params.
   --
   id-RSASSA-PSS IDENTIFICADOR DE OBJETO ::= { pkcs-1 10 }

   --
   -- Cuando se utilizan los siguientes OID en un AlgorithmIdentifier,
   -- los parámetros DEBEN estar presentes y DEBEN ser NULOS.
   --
   md2WithRSAEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 2 }
   md5WithRSAEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 4 }
   sha1WithRSAEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 5 }
   sha224WithRSAEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 14 }
   sha256WithRSAEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 11 }
   sha384WithRSAEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 12 }
   sha512WithRSAEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 13 }
   sha512-224WithRSAEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 15 }
   sha512-256WithRSAEncryption IDENTIFICADOR DE OBJETO ::= { pkcs-1 16 }

   --
   -- Este OID realmente pertenece a un módulo con los OID secsig.
   --
   id-sha1 IDENTIFICADOR DE OBJETO ::= {
       iso(1) organización identificada(3) oiw(14) secsig(3) algoritmos(2)
       26
   }

   --
   -- OID para MD2 y MD5, permitidos solo en EMSA-PKCS1-v1_5.
   --
   id-md2 IDENTIFICADOR DE OBJETO ::= {



Moriarty, et al. Informativo [Página 69]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


       iso(1) cuerpo-miembro(2) us(840) rsadsi(113549) digestAlgorithm(2) 2
   }

   id-md5 IDENTIFICADOR DE OBJETO ::= {
       iso(1) miembro-cuerpo(2) us(840) rsadsi(113549) digestAlgorithm(2) 5
   }

   --
   -- Cuando se utiliza id-mgf1 en un AlgorithmIdentifier, los parámetros
   -- DEBE estar presente y DEBE ser un algoritmo hash, por ejemplo, sha1.
   --
   id-mgf1 IDENTIFICADOR DE OBJETO ::= { pkcs-1 8 }

   -- ================
   --Tipos útiles
   -- ================

   IDENTIFICADOR DE ALGORITMO::= CLASE {
       &id IDENTIFICADOR DE OBJETO ÚNICO,
       &Tipo OPCIONAL
   }
       CON SINTAXIS { OID &id [PARÁMETROS &Tipo] }

   -- Nota: el parámetro InfoObjectSet en las siguientes definiciones
   -- permite especificar un conjunto de objetos de información distintos para los conjuntos
   -- de algoritmos como:
   -- DigestAlgorithms IDENTIFICADOR DE ALGORITMO ::= {
   -- { OID id-md2 PARÁMETROS NULOS }|
   -- { OID id-md5 PARÁMETROS NULOS }|
   -- { OID id-sha1 PARÁMETROS NULOS }
   -- }
   --

   Identificador de algoritmo { IDENTIFICADOR-DE-ALGORITMO:InfoObjectSet } ::=
       SECUENCIA {
         algoritmo
             IDENTIFICADOR-DE-ALGORITMO.&id({InfoObjectSet}),
         parámetros
             IDENTIFICADOR DE ALGORITMO.&Tipo({InfoObjectSet}{@.algorithm})
               OPCIONAL
   }

   -- ==============
   -- Algoritmos
   -- ==============

   --
   --Se permiten los algoritmos de resumen EME-OAEP y EMSA-PSS.



Moriarty, et al. Informativo [Página 70]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   --
   OAEP-PSSDigestAlgorithms IDENTIFICADOR DE ALGORITMO ::= {
       { OID id-sha1 PARÁMETROS NULOS }|
       { OID id-sha224 PARÁMETROS NULOS }|
       { OID id-sha256 PARÁMETROS NULOS }|
       { OID id-sha384 PARÁMETROS NULOS }|
       { OID id-sha512 PARÁMETROS NULOS }|
       { OID id-sha512-224 PARÁMETROS NULOS }|
       { OID id-sha512-256 PARÁMETROS NULOS },
       ... -- Permite expansión futura --
   }

   --
   --Se permiten algoritmos de resumen EMSA-PKCS1-v1_5.
   --
   Algoritmos de resumen PKCS1-v1-5 IDENTIFICADOR DE ALGORITMO ::= {
       { OID id-md2 PARÁMETROS NULOS }|
       { OID id-md5 PARÁMETROS NULOS }|
       { OID id-sha1 PARÁMETROS NULOS }|
       { OID id-sha224 PARÁMETROS NULOS }|
       { OID id-sha256 PARÁMETROS NULOS }|
       { OID id-sha384 PARÁMETROS NULOS }|
       { OID id-sha512 PARÁMETROS NULOS }|
       { OID id-sha512-224 PARÁMETROS NULOS }|
       { OID id-sha512-256 PARÁMETROS NULOS }
   }

   -- Cuando se utilizan id-md2 e id-md5 en un AlgorithmIdentifier, el
   --El campo de parámetros debe tener un valor de tipo NULL.

   -- Cuando id-sha1, id-sha224, id-sha256, id-sha384, id-sha512,
   -- id-sha512-224 e id-sha512-256 se utilizan en un
   -- AlgorithmIdentifier, los parámetros (que son opcionales) DEBEN ser
   -- se omite, pero si está presente, DEBERÁ tener un valor de tipo NULL.
   -- Sin embargo, las implementaciones DEBEN aceptar valores de AlgorithmIdentifier
   -- tanto sin parámetros como con parámetros NULL.

   -- Excepción: al formatear DigestInfoValue en EMSA-PKCS1-v1_5
   -- (ver Sección 9.2), el campo de parámetros asociado con id-sha1,
   -- id-sha224, id-sha256, id-sha384, id-sha512, id-sha512-224 y
   -- id-sha512-256 DEBE tener un valor de tipo NULL. Esto es para
   -- mantener la compatibilidad con las implementaciones existentes y con las
   -- valores de información numérica ya publicados para EMSA-PKCS1-v1_5,
   -- que también se reflejan en IEEE 1363a.

   Algoritmo hash sha1 ::= {
       algoritmo id-sha1,
       parámetros SHA1Parameters: NULL



Moriarty, et al. Informativo [Página 71]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   }

   AlgoritmoHash::= IdentificadorAlgoritmo { {OAEP-PSSDigestAlgorithms} }

   Parámetros SHA1::= NULL

   --
   --Se permiten algoritmos de función de generación de máscaras.
   -- Si el identificador es id-mgf1, los parámetros son un algoritmo hash.
   --
   PKCS1MGFAlgorithms IDENTIFICADOR DE ALGORITMO ::= {
       { OID id-mgf1 PARÁMETROS Algoritmo Hash },
       ... -- Permite expansión futura --
   }

   --
   -- Identificador de algoritmo predeterminado para id-RSAES-OAEP.maskGenAlgorithm y
   -- id-RSASSA-PSS.maskGenAlgorithm.
   --
   Algoritmo de generación de máscaras mgf1SHA1 ::= {
       algoritmo id-mgf1,
       parámetros Algoritmo hash: sha1
   }

   MaskGenAlgorithm ::= Identificador de algoritmo { {PKCS1MGFAlgorithms} }

   --
   -- Algoritmos permitidos para pSourceAlgorithm.
   --
   PKCS1PSourceAlgorithms IDENTIFICADOR DE ALGORITMO ::= {
       { OID id-pEspecificado PARÁMETROS Parámetros de codificación },
       ... -- Permite expansión futura --
   }

   Parámetros de codificación::= OCTET STRING(SIZE(0..MAX))

   --
   -- Este identificador significa que la etiqueta L es una cadena vacía, por lo que
   -- el resumen de la cadena vacía aparece en el bloque RSA antes
   -- enmascaramiento.
   --

   pSpecifiedEmpty Algoritmo de origen P ::= {
       algoritmo id-pSpecified,
       parámetros EncodingParameters : cadena vacía
   }

   AlgoritmoPSource ::= IdentificadorAlgoritmo { {AlgoritmosPSourcePKCS1} }



Moriarty, et al. Informativo [Página 72]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Parámetros de codificación de cadena vacía ::= ''H

   --
   -- Definiciones de identificadores de tipo para los OID PKCS #1.
   --
   Algoritmos PKCS1 IDENTIFICADOR DE ALGORITMO ::= {
       { OID rsaEncryption PARÁMETROS NULL } |
       { OID md2WithRSAEncryption PARÁMETROS NULL } |
       { OID md5WithRSAEncryption PARÁMETROS NULL } |
       { OID sha1WithRSAEncryption PARÁMETROS NULL } |
       { OID sha224WithRSAEncryption PARÁMETROS NULOS } |
       { OID sha256WithRSAEncryption PARÁMETROS NULOS } |
       { OID sha384WithRSAEncryption PARÁMETROS NULL } |
       { OID sha512WithRSAEncryption PARÁMETROS NULOS } |
       { OID sha512-224WithRSAEncryption PARÁMETROS NULL } |
       { OID sha512-256WithRSAEncryption PARÁMETROS NULOS } |
       { OID id-RSAES-OAEP PARÁMETROS RSAES-OAEP-params } |
       Algoritmos de origen PKCS1P |
       { OID id-RSASSA-PSS PARÁMETROS RSASSA-PSS-params },
       ... -- Permite expansión futura --
   }

   -- ===================
   -- Estructuras principales
   -- ===================

   RSAPublicKey ::= SECUENCIA {
       módulo ENTERO, -- n
       publicExponent ENTERO -- e
   }

   --
   -- Representación de la clave privada RSA con información para el CRT
   -- algoritmo.
   --
   RSAPrivateKey ::= SECUENCIA {
       versión Versión,
       módulo ENTERO, -- n
       publicExponent ENTERO, -- e
       Exponenteprivado ENTERO, -- d
       primo1 ENTERO, -- p
       prime2 ENTERO, -- q
       exponente1 ENTERO, -- d mod (p-1)
       exponente2 ENTERO, -- d mod (q-1)
       coeficiente ENTERO, -- (inverso de q) mod p
       otherPrimeInfos OtherPrimeInfos OPCIONAL
   }




Moriarty, et al. Informativo [Página 73]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Versión::= ENTERO { dos primos(0), multi(1) }
       (LIMITADO POR
         {-- versión DEBE
    sea ​​múltiple si hay otras PrimeInfos presentes --})

   OtherPrimeInfos ::= TAMAÑO DE SECUENCIA(1..MÁXIMO) DE OtherPrimeInfo


   OtherPrimeInfo ::= SECUENCIA {
       entero primo, -- ri
       exponente ENTERO, -- di
       coeficiente ENTERO -- ti
   }

   --
   --AlgorithmIdentifier.parámetros para id-RSAES-OAEP.
   -- Tenga en cuenta que las etiquetas en esta secuencia son explícitas.
   --
   Parámetros RSAES-OAEP::= SECUENCIA {
       hashAlgorithm [0] HashAlgorithm PREDETERMINADO sha1,
       maskGenAlgorithm [1] MaskGenAlgorithm PREDETERMINADO mgf1SHA1,
       pSourceAlgorithm [2] PSourceAlgorithm PREDETERMINADO pSpecifiedEmpty
   }

   --
   -- Identificador del algoritmo RSAES-OAEP predeterminado.
   --La ​​codificación DER de esto está en hexadecimal:
   --(0x)30 0D
   -- 06 09
   -- 2A 86 48 86 F7 0D 01 01 07
   -- 30 00
   -- Tenga en cuenta que la codificación DER de los valores predeterminados está "vacía".
   --

   Identificador predeterminado rSAES-OAEP Identificador de algoritmo RSAES ::= {
       algoritmo id-RSAES-OAEP,
       parámetros RSAES-OAEP-params : {
           algoritmo hash sha1,
           algoritmo maskGen mgf1SHA1,
           pSourceAlgorithm pSpecifiedEmpty
       }
   }

   Identificador de algoritmo RSAES ::= Identificador de algoritmo {
       {Algoritmos PKCS1}
   }

   --



Moriarty, et al. Informativo [Página 74]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   --AlgorithmIdentifier.parámetros para id-RSASSA-PSS.
   -- Tenga en cuenta que las etiquetas en esta secuencia son explícitas.
   --
   Parámetros RSASSA-PSS::= SECUENCIA {
       hashAlgorithm [0] HashAlgorithm PREDETERMINADO sha1,
       maskGenAlgorithm [1] MaskGenAlgorithm PREDETERMINADO mgf1SHA1,
       saltLength [2] ENTERO PREDETERMINADO 20,
       trailerField [3] TrailerField PREDETERMINADO trailerFieldBC
   }

   TrailerField ::= ENTERO { trailerFieldBC(1) }

   --
   -- Identificador del algoritmo RSASSA-PSS predeterminado
   --La ​​codificación DER de esto está en hexadecimal:
   --(0x)30 0D
   -- 06 09
   -- 2A 86 48 86 F7 0D 01 01 0A
   -- 30 00
   -- Tenga en cuenta que la codificación DER de los valores predeterminados está "vacía".
   --
   Identificador predeterminado de rSASSA-PSS Identificador de algoritmo de RSASSA ::= {
       algoritmo id-RSASSA-PSS,
       parámetros RSASSA-PSS-params : {
           algoritmo hash sha1,
           algoritmo maskGen mgf1SHA1,
           salLongitud 20,
           trailerField trailerFieldBC
       }
   }

   Identificador de algoritmo RSASSA ::= Identificador de algoritmo {
       {Algoritmos PKCS1}
   }

   --
   -- Sintaxis para el identificador hash EMSA-PKCS1-v1_5.
   --
   DigestInfo::= SECUENCIA {
       Algoritmo de digestión Algoritmo de digestión,
       Digerir CADENA DE OCTETOS
   }

   AlgoritmoDigest ::= IdentificadorAlgoritmo {
       {Algoritmos de compendio PKCS1-v1-5}
   }

   FIN



Moriarty, et al. Informativo [Página 75]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


Apéndice D. Historial de revisiones de PKCS #1

   Versiones 1.0 - 1.5:

      Las versiones 1.0 a 1.3 se distribuyeron a los participantes en RSA Data
      Reuniones sobre estándares de criptografía de clave pública de Security, Inc. en
      Febrero y marzo de 1991.

      La versión 1.4 fue parte del lanzamiento público inicial del 3 de junio de 1991.
      PKCS. La versión 1.4 se publicó como Implementadores NIST/OSI
      Documento de taller SEC-SIG-91-18.

      La versión 1.5 incorporó varios cambios editoriales, incluidos
      actualizaciones de las referencias y la adición de un historial de revisiones.
      Se realizaron los siguientes cambios sustanciales:

      * Sección 10: Procesos de firma y verificación de “MD4 con RSA”
         fueron agregados.

      * Sección 11: se agregó el identificador de objeto md4WithRSAEncryption.

      La versión 1.5 se volvió a publicar como [RFC2313] (que más tarde se publicó
      obsoleto por [RFC2437]).

   Versión 2.0:

      La versión 2.0 incorporó importantes cambios editoriales en términos de
      Estructura del documento e introdujo el cifrado RSAES-OAEP
      esquema. Esta versión continuó admitiendo el cifrado y
      procesos de firma en la versión 1.5, aunque el algoritmo hash
      El MD4 ya no estaba permitido debido a los avances criptoanalíticos en el
      años intermedios. La versión 2.0 se volvió a publicar como [RFC2437]
      (que luego quedó obsoleto por [RFC3447]).

   Versión 2.1:

      La versión 2.1 introdujo el RSA multiprime y el RSASSA-PSS
      Esquema de firma con apéndice junto con varios editoriales
      Mejoras. Esta versión sigue dando soporte a los esquemas en
      Versión 2.0. La versión 2.1 se volvió a publicar como [RFC3447].











Moriarty, et al. Informativo [Página 76]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


   Versión 2.2:

      La versión 2.2 actualiza la lista de algoritmos hash permitidos a
      alinearlos con FIPS 180-4 [SHS], agregando así SHA-224,
      SHA-512/224 y SHA-512/256. Los siguientes cambios sustanciales
      fueron hechos:

      * Identificadores de objetos para sha224WithRSAEncryption,
         sha512-224 con cifrado RSA y sha512-256 con cifrado RSA
         fueron agregados.

      * Esta versión continúa admitiendo los esquemas de la versión 2.1.

Apéndice E. Acerca de PKCS

   Los estándares de criptografía de clave pública son especificaciones producidas por
   RSA Laboratories en colaboración con desarrolladores de sistemas seguros
   en todo el mundo con el fin de acelerar el despliegue de servicios públicos
   criptografía de claves. Publicada por primera vez en 1991 como resultado de reuniones
   Con un pequeño grupo de los primeros en adoptar la tecnología de clave pública,
   Los documentos PKCS se han vuelto ampliamente referenciados e implementados.
   Las contribuciones de la serie PKCS se han convertido en parte de muchos documentos formales.
   y estándares de facto, incluidos los documentos ANSI X9 e IEEE P1363,
   PKIX, Transacción Electrónica Segura (SET), S/MIME, SSL/TLS y
   Protocolo de aplicación inalámbrica (WAP) / Seguridad de la capa de transporte WAP
   (Ventajas).

   El desarrollo posterior de la mayoría de los documentos PKCS se lleva a cabo a través del IETF.
   Se aceptan sugerencias para mejorar.






















Moriarty, et al. Informativo [Página 77]

RFC 8017 PKCS #1 v2.2 Noviembre de 2016


Agradecimientos

   Este documento se basa en una contribución de RSA Laboratories,
   Centro de investigación de RSA Security Inc.

Direcciones de los autores

   Kathleen M. Moriarty (editora)
   Corporación EMC
   Calle Sur 176
   Hopkinton, Massachusetts 01748
   Estados Unidos de América

   Correo electrónico: kathleen.moriarty@emc.com


   Burt Kaliski
   Verisign
   12061 Camino Bluemont
   Reston, Virginia 20190
   Estados Unidos de América

   Correo electrónico: bkaliski@verisign.com
   URL: http://verisignlabs.com


   Jacob Jonsson
   Subconjunto AB
   Monstruo 4
   Estocolmo SE-11127
   Suecia

   Teléfono: +46 8 428 687 43
   Correo electrónico: jakob.jonsson@subset.se

   Andreas Rusch
   Sociedad Anónima
   Calle Reina 345
   Brisbane, Queensland 4000
   Australia

   Correo electrónico: andreas.rusch@rsa.com









Moriarty, et al. Informativo [Página 78]

