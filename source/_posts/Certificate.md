---
title: Certificate
date: 2019-01-14 11:28:58
tags:
---

## iOS/Mac 设备（系统）使用 App Provisioning Profile（Code Signing Identity）中的开发证书来判断App的合法性：

* 若用证书公钥能成功解密出 App（executable bundle）的内容摘要（_CodeSignature），证明此 App 确乃认证开发者发布，即来源可信；
* 再对 App（executable bundle）本身使用哈希算法计算摘要，若与上一步得到的摘要一致，则证明此 App 未被篡改过，即内容完整。

**CSR: Certificate Signing Request**  
**Only Certificates: .p7b or .cer or .pem file**
> If Keychain Access shows a certificate in your personal keychain, but it doesn't show it in the "My Certificates" list, it means you imported just a certificate but not the private key that goes with it, so OS X can't tell that it's truly "yours".

Certificate is the proof that the public key belongs to the Owner in the certificate or not.
prove that a certificate is yours, you must have the private key that forms a matched set with the public key contained in the certificate.


[https://superuser.com/questions/936840/add-to-my-certificates-in-keychain-access-mac-os-10-10](https://superuser.com/questions/936840/add-to-my-certificates-in-keychain-access-mac-os-10-10)   
[cn ver reference1](https://blog.csdn.net/phunxm/article/details/42685597)  
[cn ver reference2](https://www.cnblogs.com/A--G/p/4627590.html)

# iOS Provisioning Profile and Code Signing
## 1.App ID(bundle identifier)
App ID is Product ID
App ID应该和bundle identifier一致(Explicit)或者匹配(Wildcard)
reverse-domian-name, Company ID as Prefix(com.apple.garageband)
Explicit App ID: com.apple.garageband
Wildcard App ID: com.apple.*

## 2.Device
UDID
`iTunes->Summary` or `Xcode->WIndow->Devices`
* Apps signed by you or your team run only on designated development devices.
* Apps run only on the test devices you specify.

## 3.Certificate
### iOS certificate
* Development: identifies you, as a team member, in a development provisioning profile that allows apps signed by you to launch on devices. 
* Production(Distribution): identifies
 your team or organization in a distribution provisioning profile and allows you to submit  your app to the store. Only a team agent or an admin can create a distribution certificate.
Individual Account:iOS Development/Production 2 Max for each.  
### Root Certificate
Apple Certification Authority(Apple Root CA)  
    -> Apple Worldwide Developer Relations Cerification Authority(Subordinate CA)  
         -> AppleWWDRCA.cer(Intermediate Certificates)  
              ->Certificate for Development 
## 4.CSR: Cerificate Signing Request
## 5.Provisioning Profiles
**App ID, Devices, Development Certificates**
![](https://lh3.googleusercontent.com/ZpTN3usvh2HHymu4R-MsxKu3Z1e4yi38z74wGw56QjIeS44izExBrk0J9dHA8vukgsGoYxhAzR9pVCbzvWX-I8_hybfPBwrf8cOThOMJ7qlY-wSHjtpY1c8yaLZXN0MYrknsTfLeZ4fHzjNUOj92yel9iIFwN-RX2CIWU9FEidnnVCDK7Q-ayMBRptyc9suXDaFjVqHK0d9MqFPY8ZFkY2eCuxDhTueTjdGC6oS31KkryXjMKc-tQWIBtbK4sJduu67s6W5kj5lkRjUSC5az7uOTr6ep7nPf5pDE70cYxlrZlcY6uQXCewbOYFTJ9N-jp6REVJP_JCl98IuGPXht0V3unO-hvo3zd_5PQuTc1YiYwagIgj6jz8OOz1Tbw_jCNbLNAdJDAPlKUgAdAfdOtSQxvPPZS-YgNwkn_uRXm1gIq7zR1s2bp5e16IhKyCY3xxZeq-082sp-5bt_nnX4ZtjYYQyCiG2k7Ye76MyTNixlxhG9o24AARH4DW4IK5hcwfXcocg6Et9CY8yD7ZtA2asUV7oTIIK0Euof27e5FtE_lCB1CGzewfrPC9zgnqVnzjuQXRPknkzbDXEAzAzUN9DBPzq-xYj1iHFyBCWL0SASldyKjiyBZHOPcQUzoB8=w618-h377-no)

如果要打包或者在真机上运行一个APP，一般要经历以下三步：
* 首先，需要证书对应的私钥来进行签名，用于标识这个APP是合法、安全、完整的
* 其次，需要指明它的App ID，并且验证Bundle ID是否与其一致；
* 然后，如果是真机调试，需要确认这台设备是否授权运行该APP。
Provisioning Profile把这些信息全部打包在一起，方便我们在调试和发布程序打包时使用。这样，只要在不同的情况下选择不同的Provisioning Profile文件就可以了。

Provisioning Profile也分为Development和Distribution两类，有效期同Certificate一样。Distribution版本的ProvisioningProfile主要用于提交App Store审核，其中不指定开发测试的Devices（0，unlimited）。App ID为Wildcard App ID。App Store审核通过上架后，允许所有iOS设备（Deployment Target）上安装运行该App。
## 6.Team Provisioning Profile
![](https://photos.app.goo.gl/hz5E7Jxxx1V4Ft1Q9)
![](https://photos.app.goo.gl/uxfLkV8cAcNTrps17)
## 7.Cetificate & Signature
![](https://lh3.googleusercontent.com/EtW_nTp-eVQk3pzFIW0-z0kEtsnY7G0OCDK_qOLBdYp6ddyNIeDwgWU3o6ACAoWimFKRHiX46o3cTtDcvJ-7srtj-Q9wCTbGazzfTMnsPZ3XPAvBJHcBTXOOOgFo_XHdl_HSYP47XxTur0exDpVh_sGEooE14nm2rK0oyEqzhNF6UnpYD6HorHTDE0b9PRp0msMZqPh3YEJDaBl2q6eOBKSvalyr2HwSpOEuF_h2VdHN14uAf4xWGIMv25Kl5RHNWUJotoAhg4D1qQm-k6HNqTB7cLmKJYecT7XIOdipCdvJj1_42O5YJ8lNnSN8Xq8UuAUH0evhsudRe9vf1DBttl-fK-OFGzQaeET5i6iPJLc0ELjAZBUelgrCBD3qyBSnL3KAwsvaxcVxK6MY2sjDDFZxe6ZHdVTtadtg8HQlD3g3sjzWNkSOdaZcVI8oEaYNP-5nCencGAF4RAa9q9AQSOT_tPa04SR9x6CJtF6IFtwyDFoLd0CjEzX96_NQ1fc9a3MUISbLAMU7OFJLMEQUS6Q7u7s5l0hTkfza-gn5nkutRb-PGoy7Va4P7W3jmLvQfmP-lZm4DOC3zFfPGDGs5xniHYezxxVN1eAdQnB0MLt96qWjNulW_U4LBG0uOzw=w696-h471-no)
![](https://lh3.googleusercontent.com/18e1ZVR7Z6KFxhSxEeltpwqLUbRy54p5cIyYBH5vAoZCxRp1ZhGxsL7FjYQ7cYtS2Mw41UjIM1JzbBNosNV-WvkSIY2OSbpldG4edz4PGlmSWWOHXXC1QS0RjGroP-fgEuuGlsk9dV9C4s-WbatalBmS5IbJDWfKJJ9Xcj8M3Sw5y646MUErxjNwnKNRwF__MWPRDmuAlKjve4KifQMxUKSkhleO--ROaQ4LgrQmbmWIzZO-ECFZOVFSjwZr0wPi2LvdFV0WkcMqkHRNeqQlwv3QTfmzKHxKpWsZggWyIaPtnMj8SLk1VnTW-eYVZTvXfjewiN6sbiDJqQ6lfAgTbt0nuh9bWf58utJbUeWWd4c28batgC0Fo83s7ggAVc7gU8uaf2Fd-qq84Ou1_RZ8F1YCCnoWmRGTXU5oPySQ1AGuAHKWjOxz40eZEl9zknwlMfInyUeCqKdRzQqAQxO7fe7AHd9JVQVPKCKBvqL3gPe9vZIyEv4mlZxdDkVE5l9D0QdxXMiO3oUxg8-GA_g9qvXR-Rgo_95BuH4gXUDUuPnm3-73xCwwOffcCUVMbcTsERxhTgtZwQ0CIKzwKiuGd4EN4oF5mIFlsTaTUEc__xinoI69HfcRLOrfsHSXeDc=w697-h573-no)
## 7.share development account amoung multi machines
1. Xcode export development account(*.developmentprofile) or PKCS12 File(*.p12)
2. Keychain Access export PKCS12File(*.p12)
---------------------
Short version:
You can't use it as your certificate unless you have the private key that forms a matched set with the public key that's in the certificate. Go find where you left your private key and import that into the keychain, and Keychain Access will automatically see that it matches with the public key in that certificate and start showing that certificate in the "My Certificates" list.

Long version:
Certificates are public documents that you can freely distribute. They are just a way to securely link your identity (i.e. identifying information like your full name, username, email address, etc.) to your public key.

Since certificates are publicly distributable, simply having a copy of a certificate is not proof you are the person named in the certificate, or that the public key in the certificate is truly your public key.

To be able to prove that a certificate is yours, you must have the private key that forms a matched set with the public key contained in the certificate.

If you just have a .p7b or .cer or .pem file, it most likely just contains a certificate, but not the private key that goes with it.

Private keys must be kept completely secure and private and never given to anyone else. When stored on disk, they should be stored in an encrypted file that you need a passphrase to decrypt. The typical way to securely store a certificate along with the matching private key in an encrypted, password-protected file, is a .p12 (PKCS#12) file. See if you already have a .p12 file somewhere.

If Keychain Access shows a certificate in your personal keychain, but it doesn't show it in the "My Certificates" list, it means you imported just a certificate but not the private key that goes with it, so OS X can't tell that it's truly "yours".

You need to go find where your private key was stored when you first generated your public/private key pair. Generating a key pair is the first step toward getting a certificate. First a key pair is generated, then the public key, along with your identity information, is put into a Certificate Signing Request (a.k.a. CSR, req), and sent off to a Certificate Authority (CA) to be signed. The CA is supposed to verify your identity information and your public key, and then if it all checks out, they sign the CSR, creating a certificate. The signed certificate is sent back to you, and you have to match it back up with the private key you'd generated in the first step, in order to truly use it.

Note that the role of CA is nothing terribly special. It doesn't have to be some corporation like Verisign. Every personal computer OS contains all the software necessary to act as a CA. Keychain Access's Certificate Assistant feature will even walk you through setting up your CA setup for your own private use.

If you don't remember generating a key pair, you were probably using some software that did it automatically for you. For example, there's a special HTML tag that CA websites can use on their CSR web forms that tells your web browser to automatically generate a key pair and submit just the public key along with the web form. When you use Safari on such a form, the private key is stored in the user keychain for the OS X user account you're logged into. When you use IE in Windows on such a form, the private key is stored in the Windows equivalent of that (Microsoft calls this the user's "Certificate Store"; "store" as in "storage container" not "retail shop" :-).

I can't tell you where your private key is because I don't know what software you used to create it, and even if I knew that, I wouldn't know for sure where you told that software to save your private key. You'll probably have to sleuth that out yourself.

If you can't find your private key, you may need to consider it compromised and revoke your certificate (you may need to contact your CA to do that) and start over by generating a new key pair, creating a new CSR, having a CA sign it and issue a certificate, match it up with the new private key, etc. This is kind of like realizing that you're missing a copy of your house key, and choosing to have a locksmith rekey all your door locks just to be safe.

tl;dr: Go find your private key and import it into the keychain.
