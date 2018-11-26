## Exercises: RSA Sign / Verify

In this exercise we shall **sign** messages and verify signatures using the **PKCS\#1 v.1.5 RSA** signature algorithm with 4096-bit keys, following the technical specification from [**RFC 8017**](https://tools.ietf.org/html/rfc8017#page-15), using **SHA3-512** for hashing the input message. The RSA-PKCS1 v1.5 digital signature algorithm can be found as library for the most programming languages.

The RSA **private key** will be given encoded in [**PEM format**](https://en.wikipedia.org/wiki/Privacy-Enhanced_Mail) \([RFC 7468](https://tools.ietf.org/html/rfc7468), see the example\). The corresponding RSA **public key** will also be given encoded in **PEM format**. The RSA **signature** is 4096-bit integer \(1024 hex digits\).

## Sign a Message with RSA

Write a program to sign given text **message** with given 4096-bit **private key**, using the **PKCS\#1 v.1.5 RSA** signature algorithm with **SHA3-512** hashing for the input message. The input consists of 2 text lines. The **first line holds** the input **message** for signing. The **next few lines** holds the private key as **hex string**. Print the **output** as JSON document, holding the input **message** + the **public key** of the signer \(as hex string\) + the RSA **digital signature** \(as hex string\).

Sample **input** \(text message + PEM-encoded RSA private key\):

```
Message for RSA signing
-----BEGIN RSA PRIVATE KEY-----
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
-----END RSA PRIVATE KEY-----
```

Sample **output** \(message + hex-encoded signature + PEM-encoded RSA public key\):

```
Message for RSA signing
28ce01ec0f8511e92407496b7aa777a8b38fbc27a3656c9862830427bf8a006d59d19ac3b3441f174aee2fe6560b2b5f91aeb72ffa150dad4bd4e93a3b78eabfb48f8051b09cdfc5cbb63b014a7beb81cae4220fa01bedf5fa10aa3b6dcdd7ad229fd7ce2e8883a4893bef532c7b7822993408577a20a198387e073e15e53ffab8d7f3c46fa50347cd45d7a5d319b66d4ead658297a2e7127cc6a1dc5e104beb3ae2ba390d5ae90a66bd8a537e4df296c212186754206c5a0b155c226a3a580e943db33bf9e9829ea3e38f00aafa0e4839bf4673d83b14c74cd9ac359afc3fa56ca7f3a8391e6fb234561b9deca9ac3fa9147d70b0f1189db734b5ea96f287c604467dab0efbf5f1c78437920283dfe6fbcd56f4e859e24ee37552b3b8de5c4fa35e65cf9fe63ec7e2fd155d503fec2648303e495d86af97ac53c14b203bdc7233365d481fda08cac905c48e31bd389bea0f983e035225c4fca269a66009332bbba83542dcd484832f4d40ab14eee3609aa78c01539984758592de3355b528de3c8a669442cbd6f03808226ef0c13924b9553b7af7ff02a6916f106061a7bcbe093f795d9455709ab2b030ff485e9993eb978ae57cabeade4747e981b47c36128c39df970d1f29c4e4a3c225a8384d55995599c9ce3afe14068f4eb4edeb120beb534955b519a4424f82136d3511a0dafad46b010c3fa15bd233bdc85a7fd42a
-----BEGIN PUBLIC KEY-----
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAoYjbzkMmss6BU/eCBYhs
3bFRBVldM9DlaM7WhPZEgmYl7C1Ob0kmEPG2O/GaNoBOnwptHykzvpYS42rr/D8I
0LeJ/2dz0uStQv6kQDIDmNRTthW9spcuBsqW3e1bRyf0JrL8ot1X8M4k0NGU7w50
8htPzRZXRS2Zonv8G/N35ePDV5Xf5mrcOPOebconndXHRqfLlyXCxCS5x0qlJGX1
d/oe2Xop7VfBP/UhrrmNmstZsBEvL3f33+a482xuCTvPIQcv62N3laR2wKOJN9Cp
FOpqjwR8cj9oLjbCRHd5T/+bgc6DO/XVzr9DAPVaYLZvm8puMhhgckNIjgPOfWsV
yI+/G1zuUH5caFMhMaS95M2a1XNIwJ5sF25PFpsttIrFXC+b0JS325mk5qvzCgnu
0DrWT2VPBNjw4rvmhBPnFb/JdXy5e5ZIpxtGRpvKYcBxDk6yqgt9SC/e81+tqCrF
SQ9cG1QCV/BnZw4cd1JHe3/AHot1YeWjb8YpIFifJ7WxFb0g9GIYJZTh3dC9hrNO
fSsIoOL+ZAyNFp43u0FJT7qtC7CtxPvJnt/h8ACE07ewgkq3M0OzmT2RNIf0HhyS
MjwdIhlY8QGGoV3+zDu9nTx63tvvaBikPwtZuCz76ipWb5Kt6SA80fsN/QOtDflm
BwjlT6UvoivgK8C7iIrwQGUCAwEAAQ==
-----END PUBLIC KEY-----
```

## Verify Message Signature with RSA

Write a program to **verify RSA signature** \(calculated by using **PKCS\#1 v.1.5** + **SHA3-512**\), created by the previous exercise. The **input** comes as signed **message** \(first line\) + RSA digital **signature** \(second line\) + 4096-bit RSA **public key** \(all input lines to the end\). Print as **output** a single word: "**valid**' or "**invalid**".

Sample input \(correctly signed message\):

```
Message for RSA signing
28ce01ec0f8511e92407496b7aa777a8b38fbc27a3656c9862830427bf8a006d59d19ac3b3441f174aee2fe6560b2b5f91aeb72ffa150dad4bd4e93a3b78eabfb48f8051b09cdfc5cbb63b014a7beb81cae4220fa01bedf5fa10aa3b6dcdd7ad229fd7ce2e8883a4893bef532c7b7822993408577a20a198387e073e15e53ffab8d7f3c46fa50347cd45d7a5d319b66d4ead658297a2e7127cc6a1dc5e104beb3ae2ba390d5ae90a66bd8a537e4df296c212186754206c5a0b155c226a3a580e943db33bf9e9829ea3e38f00aafa0e4839bf4673d83b14c74cd9ac359afc3fa56ca7f3a8391e6fb234561b9deca9ac3fa9147d70b0f1189db734b5ea96f287c604467dab0efbf5f1c78437920283dfe6fbcd56f4e859e24ee37552b3b8de5c4fa35e65cf9fe63ec7e2fd155d503fec2648303e495d86af97ac53c14b203bdc7233365d481fda08cac905c48e31bd389bea0f983e035225c4fca269a66009332bbba83542dcd484832f4d40ab14eee3609aa78c01539984758592de3355b528de3c8a669442cbd6f03808226ef0c13924b9553b7af7ff02a6916f106061a7bcbe093f795d9455709ab2b030ff485e9993eb978ae57cabeade4747e981b47c36128c39df970d1f29c4e4a3c225a8384d55995599c9ce3afe14068f4eb4edeb120beb534955b519a4424f82136d3511a0dafad46b010c3fa15bd233bdc85a7fd42a
-----BEGIN PUBLIC KEY-----
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAoYjbzkMmss6BU/eCBYhs
3bFRBVldM9DlaM7WhPZEgmYl7C1Ob0kmEPG2O/GaNoBOnwptHykzvpYS42rr/D8I
0LeJ/2dz0uStQv6kQDIDmNRTthW9spcuBsqW3e1bRyf0JrL8ot1X8M4k0NGU7w50
8htPzRZXRS2Zonv8G/N35ePDV5Xf5mrcOPOebconndXHRqfLlyXCxCS5x0qlJGX1
d/oe2Xop7VfBP/UhrrmNmstZsBEvL3f33+a482xuCTvPIQcv62N3laR2wKOJN9Cp
FOpqjwR8cj9oLjbCRHd5T/+bgc6DO/XVzr9DAPVaYLZvm8puMhhgckNIjgPOfWsV
yI+/G1zuUH5caFMhMaS95M2a1XNIwJ5sF25PFpsttIrFXC+b0JS325mk5qvzCgnu
0DrWT2VPBNjw4rvmhBPnFb/JdXy5e5ZIpxtGRpvKYcBxDk6yqgt9SC/e81+tqCrF
SQ9cG1QCV/BnZw4cd1JHe3/AHot1YeWjb8YpIFifJ7WxFb0g9GIYJZTh3dC9hrNO
fSsIoOL+ZAyNFp43u0FJT7qtC7CtxPvJnt/h8ACE07ewgkq3M0OzmT2RNIf0HhyS
MjwdIhlY8QGGoV3+zDu9nTx63tvvaBikPwtZuCz76ipWb5Kt6SA80fsN/QOtDflm
BwjlT6UvoivgK8C7iIrwQGUCAwEAAQ==
-----END PUBLIC KEY-----
```

Sample output:

```
valid
```

Sample input \(tampered message\):

```
Tampered message
28ce01ec0f8511e92407496b7aa777a8b38fbc27a3656c9862830427bf8a006d59d19ac3b3441f174aee2fe6560b2b5f91aeb72ffa150dad4bd4e93a3b78eabfb48f8051b09cdfc5cbb63b014a7beb81cae4220fa01bedf5fa10aa3b6dcdd7ad229fd7ce2e8883a4893bef532c7b7822993408577a20a198387e073e15e53ffab8d7f3c46fa50347cd45d7a5d319b66d4ead658297a2e7127cc6a1dc5e104beb3ae2ba390d5ae90a66bd8a537e4df296c212186754206c5a0b155c226a3a580e943db33bf9e9829ea3e38f00aafa0e4839bf4673d83b14c74cd9ac359afc3fa56ca7f3a8391e6fb234561b9deca9ac3fa9147d70b0f1189db734b5ea96f287c604467dab0efbf5f1c78437920283dfe6fbcd56f4e859e24ee37552b3b8de5c4fa35e65cf9fe63ec7e2fd155d503fec2648303e495d86af97ac53c14b203bdc7233365d481fda08cac905c48e31bd389bea0f983e035225c4fca269a66009332bbba83542dcd484832f4d40ab14eee3609aa78c01539984758592de3355b528de3c8a669442cbd6f03808226ef0c13924b9553b7af7ff02a6916f106061a7bcbe093f795d9455709ab2b030ff485e9993eb978ae57cabeade4747e981b47c36128c39df970d1f29c4e4a3c225a8384d55995599c9ce3afe14068f4eb4edeb120beb534955b519a4424f82136d3511a0dafad46b010c3fa15bd233bdc85a7fd42a
-----BEGIN PUBLIC KEY-----
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAoYjbzkMmss6BU/eCBYhs
3bFRBVldM9DlaM7WhPZEgmYl7C1Ob0kmEPG2O/GaNoBOnwptHykzvpYS42rr/D8I
0LeJ/2dz0uStQv6kQDIDmNRTthW9spcuBsqW3e1bRyf0JrL8ot1X8M4k0NGU7w50
8htPzRZXRS2Zonv8G/N35ePDV5Xf5mrcOPOebconndXHRqfLlyXCxCS5x0qlJGX1
d/oe2Xop7VfBP/UhrrmNmstZsBEvL3f33+a482xuCTvPIQcv62N3laR2wKOJN9Cp
FOpqjwR8cj9oLjbCRHd5T/+bgc6DO/XVzr9DAPVaYLZvm8puMhhgckNIjgPOfWsV
yI+/G1zuUH5caFMhMaS95M2a1XNIwJ5sF25PFpsttIrFXC+b0JS325mk5qvzCgnu
0DrWT2VPBNjw4rvmhBPnFb/JdXy5e5ZIpxtGRpvKYcBxDk6yqgt9SC/e81+tqCrF
SQ9cG1QCV/BnZw4cd1JHe3/AHot1YeWjb8YpIFifJ7WxFb0g9GIYJZTh3dC9hrNO
fSsIoOL+ZAyNFp43u0FJT7qtC7CtxPvJnt/h8ACE07ewgkq3M0OzmT2RNIf0HhyS
MjwdIhlY8QGGoV3+zDu9nTx63tvvaBikPwtZuCz76ipWb5Kt6SA80fsN/QOtDflm
BwjlT6UvoivgK8C7iIrwQGUCAwEAAQ==
-----END PUBLIC KEY-----
```

Sample output:

```
invalid
```


