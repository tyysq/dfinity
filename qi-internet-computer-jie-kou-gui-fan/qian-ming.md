# 签名



数字签名方案用于在IC基础架构的各个部分中对消息进行身份验证。签名是域分隔的，这意味着每条消息都以一个唯一的字节字符串作为前缀，以达到这对于签名的目的。IC支持普通签名以及通过Web身份验证生成的签名。

* 支持纯签名方案
  * [Ed25519](https://ed25519.cr.yp.to/index.html)或
  * 使用SHA-256作为哈希函数的曲线P-256 [ECDSA](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.186-4.pdf)（也称为 secp256r1）以及Koblitz曲线上的 secp256k1

通过 对域分隔符和消息的联系进行签名，来计算签名。

* * 公钥必须对签名方案Ed25519或ECDSA有效，并且编码为DER。
    * 有关Ed25519公钥的DER编码，请参阅[RFC 8410](https://tools.ietf.org/html/rfc8410)。
    * 有关ECDSA公钥的DER编码，请参阅[RFC 5480](https://tools.ietf.org/rfc/rfc5480)；请参阅[RFC 5480](https://tools.ietf.org/rfc/rfc5480)。DER编码不得指定哈希函数。对于曲线secp256k1，使用OID 1.3.132.0.10。主要是必须指定以未压缩形式（也就是说 0x04随后的高位编址32字节编码x和y）。
  * 签名被编码为两个值_r_和_s_的32字节大字节序编码的连接。
* 只能通过Web身份验证的的签名方案
  * 使用SHA-256作为哈希函数的曲线P-256 [ECDSA](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.186-4.pdf)（也称为 secp256r1）以及Koblitz曲线上的 secp256k1

通过使用域分隔符和消息的连接作为Web验证断言中的Challenge来计算签名。

通过验证 challenge 字段是否包含域分隔符和消息的连接的base64url编码，并按照WebAuthn w3c建议中的规定进行signature 验证 authenticatorData · SHA-256\(utf8\(clientDataJSON\)\)，来检查签名。

* * 公用密钥被编码为DER封装的COSE密钥，如下所述。
  * 签名是具有三个必填字段的Map的CBOR编码：
    * authenticator\_data（blob）：WebAuthn身份验证器数据。
    * client\_data\_json（text）：JSON格式的WebAuthn客户端数据。
    * signature（blob）：[WebAuthn w3c建议中](https://www.w3.org/TR/webauthn/#signature-attestation-types)指定的签名，对于ECDSA签名来说这是DER编码。

DER包裹的COSE格式使用SubjectPublicKeyInfo类型，其他的公共密钥（例如，参见[RFC 8410，第4节](https://tools.ietf.org/html/rfc8410#section-4)），以及OID 1.3.6.1.4.1.56387.1.1（iso.org.dod.internet.private）。 enterprise.dfinity.mechanisms.der-wrapped-cose）。该BIT STRING字段subjectPublicKey包含COSE编码。有关COSE编码的详细信息，请参阅[WebAuthn w3c建议](https://www.w3.org/TR/webauthn/#sctn-encoded-credPubKey-examples)或[RFC 8152](https://tools.ietf.org/html/rfc8152#section-13.1)。

> 提示：

> A DER wrapping of a COSE key is shown below. It can be parsed via the command sed "s/\#.\*//" \| xxd -r -p \| openssl asn1parse -inform der.

> 30 5E \# 长度为94字节的序列

> 30 0C \# 长度为12个字节的序列

> 06 0A 2B 06 01 04 01 83 B8 43 01 01 \# OID 1.3.6.1.4.1.56387.1.1

> 03 4E 00 \# 长度为78的BIT STRING编码,

> A501 0203 2620 0121 5820 7FFD 8363 2072 ＃ 长度位于字节边界

> FD1B FEAF 3FBA A431 46E0 EF95 C3F5 5E39 \# 内容是验证过的COSE密钥

> 94A4 1BBF 2B51 74D7 71DA 2258 2032 497E \# ECDSA在曲线P-256 上

> ED0A 7F6F 0009 2876 5B83 1816 2CFD 80A9

> 4E52 5A6A 368C 2363 063D 04E6 ED

> 您还可以在[在线ASN.1 JavaScript解码器](https://lapo.it/asn1js/#MF4wDAYKKwYBBAGDuEMBAQNOAKUBAgMmIAEhWCB__YNjIHL9G_6vP7qkMUbg75XD9V45lKQbvytRdNdx2iJYIDJJfu0Kf28ACSh2W4MYFiz9gKlOUlpqNowjYwY9BObt)中查看包装。

